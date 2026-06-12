---
title: "uninstall invalid driver with ndiswrapper ?"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by dbmnk on 2006-07-21
I recently installed Ubuntu 6.06 with the liveCD, and of course couldn't connect to the WLAN with my Asus WL-138g wireless ethernet card.

Hence I consulted the [WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") and [Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

As stated by the guide I installed ndiswrapper from the liveCD, but to my regret the graphical interface feature "windows wireless" didn't show up under the administration menu. 

Thus I tried to install the wireless driver (mrv8k51) from the command promt.

I tried to install mrv8k51 version 2.3.0.19 ([latest WinXP driver from Asus]("http://support.asus.com/download/download_item.aspx?product=11&model=WL-138g&SLanguage=en-dk#")) [as no-one stated it wouldn't work with 6.06.]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

ndiswrapper now states that the driver is invalid, so I tried the remove command, but then get the message "no driver installed".

If I try to install the driver again, I get the message "driver already installed"

Now, what do I do? How do I get rid of the invalid driver?

Where is the driver installed - in a library, or did it also modify some other files, e.g. ndiswrapper files?

- and, do you recon I got ndiswrapper installed correctly? Might I try to obtain a newer version than the one on the liveCD (downloaded start june 2006)?

It seems that all the workarounds that got WL-138g working, all succeeded on ubuntu 5.x - anyone who can direct me to a succesfull install guide for 6.06?

Thank you, 
/Simon

PS: sorry for not dropping any screendumps, but I'm at work, and far away from my now handicapped home-PC. So information rely on memmories; hope it suffice to trigger some helpfull answers.

---

### Post by wieman01 on 2006-07-21
I am also not in front of my own computer... but perhaps I can help you this way.

When installing your driver with ndiswrapper, make sure all files that come along with the appropriate are in the folder when your install the *.inf file. Otherwise the installation fails (have seen it many times myself). In my case (wusb54g v4) I left all 3 files in the folder from which I installed the driver.

Secondly you my have to specify the extension when removing it (*.inf) as well. I think that's what I had to do.

Hope this helps a bit.

---

### Post by dbmnk on 2006-07-21
thank you, I gueess the files were in the same folder, as I just extracted the downloaded folder on my USB device and installed them from that. 

The files that were contained was called .inf .sys .cab (i think it was .cab)

by this you don't mean that all .inf from WinME WinXP Win98 should be contained in the same folder, right?

---

### Post by wieman01 on 2006-07-21
No, just the three files you mentioned (.inf .sys .cab). But they need to be copied on to your computer. Otherwise the system won't find them once you remove your USB stick. Could that be the problem?

---

### Post by dbmnk on 2006-07-21
might be, I'll check for that later - but I was under the impression that ndiswrapper copied the files to their final and working destination.

I had the USB disk plugged in during the entire process, though.

---

### Post by wieman01 on 2006-07-21
Try playing around with it and let us know if you have been successful. Ndisrapper (normally) is pretty reliable and easy to configure once set up (WPA, WPA2, etc.). Give it a shot and keep us posted.

---

### Post by dbmnk on 2006-07-21
will do, thanks

---

### Post by dbmnk on 2006-07-25
well, I cannot install any new driver before I have deleted the old one, problem is: HOW?

ndiswrapper isn't willing to delete the driver, as it states that an invalid driver is already installed.

I cannot remove the driver from the library ~etc/ndiswrapper/mr8ka51/ - as ubuntu states I don't have the privileges to do that - WTF? 

Anyhow, there aren't any files in the ~etc/ndiswrapper/mr8ka51/ library, so I feel pretty stuck here.

Can anyone please guide me through deletion of the faulty driver - I can't seem to find any online guides.

:( simon

---

### Post by wieman01 on 2006-07-25
Hi, it's me again. You could try to uninstall "ndiswrapper" and reinstall it afterwards. Would this help?

Have you also tried...

ndiswrapper -r <driver name>

?

---

### Post by dbmnk on 2006-07-25
> **wieman01 said:**
> Hi, it's me again. :) hi there - and it's me again here, the linux newbie> **wieman01 said:**
> You could try to uninstall "ndiswrapper" and reinstall it afterwards. Would this help? Might, I'll try - is the ndiswrapper on the liveCD the latest or should I try obtain a newer one somewhere?

> **wieman01 said:**
> 
Have you also tried...

ndiswrapper -r <driver name>

?Yes, that is the remove command I'm using. Is there any rules of when to slap in the sudo command when using ndiswrapper?

/Thx for the prompt reply's

---

### Post by wieman01 on 2006-07-25
Well, yes, you will have to use "sudo". Apologies, should have added that. It's an administrative/root task so you need that as well.

Reinstalling it should work. But after uninstalling it, you should also delete the driver files from your HDD. Just to ensure that they won't interfer next time you install the driver.

Can you try and let me know what's happened?

---

### Post by wieman01 on 2006-07-25
Another usefule guide... does not mention "uninstall" though:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")

---

### Post by wieman01 on 2006-07-25
And oops... Could it be this one?

> sudo ndiswrapper -e <driver>

Man, I am not in front of my computer... I may have given you the wrong command. Should be "-e" and not "-r". You could check out the help function if that still does not work:

> ndiswrapper --help

---

### Post by dbmnk on 2006-07-25
> **wieman01 said:**
> 
Man, I am not in front of my computer... I may have given you the wrong command. Should be "-e" and not "-r". You could check out the help function if that still does not work:
don't worry about it, I carnt remember either, but ndiswrapper have a very usefull guide in the command prompt of its command functions - the guide appears, when you type stuff ndiswrapper doesn't understand 8) 

How do I deal with the missing privileges to delete the driver library?

Shure I'll let you know, when I get it all working. I'll post my howto - it's important to contribute.

---

### Post by wieman01 on 2006-07-25
"sudo" will do as far as the necessary priviliges are concerned. You can do anything if you use that command since it's a replacement for the root account.

Check out this guide if you have time:

[https://help.ubuntu.com/community/RootSudo#head-7bd7cf735bf6b1cfac9464a9331775eaadc8b8ec]("https://help.ubuntu.com/community/RootSudo#head-7bd7cf735bf6b1cfac9464a9331775eaadc8b8ec")

---

### Post by dbmnk on 2006-07-29
Well, I didn't succeed yet, here is what I'm runnin into:

I did a clean install of Ubuntu, deleted the pre-installed mr8k driver, installed ndiswrapper from the liveCD (no graphical interface appeared, though), and tried to install the driver as follows
> dbmnk@dbmnk-desktop:~$ sudo ndiswrapper -i ~desktop/wl138g/win98/mrv8ka51.inf
Password:
Installing mrv8ka51
couldn't copy ~desktop/wl138g/win98/mrv8ka51.inf at /usr/sbin/ndiswrapper line 135.

dbmnk@dbmnk-desktop:~$ ndiswrapper -l
Installed ndis drivers:
mrv8ka51        invalid driver!

dbmnk@dbmnk-desktop:~$ sudo ndiswrapper -e ~mrv8ka51.inf
Driver ~mrv8ka51.inf is not installed.Use -l to list installed drivers

dbmnk@dbmnk-desktop:~$ sudo rmdir ~/etc/ndiswrapper/mrv8ka51
rmdir: /home/dbmnk/etc/ndiswrapper/mrv8ka51: No such file or directory

dbmnk@dbmnk-desktop:~$ sudo ndiswrapper -i ~desktop/wl138g/winxp/mrv8ka51.inf
mrv8ka51 is already installed. Use -e to remove it

In short: The installation failed, I cannot remove the driver, and I cannot install a fresh.

How do I get into figuring and correcting the invalid install?

---

### Post by dbmnk on 2006-08-16
bump

---

### Post by wieman01 on 2006-08-16
Have you tried this guide before?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by wieman01 on 2006-08-16
Another thing that you should do... Uninstall "ndiswrapper" by having Synaptic remove it completely. Then reinstall "ndiswrapper" and go through the driver installation process once again.

The packages you need to remove & reinstall are:

1. ndiswrapper-utils
2. ndisgtk

A complete removal will also uninstall existing Windows drivers, etc. So this will - let's hope for the best - resolve your problem.

---

