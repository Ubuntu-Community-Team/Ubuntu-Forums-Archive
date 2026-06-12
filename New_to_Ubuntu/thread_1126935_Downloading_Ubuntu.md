---
title: "Downloading Ubuntu"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Michael1122 on 2009-04-15
I am downloading Ubuntu now and I am just wanting to make sure that the download will walk me through everything that is needed to get this system up and running.  Also, will the download take windows XP off of my system or do I have to do that myself.

Do I need to have antivirus software once this is loaded with Mozilla?

---

### Post by |Mitch| on 2009-04-15
Welcome to the dark side!

When you boot off the cd, you have the ability to set partitions however you please. I suggest dual booting or just running from the cd,  until you're absolutely sure that all your hardware is supported and there are 0 major problems. 

By nature, Ubuntu is a lot more secure than Windows. There really is no need to run a anti-virus, mostly all viruses are windows attacking.

Burn the image at a slow speed, and check the cd for errors before going ahead and trying to install. When you boot off the cd, you will see the option. 
If you burn to quickly, you run the risk of a *corrupted* installation.

---

### Post by LesterPalooza on 2009-04-16
Touche.

Use a hash code checker MD5Sum to check if the CD was *downloaded* from the server correctly.

---

### Post by presence1960 on 2009-04-16
> **Michael1122 said:**
> I am downloading Ubuntu now and I am just wanting to make sure that the download will walk me through everything that is needed to get this system up and running.  Also, will the download take windows XP off of my system or do I have to do that myself.

Do I need to have antivirus software once this is loaded with Mozilla?

You have the choice of keeping windows or wiping it when the partitioner starts during the install. Here is a link [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) I would recommend keeping windows until you are comfortable and confident enough with Linux, this way you have something to fall back on if you get jammed up and can't find a fix right away.

for security check this out [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by iiiears on 2009-04-16
> **LesterPalooza said:**
> Touche.

Use a hash code checker MD5Sum to check if the CD was *downloaded* from the server correctly.

That is an excellent idea. Because there are so many different applications and even scripts to do this in Windows and some are overly intrusive, large and complex it is easy to recommend.

GNU 
[http://www.gnu.org/software/coreutils/](http://www.gnu.org/software/coreutils/)

File Checker Integrity verifier. (fciv)
[http://support.microsoft.com/kb/841290](http://support.microsoft.com/kb/841290)

Python Script.
[http://code.activestate.com/recipes/266486/](http://code.activestate.com/recipes/266486/)

~ Best Wishes

---

### Post by FredB on 2009-04-16
The simplest and best way to have a good ISO image is to use a bittorrent link. Every single piece is checked on download. Using bittorrent for ISO downloading since Ubuntu Dapper Drake (6.06 LTS).

---

### Post by InfectedWithDrew on 2009-04-16
When you pop the CD in and reboot your system, the computer will boot from CD.  (Unless your BIOS is set up strangely, in that case, you will have to modify your boot order which isn't hard to do.)

Then you can check to see if the CD is healthy from inside the CD.  Chances are it is, especially if you burned it at a low speed.

After that, I suggest you select "Try Ubuntu" instead of "Install Ubuntu."  You will load a live CD session, and from there you can do whatever you'd like.  Since you seem to want to keep Windows XP, you can partition your drive from here.  Or, you can just see if you like what Ubuntu looks and feels like (though it will be very slow on the CD), and then you can boot into Windows again and install via Wubi.

---

### Post by Sef on 2009-04-16
For downloading, burning, and installing Ubuntu as a dual boot system, read [Psychocats Ubuntu Linux]("http://psychocats.net/ubuntu").

---

### Post by lukjad on 2009-04-16
I will break up your post into questions and do my best to answer them.

> **Michael1122 said:**
> I am downloading Ubuntu now and I am just wanting to make sure that the download will walk me through everything that is needed to get this system up and running.

I find the **GUI** (**G**raphical **U**ser **I**nterface) installation to be very simple and straightforward and simple. Some things may be confusing, like partitioning, but since you seem to wish to use only Ubuntu, you should be fine.

> **Michael1122 said:**
> Also, will the download take windows XP off of my system or do I have to do that myself.

It can wipe XP off your system, but I should warn you that all files and folders that you have on XP will be lost unless you back them up to an external hard drive or to a CD/DVD. If you don't have anything you want, feel free to "Use Entire Disk".

If you don't, post here and someone will explain how to divide your hard drive so that you can have both XP and Ubuntu on your computer.

> **Michael1122 said:**
> Do I need to have antivirus software once this is loaded with Mozilla?

I don't quite understand what you mean here. 

First of all, while there are some viruses out there, they are very rare, and most of them are useless today. There are always new threats that are found for Linux, but most of these are of limited use since they patched quickly. Keep your Ubuntu updated and all should be fine. 

If you mean ads that show up on the web, most of the popups are blocked out of the box with Firefox. There are two addons that I find to be extremely useful. The first is **[AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865")** and **[NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722")**.

---

