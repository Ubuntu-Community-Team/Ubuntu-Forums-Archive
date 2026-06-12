---
title: "Totally new to Ubuntu, totally frustrated.."
date: 2011-01-15
forum: New to Ubuntu
---

### Post by Kayuu on 2011-01-15
Hey, so I'm totally new to ubuntu so I thouhgt I'd give it a try yesterday. I used the Ubuntu 10.10 live install CD whilst in windows XP and install it alongside so my PC is now able to dual boot into either distro. 
 
I ran into problems when I was trying to install my belkin wireless USB adapter F6d4050. I've read around forums and tried various things but I've had no luck even though it is possible it seems. 
 
I've tried to install ndiswrapper-common, ndiswrapper-utils-1.9 and ndisgtk but I'm not sure they're installing properly? First of all, the synaptic package manager would NOT mount the ubuntu CD when I tried to add that, when I went into repositries and added it as a source I got various W: fetch errors, they seem to be trying to connect to webpages (I have no internet connection obviously), so I updated and searched for "ndis" (still in SPM) I found them and tried to install them but only ndiswrapper-common installed, installation of the other two didn't go ahead as the SPM couldn't locate them even though I found them in the path it was specifying, on the CD.
 
So I tried install them from the CD itself using the software center thing, it seemed to work as Windows wireless drivers turned up in adminstration, but everytime I try to run the program it hangs and I have to foce quit, it's really frustrating as I have no idea what to do now.
 
[Side notes] Ubuntu can see my device as it turns up in lsusb in terminal, I've followed some advice in the post of another OP using gedit to add a command strings for network_drivers.rules & network_drivers.conf but it doesn't seem to have done anything? >< rt2870sta 050d?

---

