---
title: "HOWTO: Install Belkin F5D7010 with pci id 1799:701f on fiesty"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by trainpic on 2007-07-01
This is for the realtek chipset, where the drivers on the CD are blkwgn7.inf, etc.
Belkin changes the chipset for this card (the F5D7010) with each version that they release. Therefore, this HOWTO is only expected to work with version 7 of the card. It was very difficult to identify the chipset. I checked the ndiswrapper.org database to determine my chipset. Other chipsets that have been used for different versions of this card include Atheros and BCM4306.

Install ndiswrapper-utils.
For versions earlier than Gutsy:
```
sudo apt-get install ndiswrapper-utils
```
For Gutsy and later:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```
Download the realtek drivers from [here]("ftp://202.65.194.212/cn/wlan/x86-8185(1094).zip") (This link is copied directly from the realtek.com.tw downloads site. You can go to [http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)  and search for 8185. This will take you to a driver download page. Download the drivers only, not the software.

make sure the card is inserted.

unzip the file and run (in the directory where the inf, cat, and sys files are):


```
sudo ndiswrapper -m
```This adds the module alias to ndiswrapper under wlan0
```
sudo ndiswrapper -i net8185.inf
```This copies the driver files to the /etc/ndiswrapper directory and configures ndiswrapper to use them. This is the driver installation. Make sure you are in the same directory as net8185.cat, net8185.sys, and net8185.inf.
```
sudo ndiswrapper -a 1799:701f net8185
```This tells ndiswrapper to use the net8185 driver you just installed with your wireless card.
```
sudo modprobe ndiswrapper
```This loads the ndiswrapper module to get the wifi card running.
```
sudo -i
echo ndiswrapper >> /etc/modules

```


Once these commands have been run, you should be able to use NetworkManager to configure the card. WPA works with NetworkManager under Feisty/Gutsy.
Tell me how it works for you.

thanks to ndiswrapper.org for the information about the realtek drivers.

---

### Post by mrtie on 2007-07-06
Hi I am a complete Linux noob, about 20 hours of 6.06 LTS and now about 10 in 7.04. Your's is the only guide I found for this card so I figured I could ask you.

My system.
Dell cpx
P3 650
440chipset
256meg of pc 100

Running 7.04 with Xfce

F5D7010 Ver.7000

Now what I did was use add/remove to install ndiswrapper, then I created desktop folder called wlan where I extracted the windows xp driver like you said, from there I opened the folder and opened terminal from there, sudo -s to gain root, then followed your commands exactly, and still the system does not see the card at all.

anything else I can try? any suggestions? I'm wanting badly to learn, but ubuntu has been somewhat frustrating thus far.

Thank you in advance.

---

### Post by Kreuger on 2007-07-09
```
sudo echo ndiswrapper >> /etc/modules
``` shows permission denied

---

### Post by mrtie on 2007-07-10
I take it back, I did it wrong, this guide works. Thank you so much and as for the permissions guy use sudo su before the last command to gain root access.

---

### Post by WillJo on 2007-08-19
I am running Xubuntu (Fiesty Fawn) on my old IBM T22 Thinkpad. I followed this HowTo and it *almost* completely worked. Everything went well but the computer would not recognize the card. I downloaded the hal-device-manager and ejected/inserted the card a few times until is showed up. Once it was present in device manager everything went smoothly, I am now connected to a WEP connection with no trouble. Device manager may not have helped but it did make it easy to tell when the card was finally recognized.

Thanks for the HowTo help!

---

### Post by FMonk on 2007-12-21
I'm having some trouble getting my Belkin card working in Gutsy.  I used this guide (if I remember correctly) to get the card working under Feisty, although I never got it automated (every time I booted, I had to run "sudo modprobe ndiswrapper" in the command line).   Now that I've upgraded to Gutsy, my card (of course) isn't working again.  So I tried all the steps that I did before, but I must have forgotten something along the way.  I installed all the ndiswrapper stuff via Synaptic, and all of the steps listed above work until I get here:

> ```
sudo modprobe ndiswrapper
```This loads the ndiswrapper module to get the wifi card running.

Where I get the response:
```
FATAL: Module ndiswrapper not found.
```

I'm pretty sure I'm just forgetting something silly, but searching ubuntuforums.org and google has not really helped me :(  I tried removing the ndiswrapper files and installing them manually, but when I typed make install, I got this error:
```
Cannot find kernel version in /lib/modules/2.6.22-14-386/build, is it configured?. Stop.
```

Can anyone help?  Is this an issue of changes between Feisty and Gutsy, or (more likely) have I just forgotten some steps? :)

---

### Post by FMonk on 2007-12-22
Nevermind, I got it working thanks to this post:

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

It seems the problem was somehow related to the ndiswrapper I had installed through Synaptic.  When I installed from source, it worked fine this time.  Hopefully others will not have to go through quite as much trouble as I did over this :p

---

### Post by DJM2 on 2007-12-30
I have this card, and I installed it using the instructions in the HOWTO. The card works mostly fine, but every once in a while my system will freeze for 2-3 seconds. dmesg | grep wlan shows this:

```

[   38.532000] wlan0: ethernet device 00:17:3f:d6:13:03 using NDIS driver: net8185, version: 0x50449, NDIS version: 0x500, vendor: 'Realtek RTL8185 Wireless LAN (Mini-)PCI NIC                                     ', 1799:701F.5.conf
[   38.532000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   58.872000] ndiswrapper (mp_reset:64): wlan0 is being reset
[ 2942.876000] ndiswrapper (mp_reset:64): wlan0 is being reset

