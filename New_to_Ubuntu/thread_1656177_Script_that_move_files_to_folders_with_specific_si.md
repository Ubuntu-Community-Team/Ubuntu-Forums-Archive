---
title: "Script that move files to folders with specific size"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by jasmine89 on 2010-12-30
hey, please i need your help I'm working on this script 
I want to copy files from a specific folder to folders with a specific  size
i.e : that's help when ur USB flash capacity is 2G then this script  takes the files and divide them by their sizes to folders , please help  me , it's driving me crazy , don't know where's the mistake !!](*,):confused:
Here's the code :
```
#!/bin/bash

if test $1="-s"
then

i=1

mkdir files/file$i

`ls $2 -1 -s>r`

num=1
size=0

for j in `cat r` 
 do
  if [ $size -le $3 ]
    then
   
    `ls $2 -1 -l|awk '{print $5}'|head -$num|tail -1>s`
     for w in `cat s` 
      do
        size=$[$size+$w]
      done

     `ls $2 -1|head -$num|tail -1>val`
     for c in `cat val` 
      do
        cp $2/$c file$i
      done 

  else
      mkdir files/file$i
      i=$[$i+1]
      size=0
   fi

 num=$[$num+1]

done

fi

```and the call is :(for example)
./test.sh -s Folder 2000

---

### Post by Crusty Old Fart on 2010-12-30
If you could post an error message, or some indication of how the script is failing, it would help.

---

### Post by jasmine89 on 2010-12-30
Actually it's making Empty folders , without copying any things to it !!!

---

### Post by Crusty Old Fart on 2010-12-30
> **jasmine89 said:**
> Actually it's making Empty folders , without copying any things to it !!!
Yup...I've been experimenting with your script. I had a hard time trying to understand exactly what you were trying to do with it based on my interpretation of your description.
So...if you would kindly indulge me putting it into different words, are you wanting it to do something like this:

Copy files from a directory (e.g. Folders) into another directory (e.g. files/folder1) as long as the total size of files/folder1 has not exceeded a certain limit (e.g. 2000). When files/folder1 has been filled, then continue copying into a new directory (e.g. files/folder2) until files/folder2 has been filled, based on the specified limit, and continue copying into another new directory (e.g. files/folder3) and so on, until all the files in the source directory (e.g. Folders) have been copied?

Is that right?

---

### Post by Crusty Old Fart on 2010-12-30
> **jasmine89 said:**
> Actually it's making Empty folders , without copying any things to it !!!
Yep...and it also does a lot of other weird stuff. So, rather than trying to fix it line by line, character by character, I made several assumptions (always dangerous) as to what you wanted it to do and rewrote it.
The version in the code box below has the following features:


[LIST]
[*]It is tolerant of white spaces in file and folder names.
[*]It doesn't parse output from the ls command to determine file sizes. Instead, it uses the stat command, which is far more reliable and accurate than what is given by the ls command, and the aggregate size is accounted for in number of bytes as the script runs.
[*]It doesn't create unnecessary files, like r, s, and val to store temporary values needed by the script. Instead, it uses one array, named r, for the source file names.
[*]Calling syntax is very similar to what your original script wanted (i.e.: ./test.sh -s Folder 2000) however, the size parameter is taken as being specified in kilobytes. We can change this to whatever you want. I chose kilobytes to make it easy to test the script. Keep in mind that one kilobyte is 1024 bytes, one megabyte is 1024 kilobytes, and one gigabyte is (1024*1024) kilobytes. So, if you wanted to limit the size of each folder to what a 2 gigabyte thumb drive could hold, the size parameter for this version of the script would be 2097152 (2*1024*1024) and it could be called as follows: ./test.sh -s Folder 2097152
[/LIST]

