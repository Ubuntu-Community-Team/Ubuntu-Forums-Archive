---
title: "[SOLVED] HP dv2815nr wireless no worky on hardy"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by yebo29 on 2008-05-11
I've searched the forums and can't seem to find someone with my same exact issue:

1) Whether wireless kill switch is on or off, light does not turn on (indicating wireless card is on)
2) I have tried installing/uninstalling/re-installing b43-fwcutter package and rebooting, but still no broadcom restricted driver shows up - this is making me think I **don't** have a broadcom wireless card (making me even more clueless!)
3) I have attempted ndiswrapper to no success... but maybe I'm just doing something wrong!!!

The following is the output of lshw -C network, ndiswrapper -v, ndiswrapper -l:

**ndiswrapper -v:**
ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload 586 

**ndiswrapper -l:**
 ndiswrapper -l
bcmwl6 : driver installed
	device (14E4:4315) present


**lshw -C network:**
*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:51:9e:5c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.30 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0


**iwconfig:**
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



As you can obviously see, iwconfig sees no wireless!! :(


Please help!!

Thank you

---

### Post by dmizer on 2008-05-12
yes, you DO have a broadcom wireless card.

you appear to be attempting to use the bcmwl6 driver built for windows vista.  this driver will not work in ubuntu.  you will have to use the xp driver bcmwl5

more information here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by yebo29 on 2008-05-12
Thanks for the info... let me try it out.

---

### Post by yebo29 on 2008-05-17
OK. Tried it: unfortunately doesn't work. I even installed ndisgtk (Gui frontend) and it sais the driver was installed but there is no hardware present.

I've restarted several times with and without the radio kill switch on, with cable unplugged, checked the BIOS..... This is ridiculous.

I have noticed one thing, though. In Windows (where the wireless works.. go figure), when I flick the wireless switch on, the wireless light changes from amber to blue (obviously indicating it is on). In Ubuntu, the light stays amber no matter what. Dmesg doesn't seem to show much, either It's a brand-spankin' new laptop, too, so it can't be faulty hardware...... is it???

HELP!!!!!!!!

---

### Post by Ayuthia on 2008-05-17
> **yebo29 said:**
> OK. Tried it: unfortunately doesn't work. I even installed ndisgtk (Gui frontend) and it sais the driver was installed but there is no hardware present.

I've restarted several times with and without the radio kill switch on, with cable unplugged, checked the BIOS..... This is ridiculous.

I have noticed one thing, though. In Windows (where the wireless works.. go figure), when I flick the wireless switch on, the wireless light changes from amber to blue (obviously indicating it is on). In Ubuntu, the light stays amber no matter what. Dmesg doesn't seem to show much, either It's a brand-spankin' new laptop, too, so it can't be faulty hardware...... is it???

HELP!!!!!!!!
If it is working in Windows, then the hardware is not faulty.  When it says that there is no hardware present, it doesn't like something about your driver.  I am not for sure about what driver you are using, but you could try this [link]("http://ubuntuforums.org/showthread.php?t=786397").  Try the driver that he lists in step 0.  If it does not cause your wireless to work, do step 2.

---

### Post by yebo29 on 2008-05-19
holey.... it worked!!! all I ahd to do is follow step 2 (the hack). Create a link and reboot. I do admit that the first night I had trouble connecting. But I think that's more my wireless router than the laptop.

It's working now (I'm writing this wirelessly).. Thank you very much for your help. Hope this post also helps others!

---

### Post by dmizer on 2008-05-20
> **yebo29 said:**
> holey.... it worked!!! all I ahd to do is follow step 2 (the hack). Create a link and reboot. I do admit that the first night I had trouble connecting. But I think that's more my wireless router than the laptop.

It's working now (I'm writing this wirelessly).. Thank you very much for your help. Hope this post also helps others!

that's fantastic.  i wasn't aware that you were still requiring help, or i would have looked for more solutions for you.

anyway, use the "thread tools" drop down and mark this post as solved so other people know that there is a solution here! :)

---

