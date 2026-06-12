---
title: "Wireless-G 2.4GHz 802.11g pci linksys"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by bartfliet on 2007-04-15
So I got a Wireless-G 2.4GHz 802.11g pci adapter from linksys in my computer and I dual booted in Ubuntu, but how do I connect my computer in Ubuntu to the wireless router which is connect to the computer downstairs?

anyway, I asked on another forum (where they were unable to help me all the way) and they asked me to do this check

```
lspci | grep net
```

When I did that, I got this back

```
code:<pre>02:05:0 Ethernet controller :Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139

C+ (rev10)</pre>
```

Now my question is, how can I get it work?

and I'm absolutly noob ad this, so try to explain is step by step if possible...

thanks in advance

---

### Post by bartfliet on 2007-04-15
anybody?

---

### Post by DarkN00b on 2007-04-15
Type ```
iwconfig
``` into the terminal and place the output here. That should give us some idea of what you need to do. The output above shows your wired connection. Same chipset as me. :)

---

### Post by alexmoon on 2008-04-02
I also have this usb modem (I have an old laptop). It worked for a while, then I stopped using it, and now can't work out how to get it to connect to my home network again. The output of iwconfig is:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I'm trying to connect to a WEP 128-bit network.

Thanks for any advice you can offer.

---

### Post by alexmoon on 2008-04-08
is there any more information I could give that would help here? Or something I could try?

I can see the networks, but whenever I try to connect, it just times out.

---

### Post by dstew on 2008-04-08
Hi alex, you posted on an old thread, maybe that's why you are being ignored.

It sounds like a configuration problem. What do you see in the System --> Administration --> Network window?

---

### Post by alexmoon on 2008-04-27
Under 'Network Settings', I have Wireless Connection set to 'roaming enabled' (although there is a dash in the box next to it, not a tick, and clicking the box does nothing.)

Taking away roaming mode and putting the details of my home network does not seem to achieve anything apart from make the list of available networks disappear.

When I try to connect through network manager (click on the name of the home network, then put in the key) it gets to the 'Waiting for network key' stage, and then just hangs there. I've checked the key is right about 10 times, so it shouldn't be that.

When I try to connect through wifi radar, it seems to think I'm already connected: it says.. "Connected to None (IP address 127.0.0.1)", and the only option I have is a "Disconnect" button, which does nothing when I press it.

---

### Post by alexmoon on 2008-04-27
I've just updated to Hardy Heron, and wireless is now working fine! Hurrah!

---

