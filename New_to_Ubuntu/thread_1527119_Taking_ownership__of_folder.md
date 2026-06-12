---
title: "Taking ownership  of folder"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by sparker1 on 2010-07-08
Hello, I am trying to add an image to the usr/share/images/grub folder for a bit more eye candy. However, if I try and use cp or mv to shift the image from my home folder I get no such directory. If I try and use  sudo su I get unknown id:mv or unknown id:cp. I don't have permissions for just "sudo". What am I doing wrong?
This is the full command I was using:
sudo su mv /sparker/Downloads/Isle of mann /usr/share/images/grub
Unknown id: mv
I know it will be something dumb - that is the kind of day I am having.

---

### Post by Yarui on 2010-07-08
When you say you don't have permission to use sudo, do you mean that you are using an account on someone else's computer and you haven't been given the privilege to use sudo?  If it is on your own computer, you should be able to use sudo.

---

### Post by Yarui on 2010-07-08
EDIT:This post was totally pointless and probably totally wrong.

---

### Post by marshmallow1304 on 2010-07-08
So you're typing
```
sudo su cp ...
sudo su mv ...
```

You're basically telling su that you want to change to a user named cp or mv, neither of which exists.  There is no need to use 'su' in this case.

```
sudo cp ...
sudo mv ...
```

---

### Post by jms1989 on 2010-07-08
try this: sudo mv /sparker/Downloads/"Isle of mann" /usr/share/images/grub

You shouldn't include spaces in your directory commands like the one above, use escape characters like the back slash \ or enclose the directory name in parentheses. Btw, I recommend renaming it to exclude the spaces because it could cause some grub errors or replace the space with hyphens.

---

### Post by kingbirdy on 2010-07-08
try this instead:
```

sudo mv /sparker/Downloads/Isle\ of\ mann /usr/share/images/grub
```
You don't need sudo su, and you need to escape the spaces in the file name.

---

### Post by Yarui on 2010-07-08
He said that he isn't allowed to use sudo, but maybe the way he said that is just misleading.  I am unsure why he wouldn't be allowed to use sudo, but could still use sudo in the way he is describing.

---

### Post by stmiller on 2010-07-08
>  I don't have permissions for just "sudo". What am I doing wrong?

What happens when you do sudo command. For example:

```

sudo apt-get update

```

---

### Post by sparker1 on 2010-07-08
Thanks. sudo update-get works OK. The file usr/share/images/grub tells me I can't change permissions when I click on file properties. I have tried all the commands and here is what I get:
sparker@angry1:~$ sudo mv home/sparker/Downloads/"Isle of mann" /usr/share/images/grub
mv: cannot stat `home/sparker/Downloads/Isle of mann': No such file or directory
sparker@angry1:~$ sudo mv /sparker/Downloads/Isle\ of\ mann /usr/share/images/grub
mv: cannot stat `/sparker/Downloads/Isle of mann': No such file or directory
sparker@angry1:~$ sudo mv /sparker/Downloads/"Isle of mann" /usr/share/images/grub
mv: cannot stat `/sparker/Downloads/Isle of mann': No such file or directory

I know there is a file (Isle of Mann.tga) and I have copied and pasted its location at /home/sparker/Downloads. 
all the punctuation seems OK. Damn, I know it is something simple.

---

### Post by jms1989 on 2010-07-08
try sudo mv ~/Downloads/"Isle of mann" /usr/share/images/grub

---

### Post by Yarui on 2010-07-08
Try typing
```
sudo mv ~/Downloads/'Isle of mann' /usr/share/images/grub
```
~ is your home directory. The problem is that there is no /sparker or home/sparker because /sparker would be a folder in the root directory / and home/sparker would be a folder in your working directory, which is most likely your home directory, so
```
sudo mv Downloads/'Isle of mann' /usr/share/images/grub
```
would likely work equally well.

---

### Post by sparker1 on 2010-07-09
Thanks JMS1989. I keep getting no such file or directory. - mv: cannot stat `/home/sparker/Downloads/Isle of mann': No such file or directory
I've wasted enough of everyone's time for what is some stupid error I am overlooking somewhere. Thanks for trying everyone. I'll let you know what was wrong when i finally fix it.

---

### Post by Yarui on 2010-07-09
You can try autocomplete, that assures you are typing in an existing directory.  Just type ~/Dow and then hit tab, it will autocomplete to ~/Downloads, then extend it to ~/Downloads/Isl and hit tab and it will probably autocomplete to the name of the folder.  If it doesn't hit tab 2-3 more times and it should give you a list of files and folders that match up to the point you have typed.  If it does nothing then there is no matching file or folder at all.

If that doesn't find the file, try finding it in nautilus and you should be able to look at the directory name and enter it into the terminal to do what you want.

---

