---
title: "[SOLVED] Intel DG45ID NIC Driver Support"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by Junkieman on 2008-09-10
hi all you Ubuntu lovers

i have a new pc, for the first time in years! im so excite! however im having an issue with the network card... i have searched the forums, and the tips section too. 

the problem: i installed Hardy 8.04, the nic did not pick up in the Live environment, or post-install. lspci shows the ethernet controller as an unknown device.

the details: i can elimiate faulty hardware, as the system had a trial edition of vista home prem and was working. it is an Intel chipset DG45ID [(Product Page)]("http://www.intel.com/cd/products/services/emea/eng/motherboards/392471.htm"). luckily Intel has great driver support, and the linux drivers are on the CD.

using ethtool, i discovered i need to use the e1000e driver. it seems to compile fine (as superuser), however the last message output is "cannot write to /var/cache/man/cat7/e1000e.7.gz in catman mode".

i proceeded with mobprobe and insmod, but get a "File exists" message. I did try remove an old version of the driver using rmmod, but i see the install script already does this anyway.

so... can anyone suggest anything? im very capable with the console, but never having done this before im just stuck as what to do next.

attached are the outputs from the console. any tips would be great, thanks in advance!


Intel Desktop Board DG45ID: [http://www.intel.com/cd/products/services/emea/eng/motherboards/392471.htm](http://www.intel.com/cd/products/services/emea/eng/motherboards/392471.htm)

---

### Post by josephhitt on 2008-09-11
I have the same board and also need to get the nic working.  

It's been a bit of an adventure with the DG45ID (although not my worst experience with new hardware, certainly not the best).  First I had to take back a power supply before realizing the board draws so little current it won't start unless you attach drives and other devices (probably more of a power supply issue though).  Not really cool if you wanted to create a diskless meda server.

Secondly, I usually run ubuntu but ubuntu could not see the sata dvd-rw after you pick the keyboard type during the install.  It could not find media or mount the cdrom even though it initally read from the disk .. it dumped me out to busybox.  Same with gentoo, so I tried fedora and it worked fine.  I think it was because fedora image was on a DVD instead of a CD so I may try the other distros (ubuntu) on a DVD later.

In addition, I'm a little ticked that the onboard "raid" is not real hardware raid but a pseudo "win-raid" that only works in windoze (did not say that on the box!)  anyway I'm using software raid which works better for me anyway b/c I can use other partitions for manual backups.

Now I'm at the same place as you - no network...(but, as in your case it works fine in Windoze).  Where did you get the linux driver from?

Anyway, that's what I get for buying stuff without checking HCL, har har.  But like I said the only issue right now is network under linux so if I can get that working I'll be pretty happy with the purchase.

will post back again later...

---

### Post by Junkieman on 2008-09-11
> **josephhitt said:**
> Now I'm at the same place as you - no network...(but, as in your case it works fine in Windoze).  Where did you get the linux driver from?

the included readme mentions that driver updates are found at [http://www.sf.net/projects/e1000](http://www.sf.net/projects/e1000)

initially it also dumped me into a very limited shell because it didnt pick up my SATA2 drives, [this post]("http://ubuntuforums.org/showthread.php?t=899901") solved that problem.

i would like to try the other drivers (e1000 & igb) but wont be able to do so today.

---

### Post by Junkieman on 2008-09-11
Solved!

it would've worked the first time if only i had the latest rivers ;)

Go to [http://sourceforge.net/projects/e1000](http://sourceforge.net/projects/e1000) and download the e1000e drivers, these are for the DG45ID board. i used a usb disk to transfer to the ubuntu machine.

follow these instructions as found with the drivers (modified for simplicity)

open a new terminal window, and enter superuser mode:
```
sudo -s
```
then cd to /tmp...

```

1. Copy the base driver tar file to /tmp

2. Untar/unzip archive:

     tar zxf e1000e-x.x.x.tar.gz

3. Change to the driver src directory:

     cd /tmp/e1000e-x.x.x/src/

4. Compile the driver module:

     make install

   The binary will be installed as:

     /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000e/e1000e.[k]o

```

NOTE: i did not even need to perform step 5, when i do i get a message "the file already exists", the install script obviously does this step for us. I just included it for completeness. 

After this point i just rebooted the machine, and when it came back up the card was functional, dhcp even gave it an ip... :)

```

5. Load the module using either the insmod or modprobe command:

     modprobe e1000e

     insmod e1000e

```

Good luck!

---

### Post by josephhitt on 2008-09-11
awesome, I downloaded the tarball, will try it tonight... thanks for the tip on ahci also.

For me it complained about not having kernel headers so as a temporary solution I just cheated and tossed my 3c905 card into the PCI slot so I could get on the net (yeah... i know, that takes all the fun out of it).  Gotta love 3c905 cards, they ALWAYS work.  But no point taking up a PCI slot since the board is pretty limited on those, so will get e1000e going tonight.

... next thing to try is the restricted nvidia video drivers.  DG45ID actually has decent onboard video, a lot of people are using this board for building home theater servers.

---

### Post by SDNick484 on 2008-09-11
I installed Gentoo on this board last night, and man it's a pain at the moment.  I know this is an Ubuntu forum, but maybe I can help.  The driver for the NIC is definitely the e1000e.  The problem is, you need a very recent kernel (ie. 2.6.25 or later) for it to work.  To make matters worst, there's a e1000e driver in 2.6.24, but it doesn't work with the card.  The board uses a 82567LF-2 (verify with lspci), and the kernel patch that added it is [here]("http://www.linuxhq.com/kernel/v2.6/26/drivers/net/e1000e/ich8lan.c").  

The issue for Gentoo was the latest release, 2008.0-r1, uses a 2.6.24 kernel so I couldn't get networking working for the install. I worked around it by installing without networking, then downloading the latest gentoo-sources kernel (& required patches) on another machine, moving it over via USB, and building the new kernel.  After booting to the 2.6.26.1 kernel, eth0 shows up after modprobing e1000e.

For Ubuntu 8.04, you need to either compile the driver outside of the kernel, compile a 2.6.25 or newer kernel yourself, or use an Intrepid Ibex kernel.  

The other issue, which I see already mentioned, is that you need ahci for SATA to show up.  That's simple enough to enable in BIOS.  Please note however that if you installed Windows XP using IDE, then switch to ahci, your Windows will fail to boot.  If you used ahci at the time of Windows XP's install by passing the driver (via F6), then you should be alright.  I did find a work around though to convert windows from IDE to AHCI without having to re-install.  If anyone needs it, I'll post (not sure if it works on Vista, but XP Pro is confirmed).

---

### Post by josephhitt on 2008-09-11
Another DG45ID bretheren joins the fray!

Yep, I installed Windowz while set to IDE but I'll just reinstall it.  I thought that was the case, thanks for confirming.

---

### Post by SDNick484 on 2008-09-11
To fix XP without doing a re-install, follow the instructions posted [here]("http://forums.pcper.com/showthread.php?t=444831").

You need a different registry entry however, which I'll try and post when I get home.  I used the iata85enu.exe and it all worked fine.  I created the my registry entry by running lspci -nv and swapping the values in bold (see post 128 of the linked thread) with the values of the registry entry posted on post 1.  Once that was done, it booted fine.

---

### Post by Junkieman on 2008-09-12
After getting the NIC working the system did an update, and that killed the driver :p reinstalling using the directions above fixed it, again. I wouldn't like to recompile the drivers each time a system update replaces the driver, would anyone know how to persist this? I'll mark this thread as solved once we find this answer.

Now we need to sort the graphics drivers, but thats for another thread...

---

### Post by SDNick484 on 2008-09-12
My registry entry for DG45HD to get ahci working in Windows XP after XP was set up via IDE is:
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\CriticalDeviceDatabase\pci#ven_8086&dev_3a22&cc_0106]
"Service"="iaStor"
"ClassGUID"="{4D36E96A-E325-11CE-BFC1-08002BE10318}"

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\iaStor]
"Type"=dword:00000001
"Start"=dword:00000000
"Group"="SCSI miniport"
"ErrorControl"=dword:00000001
"ImagePath"="system32\\drivers\\iaStor.sys"
"tag"=dword:00000019
"DisplayName"="Intel AHCI Controller"

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\iaStor\Parameters]
"queuePriorityEnable"=dword:00000000

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\iaStor\Enum]
"0"="PCI\\VEN_8086&DEV_3A22&SUBSYS_50028086&REV_02\\3&13c0b0c5&0&FA"
"Count"=dword:00000001
"NextInstance"=dword:00000001

```

What issues are you having with the video driver in Ubuntu, it works fine in Gentoo.  Are you just referring to 3D acceleration?

---

### Post by Junkieman on 2008-09-15
> **SDNick484 said:**
> What issues are you having with the video driver in Ubuntu, it works fine in Gentoo.  Are you just referring to 3D acceleration?

well im referring to the gfx drivers in general as im running 800x600, and yes 3D acceleration too :) i explain in detail in [this post]("http://ubuntuforums.org/showthread.php?p=5792422#post5792422").

---

