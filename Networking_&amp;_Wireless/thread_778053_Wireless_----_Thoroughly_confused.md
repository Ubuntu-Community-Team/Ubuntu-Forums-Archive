---
title: "Wireless ---- Thoroughly confused"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by eperrone on 2008-05-01
Help!

Hello all so I got Ubuntu 8.04 installed and I was going to try and get my wireless working on my laptop.  I have a Dell D830 with a Dell 1505 Draft N wireless card.

I have read quite few posts and frankly I am lost.  It seems that I need to use the windows driver and the ndiswrapper?  Howver I could nto see how to install the ndiswrapper itself.  In the help it says that it should be part of the install packages available but I could nbot find there.  then I saw on a differentpost that it was built into this version of Ubuntu and I should use the network manager?  But in network manager I did not see anything about enabling the adapter in fact it was not listed there all I saw a modem and wired ethernet card.  It seems that the documentation is a little scattered.

Can anyone point me in the right direction?

Thanks first experience with Linux and I would really like to get it going!

---

### Post by caljohnsmith on 2008-05-01
It looks like you are going to have to use ndiswrapper, because the bc43-fwcutter software is the only other option, and it doesn't support your chipset BCM4328 (that's the chip on your Dell 1505 Draft N wireless card). The following are my notes on how I installed my own wireless card using ndiswrapper and should work for you. :)

So first off, to make sure you have ndiswrapper installed, you can go to System > Admin > Synaptic Package Manager. Do a search for "ndiswrapper", and make sure it shows you have both "ndiswrapper-common" and "ndiswrapper-utils-1.9" installed (otherwise install them). If you have no internet connection they should be available on your Ubuntu install CD, and you can enable using the install CD by going to System > Admin > Software Sources. 

Next, you need to "blacklist" any existing Broadcom BCM43xx modules from loading so you can use ndiswrapper, so use the following command:
$ sudo bash -c 'echo blacklist bcm43xx >> /etc/modprobe.d/blacklist'

To use ndiswrapper, you must have the Windows (preferably Win XP) wireless drivers for your card; what you are looking for is a *.inf file and a *.sys file. If you don't have them you should be able to download them from the card manufacturer.

Now install the Win XP driver with ndiswrapper (make sure that the directory containing the .inf file also contains the .sys driver file):
$ sudo ndiswrapper -i /location_of_your_wireless_driver/yourdriver.inf  
(FYI, ndiswrapper will install the driver into the /etc/ndiswrapper directory.)
Check to see if driver was installed successfully, i.e. list the installed devices:
$ sudo ndiswrapper -l
If your wireless driver is listed OK, then install the ndiswrapper module (i.e. the ndiswrapper "driver"):
$ sudo modprobe ndiswrapper
Write configuration for modprobe:
$ sudo ndiswrapper -m

Note that file "ndiswrapper" is created in /etc/modprobe.d/ and inside the file it creates an alias for wlan0 that points to ndiswrapper. Also note /etc/modprobe.d/ files are configuration/options files for modules, but the module themselves are not automatically loaded on boot up. To get modules to load and configure on boot up, they must be added to the /etc/modules file. Therefore, to set ndiswrapper to load on startup, the following command adds "ndiswrapper" to the end of the /etc/modules file:
$ sudo bash -c 'echo ndiswrapper >> /etc/modules'

At this point, restart, and you should be able to use network manager (System > Admin > Network) to configure the wireless connection. After configuring it, you may have to do a "sudo ifup wlan0" to actually connect for the very first time. (I'm assuming your wireless connection is wlan0, but in some cases it can be assigned to eth1 or similar. To find out, use "sudo lshw -C network" and look for "logical name" under your wireless card).

Anyway, those are my notes, so hope that works for you! :)

---

### Post by Ayuthia on 2008-05-02
I just want to add one more thing to his notes.  Before you do the modprobe ndiswrapper, you will need to do following:
```
lsmod|greb ssb
```
If you see b43:
```
ssb                    36228  1 b43
pcmcia                 38688  2 b43,ssb

```You will need to do the following:
```
sudo modprobe -r b43
```
If you see b44:
```
sudo modprobe -r b44
```
and finally:
```
sudo modprobe -r ssb
```
It might be possible that you have b43 and b44.  If you have b44, you will need to do the following after modprobe ndiswrapper:
```
sudo modprobe b44
```
The b43 driver is the Linux native Broadcom wireless module and b44 is the Linux native Broadcom wired module.  The ssb module is needed for either one of them to work.  

