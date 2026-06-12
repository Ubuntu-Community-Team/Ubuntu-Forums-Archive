---
title: "Ndiswrapper and WUSB54G wireless"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by IsaacJ on 2007-04-30
Hello all. Most of the posts I've seen that get WPA working with the Linksys WUSB54G v4 wireless adapter seem to use Ndiswrapper, so it appears the built in driver doesn't support WPA no matter what. I even tried WICD, which at least gave me the option of trying WPA, but nothing works. So I attempted to load the Windows drivers using Ndiswrapper. I keep getting the dreaded "line 144" error whenever Ndiswrapper tries to install the driver. I'm using Fiesty Fawn.

I have successfully blacklisted the built in driver (the light on my adapter no longer comes on or shows up at all under network tools) and everything seems fine until I try to load the inf file. I'm typing it in correctly and even tried capitalizing the name of the inf file, which didn't help. These are the only suggestions I've found so far in the forums to resolve the line 144 error issue.

I'm pretty much a Linux noob, but I'm so close to using Ubuntu Feisty Fawn on a regular basis that I can almost taste it. Without a secured wireless connection, it's a no go. I can get connected fine using the built in driver without encryption, but that's of no use to me. I need the security of WPA.

There has to be something else I can try? If not, can anyone recommend an inexpensive USB wireless adapter that works consistently with WPA security enabled? The list of supported cards isn't much help.

Thanks for any assistance.

IsaacJ

---

### Post by IsaacJ on 2007-05-01
Bump.  (Sorry)

IsaacJ

---

### Post by Floppyjoe on 2007-05-01
Do you have all the necessary files in the same directory that you are installing the .inf file from?
For example the .sys file and possibly a .bin file.

---

### Post by IsaacJ on 2007-05-02
Yes, so far as I know. There's an inf file, a sys file, and a cat file. Those are the only 3 files in the driver's folder for v4. I don't think the cat file is necessary, but I have it there anyway.

rt2500usb.inf, rt2500usb.cat, rt2500usb.sys

Thanks for the reply.

IsaacJ

---

### Post by IsaacJ on 2007-05-02
Bump

:) 

IsaacJ

---

### Post by IsaacJ on 2007-05-02
Still hoping for some more advice from anyone.

Thanks.

IsaacJ

---

### Post by Floppyjoe on 2007-05-02
This is what i did to get mine going in Edgy. For Feisty the utilities might be updated to a newer version:

[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=21](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=21)

---

### Post by IsaacJ on 2007-05-02
Thanks a lot for the reply. :) 

Unfortunately, since I can't even get Ndiswrapper to accept the drivers (error line 144) this isn't of much help. :(  It's this error that I need help with. I gave up on using the native rt2500 drivers already. They don't seem to support WPA. I can't even get WEP working with them, and frankly, I don't want WEP any how. I really want WPA.

The lack of wireless security is the only thing holding me back from using Ubuntu for anything serious. Without it, Ubuntu and even Linux generally are useless to me.

Maybe there's no hope at all. But I would like to try.

IsaacJ

---

### Post by Floppyjoe on 2007-05-02
do you have ndiswrapper-common and ndiswrapper-utils installed?

---

### Post by IsaacJ on 2007-05-02
Yes. I used Ndiswrapper 1.9 and 1.8. I kept 1.8 since everyone says that that's the one that works the best.

IsaacJ

---

### Post by Floppyjoe on 2007-05-03
> **IsaacJ said:**
> Yes. I used Ndiswrapper 1.9 and 1.8. I kept 1.8 since everyone says that that's the one that works the best.

IsaacJ

Yes ndiswrapper-common+ndiswrapper-utils?
Or yes ndiswrapper-utils 1.8 +1.9?

---

### Post by IsaacJ on 2007-05-03
Yes to both. I have common files and the utility files.

IsaacJ

---

### Post by Floppyjoe on 2007-05-03
Which driver did you blacklist?

---

### Post by IsaacJ on 2007-05-03
rt2570

IsaacJ

---

### Post by IsaacJ on 2007-05-03
The blacklisting seems to have worked okay since the adapter went dead after that. No lights or any sign of life.

IsaacJ

---

### Post by Floppyjoe on 2007-05-03
Can you post the output of :
```
ndiswrapper -v
```
You should get something similar to this:
```
utils version: 1.9
driver filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:        1.43
vermagic:       2.6.20-15-generic SMP mod_unload 586
```

It should specify a utils version.
If it has a utils error then you need to reinstall a different version of ndiswrapper or a newer version if you previously installed ndiswrapper from sourceforge.net

---

### Post by IsaacJ on 2007-05-03
Alright. I probably won't be able to do this until tomorrow (I can't get online while in Ubuntu) as I'm working on something unfortunately.

Thanks for the for help so far, though. I will check it tomorrow and post the results.

IsaacJ

---

### Post by IsaacJ on 2007-05-03
Breakthrough!

> utils Error: no version specified!
driver version:        1.38
vermagic:       
2.6.20-15-generic SMP mod_unload 586 


Does this mean that the versions are incompatible?