### Post by sparker1 on 2010-07-09
You are a patient person Yarui. Here is what I got (i've shortened the file to mann.tga):
sparker@angry1:~$ ~/Downloads
bash: /home/sparker/Downloads: is a directory
sparker@angry1:~$ ~/Downloads/mann
bash: /home/sparker/Downloads/mann: No such file or directory
sparker@angry1:~$ ~/Downloads/mann.tga
bash: /home/sparker/Downloads/mann.tga: Permission denied
sparker@angry1:~$ sudo ~/Downloads/mann.tga
sudo: /home/sparker/Downloads/mann.tga: command not found

I have shifted the original file with nautilus but still trying to fathom where I'm going wrong.
here is what is in that directoryfrom ls command
sparker@angry1:~$ ls Downloads
3e29963e7dfb75d1.zip
ati-driver-installer-9-3-x86.x86_64.run
Feedback information.docx
fglrx-install.yqEKSq
Health Sciences Information Evening.pdf
mann.tga

---

### Post by da burger on 2010-07-09
For the purposes of a sanity test:
Open up nautilus and navigate to your downloads folder.
In a terminal type in sudo mv (don't press enter yet).
Drag the file onto the terminal window, this will automatiaclly fill in the absolute path (still don't press enter)
Finally type in the target directory (or drag and drop that as well) and press enter.

That method will give you the perfect command that you can compare to yours. If that doesn't work then there is a bigger problem.

---

### Post by sparker1 on 2010-07-09
I was looking at the permissions for the Downloads directory. My permissions are "create and delete files for folder access but "file access" has just three dashes. If I try and add "read and write" it just goes back to 3 dashses. There is also a note on the "Basic" radio button that some contents are unreadable. I guess therein lies my problem.

---

### Post by sparker1 on 2010-07-09
DA BURGER!!!!! that worked. I'll be damned. Oh, and a big thank you too.

---

### Post by 3rdalbum on 2010-07-09
the   drag   and   drop   suggestion   was   good.   You   also   could have   opened   the   Nautilus   file   browser   as   root   by   typing:

gksudo   nautilus

then   you   can  just   use   that   window   to  copy   the   files   and  you  have   permission.

---

### Post by sparker1 on 2010-07-09
3rdalbum, I agree it was good. I didn't know you could do that. I did do the nautilus thing earlier but I was trying to find out where I went wrong in the mv command. I noticed that when I did the drop thing the whole command was in quotes.

---

### Post by Yarui on 2010-07-09
The reason you got a command not found output from
```
sparker@angry1:~$ sudo ~/Downloads/mann.tga
```is because you forgot to do the mv command.  The way you did it here it tried to run mann.tga as an executable script, which it is not.  You seem to have a little bit of trouble understanding the Linux command line, so I will give you some tips on the basics that you seem to have had a bit of trouble with here.

- The folder you are currently in is known as the working directory.  By default your working directory is your /home/user folder, which I have already told you is represented by ~.  You can see your working directory after your terminal name and followed by the $ symbol.  In the above sample it is your home directory ~.  If you change directories with the cd command to /usr/local, for example, the line will read
```
sparker@angry1:/usr/local$
```- If you enter a file name and nothing else, that file will be run in the command line.

- Your working directory is represented by a period.  If you want to run a program that is in your current working directory called prog1 you would use the command
```
./prog1
```to denote that you are running the program from your current directory.  This isn't always necessary, but sometimes it is so it's best to get used to doing it all the time.

- Using sudo before a command elevates you to root privileges for that single command.  Use sudo any time you don't have permission to do something you want to do.

I think these are the main things you seem to have had trouble with in this thread, but if you have any questions about anything else, feel free to ask.  You may have already figured all of this out by now, but I thought I should clarify just to make sure you understand why you were having trouble.

---

### Post by sparker1 on 2010-07-09
*"You seem to have a little bit of trouble understanding the Linux  command line". *Whatever makes you think that, heh, heh. Nice understatement Yarui. I apologise for being a noob but I am trying to learn. If anybody is interested here is my command that goes awry:
[COLOR=Blue]sudo mv /home/sparker/Downloads/Spark /usr/share/images/grub[/COLOR]
and this is the good one:
[COLOR=Blue]sudo mv '/home/sparker/Downloads/Spark.tga' /usr/share/images/grub[/COLOR]
If I put the full file name or maybe use quotes I'm OK. I am now having a great time moving files all over the place. thanks to all who tried to help.

---

### Post by BikeHelmet on 2010-07-09
Missing the extension was what caused most of your woes.

For future reference, the terminal has tab auto-completion.

Need to copy file **SomeStrangeNameHere**?

Type in **So** and press tab. If there's no other files, you get the full name. If there are other files (like **SomeStrangeOtherName**), then you get **SomeStrange**. Type in **Na** and press tab again, to get **SomeStrangeNameHere**.

Try it out. It solves a lot of spelling mistake grief. :p

---

### Post by sparker1 on 2010-07-09
> **BikeHelmet said:**
> Missing the extension was what caused most of your woes.

For future reference, the terminal has tab auto-completion.

Need to copy file **SomeStrangeNameHere**?

Type in **So** and press tab. If there's no other files, you get the full name. If there are other files (like **SomeStrangeOtherName**), then you get **SomeStrange**. Type in **Na** and press tab again, to get **SomeStrangeNameHere**.

Try it out. It solves a lot of spelling mistake grief. :p
Sounds like great advice. Thank you.

---

