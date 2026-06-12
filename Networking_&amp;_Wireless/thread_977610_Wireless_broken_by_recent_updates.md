---
title: "Wireless broken by recent updates"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by T_W on 2008-11-10
I **had** a working wireless solution with my Dell D620 laptop and a WPA wireless network.

I recently ran some updates and now wireless is non-functional.  The Wifi light on the laptop blinks but I cannot connect to any networks.  

Were there any recent regressions to wireless functionality?

Thanks for any help.

---

### Post by OZFive on 2008-11-10
You might want to try uninstalling and reinstalling the network manager.  Workd for me one time.

I downloaded wicd and replaced NM with it too one time.  Both seemed to work, try wicd first though, most say it is better.  

I use NM as my gigabit port is broken now (darn kids) and I am using a ExpressCard Gigabit adapter to connect to the FIOS service rom Verizon and NM works with it flawlessly, wicd does not.

---

### Post by T_W on 2008-11-10
Just realized I didn't even say I am still on 8.04.

Wireless in Intel PRO/Wireless 3945ABG.

---

### Post by T_W on 2008-11-10
Well, I used the grub menu to boot back into 2.6.24-19-generic (as opposed to 2.6.24.21-generic) and it is functioning again.

Bad update?

---

### Post by T_W on 2008-11-11
BUMP

Anyone know of anything?  Do I just ignore all future kernel updates?

---

### Post by T_W on 2008-11-12
More info.  My WPA-Personal access point at home works.

The WPA-Enterprise access point at work does not work (unless I boot the older kernel).

---

### Post by enigmageek on 2008-11-13
Hello TW. Install DKMS to automatically rebuild your drivers when you upgrade the kernel. 
sudo apt-get install dkms

I'm still on Hardy until EOL but I just compiled the 2.6.27.5 kernel. Before I did, I installed DKMS and read all about it. Find the name and version of your wireless driver and look for dkms.conf files, you might find one with Google. Write or copy the conf file to the same folder as the driver for example mine is in /home/myname/madwifi-hal. Next, boot into your newest kernel and in a Terminal type:
dkms add -m module name -v version...hit enter..then
dkms build -m module name -v version...then
dkms install -m module name -v version

I don't remember if I had to use "sudo" or not. If DKMS installed properly and you wrote the dkms.conf properly, after executing the add, build, and install commands every time you upgrade the kernel the driver will be automatically rebuilt and inserted. I use it to rebuild my wireless and VirtualBox cuz I'm gonna be upgrading my kernel along with the kernel.org releases. Hope this helps.
Regards, Ray
Ubuntu Hardy 8.0.4.1-2.6.27.5

---

### Post by peterroots on 2008-11-14
I have had the same problem with kubuntu 8.04 - ran updates yesterday and now now wireless anymore.  for that matter NM does not show I have a cable plugged in either but eth0 is picking up and address.
removed network-manager network-manager-kde networkstatus and then reinstalled.
oops!
now no network so could not reach repositories to reinstall network. darn
set eth0 to dhcp in interfaces
still no connection
had to use route to add a default gateway (doing all this in network settings had no effect)
did reinstall but still no wireless or indication of plugged cable in NM

If we need to recompile drivers, got from ubuntu repros, every time we get a kernel upgrade I don't think the kernel upgrade is ready for release!!

I can't go back to 19 or 15 from 21 kernel as neither of the old ones start up - I get a message about not being able to config xorg, or something like that,then system hangs up loading timidity

Any ideas on getting NM working again?

---

### Post by peterroots on 2008-11-14
Thanks OZFive - wicd is working fine and seems nicer than NM but I have to set up all my wireless keys again (copying them out of kwallet where they were stored)
'tis but a small price to pay though
[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) for anyone else with the same problem

---

### Post by enigmageek on 2008-11-14
peterroots. Have you tried booting the older kernels into rescue mode? There should be an option to try to fix X. I had to do that one time when I messed with my xorg.conf and couldn't get a display. Good luck. DKMS is helpful because it rebuilds drivers we have added automatically whenever there's a kernel upgrade. Once you set it up and keep the driver sources, you won't have to worry about the driver again. You don't have to upgrade to Intrepid to use DKMS or even for the 2.6.27 kernel. Just a thought.

---

### Post by peterroots on 2008-11-17
thanks enigmageek
Lost internet totally due to an isp problem, which is now sorted so just got you comments.
I had not tried rescue mode for the older kernels i will give it a try at some time.
Not sure dkms is the answer as my wireless driver is fine (widc is able to make use of wired and wireless without problems) the issue seems to be Network Manager.

---

### Post by enigmageek on 2008-11-19
Hello peterroots. The DKMS program just rebuilds and installs drivers/kernel modules that you have installed which are not part of the kernel. Each time Ubuntu issues a kernel image update, usually these drivers need re-installing by hand with make install. This program just averts the need to keep re-installing by hand. Wicd does seem to be a great program from what I've seen. It seems like most all Atheros cards should work with madwifi, it's worked for me with both integrated and usb cards along with plain old Network Manager since Dapper. Take care.

---

### Post by T_W on 2008-11-28
And now kernel 2.6.24-22 is released.

Is it safe to upgrade?

---

### Post by enigmageek on 2008-12-07
Hello T_W. If you have dkms installed properly it should work after kernel upgrades. There are a lot of Intel wireless drivers included in the latest versions of the Linux kernel.If you're depending on drivers that aren't included with the kernel, I would install dkms and make sure you have a folder with the module sources you're using. Good luck. Oh, I let Hardy upgrade their kernel and I just compiled the 2.6.27.8 as well.

---

### Post by T_W on 2009-01-15
Same problem reported here:

[http://ubuntuforums.org/showthread.php?t=952569](http://ubuntuforums.org/showthread.php?t=952569)

Still no fix.  

I am using built-in drivers so I don't think dkms is going to do anything. 

I have been holding off on an 8.10 upgrade since my only working solution right now is to boot into the 2.6.24-19 kernel.

---

### Post by T_W on 2009-01-16
This seems to definitely have been caused by linux-backports-modules-2.6.24-21-generic.

The backports deb seems to include an update for my wireless driver (iwl3945).  If I remove the backports deb, WIFI works again.... but unfortunately my NVIDIA driver ceases to function if backports is removed.  

I am trying to determine if I can blacklist the updated module and go back to the original module.

---

### Post by T_W on 2009-02-17
I entered a bug into Launchpad for this bug [#329909]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/329909").

---

### Post by T_W on 2009-05-22
> I entered a bug into Launchpad for this bug #329909.

And absolutely no response 3 months later?

Did I do something wrong?  How do I get a maintainer to acknowledge my bug?

---

### Post by T_W on 2009-06-05
Seems to have been resolved by linux-backports-modules-2.6.24 2.6.24-24.32

May be duplicate of Bug [#322434: Wifi (ipw2200) stopped connecting with kernel update 2.6.24-22]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/322434")

---

