---
title: "Shell script difficulties"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by Neoncamouflage on 2011-06-24
It has become a weekly chore for me to clean out my Downloads directory of all the .iso, .jpg, and .pdf files I've downloaded. There are others I clean out, but those three seem to make up the vast majority of what clutters it up. So I finally got the bright idea to try and make a script to organize them all. Only it seems I did so....poorly...

Here's the script:
```
#!/bin/bash

mv /home/chris/Downloads/"*.iso" /home/chris/Downloads/Disk_Images

mv /home/chris/Downloads/"*.pdf" /home/chris/Documents/Ebooks

mv /home/chris/Downloads/"*.jpg" /home/chris/Pictures/To_Be_Sorted
```

Now I won't lie, I have no idea why this isn't working. It's supposed to move all files in Downloads that end in .iso/pdf/jpg to their specific sections.

This is the result when I try to run it:
```
mv: cannot stat `/home/chris/Downloads/*.iso': No such file or directory
mv: cannot stat `/home/chris/Downloads/*.pdf': No such file or directory
mv: cannot stat `/home/chris/Downloads/*.jpg': No such file or directory

```

I'll assume it's failing because it can't locate the specified files, but they are in there, and isn't "*.jpg" supposed to mean every combination of letters/numbers, and then .jpg?

Thanks in advance for the help, believe this is a case where a scripting newbie is trying something waaaay over his head.

---

### Post by s1baker on 2011-06-24
might look at the directory names, make sure the caps/no caps  are correct

---

### Post by ClientAlive on 2011-06-24
> **Neoncamouflage said:**
> It has become a weekly chore for me to clean out my Downloads directory of all the .iso, .jpg, and .pdf files I've downloaded. There are others I clean out, but those three seem to make up the vast majority of what clutters it up. So I finally got the bright idea to try and make a script to organize them all. Only it seems I did so....poorly...

Here's the script:
```
#!/bin/bash

mv /home/chris/Downloads/"*.iso" /home/chris/Downloads/Disk_Images

mv /home/chris/Downloads/"*.pdf" /home/chris/Documents/Ebooks

mv /home/chris/Downloads/"*.jpg" /home/chris/Pictures/To_Be_Sorted
```

Now I won't lie, I have no idea why this isn't working. It's supposed to move all files in Downloads that end in .iso/pdf/jpg to their specific sections.

This is the result when I try to run it:
```
mv: cannot stat `/home/chris/Downloads/*.iso': No such file or directory
mv: cannot stat `/home/chris/Downloads/*.pdf': No such file or directory
mv: cannot stat `/home/chris/Downloads/*.jpg': No such file or directory

```

I'll assume it's failing because it can't locate the specified files, but they are in there, and isn't "*.jpg" supposed to mean every combination of letters/numbers, and then .jpg?

Thanks in advance for the help, believe this is a case where a scripting newbie is trying something waaaay over his head.


Take the quotes off. I just tried it with about a dozen txt files that I use in a practice learning directory called "cliPlayground" I moved them from one folder to another and it worked like a charm.
----------------------

Edit:

Moved em back too! Then deleted the "testmove" folder I used to try it out. Works fine like that - assuming everything else is correct (the path, case of letters, etc).

---

### Post by s1baker on 2011-06-24
also, should there be a "/" after the directory names?

---

### Post by Neoncamouflage on 2011-06-24
It was the quotes, I still get the error message if there's no files that need to be moved, but I don't care about that. Thanks a lot, I'm at the same time happy to know I did that much correctly, yet annoyed something so simple completely threw me off.

And I don't think the / after the directory is needed, it works fine without.

---

### Post by ClientAlive on 2011-06-24
> **Neoncamouflage said:**
> It was the quotes, I still get the error message if there's no files that need to be moved, but I don't care about that. Thanks a lot, I'm at the same time happy to know I did that much correctly, yet annoyed something so simple completely threw me off.

And I don't think the / after the directory is needed, it works fine without.


You might want to look into something called rsync. Check out the man page for it. If I'm not mistaken it can be used to do incremental backups so maybe you can incorporate it into your script or use it instead of the mv command so you don't get the error when there isn't anything in there. Just a thought.

Check me/ it first though. I'm just doing it from memory and not sure I'm recalling that right.

Gotta go. Got a host to clone into Virtual Box.

By the way, can you mark the thread solved so others can benefit?

Thanks.

Have a good one.

---

### Post by Neoncamouflage on 2011-06-24
Sounds interesting, I'll certainly look into it. Thanks once again for your help, marked it as solved.

---

### Post by bodhi.zazen on 2011-06-24
Well, just add a handler for errors

mv *.iso 2>/dev/null || echo 'no iso found'

Or you can use conditionals (if)

---

### Post by Neoncamouflage on 2011-06-24
I had never heard of "2>/dev/null" before, that's really cool. Thanks a lot. Now instead of an aggravating error message, I am politely informed that there are no files of that type to organize. :D

Just because this got me thinking, is there anything that will count how many files are being moved that I can then use echo to tell me? Like I would like to run it and get something like:

```
No .iso files found
5 .jpg files moved
13 .pdf files moved
```

---

### Post by CaptainMark on 2011-06-24
yes ```
#!/bin/bash

filecount=$(mv -v /home/chris/Downloads/*.iso /home/chris/Downloads/Disk_Images 2>/dev/null |wc -l) && echo "$filecount files moved" || echo "no files found"
```its a long one but still a good one liner, just add another line for the other directories

---

### Post by Neoncamouflage on 2011-06-24
> **CaptainMark said:**
> yes ```
#!/bin/bash

filecount=$(mv -v /home/chris/Downloads/*.iso /home/chris/Downloads/Disk_Images 2>/dev/null |wc -l) && echo "$filecount files moved" || echo "no files found"
```its a long one but still a good one liner, just add another line for the other directories

That worked well, thank you. The only thing is that the "|| echo 'no files found'" is never used, if there are no files in the Downloads directory then it simply prints out "0 .iso files moved", so I removed it from the code.

---

### Post by CaptainMark on 2011-06-24
damn thats irritating, i tested it earlier and i had it working but now i cant recreate it on one line, any errors get disregarded when the results of the  mv command get piped to the wc command so bash thinks the command gave no errors, you could do this with a simple if/else statement in a script but if it works for you thats cool but you could shorten it to ```
echo `mv -v $HOME/Downloads/*.iso $HOME/Downloads/Disk_Images recieve/ 2>/dev/null |wc -l` files moved
```seen as theres no need for the rest of it now

---

### Post by Neoncamouflage on 2011-06-24
Yeah, I figured it could be done with an if/else statement, but where I'm still getting into this I'm not terribly familiar with them. I really have no issue with how it is now, so I'm not about to stumble around code for three hours trying to change something that's not an issue. Maybe when I get further into scripting I'll go back and fix it, just for the sake of having it the way I originally pictured.

---

### Post by CaptainMark on 2011-06-24
okay thats cool, its always good to have one more bash fan around its an undervalued subject i think, 
your first homework assignment is....... get this on one line :P, im a fan of doing things in as short a code as possible,

---

### Post by Neoncamouflage on 2011-06-24
I plan on learning to script in bash and Python both, have done a bit of work in both of them, but I just prefer to learn bash first as it uses the same commands as I regularly use in the terminal. Makes it a little easier for me to grasp and so I learn better.

That I'm not entirely sure how to do, but now I have to try, wish me luck. :D

---

### Post by CaptainMark on 2011-06-24
definitley good luck, im in the same boat ive only just started picking it up and theres still plenty to learn, the best thing about learning bash is that its easy to put into practice, you can make a script to automate something your doing manually already, your only limited by what you can think up

---

### Post by Neoncamouflage on 2011-06-24
Success, at the expense of adding a couple lines of variables. Honestly, I count it as a win, as it still looks cleaner.
```
#!/bin/bash

Source=/home/chris/Downloads
Jpg=/home/chris/Pictures/To_Be_Sorted
Iso=/home/chris/Downloads/Disk_Images
Pdf=/home/chris/Documents/Ebooks

echo `mv -v $Source*.iso $Iso recieve/ 2>/dev/null |wc -l` .iso files moved

echo `mv -v $Source*.pdf $Pdf recieve/ 2>/dev/null |wc -l` .pdf files moved

echo `mv -v $Source*.jpg $Jpg recieve/ 2>/dev/null |wc -l` .jpg files moved
```

Yeah, it is really useful. That's where this came from, after manually moving a dozen files from Downloads to where they belong, I realized this is kind of exactly what scripts are made for. :P

---

### Post by CaptainMark on 2011-06-24
hey thats better still, haha im gonna resist the urge to clean it up even further, my geek side could take control for hours

oh yeah another tip i found out not too long ago, add a symbolic link to your /bin folder and you can call the script from anywhere using any command, so on my rig```
sudo ln -s $HOME/Documents/bash/homesync_1.21 /bin/homesync
```now all i need to do is type homesync in any terminal and my backup script will run, great time saver

---

### Post by Neoncamouflage on 2011-06-24
I added a path to my script directories in my .bash_aliases file.

```
PATH=$PATH:/home/chris/bin/shell_scripts
PATH=$PATH:/home/chris/bin/python_scripts

```

Where I keep all my scripts, keeps it a little more organized, since I tend to have several I'm messing around with at one time. The added paths let me call them from anywhere as well.

---

### Post by bodhi.zazen on 2011-06-24
> **CaptainMark said:**
> hey thats better still, haha im gonna resist the urge to clean it up even further, my geek side could take control for hours

oh yeah another tip i found out not too long ago, add a symbolic link to your /bin folder and you can call the script from anywhere using any command, so on my rig```
sudo ln -s $HOME/Documents/bash/homesync_1.21 /bin/homesync
```now all i need to do is type homesync in any terminal and my backup script will run, great time saver

You should put the script in ~/bin or if you want it available for all users /usr/local/bin

~/bin should be on your path , if it is not, add it to .bashrc

```
if [ -d $HOME/bin ]; then
PATH=$PATH:$HOME/bin
if
```

---

### Post by CaptainMark on 2011-06-24
cool yeah this does the same job, are you sure you havent done this before?

---

### Post by Neoncamouflage on 2011-06-24
Adding the path I found in a Python tutorial, only place I've seen mention it, but it's really nice I think. 

Also, I'm curious, how would you clean up that code further? I can't really think of anything to condense it some more.

---

### Post by CaptainMark on 2011-06-24
> **Neoncamouflage said:**
> I added a path to my script directories in my .bash_aliases file.

```
PATH=$PATH:/home/chris/bin/shell_scripts
PATH=$PATH:/home/chris/bin/python_scripts

```Where I keep all my scripts, keeps it a little more organized, since I tend to have several I'm messing around with at one time. The added paths let me call them from anywhere as well.does this work recursively too, i have lots of branches of directories to keep my bash scripts organised i could use this option if it is or does it only check for files directly in the folders youve listed

haha, i probably couldnt but that doesnt mean the urge to try isnt there

---

### Post by Neoncamouflage on 2011-06-24
I haven't found a way to get it to work recursively, that would be nice though. Like when I only had it specify my /bin file it wouldn't look inside /shell_scripts or /python_scripts. There may well be a way, I'll hunt through google in just a bit and see.

---

### Post by bodhi.zazen on 2011-06-24
```
PATH=${PATH}:$(find $HOME/bin -type d | tr '\n' ':' | sed 's/:$//')
```

---

### Post by Neoncamouflage on 2011-06-24
I'm going to assume that does it. :P

Works perfectly, even made extra directories inside my python_scripts directory and it ran scripts from them no problem. Thanks a ton man.

---

### Post by bodhi.zazen on 2011-06-24
> **Neoncamouflage said:**
> I'm going to assume that does it. :P

Works perfectly, even made extra directories inside my python_scripts directory and it ran scripts from them no problem. Thanks a ton man.

You are most welcome =)

---

### Post by CaptainMark on 2011-06-24
> **bodhi.zazen said:**
> ```
PATH=${PATH}:$(find $HOME/bin -type d | tr '\n' ':' | sed 's/:$//')
```
good one, does this just make a list and add it to $PATH or does it make and check a new list everytime bash searches $PATH in other words if you now add another directory would it still work or would you have to run the command again, im not being picky but just feeding my curiosity

---

### Post by Neoncamouflage on 2011-06-24
> **CaptainMark said:**
> good one, does this just make a list and add it to $PATH or does it make and check a new list everytime bash searches $PATH in other words if you now add another directory would it still work or would you have to run the command again, im not being picky but just feeding my curiosity

The command runs on startup if you put it in .bashrc or .bash_aliases or somewhere like that. If you make a directory and want to run scripts from it before rebooting, all you have to do is run the command again. Actually, you could even make a script or function for this alone, make it so that like every time you type in Path_Update it runs the command and adds any directories that you've created.

I doubt you'll be making them often enough to need that, but it's just a thought.

---

### Post by bodhi.zazen on 2011-06-24
> **CaptainMark said:**
> good one, does this just make a list and add it to $PATH or does it make and check a new list everytime bash searches $PATH in other words if you now add another directory would it still work or would you have to run the command again, im not being picky but just feeding my curiosity

If you run that command on the command line, it would be for the current shell.

If you wish to enable that for all shells , put it in ~/.bashrc

If you are interested in other bashrc tweaks, you can look at my envrc (those options are generic for bash or zshrc) and bashrc

[http://bodhizazen.net/Tutorials/envrc](http://bodhizazen.net/Tutorials/envrc)

[http://bodhizazen.net/Tutorials/bashrc](http://bodhizazen.net/Tutorials/bashrc)

Save those files as ~/.bashrc and ~/.envrc ;)

---

### Post by Neoncamouflage on 2011-06-24
Thanks for the links.

And yeah, I pasted the following code into my .bash_aliases file, now every time I do Update_Path it runs the code and detects all new directories. Just paste it in one of the .bash files if you're wanting to use it and then you don't have to reboot or type in the entire command whenever you add a new directory for scripts.

```
#Update function
function Update_Path(){
        PATH=${PATH}:$(find $HOME/bin -type d | tr '\n' ':' | sed 's/:$//')
}

```

---

### Post by bodhi.zazen on 2011-06-24
With what you are doing, I would hard code the default path, the update it.

```
#Update function function Update_Path()
{
         PATH='/bin:/sbin:/usr/bin:/usr/sbin'
         PATH=${PATH}:$(find $HOME/bin -type d | tr '\n' ':' | sed 's/:$//')
 }
```Keep your updated path from getting too long, and you can call Update_Path at the end of .bashrc

---

### Post by Neoncamouflage on 2011-06-24
Not 100% sure on what you mean there, but the way I have it set up is that .bash_aliases checks and runs that code automatically to update the path on every reboot, and then I added the function so that if I add a new directory I can run the update myself. I believe this is what you said, but I don't know. XD

Sorry, still new.

---

### Post by bodhi.zazen on 2011-06-24
> **Neoncamouflage said:**
> Not 100% sure on what you mean there, but the way I have it set up is that .bash_aliases checks and runs that code automatically to update the path on every reboot, and then I added the function so that if I add a new directory I can run the update myself. I believe this is what you said, but I don't know. XD

Sorry, still new.

Sorry, the code formatting was removed from my post, I added it back in.

By setting the path you keep all those directories from getting added in multiple times (if you update your path).

> # .bashrc

# <your other .bashrc stuff here, aliases, etc>

#Update function
function Update_Path()
 {          
        PATH='/bin:/sbin:/usr/bin:/usr/sbin'
        PATH=${PATH}:$(find $HOME/bin -type d | tr '\n' ':' | sed 's/:$//')  
 }

Update_Path

---

### Post by Neoncamouflage on 2011-06-24
Interestingly enough....that doesn't work...
I looked at what you were saying and noticed that it was adding them multiple times. I updated the code and ran the update function a couple times, now this is what I get from "echo $PATH":
```
/home/chris/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/chris/bin:/home/chris/bin/python_scripts:/home/chris/bin/python_scripts/ECHO:/home/chris/bin/shell_scripts:/home/chris/bin:/home/chris/bin/python_scripts:/home/chris/bin/python_scripts/ECHO:/home/chris/bin/shell_scripts:/home/chris/bin:/home/chris/bin/python_scripts:/home/chris/bin/python_scripts/ECHO:/home/chris/bin/shell_scripts:/home/chris/bin:/home/chris/bin/python_scripts:/home/chris/bin/python_scripts/ECHO:/home/chris/bin/shell_scripts

```

And every time I run the update it readds the ones that are already there....

Oh, and to top it off my script for cleaning up downloads actually doesn't work. Keeps telling me 0 files have been moved and doesn't move any of them. *sigh* I think it was my variables that were off, as it seemed to work fine before.
**EDIT** Not my variables, so it's the code for counting the files moved.

---

### Post by nothingspecial on 2011-06-24
It's the formatting problem......

.... I think.....

It should read



```
#Update function
function Update_Path()
{ 
PATH='/bin:/sbin:/usr/bin:/usr/sbin'
PATH=${PATH}:$(find $HOME/bin -type d | tr '\n' ':' | sed 's/:$//') 
}

Update_Path
```

The way it appears, as I read it on the forums, the first 2 lines are joined as one, so the function is never declared/defined (whatever the correct term is).

To explain (as far as I can),

You need this bit

```
function Update_Path()
```

on a seperate line, that tells bash to make a function that you can run by typing 

```
Update_Path
```

But it appears in the post on the same line as 

```
#Update function
```

The # at the beginning of the line tells bash to ignore it so the function is never {declared,defined}.

I stand here ready to be corrected........


.... but I don't care......

.... just trying to help :-\"  

and learn :)

---

### Post by Neoncamouflage on 2011-06-24
That isn't it, I caught that when I read it the first time and fixed it when I copied it into the file. Good try though, what I would have guessed as well.

---

### Post by bodhi.zazen on 2011-06-24
> **nothingspecial said:**
> It's the formatting problem......

.... I think.....

It should read



```
#Update function
function Update_Path()
{ 
PATH='/bin:/sbin:/usr/bin:/usr/sbin'
PATH=${PATH}:$(find $HOME/bin -type d | tr '\n' ':' | sed 's/:$//') 
}

Update_Path
```The way it appears, as I read it on the forums, the first 2 lines are joined as one, so the function is never declared/defined (whatever the correct term is).

To explain (as far as I can),

You need this bit

```
function Update_Path()
```on a seperate line, that tells bash to make a function that you can run by typing 

```
Update_Path
```But it appears in the post on the same line as 

```
#Update function
```The # at the beginning of the line tells bash to ignore it so the function is never {declared,defined}.

I stand here ready to be corrected........


.... but I don't care......

.... just trying to help :-\"  

and learn :)

Thanks , I edited my last post (again) :lolflag:

---

### Post by nothingspecial on 2011-06-24
> **bodhi.zazen said:**
> Thanks , I edited my last post (again) :lolflag:

:p

---

