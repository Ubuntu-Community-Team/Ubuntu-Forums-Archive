---
title: "[SOLVED] Broadcom bcm4312 (rev 02) and Hardy Heron : a lost cause?"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by slayer^_^ on 2008-04-24
this wireless device : Broadcom bcm4312 (rev 02) doesn't work in hardy with b43-cutter (although never did, neither in guts with bcm43xx-gutsy); however, in gutsy i used to get it working very well with ndiswrapper, now i must edit the file /etc/rc.local to unload ssb, b43 and b44 and force them to load AFTER ndiswrapper, and it still doesn't work !!

I don't know what else to try, maybe the only way out is patching the kernel with the patch found at [www.linuxwireless.org](www.linuxwireless.org) ??

i am very disappointed, please let me know something about it.

---

### Post by kullu on 2008-04-26
This guide worked in my case.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
Look for the fix in case of Hardy and follow it. For driver download follow 2a. My wireless card is also same i.e. bcm4312 (rev02).

I had to compile the ndiswrapper from source(as given in above link).
Finally it worked but when I rebooted it was not detecting any network.
Thing was that it wasn't loading ndiswrapper properly. The workaround in my case was to remove 'ndiswrapper' from /etc/modules.
After restarting it worked. 
I hope it works for you also.:)

---

### Post by Ephidel on 2008-04-26
I have the same as you (BCM4312) so just in case the above quide doesn't work, this one did for me flawlessly:
[http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312)

Good luck =D

---

### Post by andrew.46 on 2008-04-26
Hi,

 There seems to be a lot of confusion on this issue. I have a BCM4312 (rev 01) which performs perfectly under Hardy Heron.

 There was no need for ndiswrapper, simply the firmware from [linuxwireless.com]("http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old"), and on reboot the card has worked perfectly ever since. I honestly don't know if there is any difference between (rev 01) and (rev 02) but I suspect that there would not be.

    Andrew

---

### Post by slayer^_^ on 2008-04-27
there's a big difference between (rev 01) and (rev 02). Kernel 2.6.24 doesn't support the (rev 02).

Thanx for your answers.

---

### Post by Ayuthia on 2008-04-28
> **slayer^_^ said:**
> this wireless device : Broadcom bcm4312 (rev 02) doesn't work in hardy with b43-cutter (although never did, neither in guts with bcm43xx-gutsy); however, in gutsy i used to get it working very well with ndiswrapper, now i must edit the file /etc/rc.local to unload ssb, b43 and b44 and force them to load AFTER ndiswrapper, and it still doesn't work !!

I don't know what else to try, maybe the only way out is patching the kernel with the patch found at [www.linuxwireless.org](www.linuxwireless.org) ??

i am very disappointed, please let me know something about it.
Another option which is similar is to compile the 2.6.25 kernel.

---

### Post by mattbytes on 2008-04-29
Another thread I need to follow.  Thanks for the info all!

---

### Post by ronaldv2li on 2008-04-30
Worked for me. I was ready to give up hardy... almost :P

---

### Post by Kopiermeister on 2008-05-01
Hello to all, just joined the community. First, i want to say sorry for my english, that's not the best...

Well, i got my wireless bcm4312 rev02 to work. But not very well. The wireless works, when my notebook is running with the electrical power supply. But when i cut it off, my wireless breaks. There are no wireless networks found, and the device isn't working anymore.

So, i downloaded the patch, but i don't know how to install it.

Any help please?

Thanks in advance!

---

### Post by slayer^_^ on 2008-05-03
try [here]("http://ubuntuforums.org/showthread.php?t=659027"): follow the gutsy or the hardy method. the choice is yours :)

have a nice day

---

### Post by Kopiermeister on 2008-05-03
> **slayer^_^ said:**
> try here: follow the gutsy or the hardy method. the choice is yours :)

have a nice day

Where should i try? There's no link. I downloaded the patch for the 2.6.24 kernel, could you tell me how to install it?

Thanks.

---

### Post by slayer^_^ on 2008-05-04
i added the link. If it doesn't work, here's how to patch your kernel for the (rev 02) broadcom cards...

INSTRUCTIONS: First, download a patch from somewhere, and move it to the /usr/src/linux directory (make sure /usr/src/linux links to the kernel you want to use). Now enter the /usr/src/linux directory:

cd /usr/src/linux

Extract the patch into the /usr/src/linux directory using your tool of choice.

There should now be a file called something like patch-2.x.x or patch-2.x.x-yy (where x stands for a version number, and yy stands for the initials of the patch or patchset, such as aa or ck) in the /usr/src/linux directory. To apply the patch to the kernel, run

