---
title: "Belkin F5D7050 Kills Ubuntu!"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by andypaterson on 2007-08-12
Firstly, i am VERY new to Linux and Ubuntu, having used Windows for years and finally getting a bit fed up!

Secondly, i've seached to forum, 'cos noone like noobs posting questions that have been asked a thousand times before.  I see loads of people having trouble getting the F5D7050 working, but at least they can plug theirs in without the computer dying.

Basically, i thought i'd try Ubuntu Feisty Fawn and liked it so installed it  over Vista.  Everything seemed to be going well until i tried top plug in my Belkin F5D7050 Wireless USB dongle...it just kills Ubuntu!

I wouldn't say it freezes it because i can still use the mouse, and try to open programs/terminal etc.  It's just that nothing will open, and anything already open will no longer respond.  It wont even shut down or log out, so i have to hard reset.

Also, If i have the Wireless USB plugged in at power-on, it wont boot.

Anyway, hope someone knows what the devils going on cos its driving me mad having an ethernet cable running all the way downstairs to the router nearly tripping me up every 5 mins.

Sorry about the long first thread :-p

---

### Post by bmartin on 2007-08-12
I have this wireless USB stick. Unfortunately, depending on your version of the stick, it might contain different chipsets. What is the output of **lspci | grep -i wireless**?

My guess is it's an RT73 chipset. My parents have that chipset and it used to cause their computer to freeze while booting. [Here's a HOW-TO ]("http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey") for that. Good luck.

---

### Post by andypaterson on 2007-08-13
Thanks for that, i've seen some of the similar threads and guides but not that one, will give it a bash!

I'll post the output to **lspci | grep -i wireless** when i get back home (in work at the mo).  What will that code be giving me information on?  and would the wireless stick be needed to be plugged in for any output?

Thanks :)

---

### Post by Austin_KW on 2007-08-13
The problem is usually because there is multiple incompatible drivers trying to manage your device. 
There are different versions of the F5D7050, with different chipsets and often all drivers get loaded.

Start with the howto in the second post. It may not be for your chipset but it will explain how to blacklist some drivers to stop the from loading.

The correct command to find you wireless adapter is "lsusb". The device ID xxxx:yyyy may help tell you which chipset you have (but belkin did not always update the ID, hence the multiple driver problem)
The command "lsmod | grep usbcore" will tell you which drivers are loaded and using the usb (not all will be for the wireless but if you post the output we can see what is going on)

If you still have the box, there should be a sticker on (v1000,v2000,v3000 etc).
Or you can pry the dongle apart with a finger nail and read the chip id.

---

### Post by bmartin on 2007-08-13
> **andypaterson said:**
> Thanks for that, i've seen some of the similar threads and guides but not that one, will give it a bash!

I'll post the output to **lspci | grep -i wireless** when i get back home (in work at the mo).  What will that code be giving me information on?  and would the wireless stick be needed to be plugged in for any output?

Thanks :)
Actually, doing that (plugging in the dongle) may lock up your computer. If it does, try removing the rt73usb kernel module before plugging the dongle in.
**sudo modprobe rt73usb**

