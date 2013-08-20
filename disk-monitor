#!/usr/bin/env bash

# Script takes as argument a directory. The disk usage monitoring log 
# is kept on the disk on which the given directory is located.

if [ $1="" ]; then
  dir=$(pwd)
else 
  dir=$1
fi
 
if [ ! -d $dir ]; then
  echo "$1 is not a directory"
else
  date=$(date +%y.%m.%d.%H:%M:%S)
  device=$(df $dir | awk 'NR==2 {print $1}')
  used=$(df $dir | awk 'NR==2 {print $3}')
  available=$(df $dir | awk 'NR==2 {print $4}')
  logline="$device,$date,$used,$available"

  logfile=~/diskusage.log
  if [ ! -f $logfile ]; then
    echo "Device,Date,Used,Available" >> $logfile
  fi

  echo $logline >> $logfile
fi

