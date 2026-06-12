---
title: "BASH SCRIPTING: Help! Yet another check element in array Question"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by kristo5747 on 2010-07-28
Greetings,

Administrators, please move my post if this is not the right forum. Thank you.

DISCLAIMER: My shell scripting is rusty so my question may be borderline stupid. You've been warned.:)

I need to create a script that a) lists the content of zip files in a directory and b) sends out an `exception` report. My ZIP files contain a control file (for load check). I want to abort the whole process if the control file is missing from the ZIP file.

Typically a zip file will have its contents looking like this:

```
file_1231232345.ctl
filea.txt
fileb.txt
filec.txt

```Here what I wrote so far:

```
#!/bin/bash

#get today's date in YYYYMMDD formart 
DAY=`date +%Y%m%d`

#populate array of HDD zipped log(s) for today 
HDD_ZIP_Array=(`ls *${DAY}*.zip`)
HDD_ZIPlen=${#HDD_ZIP_Array
[*]}

#echoes message if no files to process and exits. 
if [ $HDD_ZIPlen -eq 0 ]
then
        echo " HDD CheckZip -- $HDD_ZIPlen files! Process will exit!" ;         exit 1;
else
        for name in ${HDD_ZIP_Array[@]};
                 do
                echo " Zip File Name: $name"
                #list ZIP contents with unzip, remove header and trailer, 
                 #reverse sort to put control file name at index 0 and put file names in array().
                HDD_LIST_Array=(`unzip -l $name | head -n -2|tail -n +4 | sort -r | awk '{print $4}'`)
                HDD_LISTlen=${#HDD_LIST_Array
[*]}
                #iterate array to 1) build exception report and 2) look for control file
                echo -e "Files in ZIP file: $name\n"     >> report.out
                        for (( i = 0 ; i < ${#HDD_LIST_Array[@]} ; i++ ))
                                do
                                        echo -e "${HDD_LIST_Array[$i]}"  >> report.out
                                done
                echo -e "\n  Number of files in ZIP file: $HDD_LISTlen."  >> report.out
              #since the name of the control contains a random number, glob CTL extension
               if [ $i != {*ctl} ]
              then
                   echo "Control file not found!" ; exit 2;
                fi
                done
fi

```It is basic but it works. Except the bottom part where I test for the CTL file extension. It is not working whether the file is here or not.

What am missing?

Thanks for your input.

Al.

---

### Post by Apollo87 on 2010-07-29
Hello

I haven't tested the script personally, but I believe I see the issue.

For the failing if statement, it looks like the comparison is not doing what you are intending it to.  It looks like the $i is being set in the for loop above.  So when you try to compare, its trying 4 != {*ctl}.  You will need to compare the element of the array. IE: ${HDD_LIST_Array[0]}.

The way I would set this up is:
```
i=`echo ${HDD_LIST_Array[0]} | awk -F . '{print $NF}'`
if [ "$i" != "ctl" ]
  then
    echo "Control file not found!" ; exit 2;
fi
```

The line "i=`echo ${HDD_LIST_Array[0]} | awk -F . '{print $NF}'`" will grab the file extension, ctl.  Then you can just see if it matches.

Let me know if you are having any more trouble and I'll try to help some more.

---

### Post by kristo5747 on 2010-07-29
> **Apollo87 said:**
> Hello

I haven't tested the script personally, but I believe I see the issue....You will need to compare the element of the array.....

BINGO! That is exactly the problem I was having: I was not comparing the element of the array but a value that could never match.

I tried your suggestion. It worked.

Thank you!!!:D

---