patch -p1 < patch-2.x.x or patch -p1 < patch-2.x.x-yy
Note: Third party kernel patches (patches that don't come from the official kernel tree) might compromise your system (stability, security etc.) Installing several third party kernel patches usually requires patch (and/or kernel) source editing so that they can play together nicely; unless you're a developer and if you really need several patches applied to the same kernel, it is advisable to use a kernel patchset (eg: Love-Sources, Nitro Sources)

Disclaimer : I took the info [here]("http://gentoo-wiki.com/HOWTO_Install_a_Kernel_Patch").

---

### Post by chino9334 on 2008-05-07
I have a HP Pavilion DV6445US and has the Broadcom Corporation BCM4312 802.11a/b/g (rev 02) wireless card. After some time trying various guides, I finally got it to work.

I compiled ndiswrapper from source from a beginning, and had to do the hardy bug fix, on the guide that kullu posted:

> **kullu said:**
> 
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)


On this same guide I did the step 2a, and made the changes of the hardy bug fix permanent. I also did the Modifying /etc/init.d/rc.local part, version 2.0.

At first I had used this guide, which is in Spanish, but couldn't get it to work since it doesn't cover the hardy bug fix.

[http://barackman.wordpress.com/ubuntu-y-hp-pavilion-tx1232la-broadcom-corporation-bcm4312-80211abg-rev-02/]("http://barackman.wordpress.com/ubuntu-y-hp-pavilion-tx1232la-broadcom-corporation-bcm4312-80211abg-rev-02/")

I'm also running Hardy Heron on kernel 2.6.24-16-generic, the one that comes by default on the Ubuntu live CD install.

I don't know why but at this moment the download link isn't working, so I think you'll have to google-it.

---

### Post by Kopiermeister on 2008-05-10
Thank you for your answer!
But i don't have to install the patch anymore, there was a kernel update to 2.6.24-17, now it works fine without ndiswrapper!!

Kind regards,
Kopiermeister

---

### Post by d0b33 on 2008-05-10
I successfully installed the broadcom driver from my bootcamp disk using ndiswrapper but wireless would still not connect.

my card from system profiler...
```
Broadcom BCM43xx 1.0 (4.170.46.5)
```

Which driver do you recommend I use that has been confirmed to work with this chipset?

---

### Post by kevdog on 2008-05-10
What exactly does that patch do, and why do you need it?  I hate applying patches for no known reason other than "you have to!"

---

### Post by Kopiermeister on 2008-05-10
Oh no, after the reboot, there was no wireless connection anymore. So, the kernel update from 2.6.24-16 to 2-6-24-17 does not fix the rev 02 problem.

I have to try the patch.

---

### Post by esteckis on 2008-05-10
Also I think should be mentioned is that if you use encryption with the wireless device. Now in Hardy Heron, the Keyring will not let wireless engage until you provide your password and then the wireless will connect. What happened to me when I first installed Hardy, I had the wireless all set up and it would not connect. Then when I shut the computer down (by being frustrated, LOL) and re-logged on, the keyring pop-up window asked for my password. I entered the password and the wireless has connected every time now. There is supposedly a fix to have the password automatically entered upon your successful log on. I have not tried it yet because it involves the terminal. Please note there is another fix where you have to download WCID (I think it was that?). Well, when you download WCID, your network manager is disabled. This WCID fix uses the NDSwrapper. WCID did not work for me (Broadcom wireless) and I had a heck of a time trying to restore to the prior setup.

[http://www.savvyadmin.com/pam_keyrin...uthentication/](http://www.savvyadmin.com/pam_keyrin...uthentication/)

Above is the keyring fix, I question whether trying it because maybe the team is update this keyring hassle and it might cause problems, I am not sure.

My system Dell 6400 Lappy B43 driver using network manager to connect no problem.

---

### Post by Kopiermeister on 2008-05-10
I'm an ubuntu idiot. I cannot install the patch...

I copied the *patch_2.6.24 -file* into the */usr/src/linux-headers-2.6.24-17-generic -directory.*
But when I enter *patch -p1 < patch-2.6.24* i just get this error: *bash: patch-2.6.24: No such file or directory*

Pls help me!

---

### Post by Ayuthia on 2008-05-10
> **kevdog said:**
> What exactly does that patch do, and why do you need it?  I hate applying patches for no known reason other than "you have to!"
Before Hardy was released, there was a patch used to try to fix the 4312 rev 02 and 4311 rev 02 cards.  The patch caused the other chipsets to break so the developers pulled it out.  This patch is for the b43 module.  

From Kopiermeister, it sounds like they were able to get this issue fixed in 2.6.24-17.  I have not seen any confirmation on this.  Not only that, I cannot find 2.6.24-17 either.

---

### Post by Kopiermeister on 2008-05-10
> From Kopiermeister, it sounds like they were able to get this issue fixed in 2.6.24-17. I have not seen any confirmation on this. Not only that, I cannot find 2.6.24-17 either
No, sorry. I installed the kernel update and then the wireless worked perfectly. but after rebooting, the wireless card wasn't recognised anymore from hardy with the 2.6.24-17. It seems as there is no wireless card.
But when i boot the 2.6.24-16 kernel, the wireless card works again. But with the problems i've already written on the first page of the thread. So, the wireless works just with A/C connection. Not with storage battery.

Kind regards.

---

### Post by slayer^_^ on 2008-05-12
i wrote a guide for the laptop hp 6720s that uses the infamous broadcome bcm4312 (rev 02) wireless device here:

[http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966)

i listed all the methods that i know to make it work on hardy, please post your experience...

---

### Post by Kopiermeister on 2008-05-12
Thank you!! Nice guide.

But i have a problem:
The /usr/src/linux directory does not exist, so i made a folder called linux and copied the patch into it.
But when i go into that folder and enter "sudo patch -p1 < patch_2.6.24_for_4311_2" in the terminal i just get this message:
```
maxey@maxey-laptop:/usr/src/linux$ sudo patch -p1 < patch_2.6.24_for_4311_2
[sudo] password for maxey: 
can't find file to patch at input line 13
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|This combined patch includes all the changes required to update the the mainline
|git tree, or the 2.6.24-rcX code base, to incorporate the changes needed to operate
|the BCM4311 rev02 and BCM4312 rev02 (G PHY only) chips. These patches match the
|changes incorporated in the everything branch of the wireless-2.6 git tree for which
|'git describe' yields "v2.6.24-rc1-2199-g65d438b", plus the BCM4311/2 modifications.
|
|Larry
|--------
|
|diff -up -X linux-2.6/Documentation/dontdiff linux-2.6/drivers/ssb/b43_pci_bridge.c wireless-2.6/drivers/ssb/b43_pci_bridge.c
|--- linux-2.6/drivers/ssb/b43_pci_bridge.c	2007-11-20 15:13:44.000000000 -0600
|+++ wireless-2.6/drivers/ssb/b43_pci_bridge.c	2007-11-20 18:43:49.000000000 -0600
--------------------------
File to patch: 


```
And then the cursor stays blinking...

Any help? Or schould i copy the file into the "linux-headers-2.6.24-17-generic"-folder?

Regards,
Max

---

### Post by slayer^_^ on 2008-05-12
mmm can't tell ya... i can't try now :(

however, THIS IS THE solution, please help me to do the right codification of commands to apply the patch ;)

---

### Post by Kopiermeister on 2008-05-13
Found something interesting!!
Pls have a look [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197959") and check out the 4 hyperlinks (you have to scroll down to one of the last posts).

I had a look at the links and there is written much of the b43 fix with lots of files to download etc. But i don't know what to do with this information, perhaps someone of yours know...

Regards

---

### Post by slayer^_^ on 2008-05-13
please try to copy the patch in /usr/local/linux folder and directly execute it...

---

### Post by Kopiermeister on 2008-05-13
> **slayer^_^ said:**
> please try to copy the patch in /usr/local/linux folder and directly execute it...
But there is no folder called "linux". There are only folders called "linux-headers-2.6.24-17-generic", "linux-headers-2.6.24-17", "linux-headers-2.6.24-16-generic" and "linux-headers-2.6.24-16"

So does the "linux"-folder mean one of the "linux-headers......"-folders?

---

### Post by Ayuthia on 2008-05-13
> **Kopiermeister said:**
> Thank you!! Nice guide.

But i have a problem:
The /usr/src/linux directory does not exist, so i made a folder called linux and copied the patch into it.


/usr/src/linux is a symbolic link to the current linux-headers version.  So you will need to remove the files you have placed in /usr/src/linux and then do:
```
sudo ln -s /usr/src/linux-headers-2.6.24-17-generic /usr/src/linux
```

---

### Post by slayer^_^ on 2008-05-13
i have got the /usr/src/linux folder that is a link to the kernel folder (generic)... i wonder why i've got it and many others have not...

however, try to apply the put the patch in the usr/src/linux-headers-2.6.24-17-generic folder and using my guide... let's see if it works...

at the moment i can't try (however i managed to do it...) , surfing the net i discovered that the patch works no more with the last kernel updates...

let's see if it's true.

please give it a try :)

---

### Post by Kopiermeister on 2008-05-13
So, i tried. But it's still the same problem.
I copied the patchfile into /usr/src/linux-headers-2.6.24-17-generic -folder and when i enter the patch command, i still get this "error"
```
maxey@maxey-laptop:/usr/src/linux-headers-2.6.24-17-generic$ sudo patch -p1 < patch_2.6.24_for_4311_2
[sudo] password for maxey: 
can't find file to patch at input line 13
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|This combined patch includes all the changes required to update the the mainline
|git tree, or the 2.6.24-rcX code base, to incorporate the changes needed to operate
|the BCM4311 rev02 and BCM4312 rev02 (G PHY only) chips. These patches match the
|changes incorporated in the everything branch of the wireless-2.6 git tree for which
|'git describe' yields "v2.6.24-rc1-2199-g65d438b", plus the BCM4311/2 modifications.
|
|Larry
|--------
|
|diff -up -X linux-2.6/Documentation/dontdiff linux-2.6/drivers/ssb/b43_pci_bridge.c wireless-2.6/drivers/ssb/b43_pci_bridge.c
|--- linux-2.6/drivers/ssb/b43_pci_bridge.c	2007-11-20 15:13:44.000000000 -0600
|+++ wireless-2.6/drivers/ssb/b43_pci_bridge.c	2007-11-20 18:43:49.000000000 -0600
--------------------------
File to patch:  
``` and of course the blinking cursor...

I think it seems that the patch needs files cannot be found ?!

---

### Post by slayer^_^ on 2008-05-13
on launchpad i read that this patch works no more with the recent kernel updates... well i've not tried yet...


however, does the card work with ndiswrapper?

---

### Post by Kopiermeister on 2008-05-14
Recent kernel updates... so the 2.6.24-17 and -18? Does it work for the 2.6.24-16?
Yes, with ndiswrapper it worked perfectly with gutsy, so i think it should work with hardy, too.
What about using the 2.6.25 kernel?

---

### Post by slayer^_^ on 2008-05-14
compiling 2.6.25 kernel is another solution to get it working definitely. i can assure you that with fedora 9 it works with the b43 module (b43-fwcutter).

however it's not, according to everyone, a simple solution for the average user... and maybe it fixes a error you got, but causes you many more.

I think that we must see if we can use the patch with the hardy kernel, or we must use ndiswrapper waiting for ubuntu 8.10...

please tell me if you can get it working with ndiswrapper on hardy heron :)

(I'm sorry but i can't use that laptop by now...)

---

### Post by Kopiermeister on 2008-05-14
With ndiswrapper it should work, here's a [How To]("http://ubuntuforums.org/showthread.php?t=766560&highlight=BCM4312").

Have you tried compiling to the 2.6.25 kernel?
Or what about using the 2.6.24-12, which is the latest one the card worked with, right?
Do you know anything about gutsy and the bcm4312 rev02? Cause perhaps i'll go back to gutsy.

And i think i will try fedora 9 ;)