If you had to do those steps above, you will not really need to do the /etc/modules portion because of my link instructions below.

These steps are now for kernels 2.6.24 (which is what 8.04 is using) and greater.  The steps I provided will help you get started with ndiswrapper.  Once you reboot, the b43/b44/ssb modules will prevent ndiswrapper from working again.  Here is a link to get ndiswrapper working on reboot:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
Go to the Hardy Bug Fix->Making It Permanent->Modifying /etc/modprobe.d/ndiswrapper->Version 0.3.  

The information that caljohnsmith and I provided is quite a bit of information.  What I recommend is that you try to get up to the ndiswrapper -m portion first.  If you run into any problems, just post what steps you have done and we can help you through the rest.

---

### Post by Hatticus on 2008-05-02
> **caljohnsmith said:**
> It looks like you are going to have to use ndiswrapper, because the bc43-fwcutter software is the only other option, and it doesn't support your chipset BCM4328 (that's the chip on your Dell 1505 Draft N wireless card). The following are my notes on how I installed my own wireless card using ndiswrapper and should work for you. :)

**So first off, to make sure you have ndiswrapper installed, you can go to System > Admin > Synaptic Package Manager. Do a search for "ndiswrapper", and make sure it shows you have both "ndiswrapper-common" and "ndiswrapper-utils-1.9" installed (otherwise install them). If you have no internet connection they should be available on your Ubuntu install CD, and you can enable using the install CD by going to System > Admin > Software Sources. **

I'm having a similar issue, but when I tried this (following a How To I found) ndiswrapper did not appear in the Package Manager. Where do I go from here?

---

### Post by Ayuthia on 2008-05-02
> **Hatticus said:**
> I'm having a similar issue, but when I tried this (following a How To I found) ndiswrapper did not appear in the Package Manager. Where do I go from here?By any chance, have you done an update in Synaptic or done 'sudo apt-get update'?  If so, can you post your /etc/apt/sources.list?

---

### Post by Hatticus on 2008-05-02
> **Ayuthia said:**
> By any chance, have you done an update in Synaptic or done 'sudo apt-get update'?  If so, can you post your /etc/apt/sources.list?
I don't think so (I'm a complete Linux noob) I tried 'sudo apt-get install ndiswrapper-common' but it said something like E: cannot find ndiswrapper-common. 

I have not done a full install, Ubuntu is dual booting alongside XP. Am at work at the moment so will post the /etc/apt/sources.list when I get home

---

### Post by Ayuthia on 2008-05-02
You can't just go home "sick"????  Just kidding!

When you get home, try doing
```
sudo apt-get update
```
When you added the CD as a source, the system has not done an update to see what your CD has.

If that doesn't work, then post your /etc/apt/sources.list.  Do you have a wired internet connection in Ubuntu?  If not, then posting this information might not be so fun.  What we are looking for is something like this:
```
deb cdrom:[Kubuntu 8.04 _Hardy Heron_ - Alpha amd64 (20080201)]/ hardy main restricted
```
It won't be exactly like this because I am using Kubuntu and installed mine while Hardy was in the alpha status.

---

### Post by Hatticus on 2008-05-02
> **Ayuthia said:**
> You can't just go home "sick"????  Just kidding!

When you get home, try doing
```
sudo apt-get update
```
When you added the CD as a source, the system has not done an update to see what your CD has.

If that doesn't work, then post your /etc/apt/sources.list.  Do you have a wired internet connection in Ubuntu?  If not, then posting this information might not be so fun.  What we are looking for is something like this:
```
deb cdrom:[Kubuntu 8.04 _Hardy Heron_ - Alpha amd64 (20080201)]/ hardy main restricted
```
It won't be exactly like this because I am using Kubuntu and installed mine while Hardy was in the alpha status.
By CD I assume you mean LiveCD? Will try all this when Im home - yay for being nearly the weekend!

---

### Post by Ayuthia on 2008-05-02
> **Hatticus said:**
> By CD I assume you mean LiveCD? Will try all this when Im home - yay for being nearly the weekend!
Yes, I meant LiveCD.  :)

---

### Post by Hatticus on 2008-05-02
> **Ayuthia said:**
> Yes, I meant LiveCD.  :)
Haha, I thought so, but as this is my first foray into the world of Linux I'm happy to be uber-careful!

---

### Post by caljohnsmith on 2008-05-02
**eperrone:** I just wanted to add that the procedure I gave works great with my wireless card, but my card is using a Libertas chip and not specifically a Broadcom chip like yours. I know other people with other wireless chipset manufacturers who have used the procedure I outlined successfully, so that's why I thought I'd go ahead and reply to your post. But it looks like because you're using the BCM4328 chip you've got some different issues to deal with. I think following Ayuthia's additional advice will be your best bet, or the link Ayuthia originally posted seems like it's helped many in your situation:
[http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003)

