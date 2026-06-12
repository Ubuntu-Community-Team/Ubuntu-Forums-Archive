---
title: "Network problems!!"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by lover_of_sc on 2009-08-25
I had a big problem last night trying to install the network adaptor on my new Sony vaio W netbook, see tread 

[http://ubuntuforums.org/showthread.php?t=1248982](http://ubuntuforums.org/showthread.php?t=1248982)

I managed to get it working by installing linux backports modules but after I did a system update and rebooted the PC it all went back to square 1 again?!? I tried to reinstall the same packages as yesterday but it does not work...

Can someone please share some light over this wierd problem?

---

### Post by nhasian on 2009-08-25
you didnt mention what version of ubuntu you were using... 32 or 64 bit?  8.10, 9.04, karmic alpha?  

also this will tell us what network adaptor you have:

```
lshw -C network
```

---

### Post by lover_of_sc on 2009-08-25
Thank you for the quick reply, I have a 32-bit system, here is the information:

anders@anders-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c2:2c:4d:66:ad:74
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
anders@anders-laptop:~$

---

### Post by dk06 on 2009-08-25
Not sure what happened when you restarted but if you don't feel like troubleshooting it, you can try this:
[COLOR=Black]Download the correct wifi driver from the Sony site (drivers & support section)
inside the wifi .exe (extract it)[/COLOR]
[COLOR=Black]
Open your terminal and paste this in:
[/COLOR][COLOR=Black]```

sudo apt-get install ndisgtk

```[/COLOR][COLOR=Black]
**Ndisgtk** will be under your programsand is called[COLOR=Black][I] "Windows Wireless Drivers"
[/I]It will ask you to browse to the driver.[/COLOR][/COLOR][COLOR=Black]
 [/COLOR]then add the *whatever*[COLOR=Red]**.inf **[/COLOR][COLOR=Black]from the driver package you downloaded.[/COLOR]

---

### Post by lover_of_sc on 2009-08-25
I have got the ndisgkt installed but I cant for the love of my life find the inf file for the stupid network card anywhere... That being AR9285 Wireless network adaptor

---

### Post by lover_of_sc on 2009-08-25
Seems like more people have simular problems....

[http://www.uluga.ubuntuforums.org/showthread.php?p=7635367](http://www.uluga.ubuntuforums.org/showthread.php?p=7635367)

Plz help someone...

---

### Post by dk06 on 2009-08-27
Had trouble extracting the one I downloaded from the Sony site

Found this info:
__________________________________________________________________
[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)
[http://www.atheros.cz/inffile.php?inf=62&bit=32&atheros=AR9285&system=2](http://www.atheros.cz/inffile.php?inf=62&bit=32&atheros=AR9285&system=2)
[http://www.atheros.cz/download.php?atheros=AR9285&system=2](http://www.atheros.cz/download.php?atheros=AR9285&system=2)
______________________________________________________________

and I think the attached zipped package should have the correct .inf file
here is where I got it:
[http://www.nodevice.com/driver/AR9285/get64221.html](http://www.nodevice.com/driver/AR9285/get64221.html)

I just did a google search for it and don't know anything about site I downloaded it from so you are welcome to try it out but do it at your own risk.
If you want to check out the site for yourself, here it is:
[http://www.nodevice.com/driver/AR9285/get64221.html](http://www.nodevice.com/driver/AR9285/get64221.html)

edit:
I had to split it half to upload it

---

### Post by nothingspecial on 2009-08-27
Simple if improper fix.

Something about the new kernel has broke atheros wireless.

Restart and when the message about grub loading comes up press escape and boot into the previous kernel (3rd option)

---

### Post by lover_of_sc on 2009-08-27
Thank you ever so much guys! Got it running properly yesterday but reinstalling a clean 9.04 ubuntu, then I installed linux-backports-modules-2.6.28-13-generic_2.6.28-13.14_i386 and rebooted the computer, this got the network going. When I update the kernel to a newer version it disables it again. I have now locked in the old kernel version until the bug has been rectified. 

Ther network is ok now but slightly unstable...

---

### Post by dearingj on 2009-08-27
> **lover_of_sc said:**
> Thank you ever so much guys! Got it running properly yesterday but reinstalling a clean 9.04 ubuntu, then I installed linux-backports-modules-2.6.28-13-generic_2.6.28-13.14_i386 and rebooted the computer, this got the network going. When I update the kernel to a newer version it disables it again. I have now locked in the old kernel version until the bug has been rectified.

Did you try installing the package 'linux-backports-modules-jaunty'? That ensures that every time a kernel update is released, you also get the corresponding update of linux-backports-modules-2.6.28-whatever.

---

### Post by lover_of_sc on 2009-08-27
Yes I have tried nearly everything and read so many different forums etc, it appears to be a recognised problem and I am hoping for a new release/bug fix shortly. :-)

---

