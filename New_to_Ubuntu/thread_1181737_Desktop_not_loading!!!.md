---
title: "Desktop not loading!!!"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2009-06-08
I can boot fine.  I get to the password screen and then it starts to glitch.  My desktop just dosn't want to load!!!

I just upgraded to 9.04 and its been nothing but problems.

I'm really scared I'm going to loose data/pictures and all the things that I've done to make my system run well.

---

### Post by AutumnPhoenix on 2009-06-08
*update*

I get a background...and after 10 minutes some icons...but no mouse or taskbar will appear.

---

### Post by CatKiller on 2009-06-08
> **AutumnPhoenix said:**
> I'm really scared I'm going to loose data/pictures and all the things that I've done to make my system run well.

Back them up then. You should do that anyway for anything you want to keep, but especially if you're worried now.

---

### Post by dileepm on 2009-06-08
Seems a compiz problem. Just get to command terminal in recovery console at boot menu and uninstall compiz

```
sudo apt-get remove compiz compiz-core

```
Then try logging in again. You may install the compiz at any time later.

---

### Post by AutumnPhoenix on 2009-06-08
I know to backup my data...I didn't just recently becuase I didn't realize that upgrading would be such an issue...

OK I can run in recovery mode but how do I get to a command terminal

I have

Clean______try to make free space
dpkg_______repair broken packages
fsck_______file system check
netroot____drop to root shell prompt w/networking
root_______drop to root shell prompt
xfix_______try to auto repair graphic problems

I'm going to run the root command, correct?

---

### Post by AutumnPhoenix on 2009-06-08
erm ok now I went to root and I removied compiz how do I boot up?

I am at 

root@NAME:~#

---

### Post by dileepm on 2009-06-08
```
init 6
```

---

### Post by AutumnPhoenix on 2009-06-08
The after password splash still isn't working it just kinda sits there and makes the PC busy

---

### Post by LewRockwell on 2009-06-08
> **AutumnPhoenix said:**
> I can boot fine.  I get to the password screen and then it starts to glitch.  My desktop just dosn't want to load!!!

I just upgraded to 9.04 and its been nothing but problems.

I'm really scared I'm going to loose data/pictures and all the things that I've done to make my system run well.

question:

what did you upgrade from?

windoze or a prior release of ubuntu?

hate to make assumptions on the "commonly" accepted meaning of "upgrade"...

---

### Post by AutumnPhoenix on 2009-06-08
Nope not windoze

Although going to a linux based OS is the only real way to upgrade that OS... ;)

Got rid of that nearly 2 years ago now.  I'm running on a Z60m IBM thinkpad  which typically loves the penguin.

I upgraded from 8.04

I started with xubuntu b/c someone told me it was easier to learn than any other flavor.  I know my geek friends hardly consider ubuntu real linux :rolleyes: so they aren't great at tech support.

---

### Post by AutumnPhoenix on 2009-06-08
Bump...

My poor lappy isn't loading after I sign on...still stuck at the splash scree even for 10+ minutes

---

### Post by iponeverything on 2009-06-08
do: ctrl-alt-f2

run:
```
top 
```

See what's eating up your cpu.

---

### Post by AutumnPhoenix on 2009-06-08
I have a screen that now sais 
top 11:21:02 up 2 min, 2 users, loade average 25.69

Tasks 333(going down), 59 running, 274 sleeping, 0 stopped, 0 zombie

Mem: with a number in the millions
Swap: wit a number at 1.6 mil

and then
PID USER PR NI VIRT RES SHR S %CPU %Mem Time+ and COmmand

the %cpu never goes over .5 for anythin except the command for that is xfdesktop its seen that one as hight as 11

---

### Post by LewRockwell on 2009-06-08
All these seem to be relevant to the Z60m


