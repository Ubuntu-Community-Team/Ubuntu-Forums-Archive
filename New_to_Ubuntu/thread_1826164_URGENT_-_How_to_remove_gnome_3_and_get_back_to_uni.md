---
title: "URGENT - How to remove gnome 3 and get back to unity or gnome 2!"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by the-new-x on 2011-08-16
Hello guys, this is urgent, I need help, I have installed gnome 3 because it seemed to be good, but now things have went terribly wrong, neither unity, and nor gnome 3 are acting as they should! I follower the instructions from this website: [http://linux4every1.blogspot.com/2011/07/install-gnome3-on-ubuntu-1104.html](http://linux4every1.blogspot.com/2011/07/install-gnome3-on-ubuntu-1104.html)
And now I need to uninstall it to get back to my beloved Unity layout, please help.

P.S. I did try the command to revert everything, but it did not work, so is there a manual way to uninstall or another command or anything to save my system!

---

### Post by androssofer on 2011-08-16
> **the-new-x said:**
> Hello guys, this is urgent, I need help, I have installed gnome 3 because it seemed to be good, but now things have went terribly wrong, neither unity, and nor gnome 3 are acting as they should! I follower the instructions from this website: [http://linux4every1.blogspot.com/2011/07/install-gnome3-on-ubuntu-1104.html](http://linux4every1.blogspot.com/2011/07/install-gnome3-on-ubuntu-1104.html)
And now I need to uninstall it to get back to my beloved Unity layout, please help.

P.S. I did try the command to revert everything, but it did not work, so is there a manual way to uninstall or another command or anything to save my system!

gnome3 breaks unity, but its meant to start working again once you uninstall gnome3. or so i heard... uninstall:

```
sudo apt-get install ppa-purge sudo ppa-purge ppa:gnome3-team/gnome3
```
once u uninstalled gnome3 try:

```
apt-get --reinstall install unity
```

---

### Post by the-new-x on 2011-08-16
> **androssofer said:**
> gnome3 breaks unity, but its meant to start working again once you uninstall gnome3. or so i heard... uninstall:

```
sudo apt-get install ppa-purge sudo ppa-purge ppa:gnome3-team/gnome3
```
once u uninstalled gnome3 try:

```
apt-get --reinstall install unity
```
I tried this command and this is the error I am getting:

tatah@Satellite-A505:~$ sudo apt-get install ppa-purge sudo ppa-purge ppa:gnome3-team/gnome3
[sudo] password for tatah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ppa:gnome3-team


Please Help!

---

### Post by androssofer on 2011-08-16
> **the-new-x said:**
> I tried this command and this is the error I am getting:

tatah@Satellite-A505:~$ sudo apt-get install ppa-purge sudo ppa-purge ppa:gnome3-team/gnome3
[sudo] password for tatah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ppa:gnome3-team


Please Help!

looks like gnome3 is gone. try the unity commnd... when u boot what comes up?

---

### Post by the-new-x on 2011-08-16
> **androssofer said:**
> looks like gnome3 is gone. try the unity commnd... when u boot what comes up?
just tried the command (you forgot to put "sudo" in the beginning, good thing I read a little bit about what the sudo command does, it makes you do the command as root) and all went find with the command, I will try to reboot now, if you don't hear from me in 5 min, then come to Lebanon (a third world country in the middle east) with a live CD of Ubuntu, because I am never going back to windows! LOL...

And btw, when I boot up (already restarted the computer more than 5 times) a blue screen appears instead of the usual purple one (when I type in my username and password to be more exact)

Restarting now...

---

### Post by cbowman57 on 2011-08-16
> sudo apt-get install ppa-purge sudo ppa-purge ppa:gnome3-team/gnome3Should be ```
sudo apt-get install ppa-purge && sudo ppa-purge ppa:gnome3-team/gnome3
```

---

### Post by the-new-x on 2011-08-16
I have restarted the computer, the blue screen is still there, when I typed my password directly, it logged me to the gnome 3 layout, which is still as before not stable and well, screwed up, so I logged out and now I am still in the messed up unity layout!

---

### Post by the-new-x on 2011-08-16
> **cbowman57 said:**
> Should be ```
sudo apt-get install ppa-purge && sudo ppa-purge ppa:gnome3-team/gnome3
```
I am trying this command right now, it needs to download 2.3 MB of data, will take around 3 minutes to finish (I live in a third world country), hope it works!!

---

### Post by the-new-x on 2011-08-16
My terminal freezed right here:

tatah@Satellite-A505:~$ sudo apt-get install ppa-purge && sudo ppa-purge ppa:gnome3-team/gnome3
[sudo] password for tatah: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libexpat1-dev debhelper libxi-dev po-debconf libpixman-1-dev
  libfontconfig1-dev libatk1.0-dev libcairo-script-interpreter2
  libxcb-shm0-dev libcairo2-dev libpango1.0-dev libfreetype6-dev
  libxcb-render0-dev xorg-sgml-doctools html2text libxft-dev libgtk2.0-dev
  libmail-sendmail-perl libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude libcwidget3
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
The following NEW packages will be installed:
  aptitude libcwidget3 ppa-purge
0 upgraded, 3 newly installed, 0 to remove and 40 not upgraded.
Need to get 2,821 kB of archives.
After this operation, 8,651 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/main libcwidget3 amd64 0.5.16-3ubuntu2 [445 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/main aptitude amd64 0.6.3-3.2ubuntu1 [2,372 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty/universe ppa-purge all 0.2.8+bzr56 [4,360 B]
Fetched 2,821 kB in 2min 57s (15.9 kB/s)                                       
Selecting previously deselected package libcwidget3.
(Reading database ... 248609 files and directories currently installed.)
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3ubuntu2_amd64.deb) ...
Selecting previously deselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.3-3.2ubuntu1_amd64.deb) ...
Selecting previously deselected package ppa-purge.
Unpacking ppa-purge (from .../ppa-purge_0.2.8+bzr56_all.deb) ...
Processing triggers for man-db ...
Setting up libcwidget3 (0.5.16-3ubuntu2) ...
Setting up aptitude (0.6.3-3.2ubuntu1) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up ppa-purge (0.2.8+bzr56) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Updating packages lists



First time it freezes, does this mean that I'm in a real trouble!!?

---

### Post by androssofer on 2011-08-16
> **the-new-x said:**
> My terminal freezed right here:

First time it freezes, does this mean that I'm in a real trouble!!?

still froze? might just be taking a while to complete....

---

### Post by the-new-x on 2011-08-16
and just to show you guys that things are really messed up in my case right now, I have lost my wifi driver (I am now sitting on the ground with my laptop in front of me using a spare and very short Ethernet wire to connect to the Internet) and I have lost the click function of my touchpad, these are the things that I know of right now, who knows what else can happen...
Oh and now I can't see the close, minimize, and maximize buttons on top of my windows!

---

### Post by cbowman57 on 2011-08-16
Good question, try rebooting, then just run the second of those two commands ```
sudo ppa-purge ppa:gnome3-team/gnome3
```

Then ```
sudo apt-get --reinstall install unity
```

Since I have spent most of my efforts getting rid of Unity & making my system Gnome 3.0 only I'm not certain what you are going to encounter trying to do this.

---

### Post by the-new-x on 2011-08-16
> **androssofer said:**
> still froze? might just be taking a while to complete....
It worked, looks like my laptop is running much much slower than usual today!!

---

### Post by the-new-x on 2011-08-16
What is so special about gnome 3 anyways, because all I had from it was trouble!

---

### Post by the-new-x on 2011-08-16
Oh great, now it needs to download more than 67 MB in order to remove 287 MB, how worst can my day go!! (these will take more than an hour to continue, so I will get back to you guys afterwards, sitting in front of the laptop right now it just pain!!!)

---

### Post by cbowman57 on 2011-08-16
> **the-new-x said:**
> What is so special about gnome 3 anyways, because all I had from it was trouble!

It is a little system intensive, might be hard for your laptop to run it.

For me it's just more intuitive, easier to use, than Unity.  I think it's just a personal preference thing.  Find what you like, and works for you, and stick with it. :)

---

### Post by androssofer on 2011-08-16
> **cbowman57 said:**
>   I think it's just a personal preference thing.  Find what you like, and works for you, and stick with it. :)

+1 the essence of open source in a sentence :-)

