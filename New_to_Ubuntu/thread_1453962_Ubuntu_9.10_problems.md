---
title: "Ubuntu 9.10 problems"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by LadyA on 2010-04-14
I am new to Linux and have been using Ubuntu 9.10 for a couple of months, which was set up on the computer when I got it. Everything worked great until this week when several problems arose.
Problem 1- When I click on the update manager in System>Preferences, nothing happens and I do not get any notifications for security updates.
Problem 2- When I click on shutdown the screen goes blank, but comes back on to the login screen.
Problem 3- My thumb drive will not mount. I get an error message that says I do not have permission. It worked fine until now.

---

### Post by oOarthurOo on 2010-04-14
Sounds like a recent update may have made some unfortunate changes to your system. Try opening up a terminal and punching these commands:
```
sudo apt-get update
sudo apt-get full-upgrade
```
Post any error messages you receive.

---

### Post by LadyA on 2010-04-14
This is what I get in terminal.

owner@owner owner@owner-desktop:~$ sudo apt-get update
[sudo] password for owner: 
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/restricted Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security Release.gpg
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic Release
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates Release             
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/main Packages               
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/restricted Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/multiverse Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") karmic-updates/multiverse Sources
Reading package lists... Done
owner@owner-desktop:~$ 

owner@owner-desktop:~$ sudo apt-get full-upgrade
[sudo] password for owner: 
E: Invalid operation full-upgrade
owner@owner-desktop:~$

---

### Post by Don1500 on 2010-04-14
try going to the update manager now and run that again.

SYSTEM => ADMINISTRATION => UPDATE MANAGER

---

### Post by LadyA on 2010-04-14
System>Administator>Update Manager does not work. Nothing happens when I click on it.
Now there is a new problem. When I turn the computer on it goes to a screen that says:
Displash: Setting mode 1152x864 failed.
Displash: Using mode 1024x768 failed.
Mount of filesystem failed.
A maintenance shell will now be started.
Control-D will terminate this shell and re-try.
root@owner-desktop:~#
What do I do now?

---

### Post by Calash on 2010-04-14
type the following


cat /etc/group

You should get a long list.  If you only get a couple of results then you had a similar issue to what I had a while back, the loss of your group file.

Let us know how many entries you get back from the above command.

---

### Post by oOarthurOo on 2010-04-14
> **LadyA said:**
> owner@owner-desktop:~$ sudo apt-get full-upgrade
[sudo] password for owner: 
E: Invalid operation full-upgrade
owner@owner-desktop:~$

Apologies, I don't use apt-get anymore and I mixed in an aptitude command. It doesn't matter though, because according to the previous command there are no new updates pending. The previous advice to check your groups is a good place to start.

---

### Post by jaco223 on 2010-04-14
> **LadyA said:**
> System>Administator>Update Manager does not work. Nothing happens when I click on it.
Now there is a new problem. When I turn the computer on it goes to a screen that says:
Displash: Setting mode 1152x864 failed.
Displash: Using mode 1024x768 failed.
Mount of filesystem failed.
A maintenance shell will now be started.
Control-D will terminate this shell and re-try.
root@owner-desktop:~#
What do I do now?

From that prompt you could try to upgrade and see if that fixes the display issue.

Type:

```
sudo apt-get -f dist-upgrade
```See if that gets you straightened out.

Hope that helps.

Jaco

P.S I think -f will force the upgrade

---

### Post by LadyA on 2010-04-14
When I type in cat/etc/group I get:
bash: cat/etc/group: No such file or directory

---

### Post by EssexEagle on 2010-04-14
> **LadyA said:**
> When I type in cat/etc/group I get:
bash: cat/etc/group: No such file or directory

There should be a space between cat and /etc/group (cat is the command you are running, and /etc/group is the filename whose contents it will display).

---

### Post by LadyA on 2010-04-14
When I type in sudo apt-get -f dist-upgrade I get this:
Not using locking for read only lock file /var/lib/dpkg/lock
Unable to write to /var/cache/apt/
The package lists or status file could not be parsed or opened.