[http://forums.lenovo.com/lnv/board/message?board.id=Special_Interest_Linux&message.id=1192](http://forums.lenovo.com/lnv/board/message?board.id=Special_Interest_Linux&message.id=1192)

[http://forums.lenovo.com/lnv/board/message?board.id=Z_Series_Thinkpads&thread.id=1562](http://forums.lenovo.com/lnv/board/message?board.id=Z_Series_Thinkpads&thread.id=1562)

[https://lists.launchpad.net/ubuntu-x-swat/msg02928.html](https://lists.launchpad.net/ubuntu-x-swat/msg02928.html)

[http://ubuntuforums.org/showthread.php?t=1134935](http://ubuntuforums.org/showthread.php?t=1134935)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/329312](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/329312)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/338645](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/338645)

[http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg02884.html](http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg02884.html)

---

### Post by AutumnPhoenix on 2009-06-08
actuall the CPU line has a task running at 93% listed in the line

4.6%us, 3.6%sy, 0.0%ni, 0.0%id, 90.1%wa. 0.0%hi. 0.0%si, 0.0%st

---

### Post by K.Y.A on 2009-06-08
Boot back into recovery, into root terminal.
Try this:

```
sudo apt-get install fluxbox
```

Then, at the login screen, choose fluxbox from sessions. Right click to get a menu after logging in.

---

### Post by AutumnPhoenix on 2009-06-08
lew...those may be relevant to my PC, unfortunatly, they either aren't relevant to getting it to fully boot or don't have an answer.

---

### Post by K.Y.A on 2009-06-08
> **AutumnPhoenix said:**
> lew...those may be relevant to my PC, unfortunatly, they either aren't relevant to getting it to fully boot or don't have an answer.

Did you try installing fluxbox when in recovery terminal, and logging it using that session like I suggested? I guarantee that as a temporary fix...

---

### Post by LewRockwell on 2009-06-08
> **AutumnPhoenix said:**
> lew...those may be relevant to my PC, unfortunatly, they either aren't relevant to getting it to fully boot or don't have an answer.

ok, well in the eight minutes between my posting them and your response, I didn't have time to read them and digest them fully.

and since we haven't actually discovered the core difficulty you've run into, perhaps something in those threads will be useful later on in your recovery.

at least we can say we're trying...lol.

Never give up, never surrender!

---

### Post by AutumnPhoenix on 2009-06-08
I'm working on fluxbox...
I set ok t

fbsetbg: something when wrong while setting the wallpaper
run dispaly-geometry 1280x800+0+0 -window root /usr/share/fluxbox/debian-bluish walllpaper.pen frome xterm to find out w

---

### Post by AutumnPhoenix on 2009-06-08
I don't mean to be unapreciate, lew, I'm just new and more questions are more overwhelming than anything else


sooo

now how do I get to my files to save them?

---

### Post by K.Y.A on 2009-06-08
> **AutumnPhoenix said:**
> I'm working on fluxbox...
I set ok t

fbsetbg: something when wrong while setting the wallpaper
run dispaly-geometry 1280x800+0+0 -window root /usr/share/fluxbox/debian-bluish walllpaper.pen frome xterm to find out w


Good. You usually use Xfce, correct? Or Gnome? If so, you can try removing Gnome or Xfce and installing them again. You can run fbsetgb /home/Pictures/something.jpg to get picture. Of course replace /home/Pictures/something with the url to your pic. It will at least make you feel a bit at home until we figure out what is wrong ... :)

---

### Post by K.Y.A on 2009-06-08
> **AutumnPhoenix said:**
> I don't mean to be unapreciate, lew, I'm just new and more questions are more overwhelming than anything else


sooo

now how do I get to my files to save them?

That couldn't be easier. Run nautilus from terminal and your icons should come up. If not, run sudo apt-get install thunar . Then launch thunar and use it to copy your files to whatever storage device you have.

---

### Post by LewRockwell on 2009-06-08
> **AutumnPhoenix said:**
> I don't mean to be unapreciate, lew, I'm just new and more questions are more overwhelming than anything else


sooo

now how do I get to my files to save them?

no problem, I just wanted the links on this thread for the next person that has your problems and has found this thread via a google search.

sooo

you say you want to save your files, hmmm....

if you have a complete disk back-up/clone(say, using Clonezilla) then you already have a back-up/clone but you would be wise to have a current/up-to-date one anyway...

---

### Post by AutumnPhoenix on 2009-06-08
ok so now I somehow got it to look xfacy

I have to buy some CD's or such to save my stuff...so lemme do that and I'll be back in a bit.

---

### Post by AutumnPhoenix on 2009-06-08
It looks like I won't be able to acess my extra saving stuff until later today...what should I look forward to when it comes to fixing this bug...is it just an x-face bug?  Is there a way to get just ubuntu 9.04?  And do I seem too daft to manage it?

---

### Post by LewRockwell on 2009-06-08
why did you start another thread?

---

