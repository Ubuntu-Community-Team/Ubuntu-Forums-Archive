---
title: "Trying to get linksys wusb300n working with ndiswrapper (again)"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by pottzie on 2011-02-22
I'm trying to get a Linksys wusb300n working with Ubuntu 10.10, 32 bit. There are several threads to accomplish this on the forum, one of which turns out to be mine! I got it working a few months ago, but had to reinstall the operating system.
 
 I got pretty far doing what I had done earlier, but when I run
 sudo ndiswrapper -i netmw245.inf
I get; couldn't open netmw245.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
 
 modprobe ndiswrapper -l shows that ndiswrapper is there, and I can see /usr/sbin/ndiswrapper when I call it up with gedit. Can I get the bits and pieces of ndiswrapper and the netmw245.inf to work together?

---

### Post by wep940 on 2011-02-22
> **pottzie said:**
> I'm trying to get a Linksys wusb300n working with Ubuntu 10.10, 32 bit. There are several threads to accomplish this on the forum, one of which turns out to be mine! I got it working a few months ago, but had to reinstall the operating system.
 
I got pretty far doing what I had done earlier, but when I run
sudo ndiswrapper -i netmw245.inf
I get; couldn't open netmw245.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.
 
modprobe ndiswrapper -l shows that ndiswrapper is there, and I can see /usr/sbin/ndiswrapper when I call it up with gedit. Can I get the bits and pieces of ndiswrapper and the netmw245.inf to work together?
 
I believe it telling you it can't find the .inf file.  Be sure you are in the directory (folder) where the netmw245.inf file is, then try again.  I would, however, strongly recommend a different approach:
 
*IF* you know there are no native drivers for your device, and that is why you are using ndiswrapper, please use the GUI'd tool ndisgtk - it is a graphical front-end to ndiswrapper and takes care of a lot of things for you.  First be sure you have "cleaned out" things from ndiswrapper:
 
sudo ndiswrapper -l <press enter>  That's a lower case "L" for list.
 
If anything is returned, do:
 
sudo ndiswrapper -e xxxxxx <press enter> where XXXXXX is the device/driver that show in the list output
 
Repeat the list, and the remove, as many times as needed until no more devices/drivers show.
 
While Ubuntu is running, load the LiveCD - if it gives a message about a software source just cancel the message.  Using "Places", navigate to the /pool/main/n/ndisgtk folder on the CD.  Double click on the file there to start it's installation.  Wait for that to complete.
 
Now go to System/Administration/Windows Wireless Drivers (I think that's what it's called) - this will start up ndisgtk.  Select add or new, then point it to the .inf file for the driver.  It should finish and show the device/driver loaded.  That's it - now go back and try wireless again.  Be sure to right-click on the network manager icon and be sure "Enable Wireless" is checked - if not, check it.  Now left click on the network manager icon and see if any wireless networks show.

---

### Post by pottzie on 2011-02-22
I tried using ndigtk. When I point to the netm245.inf, it shows invalid driver with a big red "X" over the driver.

 ndiswapper -l returns "netmw245 : invalid driver!"

---

### Post by wep940 on 2011-02-22
Well, when I've seen that, it's 1 of 3 things:
[LIST]
[*]The driver you are trying to use is not actually for your adapter
[*]Ndiswrapper works with Windows XP driver *ONLY*
[*]The Windows driver type must match the architecture of your Ubuntu installation - 32 bit or 64 bit
[/LIST] 
I'll do a little research for you and see what I can find out.

---

### Post by wep940 on 2011-02-22
If you have downloaded and extracted the files from Linksys itself for the Windows XP driver, netmw245.inf is the correct .inf file, and the other 3 files are Mrvw243.sys, Mrvw254.sys and mrvw245.cat.  I believe these are 32-bit drivers.  If you are using "normal" Ubuntu they should work.  However, since you've already tried somethings with ndiswrapper, we have to be sure everything you tried is backed out first.
 
The first thing to do is clear any attempts at drivers that ndiswrapper knows about:
 
