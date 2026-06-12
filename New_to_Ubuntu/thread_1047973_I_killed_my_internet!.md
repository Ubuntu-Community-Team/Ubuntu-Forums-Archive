---
title: "I killed my internet!"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by weazx on 2009-01-22
This thread is cross-posted over at the kubuntu forums, postng here for more views.

> 
In trying to set a static IP I managed to mess up my connection, and in trying to fix it (following some useless guide) I totally killed my connection.  that means no network manager or ifconfig; they're just not installed.

So, how can I reset my connection to what it was (default config)?  *Please*, I finally got my sound and video working correctly, I'm not wanting to do a full reinstall.

I do have an install CD, if that would help me at all.  I didn't see a "repair" option (that would be a really nice feature!!), but maybe there's some way of pullout out the files I need?

Kubuntu 8.1 (intrepid) 64 bit

---

### Post by handydan918 on 2009-01-22
1) Not nearly enough info here. How did you "kill internet"? 
2) Why are you trying to set up static IP? Do you even know?
3) why is a noob using 64 bit? There are still things (like grapics and sound) that can be really problematic in 64 that just work in 32.

---

### Post by sleepyjon on 2009-01-22
Enable the cd in your sources. There's a gui for it but I don't know where it is under kde.

Then pop the cd in, load up synaptic or adept or whatever the package manager in kubuntu is, reload the packages, and install networkmanager & ifconfig.

---

### Post by weazx on 2009-01-23
Well long story short I slayed the web by uninstalling ... I can't remember (and I can't find that guide I used) with apt-get remove [x], but I do recall seeing what looked like everything related to networking being uninstalled, including the network manager.  That's what it looked like, but I'm just a newb.

Also, /etc/network/interfaces was wiped clean.  I tried pasting this into interfaces

auto lo
iface lo inet loopback

which I pulled from the live cd, but that alone did not work.  

Enough info?  I'm trying to find out what exactly, I did.

*edit* also also, I didn't even see sleepyjon's post.  I'll try that first

*superedit* 

okay so i did

sudo apt-get remove --purge network-manager net-tools

without thinking.  Yes it was stupid.  The plan was to apt-get it all back, but of course I hadn't realized that you can't apt-get without a connection.

Sleepyjon, I can't find where to enable cd as a source.  Does anyone else know?  Google is not being very helpful.

---

### Post by jamesrl on 2009-01-23
Go to synaptic -> Settings -> Repositories.
On the first page, there should be enable CD-ROM dvd towards the bottom.

---

### Post by weazx on 2009-01-23
I'm afraid I don't have gnome, just KDE.  The most likely place I would find the command in adept would be in "views" (says google), but my "views" menu is completely empty.

I think I'm just going to reinstall, and back up what I can on my external.  Thanks for your help everyone.

Except handydan, he was a real jerk.  People like that are part of the reason people get frustrated when trying to make the switch.  To answer your last 2 questions:

2) yes i know
3) yes, i know
 I'm not as noob as you think...

---

### Post by weazx on 2009-01-23
If anyone ever needs to know, to add a cd to adept's sources go to 

Sources -> Edit sources -> Third-party

It's so obvious I missed it.

---

### Post by sleepyjon on 2009-01-23
> **weazx said:**
> If anyone ever needs to know, to add a cd to adept's sources go to 

Sources -> Edit sources -> Third-party

It's so obvious I missed it.

Good to know you got it. Did it work?

---

### Post by halovivek on 2009-01-23
> **weazx said:**
> If anyone ever needs to know, to add a cd to adept's sources go to 

Sources -> Edit sources -> Third-party

It's so obvious I missed it.

Have you solved the problem?

---