```

#!/bin/bash
set -e

if [[ $1 == "-s" ]]; then
  (( size_limit = $3 * 1024 ))
  i=1
  declare -a r=($(ls "$2" -1))
  for j in ${r
[*]}; do
    (( file_size = $(stat --printf="%s" "$2/$j") ))
    if (( ($size + $file_size) < $size_limit )); then
      mkdir -p files/file$i
      cp "$2/$j" files/file$i
      (( size = $size + $file_size ))
    elif (( $file_size < $size_limit )); then
      (( i++ ))
      mkdir -p files/file$i
      cp "$2/$j" files/file$i
      (( size = $file_size ))
    else
      echo -e "\nThe size of the file named $j exceeds the specified"
      echo -e "limit for folder capacity. It was not copied.\n"
    fi
  done
else
  echo -e "\nMissing -s option when calling script -- execution aborted.\n"
fi

exit 0


```If you have any problems with it, would like something explained, or would like some help hacking it, please feel free to ask.

Have fun,

Crusty

---

### Post by jasmine89 on 2010-12-31
thanks a lot for your help Mr.[Crusty]("http://ubuntuforums.org/member.php?u=1173753")
Actually i want a script that gives me in the end a number of folders each one size is equal
 to the given size in the command line ... every folder contains files their total size doesn't exceed 
the given size .... sorry if my explanation is not clear ... 
to be honest , There's a lot of tokens in your code i couldn't  understand just like
set -e
state 
and the why you are making folders in the if and its else?!! 
I just make a new folder when the old one is Full (i mean the files total size is equal to the give size)
then make a new folder and start copying the files  ...  etc

---

### Post by Crusty Old Fart on 2010-12-31
> **jasmine89 said:**
> thanks a lot for your help Mr.[Crusty]("http://ubuntuforums.org/member.php?u=1173753")...
You're mighty welcome, Ms. Jasmine. :cool:
> **jasmine89 said:**
> 
Actually i want a script that gives me in the end a number of folders each one size is equal
 to the given size in the command line ... every folder contains files their total size doesn't exceed 
the given size .... sorry if my explanation is not clear ... 

Yup...that's _exactly_ what the script does. Evidently your initial explanation was clear enough.
> **jasmine89 said:**
> 
to be honest , There's a lot of tokens in your code i couldn't  understand just like
set -e
state 

The set -e command causes the script to abort on the first error it encounters. It is very helpful when developing code and, in my opinion, should remain in the script whenever possible. The following quote is the content of a posting about set -e that I made some time ago on another thread.

> **Crusty Old Fart said:**
> Here's something I highly recommend that can really save your tail.
```

#!/bin/bash
**[COLOR=Red]set -e[/COLOR]**

```The line in **[COLOR=Red]red[/COLOR]** above will cause your script to abort on its first error. The best place to put it is directly beneath #!/bin/bash.

Sometimes, you can make a simple typo in a script and it can end up throwing all sorts of really wild commands at the shell that end up trying to be executed. God only knows how badly this can mess up a system. There's no UNDO in the shell. If it gets a tsunami of crap code thrown at it, you can't take anything back that it executes.

If someone were to ask me: What is the most important script command that every newbie should learn?...This one would be my answer.

Beyond that, I would recommend they learn as much as they can about grep, sed, awk, and regular expressions (regex).

Have fun.

I'm assuming that when you mentioned "state", you may have intended to write "stat". The "stat" command displays file or file system status. The --printf option was used in my script with the file format sequence: "%s", which gives us the size of the file under consideration in bytes. You can learn more about the "stat" command from its manpages by entering the following commands:
```

man stat
man 2 stat

```> **jasmine89 said:**
> 
and the why you are making folders in the if and its else?!! 
I just make a new folder when the old one is Full (i mean the files total size is equal to the give size)
then make a new folder and start copying the files  ...  etc
Yup...my script is doing the same thing. However, it's creating the folders within the construct of an if statement in order to check to make sure there is enough room left in the current folder to hold the next file to be copied. Secondly, if there is not enough room for it, then before copying it to a **new** empty folder, the size of the file is checked to make sure it will fit in it. This second check prevents the script from copying a file that is bigger than the entire storage space allowed for a new, empty folder.