---

### Post by slayer^_^ on 2008-05-16
yes, it works with ndiswrapper on gutsy, see this other guide..

[http://ubuntuforums.org/showthread.php?t=659027](http://ubuntuforums.org/showthread.php?t=659027)

thanx ;)

---

### Post by Kopiermeister on 2008-05-17
(*,)
I can't believe it... I installed Fedora 9 to test the wireless card, cause of the 2.6.25 kernel that SHOULD solve the b43 curse...

1. Good, the card is recognised by the system, whithout installig anything. B43-fwcutter was also installed already.
2. I went to linuxwireless.org and fallowed the "2.6.25 kernel guide"
3. Good, everything worked great, no problems extracting the firmware...
4. Restart
5. *jump jump jump* the card works, successfully connected to my network, no problems with wpa/wpa2. So everything SEEMS to work great...
**BUT**
When i pull of the power supply unit, and the notebook is running with the battery, the wireless connection breaks again!!
It's horrible!!!
The same curse than with Hardy, so, in my opinion, the 2.6.25 does NOT solve the problem!!

:confused:

---

### Post by StaceyRVC on 2008-05-17
I used this site [http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/](http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/) to get my broadcom to connect and haven't had an issue since

---

### Post by Kopiermeister on 2008-05-17
> **StaceyRVC said:**
> I used this site [http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/](http://blog.roberthallam.org/2008/04/broadcom-4318-ubuntu-hardy-heron-ndiswrapper/) to get my broadcom to connect and haven't had an issue since
Yes, i know that the card works with ndiswrapper. But i need the b43 drivers, because i want/need to use aircrack, kismet and this fantastic tools :)

