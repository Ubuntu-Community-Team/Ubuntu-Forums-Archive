---
title: "Script to import string characters into array"
date: 2011-03-30
forum: New to Ubuntu
---

### Post by camocazi on 2011-03-30
Hey all,
 
This is my first post, and I am relatively new to linux. I am writing a bash script in which I am trying to extract one line from another file and parse specific words from the line into an array. So for example, I have a file called SortScans in which the first 5 lines might look like this (nevermind that this file is in csh):
 
```
 
#!/bin/csh
 
set Runs = (2 3 4 5 6 7 8 9 10 11 12 13)
set Folders = (anat RS1 RS2 RS3 DTI DTI DTI DTI DTI DTI DFM DFM)

```
 
and in my new script, I want to create 2 arrays that would correspond just to what's inside those parentheses, where the end result would be the following 2 arrays
 
RunsArray
[*] = 2 3 4 5 6 7 8 9 10 11 12 13
FoldersArray
[*] = anat RS1 RS2 RS3 DTI DTI DTI DTI DTI DTI DFM DFM
 
So here is the code that I am using so far in my script just to create RunsArray:
 
```
 
#!/bin/bash
 
RUNS=`echo | awk 'NR==4 {print;exit}' SortScans`
 
sed -i 's/*(//' $RUNS
sed -i 's/)//' $RUNS
 
declare -a RunsArray
RunsArray=$RUNS

```
 
I don't really know what I'm doing there, I just sort of copy pasted different related things I've seen on forums. But I'm getting the following error on the sed part -
 
sed: can't read set: no such file or directory
 
and that error repeats for each word or number down the line (i.e. runs, =, (2, 3, 4, etc.)
 
Anybody think they can help me out? Like I said I'm just starting out, so if you think you have a better way of doing this altogether, I would love to hear it. Thanks y'all.

---

### Post by kaibob on 2011-03-31
The following shell script will do what you want. It reads the file "SortScans" line by line and assigns the second word in each line to the variable "item" and assigns everything from the fourth word to the end of the line to the variable "data". When the second word in a line contains the string "Runs" then the array "RunsArray" is created from the contents of the variable "data". When the second word in a line contains the string "Folders" then the array "FoldersArray" is created from the contents of the variable "data". 

This shell script could break easily, but it works with the text presented in your post. My knowledge of the eval command is quite limited, but it seems to be necessary to expand the contents of the variable "data" before the arrays "RunsArray" and "FodlersArray" are created. 

```
#!/bin/bash

while read -r _ item _ data ; do
  [[ "$item" = Runs ]] && eval RunsArray=$data
  [[ "$item" = Folders ]] && eval FoldersArray=$data
done < SortScans

echo "${RunsArray[*]}"
echo "${FoldersArray[*]}"
```

Your shell script could be modified to work as shown below. I am not knowledgeable with sed, so I instead used parameter expansion to get the data inside the parentheses (see reference below).

```
#!/bin/bash
 
RUNS=$(awk 'NR==4 {print;exit}' SortScans)
 
RUNS="${RUNS##*(}"
RUNS="${RUNS%)*}"
 
RunsArray=($RUNS)

echo "${RunsArray[*]}"
```

REFERENCE
[http://wiki.bash-hackers.org/syntax/pe](http://wiki.bash-hackers.org/syntax/pe)

---

### Post by Crusty Old Fart on 2011-04-01
Using sed, it could be like this:
```

#!/bin/bash
 
declare -a RunsArray=($(awk 'NR==4 {print}' SortScans | sed -e 's/.*(//' -e 's/)//'))
declare -a FoldersArray=($(awk 'NR==5 {print}' SortScans | sed -e 's/.*(//' -e 's/)//'))

echo RunsArray
[*] = ${RunsArray
[*]}
echo FoldersArray
[*] = ${FoldersArray
[*]}

exit 0

```Just another way to skin the cat. Perhaps a little cleaner, depending on your taste and style.

---

### Post by camocazi on 2011-04-01
Nice!! That did the trick. Thanks

---

### Post by Crusty Old Fart on 2011-04-01
> **camocazi said:**
> Nice!! That did the trick. Thanks
Great. Glad you got it working.

It helps everyone if you mark your threads as [SOLVED] when you're happy with a solution.
Only you, as the Original Poster (OP), can do it.

Follow the green How To link in my signature.

Best wishes,

Crusty

---

### Post by Crusty Old Fart on 2011-04-02
Upon thinking about this a little more, I realize that it would have been better to use **grep** instead of **awk**, as follows:
```

#!/bin/bash
 
declare -a RunsArray=($(grep Runs SortScans | sed -e 's/.*(//' -e 's/)//'))
declare -a FoldersArray=($(grep Folders SortScans | sed -e 's/.*(//' -e 's/)//'))

echo RunsArray
[*] = ${RunsArray
[*]}
echo FoldersArray
[*] = ${FoldersArray
[*]}

exit 0

```My earlier script, using **awk**, would only work correctly when ***Runs*** appeared on line 4 and ***Folders*** appeared on line 5 in the SortScans file. This version, using **grep**, is more tolerant in that it will find ***Runs*** and ***Folders*** regardless of which lines they appear on. It's also a bit cleaner. I should have written it like this in the first place...sorry.

Have fun,

Crusty

---