Perhaps it would help to break apart the if construct and explain what is happening. Here is the construct of the if statement:
```

[COLOR=Green][B]    if (( ($size + $file_size) < $size_limit )); then
      mkdir -p files/file$i
      cp "$2/$j" files/file$i
      (( size = $size + $file_size ))[/B][/COLOR]
[COLOR=Blue][B]    elif (( $file_size < $size_limit )); then
      (( i++ ))
      mkdir -p files/file$i
      cp "$2/$j" files/file$i
      (( size = $file_size ))
[/B][/COLOR][COLOR=Red][B]    else
      echo -e "\nThe size of the file named $j exceeds the specified"
      echo -e "limit for folder capacity. It was not copied.\n"[/B][/COLOR][B]
    fi[/B]

```There are three important variables used to assure that we don't exceed the disk storage space that we are specifying for our folders. They are defined as follows:

[LIST=1]
[*]**size** is the amount of disk storage space, within the current folder, that has already been used.
[*]**file_size** is the size of the file that is currently being considered for copying.
[*]**size_limit** is the maximum disk storage space we have allowed for each of our folders when we invoked the script.
[/LIST]
Now let's look at the green lines of the if construct:
```
[COLOR=Green][B]   if (( ($size + $file_size) < $size_limit )); then
      mkdir -p files/file$i
      cp "$2/$j" files/file$i
      (( size = $size + $file_size ))[/B][/COLOR]
```In this section of code, the first line checks to see if there is enough room in our current folder to hold the file we want to copy into it. If the file will fit, then the rest of the green lines are executed as follows:

[LIST]
[*]The second line creates a folder and its parent if they don't yet exist.
[*]The third line copies our file into the current folder.
[*]The fourth line updates the amount of storage space that has been used in the folder after we have copied our current file into it.
[*]Finally, further execution of the if construct will skip over the blue and red lines and jump to its end, and thereby start the next lap around the parent **for loop**.
[/LIST]
 If there isn't enough room for our file to fit in the folder, execution of the script will jump over all but the first of the green lines and begin executing the section of code shown in blue below: 
```
[COLOR=Blue][B]    elif (( $file_size < $size_limit )); then
      (( i++ ))
      mkdir -p files/file$i
      cp "$2/$j" files/file$i
      (( size = $file_size ))[/B][/COLOR]
```The code shown above gets executed when our file is too big to fit into the current folder. So, we'll need to put it into a new folder _if we can_. But, what  if the file is so large that it won't fit into a brand new empty  folder. For example, suppose the size of our folders has been limited to  what would fit on a 2 gigabyte thumb drive, and the file we're wanting  to copy is 3 gigabytes in size. Clearly we don't want to copy this file. The elif section checks for this  condition. In this section of code, the first line checks to see if the file will fit into a brand new empty folder. If it will, then the rest of the blue lines are executed as follows:

[LIST]
[*]The second line increments the folder counter (**i**) so that our new folder will be named correctly.
[*]The third line creates our new folder.
[*]The fourth line copies our file into our new folder.
[*]The fifth line updates the amount of storage space that has been used in the folder after we have copied our current file into it.
[*]Finally, further execution of the elif construct will skip over the red lines and jump to the end of the if construct, and thereby start the next lap around  the parent **for loop**.
[/LIST]
In the event that the file we wanted to copy was too large for a new, empty folder, execution  of the script will jump over all but the first of the blue lines and begin executing the section of code shown in red below:
```
[B][COLOR=Red]    else
      echo -e "\nThe size of the file named $j exceeds the specified"
      echo -e "limit for folder capacity. It was not copied.\n"[/COLOR][/B]
```The red code does nothing more than send a message to the shell that lets us know our file was too big and was not copied. After the message has been sent, the end of the if construct is reached and another lap around the parent **for loop** is started.

I hope I've been able to explain all of this well enough for you to get a better understanding of what these parts of the script are doing.

If you have any further questions, I'd be happy to try to answer them.