Thanks though!

---

### Post by kevdog on 2008-05-17
Off topic, but get an Atheros card if your planning on aircrack and kismet.  madwifi is much more predictable as this thread and thousands of others prove if your doing aircracking.

---

### Post by Kopiermeister on 2008-05-17
But I think it's not that easy to change the wireless card of my notebook...
And, the wireless card works with fedora, but just with power and not with battery. That's the only thing that's a pain on my neck.
And i testet aircrack and kismet already, it works with the card :) But as I said already, not with the notebook running with the rechargeable battery.

Thanks though!

---

### Post by slayer^_^ on 2008-05-20
i can assure you that with fedora 9 it works great even with the battery. thus i suggest to compile your 2.6.25 kernel to use hardy...

or keep using ndiswrapper until intrepid ibex :))

---

### Post by Kopiermeister on 2008-05-26
No, with fedora 9 it doesn't work with the battery for me with the 2.6.25.3-18 kernel. with the standard 2.6.25 it works great.
A really sad thing...

---

### Post by andrew.46 on 2008-05-28
Hi:

> **slayer^_^ said:**
> there's a big difference between (rev 01) and (rev 02). Kernel 2.6.24 doesn't support the (rev 02).

Oops, my apologies. Looks like the patch to allow the rev 02 card to run under Hardy has been deliberately withheld.

To make up for my ignorance I note that some have managed to get this card working:

[https://answers.launchpad.net/ubuntu/+question/30908](https://answers.launchpad.net/ubuntu/+question/30908)

and one gentleman has been good enough to make a debian package of the patched kernel. Perhaps this might get your BCM working?

        Andrew

---

### Post by Kopiermeister on 2008-05-30
I tested the *.deb files. With a new hardy installation it works. I mean, the card is recognised by the "restricted driver manager" and after extracting the firmware the card seems to work.
But i have to say, that i can't find every wireless network around (for example, there is a network called "edv1" and i can find and access it with windows xp, but not with ubuntu. I can't see the network with the network manager), and the card still doesn't work with the notebook battery.

