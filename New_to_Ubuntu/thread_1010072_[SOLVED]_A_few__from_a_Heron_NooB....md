---
title: "[SOLVED] A few ? from a Heron NooB..."
date: 2008-12-13
forum: New to Ubuntu
---

### Post by ChuckEaufarley on 2008-12-13
I've been running XP since its release, and have become very familiar with its operations (as well as weaknesses), and with the release of Vista I knew I was going to learn a new system one way or another, so I decided to make the switch to Ubuntu Linux because it was claimed to be user-friendly (enough) and has a tight security for everyday use.  I've been trying my best to figure out all the ins & outs of the new system, but I have a few questions - some simple and others just silly, but I appreciate serious input either way.

1)  Silly Q:  I've been trying to add custom cursor themes from [here]("http://www.gnome-look.org/content/show.php?content=19506") and after reading the instructions, I'd like some clarification on exactly how to > copy them as root (type "su" in console) in this directory: /usr/lib/X11/icons/  I'd also like to know how to verify that > a folder named tuxcursor in the /usr/lib/X11/icons/ directory and a folder named /default which contains the index.theme
 as well as > check if the index.theme contains this line: inherits=tuxcursor  So pretty much the only thing that I know how to do from these instructions is to extract the files, and restart the machine.  I'm sure that changing the cursor is likely a very easy thing to do and the instructions well-written to the computer literate, but it looks totally Greek to me and this seems to be a good place for me to start learning the simple stuff without breaking anything.

2) A Firewall - I know that some folks have gotten away without one for years, but for me, if nothing else it's a peace of mind.  I've heard that passwords are golden in this OS, so the pester of always having to enter it in is a security-thing yadda, yadda, yadda, but if there's a firewall out there that won't shut down my printer port and will still barricade without having to ask for everything first - that would be neat.  So if y'all know any good (user-friendly yet still secure) firewalls out there for Ubuntu that you would recommend then let me know please.

I'd like to thank you in advance for your patience, I know that this has probably been covered 1000+ times, but a search turns up so much stuff to pour over, and direct answers are always best anyhow so thanks for posting!  ):P

---

### Post by Kareeser on 2008-12-13
You'll have to go diving into the command line :)

Think of it as using the command prompt in Windows, except you can actually do a lot more, compared to Windows.

1. Logging into root.
'round here, lots of us prefer to use the command "sudo" instead of "su" to do stuff in root. The Root account is basically a superuser that has access to all directories. As such, it's quite dangerous, and "sudo" allows you to execute commands in root on a temporary basis.

The "copy" command, in Unix, is "cp", and uses the same format as windows.

For #2. Remember "dir" in Windows? Try "ls" in Unix.

---

### Post by Riffer on 2008-12-13
By default Ubuntu is firewalled using a file called iptables.  You can use a program Called firestarter to config said firewall.  There is also guarddog which does the same thing.

I'd be surprised if your printer port is firewalled.

---

### Post by w4ett on 2008-12-13
> 2) A Firewall - I know that some folks have gotten away without one for years, but for me, if nothing else it's a peace of mind.

iptables is installed by default:

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by Paqman on 2008-12-13
Btw, if you don't believe us about the firewall, run one of the online scans. You unfirewalled Ubuntu system will probably beat a firewalled Windows one!

By default, Ubuntu has no service listening on any ports. So there's nothing for a malicious intruder to connect to. Adding a firewall to this setup would not increase security at all. If you install any kind of web-facing sever software then you would have services listening on ports, so would need to start thinking about security.

---

### Post by ChuckEaufarley on 2008-12-13
Oh nice.  The built in firewall is a big [SIZE="3"]**+**[/SIZE]  
But as for the cursor-thing... I'm getting very frustrated.  Is there an _Linux for Complete F-ing Idiots_ book that I needed to read before installing the Ubuntu CD, or is everybody thats been addicted to XP this stupid?  I've been reading the how-to's and I still don't get it.  

So far I've unpacked my .tar.bz2 file and have the extracted folder on my desktop. 

I opened Applications/Accessories/Terminal and typed in "sudo aptitude install gcursor " to which it did this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be installed:
  gcursor 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/14.4kB of archives. After unpacking 156kB will be used.
Writing extended state information... Done
Selecting previously deselected package gcursor.
(Reading database ... 114355 files and directories currently installed.)
Unpacking gcursor (from .../gcursor_0.061-ubuntu5_i386.deb) ...
Setting up gcursor (0.061-ubuntu5) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done            

...Which I guess is a good thing. 

I then went to System/Preferences/Cursor Selection only my "Install Theme" and "Go To Theme Folder" buttons are not responding - whether I have a cursor highlighted on the left or not, nothing happens.

Anybody care to break this one down for a T-total NooB?  
We can just pretend I've never seen a computer before.

Thanks for the input!

---

### Post by Twitch6000 on 2008-12-13
> **ChuckEaufarley said:**
> Oh nice.  The built in firewall is a big [SIZE="3"]**+**[/SIZE]  
But as for the cursor-thing... I'm getting very frustrated.  Is there an _Linux for Complete F-ing Idiots_ book that I needed to read before installing the Ubuntu CD, or is everybody thats been addicted to XP this stupid?  I've been reading the how-to's and I still don't get it.  

