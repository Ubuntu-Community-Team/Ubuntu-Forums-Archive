---
title: "[SOLVED] Intel wireless card not recognised on Dell Inspiron 9400 laptop"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by Irishpolyglot on 2007-05-20
Hi everyone!!
Ubuntu is installed and so far looks good... but there's no wireless Internet . I'm on a DELL Inspiron 9400 with Ubuntu 7 64bit. It workes fine on the wired connection.
I have an Intel Next-Gen Wireless-N Mini-Card (for Intel Core 2 Duo Processors).
In the network settings I can only see Wired Connection and Modem Connection - no wireless like in tutorial images... so the drivers aren't there for this card.
I entered 
> lspci | grep -i network"
 and I got back 
> 0c:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
I tried a couple of sites to investigate the problem and got on to "ndiswrapper", but when I go through the tutorials (tried 2 different versions) I just get error messages since they don't apply to my system. How can I install the drivers on this? I can't find anything online (or in this forum) related to my computer or the Intel wireless card. Any advice? I am quite new to all this... can't wait to get it working fully!!
Thanks a mil for your help!!

---

### Post by Kobalt on 2007-05-20
You laptop has an IPW3945 wifi chipset. You can get it working pretty easily installing this : ```
sudo apt-get install linux-restricted-modules-generic
```After this reboot, and you should now be able to connect from the Network-Manager, in the top right corner of your screen.

---

### Post by x64Jimbo on 2007-05-20
the above command is missing a piece. it should say:
sudo aptitude install linux-restricted-modules-generic

---

### Post by Kobalt on 2007-05-20
oOops !

---

### Post by Irishpolyglot on 2007-05-20
> **Kobalt said:**
> You laptop has an IPW3945 wifi chipset. You can get it working pretty easily installing this : ```
sudo apt-get install linux-restricted-modules-generic
```After this reboot, and you should now be able to connect from the Network-Manager, in the top right corner of your screen.

I tried that (with aptitude instead of apt-get) and I got this back: > Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Still no wireless available... any other thoughts?

---

### Post by x64Jimbo on 2007-05-20
looks like the package is already installed. have you tried to modprobe the kernel module for that card?

---

### Post by Irishpolyglot on 2007-05-20
No, I haven't... how can I do that?

---

### Post by Kobalt on 2007-05-21
Try this command line ```
sudo modprobe ipw3945
```

---

### Post by chili555 on 2007-05-21
I do not believe he has a 3945. I think he has a 4965AGN card. Please see post #8 here: [http://ubuntuforums.org/showthread.php?t=396204](http://ubuntuforums.org/showthread.php?t=396204) 

I suspect a crucial element is having the wireless turned off as you boot:> make sure that wireless is turned off when you exit/ enter ubuntu (fn + f2). If it remains on (wireless) then ubuntu can fail to boot or shutdown.

---