Sounds like I need to uninstall all the ndiswrapper software and start over to make sure I have everything squared. I'm unsure what goes with what, however. Any advice on what I should look for? I continue to hear that ndiswrapper 1.8 is better, but I'll use 1.9 if it will work. Maybe I should then reinstall everything off the live disk and see what happens.

I do not know how to compile code in Linux, so I have been using Deb packages to make it go more smoothly. After fiddling with this for weeks, I don't remember where I found the packages I used. Not sure if I should add another variable to the equation that is dependent on my nooby Linux skills just yet (though I want to learn how to compile). If I have to download these instead of getting them off the live disk, is there a single place I could go to get the Deb files all at once? Just thought I'd ask. I don't think I had much luck finding them before and had to find everything in separate places. Which is probably why I'm getting this error. :)

Thanks a lot for the help. If nothing else, now I have some idea of what to look at next.


IsaacJ

---

### Post by IsaacJ on 2007-05-03
I tried reinstalling the common and utilities file from the disk, which is ndiswrapper 1.9, and I get the exact same message when running with the -v command. I then tried rebooting to make sure the install completed, but also got the same message. So ndiswrapper still reports that the driver is invalid.

What am I doing wrong?

Thanks again for the help.

IsaacJ

---

### Post by rclark68137 on 2007-05-03
What versions of the Windows drivers are you using?  Maybe you need to download the most recent drivers from Linksys. I'm successfully using these versions:  

rt2500usb.cat    4-25-2005
rt2500usb.inf    4-21-2005
rt2500usb.sys    4-13-2005

Also, are you running ALL your commands using sudo?
sudo ndiswrapper -i /home/your_user/WUSB54GV4/rt2500usb.inf
sudo ndiswrapper –l
sudo depmod –a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

---

### Post by IsaacJ on 2007-05-03
I have tried the last two most recent versions of the drivers. However, given what I've learned so far, it sounds like the problem might be with ndiswrapper, not the drivers.

I am using the sudo command.

IsaacJ

---

### Post by IsaacJ on 2007-05-03
bump

---

### Post by Floppyjoe on 2007-05-04
It looks like you have installed a version of ndiswrapper from sourceforge.net previously and that is why you get the utils error. This may be why ndiswrapper is not working properly for you. I have the same output on my laptop with the utils error and my laptop wireless still works though. I have had other instaces with the error where ndiswrapper did not work because of the error. I would suggest you download and install from sourceforge.net version 1.38 or higher. Maybe burn it onto a cd and copy it over or use a USB thumbdrive.

This is a link to a ndiswrapper howto:
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3)

---

### Post by IsaacJ on 2007-05-04
Just wanted to make sure you were clear on this. The last time, I uninstalled everything ndiswrapper related and reinstalled from the disk instead of anything that I had downloaded. I still get version number error and an invalid driver error.

Then again, maybe it will work despite that. I don't get the line 144 error any more. Maybe I should just proceed and see what happens.

Thanks for the help.

IsaacJ

---

### Post by Floppyjoe on 2007-05-04
The version you need to download is not on the disk, it is at sourceforge.net
After you have installed it from there once, it won't work to install it from the disk.

---

### Post by IsaacJ on 2007-05-04
Got ya. I'll send word of what happens next.

IsaacJ

---

### Post by IsaacJ on 2007-05-04
I reinstalled Ubuntu entirely and still get the same results. 

Ndiswrapper -l = invalid driver. Ndiswrapper -v = no version error for utilities. Yet I installed them fresh off the CD without ever having installed the older Sourceforge stuff first.

Is there anything else that I could try?

IsaacJ

---

### Post by IsaacJ on 2007-05-04
I got it backwards, didn't I? You wanted me to start over with the Sourceforge files again, right?

That's what I get for playing with this at 5 in the morning. :lolflag: 

Sorry.

IsaacJ

---

### Post by PARO on 2007-05-05
I got this same network adapter working today on feisty, on our old computer.  I don't know if it's supporting WPA and what not, I wasn't really concerned with that. But I did the command line install (for a very old computer), got the debs from [http://packages.ubuntulinux.org/feisty/]("http://packages.ubuntulinux.org/feisty/") for the ndisgtk one too, but I didn't use it, I followed the previously posted "floppyjoes" example and used the newest versions of ndiswrapper and utils in the repos. I don't have the cd for the thing, so I just downloaded the driver package from floppyjoes and that worked fine. I'm on the net and all. Hope this helps.

EDIT: This floppyjoes howto, sorry I didn't realize a couple different ones were tossed out there:  [http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=21]("http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=21")

---

### Post by IsaacJ on 2007-05-06
Thanks PARO. I am also able to get this adapter to work WITHOUT WPA. It's WPA that's killing the deal for me. :( 

Thanks for trying, though.

IsaacJ

---

### Post by eightbit on 2007-05-18
I followed the instructions from the floppyjoes link and I can see the connections and I believe that I can link up to the unsecured ones but firefox and synaptic still don't work -  I get a blanket "check you network connections" or something similar.  The wireless modem is active,  and I even have a little network icon in the toolbar.  It show 5 available networks with 2 unsecured <-- which I can connect to.  Any ideas?  BTW I have a WUSB54Gv4

---

