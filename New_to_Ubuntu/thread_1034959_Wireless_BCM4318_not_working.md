---
title: "Wireless BCM4318 not working"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Mortfish on 2009-01-09
Hi,
I decided to try out xubuntu v.8.10 Intrepid ibex on my old HP Pavilion ze2000 laptop in stead of reinstalling xp as it was getting extremely slow.  

The wireless card is Broadcom BCM4318(rev2).  I read that these cards can be tricky to set up.  I have tried two methods without success.  At the same time I read that this card is in fact supported in Intrepid: 
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4318)

I tried sudo lshw -C network and found the WLAN device is Disabled.

If the card it is supported, then what's the problem? Hope someone can point me in the right direction.

Thanks
M.

---

### Post by nothingspecial on 2009-01-09
Read this

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Tim Sharitt on 2009-01-09
What install method did you try?

---

### Post by Mortfish on 2009-01-09
OK thanks, I'll give it a shot!

---

### Post by Mortfish on 2009-01-09
Tim,
I tried this
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
I just did not understand that I needed to be connected via wire...

---

### Post by Tim Sharitt on 2009-01-09
First, do you have a way to get ubuntu online (ethernet cable). If not, do you have a way to download a file and access via ubuntu (for example, downloading in Windows to a usb stick, or accessing your windows partion via ubuntu)?

---

### Post by Mortfish on 2009-01-09
Yes, I can try with an ethernet cable. The wired connection is using pppoe, I have not tried to connect this way in xubuntu but i know how to set ut up in windows.  

I have a second laptop and memory stick, I used this last time to install ndiswrapper moving it from one computer to the other, along with the network driver files I found on the system CD.

---

### Post by Tim Sharitt on 2009-01-09
Download the following files to the USB stick
```
 http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2


```

Boot into Xubuntu and copy the file to your home folder.

Open a terminal and do
```

tar xjf b43-fwcutter-011.tar.bz2

cd b43-fwcutter-011

make

cd ..

tar xjf broadcom-wl-4.80.53.0.tar.bz2

cd broadcom-wl-4.80.53.0/kmod

sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware

wl_apsta.o

```

Reboot and see if your wireless card works.

---

### Post by Mortfish on 2009-01-09
Thanks, I will try this.
One strange thing; I pasted the links you provided into IE, but the files saved as "b43-fwcutter-011.tar.tar" and "broadcom-wl-4.80.53.0.tar.tar" instead of ending with "*.bz2". Do I need to rename them before copying to my home folder??

---

### Post by Tim Sharitt on 2009-01-09
> **Mortfish said:**
> Thanks, I will try this.
One strange thing; I pasted the links you provided into IE, but the files saved as "b43-fwcutter-011.tar.tar" and "broadcom-wl-4.80.53.0.tar.tar" instead of ending with "*.bz2". Do I need to rename them before copying to my home folder??
Yes, I think that would be a good idea.

Also, If you still have ndiswrapper installed, it needs to either be uninstalled or added to /etc/modprobe.d/blacklist
```
gksu gedit /etc/modprobe.d/blacklist
```
Just add it to the end, make sure it is on it's own line.

---

### Post by Mortfish on 2009-01-09
tar xjf broadcom-wl-4.80.53.0.tar.bz2

This command returns the following:
bzip2: (stdin) is not a bzip2 file.
tar: Child returns status 2
tar: Error exit delayed from previous errors

---

### Post by anewguy on 2009-01-09
The firmware cutter method is quite valid - its is ubuntu's attempt to provide a driver, so I would try this method again.  It would appear that somehow the file may have been renamed to the improper suffic - be sure it matches exactly what you were downloading before Windows added to the file name, and then try again.  However, I have had problems with that driver in the past, and ended up using ndiswrapper with the Windows driver.  That is another option I can give to you.  If you would like to try that way (it's actually quite painless :) ) let me know and I'll post step-by-step for you.  The only thing you will need is the install Cd (preferably the LiveCD) and a copy of your Windows driver.  These cards are normally a cinch to get working in ndiswrapper.

Dave :)

---

### Post by Mortfish on 2009-01-10
Oookido.. *sigh*
one inch from giving up here..

Yes, I'd like you to post the step-by-step method please.
I have the Windows drivers on a CD, and I have the possibility to download anything else on my other computer and move files to the xubuntu one with a USB stick.  I would prefer a method that do not require me to be online with the Xubuntu PC because I am not exactly sure how to this.

