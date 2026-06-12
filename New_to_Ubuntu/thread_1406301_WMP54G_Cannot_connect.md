---
title: "WMP54G Cannot connect"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by Dukes24 on 2010-02-13
Good evening, 
 
After much review, I decided to switch from Windows XP to Ubuntu given some of the things I've read, one thing I missed however, was how hard it can be to just connect to the internet.
 
It would appear that my wireless card isn't really suited for this OS, however I've read a few posts that claimed to have a way to fix that, and I've tried just about everything I've read, such as:
 
1 - Download the driver and NDIS and install it. I've burned those files onto a CD from another computer in the house, with is running Windows 7, however Ubuntu does not reconize the CD, and won't let me open it, but my other computer reconizes and allows me to open it.
 
2 - I've loaded the boot CD, and searched for NDIS, however no file was found.
 
The biggest problem I face right now is that my computer cannot connect to the internet as I can't reach it with an ethernet cable. 
 
Can someone try and help me out with this? I really like what I see so far, and would like to keep it, but I've been reading and trying things for the last 4 hours, and my patience is wearing thin...
 
Any input would be greatly appreciated.
 
Cheers

---

### Post by coldfusion1313 on 2010-02-13
I have the same card and it is working fin in ubuntu, which version are you running?

---

### Post by Dukes24 on 2010-02-13
I took it out of the system and couldn't find a version number, so I'm assuming it's 1.0.  It worked fine when I was using Windows XP

---

### Post by Dukes24 on 2010-02-13
Is it maybe because I'm using a WPA connection?  Would a WEP be better?

---

### Post by Dukes24 on 2010-02-13
Can no one help me?

---

### Post by Dukes24 on 2010-02-14
Alright, I figured out how to get connection, however now my system won't boot without the CD, it just goes straight to a black screen, and when I do get it to boot with the CD, it'll freeze after about 10 minutes of usage.

After uninstalling, and reinstalling, I've come to the conclusion that the update that I do to get connection is the cause of the problem.  One of the files that I am updating is causing an error with my system, so my question now is, how do I install just the one file.  

After I reinstalled 9.10, my system booted up no problem, and was not freezing, then I did this:

Went to the system repository, loaded the CD update, hit reload, and had some files, 7/15 install, the rest went to error because I'm still not connected to the internet at that point.  Once that finished, I loaded the BCMWL Kernel Source, which is what I need to get the system to recognize my wireless card, and rebooted my computer.  Now my system won't boot up again without the CD, and freezes when I boot with the CD.  What I think will work is if I can somehow just download and install that BCMWL Kernel file, without the rest.  I can't imagine that being that hard, so can someone help me out with this.

---

### Post by Dukes24 on 2010-02-14
Alright, I figured it out on my own, and I am now connected to the Internet, and it boots perfectly fine.  If anyone has trouble like I had, send me a message, I'll be more than willing to help you out, since it's impossible to get answers from anyone on here.

---

### Post by sois on 2010-06-09
Having the same problem.  Ubuntu 10.04.  WMP54G v 1.1 I think.

---

### Post by anewguy on 2010-06-10
> **Dukes24 said:**
> Alright, I figured it out on my own, and I am now connected to the Internet, and it boots perfectly fine.  If anyone has trouble like I had, send me a message, I'll be more than willing to help you out, since it's impossible to get answers from anyone on here.

If you had mentioned earlier that your problem was with a Broadcom chipset wireless adapter, you would have gotten plenty of replies.  In addition, there are *TONS* of posts on the forum and on the net for this.  So, if someone is having a problem like this, provide the following information first:

- open a terminal window (Applications/Accessories/Terminal)

- if the adapter is a USB adapter, or if you are having problems getting internal wireless to work on a laptop, type:

lsusb <press enter> Copy the output and post in the opening post for your thread

- if it is internal wireless on a laptop or desktop, type:

lspci <press enter> Look for something that would indicate a wireless adapter - as an example it might say Broadcom BCM4316 Air Force One.  Copy this output and post in the opening post for your thread

Also, for all wireless that isn't working, check in System/Administration/Hardware drivers and see if a restricted driver shows for the device.  If it is not enabled, enabled it.  

In addition, for a lot of the Broadcom devices, it comes in handy if you can temporarily hard-wire your PC to the router, then:

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo apt-get update <press enter> When prompted for a password just enter your regular password.  It won't show on the screen for security purposes, but type it anyway.

In addition, you may need to type:

sudo apt-get upgrade <press enter>

Then check again under System/Administration/Hardware Drivers and see if there is a driver listed for the device now.  If so, be sure it is enabled.

After you have added the driver via a hard-wired connection, disconnect the hard-wire cable, wait a couple of minutes.


If you are unable to get a driver working under the above instructions, or perhaps you have read about and want to use ndiswrapper, the following is for you:

Ndiswrapper is a utility which lets you use the Windows XP wireless drivers in Linux.  You may have seen other posts on ndiswrapper that required a lot of typing (even some of my own old posts).  For the most part, you can use a windowed front end to ndiswrapper that makes it easy to install your driver.  Here are the steps:

- if you have a network connection, go to Synaptic Package Manager and install ndiswrapper common and ndiswrapper utilities

- if you do not have a network connection:

Put the LiveCD in your drive.  After it spins up you may get a notice about a disk with software packages was detected.  Just cancel out of that.

Via "Places", go to the media drive containing the LiveCD

Navigate to the pool/main/n folder.  You will find two subfolders there - one for ndisgtk and one for ndiswrapper.  We must do ndiswrapper first, so click on that folder to open it.  There you will find 2 files - one for ndiswrapper-common, and one for ndiswrapper-utilities.  Double click on the ndiswrapper-common file to begin installing it.  Once it finishes installing, double click on the ndiswrapper-utilities file to begin installing it.  When these 2 installations have finished, navigate back 1 folder level to the pool/main/n folder.  Locate the ndisgtk folder and click on it to open it.  Double click on the file there to begin installing it.  When it has finished you can exit the terminal by typing "exit" and pressing "enter".

Now you need the files for your Windows driver - there should be at least one .inf file and at least one .sys file.  Copy these files to your Ubuntu desktop.

Start ndisgtk via System/Administration/Windows Wireless Drivers.

When ndisgtk opens up, just "Add" and point it to the driver .inf file you placed on your desktop.

When it finishes it should show the device as active. 

For all:

Check in network manager to be sure that "Enable Wireless" is checked.

Now check to see if you have wireless access points showing in network manager.

Some devices do require more - if you have problems with ANY wireless adapter or instructions for setting it up, please gather the output of the lsusb and lspci commands as shown above, then open a thread being sure to post the outputs from the commands in your opening post.

I'm sorry you did not get the response you thought you deserved.  Maybe your thread went in at one of the times when a lot of us weren't watching and/or we just missed it.  Our apologies, and glad you got it working.

dave ;)

---