Anybody with the same problem?

EDIT: The Patched *.deb files don't work with the 2.6.24-17 kernel. There, the card isn't recognised anymore by the system.

---

### Post by slayer^_^ on 2008-06-01
perfect, we did it ;)

---

### Post by Kopiermeister on 2008-06-01
> **slayer^_^ said:**
> perfect, we did it ;)

Does the card work for you without problems, now? For me, it still doesn't.

---

### Post by slayer^_^ on 2008-06-02
mmm, please check your hardware! Are you sure it is bcm4312 _(rev 02)_ ?? I mean, it works for me with fedora 9, both plugged or not, why doesn't yours? 

Moreover, many people wrote me that the infos on bcm4312 (rev 02) i put in my new guide for the HP 6720s laptop made their cards work : [http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966) . So i find it strange you can't!

Please let me know more about your hardware...

---

### Post by Swathe on 2008-06-02
I can see the wireless networks I just can't connect to them :(

---

### Post by Kopiermeister on 2008-06-02
> **slayer^_^ said:**
> mmm, please check your hardware! Are you sure it is bcm4312 _(rev 02)_ ?? I mean, it works for me with fedora 9, both plugged or not, why doesn't yours? 

Moreover, many people wrote me that the infos on bcm4312 (rev 02) i put in my new guide for the HP 6720s laptop made their cards work : [http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966) . So i find it strange you can't!

Please let me know more about your hardware...

Yes, i'm shure i've got a bcm4312 rev02!! With fedora 9 it worked for me, too. But only with the standard kernel (2.6.25) not with the kernel security update (2.6.25.3-18 )

Think i'll try wicd and uninstall network-manager.

regards

---

### Post by slayer^_^ on 2008-06-02
it is quite strange because mine keeps working with fedora updates ... 

let me know if you find a solution :(

---

### Post by Kopiermeister on 2008-06-02
It's a horror!!!
With wicd it doesn't work, too! After every reboot, wicd doesn't start anymore. So I had to install network-manager-gnome again. I removed and reinstalled b43-fwcutter & firmware again, but no success... :(

Now, network-manager does not find any wireless networks anymore...

But i don't think the card is damaged, cause with windows xp it works quite well...

But i want to use linux, not windows :)

Pls tell me if someone has the same problem than me!!

Regards

---

### Post by slayer^_^ on 2008-06-02
if you're using hardy and you haven't patched your kernel you can't use the (rev 02) hardware.

you can try ndiswrapper... try my hardy tutorial

[http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966)

bye!

---

### Post by Kopiermeister on 2008-06-03
I have patched my kernel! I used the *.deb files from the launchpad page you posted.
I think i'll reinstall hardy another time and try it again.

regards

---

### Post by Kopiermeister on 2008-06-03
I think i'll try opensuse 11.0
It's with kernel 2.6.25 and the final release will come in 16 days...

regards

---

### Post by Kopiermeister on 2008-06-04
:guitar:
Jeah, it works!!! With the RC1 of opensuse 11 it works!!! :guitar:

---

### Post by andrew.46 on 2008-06-04
Hi:

> **Kopiermeister said:**
> :guitar:
Jeah, it works!!! With the RC1 of opensuse 11 it works!!! :guitar:

Congrats! I guess you will be sticking to Open Suse until Ubuntu ships a newer kernel? Good to see that wireless is finally coming to Linux with a degree of success though.

        Andrew

---

### Post by slayer^_^ on 2008-06-04
i like the kernel of opensuse, but i really don't like his graphic asset (and its horrible menu!!! argh!!!).

How is it possible that everyone managed to get this card working with ndiswrapper on hardy???

---

### Post by slayer^_^ on 2008-06-06
You can give another chance to Hardy Heron...

You got to compile a patched kernel and then install it.

Let me see, so i can update the guide too...

_Before you follow this method please take a backup of your data, the result could be a damage of your ubuntu installation..._

Let's compile a patched kernel from the linux-source  package:

```
sudo apt-get install linux-source
mkdir ~/src
cd ~/src
tar xjvf /usr/src/linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24
```

Now let's configure it. We will re-use the configuration of the already running kernel:

```
sudo cp -vi /boot/config-`uname -r` .config
```

We'll need some packages now for the next step

```
sudo apt-get install libncurses5 libncurses5-dev
```

Now let's run:

```
sudo make menuconfig
```

Here you can choose your modules. you won't need this, but i suggest you to unselect "Kernel Debugging" (under "Kernel Hacking) for a lighter kernel.

Before compiling our kernel, we need to patch it!

Be sure yo ugot the necessary packages:

```
sudo apt-get install linux-source-2.6.24 kernel-package build-essential
```

Download the patch:

[http://linuxwireless.org/download/b43/patch_2.6.24_for_4311_2](http://linuxwireless.org/download/b43/patch_2.6.24_for_4311_2)

Drag and drop the patch file in the directory /yourusername/src/linux-headers-2.6.24-18-generic (well the name of the folder may be a bit different...however there should be only one!)

Now, in terminal:

```
sudo patch -p1 --dry-run < patch_2.6.24_for_4311_2
```

If all looks good, re-run the patch command and remove the --dry-run to do it for real. 

Now we got to compile our patched kernel!

If you got a dual core or quad processor, you'll be happy to use it! Give this info to the terminal _only_ 

If you got a Dual Core:

```
export CONCURRENCY_LEVEL=3
```

If you got a Quad Core:

```
export CONCURRENCY_LEVEL=5
```

because the number in the end means 1 + "the number of your processors".

Now, finally, let's compile our patched kernel (copy and paste as it is written):

```
sudo fakeroot make-kpkg --initrd --append-to-version=-some-string-here kernel-image kernel-headers
```

Let it compile...

When it has finished, you got your patched kernel in the folder /home/yourusername/src/ directory. 

It is a *deb archive (there should be two packages, one for the image, one for the headers). 

Install it and enjoy...  :)

p.s. perhaps I've forgotten one or two packages needed to perform all the operations i posted. In this case the terminal should help you ;)

_Please_ post your experience here, if this method works for you please let us all now... It is not easy to find someone that teaches you to recompile a kernel :(

---

### Post by slayer^_^ on 2008-06-06
I heard that also a Hardy Heron updated (after unlocking the "proposed" section of the repositories) supports the bcm4312 (rev 02) wireless card.

---

### Post by Kopiermeister on 2008-06-09
@slayer: pls let mi know if you've got a hardy 32-bit or a 64-bit system.
Cause i made a "nice" discovery...
I tried opensuse 11 32-bit and 64-bit. And my card just works with the 64-bit operating system. With the 32-bit system, the card does not work with the notebook battery!!
So, perhaps it's the same issue in ubuntu. Perhaps the card just works with 64 bit?
So pls tell me which version of hardy u use!!

regards!!

---

### Post by slayer^_^ on 2008-06-11
i use a 32 bit version on my laptop..

however i've read that a patch for this card has been put in the "proposed" section of the repositories.

So a full update having unlocked the "hardy-proposed" section should do the trick.

Take a try!

---

### Post by Kopiermeister on 2008-06-11
Ok, i'll try! Is the patch available for the 32- and 64-bit system? or just for 32-bit?
Cause i tried 64 bit and i really like it... no real problems...
And...i'm really starting to like opensuse... so it's good that the ubuntu-patch is now available :)

regards

---

### Post by slayer^_^ on 2008-06-11
1) the update available in the "hardy-proposed" section of the repositories is, obviously, available both 32 bit and 64 bit.