---

### Post by LadyA on 2010-04-14
When I type in cat /etc/group I get 24 entries.

---

### Post by jaco223 on 2010-04-14
I've been googling "Not using locking for read only lock file /var/lib/dpkg/lock"
trying to find some helpful info, but what I'm finding is quite dated.

---

### Post by torchfire on 2010-04-14
I'm having the exact same problem with Update Manager on a new install of Xubuntu 9.10.  The Update Manager notification says there are 187 updates.  Clicking the notification does nothing.

I get many entries when I run cat /etc/group. 

Choosing System>Update Manager does nothing.

When I run sudo apt-get updates, I get pretty much the same output as the original poster: 

Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done


Now, I'm trying the Mark All Upgrades feature in Synaptic Package Manager.  I'll let you know how that goes. 

torch

---

### Post by torchfire on 2010-04-14
The Downloading Packages process has begun, and it seems that there are 187 of them, which matches what the notifier says.

Hoping for the best!

---

### Post by Calash on 2010-04-14
> **LadyA said:**
> When I type in cat /etc/group I get 24 entries.

24 sounds a bit low, but that does not match the problem I had (I only had 3 entries).

This is good in that the problem I had was a nightmare to fix, but bad because I am not sure if any of my suggestions will be much help.

From the maintenance shell can you type the following and let us know if you get a reply

grep gdm /etc/group
grep root /etc/group
grep messagebus /etc/group
grep adm /etc/group


You should get single line replies formatted something like the following

gdm:x:120:


Your numbers will vary.  What these commands do is search the /etc/group file for specific strings.  In each case the string is the name of a group that I want to confirm is still in the file.  

I am expecting you will get replies for all of them based on what I know so far but it will help me rule out the issue.

---

### Post by torchfire on 2010-04-14
Using the Mark All Upgrades feature, I was able to install all 187 updates without a problem. 

However, this did not resolve the problen that Update Manager does not run. 

Any other ideas on that? 

Thanks. 
Torch

---

### Post by LadyA on 2010-04-14
Calash, here is the results from the maintenance shell:
gdm:x:119:
root:x:0:
messagebus:x:106:
admin:x:115:owner

---

### Post by lidex on 2010-04-14
torchfire [not OP]
Try this from a terminal:
```
gksudo update-manager
```
and post any error output.

---

### Post by lidex on 2010-04-14
LadyA,
Can you boot into a LiveCD session and retrieve some log data?
```
~/.xsession-errors
/var/log/dmesg
/var/log/messages
/var/log/syslog
/var/log/user.log
```

---

### Post by LadyA on 2010-04-14
Lidex, I do not have a CD. Would the CD work on the computer that I have Ubuntu on if I downloaded the ISO and burned a bootable CD with Disk Utility on my Mac? I can't log in with Ubuntu so I can't do it on there.

---

### Post by lidex on 2010-04-14
> **LadyA said:**
> Lidex, I do not have a CD. Would the CD work on the computer that I have Ubuntu on if I downloaded the ISO and burned a bootable CD with Disk Utility on my Mac? I can't log in with Ubuntu so I can't do it on there.

Yes.

---

### Post by LadyA on 2010-04-15
Lidex, when I put the CD in I get a screen that says:
Try Ubuntu without any change to your computer
Install
Check disc for defects
Test memory
Boot from first hard disk
Press F4 to select alternative start-up and installation modes.
F1 Help F2 Language F3 Keymap F4 Modes F5 Accessibility F6 Other Options
Which one do I pick and am I looking for the terminal?

---

### Post by e4uforums on 2010-04-15
I would select "Try Ubuntu without any changes to your computer".  This will load Ubuntu desktop so you have a graphical interface to get the log files with.

---

### Post by LadyA on 2010-04-15
All commands said Permission Denied
Am I doing this wrong? After chosing Use ubuntu without any change to computer, I went to Terminal and put in commands.

---

