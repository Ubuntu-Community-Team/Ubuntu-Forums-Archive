---
title: "[SOLVED] More Broadcom Issues"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by Titan8990 on 2008-11-24
First off, I have had the wireless working on my laptop before. The first time I had it working I installed my wireless drivers via ndiswrapper from this guide: [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092). The only difference I have done is I did not compile ndiswrapper from source. Instead I just used the debian package.

I'm using Ubuntu 7.10 as that is the only version I have successfully installed my drivers.

Anyways, after multiple unintstall/reinstall for ndiswrapper I continue to get this error when trying to execute the command:

```
sudo modprobe ndiswrapper
```


The error is:

FATAL: Module ndiswrapper not found.


I have never encountered this issue and do not know how to go about solving it.

I have been struggling with getting my wireless working again for well over a week (wasted a lot of time trying to get 8.10 Broadcom drivers to work.

My last support thread when attempting to get 8.10 Broadcom drivers to work (unsolved and gave up): [http://ubuntuforums.org/showthread.php?t=985223](http://ubuntuforums.org/showthread.php?t=985223)

And my feedback post on the issue: [http://ubuntuforums.org/showthread.php?t=986374](http://ubuntuforums.org/showthread.php?t=986374)


All help is appreciated in getting this modprobe error resolved.

---

### Post by Olivier2371 on 2008-11-24
Just a silly question to start.

Have yuo rebooted your system after installing ndiswrapper.

---

### Post by jnorthr on 2008-11-24
yes, wireless connections using broadcom chips is really hard under 7.10 so i bit the bullet and did a fresh install of 8.10 which is much better to start with cos i did not use  ndiswrapper after i found a site with the ucode5.fw firmware to install. needed to reboot several times and wait while the router final 'discovered' my system.

---

### Post by caleb12 on 2008-11-24
You can also locate the module by:

sudo modprobe -l |grep ndis

If it doesnt appear, then there is a good chance it is not installed for the running kernel. Remember we are dealing with modules, so if the kernel gets upgraded (like going from 7.10 to 8.10) then ndiswrapper would have to be reinstalled for the current kernel. This is usually handled by dkms, however I dont believe that was an option in 7.10. 

I skimmed through your other posts, so forgive me if I ask something that you have answered a thousand times previous... but, in my experience wireless with Broadcom has been relatively easy to get going - doesn't always work the way I want, but it's easy enough to get going... 

What ndis packages have you installed? There are 3 packages available, ndiswrapper (the module), ndiswrapper-utils, and ndisgtk. 

I just installed ndis about a week ago, and I would have two pieces of advice if you are going off the older How-Tos in the forum... One - get an updated driver from the manufacturers website; two - use ndisgtk. 

It's as easy as:

sudo ndisgtk 

Gives you a GUI, point it to the bcmwl5.inf file and it's done... sudo modprobe ndiswrapper. It literally took me about 15 seconds... Then again, I am on 8.10. What Broadcom card are you using anyways? 

Were you using the B43 module for your Broadcom card previously? 

Did you blacklist B43? SSB? etc... 

And on a side note, how did you go about installing B43? Have you followed the guide at [**_Linux Wireless_**]("http://linuxwireless.org/en/users/Drivers/b43")?

---

### Post by Ayuthia on 2008-11-24
> **Titan8990 said:**
> 
I'm using Ubuntu 7.10 as that is the only version I have successfully installed my drivers.

Anyways, after multiple unintstall/reinstall for ndiswrapper I continue to get this error when trying to execute the command:

```
sudo modprobe ndiswrapper
```


The error is:

FATAL: Module ndiswrapper not found.


I have never encountered this issue and do not know how to go about solving it.

If you are unable to find the ndiswrapper.ko file (should be found in /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper).  If it is not there, you should be able to get it back by reinstalling linux-image-`uname -r`-generic.  However if you compiled ndiswrapper, you will need to recompile ndiswrapper so that it can build the .ko file for you.

If the module is not missing, you will want to check ndiswrapper -l to see if the device is present.  If it is, check dmesg|grep ndis to see if there are any error messages.

You said that you are using 7.10, is that correct?  If so, the b43 and ssb drivers will not be there because they are introduced in the 2.6.24 kernel.

---

### Post by nightmare0 on 2008-11-24
If you have the .inf driver files for your adaptor then see if you can reinstall ndiswrapper from your install cd. ( Im not sure that it is included on the 7.10 cd, but it is on 8.04 and newer.) All that you would need to do is either ```
sudo apt-cdrom add
``` then try to install using either synaptic or apt. the mod shouldn't have much to do with your problem unless you dont have the drivers for some reason

---

### Post by Titan8990 on 2008-11-25
Alright, thank you everyone who replied.

In regards to the person that said to start with 8.10, I have had **much** better luck with 7.10 and 8.04: [My Feedback of 8.10 Broadcom Support](http://ubuntuforums.org/showthread.php?t=986374)



I think Caleb is on the right track with it installing to the wrong kernel. I originally installed 7.10 server. Then I installed the desktop kernel and removed the server kernel. However, I didn't install ndiswrapper until after this.

The packages I installed were:

ndiswrapper-utils-1.9 

and

ndiswrapper-common

I have also reinstalled the following ways:

sudo apt-get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9

and

sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9


I think it is looking like I will reformat again. 

> 
Were you using the B43 module for your Broadcom card previously? 


Tried it, didn't work. The only way I have got my wireless to work is via ndiswrapper.


> It's as easy as:

sudo ndisgtk

Gives you a GUI, point it to the bcmwl5.inf file and it's done... sudo modprobe ndiswrapper. It literally took me about 15 seconds... Then again, I am on 8.10. What Broadcom card are you using anyways?

I avoid GUIs at all costs. I don't have my laptop with me atm so I will have to get back to you on the exact model number of the Broadcom card.


Thanks again for the help. When I get home I will try this:


> If you are unable to find the ndiswrapper.ko file (should be found in /lib/modules/`uname -r`/kernel/ubuntu/ndiswrapper). If it is not there, you should be able to get it back by reinstalling linux-image-`uname -r`-generic. However if you compiled ndiswrapper, you will need to recompile ndiswrapper so that it can build the .ko file for you.

---

### Post by Titan8990 on 2008-11-26
After playing with it for a while, I am now reformatting again and installing the Desktop version from CD.

---

### Post by Titan8990 on 2008-11-26
UPDATE:


After reformat and working through the tutorial again, my issue is solved.

---