### Post by ronnielsen1 on 2011-01-15
[http://ubuntuforums.org/showthread.php?t=1610174&highlight=F6d4050](http://ubuntuforums.org/showthread.php?t=1610174&highlight=F6d4050)

> A common problem for most people with them. This tutorial Applies to the [COLOR=Red]Belkin N150 F6D4050.[/COLOR] 100& Success rate.

1. Open Application>Accessories>Terminal.

2. Type in **lsusb**

3. Your device ID should read out **050d:935a**

4.If it does read out, in the same terminal, type **sudo gedit /etc/udev/rules.d/network_drivers.rules**

5. A File should open, in this file type **ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="935a", RUN+="/sbin/modprobe -qba rt2870sta"**

6. Save and close this file, then in the same Terminal type **sudo gedit /etc/modprobe.d/network_drivers.conf**

7. Another file should open, similar to step 5. Type in **install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "050d 935a" > /sys/bus/usb/drivers/rt2870/new_id**

9. Save and Close this file. In the terminal either type **sudo reboot** or just restart your pc as normal.

10. Upon login, a rectangular box will appear saying, wireless networks are available.


Sorry you're having troubles

---

### Post by Kayuu on 2011-01-15
Yes, I've followed thos instrctions already but nothing seems to happen. Are you meant to do this after installing the windows driver with nd-xxxx etc or do you not have to do that at all?

---

### Post by ronnielsen1 on 2011-01-15
> Yes, I've followed thos instrctions already but nothing seems to happen. Are you meant to do this after installing the windows driver with nd-xxxx etc or do you not have to do that at all?

It doesn't appear to need the windows driver. Does lsusb show the same numbers in the results and have you copied and pasted EXACTLY like on the help forum? Any errors?

---

### Post by ronnielsen1 on 2011-01-15
Did you save your changes?

---

### Post by wep940 on 2011-01-15
It would appear, if everything matched up above, that you don't need ndiswrapper.  However, since you did ask and others may see the thread, don't try to add the LiveCD as a source to synaptic package manager to install ndiswrapper and ndisgtk.  It's a little easier than that:
 
[LIST]
[*]After booting Ubuntu, load the LiveCD and let it spin up.  If a message appears about a software source being found just cancel it.
[*]Via "Places", navigate to the /pool/main/n/ndiswrapper folder on the CD
[*]Double-click the ndiswrapper common file to install it - wait for the installation to complete.
[*]Double-click the ndiswrapper utilities file to install it - wait for the installation to complete.
[*]Navigate to the /pool/main/n/ndisgtk folder on the CD.
[*]Double-click the ndisgtk file to install it - wait for the installation to complete.
[/LIST]To actually use ndiswrapper to load Windows drivers:
[LIST]
[*]Go to System/Administration/Windows Wireless Drivers - this will start up ndisgtk, a GUI'd front-end to ndiswrapper.  Using ndisgtk instead of all the command line typing for ndiswrapper makes it much easier and far less likely to have a typo that results in failure.
[*]Click on "New.....".
[*]Point it to your Windows driver .inf file -> it should complete and show the device and driver ready.
[/LIST]Things to remember if you do use ndiswrapper/ndisgtk:
[LIST]
[*]the drivers must be Windows XP drivers only
[*]the driver architecture must match your Linux architecture - 32-bit for 32-bit Linux, 64-bit for 64-bit Linux.  Trying to mix them won't work.
[*]ALWAYS check first to see if there is a native or restricted driver available, or if you need to follow some specific instructions such as those already posted by others above.
[*]It's best to only use ndiswrapper/ndisgtk as a last resort.  There is nothing wrong with these programs, and nothing wrong about using them.  It's just that in the long run you'll be better off using native or restricted drivers.
[/LIST]

---

### Post by electroken on 2011-01-15
> **wep940 said:**
> It would appear, if everything matched up above, that you don't need ndiswrapper.  However, since you did ask and others may see the thread, don't try to add the LiveCD as a source to synaptic package manager to install ndiswrapper and ndisgtk.  It's a little easier than that:
 
[LIST]
[*]After booting Ubuntu, load the LiveCD and let it spin up.  If a message appears about a software source being found just cancel it.
[*]Via "Places", navigate to the /pool/main/n/ndiswrapper folder on the CD
[*]Double-click the ndiswrapper common file to install it - wait for the installation to complete.
[*]Double-click the ndiswrapper utilities file to install it - wait for the installation to complete.
[*]Navigate to the /pool/main/n/ndisgtk folder on the CD.
[*]Double-click the ndisgtk file to install it - wait for the installation to complete.
[/LIST]To actually use ndiswrapper to load Windows drivers:
[LIST]
[*]Go to System/Administration/Windows Wireless Drivers - this will start up ndisgtk, a GUI'd front-end to ndiswrapper.  Using ndisgtk instead of all the command line typing for ndiswrapper makes it much easier and far less likely to have a typo that results in failure.
[*]Click on "New.....".
[*]Point it to your Windows driver .inf file -> it should complete and show the device and driver ready.
[/LIST]Things to remember if you do use ndiswrapper/ndisgtk:
[LIST]
[*]the drivers must be Windows XP drivers only
[*]the driver architecture must match your Linux architecture - 32-bit for 32-bit Linux, 64-bit for 64-bit Linux.  Trying to mix them won't work.
[*]ALWAYS check first to see if there is a native or restricted driver available, or if you need to follow some specific instructions such as those already posted by others above.
[*]It's best to only use ndiswrapper/ndisgtk as a last resort.  There is nothing wrong with these programs, and nothing wrong about using them.  It's just that in the long run you'll be better off using native or restricted drivers.
[/LIST]
Would this method also work to get the proper windows drivers for my dvd burner so that one of my windows programs (Magic Dvd Copier) will be able to see the dvd/cd as a dvd-rw drive when it runs under wine?
I am just a newbie myself and this seemed to be relevant to my issues of Magic Dvd Copier not seeing the dvd burner, but able to read the data off the disk I put in the drive during the first part of the copy process. All is good until it goes to write the modified video files to the empty dvd-r.

---

### Post by wep940 on 2011-01-15
> **electroken said:**
> Would this method also work to get the proper windows drivers for my dvd burner so that one of my windows programs (Magic Dvd Copier) will be able to see the dvd/cd as a dvd-rw drive when it runs under wine?
I am just a newbie myself and this seemed to be relevant to my issues of Magic Dvd Copier not seeing the dvd burner, but able to read the data off the disk I put in the drive during the first part of the copy process. All is good until it goes to write the modified video files to the empty dvd-r.
 
No - this would be purely for network devices.  However, if you open a new thread with this problem, someone may be able to help.  I haven't looked at Wine in a long time now, but it might be that when you configure wine you have to add the DVD burner device as it might only know about hard drives at that point.

---

### Post by Kayuu on 2011-01-15
Thank you for your responses :) When I looked closer into the command string I had missed a letter out of it. When I added it and rebooted it worked. I'm now using ubuntu to type this reply :)

---

### Post by Kayuu on 2011-01-15
Thank you for your responses :) When I looked closer into the command string I had missed a letter out of it. When I added it and rebooted it worked. I'm now using ubuntu to type this reply :)

---

### Post by ronnielsen1 on 2011-01-15
>  seemed to be relevant to my issues of Magic Dvd Copier not seeing the dvd burner, 

I suggest looking for alternative programs. Linux has excellent free programs that will do the same thing. Why try to run Magic DVD Copier in wine when K3B, gnomebaker ot tons of other free software will do the same thing?
[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)

---

### Post by electroken on 2011-01-15
well the problem is that in more than 5 years the only program I have ever found which can copy a vr mode dvd disk is Magic Dvd Copier and that includes all the windows rippers, nero, etc which all come up with a crc redundancy error check when trying to copy the files in the Video_vr directory to the hard drive to make an iso etc. Parts of the file is in the Video_vr directory and part of it is in the Video_ts directory or at least pointers and major part of the file. It is to allow the files to be edited on the standalone dvd burner. I can always try another program if you have one, but it still remains for me to be able to figure out how to get a burner program or any other program to be able to see the dvd-rom drive as a dvd-rw.

---

