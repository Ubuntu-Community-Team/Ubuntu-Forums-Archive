---
title: "simple command line CD/disk Catalog"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by SirSlipALot on 2009-10-20
Hello alls,

I want to use the brains of the interwebs to write an offline cataloger of media (CD, dvd, any_directory): wherever a ls command works

I want it to be simple and future proof. and since I don't have a lot (well...) of stuff I want all the information to be written in plain ascii files (or some sort of xml human readable format).
one file for each CD or whatever media.

search is accomplished by means of an editor (e.g.: medit - search in files) or with grep...

I'm doing this for years now (with no regrets) on windows - I've been using windowss ever since there is windowss - but now i definitly changed to ubuntu (to commemorate windows 7 ;)
The catalog actually as grown quite big in size and takes some seconds to search - but why do we need bigger hard disks and faster cpus? ... :)

And there you have it: for each CD that i have, i have a correspondent ascii file describing me the contents of that cd. that way is easy to find a book, movie or music.

now i want to learn more about bash and linux and i want a "glorified script" or ls of sorts... btw i want it to be called CD Catalog or cdc for shorts - you know: whatever :)

here's how i started:

ls -AkNqRsX --group-directories-first --file-type > volume_name.txt

this is cute but i want more...

((( btw, some explanation with man ls:
-A, --almost-all
              do not list implied . and ..
-F, --classify
              append indicator (one of */=>@|) to entries
--file-type
              likewise, except do not append ‘*’
--block-size=8  = -k     like --block-size=1K
--group-directories-first
              group directories before files
-N, --literal
              print raw entry names (don’t treat e.g. control characters specially)
-p, --indicator-style=slash
              append / indicator to directories   -> included in -F
-q, --hide-control-chars
              print ? instead of non graphic characters
-R, --recursive
              list subdirectories recursively
-s, --size
              print the size of each file, in blocks
-X     sort alphabetically by entry extension
)))

for example, i don't know how to write the modification date of each file and only the date...... :/

this stupid devilish detail led me to want more (wich is always a bad thing):

if the file is a:

1) movie: run something like ffmpeg -i filename.avi OR tcprobe -i -> return information on input file filename.avi : duration, Geometry: Rows x Lines, Kbit/s, maybe the codecs...
2) pdfinfo -> print information on a pdf file : number of pages
3) file -> return "generic" information about a file....
4) mp3info -> return info. on a mp3 file : duration, kbps
5) 7z -l  -> list contents of the compressed file
6) identify -> return info. on an image : Geometry, colordepth...
...

some of this commands do have to be installed...


I suppose there are many ways of getting what i want. but i would like to keep it in the "bash realm".

