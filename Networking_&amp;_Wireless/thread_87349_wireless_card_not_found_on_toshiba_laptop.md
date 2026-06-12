---
title: "wireless card not found on toshiba laptop"
date: 2005-11-07
forum: Networking &amp; Wireless
---

### Post by hunteramor on 2005-11-07
I have a Toshiba Satellite A-25 S-207 dual-booting XP and Ubuntu.  In XP, my wireless card works just fine, but it's not recognized at all in ubuntu.  the output of my ifconfig -a is:

> eth0      Link encap:Ethernet  HWaddr 00:00:39:EA:F1:D5
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:feea:f1d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61073 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:60197863 (57.4 MiB)  TX bytes:7869908 (7.5 MiB)
          Interrupt:11 Base address:0xed00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:73560245 (70.1 MiB)  TX bytes:73560245 (70.1 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


from reading on some forums, i think my card should be eth1.  it's not listed in system/administration/networking, either.

please let me know what other information i should supply in order to get on the path to getting my wireless working in ubuntu.

---

### Post by hunteramor on 2005-11-07
i should add that i don't really have a lot of information on what the card actually is.  in XP, it's described only as "Toshiba Mini PCI Wireless LAN," which doesn't seem very specific or helpful.

---

### Post by majed on 2005-11-08
You might need to use ndiswrapper to load the drivers for you..

Here is the how-to: [https://wiki.ubuntu.com/HowToSetUpNdiswrapper]("https://wiki.ubuntu.com/HowToSetUpNdiswrapper") & [https://wiki.ubuntu.com/SetupNdiswrapperHowto]("https://wiki.ubuntu.com/SetupNdiswrapperHowto")

I used it in Hoary and it worked.. u just might need to spend a little time trying things ;)

---

### Post by hunteramor on 2005-11-08
it says i should use the lspci command to find out which chipset my card is using.  here's the output for that command - which one is the one i need?  nothing is immediately jumping out at me.

> 0000:00:00.0 Host bridge: ALi Corporation: Unknown device 1672
0000:00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
0000:00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 33)
0000:00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)

---

### Post by mips on 2005-11-08
If you have a 802.11b card then it is probably Agere chipset.
If you have a 802.11a/b card then it is probably Atheros chipset, which is what I suspect you have.

---

### Post by hunteramor on 2005-11-08
should the fact that it's not showing up in lspci tell me something?

---

### Post by hunteramor on 2005-11-08
also, which atheros driver would you suggest?  i just installed two of them with the ndisgtk utility in the repositories and it's saying the hardware isn't present for both.

---

### Post by majed on 2005-11-08
There is no toshiba driver?

---

### Post by hunteramor on 2005-11-08
on [the list]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List"), there are only two mentions of toshiba.  one is a broken link, and the other looks like it was made for redhat only, i don't see any .inf files in the tar.gz

would it help if i posted the output of lsmod?

---

### Post by hunteramor on 2005-11-08
ok, on the spec sheet for the laptop the card is described as:
Integrated Wireless (802.11b) LAN

on the toshiba driver download page, the two options are:

  Atheros 802.11a/b/g WiFi driver with Cisco/WPA support for Windows XP/2000 (v2.4.2.14; 11-11-2003; 3.72M)
	Download atheros_wpa_driver.exe
and 

  Atheros WiFi Client Utility with Cisco/WPA Support for Windows XP/2000 (v2.4.2.18; 11-11-2003; 4.66M) 
Download atheros_wpa_client.exe

the driver one is a self-extracting zip file.  it includes a file called net5211.  i'd previously gotten a file of that name from 'the list' and installed through the old ndiswrapper.

i'm going to try compiling ndiswrapper from source

---

### Post by hunteramor on 2005-11-08
ok, i was able to install what i'm pretty confident now is the correct driver, but when i do ndiswrapper -l, i see:

Installed ndis drivers:
net5211 driver present

it's not detecting the hardware.  any suggestions?

---

### Post by majed on 2005-11-09
what i did was look for the right .inf file in my windows partition then copy it and install it for ndiswrapper.. after that i made sure ndiswrapper is configured and registered and all, rebooted, and then i could see my card in the networking admin wizard and i could configure it and use it.. 

good luck!

---