### Post by albert s on 2010-04-15
frirst thing I would do would be   check disc for defects , 
then if all is ok you could simply re-install ubuntu on the existing ubuntu partition,
or do you have stuff on there you do not want to wipe out?  sorry I havent read the full thread.  :oops:

sometimes try without installing wont give all the priviledges you need.

---

### Post by lidex on 2010-04-15
> **LadyA said:**
> All commands said Permission Denied
Am I doing this wrong? After chosing Use ubuntu without any change to computer, I went to Terminal and put in commands.

What commands did you use? Did you try using nautilus to browse the install partition?

---

### Post by LadyA on 2010-04-15
Lidex, with the live CD I put in the commands you gave me in reply #20 and it said Permission Denied. I don't know enough to understand what you mean by using nautilius to browse the install partition. How do I get there and what would I look for? I know I am kind of dumb at this, but I do appreciate everyone's help and I am trying to learn everything I can.

---

### Post by lidex on 2010-04-15
> **LadyA said:**
> Lidex, with the live CD I put in the commands you gave me in reply #20 and it said Permission Denied. I don't know enough to understand what you mean by using nautilius to browse the install partition. How do I get there and what would I look for? I know I am kind of dumb at this, but I do appreciate everyone's help and I am trying to learn everything I can.
Those weren't commands, just the paths to the files. To view in a terminal the command is ```
cat /path/to/file
``` so ```
cat /var/log/messages
``` should display the messages file in the terminal. To browse, simply go to "Places" in the panel menu and click on one of the entries (home,desktop,etc.) to open a nautilus window. The pane on the left will display the partitions. Simply click on the entry for the one you wish to browse to mount it and display the contents in the right.

---

### Post by LadyA on 2010-04-16
Lidex, on the live CD I can view the log files. How will they help me to figure out the problem.

---

### Post by whiteman on 2010-04-16
When I use Jaunty...all of my printers...2 HPS and a Canon MP470 all showed up when I chose ad printer. It was very easy to add them. I can print from my MAc, WIndoze, even my iphone. NOW I tried to upgrade to Karmic.....it doesnt even show my Canon printer anymore.(When I choose to add printer) It only shows a that it found myDeskjet 930. And thes strangest thing is thhis...I am showing like a mounted drive..called Canon Mp470?! My printer is mounted, but totally useless. I tried installing from a canonnical disk,(caME IN MAIL) Upgrading from Jaunty.Each time INSTALL was an experiennce. SOmetimes it would make me type my username-paswd over and over. Wouldnt login. I finally started rebuiding Grub on each install and fixed this. I really didnt change that much. FinALLY I GOT FED UP. I need a dependable unit because all of my computers depend on this Ubuntu Jaunty to print, scan, fax. I gave up on Karmic. What caused this printer-drive thing?

---

### Post by lidex on 2010-04-16
> **LadyA said:**
> Lidex, on the live CD I can view the log files. How will they help me to figure out the problem.

Probably won't help you at all, but if you post them here using the code tags, one of us may figure it out. To use the code tags, copy your text to the clipboard, press the "#" symbol in the toolbar, and press Ctrl+V. Alternately, paste the text into your post, highlight it and press the "#" symbol.

---

### Post by cuberts on 2010-04-16
> **LadyA said:**
> I am new to Linux and have been using Ubuntu 9.10 for a couple of months, which was set up on the computer when I got it. Everything worked great until this week when several problems arose.
Problem 1- When I click on the update manager in System>Preferences, nothing happens and I do not get any notifications for security updates.
Problem 2- When I click on shutdown the screen goes blank, but comes back on to the login screen.
Problem 3- My thumb drive will not mount. I get an error message that says I do not have permission. It worked fine until now.have you tried reinstalling it?
If that does not work then you should boot up from Wubi inside of Windows.
Computer>installs>wubi    In Windows.
Make sure that you have installed it

---

### Post by LadyA on 2010-04-17
I got the system to bootup and go to desktop. When I click on shutdown, the screen goes off, but but comes back on to the desktop. How can I safely shutdown? This is all so confusing.

---