My problem is i know very little of it (and i'm lazy) and this thing doesn't work:

->>  for f in `ls --cute_options`; do file_info $f; done

what now?

give some tips and clues and i'll be back to this thread until we have a decent cdc.

Many thanks!


PS: programs like Gwhere and cdcat do the job, but you are stuck with them after you start using them and aren't as powerfull as a script promises to be...
(actually the best program for the job is selfishware: Whereisit for windows - but its proprietary stuff)

---

### Post by LewRockwell on 2009-10-20
unrelated link but fun nevertheless

[http://www.ultralightnews.com/ssulbg/nieuport11-grahamlee/experimental_amateurbuilt.html](http://www.ultralightnews.com/ssulbg/nieuport11-grahamlee/experimental_amateurbuilt.html)

.

---

### Post by SirSlipALot on 2009-10-24
There is progress. Here is the current bash script:

```

#!/bin/bash

# cdc = CD Catalog: Human readable catalog of a directory recursivly with file size, name, date and extra information where relevant...

# Usage help:
if [ "$1" = "-h" ]; then
cat << !

cdc = CD Catalog: Human readable catalog of a directory recursivly with file size, name, date and extra information where relevant...

 cdc usage:
 cdc [ directory ] [ -o filename]
 if no directory is given then cdrom is assumed by default.
 if no filename is given then standard output is the default used.
 -o filename -> send output to filename.

 Examples:
 $ cdc     -> catalog the cdrom contents to the standard output (monitor)
 $ cdc .   -> likewise, but catalog the current directory and sub-directories
 $ cdc ~ -o ~/home.txt   -> catalog home directory and put result into the file home.txt located in the home directory ~

!
exit 0
fi

# set base_directory to $1. if undefined: set to '.'
if [ -z $1 ]; then
  base_dir=`awk '{if ($1=="/dev/sr0") print $2}' /proc/mounts`
# if base_dir is empty output=(nolabel).txt ???????????????????????????????????????????????????
  output=`basename $base_dir`.txt # or use the command volname...
else
  if [ $1 = "-o" ]; then
    base_dir=`awk '{if ($1=="/dev/sr0") print $2}' /proc/mounts`
# if base_dir is empty output=(nolabel).txt ???????????????????????????????????????????????????
    output=$2
  else
    base_dir=$1
  fi
fi

if [ "$2" = "-o" ]; then
  output=$3
fi

if [ -z $output ]; then
  output="&1" # redirect to standard output (stdout) &1  ?????????????????????????????
else
# check if output file already exists
  if [ -e $output ]; then
    echo -n "File already exists. Overwrite $output? (y/n) "
    read keyin
    if [ "$keyin" = "y" ]; then
      rm -f $output
    else
      echo Aborting.
      exit 1  #??????????????????????????
    fi
  fi
fi

current_dir=""
echo base_dir = $base_dir

ls -1ANqRX --group-directories-first --file-type $base_dir | while read -r FILE
do
# if $FILE terminates with '/' then print <DIR>
# if $FILE terminates with ':' set current_directory accordingly

# if does not terminate with ':', nor is empty, print size, name, date
  echo "$FILE" >&1 #>> $output

# case relevant extension: print extra information

done

#echo Done.

# cdc v0.00
# copyleft: code under a GNU GPL licence
# main design: SirSlipALot @ Ubuntu forums
# Thanks for the help: undecim @ Ubuntu forums


```Tips, clues and general help very welcome!
Thanks :)

---

### Post by SirSlipALot on 2009-10-25
Not finished just yet :)

more (better) progress:

```

#!/bin/bash

# cdc = CD Catalog: Human readable catalog of a directory recursively with file size, name, date and extra information where relevant...
# alternative name: cdahr = CD Archive Human Readable, as in: - Aahr! Me is a Pirate! Ahr! :))

# Usage help:
if [ "$1" = "-h" ]; then
cat << !

CD Catalog: Human readable catalog of a directory recursively with file size, date, name and extra information where relevant...

 cdc usage:
 cdc [ directory ] [ -o filename]
 if no directory is given then cdrom is assumed by default.
 -o filename -> send output to filename.
 if no filename is given then standard output is used.

 Examples:
 $ cdc     -> catalog the cdrom contents to the standard output (monitor)
 $ cdc .   -> likewise, but catalog the current directory and sub-directories
 $ cdc ~ -o ~/home.txt   -> catalog home directory and put result into the file home.txt located in the home directory ~
!
exit 0

# Ideas...:
# -O     -> force overwrite of file
# -s     -> simplified output - no extra information (just ls...)

fi

# Process options:
if [ -z "$1" ]; then
  base_dir=`awk '{if ($1=="/dev/sr0") print $2}' /proc/mounts`
  output=`basename $base_dir`.txt # or use the command volname...
# if base_dir is empty output=_nolabel_.txt ???????????????????????????????????????????????????
  if [ "$output" = ".txt" ]; then
    echo cdrom has no label. Renaming output file to _nolabel_.txt ! >&2
    output=_no_label_.txt
  fi  
else
  if [ "$1" = "-o" ]; then
    base_dir=`awk '{if ($1=="/dev/sr0") print $2}' /proc/mounts`
    output=$2
  else
    base_dir=$1
# check if base directory is valid
    if [ ! -d $base_dir ]; then
      echo Directory $base_dir doesn\'t exist. Aborting. >&2
      exit 1 # ????????????????????????????????
    fi
  fi
fi

if [ "$2" = "-o" ]; then
  output=$3
fi


if [ -z "$output" ]; then
  exec 3>&1 # redirect output to standard_output (stdout) &1
else
# check if output directory is valid
  if [ ! -d `dirname $output` ]; then
    echo Directory `dirname $output` doesn\'t exist. Aborting.
    exit 1 # ????????????????????????????????
  fi
# check if output file already exists
  if [ -e $output ]; then
    echo -n "File already exists. Overwrite $output? (y/n) " >&2
    read keyin
    if [ "$keyin" = "y" ]; then
      rm -f $output
    else
      echo Aborting. >&2
      exit 1  #??????????????????????????
    fi
  fi
  exec 3<> $output # Open $output and assign file descriptor 3 to it.
  exec 1>&3 # redirect stdout to fd 3.
fi


# Main script:

# some progress information ...
echo -n "[`basename $0` progress: Preparing list... this may take a while. ]" >&2

# FORMAT du output. ex: 12345678->12,345,678 for better reading ??? -> printf "%'d\n" 1234567
echo Total=$(printf $(du -s --block-size=1 $base_dir)) bytes "(="$(printf $(du -sh $base_dir))")" on `stat -f -c "%n, System_type=%T, Block_size=%s bytes, Free_blocks=%f" $base_dir` >&3

pip1="/dev/shm/pip1.txt"
ls -1hNopqRX --group-directories-first --file-type $base_dir > $pip1

total_lines=$(wc -l < $pip1 )

# del NNN characters.... search for better way ???????????
echo -e "\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b                                                         " >&2

# for progress information ...
counter=0

while read -r FILE
do
  let counter=counter+1
# echo [`basename $0` progress:  xxx % ]   -> x=(current_line in ls-R )/(total_lines in ls-R) ... :)
#####if [ ! -z "$output" ]; then
#####  printf "\b\b\b\b\b\b" >&2
#  printf "% 3d %s" $(( $counter/$total_lines*100 )) "%" >&2
#####  printf "% 5d %s" $(( $counter )) "%" >&2
#####fi

  cfile=${FILE#*$USER} #->>> remove everything before occurrence of string $USER ->> ?????? will FAIL if username is drwxr or substring :))
###echo cfile=$cfile
# # # # # FAIL FAIL FAIL FAIL FAIL FAIL : extract fixed length of $FILE using also the lenght of $USER

  control=${cfile:(-1)}

# case "$control" ......

  if [ ! -z "$control" ]; then

# if $FILE terminates with '/' then print directory field
    if [ "$control" = "/" ]; then
      echo "dir >" $(echo -n $cfile|cut -d ' ' -f2-) >&3
    else

# if $FILE terminates with ':' set current_directory accordingly
      if [ "$control" = ":" ]; then
        current_dir=${cfile%?}  # $(echo -n "$s")|head -c -1
        echo -e "\n"$current_dir":"
      else
        echo -n "$cfile ;" >&3

# if not "total" line:
# case relevant extension: print extra information ELSE print size in bytes.
if [ ${cfile:0:5} != "total" ]; then
#ext=${cfile#*.}
#echo ext=$ext >&3
cfile=$(echo -n $cfile|cut -d ' ' -f4-)
###echo current_dir=$current_dir, cfile=$cfile
echo `file -bi "$current_dir/$cfile"`
fi

# pdf
# picture
# sound
# video
# archive

# available command line apps:
# ffmpeg -i filename.avi OR tcprobe -i - return information on input file filename.avi
# pdfinfo - print information on a pdf file
# file - return "generic" information about a file....
# mp3info - return info. on a mp3 file
# 7z -l  - list contents of a compressed file
# identify - return info. on an image

 
      fi
    fi
  fi #if [-z "$control"]; then
done < $pip1

# clean progress information ...
if [ ! -z "$output" ]; then
  printf "\b\b\b\b\b\b" >&2
fi

# clean up...
###rm $pip1
exec 3>&- # Close fd 3.

#echo Done.

# cdc v0.01
# copyleft: code under a GNU GPL licence
# main design: SirSlipALot @ Ubuntu forums
# Thanks for the help: undecim @ Ubuntu forums
# note... bash is an interpreted language, and a rather slow one... ;)


```This is my first bash script. lots of gooogle! :P

Suggestions appreciated

---