Thanks again.

---

### Post by anewguy on 2009-01-10
Sorry it took a while to get back here, but when I was trying last night the forum was down.

I think these steps should do it:

(1) install ndiswrapper and it's utilities (if available).  If you don't have a wired access to go through synaptic package manager and install it, then just put your LiveCD you installed from in the cd drive and navigate to the /pool/main/n/ or /pool/main/n/ndiswrapper (I forget the exact location right now) folder and double-click on the ndiswrapper things there to install them.

(2) copy your (remember - non-Vista) Windows driver files (the .inf and .sys files) for your wireless to a new folder - perhaps wireless_driver

(3) open a terminal window (applications/accessories/terminal)

(4) type:

cd {wherever you put your windows driver stuff} <press enter>

(5) type:

sudo ndiswrapper -l <press enter> that's a lower case "L" for "list", and the password will be your normal logon password

Hopefully nothing is returned.  If ndiswrapper does return any list of drivers installed, you must remove them first:

sudo ndiswrapper -e xxxxxx <enter> where xxxxxx is the driver name returned in (5)

repeat (5) until an empty list is returned

(6) sudo ndiswrapper -i xxxxxx.inf <enter> where xxxxxx is the name of the correct .inf file, the driver for your wireless. If you select the incorrect .inf, the wireless probably will not work.

sudo ndiswrapper -l <enter> List again, to be sure it shows your driver and does not show any errors associated with it

(7) sudo depmod -a <enter>

(8/) sudo modprobe ndiswrapper <enter>

(9) sudo gedit /etc/modules <enter> This will start up the graphical editor so we can edit the modules file.  Once the file shows on the screen, navigate to the bottom and add a new line as follows:

ndiswrapper

Now save the file and exit the editor.  The modules file contains "extra" kernel modules to be loaded at boot.  We added ndiswrapper so we can be sure it is started when you reboot.

(10) type:

cd /etc/modprobe.d <enter>

sudo gedit blacklist <enter>  This will open the blacklist file in the same editor so we can add to it:

Navigate to the bottom and add the following new line:

blacklist bcm43xx

Now save the file and exit the editor.  The blacklist file(s) tell Linux things not to load at boot.  In this case, there is a "skeleton" driver for the broadcom 43xx series of adapters that we have to stop from loading.  With 8.04 and 8.10 there might be 1 or 2 more, but let's start with just these for now.

(11) reboot

After reboot, click on your network manager icon and see if it shows any wireless networks. Be sure roaming is enabled under system/administration/network. If your router is set to not broadcast the network name, it will not show in network manager - you must select the "Connect to Other Wireless Network" option and manually enter in the network name and associated data such as wep or wpa information if used.

If for some reason network manager is not installed (you should see 2 little computers in the status line if it is), we'll need to install it.

Try this for now and post back with how things worked or if you have any questions and we can go from there.

Dave :)

---

### Post by Mortfish on 2009-01-12
I get to step 9.
Error message is "Sudo :gedit: Command not found"

---

### Post by nothingspecial on 2009-01-12
It should be ```
gksudo gedit
```

All lower case

---

### Post by anewguy on 2009-01-14
I apologize - you're running xubuntu.  What you want to do is edit the 2 files mentioned using an editor, whatever xubuntu has available, but run it as the super user (e.g., sudo), otherwise you won't be able to save the files.

I believe it would be in this syntax:

gksu mousepad /etc/modules <enter> for step 9

and

gksu mousepad blacklist <enter> for step 10


Let me know if that helps or not.

Sorry so late getting back to you - they seem to be working on the forums and I haven't had much luck getting in here until now.

Dave ;)

---

### Post by newbee70 on 2009-01-14
> **anewguy said:**
> The firmware cutter method is quite valid - its is ubuntu's attempt to provide a driver, so I would try this method again.  It would appear that somehow the file may have been renamed to the improper suffic - be sure it matches exactly what you were downloading before Windows added to the file name, and then try again.  However, I have had problems with that driver in the past, and ended up using ndiswrapper with the Windows driver.  That is another option I can give to you.  If you would like to try that way (it's actually quite painless :) ) let me know and I'll post step-by-step for you.  The only thing you will need is the install Cd (preferably the LiveCD) and a copy of your Windows driver.  These cards are normally a cinch to get working in ndiswrapper.

Dave :)