Best wishes to you for a happy, healthy, and prosperous New Year,

Crusty

---

### Post by Crusty Old Fart on 2011-01-01
> **jasmine89 said:**
> ...to be honest , There's a lot of tokens in your code i couldn't  understand...

Sorry about that. I've gone back and made several improvements to my script to increase efficiency and remove statements containing tokens that may be foreign to you. I've also edited my posts #5 and #7 to make them consistent with the changes made to my script.

Hopefully, this will make things easier for you to understand.

As I was working on this stuff, and studying your original script again, I began to question the approach I've been taking to helping you out. When I first began testing your script and fixing errors, each time I fixed something, it allowed the script to run a little further before it crashed on a lower layer of errors that had been allowed to surface. I found so much wrong, and spent so much time finding it that I got frustrated before I finished fixing it. So, I decided the best way to help was to start from scratch and write a new script that would do what you wanted it to. Now that I've done that, I'm wondering whether or not it was such a good idea.

My programming style is quite a bit different than yours is, which makes it difficult for you to understand what I've coded. It seems to me, from what you've written in your posts, that you aren't able to understand my script well enough to trust that you could safely run it. If that's the case, then you are smart to be cautious about running code that you don't understand because it's risky to blindly trust that it won't do something malicious to your computer. So, that's good. What isn't so good is the fact that as long as I continue to write code that you can't understand or trust, then I'm not really helping you at all.

With this in mind, I think I should approach this problem a little differently. I've spent some more time studying your script and have been thinking about how I could guide you through making the changes it needs to make it work. There are several of them and they will require us to post back and forth until we finish, especially if we make changes with the intention that you fully understand them as we go. Perhaps that would be much more help to you since we would be starting with something that you had coded in your own style. During this process, I may show you better ways to do some things, as well as teach you some new tricks. When I look at your script, I see, embodied in the code you have written, a reflection of you that suggests you are trying very hard to make it work, are becoming increasingly frustrated and confused, but have continued trying everything you can think of to make it run. I congratulate you for your persistence and would like to help you in a way that is best for you.

So, I'm offering you a couple of options:

[LIST=1]
[*]If you want a script that will run right now, you can use the one I wrote. That might get you out of an immediate jam, but it probably won't do much to make you a better programmer.
[*]On the other hand, if you aren't in a big hurry, and you'd like to turn this into a meaningful learning experience, I'd be happy to guide you through hacking what you have written, make changes gradually, and take the time we need to make sure you acquire a full understanding of what we're doing as we work on it. If you like this idea better, are willing to learn, and have patience with yourself, I believe you will become a much better programmer as a result. Perhaps so much better that getting your script to run will feel more like a secondary bonus when compared to the improvement you may experience in your coding skill.
[/LIST]
So, what say you, Ms. Jasmine? :cool:

Respectfully,

Crusty

---

### Post by jasmine89 on 2011-01-02
Thanks so much for your great explanation, I think that you have  made all your code clear and that's enough for me 
Wish you a very lovely new year full of happiness and empty of "BUGS" ;)
Actually I appreciate your offer but I'm having the middle-term exams now 
that's my e-mail : [email]jasmine_442002@hotmail.com[/email]

---

### Post by Crusty Old Fart on 2011-01-02
> **jasmine89 said:**
> Thanks so much for your great explanation, I think that you have  made all your code clear and that's enough for me 
Wish you a very lovely new year full of happiness and empty of "BUGS" ;)
Actually I appreciate your offer but I'm having the middle-term exams now 
that's my e-mail : [EMAIL="jasmine_442002@hotmail.com"]jasmine_442002@hotmail.com[/EMAIL]
You're mighty welcome. I'm glad that my explanation cleared things up for you rather than adding confusion. I wish you a wonderful new year as well. However, mine will not be empty of "BUGS" because I deliberately go looking for them, hunt them down, and do my best to flatten the pesky little critters. These forums provide a target rich environment for bug-busters. :cool:

Wishing you the best of luck on your mid-terms,

Crusty

---

