---
title: "Broadcom Wireless card with Ubuntu 6.10"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by bmralex on 2006-12-24
Hello
I have 3 y.o Dell Latitude D600 laptop with built-in Truemobile 1400 802.11a/b.g card, which I am trying to make working under Ubuntu 6.10.
Although I have windows driver and followed the instructions posted at 
[http://www.ubuntuforums.org/showthread.php?t=185174&highlight=ipv6+routers](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=ipv6+routers)
and 
[http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/](http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/)
nothing is working.

The output of  command
lspci | grep Broadcom\ Corporation

shows:
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 02)

Please help!
Thank you!!!

---

### Post by cilynx on 2006-12-24
When following the first tutorial (bcm43xx-fwcutter as opposed to ndiswrapper), how does in "not work"?

---

### Post by bmralex on 2006-12-24
As stated in the paragraph 7 of that link ([http://www.ubuntuforums.org/showthread.php?t=185174&highlight=ipv6+routers](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=ipv6+routers))
after the reboot  I expected to see the wireless bar symbol in the upper right corner of the screen. The symbol did not appear.
I enabled  the Wireless Connection under System>>Administration>>Networking, but it did not help. Only wired connection is working.
What shall I do next?

---

### Post by cilynx on 2006-12-24
Alrighty.  Unfortunately, Broadcom often requires setup on the console...

Can you give me the output of:
```
iwconfig ; lsmod |grep bcm43xx ; lsmod |grep -i ndis
```
I'm checking for wireless tools and the wireless interface
Checking if the bcm43xx module is loading
Checking if ndiswrapper is getting in the way

We'll go from there --

---

### Post by bmralex on 2006-12-24
Thank you for the prompt reply.
The output of the command is below:


bmralex@bmralex-laptop:~$ iwconfig ; lsmod |grep bcm43xx ; lsmod |grep -i ndis
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11a/b/  ESSID:"IETWireless"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

bcm43xx               127252  0 
ieee80211softmac       33792  1 bcm43xx
ieee80211              35272  2 bcm43xx,ieee80211softmac


Thank you!

---

### Post by bmralex on 2006-12-24
Thank you Cilynx for your help.
I finally have my latitude D600 runing Ubuntu 6.10 to work with Truemobile 1400 (BCM4309 chipset) wireless card.
Here is what I  did:

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper

Ubuntu 6.10 requers ndiswrapper-1.8, which I  downloaded from 
[http://sourceforge.net/project/downloading.php?groupname=ndiswrapper&filename=ndiswrapper-1.8.tar.gz&use_mirror=superb-east](http://sourceforge.net/project/downloading.php?groupname=ndiswrapper&filename=ndiswrapper-1.8.tar.gz&use_mirror=superb-east)
Then followed the installation installation instructions specified in INSTALL

Downloaded the windows driver for Truemobile 1400  from
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R94827&formatcnt=1&libid=0&fileid=122975](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R94827&formatcnt=1&libid=0&fileid=122975)

sudo ndiswrapper -i /home/bmralex/Desktop/R94827/bcmwl5.inf
sudo ndiswrapper -m
sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
sudo modprobe ndiswrapper

Rebooted, and selected wlan0 at wireless connection.
IT FINALLY WORKED!!!!

Good luck

---

### Post by cilynx on 2006-12-24
Glad you got it going.  I need to compile a list of versions that things work on.  I guess I was lucky.  I got bcm43xx-fwcutter working on Dapper and it has lived just fine through upgrades all the way to Feisty.  No matter.  So long as you've got it working, we've got another success story --

---

### Post by gb5757870 on 2006-12-25
Hi,

*bmralex*, it's quite possible that I will name my first child after you. I have battled for months to get wireless working and with your instructions (and a few other bits and pieces for a newbie like me to figure out), it works. Writing this using wireless

Cheers
G

---

### Post by bmralex on 2006-12-29
Hello  gb5757870 
Thank you for your kind words.
I am glad it helped!
Happy New Year and Good luck

---

### Post by gb5757870 on 2007-02-11
Well, well, well. After updating the kernel to 2.6.17-11, my wireless card can no longer see my wireless network.

This was first evident when I couldn't see my network through KNetWorkManager but then ran iwconfig just to be sure and sure enough, no wireless networks detected.

I booted back into the 2.6.17-10 kernel and (whew) I'm writing this after connecting as before. Bugger. Has anyone else experienced the same problem?

cheers

G

---

### Post by c00ch on 2007-02-11
@gb5757870

Yup. Same problem here. Upgrade to kernel 17-11 and - bang! I suspect it's got something to do with ndiswrapper (i.e. needs to be compiled for the kernel it's working on). :(

---

### Post by c00ch on 2007-02-11
I was right.

After the kernel update (2.6.17-10 > 2.6.17-11) my wlan connection gave up on me. It would work under 17-10. Fixing that is relatively easy (although bloody annoying). Here's what's worked for me:

1. Download nidswrapper [http://sourceforge.net/projects/ndiswrapper/]("http://sourceforge.net/projects/ndiswrapper/")
(Follow the [installation instructions]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Compile_and_install") to compile and install for the new kernel)

2. either follow bmralex instructions above to install your driver - or if the driver's there already (e.g. was working in 2.6.17-10) just run

```
sudo modprobe ndiswrapper
```

3. reboot and your wireless should be back up (you might have to enable and set it up again in System > Administration > Networking)

Hope that helps.

---

### Post by gb5757870 on 2007-02-11
cheers mate, will give it a crack and post my results

---

### Post by glendavee on 2007-02-11
I've just had exactly the same problem. Rebooting in 2.6.17.10 brings things back to normal.
I've been told I need to re-install the driver under 2.6.17.11, but don't know if I want to take the risk.

---

### Post by glendavee on 2007-02-11
Further to the above post, in 2.6.17.11, ndiswrapper -l shows the driver present and correct ie
rt73 : driver installed
        device (050D:905B) present

modprobe ndiswrapper gives  a Fatal error message

---

### Post by c00ch on 2007-02-11
@glendavee

Re-compiling ndiswrapper from source (see my post above) solved that problem for me.

---

### Post by gb5757870 on 2007-02-12
c00ch, thanks heaps for the instructions, recompiling with new kernel (as per your instructions above) fixed it.

G

---

### Post by glendavee on 2007-02-20
Thanks for the suggestion. I've been away for a week, but installing ndiswrapper, then reinstalling the latest (1.37) has fixed problem. Yipee

---