Dave, I had the same issue with ndiswrapper when trying to use bf43-fwcutter.  I found a "how to" that had me sudo apt-get purge "ndiswrapper" then install the b43-fwcutter; it ran and installed the needed driver.  ** but you have to be online with the computer that you are running b43-fwcutter on. **

---

### Post by Mortfish on 2009-01-14
Dear all 
I am very pleased to see that so many people are willing and eager to assist.  The problem has now been solved. What happened was that I got the computer hooked up via wire, it started to update xubuntu, and before I knew it it had installed fwcutter (I think), and the wireless was up and running in no time.

Thanks again.

---

### Post by anewguy on 2009-01-14
newbee70: 

Well, you don't use the firmware cutter and ndiswrapper together - it's either one or the other.  If you have already tried ndiswrapper and want to try the fwcutter method, you will need to remove ndiswrapper for /etc/modules and also run ndiswrapper with -e and remove any drivers it knows about.  As I mentioned earlier, the firmware cutter method is quite valid - I just have leaned a little towards ndiswrapper yet as there are some people who report problems with the firmware cutter method.  If you have tried it and now need to try ndiswrapper you would need to also add blacklist b43 to the end of /etc/modprob.d/blacklist.

Mortfish:

Great job - glad you got it working!

dave :)

---

### Post by newbee70 on 2009-01-14
> **anewguy said:**
> newbee70: 

Well, you don't use the firmware cutter and ndiswrapper together - it's either one or the other.  If you have already tried ndiswrapper and want to try the fwcutter method, you will need to remove ndiswrapper for /etc/modules and also run ndiswrapper with -e and remove any drivers it knows about.  As I mentioned earlier, the firmware cutter method is quite valid - I just have leaned a little towards ndiswrapper yet as there are some people who report problems with the firmware cutter method.  If you have tried it and now need to try ndiswrapper you would need to also add blacklist b43 to the end of /etc/modprob.d/blacklist.

Mortfish:

Great job - glad you got it working!

dave :)


anewguy,

I was not saying you were wrong, as a matter of fact I think you are very correct. All I was pointing out was if the ndiswrapper failed to work, it should be completely remove before trying the cutter method, and vice-versa.

Again you give good advice, which I would not be afraid of following.
And you make the forums a nice place to hang out, and 1)learn how to troubleshoot problems "by following the posts and asking questions". 2) learn what questions to ask in shooting specific problems. 3) useful commands to help isolate the issue. 4) Learning to understand what everyone is trying to put into words "learning to listen properly".

Again, If you took my statement as a rebuke of what info you were giving I apologize.

---

### Post by anewguy on 2009-01-14
> **newbee70 said:**
> anewguy,

I was not saying you were wrong, as a matter of fact I think you are very correct. All I was pointing out was if the ndiswrapper failed to work, it should be completely remove before trying the cutter method, and vice-versa.

Again you give good advice, which I would not be afraid of following.
And you make the forums a nice place to hang out, and 1)learn how to troubleshoot problems "by following the posts and asking questions". 2) learn what questions to ask in shooting specific problems. 3) useful commands to help isolate the issue. 4) Learning to understand what everyone is trying to put into words "learning to listen properly".

Again, If you took my statement as a rebuke of what info you were giving I apologize.

No, not at all!  I was only expanding a little upon what you posted.  No offense taken, and I sure hope none given - wasn't my intent!

I'm just like the rest of you - my bean count may be a different number but it's probably because I ask so many questions, not that I'm any good at this!.  I, too, hang out here to see how things are done, and when possible, try to pass that along to someone else in need.  Seems like when someone has gone to the trouble to voluntarily help someon, the least I can do after all the help I get is try to help someone else when I can.

Me stupid - just learning and passing it along!

No offense taken, and I sure apologize if it appeared I was disagreeing or anything with what you posted - it was quite valid.

Dave :)

---

### Post by handydan918 on 2009-01-14
Wow. 
I have this card in my lappy. I just suffered a total hard drive fail and had to reinstall. 
It took like 2 minutes (including a reboot!) to set it up in Mepis using a native driver. Wassup with ndiswrapper? I haven't had to use that for over a year!

:lolflag:

---

### Post by Mortfish on 2009-01-16
Anewguy

As I said I got to step 9 in the instructions you gave me. I guess that means that I have installed ndiswrapper.  Still, everything works now, by the fwcutter method (i think!?) so I live by the motto "don't try to fix it if it ain't broken" :)

Thanks & Regards
Morten

---

