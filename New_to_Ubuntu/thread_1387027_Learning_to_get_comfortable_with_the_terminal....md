---
title: "Learning to get comfortable with the terminal..."
date: 2010-01-21
forum: New to Ubuntu
---

### Post by hortstu on 2010-01-21
I've been using Ubuntu for a few months now and I'm using it just like windows.  I want to learn a little bit.  

The only things I do in the terminal so far are 
sudo apt-get update
sudo apt-get upgrade

That basically does the same thing as clicking on the little down arrow in the toolbar I assume since it always goes away after I do it.

What's the next step?

---

### Post by deadalus.globalnode on 2010-01-21
Next i would learn
sudo apt-get install <program name>

I also highly recomend getting use to using man pages.
Man pages give you a lot of information on a terminal command and just about anything else.
$man <terminal command here>
so
$man man
will give you information on how to use man pages. To exit just hit Q.

Using man pages I suggest you learn the basics about
cp
chmod
ls
rm
mkdir

Please let me know if I said anything that didn't make sense.

---

### Post by lykwydchykyn on 2010-01-21
[http://linuxcommand.org/](http://linuxcommand.org/)

^Good place to start^

---

### Post by stim on 2010-01-21
You may find this useful [http://mssaleh.wordpress.com/2008/05/10/command-line-alternatives-in-ubuntu-linux/]("http://mssaleh.wordpress.com/2008/05/10/command-line-alternatives-in-ubuntu-linux/")

You are on the right track. If you know a programming language, learn to program on linux.

---

### Post by jmszr on 2010-01-21
hortstu,

You may find this of use: [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

Also these are good to have: [http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/) and: [http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)

---

### Post by Grenage on 2010-01-21
> What's the next step?

Do as much in the terminal as you can; you won't know how to do most things, but web searches will get you there.  Only through constant use and experimentation will the knowledge stick.

It's the same with any new skill.

---

### Post by warfacegod on 2010-01-21
If you have the drive space you might consider installing a second OS. Use that one to experiment with. That way you'll have no worries about breaking your system because you won't be using your primary install. Creating dual boots also provides learning experiences in and of itself.

---

### Post by rotwang888 on 2010-01-21
Other basics are mv and cd.  Also apt-cache search "name of program". And I'll second linuxcommand.org .  Try spending a day or so forcing yourself to use the terminal to do all basic file stuff like deleting, moving something you just downloaded, etc.  You'll be forced to deal with things you didn't expect, like how to deal with spaces in file names. Also, experiment with using the tab key to auto-complete commands and file names.  You'll save a lot of typing.  Have fun!

---

### Post by steveneddy on 2010-01-21
Look at the links in my sig so you can get a better understanding of what the OS is capable of and if you see something that you are interested in, simply use the terminal commands that are listed for the function you would like to perform.

---

### Post by achase79 on 2010-01-21
I believe man is one of the most important program.  you can use man <command> to see how a terminal command works

---

### Post by hortstu on 2010-01-21
> **deadalus.globalnode said:**
> Next i would learn
sudo apt-get install <program name>

OK but the only way I know how to find programs is via the applications tab >add/remove.  Do you suggest I search for what I want there and then use the terminal to get it?

> I also highly recomend getting use to using man pages.
Man pages give you a lot of information on a terminal command and just about anything else.
$man <terminal command here>
so
$man man
will give you information on how to use man pages. To exit just hit Q.

Using man pages I suggest you learn the basics about
cp
chmod
ls
rm
mkdir

Please let me know if I said anything that didn't make sense.

Lots of what you said didn't make sense but I'll try $man man and then come back.

> **lykwydchykyn said:**
> [http://linuxcommand.org/](http://linuxcommand.org/)

^Good place to start^

Thanks

> **stim said:**
> You may find this useful [http://mssaleh.wordpress.com/2008/05/10/command-line-alternatives-in-ubuntu-linux/]("http://mssaleh.wordpress.com/2008/05/10/command-line-alternatives-in-ubuntu-linux/")

You are on the right track. If you know a programming language, learn to program on linux.


Yeah no programming here I'll check out the link though thanks.

> **jmszr said:**
> hortstu,

You may find this of use: [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

Also these are good to have: [http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/) and: [http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/4/ubuntu-cheat-sheet/)

Thanks

> **warfacegod said:**
> If you have the drive space you might consider installing a second OS. Use that one to experiment with. That way you'll have no worries about breaking your system because you won't be using your primary install. Creating dual boots also provides learning experiences in and of itself.

I currently have a dual boot with xp on my desktop.  I'm in the process of repairing an old laptop.  I plan to run just linux on it.  I was thinking of trying a dual boot with open SUSE and Hardy.

> **rotwang888 said:**
> Other basics are mv and cd.  Also apt-cache search "name of program". And I'll second linuxcommand.org .  Try spending a day or so forcing yourself to use the terminal to do all basic file stuff like deleting, moving something you just downloaded, etc.  You'll be forced to deal with things you didn't expect, like how to deal with spaces in file names. Also, experiment with using the tab key to auto-complete commands and file names.  You'll save a lot of typing.  Have fun!

Wow I wouldn't even know where to start with that stuff but it does sound like a good suggestion. I'll look into it.

> **achase79 said:**
> I believe man is one of the most important program.  you can use man <command> to see how a terminal command works

Thanks for all the replies.

I'll come back with questions I'm sure

---

### Post by deadalus.globalnode on 2010-01-21
Sorry if I was confusing.
First of all the $ sign means that it is a terminal command so

$man man

just means open a terminal and type 

man man

for the commands that I gave (and the ones I forgot to give that rotwang888 mentioned mv, and cd) earlier just use man pages to find out what they do. For example if you don't have any Idea what ls does just type

 man ls

Into your terminal.

---

### Post by hortstu on 2010-01-21
> **deadalus.globalnode said:**
> Sorry if I was confusing.
Firs of all the $ sign means that it is a terminal command so
$man man
just means open a terminal and type 
man man

About the commands I gave earlier:
ls - this shows the files and folders in your current directory

No apologies necessary.  You definitely helped.  I'll be back when I hit a wall.

---

### Post by warfacegod on 2010-01-21
Without Windows, not much point in walls either.

](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by nothingspecial on 2010-01-21
Think of something you do alot.

Such as playing music or veiwing photos, or converting videos (whatever).

Try and do it from the command line.

The most useful app I know of when trying to do things in the terminal is dvtm.
```

sudo apt-get install dvtm
dvtm
```

dvtm allows you to split your terminal into multiple windows.

So, once it is running press Ctrl-G then C

This will split your terminal into 2 windows

Type ```
man dvtm
```

This will display the dvtm man page in one window. Learn how to use dvtm with that man page.

Next time you find a command line app you want to learn how to use, launch dvtm and play with it while you can see the instructions in the other window.

---

### Post by The Cog on 2010-01-21
What they haven't mentioned is that when you look at the manual for a command, with a command like **man ls** , you have to quit with the Q key. It took me a while to find that.

I would suggest getting the hang of the commands:
**ls** - list directory contents (also **ls -l**)
**cd** - change directory - GUI users will find the idea of a "current working directory" rather alien.
**pwd** - print working directory for when you get lost
**cp** - copy a file from one place to another
**mv** - move a file from one place to another (or rename)
**cat** - type a file, e.g. **cat /etc/services**
**rm** - remove a file

The above were the basics I learned first. ALso useful:

**less** - shows file contents (scrollable), e.g. **less /etc/services**
**nano** - a simple file editor
Also learn piping from one command to another, e.g. **lshw | less**
**grep** is incredibly useful for searching text, e.g. **lspci | grep Network**

Beyond that, follow your curiosity. Getting comfortable with the command line takes time. But the power when you get used to it is awesome.

---

### Post by nothingspecial on 2010-01-21
> **The Cog said:**
> What they haven't mentioned is that when you look at the manual for a command, with a command like **man ls** , you have to quit with the Q key. It took me a while to find that.

Doesnt really matter in dvtm



> **less** - shows file contents (scrollable), e.g. **less /etc/services**

I love this forum, I`ve always piped (as you`ve mentioned) cat through less, ie ```
cat /etc/services | less
``` 

I never realised you could just type less - cheers! :D

---

### Post by xieu90 on 2010-01-21
if you know how to use terminal you can be the cat in the darkness
so you can do things with closed eyes ^^

I am still a blind cat:lolflag::lolflag::lolflag::lolflag::lolflag:

so I know only some command
sudo apt-get install "program name"  example: 
sudo apt-get install vlc,mplayer,gedit

sudo shutdown -hP +60 --> computer will shutdown after 60 minutes ^^ good for lullaby before you sleep in bed ^^

sudo htop (if my computer is frozen then i will ctrl alt F1 then log in, and use that command then find the one who troubles me ^^ then F9 9 Enter to kill it) 

I think that is all I know about terminal ^^

---

### Post by corncob on 2010-01-21
I'm sure you have enough to do already but I think this is what you're looking for:
[http://www.phys.uu.nl/~0020621/CP/unixforthebeginningmage.pdf](http://www.phys.uu.nl/~0020621/CP/unixforthebeginningmage.pdf)
Its been said that Linux is not Unix but, nontheless, everything works in Terminal.

---

### Post by Mariane on 2010-01-21
When you know where you want to go the terminal is much quicker. Think of a path you often follow, such as
Desktop/music/myfavorite

If you type
cd De 
tab
mu
tab
myf
tab
return

"tab" and "return" are the keys, I don't mean you have to spell "tab" or "return".

and then the name of the program you use to listen to music, this program will open in the right directory and you just have to find your file to launch it. 

It is much quicker than finding the directories one by one with the mouse. 

Mariane

---

### Post by wojox on 2010-01-21
This is a cool page [Linux 101 Hacks]("http://linux.101hacks.com/toc/")

---

### Post by oldos2er on 2010-01-21
> **achase79 said:**
> I believe man is one of the most important program.  you can use man <command> to see how a terminal command works

I haven't read through the whole thread, but I agree that **man** is essential, and so is **apropos**.

---

### Post by xieu90 on 2010-01-22
> **Mariane said:**
> When you know where you want to go the terminal is much quicker. Think of a path you often follow, such as
Desktop/music/myfavorite

If you type
cd De 
tab
mu
tab
myf
tab
return

"tab" and "return" are the keys, I don't mean you have to spell "tab" or "return".

and then the name of the program you use to listen to music, this program will open in the right directory and you just have to find your file to launch it. 

It is much quicker than finding the directories one by one with the mouse. 

Mariane


wow, this tab one is new for me ^^
normally I type
De*
enter
m* or mu*
and so on
but may be i will switch to tab now ^^
any other tricks?

yeah
I would install gnome-do and use it together with terminal
super+space
t
enter 
then I can go ^^

---

### Post by hortstu on 2010-02-12
Thanks for all the suggestions... some of them are ovemy head at this point but I'm going to keep working at it.  

What I'd like to see is an interactive outline of how to learn Ubuntu.  Right from the install setting up the partitions etc, setting up settings, getting Firefox right, learning the terminal, the file system...

I feel like I'm jumping all over the place and I need a hierarchy for grasping this stuff the shell the kernal the gui the gnome...

Or you know what would be cool?  A translator, like in babelfish, I could copy and paste some code someone gives me into it and it would tell me exactly what is going to happen in english, or whatever other language I speak.

Yeah I'm a newb.

---

### Post by hortstu on 2010-02-19
just figured this should be marked solved... don't hesitate to add if you have something.

---