If you want to permanently remove the kernel module, you can blacklist it:
```
echo blacklist rt73usb | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by andypaterson on 2007-08-13
Excellent, good few ideas to try out tonight then!  Thanks for the help, what a friendly place :)

---

### Post by andypaterson on 2007-08-13
> **bmartin said:**
> I have this wireless USB stick. Unfortunately, depending on your version of the stick, it might contain different chipsets. What is the output of **lspci | grep -i wireless**?
 [/URL] for that. Good luck.

No output.

I blacklisted the rt73usb and now it enables me to plug in the USB device without freezing, so thats good!

I'll try the guide now and see if i can get it working.

---

### Post by bmartin on 2007-08-13
Okay, then you probably have the RT73. That guide should work. You'll have to rebuild the kernel module every time you have a new kernel. If you're handy with scripting, you can write a script that rebuilds the kernel module if it doesn't already exist. If you want help with that, let me know.

---

### Post by Austin_KW on 2007-08-13
> **andypaterson said:**
> No output.

I blacklisted the rt73usb and now it enables me to plug in the USB device without freezing, so thats good!

I'll try the guide now and see if i can get it working.

The command should be lsusb. If it is 050d:7050 it is probably a rt2570 or a prism, if it is 050d:705a it is probably a rt73.
 
You will also need the output of "lsmod | grep usbcore" (you may also see prism and rt2570 drivers) as rt73usb should not have caused a freeze on its own.

---

### Post by andypaterson on 2007-08-13
> **Austin_KW said:**
> The command should be lsusb. If it is 050d:7050 it is probably a rt2570 or a prism, if it is 050d:705a it is probably a rt73.
 
You will also need the output of "lsmod | grep usbcore" (you may also see prism and rt2570 drivers) as rt73usb should not have caused a freeze on its own.

Ok, here goes.  Got to stage 13 of the guide, but i get the messaeg:

> andy@Ubuntu:/usr/src/rt73-cvs-2007081313/Module$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device


lspci | grep -i wireless brought back nothing.

lsusb
> Bus 002 Device 002: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 050d:705a Belkin Components 
Bus 001 Device 001: ID 0000:0000  

And finally

lsmod | grep usbcore
> usbcore               134280  7 rt73,ipaq,usbserial,usbhid,uhci_hcd,ehci_hcd

So it would seem that i have the 705a which is the rt73.  But it's not being seen properly?

Very confusing if you ask me!

---

### Post by bmartin on 2007-08-13
The name of the wireless device for Ralink devices isn't normally wlan0. Type **iwconfig** into a terminal and see if a wireless device shows up. It should be named rausb0 or something like that. Use **sudo ifconfig rausb0 up** instead... or whatever the device name is.

---

### Post by Austin_KW on 2007-08-13
Yes, looks good so far,

Try the command "ifconfig -a" Sometimes it creates wlan1 rather than wlan0.

---

### Post by andypaterson on 2007-08-13
> **Austin_KW said:**
> Yes, looks good so far,

Try the command "ifconfig -a" Sometimes it creates wlan1 rather than wlan0.

Spot on, i realised it was wlan1.

The device is showing up in the network settings, tried to configure it to my Wireless but it didnt seem to want to .  Have read that it might be because of my encryption (WPA), so might take off the encryption and see if i can connect then.

Not tonight though, im off to bed!   :-p

---

### Post by andypaterson on 2007-08-14
Well i'm now typing on the forum using my Wireless!  Success.  Relatively, as theres no encryption at the moment.  I'll work on adding that on.

Whats most compatible though, WPA or WEP?  I was using WPA-PSK before.

Also, i had to unplug and reinert the dongle to egt it working.  Is that normal, or do i have to code it to start automatically?

Thanks for the help guys.  =D>

---

### Post by Austin_KW on 2007-08-14
> **andypaterson said:**
> Well i'm now typing on the forum using my Wireless!  Success.  Relatively, as theres no encryption at the moment.  I'll work on adding that on.

Whats most compatible though, WPA or WEP?  I was using WPA-PSK before.

Also, i had to unplug and reinert the dongle to egt it working.  Is that normal, or do i have to code it to start automatically?

Thanks for the help guys.  =D>

You want to use WPA-PSK, WEP can now be cracked in 2 minutes using a replay attack.

You want to configure the device to use WPA in the file /etc/network/interfaces, follow the howto. I have the same V3000 device and sometimes I need to remove and reinsert, if it does not come up on boot. After reinserting you may need to enter the command "sudo ifup --f wlan1" to force a re-execute of the init in /etc/network/interfaces.

---

### Post by bmartin on 2007-08-14
On every subsequent startup of your computer, it should be detected automatically

*except*

You had to compile a kernel module to get this running, right (rt73.ko)? You need to compile a new kernel module every time your kernel updates, which isn't often.

---

### Post by andypaterson on 2007-08-15
> **Austin_KW said:**
> You want to use WPA-PSK, WEP can now be cracked in 2 minutes using a replay attack.

You want to configure the device to use WPA in the file /etc/network/interfaces, follow the howto. I have the same V3000 device and sometimes I need to remove and reinsert, if it does not come up on boot. After reinserting you may need to enter the command "sudo ifup --f wlan1" to force a re-execute of the init in /etc/network/interfaces.

Just trying the guide now for WPAPSK, doesnt seem to be working though.  When i fo "sudo ifup --f wlan1" it just wont resolve, cant ping the router and states "no working leases in persistent database".  Sure i've got all the right details in /etc/network/interfaces.

Ill keep trying.

---

### Post by nickmcg on 2007-08-15
With that driver, you won't be able to use the usual tools which use wpasupplicant, but will need to use 'iwpriv' - there are several threads on this, some are more complicated than others (search on rt2500, wpa, iwpriv) - look at [http://ubuntuforums.org/showthread.php?t=520363](http://ubuntuforums.org/showthread.php?t=520363)

I'm using a wireless card with the rt2570 chip, and have just had success with gutsy gibbon which uses the later rt2x00 drivers which do support wpasupplicant, so configuration is much simpler - I couldn't build these drivers in feisty.

The drivers for these ralink chips are from serialmonkey [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

I hope that's of some use

Nick

---

### Post by Austin_KW on 2007-08-15
> **andypaterson said:**
> Just trying the guide now for WPAPSK, doesnt seem to be working though.  When i fo "sudo ifup --f wlan1" it just wont resolve, cant ping the router and states "no working leases in persistent database".  Sure i've got all the right details in /etc/network/interfaces.

Ill keep trying.

You should be able to get it working, I have the same usb stick.

Make sure that you change your router to use WPAPSK.

Check your wpa psk key and other settings in /etc/network/interfaces for typos. Also make sure that you have removed the old WEP config from this file.
One other thing to try is setting the SSID twice in /etc/network/interfaces; Once before setting the WPAPSK and once after. Some serialmonkey drivers did require this as the ssid is used with the PSK to generate the actual encryption key.

If you still have problems you might post your /etc/network/interfaces an we can see if there is anything obvious.

---

### Post by andypaterson on 2007-08-15
Got it working from the How-To thread.  Needed to put this into the interfaces:

> auto wlan1
iface wlan1 inet dhcp
    pre-up ifconfig wlan1 up
    pre-up iwconfig wlan1 mode managed
    pre-up iwpriv wlan1 set EncrypType=TKIP
    pre-up iwpriv wlan1 set AuthMode=WPAPSK
    pre-up iwconfig wlan1 essid Xxxxx
    pre-up iwpriv wlan1 set WPAPSK="xxxxxxxxxx"
    pre-up iwconfig wlan1 essid Xxxxx

Just realised you'd pretty much said that in:

> **Austin_KW said:**
> 
One other thing to try is setting the SSID twice in /etc/network/interfaces; Once before setting the WPAPSK and once after. Some serialmonkey drivers did require this as the ssid is used with the PSK to generate the actual encryption key.



Works a treat now, picks up the device and configures automatically from boot-up.  Thanks for all the help!

Now need to do some tweaking to get everything else running perfick.  Don't be suprised to see some other threads from me ;-)

---

### Post by dannyboy79 on 2007-08-15
Are you saying that you got it working with Gutsy Tribe 4 out of the box??? Mine will not work. I just keep getting the DHCPDISCOVER message on various ports failing over and over. My Belkin F5D7050 has the 2571wf wireless chip in it. Is this why it doesn't work with the rt73usb, rt2x00 or rt2500 drivers that Ubuntu Gutsy provides by default?

I can however use the rt73 cvs daily from serialmonkey but that's not the point, I just don't understand why Ubuntu does include what WORKS versus something that hasn't worked since Dapper I believe.

---

### Post by dannyboy79 on 2007-08-15
> **Austin_KW said:**
> The command should be lsusb. If it is 050d:7050 it is probably a rt2570 or a prism, if it is 050d:705a it is probably a rt73.
 
You will also need the output of "lsmod | grep usbcore" (you may also see prism and rt2570 drivers) as rt73usb should not have caused a freeze on its own.

just an FYI, my lsusb shows 050d:7050, when I looked inside it was a 2571wf chip. The rt73 cvs daily from serialmonkey got it working.

---

### Post by Austin_KW on 2007-08-15
> **dannyboy79 said:**
> just an FYI, my lsusb shows 050d:7050, when I looked inside it was a 2571wf chip. The rt73 cvs daily from serialmonkey got it working.

Yes, Hence my first post in this thread and my cautious use of the word "probably" ;) 
You have to love belkin, changing the chipset but not the ID, the mark 1 fingernail is the best tool for finding which chipset it is.

---

### Post by nickmcg on 2007-08-15
> **dannyboy79 said:**
> Are you saying that you got it working with Gutsy Tribe 4 out of the box??? Mine will not work. I just keep getting the DHCPDISCOVER message on various ports failing over and over. My Belkin F5D7050 has the 2571wf wireless chip in it. Is this why it doesn't work with the rt73usb, rt2x00 or rt2500 drivers that Ubuntu Gutsy provides by default?

I can however use the rt73 cvs daily from serialmonkey but that's not the point, I just don't understand why Ubuntu does include what WORKS versus something that hasn't worked since Dapper I believe.

I had that problem until this morning's update - dhcp was failing, although the adaptor was associated with the ap, and ifdown would report that a dhcp lease was being released.

I assume that there must have been an update of the rt2x00 module, as the sources were updated.

Funny thing is that the network didn't start working until the third time I restarted.

Nick

---

### Post by dannyboy79 on 2007-08-15
> **nickmcg said:**
> I had that problem until this morning's update - dhcp was failing, although the adaptor was associated with the ap, and ifdown would report that a dhcp lease was being released.

I assume that there must have been an update of the rt2x00 module, as the sources were updated.

Funny thing is that the network didn't start working until the third time I restarted.

Nick

ok, did you blacklist the rt73usb module? because when I view dmesg it shows that the rt73usb driver is being loaded. I'll try to do an update and safe-upgrade on my Ubuntu Tribe 4 install and pray that it works. I can' t even get associated to the AP. iwconfig says Not Associated. Also, I use WEP if you think that matters.

---

### Post by nickmcg on 2007-08-15
> **dannyboy79 said:**
> ok, did you blacklist the rt73usb module? because when I view dmesg it shows that the rt73usb driver is being loaded. I'll try to do an update and safe-upgrade on my Ubuntu Tribe 4 install and pray that it works. I can' t even get associated to the AP. iwconfig says Not Associated. Also, I use WEP if you think that matters.

I was using WEP and have now changed to WPA. I was using rt2570 in kernel  2.6.22-8-generic (ok, different drivers, same authors etc.), and the upgrade to  2.6.22-9-generic introduced the rt2x00 which initially did not seem to work. I deliberately didn't add rt2570 to the latest kernel, and used the previous version for most things. 
It was during this morning's test that I found that things miraculously worked!

The details of earlier problems are in this thread [http://ubuntuforums.org/showthread.php?t=522589](http://ubuntuforums.org/showthread.php?t=522589)

HTH

Nick

---

### Post by dannyboy79 on 2007-08-15
I am a little puzzled by what this means? "and the upgrade to 2.6.22-9-generic introduced the rt2x00 which initially did not seem to work. I deliberately didn't add rt2570 to the latest kernel, and used the previous version for most things."
Are you saying that you compiled your own kernel? Are you saying that you blacklist the rt2570 module, if so I didn't even realize there was one, I always thought it was just rt73usb, rt2x00lib, rt2x00, rt2500. I may be wrong here but that's what I thought I all saw when doing lsmod rt and then using tab completion.

ok, if you wouldn't mind, could you please inform me if you had to blacklist anything? What chip exactly is in your usb wireless adapter? Could you show me the output of a dmesg | grep rt73 OR dmesg | rt2
also a
lsmod | grep rt
what does lsusb show. I just can't believe that we have the same chips in our usb adapters due to me just trying Gutsy Tribe 4 days ago and I kept getting the no dhcp offers error. I even see the light blinking when I do the sudo ifup wlan0 but it's only a blink or 2, then the light is dead again.

---

### Post by nickmcg on 2007-08-15
Sorry for any confusion - to try & explain:

I'm using Gutsy gibbon and update regularly
The kernel version was upgraded to 2.6.22-9 by the update daemon. It seems that when this update was applied, the rt2x00 drivers were included.
In the previous versions of gutsy kernel, (e.g 2.6.22-8 ) I'd had to build rt2570 to have the wireless working.

So, while I was trying to find out why the current version of gutsy (2.6.22-9 with rt2x00) didn't get an ip address, I would reboot to the previous kernel (2.6.22-8,  which had rt2570 loaded) from the grub menu so that I could use the net.
 
As you requested
```
robot@lex:~$ dmesg | grep rt2
[   64.032000] usbcore: registered new interface driver rt2500usb
```
and```
robot@lex:~$ lsmod | grep rt
snd_rtctimer            4384  0 
gameport               16776  1 snd_via82xx
rt2500usb              22016  0 
rt2x00usb              12032  1 rt2500usb
rt2x00lib              19712  2 rt2500usb,rt2x00usb
rfkill                  8208  1 rt2x00lib
mac80211              171016  3 rc80211_simple,rt2x00usb,rt2x00lib
snd_mpu401_uart         9600  1 snd_via82xx
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_timer              24324  5 snd_rtctimer,snd_pcm,snd_seq
snd                    54660  19 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                35016  1 via_agp
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
usbcore               137864  7 gspca,rt2500usb,rt2x00usb,xpad,usbhid,uhci_hcd
```
and ```
robot@lex:~$ lsusb
Bus 002 Device 002: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi
```

We are not using the same chip, but the drivers are from the same authors, so it may be that it's a similar problem that has been fixed   (I'm ever the optimist).

I haven't built my own kernel (I've tried in the past, but created more problems than I've cured), but had to compile the rt2570 module for the previous gutsy kernel.
I have not touched the blacklist (ever).

It seems to have been today's update that fixed my rt2x00 problems.

I hope that this is of some use. Let me know if you want any more info.

Nick

---

### Post by dannyboy79 on 2007-08-15
thanks, that what I figured. The rt73usb driver just plain doesn't ever associate itself with the AP nor do I ever get an ip. I just don't get why the dev's can't just include the rt73 that works with Gutsy. Oh well, i'll just have to compile it, blacklist all the others, and use the rt73 which does work. It's just a shame that this doesn't work out of the box.

Gutsy isn't done so maybe they'll get it right but I have seen this driver not work since back to Dapper.

---

### Post by nickmcg on 2007-08-15
Have you tried building the latest version of the driver from [serialmonkey's]("http://rt2x00.serialmonkey.com") website?

Nick

---

### Post by _oOMOo_ on 2007-08-15
I don't know if this is useful, but I have the Ralink RT73 chipset on usb and it works with the RT73usb  module. It drops connection occasionally, have been trying to figure out why all evening, but after reading up about the module it seems it is unusual for it to work at all!

The biggest problem is that when it drops connection I have to actually shut down the laptop and reboot for it to connect again.

It connects fine with network manager to WPA-PSK.

Just to confer with nickmcg - I'm guessing it must have been the kernel update that brought in the updated rt2x00 driver package, but I've only just installed Gutsy so I can't be sure.

---

### Post by nickmcg on 2007-08-16
> **_oOMOo_ said:**
> The biggest problem is that when it drops connection I have to actually shut down the laptop and reboot for it to connect again.

What happens if you ```
sudo ifdown wlan0
sudo ifup wlan0
```(assuming that wlan0 is the device name)?

Nick

---

### Post by nickmcg on 2007-08-16
> **dannyboy79 said:**
> thanks, that what I figured. The rt73usb driver just plain doesn't ever associate itself with the AP nor do I ever get an ip. I just don't get why the dev's can't just include the rt73 that works with Gutsy. Oh well, i'll just have to compile it, blacklist all the others, and use the rt73 which does work. It's just a shame that this doesn't work out of the box.

Gutsy isn't done so maybe they'll get it right but I have seen this driver not work since back to Dapper.

Back to the drawing board - it's all gone wrong!:(

I had to reset the machine, and now it's stopped talking to the network. occasionally I can get an ip address, but then the network is unreachable

Back to rt2570 (if I can)

Nick

---

### Post by _oOMOo_ on 2007-08-16
```

