---
title: "Some questions from a confused begginer"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Dave851 on 2010-05-17
Ok well first off I am 16....
 
I am useing the ubuntu server edition 10.04. I can do ver simple things but I am having hhsome small issuses. This is my first server. I got a blade for free from a local compony. its a small one but its going to be my test subject so I can learn about servers,networking and ubuntu. I am reading the documentation and I need to ajust a repository. but i can not seem to get to it. What is the command to open up the file? I typed in /ect/apt/sources.list and that didn't work..

---

### Post by ubunterooster on 2010-05-17
try
sudo nano /ect/apt/sources.list

---

### Post by MCVenom on 2010-05-17
It would be this:

```
sudo nano /etc/apt/sources.list
```

And lemme just say I'm 14, myself... :p I assume you'd feel more comfortable with nano, it's a pretty easy to get and intuitive text editor. If nano isn't already installed, use this command:

```
sudo apt-get install nano
```

Though I would point out that if you have the time to learn the basics, Vim is a great CLI editor to learn, and it's really an invaluable skill! :D Though simply for the sake of being able to manage the terminal windows, I'd learn it on a desktop install, there's a great 30 minute-or-so primer available by issuing the command:

```
vimtutor
```

Oh and speaking of 'window management', byobu is an invaluable tool in a CLI environment, if you don't know what it is, I'd look it up. You can install it with:

```
sudo apt-get install byobu
```

and then run it with the command: 

```
byobu
```

I hope my post was helpful, good luck and have fun! :D

---

### Post by marshmallow1304 on 2010-05-17
You need to specify an editor to edit the file.  nano is nice and simple.  Additionally, you need to have root privileges to write to that file, which can be accomplished with sudo.  Thus,

```
sudo nano /etc/apt/sources.list
```

Ctrl+o Enter to save
Ctrl+x to quit

---

### Post by MCVenom on 2010-05-17
> **ubunterooster said:**
> try ```
gksu gedit /ect/apt/sources.list
```
Unless he installed Gnome after the fact, that wouldn't work. Neither gksu nor gedit would be on his system.

---

### Post by ubunterooster on 2010-05-17
> **BlackOtaku said:**
> Unless he installed Gnome after the fact, that wouldn't work. Neither gksu nor gedit would be on his system.
Right; thanks (edits post; hopefully before OP sees it.)

---

### Post by Dave851 on 2010-05-17
Ok so i tryed the gksu and nano and I do not understand how to operate eather..
 
