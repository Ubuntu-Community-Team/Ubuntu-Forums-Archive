---
title: "Very first time with Ubuntu and don't know what to do next?"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by sehana on 2009-07-17
Very first time with Ubuntu and don't know what to do next?

I used a linux distro before but I forgot which it was, I believe it was knoppix. But that was a REALLY long time ago and it was given to me. I didn't have to burn it & ran the cd to boot up first and worked and ran off the disc didn't have to install it.

So I burned the Ubuntu 9.04 .iso file onto the disc and restarted the PC to boot the cd first, but nothing happened?

What am I s'posed to do? 

I have the old, but reliable XP. I don't want to install linux over windows or with windows just yet, but want to see what ubuntu is like before installing.

---

### Post by cozmicharlie on 2009-07-17
It should boot into the Ubuntu installer and show a list of options.  This should help.  
[https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html)

post back if you have problems.

---

### Post by michy99 on 2009-07-17
What exactly do you mean when you say nothing happened? Just a black screen or what?

---

### Post by howefield on 2009-07-17
> **sehana said:**
> I burned the Ubuntu 9.04 .iso file onto the disc and restarted the PC to boot the cd first, but nothing happened?

What am I s'posed to do?

Something must have "happened".

Are you saying the computer didn't boot at all ?

You could take the cd out of the drive and boot into windows, then put the cd back in and install Ubuntu via Wubi.

This will install Ubuntu as a file on your windows system, and sort out a boot menu from which you can select which operating system to boot,benefit of this being you can try out Ubuntu without getting into the difficulties of partitioning ect and can remove Ubuntu using windows add/remove programs wizard.

---

### Post by hibliss on 2009-07-17
For testing, Wubi is suggested over a liveCD trial. LiveCD will be slow. Wubi will be faster. A partitioned install will be best, once you know for sure that you like it.

---

### Post by sehana on 2009-07-17
oops what I mean is nothing happened and windows loaded still instead of the disc. I did change boot settings to boot cd first.

what is Wubi?

---

### Post by TeoBigusGeekus on 2009-07-17
Sorry if this sounds dumb, but did you create a data disk and put the iso file in or did you actually burn the iso _image_?

---

### Post by Tibuda on 2009-07-17
> **sehana said:**
> oops what I mean is nothing happened and windows loaded still instead of the disc. I did change boot settings to boot cd first.

what is Wubi?
What do you see in the CD from Windows Explorer?

About Wubi, see [http://wubi-installer.org/](http://wubi-installer.org/)

> Wubi is an officially supported Ubuntu installer for Windows users that can bring you to the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way. Are you curious about Linux and Ubuntu? Trying them out has never been easier!

---

### Post by sehana on 2009-07-17
LOL you know I think I just made a data disc!!
I'll have to try again monday.

To: [danielrmt]("http://ubuntuforums.org/member.php?u=702969")
Ah ok, Thanks

---

### Post by steveneddy on 2009-07-17
Make sure that you burn the CD as an image.

There are free versions of applications that are able to burn a proper .iso to your CD.

Look at this link:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

it is one of the links in my sig.

On the left you will see a link about burning your .iso

There is lots of info on this web page that may want to study for future reference.

At the very least book mark it.

Good luck.

Wubi sucks - dual boot or use Virtualbox if you want to install.

---

### Post by sehana on 2009-07-17
> **danielrmt said:**
> What do you see in the CD from Windows Explorer

just the ubuntu9.04.iso file

---

### Post by Tibuda on 2009-07-17
> **sehana said:**
> just the ubuntu9.04.iso file

It's because you have made a data disc with that file inside. This disc won't boot. See steveneddy advice.

---

### Post by sehana on 2009-07-20
Ok so I made the disc correctly this time and see the folders and files. I rebooted PC to boot the CD Drive first and XP started not the disc.

What am I doing wrong?

How do I use it like a Live CD where I can sample it without installing.
Because I would like to wait until I can get another hard drive to put Ubuntu on.

---

### Post by hibliss on 2009-07-20
> **steveneddy said:**
> 
Wubi sucks - dual boot or use Virtualbox if you want to install.

It is faster and easier than LiveCD and uninstallable from within Windows. For testing in a try before you buy situation, Wubi does not suck. For extended use, Wubi is not recommended.

Especially for someone having a hard time getting the LiveCD to even boot, Wubi is not a a bad testing option.

---

### Post by sehana on 2009-07-20
So just install it within windows to try it? and when finished uninstall?

---

### Post by /usr/sbin on 2009-07-20
Yes, I did that. But I am not sure how to get rid of the option to boot into ubuntu even when it is not installed. Sorry to hijack your thread.

---

### Post by hibliss on 2009-07-20
> **/usr/sbin said:**
> Yes, I did that. But I am not sure how to get rid of the option to boot into ubuntu even when it is not installed. Sorry to hijack your thread.

Start your own thread. There is an easy solution by editing either the boot.ini in XP or BCD in Vista. Google it.

@ OP, yes, do that. If you like it, uninstall and partition for the real thing.

---

### Post by sehana on 2009-07-20
Ok so I installed it and I liked it, but I will wait to install fully when hard drive arrives. 

So I uninstalled it and restarted PC.

At Boot it still asks whether I want to install XP or Ubuntu.
How to get rid of that?

---

### Post by hibliss on 2009-07-20
In XP, you need to edit the Boot.ini file to remove the Ubuntu entry.

Go to start>Run>type msconfig. Now go to the boot.ini tab and remove the Ubuntu entry.

---

### Post by sehana on 2009-07-20
Thanks that worked

---

