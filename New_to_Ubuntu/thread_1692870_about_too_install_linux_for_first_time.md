---
title: "about too install linux for first time"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by sogeking99 on 2011-02-22
hi, i have a new laptop, i intend to shrink my windows os(included with new laptop) to about 100GB, leaving me with 250GB for ubuntu.

i've done research and i believe i want 3 partitions right? '/' 'swap' and 'home? i have 4GB of ram so i want swap to be 2GB dont i?

i dont know how big the others should be, and also, what file system to use

thanks, pretty nervous :D

---

### Post by sikander3786 on 2011-02-22
Welcome to the forums :-)

Baically you just need 2 partition, '/' and swap. Separate /home is handy in case of re-installs as it preservers all your settings/data.

For some basic info, see here.

[http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/02/manual-advanced-partitioning-in-ubuntu.html)

Feel free to post back any queries you've got.

---

### Post by sogeking99 on 2011-02-22
thanks. i think a home partition would be helpful. that will just be the remaining space from the hdd right?

not sure how big to make '/' i dont want it to be too small and have it give me problems.

---

### Post by marl30 on 2011-02-22
It's good you have decided to try Linux, but have you checked to ensure  that your computer's hardware is fully compatible with Ubuntu? Perhaps if  you post your computer's name/hardware specs here someone could verify whether or not it  will work flawlessly. Most hardware work out the box in Ubuntu, but  there are also occasions where some may need some tweaking to get  working. Just want to make sure you start off on the right footing. :)

Welcome to the forum btw.

---

### Post by sogeking99 on 2011-02-22
thanks :)

here is my laptop [http://www.ebuyer.com/product/237739](http://www.ebuyer.com/product/237739)

should be fine right? just need 64bit version?

---

### Post by scheuri on 2011-02-22
Hi there

1) There is no NEED to install 64bit Ubuntu. The 32bit would run as well, but would not be able to address the full 4 GB RAM without some minor tinkering (using a kernel having PAE enabled)

2) Its hard to say that you are "safe" with that laptop. Laptops unfortunately use hardware that are specially tinkered for them usually ending up with different drivers as the "same" hardware components you would buy for a desktop computer.
You might just try a Live CD from Ubuntu (running Ubuntu without installing it right away) and try your stuff like Internet, Audio, etc.