### Post by Kobalt on 2007-05-21
Not sure about tthat chili : [http://www.hardware.info/en-US/productdb/bGNkZpiZmJTK/viewproduct/Dell_Inspirion_9400/](http://www.hardware.info/en-US/productdb/bGNkZpiZmJTK/viewproduct/Dell_Inspirion_9400/)
I've read nowhere of a Dell 9400 with such a device...

---

### Post by Irishpolyglot on 2007-05-21
Hi again!
The "sudo modprobe ipw3945" didn't work.
I do not have the 3945. That was offered to me when I was buying the machine but I bought the slightly more expensive one (which is simply called "Intel Next-Gen Wireless-N Mini-Card (for Intel Core 2 Duo Processors"). Hopefully I can still use some kind of drivers that help for it..
I'm going through the installation process for NDISwrapper, but I get the error message: > make[1]: Entering directory `/home/benny/Desktop/ndiswrapper-1.44/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
.... then a few pages later
> loadndisdriver.c:527: warning: implicit declaration of function ‘atoi’
loadndisdriver.c:542: warning: implicit declaration of function ‘atof’
.....
 during installation. It continues on, with "error" and "warning" for a huge list of files. It might be the way I'm installing it, or the directory I'm in when I do it? - I went through the instructions exactly as they are laid out on the NDISwrapper installation site. Any ideas? I'm still trying to get my head around the new OS, but I like it! I'm learning slowly but surely... When I get that to work I'll try #8 of that post hoping it'll work with a 4965 driver even though I don't think it's that one either...
BTW, sry I posted this thread again :oops:... n00b impatience you know...
Any other tips for installation of NDISwrapper and which driver to use with it?
Thanks!!

---

### Post by Kobalt on 2007-05-21
> **Irishpolyglot said:**
> That was offered to me when I was buying the machine but I bought the slightly more expensive one (which is simply called "Intel Next-Gen Wireless-N Mini-Card (for Intel Core 2 Duo Processors")
Ah... That explains it. (so chili : my mistake)
I've read a few posts about this card but honestly I've never read a 'real' solution, only workarounds.

---

### Post by Irishpolyglot on 2007-05-22
Ok, so does anyone have any ideas? Even a workaround would be a start. Surely I can just use the DELL CD that came with my computer for the drivers instead of downloading them? If so, then what am I doing wrong in my NDISwrapper installation? Thanks!

---

### Post by chili555 on 2007-05-22
I think you need to have the packages *build-essential* and *linux-headers-`uname -r`* installed, which you can get from Synaptic.

---

### Post by Irishpolyglot on 2007-05-25
Hi again!! I will be trying my best to get Ubuntu to work 100% over this weekend so I can finally abandon the Windows Dual boot ;-)

