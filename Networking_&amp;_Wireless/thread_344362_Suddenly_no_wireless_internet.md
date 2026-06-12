---
title: "Suddenly no wireless internet"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by LeslieL on 2007-01-22
As usual I'm in the middle of experimenting with desktops, etc. Yesterday I tried out Ubuntu Edgy; today I'm playing with Kubuntu Edgy.

Yesterday the wireless Internet connection was working great (that's how I downloaded the Kubuntu ISO). This morning it wasn't. That was under Gnome. So I installed Kubuntu and updated it using an Ethernet cable, assuming when everything was settled down I'd get the wireless back. 

No such luck. I have wireless Internet when I'm running Windows XP, but switch  to Kubuntu - gone! But I can see and interact with the rest of the local network just fine, and everything looks good when I run the few check commands I know. For example: 

lshw (relevant part)
>        *-network:1
                description: Wireless interface
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 2
                bus info: pci@02:02.0
                logical name: eth1
                version: 05
                serial: 00:0e:35:aa:ea:8d
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 ip=192.168.2.30 multicast=yes wireless=IEEE 802.11b
                resources: iomemory:90000000-90000fff irq:5
           *-pcmcia


and iwconfig: 
> 
eth1      IEEE 802.11b  ESSID:"Craigallachie"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:01:24:F1:D8:97
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=-28 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


What's happening? Why no Internet when I have everything else?

To recap: The hardware is working. I have wireless Internet under Windows. I have only hard-wired internet under Kubuntu Edgy. This seems to be new. Why? What can I do about it?

---

### Post by Steiny1 on 2007-01-22
I see no replies to any of our inquiries.  Please let me know if you figure it out.  I just installed Edgy last night and have no idea what to do to get this working.

P.S. same situation, it works with Windows.

---

### Post by dmizer on 2007-01-23
@LeslieL,

you're probably getting stuck with ipv6 as a result of recent updates rather than your experimenting with kubuntu.  in /etc/modprobe.d/blacklist add the following at the end of the file:
```
blacklist ipv6
```
reboot, and you should be online.

@Steiny1,
please try to understand that everyone helping here is VOLUNTEERING their time.  while i well know that it's frustrating to not have questions answered (check my history and you'll see that i have many yet unanswered questions to problems i am even yet experiencing).

wireless does take some doing to get working sometimes, but browsing through some of the wireless threads will give you clues, and may even provide you with your answer.

---

### Post by LeslieL on 2007-01-23
Thank you, dmizer.

One of the reasons I'm an evangelical Linux user is the help I get from people like you. I knew someone would know what was going on and there would be help just hours after I asked the question. I appreciate what you more experienced users do for the rest of us (and I try to help when I can).

My only complaint about the forums is that I find it hard to search. That's probably why I missed Steiny1's question. It's frustrating because I'm a trained librarian and should be able to find things. I generally use Google to look for answers, even when I know they'll be in this forum. 

Anyway, thanks. I'm using the dreaded Windows now, but will try your solution as soon as I can.

---

### Post by LeslieL on 2007-01-23
It didn't work. Sounded likely, but it wasn't that. I'm going back to Dapper. Thanks anyway!

---