3) A way to check whether there are already people using your kind of laptop you may want to have a look at:
[http://www.linux-laptop.net/](http://www.linux-laptop.net/) (there might be other sites for those information, too).

4) as for partitioning I higly recommend using three partitions. One for swap, one for / and one for /home. So if you ever have to reinstall you can leave your /home and reuse your data and settings (but always, always, always, always, always back up your data!!!!!!!!).
You have 320 GB of storage available, so I would suggest you make at least 4 GB of swap (lets say max. 8 GB), a minimum of 10 GB (I'd say 20 GB) of / and the rest for /home. That is, I guess, a safe bet unless you really really really need every byte for your home.

Good luck
Best regards
scheuri

---

### Post by sogeking99 on 2011-02-22
thanks. really hope it does work, the purpose of the laptop is to run linux.

---

### Post by mastablasta on 2011-02-22
yep, try it with the LiveCD (or live USB) first.
 
i would just like to add that if you are worried about partitions Ubuntu installer can autoparittion the disk for you. you can easilly create home partition after install.
 
on and be carefull with windows partitions (have a restore disk ready). sometimes preinstaleld windows come wih 4 primary partitions, so you will need to modify that so that linux can use one of those.

---

### Post by sogeking99 on 2011-02-22
ok thanks, so why not get 64 bit ubuntu?

---

### Post by mastablasta on 2011-02-22
you can use 64bit. note that if a program is made for 64bit as well the whole thing will run faster. if it's made for 32bit it could run a bit slower. most programmes are 32bit (still i think). but in Ubuntu i guess you should go with 64 bit (not just because of ram but also because processor will be used better)

---

### Post by sogeking99 on 2011-02-22
cool, just waiting for postal force to bring me my laptop, should be here today during AM time.

---

### Post by sogeking99 on 2011-02-22
ok i have the laptop but when i try to boot usb with ubuntu i get an error messege 'book error' then i have to restart with windows as boot priority again.

not a good start :(

---

### Post by sogeking99 on 2011-02-22
ok pretty concerned now, the usb boots fine on my pc, i bought this laptop just for linux really :(

is this the right iso for this laptop?

iso: ubuntu-10.10-desktop-amd64.iso
laptop: [http://www.ebuyer.com/product/237739](http://www.ebuyer.com/product/237739)

---

### Post by bill516 on 2011-02-22
Hmmm, I used an Asus not unlike yours with Ubuntu and I had no problems with it.

When you say "boot USB" tell us more clearly what you mean.  Are you trying to boot the liveCD in the DVD drive?  Are you trying to boot a system contained on a USB jump-drive?

What exactly are you trying to do and what is the error message?

Have you checked the integrity of the liveCD you burned?  If it has errors or if you merely copied the iso file rather than burning it the disk will not work.  If you have not burned iso files previously there is a first-rate write up on how to do it in Community Docs.

The Bios on your machine probably will try to boot a liveCD from the DVD drive if it detects the disk in the drive, but if it does not go into the BIOS and check the boot order.  If you need to adjust it, just make a change so that your machine boots first from the DVD drive.

If you try to run a system from a USB stick you can do that, but you may have to bring up a "boot menu" and select the USB device.  Pressing F1 or F8 while the machine starts its boot process generally does it.

Don't be discouraged!  Just post back with what is going on.  There are people here much better informed than I am and one of them will help you.

Your Asus laptop is a good one and it should work fine for you.

And have fun!

---

### Post by sogeking99 on 2011-02-22
thanks :)

i put the live ubuntu iso on my usb with universial usb creator and it works fine on the pc, but when i try it on my new laptop i am getting 'boot error' and must restart and remove usb.

i have tried setting it as top priority and also pressed escape while starting up and manually choosing to boot from the usb drive. but ti still takes me to a blacks creen with just one messege 'boot error'

sorry for lack of information on my first post.

---

### Post by ivanovnegro on 2011-02-22
Ok, if booting from USB is not working, try the Live CD.
Normally it has to work from USB but I often encountered problems with this method, dont know why.

---

### Post by sogeking99 on 2011-02-22
sadly i have no blank cd's

---

### Post by spydeyrch on 2011-02-22
Yes, if you have a 64 bit CPU, then that would be the correct one. Sometimes the universal usb creator doesn't run correctly and thus doesn't "install" the iso the correct way. It has happened many times to me. I just re-format the usb drive as a fat32 and then run the universal usb creator again. If that doesn't work, give unetbootin a try. Again, there will be times when it won't install correctly to the usb drive for some reason. Just re-install it again to the usb drive and give it a try.

-Spydey

---

### Post by sogeking99 on 2011-02-22
but it does work on my pc, just not my laptop

---

### Post by sogeking99 on 2011-02-22
i got it on but there is no sound, i typed lspci -v | less in the  terminal and there is no sound card listed. does this mean the laptops  sound card is not compatible with linux?

---

### Post by ivanovnegro on 2011-02-22
> **sogeking99 said:**
> i got it on but there is no sound, i typed lspci -v | less in the  terminal and there is no sound card listed. does this mean the laptops  sound card is not compatible with linux?

Maybe, could you post the output here and someone experienced could take a look on it to know what to do. I have no idea about sound cards.
But there is also a section to install proprietrary drivers on Ubuntu if not recognized.
Go to System-> Administration-> Additional drivers.

---

### Post by sogeking99 on 2011-02-22
ok, heres the output
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
        Subsystem: ASUSTeK Computer Inc. Device 1f27
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 1be2
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at e080 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
        Subsystem: ASUSTeK Computer Inc. Device 1f27
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at d540a000 (64-bit, non-prefetchable) [size=16]

if i cant have sound i will be devastated, this laptop i bought just for linux :(

---

### Post by sogeking99 on 2011-02-22
ah, i installed it and had many issues, first off all it had no gui, so i opened it in failsafe  gui and updated the OS(which may i say is much better than windows updater!) and this seems to have fixed everything, *phew*

looking around the software center, so great nearly everything i need seems too be there already.

is there a free book or something to learn bash? i know most about dos, growing up with dos makes bash seem strange too me, but i would love to learn it.

i also need to sort out flash and stuff as youtube doesn't work.

thanks guys

---

### Post by ivanovnegro on 2011-02-22
> **sogeking99 said:**
> ah, i installed it and had many issues, first off all it had no gui, so i opened it in failsafe  gui and updated the OS(which may i say is much better than windows updater!) and this seems to have fixed everything, *phew*

looking around the software center, so great nearly everything i need seems too be there already.

is there a free book or something to learn bash? i know most about dos, growing up with dos makes bash seem strange too me, but i would love to learn it.

i also need to sort out flash and stuff as youtube doesn't work.

thanks guys

Yes, I forgot to mention that updates could solve some hardware issues also.
Flash is always a problem, there is no good support for it in Linux. Some alternatives are to use Minitube without Flash but I encountered some bugs with this program like seeking, here the [link]("http://www.webupd8.org/2011/02/minitube-14-plays-youtube-videos.html") or use the repos, but this updated package is better.
Or use html5 to watch Youtube videos without Flash within the browser (Chromium does it), but it is a little bit experimental at the moment.

---

### Post by sogeking99 on 2011-02-22
ok thanks. first thing i got was chrome, my favourite browser :)

also, could you tell me how to have a nice temp monitor, and maybe also cpu usage display on the side of my desktop? someone told me to use conky which i have downloaded but i dont know what to do now.

i would like a transparent display, kind of like windows 7 gadgets.

---

### Post by ivanovnegro on 2011-02-22
> **sogeking99 said:**
> ok thanks. first thing i got was chrome, my favourite browser :)

also, could you tell me how to have a nice temp monitor, and maybe also cpu usage display on the side of my desktop? someone told me to use conky which i have downloaded but i dont know what to do now.

i would like a transparent display, kind of like windows 7 gadgets.

First, Im not using Conky nor applets or something similar, but you could go to the appropriate section in the Forums to ask, I know there is a hyper mega thread about Conky, just search it here. This [site]("http://conky-pitstop.wikidot.com/") is also interesting for Conky support.
There are also an amount of applets to use and to display whatever, Im not using such things but search for it again here on the Forums in the right section and Im sure you will get your answers.
On the Gnome panel you can add with a right click also the CPU monitor/system monitor and [here]("https://help.ubuntu.com/community/Applets") the Applet documentation of Ubuntu.

---

### Post by gordintoronto on 2011-02-22
First, install the "ubuntu-restricted" files from Synaptic. Flash should work perfectly.

Then, Google "lm-sensors" or go to the Full Circle Magazine web site and download issue 43, which includes an article on installing lm-sensors.

---

### Post by gordintoronto on 2011-02-22
> **ivanovnegro said:**
> Flash is always a problem, there is no good support for it in Linux.


This is completely untrue. I have used many versions, and Flash has always worked perfectly. After installing Ubuntu, install the "restricted extras."

Or install Linux Mint, which includes flash support "out of the box."

---

### Post by ivanovnegro on 2011-02-22
> **gordintoronto said:**
> This is completely untrue. I have used many versions, and Flash has always worked perfectly. After installing Ubuntu, install the "restricted extras."

Or install Linux Mint, which includes flash support "out of the box."

Perfectly? Im sorry, not for me.
I have Flash installed, what I wanted to say is that it consumes CPU highly and this is a known issue, there are also reported problems with full screen on Maverick, ok, this is an Ubuntu issue. Because of that its not supported perfectly in my opinion, compare it on windows machines. Flash is a buggy thing and I assume the whole world knows that. Of course it works but I try to avoid it. Look the Forums for Flash issues, you will find an amount.

---

### Post by gordintoronto on 2011-02-23
> **ivanovnegro said:**
> Perfectly? Im sorry, not for me.
I have Flash installed, what I wanted to say is that it consumes CPU highly and this is a known issue, there are also reported problems with full screen on Maverick, ok, this is an Ubuntu issue. Because of that its not supported perfectly in my opinion, compare it on windows machines. Flash is a buggy thing and I assume the whole world knows that. Of course it works but I try to avoid it. Look the Forums for Flash issues, you will find an amount.

Sorry to hear you have issues with flash. I run full-screen flash in Maverick, it works perfectly. Perhaps my computer is fast enough that it works. I'm running Ubuntu 10.10 64-bit, have flash 10.2.152.27. I have a nice Nvidia video card.

---