2) the kernel patch, that allows you to recompile a kernel that lets your bcm4312 (rev 02) card work is binary, so it works for both 32 bit and 64 bit.

you should find everything you need here in my tutorial

[http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966)

best regards ;)

---

### Post by Kopiermeister on 2008-06-16
At the moment, i'm downloading virtual box in suse that i can try hardy... Do you know if i can test the wireless device in a virtual pc? or do i have to install it "really" ?

Regards,
Kopiermeister

---

### Post by slayer^_^ on 2008-06-17
mmm can't tell ya... however, the guys that tried the wireless device in hardy, have written in my tutorial ( [http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966) ) that they managed to make it work updating hardy (after having unlocked the hardy-proposed section).

I really suggest you to make a try ;)

---

### Post by Kopiermeister on 2008-06-17
jeah, i've installed ubuntu hardy heron about an hour ago, just have to wait until i'm at home to have a wired internet connection to download the updates.
Hope it will work!!

---

### Post by Kopiermeister on 2008-06-17
Well, i have unlocked the hardy-proposed repository. Result: Wireless device recognised by hardy and after installing b43-fwcutter and firmware and restarting the system, my wirelesscard seems to work... i can connect to my wireless network, but the connection is very, very slow. just 2mbit/s.
So if i enter for example [www.google.de](www.google.de), it doesn't work, i always get the "adress not found" error message, i think because of the long time it takes to load a site... i always get this "timeout"...

anybody the same problem?

I use hardy 64 bit

best regards

EDIT: And when i'm connected to a wired network, i can't see any wireless networks anymore

---

### Post by Kopiermeister on 2008-06-23
Well... I tried it again with hardy 32-bit now. It's a horror. With the 32-bit system it works, but still not with the notebook battery.
And as I said already, with the 64-bit system i'm connected to my wireless network, but i can't look up any site in the internet...
Very, very strange...

Well, sorry, think I have to use opensuse until ubuntu 8.10 is out... A long time, perhaps a positive result will be found in a while...

regards,
Kopiermeister

---

