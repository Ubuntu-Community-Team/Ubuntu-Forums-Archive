---
title: "How to setup wireless"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by feest on 2007-09-12
Now, in the latest releas, wireless networking has become very easy in Ubuntu. However, I have 0 experiance and I don't seem te be able to help myself out. How do I setup my wireless lan (my intel proset is properly working since I've seen ubuntu wireless on my laptop) I have the following information available: (see atachment). Now, I don't blame Ubuntu for my trouble I blaim myself for not knowing anything about wireless networks.

Can somebody give me/make me a clear guided illustrated turorial about how to set up you network, and what to enter where...

Thanks in advance

~ Sven van de Scheur

---

### Post by feest on 2007-09-13
anyone? thought ubuntu was  known for it's good support, do I ask a very hard querstion?

---

### Post by spd106 on 2007-09-13
Try reading this help docs page.
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

It should be a simple case of selecting your networks name (ssid) from a list and entering the WEP key. Just make sure you have the correct key format selected, hexadecimal or ASCII.

---

### Post by feest on 2007-09-13
I'm affraid this won't help me, I've got feisty with that applet and I just don't know how to set my internet connection up.  Can somebody guide me through it?

(I did tried the tutorial though but it won't help me since it only describes how to setup the applet)

---

### Post by mojoman on 2007-09-13
Let's see if I understood the problem. You have a router up and running with a WEP encryption. You got a wireless modem on your computer with working drivers and you want to connect to the router. Is this it? Or is it the modem drivers that's giving you a hard time?

I'll try to chip in but I've got very little experience with wireless gui so it'll have to be through the terminal. 

First, what wireless devices do you have up and running? Find out by opening a terminal and type the following:

```
ifconfig
```
```
iwconfig
```

Then let's see what networks are available. In the terminal, type:
```
iwlist scan
```

Post the output of these three commands and perhaps I can figure out what is wrong.

/mojoman

---

### Post by feest on 2007-09-13
```

root@LinuLuuk:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:3F:08:3C:A8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:59:F7:AC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x2000 Memory:d0000000-d0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:327 errors:0 dropped:0 overruns:0 frame:0
          TX packets:327 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28749 (28.0 KiB)  TX bytes:28749 (28.0 KiB)

```

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"Sitecom"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:7069-617A-6F   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@LinuLuuk:~# 

```

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
root@LinuLuuk:~# 

```

I have no idea what this means..

the wifi card is an intel proset 2200 i think, i've seen wifi working on ubuntu on this machine...

---

### Post by mojoman on 2007-09-13
Hmm, I'm a bit concerned about iwlist scan giving the output that eth1 (your wireless) don't find any networks. This sounds odd. My pick up quite a lot but I suppose that depends on where you live (I get my neighbours networks as well...) .But you do have a working router that's up and running? Do you by any chance have the necessary information from the router, specifically channel, WEP-key, ESSID.

If you do, you could try to bring the card up manually by the following command.

```
fconfig eth1 up
```
```
iwconfig eth1 essid "YOUR-ESSID" channel "X" key "YOUR-KEY"
```
(of course, you enter whatever ESSID, channel and WEP-key you use)

Also, there is a configuration file that is important and might be of interest nad this is /etc/network/interfaces.

Could you post the contents of it?
```

cat /etc/network/interfaces
```
(If you're paranoid - I know I am - you might want to edit out some of the contents, such as the WEP key before posting it)

/mojoman

---

### Post by spd106 on 2007-09-13
This blog post suggests that you could have a hardware switch (or some other manufacturer dependant switch) in the off position.
[http://blog.preshweb.co.uk/2007/04/installing-intel-ipw2200bg-under-linux/](http://blog.preshweb.co.uk/2007/04/installing-intel-ipw2200bg-under-linux/)

---

### Post by feest on 2007-09-13
sorry, i don't have the time right now to follow all those steps but i found out the wireless led isn't on in ubuntu... altough, if i go to the hardware screen it is listed... but once again the led will never light up???

---

### Post by mojoman on 2007-09-14
> **feest said:**
> sorry, i don't have the time right now to follow all those steps but i found out the wireless led isn't on in ubuntu... altough, if i go to the hardware screen it is listed... but once again the led will never light up???

I read through the blog and I think that spd106 is right. I couldn't figure out the 'radio off' part in your iwconfig but this is the likely explanation. (Yes, I'm bad. I didn't Google.) If you follow the instructions in the blog you'll probably get it up and running. After that, you'll probably be able to configure the rest in graphical mode by just following common sense and intuition. If not, get back when you have time and well try some more then.

/mojoman

---

### Post by HokeyFry on 2007-09-14
try following the steps in the HOWTO in my signature

if you do try my HOWTO i suggest trying to use ndiswrapper as is before trying to compile it from source

---

### Post by mojoman on 2007-09-14
> **HokeyFry said:**
> try following the steps in the HOWTO in my signature

if you do try my HOWTO i suggest trying to use ndiswrapper as is before trying to compile it from source

But how will using a ndiswrapper take care of the problem with the hardware switch?

---

### Post by noob12 on 2007-09-14
The drivers are loaded and may be fine.   I wouldn't suggest ndiswrapper yet.

feest:
What make and model of laptop do you have?  Depending on the laptop, you may need to load a module or set an option on your wireless driver to recognize the wireless switch that enables the radio.  This is particularly true of Acer, AOpen/Tundra, but also several other brands.

Can you please run the command **lspci -nn**.  From the output find your 802.11 wireless ethernet device listed  and post that line?  If in doubt, post all of the output.

Can you please run **sudo lshw -C network**, find the configuration line for the wireless device and post what it says for the driver.

---

