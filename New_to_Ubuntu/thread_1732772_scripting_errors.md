---
title: "scripting errors"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by compost1 on 2011-04-18
Hey all!!
New to using these threads and forums, so please correct me if i'm in the wrong thread.
I'm running 10.10 mavrick, 2.5.35-28-gen.

Im pretty much a noob to scripting, i have this script


# !usr/bin/bash
#
# SCRIPT:    Parsing a file
# AUTHOR:    Modified by 
# DATE:        04/16/2011
# REV 1.2
# Parsing and Timing of a Logfile in a unix environment
#
# This script shows one way of reading a file line-by-line.
#
######################################################################
#

INFILE="access_*"
OUTFILE=writefile.out
TIMEFILE="/tmp/loopfile.out"
>$TIMEFILE
THIS_SCRIPT=$(basename $0)

######################################################################

function usage

{
echo "\nUSAGE: $THIS_SCRIPT file_to_process\n"
echo "OR - To send the output to a file use: "
echo "\nTHIS_SCRIPT file_to_process > output_file_name 2>&1 \n"
exit 1
}

#####################################################################

function while_read_LINE_bottom

{

# Method 2

# Zero out the $OUTFILE


>$OUTFILE

while read LINE

do 
    echo "$LINE" >> $OUTFILE 
    :

done < $FILENAME

}

#####################################################################

# function verify_files
# {
# diff $INFILE $OUTFILE >/dev/null 2>&1
# if (( $? != 0 ))
# then
#    echo "ERROR: $INFILE and $OUTFILE do not match"
#    ls -l $INFILE $OUTFILE
# fi
# }


#######################################################################
##### START OF MAIN ###################################################
#######################################################################

#     Test the Input

# Looking for exactly one parameter
(( $# == 1 )) || usage

# Does the file exist as a regular file?
[[ -f $1 ]] || usage

echo "\nStarting File Processing of each Method\n"

echo "Method 2:"
echo "\nfunction while_read_LINE_bottom\n" >> $TIMEFILE
echo "function while_read_LINE_bottom"
time while_read_LINE_bottom >> $TIMEFILE

But i'm getting this error in terminal which is not really an error so to speak.

./parsbottom
\nUSAGE: parsbottom file_to_process\n
OR - To send the output to a file use: 
\nTHIS_SCRIPT file_to_process > output_file_name 2>&1 \n

Completely lost, any help would greatly be appreciated.

Thank you all.

---

### Post by manishraj2011 on 2011-04-18
As I checked the code in ubuntu Terminal, I found that the **echo **command in ubuntu doesn't support **backslash escape sequence** by default. 

So, You need to write **echo -e <<The code>>** 
                instead of  **echo <<The code>>**.

I think this should solve the problem.

---

