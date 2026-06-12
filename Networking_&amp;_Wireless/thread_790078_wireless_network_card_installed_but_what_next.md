---
title: "wireless network card installed but what next?"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by joshpond on 2008-05-11
Hi all,

I'd appreciate any help you can give if you could please keep it simple as this is the first time I've tried anything linux.

I've installed gusty and am trying to get my netgear WG311v3 wireless card installed and logging onto the network.

I've installed ndiswrapper and have gotten what I believe to be the driver installed. 
ndiswrapper -l  
shows:

netwg311 : driver installed
     device (11AB:1FAA) present

however I don't know what to do next.

I've tried copying this help page that ran:
sudo modprobe ndiswrapper
but I have no idea what that does and nothing seems to work.

Where do I go from here?

Thanks Josh

---

### Post by chili555 on 2008-05-11
Josh-

Welcome to the party! We were all new once upon a time, so don't feel shy. Ask all the questions you need to. Sometimes we have little pile-ups to give the answer! One question sometimes get 5-6 answers.> sudo modprobe ndiswrapper
but I have no idea what that does and nothing seems to work.
sudo means, roughly, Super User (he who can do anything) do this command. modprobe means insert this module and any other modules needed to get it to work properly into the system. ndiswrapper is simply the module you want inserted. When you issue the command and the cursor just pops back to the prompt, it means, OK, I executed that command and I have no errors or warnings to report.

Can you see the Network Manager icon at the top right? If you click it, you should be able to select your network and connect.

---

### Post by joshpond on 2008-05-11
Thanks for the reply,

I've done all that and like you said just a new blank line comes up so I assume it all went well and nothing went wrong.

However when I click on the network tab there is no wireless connection available, just the the two standard ones. (Can't remember exactly but I think its the wired roaming and some other.)


Thanks Josh

---

### Post by chili555 on 2008-05-12
Let's look at these terminal commands:```
ifconfig
iwconfig
```Thanks.

---

### Post by rogier.de.groot on 2008-05-12
I'm not sure if this is appropriate for your situation, but several people, myself included, have had problems with the 'ssb' module taking over the wireless card before ndiswrapper can get to it. Try 'lsmod' to see a list of loaded modules (in a terminal window), or 'lsmod | grep ssb' just to check for ssb.
If ssb is there it might be messing with your wireless. Try
'sudo rmmod ssb'
'sudo rmmod ndiswrapper'
'sudo modprobe ndiswrapper'
and then wait a little while (half a minute or somesuch) before checking the network applet (next to the volume applet, top-right of your screen) if your wireless network is being detected.
Good luck, hope it helps.

---

### Post by joshpond on 2008-05-13
Hi guys, thank for the help so far.

I thought I posted something here yesterday but it looks like it didn't come up so here goes again.

I've tried the ssb and it wasn't loaded.

Ifconfig and iwconfig are below:

josh@josh-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0F:EA:B7:AA:6F   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:21 Base address:0xe800  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:256 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:19968 (19.5 KB)  TX bytes:19968 (19.5 KB) 

josh@josh-desktop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
I hope this helps.

thanks Josh

---

### Post by joshpond on 2008-05-16
Shameless bump...

Anyone?

Thanks Josh

---

### Post by PaJoe on 2008-05-16
> **joshpond said:**
> Shameless bump...

Anyone?

Thanks Josh

It is rough when you are all alone and don't even know how to identify the problem, I am a little further along than you are, but still don't have it either. However, when I run iwconfig after plugging in my usb wireless adapter I get the following:

buntu:~$ sudo iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT73 WLAN  ESSID:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



That makes me think you still don't have your driver installed properly, sorry I can't help you, but I didn't want you to think no one cares. I don't use ndswrapper . At one point I was able to get things moving by using: sudo dhclient wlan0

---

### Post by mplexus on 2008-05-16
when you issue sudo modprobe ndiswrapper what does it say on /var/log/messages about ndiswrapper? It might report a failure.

also, is this on a laptop? if yes, does it have a special button to enable the wireless card first?

also, if you want to bypass network manager have you looked at this?  [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by Ayuthia on 2008-05-16
You will want to see if ndiswrapper has been loaded.  Can you post your lshw -C network results?  There will be a line that contains "driver:"  It should have ndiswrapper in there.  If it doesn't then ndiswrapper did not load.

Another check is to do the following:
```
lsmod|grep ndiswrapper
```
This will go through all the active modules and find with that contains ndiswrapper.  If nothing comes up, then it is not loaded.  From there we need to see why it did not load. As mplexus, you can check /var/log/messages.  An alternative to this is to check /var/log/dmesg or type dmesg in a Terminal.  This is similar to /var/log/messages, but it only lists things for the current session instead of including the last few boots.

---

### Post by joshpond on 2008-05-16
Hi guys,

thanks for all the help.

After Pajoe thought the driver may not have been installed properly I decided to reinstall Ubuntu and reinstall the drivers all over from scratch.

I followed this setup and one differece is that I used the marvel driver instead of the netgear, don't know if this made a difference but...

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

this seems to have worked and the device is now loaded and it comes up under the network applet.

josh@desktop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11b  ESSID:off/any   
          Mode:Managed  Channel:0  Access Point: Not-Associated    
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm   
          RTS thr=2346 B   Fragment thr=2346 B    
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 


 So thanks for all your help. i just have to connect it up to the network now as dhcp doesn't work.

I know that it is a wired network with a wireless router but can't remember if it is static or not.

Thanks for the help.

---

### Post by zspitzer on 2008-05-20
I just tried the same and it failed.. again, this wg311v3 card is annoying

i'm on 8.0.4 64 bit

[   50.022138] ndiswrapper: using IRQ 17
[   50.035441] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   50.035448] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   50.035458] ndiswrapper (mp_halt:259): device ffff8100b12cf700 is not initialized - not halting
[   50.035460] ndiswrapper: device eth%d removed

---

### Post by Ayuthia on 2008-05-20
> **zspitzer said:**
> I just tried the same and it failed.. again, this wg311v3 card is annoying

i'm on 8.0.4 64 bit

[   50.022138] ndiswrapper: using IRQ 17
[   50.035441] ndiswrapper (mp_init:216): couldn't initialize device: C0000001
[   50.035448] ndiswrapper (pnp_start_device:439): Windows driver couldn't initialize the device (C0000001)
[   50.035458] ndiswrapper (mp_halt:259): device ffff8100b12cf700 is not initialized - not halting
[   50.035460] ndiswrapper: device eth%d removed
You might try:
```
sudo modprobe -r ndiswrapper
sudo depmod -ae
sudo modprobe ndiswrapper
```and see if it clears it up in dmesg.  If it does not, you might try another driver.

---

