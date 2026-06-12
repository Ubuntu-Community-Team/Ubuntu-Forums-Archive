---
title: "Ubuntu says i don't have enough space"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by bobayoga on 2009-07-15
Hello, all! I am a total noob at Ubuntu and Linux. And I've recently installed Ubuntu, which works great, but I've run into a problem:

Whenever I try to download stuff, anything, really, Ubuntu says I don't have enough space on the disk. as if Ubuntu created its own "Virtual Disk" and doesn't want to read my hard drive disk

I've read about this and, honestly, I don't understand "BEEP". People are either talking about commands that you have too enter in the terminal, which I do but it doesn't do anything.

Either that or they're talking about a Live CD thing or something.

Please... I don't know anything about Linux and I would like some very very very very specific help. It would be very appreciated.

oh. And I've also run into another weird problem. Now for some reason the "back" button on my firefox browser doesn't work at all.... And it's a button I tend to use a lot.

Thanks in advance for your help.

---

### Post by philinux on 2009-07-15
Use this in a terminal and report back.
Applications>accessories >terminal.
```
df -h
```

---

### Post by ramnarayan on 2009-07-15
go to Applications _> Accessories -> Terminal

and type exactly what is below and press enter

uname -r

use the mouse to select but for copy you have to use ctrl+shift to copy the selected area

paste the results here

similarly type the following command

sudo df -h

and paste these results also here

this will help us know what your system is like and maybe understand the problem better

---

### Post by bobayoga on 2009-07-15
I really thank you a lot for trying to help me... but now I've got another completely different problem.

I cannot report back because now, for some reason, my firefox browser not only doens't let me use the "back" button, but it doesn't let me log in to this forum. when I type my username and password and I press enter, the password dissapears. Right now I'm using vista... Is tehre anyway to... I don't know.. reinstall Firefox or something?

---

### Post by ramnarayan on 2009-07-15
> **bobayoga said:**
>  Right now I'm using vista... Is tehre anyway to... I don't know.. reinstall Firefox or something?

Firefox on Vista

hmmm.. no idea maybe you can try and download opera or something and see if that works

till you resolve your problem

alternatively why not try a live session of Ubuntu and see what all works (am sure Firefox) won't cause the same trouble there

---

### Post by bobayoga on 2009-07-15
No, I mean. Within Ubuntu, Firefox doesn't work properly.

When I said that I was using Vista I meant that I went back in here (In vista) so I can talk to you because the firefox browser I have on Ubuntu doesn't let me log in because the "password disappearing" issue.

---

### Post by running_rabbit07 on 2009-07-15
> **ramnarayan said:**
> Firefox on Vista

hmmm.. no idea maybe you can try and download opera or something and see if that works

till you resolve your problem

alternatively why not try a live session of Ubuntu and see what all works (am sure Firefox) won't cause the same trouble there

I love it when people don't read before they type.

The guy asked for help with the FF on his Ubuntu that he is having problems with.

---

### Post by bobayoga on 2009-07-15
OKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKK !!! I somehow managed to get rid of the fire fox problem for now. SOOOO


here is what I get when I enter the df -h thing:

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       17G   16G   58M 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  112K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  164K  1.5G   1% /dev
tmpfs                 1.5G  484K  1.5G   1% /dev/shm
/dev/sda2             289G  204G   85G  71% /host
lrm                   1.5G  2.2M  1.5G   1% /lib/modules/2.6.28-13-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
bobayoga@ubuntu:~$ 

And this is what I get when I enter uname -r

2.6.28-13-generic


I'm sorry for bustin your balls with the Fire Fox thing... I don't know why all of a sudden it works fine now... but ehh. Thanks again in advance for your help.

---

### Post by running_rabbit07 on 2009-07-15
> **bobayoga said:**
> I really thank you a lot for trying to help me... but now I've got another completely different problem.

I cannot report back because now, for some reason, my firefox browser not only doens't let me use the "back" button, but it doesn't let me log in to this forum. when I type my username and password and I press enter, the password dissapears. Right now I'm using vista... Is tehre anyway to... I don't know.. reinstall Firefox or something?

Go to System> Administration>Synaptic Package Manager and search for firefox, scroll down to and click on firefox-3.0. When you see it the box should be green, when you click on it, it should offer you a few options, click on "mark for reinstallation" and then click the Apply command at the top of the box. After that is done your firefox aka FF should work fine. You may need to add some add-ons to make all the web pages work such as Java and what not.

After fixing FF you can run and post the commands that the other guys have posted to help with you storage problems.

["How to get the best help."]("http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/") by AYSIU

