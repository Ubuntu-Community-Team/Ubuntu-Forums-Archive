---
title: "Move Multiple Files in multiple folder into one"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by Jundy on 2011-01-12
Hi,

I made a long research into getting a command to move all contents of sub_folders into one folder: e.g:

Folder1.xx 
Folder2.xx
Folder3.xx

Each of the above folder contains one file ee_001.r ee_002.r and so on respectively.

I have tried the following commands:
mmv -r "fo*/ee*" "~/Downloads/"

I was inside the directory of all folders then run the following:
find -name "*.xx" -exec mv {} ~/Downloads/

mv *.xx/*. ~./Downloads


None of the above worked,

How can I move the contents of each folder into the Downloads folder ?

Please help me form a command line

Regards,
Jundy

---

### Post by bikodog on 2011-01-12
> **Jundy said:**
> Hi,

I made a long research into getting a command to move all contents of sub_folders into one folder: e.g:

Folder1.xx 
Folder2.xx
Folder3.xx

Each of the above folder contains one file ee_001.r ee_002.r and so on respectively.

I have tried the following commands:
mmv -r "fo*/ee*" "~/Downloads/"

I was inside the directory of all folders then run the following:
find -name "*.xx" -exec mv {} ~/Downloads/

mv *.xx/*. ~./Downloads/


None of the above worked,

How can I move the contents of each folder into the Downloads folder ?

Please help me form a command line

Regards,
Jundy

see if this works

mv -vi Folder{1,2,3}.xx/* ~/Downloads

***remember, the command line is case sensitive. If your directory name is "F"older, you have to capitalize the F

---

### Post by Jundy on 2011-01-12
> **bikodog said:**
> see if this works

mv -vi Folder{1,2,3}.xx/* ~/Downloads

***remember, the command line is case sensitive. If your directory name is "F"older, you have to capitalize the F

thanks for your feedback.

but I have over 100 folders :)

Do i need to type in {1,2,3,4...etc } ???

---

### Post by bikodog on 2011-01-12
> **Jundy said:**
> thanks for your feedback.

but I have over 100 folders :)

Do i need to type in {1,2,3,4...etc } ???

no in that case, just try using the *

Folders*/*

Also, the -v and -i options are my preference whenever using the mv command (simplified by -vi).

-v = verbose output, so that you can see the files being moved
-i = prompt before overwriting files, so that you can avoid loosing something important :)

---

### Post by nothingspecial on 2011-01-12
> **Jundy said:**
> Hi,

I made a long research into getting a command to move all contents of sub_folders into one folder: e.g:

Folder1.xx 
Folder2.xx
Folder3.xx

Each of the above folder contains one file ee_001.r ee_002.r and so on respectively.

I have tried the following commands:
mmv -r "fo*/ee*" "~/Downloads/"

I was inside the directory of all folders then run the following:
find -name "*.xx" -exec mv {} ~/Downloads/

mv *.xx/*. ~./Downloads


None of the above worked,

How can I move the contents of each folder into the Downloads folder ?

Please help me form a command line

Regards,
Jundy

Try this 

```
cd parent_directory
```That is the folder containing all the other folders. If I understand you correctly , you want to move every file in all those folders to your Downloads directory. If this is the case, you don`t have to worry about the name.

```
find ./ -type f -exec mv '{}' ~/Downloads \;
```[SIZE=3][COLOR=Red]DO NOT DO THAT FROM YOUR /home/username OR YOU WILL TOAST YOUR SETUP[/COLOR][/SIZE]

[SIZE=5][COLOR=Red]AND REALLY REALLY DO NOT DO THAT FROM / AS ROOT OTHERWISE IT`S GOODBYE SYSTEM - TIME TO REINSTALL!

[SIZE=2][COLOR=Black]In fact, you would do well to take sisco311`s advice later on in this thread

[/COLOR][/SIZE][/COLOR][/SIZE]> **sisco311 said:**
> When you test a new script/command you can use **echo** to print the possibly dangerous commands first instead of executing them:
```
find ./ -type f -exec **echo** mv -- '{}' "/path/to/new/dir" \;
```or
```
for file in folder*/*; do
  if [ -f "$file" ]; then
    **echo** mv -- "$file" "/path/to/new/dir"
  fi
done
```

---

### Post by Jundy on 2011-01-12
> **bikodog said:**
> no in that case, just try using the *

Folders*/*

Also, the -v and -i options are my preference whenever using the mv command (simplified by -vi).

-v = verbose output, so that you can see the files being moved
-i = prompt before overwriting files, so that you can avoid loosing something important :)

COOL,

cannot stat `Folder*/*': No such file or directory

When I do ls, the Folder all in red color is this normal ?

---

### Post by Jundy on 2011-01-12
Thanks _nothingspecial that worked_

but it moved for me the folders with their contents :(

I just wanted the contents and not the folders

---

### Post by nothingspecial on 2011-01-12
Again, use sisco311`s advice before you carry out the any of the commands

> **sisco311 said:**
> When you test a new script/command you can use **echo** to print the possibly dangerous commands first instead of executing them:
```
find ./ -type f -exec **echo** mv -- '{}' "/path/to/new/dir" \;
```or
```
for file in folder*/*; do
  if [ -f "$file" ]; then
    **echo** mv -- "$file" "/path/to/new/dir"
  fi