Unfortunately there is no panacea when it comes to wireless woes in LinuxLand since it can vary so much from card-to-card, or chipset-to-chipset. I'm sure you can get it working though. :)

---

### Post by Hatticus on 2008-05-02
> **Ayuthia said:**
> By any chance, have you done an update in Synaptic or done 'sudo apt-get update'?  If so, can you post your /etc/apt/sources.list?
Right, tries the sudo apt-get update, but as I have no internet connection (wired) it didnt work.

I did the /etc/apt/sources.list and it said 
bash: /etc/apt/sources.list: Permission denied.

Any other ideas??

---

### Post by eperrone on 2008-05-02
Sorry all,

I was able to get the ndiswrapper installed.  My main source of confusion was that the packages I needed were not in the package manager by default.  And up to this point I had not connected the machine to a network.  Last night I sat down at my router and plugged in and it updated all the packages.  I installed the network manager, device manager and windows wireless drivers tool.  After I did that I got the card to work...  Woo hoo!!!

The key was to get the machine on the internet then I could Get to all the tools I read about (the lack of which was the beginning to all my confusion).  Then after a bit of playing and trial and error I got things going.  

BTW be sure to unplug you wired connection before you try to connect the wireless one!

But....... here is the kicker

The card is slow slow slow.  When I boot the machine in windows I have a good wireless internet connection but in Linux it is barely usable.  I had checked the "rate" setting in iwconfig and it seems ok, 54MB,  I also tried using WEP vs WPA and both of them were the same so it does not seem to be that.  I guess it is the ndiswrapper that makes it slow?

Any ideas!

thanks all!
Eric

---

### Post by Hatticus on 2008-05-02
I managed to get everything working too, so thanks for everyone's help! Managed to install ndiswrapper from the CD and then used ndigtk(?) to install the driver. I also managed to install TrueType fonts myself, which I'm pretty happy with! :):)

---

### Post by caljohnsmith on 2008-05-02
> **eperrone said:**
> 
The card is slow slow slow.  When I boot the machine in windows I have a good wireless internet connection but in Linux it is barely usable.  I had checked the "rate" setting in iwconfig and it seems ok, 54MB,  I also tried using WEP vs WPA and both of them were the same so it does not seem to be that.  I guess it is the ndiswrapper that makes it slow?

Any ideas!

thanks all!
Eric
Ndiswrapper should not be the cause of a really slow internet connection. If it's still really slow, post the full results of "ifconfig" and "iwconfig" and maybe I or someone else can help. Also, what is your internet connection? Are you using a DSL modem along with your router, or are you using cable?

---

### Post by eperrone on 2008-05-02
Hello all,

As requested here is results from the configs...  anyone see anything why it would be so slow?  BTW I am currently sitting downstairs form the router.  So the speed looks slower today than yesterday (Bit Rate=24Mb/s) But yesterday when I was sitting 1 foot away from the router the performance was the same and the signal was 100%  so I think that is not the problem.  Also I sit on my couch regularly with WinXP and it works great from here.  Anyway willing to try anything...

My internet connection is DSL the highest speed from BellSouth.


Thanks

From iwconfig


wlan0     IEEE 802.11g  ESSID:"xxxxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:47:41:D8   
          Bit Rate=24 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


From if config

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:c0:a2:d0  
          inet addr:192.168.1.106  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fec0:a2d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1205337 (1.1 MB)  TX bytes:174634 (170.5 KB)
          Interrupt:17 Memory:f9ffc000-fa000000

---

### Post by eperrone on 2008-05-03
So I tried to run a few speed tests on the internet connection.  Just to see what is up.

This first test isis using wireless from my laptop when booted into Windows XP.  

As you can see my download speed is close to 6000
[IMG]http://www.dslreports.com/im/50240407/8423.png[/IMG]

This second test is from the same laptop booted into Ubuntu 8.04 using a wireless connection a few minutes later.


[IMG]http://www.dslreports.com/im/50241544/9422.png[/IMG]

Here are the results in Ubuntu with a Wired Connection

[IMG]http://www.dslreports.com/im/50244023/1333.png[/IMG]


What is pretty amazing is that the download speed is slower than upload!  I figure that must be some type of configuration problem.  Maybe?

Weird.

As always any suggestions appreciated!

---