---

### Post by ramnarayan on 2009-07-15
> **bobayoga said:**
> OKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKKK !!! I somehow managed to get rid of the fire fox problem for now. SOOOO


here is what I get when I enter the df -h thing:

Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       17G   16G   58M 100% /


it seems your root section (which i think also includes your /home) has run out of space and that is the cause of your problem

you either need to add another disk or clean up your / (and /home) so that you can get on with life

---

### Post by bobayoga on 2009-07-15
> **ramnarayan said:**
> it seems your root section (which i think also includes your /home) has run out of space and that is the cause of your problem

you either need to add another disk or clean up your / (and /home) so that you can get on with life


As I mentionned above, I'm a total idiot. So, thank you for your answer, but... how do i do that? (add another disk or clean)

thank you

---

### Post by ramnarayan on 2009-07-15
your df -h does not show a /home

which indicates that it is not separate from your / (or /root) partition

am not sure if its possible to move an existing /home to a new partition  just check around for that.

You have a 
/dev/sda2 289G 204G 85G 71% /host

which seems to have enough free space for you to create an additional partition for home 

If need be back up your home to this place and then reinstall Ubuntu with a better partitioning structure

again ask / check around for a suitable partitioning scheme

Some of the norms are
1. Don't keep Root and home together (if your root gets messed up then your home (or hwhere your data is also gets messed up)
2. Create Swap - usually twice your RAM
3. If Linux is your main OS then have about 100 MB of /boot

this i think is the minimum

---

### Post by Wim Sturkenboom on 2009-07-15
You still have some place on /host. Not sure what it is (not an usual Ubuntu directory as far as I know) but you can move some of your music, movies or whatever on there for a while.

And next you must find a solution for your disk problem as it will happen again. Is adding a new disk an option? If so, let us know and we can guide you through it.

---

### Post by running_rabbit07 on 2009-07-15
One thing that may help us see what is going on would be to open System>Administration>System Monitor and click on the File Systems tab and take a screenshot. You can take a screen shot via Applications>Accessories>Take Screenshot. And post it. There is an attachment adder in the screen where you type your post.

It should look something like my attachment.

---

### Post by ramnarayan on 2009-07-15
> **bobayoga said:**
> As I mentionned above, I'm a total idiot. So, thank you for your answer, but... how do i do that? (add another disk or clean)

thank you

to free up some space try
in terminal

```
sudo apt-get clean
```

To add another disk - i guess you need to buy one and put it on (if its a Desktop) 
However your HD seems to have enough space its a question of moving /home there

if you cannot move /home then you could create a new partition out of your /dev/sda2 and keep all your data there and make sure your /(root) partition does not fill up. 

This requires constant awareness as all work by default ends up in /home

**
finally maybe you could think of reinstalling and doing a new scheme of partitioning

---

### Post by running_rabbit07 on 2009-07-15
> **Wim Sturkenboom said:**
> You still have some place on /host. Not sure what it is (not an usual Ubuntu directory as far as I know) but you can move some of your music, movies or whatever on there for a while.

And next you must find a solution for your disk problem as it will happen again. Is adding a new disk an option? If so, let us know and we can guide you through it.

Or he may need to make the partition bigger.  Whichever is more convenient.

---

### Post by bobayoga on 2009-07-15
here it is

---

### Post by running_rabbit07 on 2009-07-15
> **bobayoga said:**
> here it is

It does look like you have plenty of space. Did you set up a Linux swap when you installed? How big is it? How big is your RAM?

---

### Post by bobayoga on 2009-07-15
Welll... I don't know if this is what you mean but when I bought my computer the guy said it have 4 GB of RAM

---

### Post by Wim Sturkenboom on 2009-07-15
> **ramnarayan said:**
> am not sure if its possible to move an existing /home to a new partition  just check around for that.
Yes, it is.
[LIST=1]
[*]Create new partition and format it.
[*][COLOR="Red"]Make backup of all important data[/COLOR]
[*]Reboot to single user mode so there is no risk that the original home directory is in use.
[*]Create a mountpoint (e.g. in /media) and mount the partition.
[*]Copy the files (making sure that you preserve the permissions, ownership etc).
[*]Delete the content of /home; you can not move the file as the *mv* command can not preserve permissions,ownership etc.
[*]Unmount the new partition.
[*]Create an entry in /etc/fstab for your new partition so it gets mounted on /home
[*]Testdrive by mounting /home and cd'ing to it.
[*]Reboot.
[/LIST]
This only describes the steps, not the actual commands. We will get there when OP wants to do the steps.

---