### Post by slayer^_^ on 2008-06-23
found nothing useful here? [https://wiki.ubuntu.com/HP_dv6000_Series#head-620e0d4896ac78e30bde75792dc1ccaf3e2c79ba](https://wiki.ubuntu.com/HP_dv6000_Series#head-620e0d4896ac78e30bde75792dc1ccaf3e2c79ba)

---

### Post by Kopiermeister on 2008-06-24
> **slayer^_^ said:**
> found nothing useful here? [https://wiki.ubuntu.com/HP_dv6000_Series#head-620e0d4896ac78e30bde75792dc1ccaf3e2c79ba](https://wiki.ubuntu.com/HP_dv6000_Series#head-620e0d4896ac78e30bde75792dc1ccaf3e2c79ba)

No, unfortunately not.
> On Ubuntu 8.04 Hardy it is enough to install the package b43-fwcutter .
But this is just for rev01 cards. Thank you for the link, but it's no help for me.

Regards

---

### Post by slayer^_^ on 2008-06-24
so, updating after having unlocked the repositories doesn't help you uh? have you tried wicd instead of network-manager ?

usually it solves many things.

so, when you've got time, install ubuntu hardy 64 bit, update it unlocking all the repositories, install the package b43-fwcutter and install wicd.

regards :°D

---

### Post by Kopiermeister on 2008-06-25
OK, i'll try. Hope it will work then.

Regards

---

### Post by Kopiermeister on 2008-06-25
So, installed hardy 64-bit again, installed b43-fwcutter and firmware, installed wicd and removed network-manager.
No real positive result. I can connect to my wireless network, but i only can "surf" in the web for about 10 seconds. I'm just fast enough to type in "www.google.de" and i get a result. But when i want to search for something then, nothing happens. wicd tells me, that i'm connected to the network, but i can't view any site again...

It's frustrating... :(

---

### Post by slayer^_^ on 2008-06-25
have you tried to specify a static ip instead of assigned by dhcp? with wicd, obvious... it works for so many ;)

try also wep instead of wpa :D

---

### Post by Kopiermeister on 2008-06-25
> **slayer^_^ said:**
> have you tried to specify a static ip instead of assigned by dhcp? with wicd, obvious... it works for so many ;)

try also wep instead of wpa :D

Ok, i'll try wep... But i don't think there's something "wrong" with the wpa encryption, cause wpasupplicant is installed.
And what is the difference if i use wpa or wep? cause i am able to connect to the network and i get an ip adress... so what should be wrong with dhcp?
I don't understand... :confused: But i'll try your hints.

Do you know any usernames, this card works perfectly for? So i could ask them for their settings etc.

Hope i get this working, i want to stay with ubuntu, it's still my favourite distribution.

Thanks in advance!

regards

---

### Post by Kopiermeister on 2008-06-25
Thank you!! Thank you!! Thank you!! It works!!!!!
With WEP it works!!!

Thanks for your GREAT help!!!
:guitar:

---

### Post by slayer^_^ on 2008-06-26
OOOOOOOOOH, finally we managed to get your card to work :°D

I am happy for you :°D

p.s. why don't you now write a tutorial for your laptop as I did for mine? ;) [http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966)

Have a nice day and enjoy your oo-boo-ntoo .D

---

### Post by Kopiermeister on 2008-06-26
> **slayer^_^ said:**
> OOOOOOOOOH, finally we managed to get your card to work :°D

I am happy for you :°D

p.s. why don't you now write a tutorial for your laptop as I did for mine? ;) [http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966)

Have a nice day and enjoy your oo-boo-ntoo .D

:( I was happy... but not for a long time. i had removed ubuntu and opensuse and installed hardy 64 bit again, that i can use the "suse-discspace" with hardy. and after updating the system with "aktivated" hardy-proposed repository, i wasn't able to connect to the network anymore... don't know why... Yesterday, after changing wpa-encryption to wep-encryption, i was able to connect and "surf" for minutes, so i did what i've written above. removed hardy and suse, and installed hardy again... i don't know why it doesn't work anymore, cause i did everything the way i did it, when it worked... strange, strange, strange... :(
I'm fed up with the b43... I'll use ndiswrapper until ubuntu 8.10 is released.
So, i can't use some nice programs, like kismet, aircrack etc... but i'll have a working wireless.

Thank you very much for your help and the time you spent!!! But now, i have to use ndiswrapper, cause i don't want to use an other linux distribution. I'll have a look at your tutorial for the ndiswrapper way...

Thank you slayer, thank you very much! I'm sorry it was without success.

Kind regards,
Kopiermeister

---

### Post by Kopiermeister on 2008-06-26
Jeah, with ndiswrapper it works perfectly!!! Thank you for your great tutorial!!! *thumbs up*

Regards

---

### Post by slayer^_^ on 2008-06-27
ehm, after you re-installed everything, did you specify a static ip or dynamic? perhaps it was the static ip that made everything work, and not the wep encryption.

However, in my tutorial there's also a kernel-patching method that allows you to use the bcm4312 rev 02 card. If a simple upgrade doesn't work:

1) try installing the package "linux-backports-hardy-generic" (of course unlock all the repositories).

2) Compile your own Hardy Heron 64-bit _patched_ kernel. In my tutorial you'll find everything you need.