~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

```

wlan0 is the Ralink usb:

```

~$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:10:60:FB:D5:DE  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::210:60ff:fefb:d5de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7585 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15725693 (14.9 MB)  TX bytes:822873 (803.5 KB)

```

The connection works in the main but dies horribly requiring shutdown + reboot.

---

### Post by nickmcg on 2007-08-16
> **_oOMOo_ said:**
> ```

~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

```


How do you configure your network card? Netmanager?

Nick

---

### Post by dannyboy79 on 2007-08-16
ifdown and ifup I believe just parse your /etc/network/interfaces file for it's info. you need to ensure that your interfaces file has a section for wlan0 interface. or you can just use the iwconfig to setup the connection. I have read that network-manager causes issues with the belkin adapters so I uninstalled mine. try out wifi-radar maybe? or serialmonkey has a utility for configuring wireless adapters on their site. as I asked before, what chip are you using.

have you tried this guide: [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by _oOMOo_ on 2007-08-16
It seems I have the rt73usb module working now - it's early as yet but it's been transferring at ~950 kbps on 350MB files.

Yes it was configured on install by network manager.

I think my problem (or at least part of the problem) was related to APIC - on boot I was getting:

MP-BIOS bug: 8254 timer not connected to IO-APIC

I added noapic to /boot/grub/menu.lst and ran update-grub as sudo (more details [http://ubuntuforums.org/showthread.php?t=191355]("http://ubuntuforums.org/showthread.php?t=191355"))and the bug stopped coming up on boot and the wireless seems ok....

---

### Post by dannyboy79 on 2007-08-16
> **_oOMOo_ said:**
> It seems I have the rt73usb module working now - it's early as yet but it's been transferring at ~950 kbps on 350MB files.

Yes it was configured on install by network manager.

I think my problem (or at least part of the problem) was related to APIC - on boot I was getting:

MP-BIOS bug: 8254 timer not connected to IO-APIC

I added noapic to /boot/grub/menu.lst and ran update-grub as sudo (more details [http://ubuntuforums.org/showthread.php?t=191355]("http://ubuntuforums.org/showthread.php?t=191355"))and the bug stopped coming up on boot and the wireless seems ok....
ok, this is very weird. Are you positive that your wireless chip (by actually looking at it within the adapter) is the rt73. It's just weird that I can't get my Belkin wireless usb adapter to work with the rt73usb out of the box module but I can get the rt73 module from serialmonkey to work. I suppose I can see if I am getting that same error in the dmesg output as far as APIC goes but I don't remember seeing it. I would always see wlan0 link not ready after the rt73usb module was loaded within dmesg output.

Now I know my wireless chip for sure is the rt2571wf since I opened the adapter using my fingernail. I just wonder why the rt73 module works for the rt2571wf chip but the rt73 doesn't? Anyway, anymore info you could provide would be great. Like do you blacklist modules? What does you /etc/network/interfaces file look like. Are you using Tribe 4? Is it kubuntu, gnome, or xubuntu whichever version is it (meaning feisty, egdy, or gutsy, or dapper) What kernel? (uname -r) What type of upadtes do you accept? all or only security updates.

---

### Post by Austin_KW on 2007-08-16
> **dannyboy79 said:**
> ok, this is very weird. Are you positive that your wireless chip (by actually looking at it within the adapter) is the rt73. It's just weird that I can't get my Belkin wireless usb adapter to work with the rt73usb out of the box module but I can get the rt73 module from serialmonkey to work. I suppose I can see if I am getting that same error in the dmesg output as far as APIC goes but I don't remember seeing it. I would always see wlan0 link not ready after the rt73usb module was loaded within dmesg output.

Now I know my wireless chip for sure is the rt2571wf since I opened the adapter using my fingernail. I just wonder why the rt73 module works for the rt2571wf chip but the rt73 doesn't? Anyway, anymore info you could provide would be great. Like do you blacklist modules? What does you /etc/network/interfaces file look like. Are you using Tribe 4? Is it kubuntu, gnome, or xubuntu whichever version is it (meaning feisty, egdy, or gutsy, or dapper) What kernel? (uname -r) What type of upadtes do you accept? all or only security updates.

I have just post to the rt73 howto about getting rt73usb working. You will need to update to the latest gusty kernel and wireless tools and undo any blacklisting of the rt2x00/80211 modules. It is not perfect. It would not work when I was using channel 13 and it is not always seeing all networks in a scan, but you can manually configure it using the network manager.

---

### Post by dannyboy79 on 2007-08-16
> **Austin_KW said:**
> I have just post to the rt73 howto about getting rt73usb working. You will need to update to the latest gusty kernel and wireless tools and undo any blacklisting of the rt2x00/80211 modules. It is not perfect. It would not work when I was using channel 13 and it is not always seeing all networks in a scan, but you can manually configure it using the network manager.

well I have to disagree. I have been trying this darn Belkin usb adapter ever since Edgy. I am currently using the latest Tribe 4 downloaded AS Tribe 4 not updated to it, with the latest kernel 2.6.22-9-generic it does NOT work. This is a brand new install, no blacklisting of anything or anything like that. It's a Dell Dimension 8200, 256mb ram, MX 400 nvidia gfx card. As I have specified over and over, the chip inside the Belkin F5D7050 is a 2571wf. 

dmesg just says wlan0 link not ready. and when I configure it manually thru network-manager,  i just keep getting the no DHCP offers found or whatever it was. and if I do the configuring of the interface through the command line and then try sudo ifup --f wlan0, I just keep getting DHCPDISCOVER over and over on various ports than nothing. The light does blink for a second but then nothing.

---

### Post by Austin_KW on 2007-08-16
Me LEDs did not light up initially.
Remove your auto wlan0 config from interfaces. I am using  2.6.22-9-generic #1 kernel on feisty with updated gusty wireless tools on a belkin 7050 v3. Are you getting the wireless config options on network manager after you plug it in? It can work because I posted to that thread using it.
Have you checked lsmod for conflicting drivers

---

### Post by _oOMOo_ on 2007-08-16
Apologies - I did think I had it working, it hadn't ever been so stable, but it dropped out horribly again when barely being used.

My syslog shows this error repeatedly:

```

