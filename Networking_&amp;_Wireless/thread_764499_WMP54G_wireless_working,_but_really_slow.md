---
title: "WMP54G wireless working, but really slow"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by sebast on 2008-04-23
Hi,

I'm trying to set up Ubuntu correctly on a friend's computer but I'm having troubles. I had the same troubles with 7.10 but just gave up so my friend continued to use windows but now I'm giving an other try.

In Ubuntu 7.10 as well as 8.04, the wireless in the Linksys WMP54G is detected and works out of the box, but is really slow so it's a pain in the ***.

Works well under windows. Any ideas why I get a slow connection?

Thanks

---

### Post by nicedude on 2008-04-24
You need to post some more info for anyone to help you. For starters answer the following so me or anyone else can get a good idea of what could be wrong.

Copy and paste the following one at a time into a terminal and post results of these.

iwconfig

lshw -C network

Also are you using wep or wpa encryption?

You could also try to give a little more description of the speed your receiving. And last you could try installing wifi radar and see if it manages your connection better. Below is a command to install wifi radar if you dont know how to find things to install.

sudo apt-get install wifi-radar

Just post the info back and someone will give you some idea what is going on here.

---

### Post by sebast on 2008-04-24
Sorry about the lack of info, here it goes:

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"charles"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:F4:A8:16   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=49/100  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 19
       serial: 00:17:31:15:dd:83
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: wmaster0
       version: 00
       serial: 00:18:f8:29:34:29
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.0.100 latency=64 module=rt61pci multicast=yes wireless=IEEE 802.11g
```

And the network is using no encryption at all for now. The wireless card is pretty popular so it should work fine, I really don't know why it's so slow. I seem to get bursts of full speed immediately followed by a really slow connection. Therefore, the connection seem instable.

---

### Post by shivans on 2008-04-25
I've got exactly the same issues with my Netgear wireless router. Download speeds are around 15kbps. I'm paying for a 20mb cable broadband service with download speeds of around 2000+kbps

I'm at work so can't post the same info above but I'll be interested to find a resolution.

I installed Hardy last night and everything works perfectly except for the wireless. I booted back into XP to make sure it wasnt my connection, but normal service was resumed in XP.

After reading various posts, some suggest using the OpenDNS config, which didn't work for me. I also disabled IPv6 to no effect.

Its a shame, because this version of Ubuntu is working like a charm except for this major problem.

---

### Post by JacksonL on 2008-04-27
I'm having this same problem with Hardy right now as well. I'm also using a Linksys WMP54G on an unencrypted network. My download speeds average around 40 kB/s while the other (Windows) computers on my network are able to download at speeds up to 300 kB/s. It's a little bit disconcerting.

---

### Post by sebast on 2008-04-28
The fact that this problem is there since Ubuntu 7.10 is concerning too, this card should be popular enough to be tested on a lot of configurations.

---

### Post by Keets on 2008-04-28
I posted this somewhere else, and like I said there, I don't know if this will help. It worked for me, though (rt2500) ; maybe it will work for you. 

Somehow, from what I understand, the Bit Rate defaults to 1Mb/s, which your "iwconfig" showed. So, I changed mine to 54M by the following command - 

"sudo iwconfig wlan0 rate 54M"

The only thing is, it doesn't "stick"; you have to enter it every time you power up. At least that's been my experience. 

* Worked for me, hopefully it'll work for you....

---

### Post by kevdog on 2008-04-28
Might want to try a different driver such as the serial monkey version.

---

### Post by shivans on 2008-04-28
> **kevdog said:**
> Might want to try a different driver such as the serial monkey version.

Yeah, the problems I had were resolved in this post...

[http://ubuntuforums.org/showthread.php?t=766724](http://ubuntuforums.org/showthread.php?t=766724)

---

### Post by RussellWing on 2008-05-12
Simply changing the bit rate to 54M worked for me too (RaLink RT2561/RT61 802.11g PCI). No other changes were needed.

To make it stick you can do this:

Make a script that can be called as part of the start up process (S99local is the conventional name for machine specific scripts that are not part of the distro):
> sudo nano /etc/init.d/S99local

Copy in this line (you may need to change wlan0 to wlan1 or eth0 etc):
> iwconfig wlan0 rate 54M
Use CTRL-O to write out, then exit with CTRL-X

Now make the script executable:
> sudo chmod 755 /etc/init.d/S99local

Next update so that the script will be called as the last thing for runlevels 2-5
> sudo update-rc.d S99local defaults 90

See [this for more info]("http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Forums_FAQ#How_can_I_make_Ubuntu_execute_a_script_or_program_at_startup.3F") on run levels and scripts

---