### Post by ramnarayan on 2009-07-15
> **Wim Sturkenboom said:**
> Yes, it is.


Nice, now i have one less worry when its required

thanks

---

### Post by running_rabbit07 on 2009-07-15
One way to clean up space is to use Computer Janitor under System>Administration. If the program isn't there you can find it in Synaptic Package Manager. I included a screenshot of it in Synaptic just in case. I have never used that program so I have no clue how well it will work.

---

### Post by bobayoga on 2009-07-15
I DO want to do the steps. I know I'm being annoying but I would actually need steps to do the steps... :P (I'm trying to be cute so you don't get tired of trying to help me)

ORRR .. someone talked about reinstalling ubuntu completely with some better partition or whatever... so do i just go into vista.. then find ubuntu, then uninstall it, then reinstall the whole thing?? 

But up to that point how do i make the partitions better WHAT IS a partition? I'M totaly lost. I thought Ubuntu would solve all my problems but it seems no matter what your system runs on.. computers are bullshisle.

But don't get me wrong I wanna keep trying.

---

### Post by Wim Sturkenboom on 2009-07-15
[quote=]here is what I get when I enter the df -h thing:

Filesystem Size Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
17G 16G 58M 100% /
tmpfs 1.5G 0 1.5G 0% /lib/init/rw
varrun 1.5G 112K 1.5G 1% /var/run
varlock 1.5G 0 1.5G 0% /var/lock
udev 1.5G 164K 1.5G 1% /dev
tmpfs 1.5G 484K 1.5G 1% /dev/shm
/dev/sda2 289G 204G 85G 71% /host
lrm 1.5G 2.2M 1.5G 1% /lib/modules/2.6.28-13-generic/volatile
overflow 1.0M 16K 1008K 2% /tmp
bobayoga@ubuntu:~$ 
[/quote]
[QUOTE=bobayoga]here it is[/QUOTE]
They don't seem to match. What am I or are we missing. And why is there a /boot of nearly 290GB without a file system.

I have no experience with Wubi, but can this be a Wubi install?

---

### Post by bobayoga on 2009-07-15
Hey I got another idea... tell me what you think... It seems I only have like 20 GB or so with the "home" folder of Ubuntu.

But the "Host" folder has all my old stuff that I have on vista... so what if i just transfer everything there, and each time I want to downlaod somehting, everytime it finishes to download i transfer it to host?

yeah sorry if some of my sentences don'T make sense English is not my first Language

---

### Post by running_rabbit07 on 2009-07-15
> **Wim Sturkenboom said:**
> They don't seem to match. What am I or are we missing. And why is there a /boot of nearly 290GB without a file system.

I have no experience with Wubi, but can this be a Wubi install?


Seems likely.

---

### Post by Wim Sturkenboom on 2009-07-15
> **bobayoga said:**
> Hey I got another idea... tell me what you think... It seems I only have like 20 GB or so with the "home" folder of Ubuntu.

But the "Host" folder has all my old stuff that I have on vista... so what if i just transfer everything there, and each time I want to downlaod somehting, everytime it finishes to download i transfer it to host?

yeah sorry if some of my sentences don'T make sense English is not my first Language
That only treats the symptoms, but does not cure the disease :) If you want to and can work like that, it will do the trick but I think that you eventually you will get sick an tired of that.

Can you indicate what your main operating system is. Do you do most of your work in Windows or do you most of it in Linux. This might determine the advice with regards to a new install of both Windows and Ubuntu if it gets to that point. Also the size of your HD (320GB ?).

I don't have a clue how Wubi works. Can it be un-installed and re-installed with more disk space?

---

### Post by bobayoga on 2009-07-15
I've never used linux until today. I usualy use Windows Vista

---

### Post by running_rabbit07 on 2009-07-15
> **Wim Sturkenboom said:**
> 

I don't have a clue how Wubi works. Can it be un-installed and re-installed with more disk space?

When I originally installed Ubuntu it was with Wubi and it didn't offer any size settings. Uninstalling was very easy though. Just went to Add/Remove in Windows and clicked uninstall and took like 2 seconds. 

Installing as an OS should fix all those problems.

---

### Post by running_rabbit07 on 2009-07-15
> **bobayoga said:**
> I've never used linux until today. I usualy use Windows Vista


I would recommend not changing any settings and just playing around with it until you are familiar with Ubuntu and when you decide you really want it on your system, install it in it's own partition. 

Wubi is okay for sampling Ubuntu but you can't get the full effect until it is separate.

---

### Post by bobayoga on 2009-07-15
All right thanks a lot to every body for your help. :)

Have a nice day

---