gksu: after I installed it(The one thing i do know how to sure is the apt funtion) I typed in gksu redit /ect/apt/source.list and it did list some thing im not to sure(can't see it)
 
Nano: I typed it in and got a toolbar on the op and bottom. It has the file path listed at the top center but the page is blank. I can figure out how to use the commands on the bottom.
 
Edit: Ok i am installing gedit now.... So ^ is a way of saying ctrl? I tryed **** but didn't think ctrl.
 
Also I will have to do this at a remote location with no internet connection. is there a way to put the utilitys on a cd and get them from there

---

### Post by Dave851 on 2010-05-17
ok for the "gksu gedit /ect/apt/sources.list". i get (gksu:17698): Gtk-WARNING **: CANNOT OPEN DISPLAY:

---

### Post by MCVenom on 2010-05-17
> **Dave851 said:**
> ok for the "gksu gedit /ect/apt/sources.list". i get (gksu:17698): Gtk-WARNING **: CANNOT OPEN DISPLAY:
Dave, you don't have any GUI or anything installed (I'm assuming), so GUI programs like gksu and gedit won't work. You'll need to use a command-line editor, like nano, vim, or emacs (and don't ever think of using emacs!!! EVAR!!! :lolflag:).

Nano's by far the easiest to use, however.

---

### Post by ubunterooster on 2010-05-17
why can't you just apt-get install ubuntu-desktop?

---

### Post by Dave851 on 2010-05-17
> **ubunterooster said:**
> why can't you just apt-get install ubuntu-desktop?
 
didn't know i need to and also i want to learn how this is used in the real word and from what i read that means no desktop. So how do i use nano? I get the toolbars but no text. Also is there a way to put the utilitys on a cd and get them from there?

---

### Post by oldos2er on 2010-05-17
> **Dave851 said:**
>  Edit: Ok i am installing gedit now.... So ^ is a way of saying ctrl? 

Yes. Also, you're misspelling the file path. It should be ```
sudo nano /etc/apt/sources.list
```

---

### Post by Dave851 on 2010-05-17
> **oldos2er said:**
> Yes. Also, you're misspelling the file path. It should be ```
sudo nano /etc/apt/sources.list
```
 
Still coming up blank.......

---

### Post by MCVenom on 2010-05-17
> **Dave851 said:**
> Nano: I typed it in and got a toolbar on the op and bottom. It has the file path listed at the top center but the page is blank. I can figure out how to use the commands on the bottom.

Are you sure you typed the file path in correctly? If so, could you run this command and post the output?

```
ls /etc/apt/ 
# This command will print what's in /etc/apt/ directory.
```

> Also I will have to do this at a remote location with no internet connection. is there a way to put the utilitys on a cd and get them from there

There are ways to put all of the contents of the repos on a portable drive or some DVDs, I'll post them if you're interested. ;)

---

### Post by MCVenom on 2010-05-17
> **ubunterooster said:**
> why can't you just apt-get install ubuntu-desktop?
Because a desktop is a NIGHTMARE for a server. 

SO MANY GAPING HOLES, SURROUNDING ME LIKE ANGRY SWISS CHEESE, AAAAAAAAAAAAAAAAAA!!!!!!!!!!!!!!!! :lolflag: 

It's usually unnecessary, eats resources that could be better used, and decreases stability and security.
> **Dave851 said:**
> didn't know i need to and also i want to learn  how this is used in the real word and from what i read that means no  desktop.
OP's right on the mark, NO DESKTOPS.

---

### Post by Dave851 on 2010-05-17
> **BlackOtaku said:**
> Are you sure you typed the file path in correctly? If so, could you run this command and post the output?
 
```
ls /etc/apt/ 
# This command will print what's in /etc/apt/ directory.
```
 
 
 
There are ways to put all of the contents of the repos on a portable drive or some DVDs, I'll post them if you're interested. ;)
 
Ok well from the [EMAIL="user@ubuntu:~$"]user@ubuntu:~$[/EMAIL] i entered ls /ect/apt and it said ls: cannot acces /ect/apt. also what is ls?
 
Also i need it on cd the blade only has a cd drive not dvd

---

### Post by MCVenom on 2010-05-17
> **Dave851 said:**
> Ok well from the [EMAIL="user@ubuntu:~$"]user@ubuntu:~$[/EMAIL] i entered ls /ect/apt and it said ls: cannot acces /ect/apt. also what is ls?
 
Also i need it on cd the blade only has a cd drive not dvd
Alright we'll solve the local repos thing later, but I think you might have mispelled it, it's '*/etc/*apt'. But whether or not this is the case, I'd also like you to try sudo in front, just in case. So run: 
```
sudo ls /etc/apt/
```

**ls** stands for **l**i**s**t. It's used to list the files and directories(folders) in a directory. By default it will list whatever is in the directory you're currently working in. For example, running ls on my machine I get ( ~ means that user's home folder):

```
blackotaku@blackotaku-laptop:~$ ls  
examples.desktop   Pictures  some-ui-enhancement
Desktop            lmms               Podcasts  Templates
Documents          LucidDreaming.png  Public    Videos
Downloads          Music              pyjunior
```

I can specify a directory to list the contents of by putting it after ls. For example, this is what I get if I run 'ls /etc/apt/'

```
blackotaku@blackotaku-laptop:~$ ls /etc/apt
apt.conf.d     secring.gpg   sources.list.d     trustdb.gpg  trusted.gpg~
preferences.d  sources.list  sources.list.save  trusted.gpg  trusted.gpg.d
```

Here's an intro to common linux terminal commands and tricks, you'll need it for a server :p: [http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)

---

### Post by Dave851 on 2010-05-17
ok so i was spelling it wrong.. now it works.. my speeling suck if you didn't notice

---

### Post by MCVenom on 2010-05-17
> **Dave851 said:**
> ok so i was spelling it wrong.. now it works.. my speeling suck if you didn't notice
It's okay... glad you got it working! :D And do you have a portable drive you could use?

---

### Post by Dave851 on 2010-05-17
Also i get got a random small game bomber thought aptitude. I am wondering how to lunch it. I know games arn't on servers but i figured it would be good to get new apt and be able to launch them....

---

### Post by Dave851 on 2010-05-17
> **BlackOtaku said:**
> It's okay... glad you got it working! :D And do you have a portable drive you could use?
 
Ok well the blade is old. from the 90's. It dosn't have any usb ports....
 
p.s. its actuly a compaq prosignia 500 server...

---

### Post by MCVenom on 2010-05-17
> **Dave851 said:**
> Also i get got a random small game bomber thought aptitude. I am wondering how to lunch it. I know games arn't on servers but i figured it would be good to get new apt and be able to launch them....
Does it require a GUI (is it a graphical application?)? Those will require X to be installed, and you'll need a window manager as well. Openbox is a good, lightweight window manager; you can find more information on installing it and setting it up here : [https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)

---

### Post by Dave851 on 2010-05-17
> **BlackOtaku said:**
> Does it require a GUI (is it a graphical application?)? Those will require X to be installed, and you'll need a window manager as well. Openbox is a good, lightweight window manager; you can find more information on installing it and setting it up here : [https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)
 
how do you know if it needs a gui??

---

### Post by MCVenom on 2010-05-17
Here's a guide on setting local repos up on CDs. I would definitely advise you do this from a desktop install or at least a LiveCD, it'll make things much easier. [http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

Please note that this will take **a lot** of CDs, and you'll need **at least 40 gigs **of free space on the computer you do this on. Also, I hope you won't be doing this on a family computer; this process could take about a day. Also if your ISP has bandwidth caps, that should definitely be a consideration.

**If you have a much smaller and more specific number of packages you want, this guide is probably much better for you; **[http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher](http://www.packtpub.com/article/create-local-ubuntu-repository-using-apt-mirror-apt-cacher)

---

### Post by MCVenom on 2010-05-17
> **Dave851 said:**
> how do you know if it needs a gui??
Typically, you don't install extraneous things on a server... especially if you're not sure what they do or how they work.

Do you mind me asking what this 'server' is for, exactly? Is it just to learn, are you planning a specific purpose? i.e.; website hosting, mail server, etc?

Also, learning Linux and how it does things can be a challenge at times, but it is definitely rewarding. Here are some tips for learning more:

-Google is your friend. Never forget that. :p

-Wikipedia is also a good buddy to have around to learn about the history or get a description or comparison of something.

-We are all friends here too, don't ever be afraid to ask questions! :D

-You might wanna do more reading and/or research from books and magazines. For example, Linux Format is a magazine from the UK (in the US you should also be able to find it in most moderately sized bookstores). It has articles and pieces for pretty much anyone who could possibly be using Linux. It also has great beginner's guides and tutorials, I'd definitely check it out. In fact, this month's issue happens to have a piece on how your average Linux system fits together, in an easy to follow guide. (Plus they come with DVDs packed with free software, Tutorials, and usually some kinda Linux OS. They also happen to be Eco Discs, which is awesome because you can bend them like a thin piece of cardboard, and throw them like Frisbees :lolflag:)

The Official Ubuntu Book is also a great read. Even if you think you know everything there is to know, you should buy it; it covers everything from Linux history, to Ubuntu, to Kubuntu, to Edubuntu, to Ubuntu Server, to baking Ukrainian bread that's shaped like the Ubuntu logo! :lolflag: It's **invaluable.**

Also, I'm sure if you make a thread in the Community Cafe asking about good ways to learn more, you'll get even more, better suggestions. :p

Happy Tuxing! :D

---

### Post by Dave851 on 2010-05-18
Well this is going to be for learning. I decided to kill 2 birds with one stone. I can learn linux and server networking...

---

### Post by MCVenom on 2010-05-18
> **Dave851 said:**
> Well this is going to be for learning. I decided to kill 2 birds with one stone. I can learn linux and server networking...
A server is a good way to learn some things, but I've found that the best and easiest ways to learn about Linux (and it's important you understand basic underlying principles of the system you're working with to be able to work with a server) is actually to jump into desktop or general-purpose distros that require some effort to set up. What is your experience with other distros? 

Btw, if you haven't tried Arch yet, I'd definitely recommend you do; it has a great beginner's guide for setting up your system, and you'll learn things from installing it.

---

### Post by Dave851 on 2010-05-18
> **BlackOtaku said:**
> A server is a good way to learn some things, but I've found that the best and easiest ways to learn about Linux (and it's important you understand basic underlying principles of the system you're working with to be able to work with a server) is actually to jump into desktop or general-purpose distros that require some effort to set up. What is your experience with other distros? 
 
Btw, if you haven't tried Arch yet, I'd definitely recommend you do; it has a great beginner's guide for setting up your system, and you'll learn things from installing it.
 
This is my first shot at anything linux...

---

### Post by MCVenom on 2010-05-18
> **Dave851 said:**
> This is my first shot at anything linux...
Okay, then let me be blunt: Running a Linux server is **NOT** the best way for a beginner to learn about Linux. :p

Why don't you take a look at Ubuntu's Desktop Edition? You can download it or get a free, professionally pressed CD of it (mine came in the mail last week or so :D), and it's great for just getting started with a Linux OS. It's easy-to-use and get the hang of, but you'll still learn little things from using it that you can build on to learn more. You can set up a system to choose between Windows and Ubuntu when you start it up easily, and you might even eventually decide that you want to use it as your main OS, like I did.

You can start your journey here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) ;)

PS: There's an easy, very painless way to dual-boot Windows and Ubuntu without the dealing with partitioning. :D If you click on 'Alternate download options' and select Ubuntu Installer for Windows (Wubi), you can install Ubuntu on your system from inside Windows and dual-boot it without the hassle of partitioning. If you decide to uninstall it, you can do so from Add/Remove Programs in Windows. A Wubi install may be a bit slower though, and I believe you won't be able to hibernate Ubuntu in one.

Good luck! :D

---

### Post by Dave851 on 2010-05-18
Na i just run it in a vmbox. thats how i'm getting used to the server edition with out the server

---

