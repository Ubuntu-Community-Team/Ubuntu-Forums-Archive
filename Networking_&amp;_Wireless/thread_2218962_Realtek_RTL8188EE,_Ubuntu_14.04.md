---
title: "Realtek RTL8188EE, Ubuntu 14.04"
date: 2014-04-22
forum: Networking &amp; Wireless
---

### Post by claudiorv89 on 2014-04-22
Hi! I have a new HP Pavilion 15-006ss with Windows 8, and, now, with Ubuntu 14.04 64 bits. I have the Realtek 8188EE. Internet with Windows 8 works perfectly, but Ubuntu... It´s works very bad. I read here that using Ubuntu 12.04 there isnt problems. Is the better solution? Ubuntu 12:04 64? Thanks.

---

### Post by SLaCK3r on 2014-04-22
I am NOT an expert. I just want to share with you my discovery.

I have an HP Envy 15TS with an RTL8188EE wireless card. I had the exact same problem with 14.04. After lots of screwing around, I couldn't fix the spotty connection and slow internet, so I downgraded to 12.04LTS and it works flawlessly! 

Just something to keep in mind:)

I'll be following this thread to see if you get any resolution!

---

### Post by claudiorv89 on 2014-04-22
Perfect! I go to try with 12.04 64 then. If I found something I'll post it, but I don't know if is posible XD Thanks!

---

### Post by claudiorv89 on 2014-04-23
I'm ready to install Ubuntu 12.04 64 bits, but I have two questions.  Can we have a good performance with ubuntu12? Isnt better 14? And...  when/how can we know is the problem resolved in Ubuntu 14, if we can.  Thanks you a lot!

---

### Post by jdhamric on 2014-04-28
I've had a similar problem with my Toshiba C55t-A5314 with the RTL8188EE wirless adapter. With Ubuntu 14.04 3.13 kernel I get no wireless connection even though my network can be seen. A connection keeps trying to be made with no success. Booting with the 3.11 kernel I can connect, so that's what I currently do. In either case the network manager indicator is missing in the panel. I've read that manually installing the 3.14 kernel may solve the issue, but I don't know if I fell comfortabledoing that.

If someone else has an idea, I'm willing to listen. I was really hoping that 14.04 was going to be more stable and smoother.

---

### Post by SLaCK3r on 2014-04-28
> **jdhamric said:**
> I've had a similar problem with my Toshiba C55t-A5314 with the RTL8188EE wirless adapter. With Ubuntu 14.04 3.13 kernel I get no wireless connection even though my network can be seen. A connection keeps trying to be made with no success. Booting with the 3.11 kernel I can connect, so that's what I currently do. In either case the network manager indicator is missing in the panel. I've read that manually installing the 3.14 kernel may solve the issue, but I don't know if I fell comfortabledoing that.

If someone else has an idea, I'm willing to listen. I was really hoping that 14.04 was going to be more stable and smoother.

Manually installing the 13.14.1 kernel si very easy. You just download 3 .deb files and click to install them, then after they are installed you restart your laptop.

---

### Post by insane9 on 2014-04-28
I've got the same issue with a HP laptop using the Realtek RTL8188EE chip. Internet is SLOW...I'm on a 60mb/s line and on Speedtest.net, i'm getting 4mb/s. When I boot into my Windows 8.1 partition (on same laptop) I get the full 60mb/s. I have a love/hate relationship with Linux. I always get driver issues like this and it stops me from making the switch from Windows to Linux for good. 

I'm going to try install the 3.14 kernel now. If it doesn't work i'll have to downgrade to 12.04 LTS as well.

EDIT: Just installed the 3.14 kernel and it seems to have done the trick... My wireless was working but VERY slow before installing the kernel. It's now much faster. Here are the instructions I used:

**[B][COLOR=#000000][SIZE=2][FONT=arial]Installation [/FONT][/SIZE][/COLOR][COLOR=#000000][FONT=arial]For 32-Bit Systems[/FONT][/COLOR]**
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[/B][COLOR=#000000][SIZE=2][FONT=arial]Download the .debpackages by firing up the terminal and copying and pasting the commands below.. (wait for each .deb file to download before
[/FONT][/SIZE][/COLOR]moving onto the next one)[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]$ wgetkernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-headers-3.14.0-031400_3.14.0-031400.201403310035_all.deb[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]$ wgetkernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-headers-3.14.0-031400-generic_3.14.0-031400.201403310035_i386.deb[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]$ wgetkernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-image-3.14.0-031400-generic_3.14.0-031400.201403310035_i386.deb[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]Install them.[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]$ sudo dpkg -ilinux-headers-3.14*.deb linux-image-3.14*.deb[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]Reboot the system.[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]sudo reboot

[/FONT][/SIZE][/COLOR][B]
**[COLOR=#000000][SIZE=2][FONT=arial]Installation For 64-Bit Systems[/FONT][/SIZE][/COLOR]**
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[/B][COLOR=#000000][SIZE=2][FONT=arial]Download the .debpackages by firing up the terminal and copying and pasting the commands below.. (wait for each .deb file to download before
[/FONT][/SIZE][/COLOR]moving onto the next one)
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]$ wgetkernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-headers-3.14.0-031400_3.14.0-031400.201403310035_all.deb[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]$ wgetkernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-headers-3.14.0-031400-generic_3.14.0-031400.201403310035_amd64.deb[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]$ wgetkernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-image-3.14.0-031400-generic_3.14.0-031400.201403310035_amd64.deb[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]Install them.[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]$ sudo dpkg -ilinux-headers-3.14*.deb linux-image-3.14*.deb[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]Reboot the system.[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]sudo reboot[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]To uninstall,[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]
[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]sudo apt-get removelinux-headers-3.14* linux-image-3.14*

[/FONT][/SIZE][/COLOR]
[COLOR=#000000][SIZE=2][FONT=arial]source:[http://www.yourownlinux.com/2014/04/install-upgrade-to-linux-kernel-3-14-in-linux.html](http://www.yourownlinux.com/2014/04/install-upgrade-to-linux-kernel-3-14-in-linux.html)[/FONT][/SIZE][/COLOR]

---

### Post by basgoossen on 2014-04-29
I updated to kernel 3.14 when the WiFi card works it now seems a faster (download of 2mB/s instead of 400kb/s). however the card is still unstable, it works a while than it does not, then it works again and then not again... so not very reliable. Pings to the local IP always succeed of course, but pings to the router stop from time to time with breaks of over a few minutes. Is there anybody who has another solution?

---

### Post by insane9 on 2014-04-29
basgoossen - I've had the same issue. It was faster, but still VERY unstable. My most recent 'fix' is to change the channel setting on your router. Mine was set to 'auto' - I've now changed it to '2 + 6' (Virgin Media, UK) and it seems fine now. Perhaps this is an issue with both driver and channel? I'll keep you posted on how stable it is for me.

---

### Post by SLaCK3r on 2014-04-29
My network is WPA/WPA2, EAP-PEAP, MSCHAPV2 and I don't lose connection. Sometimes the connectivity drops to 1 bar, but in seconds it goes back to 4 bars and I don't lose connection.

---

### Post by jdhamric on 2014-04-30
I took the plunge and installed the 3.14.1 kernel. The good news--I could get a connection. the bad news--very unstable. It keeps cutting out. I just  followed the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=2219952](http://ubuntuforums.org/showthread.php?t=2219952)

and so far everything looks great!

Keeping my fingers crossed.

---

### Post by tmNihonsuki on 2014-05-14
> **SLaCK3r said:**
> Manually installing the 13.14.1 kernel si very easy. You just download 3 .deb files and click to install them, then after they are installed you restart your laptop.

[SIZE=3][FONT=arial]A word of caution for any who are contemplating this from one who has tried it. I have an HP Pavilion 17 with Hybrid graphics on the proprietary ATI/AMD driver. After installing the 13.14.1 kernel I could not boot into graphics mode until I removed the proprietary flgrx driver. Nor could I remove the kernel and downgrade. I had previously applied the drivers for the RTL8188EE/CE, but whilst that had worked fine at home it did not work so well at my workplace. Just my 2p worth.

Further to this - the wireless access points at home and work seem in all ways similar except that at home the authentication is WPA2 and at work WPA.  Could this be the problem?  As for installing the RTL8188EE/CE, here it can be done thus:
[/FONT][COLOR=#BEBEBE][FONT=Ubuntu Mono]
[/FONT][/COLOR][/SIZE][FONT=fixedsys][SIZE=3]1.) sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git[/SIZE][/FONT]
[FONT=fixedsys][SIZE=3]2.) git clone [https://github.com/FreedomBen/rtl8188ce-linux-driver](https://github.com/FreedomBen/rtl8188ce-linux-driver)[/SIZE][/FONT]
[FONT=fixedsys][SIZE=3]3.) cd rtl8188ce-linux-driver[/SIZE][/FONT]
[FONT=fixedsys][SIZE=3]4.) sudo make[/SIZE][/FONT]
[FONT=fixedsys][SIZE=3]5.) sudo make install[/SIZE][/FONT]
[SIZE=3][FONT=fixedsys]6.) sudo cp -r firmware/* /lib/firmware[/FONT]

to be repeated after every kernel upgrade, it seems.[/SIZE]

---

### Post by modrobert on 2014-05-19
Another word of caution if you are thinking about installing the 3.14.1 kernel on a HP Pavilion 17 (e110so) laptop which includes the Seagate/Samsung ST1000LM024 HN-M101MBB (2BA30001) hard drive (1TB). I suspect due to a bad [libata patch]("http://comments.gmane.org/gmane.linux.kernel/1662676") in this kernel which enables "ATA_HORKAGE_BROKEN_FPDMA_AA" quirk for this specific hard drive (and firmware) you will get read errors (bad sectors) on the drive eventually, also reported as bad in "Current Pending Sector Count" in the SMART data. 

First I thought the hard drive was going bad, but when booting an older kernel (Knoppix) from removable media and fixing the partition with 'fsck' I couldn't reproduce any more errors, even after days of stress testing the hard drive by running three concurrent scripts which wrote, read and deleted 100gb files in parallel on the drive with ext4 file system. Also, after writing to the bad sectors, they disappeared from the SMART data, both pending and uncorrectable sectors were back to zero.

A fix that worked for me was to revert back to the default 3.13.0 kernel for Ubuntu 14.04, and adding this kernel parameter for the hard drive problems: 

libata.force=1:3.0G,1:noncq

(Note that this parameter did not fix the creeping bad sector problem when booting with the 3.14.1 kernel.)

I also had to compile the RTL8188EE driver from source as tmNihonsuki mentioned in previous post to get the Wifi running OK on kernel 3.13.0.

---

### Post by owenll on 2014-05-24
I suffered with no wifi / bad wifi until I installed the 3.14.1 kernel. Works well now. Radical surgery, but well worth it.

---