So far I've unpacked my .tar.bz2 file and have the extracted folder on my desktop. 

I opened Applications/Accessories/Terminal and typed in "sudo aptitude install gcursor " to which it did this:

 

...Which I guess is a good thing. 

I then went to System/Preferences/Cursor Selection only my "Install Theme" and "Go To Theme Folder" buttons are not responding - whether I have a cursor highlighted on the left or not, nothing happens.

Anybody care to break this one down for a T-total NooB?  
We can just pretend I've never seen a computer before.

Thanks for the input!

Okay do not feel bad when changing oses it always feels wierd.

Trust me I let me grandparents try Linux for about 1 day and they wanted to kill me lol...

Anyways, this is how I install new cursors -

Get your .tar, right click and click the change background apperence, then click themes, then click icons.

After that just click and pull the .tar over the icon menu :].

It should then say installed.

After that click the cursor.

Here is a link to a better step by step that helped me.

[http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/](http://tombuntu.com/index.php/2008/05/19/how-to-install-cursor-themes/)

Just to let you know if you do not want to use the terminal, let us know and we can give a gui alternative :).

ITs just alot of us here(myself included) are a bit addicted to the terminal :P.

---

### Post by ChuckEaufarley on 2008-12-13
I think I mis-typed in my original post, and perhaps would have been better understood if I'd said "I've been running XP since its release, and have become very familiar with its *navigations*..." 

...run prompt scares me - I've been burned in there before.

I just finished a conversation with the man that shined me on to Ubuntu and we're working on getting this straightened out, but I have to admit that I'm feeling pretty discouraged.  Whereas I once thought I knew more than the average bear with my old system, I feel like a monkey trying to do algebra when it comes to the Linux technical-talk and encrypted command prompts.

Maybe once I have this figured out, I might post a how-to for silly & stupid things like this for other XP converts.

---

### Post by Tyke91 on 2008-12-13
encrypted command prompts?

the shell is your friend, and your most powerful tool. I believe that there is a link in my sig to a place where you can learn some basic linux shell tools.

---

### Post by ChuckEaufarley on 2008-12-13
Thank you to Tyke and Twitch for the links.  I have successfully installed my new cursor, and it was A LOT more simple than what it was made out to be.

For those that are used to drag & drop / point & click kinda stuff this works out real nice-like.

1)  Download & Extract the cursor to the desktop.
2)  Open Applications/Accessories/Terminal and type:
    > sudo aptitude install gcursor then hit enter, and close the Terminal.
3)  Then open Places/Desktop/[cursor file name] and minimize to tray.
4)  Next open System/Preferences/Appearance and select the "Theme" tab.
5)  Drag & Drop the extracted custom cursor file into the "Theme" frame from the desktop frame and click "Install."

That was really easy - like, a lot easier than all the other stuff I tried :lolflag:  Anyway, I finally got it, and I'm sure I'll be back with a few more ridiculous questions for the NooB board.  Thanks again!

---

### Post by sneeks on 2008-12-13
Well done,you are on your way....

---

### Post by albinootje on 2008-12-13
By default Ubuntu does *not* use a firewall.
But (i think) since Hardy Heron there's build in easy to use firewall software called "ufw".

it's a commandline tool : ufw -h

Usage: ufw COMMAND

Commands:
  enable			enables the firewall
  disable			disables the firewall
  default ARG			set default policy to ALLOW or DENY
  logging ARG			set logging to ON or OFF
  allow|deny RULE		allow or deny RULE
  delete allow|deny RULE	delete the allow/deny RULE
  status			show firewall status
  version			display version information

Application profile commands:
  app list			list application profiles
  app info PROFILE		show information on PROFILE
  app update PROFILE		update PROFILE
  app default ARG		set profile policy to ALLOW, DENY or SKIP

There's an unofficial GUI for it :
[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

But, assuming that you're already behind a firewall from your ADSL-router or cable-modem, you can easily do without.

It's much more important to keep your software up to date, especially web-browsers that you're using (Firefox, Galeon, Konqueror, Epiphany-browser), and be a bit careful with p2p software as a start.

---

### Post by Paqman on 2008-12-14
> **albinootje said:**
> By default Ubuntu does *not* use a firewall.
But (i think) since Hardy Heron there's build in easy to use firewall software called "ufw".

it's a commandline tool : ufw -h


Ufw isn't really a firewall either. Like Firestarter it's a config tool for iptables. There's a GUI for it called gufw.

---

### Post by ChuckEaupharlie on 2008-12-17
Dear mods:  The other Chuck is dead - XP ate his PW's when MyMachine crashed, and I didn't write them down, so feel free to delete him - he's just me :D

So let's try another one.

I have a .png image on my desktop right now for a "start" menu that doesn't want to cooperate.  

I have gone into the Terminal and typed in:

> gconf-editor

Opened apps/panel/objects/object_1

I tried changing the values of "object_type" to > /home/chuck1/Desktop/start.png and clicked the box next to "use_custom_icon" but that didn't work.

I think I'm kinda lost here ...any help?

---