---

### Post by cbowman57 on 2011-08-16
> **androssofer said:**
> +1 the essence of open source in a sentence :-)

Exactly, if more people adopted that philosophy instead of elevating a DE, distro or OS to cult status we'd all be better off. :)

---

### Post by the-new-x on 2011-08-16
Way to open up the open source spirit...

The download is at 70% now, will tell you when it is finished.

And about my laptop, I think it can easily run it, I have 4GB DDR2 with core 2 duo processor at 2.1GHz, so I guess it is more than enough, I think that it is my Internet that screwed everything up, since gnome 3 is a relatively big file, and something might have went wrong during the download which corrupted the system, I will make sure to give it another shot another day, as for now, I will stick with unity simply because it is the first Ubuntu layout that I have ever tried (I have installed Ubuntu around a week ago, and it is my first Linux distro!)

---

### Post by cbowman57 on 2011-08-16
Good idea, get familiar with the defaults first before you experiment.

Your laptop should have no problem running Unity or Gnome 3.0 if you choose to at a later date.

---

### Post by the-new-x on 2011-08-16
OK, i went away for a while, and now I am back, I found that the command was complete, but while reviewing, I noticed that it can't find certain things, but it continued normally after a while, and when I closed the terminal, I found that the update manager windows had shown up with some updates that were downloaded but not installed (I believe that those are from the command) so I installed them, and now I will restart, see you afterwards!

---

### Post by the-new-x on 2011-08-16
It worked, it is good to be back, thank you guys, you are the best, I hope that someday I will know all the commands you do and help others that are trying to learn as myself, again, thank you!
And speaking of which, how do you know all these commands, do you memorize them, write them down in a document, have an e-book of some kind designed for that or what, if you have any resources, please share them with me!

---

### Post by cbowman57 on 2011-08-16
Spent a lot of time with google & in this forum. :)

If you stay with linux long enough it will become pretty easy.

---

### Post by the-new-x on 2011-08-16
> **cbowman57 said:**
> Spent a lot of time with google & in this forum. :)

If you stay with linux long enough it will become pretty easy.
I'm never planning to leave Linux, trust me, I have seen the light!
So hopefully a couple more weeks and I will understand everything I need to know about Linux, and in a couple of months, I will understand everything that I don't need to know about Linux!
So thanks again people, and cbowman57, you're a life saver!

---