Try that before you surrender to ndiswrapper, because you could use a 64 bit (patched) Hardy Heron!

Have a nice day :D

---

### Post by Kopiermeister on 2008-06-27
> **slayer^_^ said:**
> ehm, after you re-installed everything, did you specify a static ip or dynamic? perhaps it was the static ip that made everything work, and not the wep encryption.

I've never specified a static or dynamic ip. Wep and dhcp worked. Well, as i said, just one time. :)

Ok, i'll try to patch the kernel, when i've got enough time :popcorn:

Regards

---

### Post by enboig on 2008-06-29
I have been able to connect using b43 wireless driver from restricted drivers, but just to open networks; when I try connect to a wpa encrypted connection it appear as connected but I am unable to ping anywhere.
How could I check it further to find where the problem is and to find a solution?

thanks

PS: I don't give up, I don't want to use ndiswrapper

---

### Post by enboig on 2008-06-29
My apologies; I had a problem with the MAC filter on the second router; I can connect without any problem using b43 driver using WPA, with no encryption, etc...
My card is (lspci):
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

And I have used no patch nor anything; just a clean install, updated everything, using 3rd part (no proposed, no backports).
Now I will start with the touchscreen and nvidia card from my hp tx1320 laptop

---

### Post by slayer^_^ on 2008-06-30
great!

I hope Kopermeister finds how to get his card working too ;)

:popcorn:

---

### Post by Lisanels on 2008-06-30
bcm43xx-fwcutter-006-4.fc9.i386

I've used the bcm driver via. the above package, and it's working great.  I avoid using ndiswrapper.

---

### Post by slayer^_^ on 2008-07-03
i guess you're talking about fedora :confused:

---

### Post by Kopiermeister on 2008-08-02
Hello everybody!
Just wanted to tell you that my wireless works now with the b43 driver!! :) Not really perfect, sometimes a bit slow, sometimes really fast... don't know why... But it works an that's the important thing!! I also had to write a little startup script, cause the card was not loaded automatically.
Thx allot for your help!!

Regards,
Kopiermeister

:popcorn:

Edit: kernel 2.6.24-20

---

### Post by superm1 on 2008-08-07
With the 4312, you can try out the broadcom official driver instead.  From the cards i've tried it on, it's got a modest increase in performance.

[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by slayer^_^ on 2008-08-12
as soon as i´ve got time, i&#314;l give it a try... thank you very much

---

### Post by JunnyJunJun on 2008-08-21
Hello, my laptop uses a Broadcom bcm4312 (rev 01).  I'd like to start off by saying I've went through the first 3 pages of this thread trying to get my wireless to work but to no avail and have decided to ask more directly.  So if someone already posted how to solve my problem please let me know because I'm just about ready to give up.

I keep seeing that rev 01 is supported by Ubuntu 8.04 in this thread but I am still having trouble keeping my wireless connection intact after a reboot.  After a reboot I have to go into System->Administrator->Network and retype all my router settings again a few times to get connected again.  I've already tried using the firmware version from [http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-old)

and still the problem exists.

---

### Post by slayer^_^ on 2008-08-21
If it is a rev ö1 just try a fresh install of ubuntu, then unlock every repository and then just install the package b43-fwcutter...

if you haven´t tried this passage, please do so..

if you have and it didn´t work, please check my post [http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966) , every method I posted should work...

please, before trying those methods, try the newer one suggested by the guy with the super mario avatar (but I haven´t tried it, so I can´t say...).

Please feel free to post your experience (even if rev 01 is ot)

bye :)

---

### Post by jarome on 2008-08-23
> **slayer^_^ said:**
> If it is a rev ö1 just try a fresh install of ubuntu, then unlock every repository and then just install the package b43-fwcutter...

if you haven´t tried this passage, please do so..

if you have and it didn´t work, please check my post [http://ubuntuforums.org/showthread.php?t=781966](http://ubuntuforums.org/showthread.php?t=781966) , every method I posted should work...

please, before trying those methods, try the newer one suggested by the guy with the super mario avatar (but I haven´t tried it, so I can´t say...).

Please feel free to post your experience (even if rev 01 is ot)

bye :)

I have tried every method, including the new beta driver with no success. Currently I am using ndiswrapper compiled from the latest source. I think the problem is not the drivers, but the Ubuntu Network manager. How can I configure wpa2 manually?

For example, I can scan the network and see my net:
> iwlist wlan1 scanning
wlan1     Scan completed :
          Cell 01 - Address: 00:18:39:F6:79:11
                    ESSID:"lan4116"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:98/100  Signal level:-33 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

So the wireless is working I think. It is the wpa2 encryption that is not.

So I am unsure of how to set up /etc/wpa_supplicant.conf and /etc/networks/interfaces. I think they need to have the info on the encryption. The gnome network manager strips this from the interfaces file.

---

### Post by jarome on 2008-08-24
It was the Gnome NetworkManager, even the latest version from their web site. I installed wicd ([http://wicd.sourceforge.net](http://wicd.sourceforge.net)), rebooted, and wireless worked the first time. I am using ndiswrapper.

---

