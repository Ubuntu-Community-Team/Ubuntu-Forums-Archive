---
title: "Wireless Connection Speedtest results. Help :("
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by kestal on 2008-09-14
I was curious to see how my XP and Ubuntu compared with one another. I checked XP and it was 6.5-6.8Mbps (Download) (8 tests), then I checked on Ubuntu and it was 1.3-1.6Mbps.

What went wrong? Is this 'normal'? I didn't really notice it until I tried to download a few things.

I am using a Linksys WRT54G v5 and I connect using Network Manager (with a WEP hex password key). I use the Linksys WMP54G Wireless-G PCI Adapter. (Everything seemed to work fine out of the box).

On a previous version, I had normal, if not better speeds than what I had in XP/Vista.

I did have to remove network manager (but reinstall it) in order to get rid of the buggy shut down which a lot of people complain about.

System Specs:
- AMD 2.6ghz Dualcore (Black)
- 4gb of Ram (not all 4 being used by Ubuntu 32bit, obv.)

Any ideas?

---

### Post by kestal on 2008-09-14
Anyone?

---

### Post by caljohnsmith on 2008-09-14
What driver are you using for your wireless card in Ubuntu? Also, what type of internet connection do you have--is it cable or DSL? I ask because I'm thinking that possibly your MTU (TCP Maximum Transmission Unit) might not be optimally set in Ubuntu and you might be getting packet fragmentation or something. Also, please post the output of:
```
ifconfig
iwconfig
```

---

### Post by kestal on 2008-09-14
im on Cable. (Provider: Rogers Cable). I have been using them for years and I think I have a 6-7mbit connection with them after being a loyal customer.

I am on a wireless router though this is the first time I noticed this problem.

**[COLOR="Red"]Ifconfig:[/COLOR]**

eth0      Link encap:Ethernet  HWaddr 00:22:15:b4:09:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3613398768 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:221 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:258500 (252.4 KB)  TX bytes:258500 (252.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:8d:5d:a1  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe8d:5da1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10531843 (10.0 MB)  TX bytes:1281531 (1.2 MB)

**[COLOR="Red"]iwconfig:[/COLOR]**

wlan0     IEEE 802.11g  ESSID:"linksys_sokalski"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:14:BF:C8:05:C4   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=88/100  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Odd.. iwconfig shows me at 1mb/s.. could I have configured something incorrectly? Unfortunetely, due to a neighbour, I am forced to use a WEP/password with my wireless router (as they like to leech off my net and download beyond my limit).

Not trying to be disconcerning, but I do miss 600kb+/sec download speeds :(

---

### Post by caljohnsmith on 2008-09-14
Yes, the fact that your wireless card is connected to your WLAN at only 1 Mb/s is definitely a problem. So what wireless driver are you using in Ubuntu? Do you use ndiswrapper? Also, please post:
```
sudo lshw -C network
```

---

### Post by kestal on 2008-09-14
Hmm.. From out of the box clean install, I did not install any drivers for Internet. Wireless worked out of the box. I assume that now may be what the problem is... I did not use Ndiswrapper.
[B][COLOR="Red"]
lshw -C network:[/COLOR][/B]

```
  *-network
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wmaster0
       version: 01
       serial: 00:12:17:8d:5d:a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.1.101 latency=64 module=rt2500pci multicast=yes wireless=IEEE 802.11g


```

Is Ubuntu not detecting the right wireless properly?

I know that for XP I just used Atheros drivers to get my wireless running smoothly...

Could me uninstalling Network Manager (and reinstalling) effect something? I did it because during logout procedures I was getting the ubly logout sequence with text.

---

### Post by kestal on 2008-09-14
Edit: Nvm... didn't fix it.

---

### Post by caljohnsmith on 2008-09-14
So what did you do to fix it?

---

### Post by kestal on 2008-09-14
> **caljohnsmith said:**
> So what did you do to fix it?

I thought I fixed it. Before I had a manual connection because I removed/re-added Network Manager (to fix the pam-keyring bit), but ticked roaming back on and restarted. (just to test it out). I then filled out my WEP password upon loadup (after Ubuntu asking for my keyring), tested Speedtest and had over 6.4mb/s. Posted on here. Checked again, and it was down to 1.2.

I just restarted my pc again and my iwconfig right now shows 54mb/s which is what it should be, but I fear that it'll die off again soon.
```

wlan0     IEEE 802.11g  ESSID:"linksys_sokalski"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:BF:C8:05:C4   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=88/100  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Right now, it seems stable though, at 54mb/s between router and wireless PCI.. which is good. Before it was 1mb/s.

However, the pam-keyring problem is now back, same with the ugly error-filled (flashes for less than a second) start up before booting into the human background.

---

### Post by kestal on 2008-09-14
*sigh*

Bit Rate=1 Mb/s again.
Though speedtest shows 3.2Mbps

Edit:

Speedtest back to 0.8Mbps now on download.


Basically my wireless keeps fluctuating. Sometimes its where it should be, other times its pretty horrible. Any ideas what could cause it?

---

### Post by caljohnsmith on 2008-09-14
I did a quick search on your RT2500 wireless chipset, and there wasn't any clear easy solution that stood out that I could find; it seems others have had exactly your speed issue with the rt2500pci driver you are using, but some have used ndiswrapper while others have done workarounds to get the rt2500pci driver working. I would suggest searching the forums yourself and seeing what you come up with. Also, two of the forum members who are most experienced and knowledgeable at troubleshooting wireless issues are Ayuthia and pytheas22. You might want to try PMing either of them as I think they are usually friendly about that kind of thing. Anyway, good luck, sorry I can't be of more help.

---

