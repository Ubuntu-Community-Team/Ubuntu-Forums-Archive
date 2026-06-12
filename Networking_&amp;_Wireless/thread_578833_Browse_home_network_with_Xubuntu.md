---
title: "Browse home network with Xubuntu?"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by ~Maxx on 2007-10-17
Hey all...  It seems that this is likely a common issue for noobs (myself included).  But I've not been able to find a solution that isn't "over my head" (technically speaking).  Then again I'm just as new to networking as I am to Linux.

So what I have are two desktops in my office networked via only a crossover cable.  I have XP (Home) installed on my main PC, and the second one was recently switched from Ubuntu to Xubuntu (it's a Pent. II).  While running Ubuntu my network (including internet) seemed to have been configured properly (with little or no effort on my part).  Since changing to Xubuntu, however, I've yet to discover a way to access my main PC's shared files from my second machine.  Internet works fine in Xubuntu (modem is connected to XP PC).  

I found a how-to thread [here (<--- link)]("http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu"), but got stuck on step 3.  I have absolutely no idea what this step is trying to tell me to do.  If anyone would be willing to point me in the right direction (or if there's a better/more simple way to accomplish things) I'd sure appreciate some advice.  Anyone know if this is addressed in the upcoming Gutsy release?

Thanx a bunch...

~Maxx

---

### Post by Hero of Time on 2007-10-18
> **~Maxx said:**
> Hey all...  It seems that this is likely a common issue for noobs (myself included).  But I've not been able to find a solution that isn't "over my head" (technically speaking).  Then again I'm just as new to networking as I am to Linux.

So what I have are two desktops in my office networked via only a crossover cable.  I have XP (Home) installed on my main PC, and the second one was recently switched from Ubuntu to Xubuntu (it's a Pent. II).  While running Ubuntu my network (including internet) seemed to have been configured properly (with little or no effort on my part).  Since changing to Xubuntu, however, I've yet to discover a way to access my main PC's shared files from my second machine.  Internet works fine in Xubuntu (modem is connected to XP PC).  

I found a how-to thread [here (<--- link)]("http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu"), but got stuck on step 3.  I have absolutely no idea what this step is trying to tell me to do.  If anyone would be willing to point me in the right direction (or if there's a better/more simple way to accomplish things) I'd sure appreciate some advice.  Anyone know if this is addressed in the upcoming Gutsy release?

Thanx a bunch...

~Maxx
What you need to do is open that file, located in /etc/ with the name 'modules' and add the right words. Be sure that you open it with root privileges. E.g. at a terminal, run 'sudo nano /etc/modules', type your password and add fuse to the modules list.

---

### Post by ~Maxx on 2007-10-18
Thanx for the reply Hero.  It seems that "fuse" is already in the list though (how it got there I don't know).  Unfortunately this has only got me as far as step 6 (see below for quote from thread).  There must be something I'm not grasping about user privelages, because I am unable to create any folders within the Home directory or any of its subdirectories other than the directory for my user name.  And when I create a "Network" directory there and enter it with the recomended text in step 6.5 it states that "no such file" exists.

Sorry to be such a pain.  Thanx in advance for any advice...



[QUOTE=Tazix]Since Thunar doesn't have native network Browsing, here is a good way to accomplish it:

1) In XFCE's Applications -> System -> Shared Folders. (This should trigger a Samba install if you don't already have a share, and it should allow you to define the proper workgroup)

2) Install fusesmb in Synaptic (from Universe repository)

3) Edit /etc/modules and add the word 'fuse' to the modules list to be loaded (without quotes), and save the file.

4) Reboot, so the fuse module loads, and the proper workgroup is read for samba.

5) In XFCE Applications -> System -> Users and Groups... Properties of your username... User Priveleges Tab... check "Allow use of fuse file systems..."

6) Create a directory that you are going to mount your network browse to... I used /media/network. Change permissions to read / write for group and others (777).

*** 6.5) In a terminal, type: sudo chown <username>:fuse /media/network
(Where <username> is your user account logon name)

*** 6.6) Double check that the permission to use fuse took. Applications -> System -> Users and Groups... Manage Groups... find fuse and choose properties. Make sure your user name account is in that group and check-marked.

*** 6.7) Reboot the system and triple check with step 6.6

7) In XFCE Applications -> Settings -> Autostarted Applications... Add an application... name and describe as you wish... for command line, put: fusesmb /media/network (Or whatever mountoint you created).

Open Thunar, and navigate to the parent folder of your mountpoint... then drag the 'mounpoint folder' to the places (shortcut) pane of thunar.

9) Logout and log back in (So the user privilege and fusesmb autostart will take affect)

*** Added steps to help prevent some access denied issues some people have been experiencing with fusesmb.[/QUOTE]

---

### Post by Hero of Time on 2007-10-18
What you need to do, is when the mount is outside your home folder (/home/<username>) is to use sudo. In a terminal, type 'sudo mkdir /media/network' to create the network folder in the /media folder. As I followed these steps aswell without any problems, I find it strange that you don't understand this howto. Almost all howto's here are very simple to execute, even for newbies.

---

### Post by ~Maxx on 2007-10-18
> I find it strange that you don't understand this howto. Almost all howto's here are very simple to execute, even for newbies.
I couldn't agree more.  I'm not sure if I missed out on some core knowledge base that other noobs have found, or if I'm just plain dense (though I've never been accused of being such).  But I've certainly realized that the learning curve when transitioning from XP to Ubuntu (or Linux in general) is a bit more than I expected.  I've read the entire Help file for both Ubuntu and Xubuntu, but much of it seems to be written with the assumption that I have an understanding of certain other, more general things.  I intend to do a bit more research over the weekend, and hope to educate myself a bit more on the generalities of Linux and Ubuntu in order to avoid crawling to the forums every other day when I can't grasp something.

Thanx again for your reply.  I'll attempt the final steps of the tutorial after work tomorrow, and hopefully have things up and running properly.  

All the best!

~Maxx

---

