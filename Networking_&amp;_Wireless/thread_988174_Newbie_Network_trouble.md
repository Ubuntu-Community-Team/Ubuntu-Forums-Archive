---
title: "Newbie Network trouble"
date: 2008-11-20
forum: Networking &amp; Wireless
---

### Post by Castarmax on 2008-11-20
Ok after hosing my system I finally have Ubuntu installed on HD1 and XP on HD0.
I can dual boot from either system depending on what bios has as 1st HD. That was achieved my editing boot.ini and /boot/grub/menu.1st. Easy enough...
As far as my network I have DSL service coming into an Embarq 660 modem which is in bridged (DMZ) mode. From there it goes into a wireless G Linksys WRT54GS 4 port wireless router. I do not normally use the wireless. This was set up as DCHP.
When trying to get Ubuntu up, it would not connect to the net but the other XP box would UNLESS Ubuntu was running. XP connects on both boxes always unless Ubuntu is running. In an attempt to fix that I set the router to manual. Router is set at 192.168.0.1. I set both XP boxes with static IP's 192.168.0.10 and 192.168.0.20 and the printer at 192.168.0.150 gateway at 192.168.0.1 and subnet at 255.255.255.0 with DCHP server at 192.168.0.1.
All works just fine with static IP's except Ubuntu which has the same settings installed using alternate install CD. I used 192.168.0.10 for both XP and Ubuntu since its dual boot.
Ubuntu upon 1st reboot will rename eth0 to ifup eth0. I can reconfigure this to the proper settings but can not change the name. Also the subnet mask ALWAYS changes to a single number upon reboot. I can not delete that card.
When this did not work I manually did the settings by editing /ect/network/interfaces to...

iface eth0 (or whatever card is called) inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

While in root Ubuntu finds errors when I try ifup eth0 or ifdown eth0.
Sometimes Ubunto will see the card ok and say it connected. Then I can actually ping 192.168.0.10 but nothing else. Now I can't even see the 2 monitors in the corner.

I have a Striker Extreme MB with 2 onboard nics. I have disabled one of them in bios for simplicity. I have read about this card and some fixes. The fix was editing /ect/modprobe.d/options and adding

options forcedeth msi=0 msix=0

This doesnt seem to do anything.I have Googled and Googled and Googled and have not gotten anywhere. This becomes more difficult as I am a total Ubuntu newb. After this is resolved I have to attack installing the proper video drivers. Apparently the Nvidia 8800 GTX has issues.
Regardless, anyone have suggestions. I'd post logs ect but I dont know how or what to post nor do I know how to get the logs from Ubuntu to XP for posting short of burning them on cd maybe??

HELP!!


John

---

### Post by superprash2003 on 2008-11-20
if router ip is 192.168.0.1 then shouldnt your gateway be 192.168.0.1 instead of 192.168.1.1

---

### Post by Castarmax on 2008-11-20
Typo here in the forms. I edited it.

Thanks

---

### Post by Castarmax on 2008-11-20
Hoping these are helpful. Anything else I should post?


john@ubuntu:~$ ifconfig eth0 
eth0      Link encap:Ethernet  HWaddr 00:1a:92:81:1b:71  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::21a:92ff:fe81:1b71/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2212 (2.2 KB) 
          Interrupt:214 Base address:0x8000 



here is /ect/network

# The primary network interface 
auto eth0 
iface eth0 inet static 
	address 192.168.0.10 
	netmask 255.255.255.0 
	network 192.168.0.0 
	broadcast 192.168.0.255 
	gateway 192.168.0.1 
	# dns-* options are implemented by the resolvconf package, if installed 
	dns-nameservers 192.168.0.1 
	dns-search john




here is /ect/modprobe.d/options

# Enable double-buffering so gstreamer et. al. work 
options quickcam compatible=2 

# Default hostap to managed mode 
options hostap_pci iw_mode=2 
options hostap_cs iw_mode=2 

# Stop auto-association. 
# LP: #264104 
options ipw2200 associate=0 
options forcedeth msi=0 msix=0 

# XXX: Ignore HPA by default. Needs to be revisted in jaunty 
options libata ignore_hpa=1

---

### Post by Castarmax on 2008-11-21
Anyone? Am I posting enough? Can I do something more to provide you guys with more information? Any replies would be greatly appreciated.

Thanks

---

### Post by Iowan on 2008-11-21
I don't have 8.10 installed yet, so I don't know if the Net Manager bug got fixed.  Check [this]("http://ubuntuforums.org/showthread.php?t=974382") workaround - maybe it will help.

---

### Post by Castarmax on 2008-11-22
I gave up. Apparently the problem was 2 fold. 1st The nVidia onboard nic card on the Striker Extreme MB,2nd was using a static ip. The workaround for the static ip worked so THANKS. Once I threw in a new nic card everything worked right off the bat including static ip's. Would rather not have 2 onboard nics plus a third but oh well...

---

### Post by Iowan on 2008-11-22
Search the forums - it's possible your nVidia onboard NIC needs a different driver.

---