done
```

Shouldn`t have done, copy and paste this, assuming all the folders are now in you ~/Downloads directory

```
cd ~/Downloads
find ./ -type f -exec mv '{}' ./ \;
```Then if to remove the empty directories

```
find -type d -empty 
```If the result of that only returns the directories you want to remove, then

```
find -type d -empty -exec rmdir '{}' \;
```

---

### Post by nothingspecial on 2011-01-12
Of course you may have to run the last one a few times because it will only remove the bottom level directories. I`m sure you can remove them all but I have to go. I`ll think on a one liner to do that.

---

### Post by Jundy on 2011-01-12
well thanks for the warning in red, 

I think I just (F_up) my system :(

I ignored your warning because I didn't understand it.

Ah well Is there a way to undo ?

I moved 100s of files I have no idea what they are :(

I think I need to re_install Ubuntu again :(

well its a test env, 

thank any way for your help, at least I learn from my mistake, 

Note: for future ref please let me know what do you mean try it not from /home/username

---

### Post by nothingspecial on 2011-01-12
Oh c**p

Thank god it was a test environment. I did my best to warn you, I`m sorry you didn`t understand it.

```
find ./ -type f -exec mv '{}' ./ \;
```I`ll explain the command

find ./ means find everything in this directory that I`m in and all it`s subdirectories

- type f means only files, not directories

-exec mv means move 

'{}' represents the files find has found

./ means this directory

\; ends the command

So you`ve moved every single file in your home, including all your settings out of their directories and into your home folder.




If you`ve done that from your home directory, your setup, but not your system is hosed. You can create a new user and remove the old one without the need to reinstall.

If you don`t wish to reinstall, boot into recovery mode > root shell and type
```

 adduser bob 
```

```
adduser bob admin
```
```

exit
```

You will now have a new admin account with which you can use your existing system.

I`m really sorry about this. I`m on the move at the moment, if you would like more detailed advice on how to fix your system post back, but I may or may not be able to reply for a few hours.

---

### Post by Jundy on 2011-01-12
Thank you very much, no harm is done. I just finished updating the new OS again.

Well its a powerful command this exec is :P

very useful information and thanks again for details.

I learned many new things in Linux (today) won't forget. One of them, never me in root or root user for simple testing \0/

until next time.
Regards,
J

---

### Post by sisco311 on 2011-01-12
When you test a new script/command you can use **echo** to print the possibly dangerous commands first instead of executing them:
```
find ./ -type f -exec **echo** mv -- '{}' "/path/to/new/dir" \;
```
or
```
for file in folder*/*; do
  if [ -f "$file" ]; then
    **echo** mv -- "$file" "/path/to/new/dir"
  fi
done
```

---

### Post by nothingspecial on 2011-01-12
> **sisco311 said:**
> When you test a new script/command you can use **echo** to print the possibly dangerous commands first instead of executing them:
```
find ./ -type f -exec **echo** mv -- '{}' "/path/to/new/dir" \;
```or
```
for file in folder*/*; do
  if [ -f "$file" ]; then
    **echo** mv -- "$file" "/path/to/new/dir"
  fi
done
```


Thanks sisco, I`ve quoted you in my previous posts so if this doesn`t happen again.

---

### Post by nothingspecial on 2011-01-12
> **Jundy said:**
> Thank you very much, no harm is done. I just finished updating the new OS again.

Well its a powerful command this exec is :P

very useful information and thanks again for details.

I learned many new things in Linux (today) won't forget. One of them, never me in root or root user for simple testing \0/

until next time.
Regards,
J

Thanks for taking this so well, and using it as a learning exercise.

This sort of thing is kind of what I mean by my sig, in that the shell won`t ask you if your sure, it will just do it.

---

### Post by Jundy on 2011-01-12
> **nothingspecial said:**
> Thanks for taking this so well, and using it as a learning exercise.

This sort of thing is kind of what I mean by my sig, in that the shell won`t ask you if your sure, it will just do it.

I agree, the red hat expert in our team told me exactly the same thing. 

I thought  OK at first then I read your sig and said to myself I need to remember that then. 

It seems every Linux user must always tattoo this sentence to their Brain. 

Thanks for the above info. Very useful.

Well its time to learn pipe, other commands and other useful ~ usage.

Will open up new topics in future in case I stuck :)
Regards,
J

---