[LIST]
[*]open a terminal window (Appllications/Accessories/Terminal)
[*]type:
[/LIST]sudo ndiswrapper -l <press enter>  That's a lower case "L" for list.
 
If anything is returned, type:
 
sudo ndiswrapper -e xxxxxx <press enter> Where xxxxxx is the driver/device returned in the list command.
 
repeat the 2 above until nothing is returned.
 
Next be sure you have removed anything you may have added to the modules file, and be sure to reverse any edits you may have to the blacklist.conf file.
 
Now to try again:
 
[LIST]
[*]Be *SURE* you are running 32-bit Ubuntu.
[*]Be sure all of the 4 files associated with the device driver are in a single folder.
[*]Be sure you have ndisgtk installed.
[*]Go to System/Administration/Windows Wireless Drivers - this will start up ndisgtk, the graphical front-end to ndiswrapper.
[*]Select new or add (I don't have it in front of me right now).
[*]Point it to the .inf file in the folder you have all the adapter's device driver files in.
[*]Click ok or whatever it is (again, sorry for being a little vague, but I don't have it in front of me right now).  If you get an error, STOP and post back.
[*]Disconnect any hardwire connection you might have from your ethernet port.
[*]Right-click on the network manager icon and be sure "Enable Wireless" is checked - if  not, be sure to check it.
[*]Left-click on the network manager icon and see if wireless networks show.
[/LIST] 
As mentioned, the driver files from Linksys itself are 32-bit.  They should work if you are using 32-bit Ubuntu.  The above instructions should hopefully have cleared out anything you attempted before.  So, if this doesn't work please post back again with the error, otherwise post back your success so others can know, and so we can say "job well done!" to you.

---

### Post by pottzie on 2011-02-23
I was able to get the driver to work with ndisgtk once I figured out that the XP drivers were in a directory, and pointed that to ndisgtk. I'm still not able to get the receiver to connect to my router, though.

 modprobe -l does show that ndiswrapper.ko is loaded as a module. When I reboot and try to use the wusb300n, no networks show up.

---

### Post by wep940 on 2011-02-24
If you right-click on the network manager icon, is the "Enable Wireless" checked?

---

### Post by pottzie on 2011-02-24
Yes, enable wireless is checked. I'm posting from it now, but I have to use my "G" receiver.

 Am I supposed to disable any drivers for ndiswrapper to work? I was looking over an Ubuntu wiki guide and it mentioned blacklisting free drivers, but the guide was a couple of years old.

---

### Post by wep940 on 2011-02-24
I don't have any experience with that adapter or driver, so I really don't know.  However, if it's working using G then I suspect it's probably something other than driver module that would need to be blacklisted.  Usually, and I say that loosly, ndisgtk tries to take care of that.  Most of the blacklisting I have seen have been for Broadcom and some realtek adapters.
 
Is the Wiki guide specifically for your device?  If so, post the link and I can look at it and see if I can tell anything from that or not.

---

### Post by pottzie on 2011-02-24
It was a sort of generic wiki for ndiswrapper.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

 It looks like ndiswrapper has "done it's thing," and perhaps ndisgtk has done everything it's designed to do too. That being said, I notice that the wusb300n is blinking away, with both the power and transmit/receive LEDs blinking away like everything's just peachy. Then when I remove the G receiver and try to connect, it doesn't show anything other than VPN connections..whatever that is.

---

### Post by wep940 on 2011-02-24
Wish I could help you more - I assume by a "G" receiver you talking about a wireless router than will 802.11G?  I also assume you have a "N" wireless router someone you can try to connect to when the "G" is disconnected?

---

### Post by pottzie on 2011-02-25
Yes, the "G" receiver works natively with the kernel. I'll try linuxquestions and see if anyone there can figure out what I'm doing wrong. What stumps me is that I've gotten this to work with both Ubuntu and Linux Mint before!

---

### Post by wep940 on 2011-02-25
Sorry I couldn't help you more.  Do me a favor - when you get the solution and it's working, PM me with either a link to the new thread or with the solution.  I'm curious to know (I'm trying to learn as much as I can but I'm pretty slow at it).

---