Aug 16 19:37:35 charlie NetworkManager: <info>  nm_policy_device_change_check:: old_dev has_link? 1 
Aug 16 19:37:35 charlie NetworkManager: <info>  nm_policy_device_change_check:: old_dev && new_dev!!

```

But it happily spits that out at 2min(ish) intervals all the time it is connected.

When it hangs it spools this error until it times out:

```

Aug 16 19:37:49 charlie kernel: [  179.036000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
Aug 16 19:37:49 charlie kernel: [  179.136000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x308c with error -110.
Aug 16 19:37:49 charlie kernel: [  179.236000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
Aug 16 19:37:50 charlie kernel: [  179.772000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
Aug 16 19:37:50 charlie kernel: [  179.872000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
Aug 16 19:37:50 charlie kernel: [  179.972000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
Aug 16 19:37:50 charlie kernel: [  180.072000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
Aug 16 19:37:50 charlie kernel: [  180.172000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
Aug 16 19:37:50 charlie kernel: [  180.272000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
Aug 16 19:37:50 charlie kernel: [  180.372000] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.
Aug 16 19:37:50 charlie kernel: [  180.372000] phy0 -> rt73usb_bbp_read: Error - PHY_CSR3 register busy. Read failed.

```

I also see this occasionally:

```

Aug 16 19:37:35 charlie kernel: [  165.152000] wlan0: duplicate address detected!

```

but it isn't responsible for the dropping of signal.

Sorry about the APIC red herring, it seemed too good to be true!

---

### Post by dannyboy79 on 2007-08-16
> **Austin_KW said:**
> Me LEDs did not light up initially.
Remove your auto wlan0 config from interfaces. I am using  2.6.22-9-generic #1 kernel on feisty with updated gusty wireless tools on a belkin 7050 v3. Are you getting the wireless config options on network manager after you plug it in? It can work because I posted to that thread using it.
Have you checked lsmod for conflicting drivers
well then we obviously don't have the same wireless chip then. Yes I am getting the wireless options within the network-manager. when I run lsmod it returns both the rt73usb and the rt2500 or was it rt2x00 and also something like rt2x00lib or was it rt2500lib. That's why I asked you if you blacklisted anything and you said no. 
dmesg shows it load rt73usb and wlan0 link not ready. apparently we have different chips within our adpaters. I keep telling you mine but you haven't informed me what chip is in yours? if you did I didn't see that so what was it again?

---

### Post by Austin_KW on 2007-08-16
Mine is a rt2571wf. But I would not bother, it is not ready for prime time. Done some more testing and it is interfering with my other usb devices and I can not get it to work as wlan0, only as wlan1.
You might try editing you iftab and seeing if having yours set to wlan1 helps.

---

### Post by Austin_KW on 2007-08-16
Ok, at least on my laptop, it definately has to be set as wlan1. I have now verified the new beta rt2x00 drivers on rt2500 and rt73(2571wf)

---

### Post by dannyboy79 on 2007-08-17
> **Austin_KW said:**
> Ok, at least on my laptop, it definately has to be set as wlan1. I have now verified the new beta rt2x00 drivers on rt2500 and rt73(2571wf)

when you say the new beta drivers, are you referring the drivers that come with Gutsy? Meaning will it work "out of the box"? If so, do I need to blacklist the rt73usb driver? I keep asking the same questions over and over because as I have already stated, I am running Gutsy Tribe 4 (downloaded days ago) and it does not work by simply booting the machine and configuring wlan0 which is what shos up in the Network dialog box. Also, if only wlan0 shows up, how would it help to go to my interfaces file and make an wlan1 interface? Thank you for anymore info you can provide for this.

---

### Post by Austin_KW on 2007-08-17
> **dannyboy79 said:**
> when you say the new beta drivers, are you referring the drivers that come with Gutsy? Meaning will it work "out of the box"? If so, do I need to blacklist the rt73usb driver? I keep asking the same questions over and over because as I have already stated, I am running Gutsy Tribe 4 (downloaded days ago) and it does not work by simply booting the machine and configuring wlan0 which is what shos up in the Network dialog box. Also, if only wlan0 shows up, how would it help to go to my interfaces file and make an wlan1 interface? Thank you for anymore info you can provide for this.

Yes, I am experimenting with the gutsy kernel 2.6.22-9-generic and drivers (under feisty, not that that should matter)

You should not need to blacklist anything unless something is interfering with your usb dongle. 
"lsmod | grep usbcore" will tell you what is using the usb

You change the interface name by editing /etc/iftab and adding/changing  a line with your mac addresss "wlan1 mac 00:11:xx:xx:xx:xx arp 1"   I could not get it to work for wlan0 but this could be something in my hacked up settings. I have 2 ralink wireless cards (rt73 & rt2500) and I could never get the one set to wlan0 to work so I use wlan1 and wlan2

Do not put "auto wlan1" or "ixconfig wlan1" settings in your interfaces file. Use networkmanager to manage your settings. 

When manually scanning for networks use "sudo iwlist scan" not "iwlist scan". This should be the first thing you do. Then select your network using the network manager, it should be listed if it is not hidden. It may take you a couple of attempts to connect and get an ip address.

---

### Post by defconoii on 2007-10-24
i have the same card Belkin F5D7050-4 rev 3002, the ubuntu modules/drivers are completely broken for this card, it is a known issue and a lack of manpower/knowledge, there is plenty of complains on launchpad and bug reports but whoever maintains these drivers for the rt73 have over looked it since pre-feisty and neglected to fix the problem, other os's like pclinuxos and fedora support this card and work out of the box, its a shame because they are so far inferiour to ubuntu.  The only solution I have come to is to grab the serialmonkey drivers and use wep, because wpa seems to crash ubuntu gutsy final, wpa/wep worked fine in feisty with the serialmonkey drivers.

I know more than a dozen people I work with that use these cards and that just near me, so there is probably thousands of people stuck with windows that have these cards...

Thats total BS is that the chipset maker released opensource drivers and firmware and ubuntu has it all wrong, wtf have they done and wtf are they doing!!!

---