SO, I have installed NDISwrapper and gone through a few threads to see if I could get any further, and the one chilli (btw thanks for that last post!! Worked a charm :) ) mentioned here: [http://ubuntuforums.org/showthread.php?t=396204](http://ubuntuforums.org/showthread.php?t=396204) (post #8 ) seemed the perfect one to go with (I do have the 4965 card) - I got through it without hitches but at the second last step when I was almost done I entered > ndiswrapper -l, and alas! > netw4x32 : invalid driver! - I tried to install the netw4x64 driver just in case (I have the 64bit ubuntu installed) but now it just lists both as invalid drivers (I hope they aren't conflicting with eachother?). I got them from the DELL website and they are definitely for this card! What can I do? I'm so close to closing this thread :-P

Ah yes, one thread that left me a bit confused was this one: [http://ubuntuforums.org/showthread.php?t=451540](http://ubuntuforums.org/showthread.php?t=451540) - he had the same problem as me, and seemed to use > liblzo2-2 and then openvpn as well as ndiswrapper... would that make any difference?

Thanks again for any help ppl!! I don't  know how you have so much patience with us n00bz :-P I hope I will some day!!

---

### Post by envoy on 2007-05-25
The NDISwrapper homepage says that 1.45-rc1 supports the 4965AGN by simply changing the ndiswrapper script. I'll check it out later.

Edit: no luck yet, no wlan0 device is created. ndiswrapper says "netw4v32 : driver installed" and " device (8086:4229) present" though...

---

### Post by Irishpolyglot on 2007-05-26
I got the same no wlan0 created error (but this was only in going through NDISwrapper's tutorial, which has quite a lot of things to go through and much more than post #8 in the link above). Don't know why it would show it installed for you and not for me... anyone else have any other thoughts? How could it be an invalid driver? What's this about changing the script?

---

### Post by Irishpolyglot on 2007-05-26
OK, I re-read the threads and it turns out a lot of people had the same problem as me because the NDISwrapper version was wrong. (I downloaded 1.44, but when I added the -v tag to see it's version it said 1.38!!) I removed that one, and downloaded v1.43 as recommended - I'm sure I'm at the last step of solving the problem but... I still have the drivers installed from the bad NDISwrapper! 
When I try to remove them with the ndiswrapper -r netw4x32, it says > couldn't delete /etc/ndiswrapper/netw4x32: Inappropriate ioctl for device
 I'm not too sure what this means... Can I just go into the directory and delete them directly? How can I get around this? Once I uninstall these drivers, I can reinstall them and theoretically the problem will be solved :D
Thanks!!!

---

### Post by envoy on 2007-05-26
I removed /etc/ndiswrapper/netw4x32 manually, since it only contained the .inf file anyway.

---

### Post by envoy on 2007-05-28
It works, with 1.45-rc3. And the latest XP (! not the Vista) driver for the 4965AGN from Intel.
A full system restart seems to have been the final missing piece for me :)

---

### Post by Irishpolyglot on 2007-05-29
Arg... I know I might just be really stupid... but I'm still on this issue :(
Gladly I think I'm past the NDISwrapper bit - I got v. 1.45-rc3 and the installation DID actually work! 
ndiswrapper -l gives > netw4x64 : driver installed
        device (8086:4229) present
 the netw4x32 one still gives error messages, but the x64 one installs fine - I assume that's better as I installed the 64bit Ubuntu edition.
Note that on installation when I entered "ndiswrapper -m", I saw:
> module configuration already contains alias directive
. Does that mean anything?
Well despite the installation working finally, my wireless itself STILL doesn't work!! "lspci | grep -i network" still gives
"0c:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)"
 - the wifi light is still not on (as it has for other people in similar questions raised on this forum) and there is still no wireless option in the Network settings... I restarted the computer and there's no difference.
What am I missing? I'm sure it's something quite obvious - but if the driver is installed it should work, right?
Thanks!!

---

### Post by vronp on 2007-05-30
> **Kobalt said:**
> You laptop has an IPW3945 wifi chipset. You can get it working pretty easily installing this : ```
sudo apt-get install linux-restricted-modules-generic
```After this reboot, and you should now be able to connect from the Network-Manager, in the top right corner of your screen.

This is not correct.  It's the new 4965 chipset from Intel.  Intel is supposed to release a Linux driver for it in June.

---

### Post by vronp on 2007-05-30
Here are a couple links:

[http://www.intel.com/network/connectivity/products/wireless/wireless_n/overview.htm](http://www.intel.com/network/connectivity/products/wireless/wireless_n/overview.htm)

[http://www.intel.com/support/notebook/sb/cs-006408.htm](http://www.intel.com/support/notebook/sb/cs-006408.htm)

---

### Post by vronp on 2007-05-30
Sorry, I forgot this most important link:

[http://www.intel.com/support/wireless/wlan/sb/cs-025330.htm](http://www.intel.com/support/wireless/wlan/sb/cs-025330.htm)

---

### Post by Irishpolyglot on 2007-05-30
Which website can I go to, to check for that update to download it, or the date that it's released? Will I just regularly check back on the Intel driver link you gave and the 4965 will appear in the next weeks? (Mid-Q2 2007 is a bit vague...) Thanks for the links!

Of course, once a Linux driver is available I will use that, but is there any particular reason it isn't working with NDISwrapper from what I've said? It has worked on this chipset with others in this forum.
Thanks again!

---

### Post by vronp on 2007-05-30
Hi,

As you suggested, I am checking the driver page for a new entry on the 4965.  I hope it is posted soon.

I can't help you with ndiswrapper because I just haven't tried to go that route.  I have a Linksys WUSB54G that I have been using with my Inspiron 9400 as I wait for the Linux driver on the 4965.

All I can suggest is that you search this forum for "4965" and try to duplicate with others have done with ndiswrapper.  However, it sounds as if you have already done this.

Good luck.

Dave

---

### Post by klyver on 2007-07-05
Hi I'm having the exact same problem. Finally gone through the ndiswrapper thing, but the wireless is still not working. Please tell me if you or anybody found a solution

---

### Post by Irishpolyglot on 2007-12-21
Hi guys!!! Months later and I'm still on the same problem; the lack of mobility on my laptop has kept me from really getting into Ubuntu and I'm still at complete newbie status because of it :(
Now the driver is available on the Intel website. I downloaded it, but I'm not sure where to go from there, regarding installing it. Should I remove the drivers installed from the steps above? BTW I'm on distro 7.10 now if that makes any difference. If someone has the patience to explain what I need to do, or a link to the relevant thread (couldn't find one that helps) I'd be so relieved!! :)
BTW, surely the updates should have been included with the 7.10 upgrade? Sorry; it's probably a really silly question... I'm just tempted to wipe the installation and start over installing from the CD again hoping it would work :P
Thanks!!!

---

### Post by Irishpolyglot on 2007-12-26
FYI: I started over and installed 7.10 and the problem was solved

---