```

I've searched far and wide on these forums and Google and have seen people getting the same error, but no solutions that applied to this card. Does anyone know what's going on? The card is usable, but this is quite annoying.

Edit: I'm running Xubuntu Gutsy.

---

### Post by ZeroDoom on 2008-02-04
This walk though worked great for me. I picked up a Belkin wireless G notebook card F5D7010 ver. 7032 from Wal-Mart for $32.99. After spending the better part of the weekend playing around I found this walk though, followed it, and I was up and running and downloading updates in no time. Really the only annoying part was downloading the Debs of the necessary packages and copying them to the Xubuntu system via usb key because it didn't have a NIC.

 The only thing I've notice is the card seems somewhat unreliable. It tends to disconnect from the Wifi network and for some reason it doesn't wanna reconnect. I found if I just remove the PC card and put it back it goes back on the wifi promptly. Now, I think I can blame the Wifi signal strength for some of that because when I moved closer to the AP the disconnects happened less often.

---

### Post by cclukins on 2008-02-10
I've used every other How to for this card and none worked. The were missing a step or two. Anyway, it works. Thank you for posting this. I tried this card in Fedora Core 8 and whenever it tried to connect the whole system just locked up. With Ubuntu and this particular How to, everything is good.

---

### Post by mikethetyro on 2008-02-11
Thanks sincerely! I had all but given up trying to get my card working but the drivers you found work perfectly. I had resigned myself to finding a different version card - I had success with 7011 cards straight out of the box - but this one was kicking me to bits.:)

---

### Post by jack_spratt on 2008-04-13
I cant get mine working...I followed your guide, followed it several times in fact but although ndiswrapper always seems to successfully install the driver, and lists the device as being present when it is, the wireless card or opportunity for wireless connection never shows up in network manager. I really dont know what to do next.

lspci lists the belkin card as an unknown Ethernet device for some reason, no idea why. Also I used the drivers that came on the CD with the card as they worked beautifully in other distros and I had a problem following the link to the ones that you suggested.

Help please! In other distros this setup to less than 3 minutes - why oh why doesnt it show up in network manager?? :cry:

currently lspci shows "02:00.0 Ethernet controller: Belkin Unknown device 701f (rev 20)". The pcmcia card is the only belkin device attached to this machine as far as I know. Also, when both the driver that came on the CD and the driver linked in the OP are installed together, the driver from the CD takes priority and states 'device present' whilst the the other downloaded driver simply says 'driver installed'.

'lshw -C network' gives:

  *-network UNCLAIMED
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: 2
       bus info: pci@0000:02:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=64 mingnt=32

'ndiswrapper -l' currently gives (net8185  was there first):

blkwgnv7 : driver installed
        device (1799:701F) present
net8185 : driver installed

---

### Post by jack_spratt on 2008-04-14
[IMG]http://www.easysmileys.com/img/other_smoker.gif[/IMG]    bump

---

### Post by bcnaat on 2008-04-14
here's what I get when I -l ndiswrapper:

pcilib: Cannot open /sys/bus/pci/devices/0000:03:00.0/config
Unable to read the standard header from device 0000:03:00.0
blkwgnv7 : driver installed
net8185 : driver installed
root@kay-laptop:~# ndiswrapper -r blkwgnv7
root@kay-laptop:~# ndiswrapper -l
pcilib: Cannot open /sys/bus/pci/devices/0000:03:00.0/config
Unable to read the standard header from device 0000:03:00.0
net8185 : driver installed

What have I done or what do I need to do?

Thanks,

Kay

---

### Post by jack_spratt on 2008-04-15
I get that when I remove and then reinsert the card; try inserting the card and then restarting. If it wont boot up properly when the card is inserted (like mine, which hangs at loading managed drivers) then remove the card, boot up, completely remove ndiswrapper, insert the card, reboot, reinstall and configure ndiswrapper.

---

### Post by jack_spratt on 2008-04-16
[img]http://www.clicksmilies.com/s1106/ernaehrung/food-smiley-006.gif[/img]  bump

---

### Post by bcnaat on 2008-04-16
Thanks Jack, I'll try that. I've already tried inserting/reinserting the card. For some reason it freaked out the mouse on my laptop. Hmmm, nope, that shouldn't matter since the mouse is usb and the card is what? pci...something or another.

---

### Post by jack_spratt on 2008-04-16
PCMCIA (Personal Computer Memory Card International Association, I believe). Its listed by the 'lspci' command however (list PCI devices); presumably there's a link between the two therefore...?

Tried the same card in Mandriva too by the way, from inserting the driver CD to browsing the net wireless took less than two minutes :???:

---

### Post by bcnaat on 2008-04-16
I am currently posting this with my wireless connection! Thank you! I usually have it hard-wired since I'm at home but if traveling I need to be able to use the wireless card. I am curious as to why removing the card stops both the usb mouse and the touchpad. 

So, now that we've accomplished that little feat, rather smoothly I might add, is there a way to eject the card so I don't have to shut down the computer to (hard reboot) since apparently the keyboard doesn't respond after pulling the card as well. I don't see a kernel panic since no lights are flashing when I remove the card.

Thanks again for this thread and for posting a response jack_spratt! Nice to know that I'm almost Windows free now. Even got the blackberry curve to show up as an external drive (using a sdmicro in the phone). No luck on the sync yet, but that will come.

---

### Post by jack_spratt on 2008-04-16
Well done bcnaat!  [img]http://www.clicksmilies.com/s1106/party/party-smiley-034.gif[/img]

Congrats. Hope you manage to fix the removal problem soon; I don't understand why it behaves in this way, but hopefully someone else who does will come along and help soon. :)

---

