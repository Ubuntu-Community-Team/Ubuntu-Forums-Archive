---
title: "Wired Connection"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by kjhud on 2008-04-04
I have ubuntu on the ps3 and I can't get any kind of internet connection. I tried putting in the information manually but nothing happens. Can anyone help? I just need this so I can install updates and fix my resolution and bluetooth.

I have a ethernet cable from my ps3 to my ISR but it shows as no connection and it doesn't show my wireless card either. it is a pain for me to work because of my resolution is split in half and then flipped. Help?

---

### Post by kjhud on 2008-04-04
I have ubuntu on the ps3 and I can't get any kind of internet connection. I tried putting in the information manually but nothing happens. Can anyone help? I just need this so I can install updates and fix my resolution and bluetooth.

I have a ethernet cable from my ps3 to my ISR but it shows as no connection and it doesn't show my wireless card either. it is a pain for me to work because of my resolution is split in half and then flipped. Help?

---

### Post by tamoneya on 2008-04-04
I wasnt aware that you could install ubuntu on a PS3 but please post the results of ifconfig

---

### Post by neurostu on 2008-04-04
when you type in a terminal:
```

ifconfig

```
what do you get?

---

### Post by kjhud on 2008-04-04
i think i have tried to type ifconfig in terminal and nothing happened, i will try again.

---

### Post by kutjara on 2008-04-04
> **tamoneya said:**
> I wasnt aware that you could install ubuntu on a PS3 but please post the results of ifconfig

Yellow Dog Linux is the "official" distro for the PS3 (or at least the one IBM recommends for use with its Cell processor), but a number of people have installed other versions. I've got YDL on my PS3 and it works pretty well (even recognizing my Logitech wireless keyboard). It also sets up networking (wired and wireless) correctly. Loathe as I am to recommend another distro, YDL may be the easier route if you can't get Ubuntu to behave.

---

### Post by kjhud on 2008-04-04
When I type ifconfig, it gives me nothing. I just get:

kenny@localhost:~$ ifconfig
kenny@localhost:~$

---

### Post by kjhud on 2008-04-04
> **tamoneya said:**
> I wasnt aware that you could install ubuntu on a PS3 but please post the results of ifconfig

When I type ifconfig, it gives me nothing. I just get:

kenny@localhost:~$ ifconfig
kenny@localhost:~$

---

### Post by kjhud on 2008-04-04
Well I have ubuntu on my desktop, laptop and on an external HDD. I just didn't want to put something new on it. I am just having issues getting started and the issues are with the main things I need as in internet, resolution and my bluetooth mouse/keyboard. I can't get any of that right on my PS3.

---

### Post by kutjara on 2008-04-04
> **kjhud said:**
> Well I have ubuntu on my desktop, laptop and on an external HDD. I just didn't want to put something new on it. I am just having issues getting started and the issues are with the main things I need as in internet, resolution and my bluetooth mouse/keyboard. I can't get any of that right on my PS3.

I can totally understand wanting to stay with Ubuntu. I just suggested YDL as a sort of path of least resistance. Hell, if nothing else, you can poke around in the networking settings to figure out how to set up your Ubuntu config files. :)

edit: FYI, YDL requires that video input to the TV be via HDMI. Your resolution problems may be related to that. Just food for thought.

---

### Post by kjhud on 2008-04-04
Ok I searched elsewhere i found that i had to type "sudo ifconfig eht0 up" and then "ifconfig"

eth0 link cap: ethernet  HWaddr 00:1D:19:7A:43
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        Rx packets:1 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:- txqueuelen:1000
        RX bytes:460 (460.0 b) TX bytes:0 (0.0 b)
        Interrupt: 29

---

### Post by kjhud on 2008-04-04
Ok I searched elsewhere i found that i had to type "sudo ifconfig eht0 up" and then "ifconfig"

eth0 link cap: ethernet  HWaddr 00:1D:19:7A:43
        UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
        Rx packets:1 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:- txqueuelen:1000
        RX bytes:460 (460.0 b) TX bytes:0 (0.0 b)
        Interrupt: 29

---

### Post by kjhud on 2008-04-04
> **kutjara said:**
> I can totally understand wanting to stay with Ubuntu. I just suggested YDL as a sort of path of least resistance. Hell, if nothing else, you can poke around in the networking settings to figure out how to set up your Ubuntu config files. :)

edit: FYI, YDL requires that video input to the TV be via HDMI. Your resolution problems may be related to that. Just food for thought.
I had no clue what you mean about the config files but I have m ps3 through HDMI and I have a 1080p HDTV. The first time I could only get 480 and 576? to work and now I can get other resolutions to work but the are cut in half and then flipped, but I just need internet right now so I can go through updates and then I will work on the bluetooth and then the resolution.

---

### Post by Crafty Kisses on 2008-04-04
> **kjhud said:**
> I have ubuntu on the ps3 and I can't get any kind of internet connection. I tried putting in the information manually but nothing happens. Can anyone help? I just need this so I can install updates and fix my resolution and bluetooth.

I have a ethernet cable from my ps3 to my ISR but it shows as no connection and it doesn't show my wireless card either. it is a pain for me to work because of my resolution is split in half and then flipped. Help?

Try this:
```
ifconfig
```
Then you might also want to try this:
```
ping google.com
```
To see if you're getting an actual internet connection.

---

### Post by kjhud on 2008-04-04
iwconfig=

lo        no wireless extnesions.
eth0   no wireless extensions.


ping google.com=

ping: unknown host google.com

---

### Post by Crafty Kisses on 2008-04-04
> **kjhud said:**
> iwconfig=

lo        no wireless extnesions.
eth0   no wireless extensions.


ping google.com=

ping: unknown host google.com
You have a DSL connection, right?

---

### Post by kutjara on 2008-04-04
> **kjhud said:**
> I had no clue what you mean about the config files but I have m ps3 through HDMI and I have a 1080p HDTV. The first time I could only get 480 and 576? to work and now I can get other resolutions to work but the are cut in half and then flipped, but I just need internet right now so I can go through updates and then I will work on the bluetooth and then the resolution.

I was just suggesting that, if you can't find out what you need to know from the forums, you might be able to figure it out by installing YDL and looking at how it configures networking. You could then apply those settings to Ubuntu. It's a bit of a long-winded way of doing things, I know, but if nothing else works, you might consider it.

---

### Post by kjhud on 2008-04-04
Yes and my connection is fine, I am on a laptop right now, the ps3 was just on the internet from the Sony OS before i loaded ubuntu. the ps3 has a wireless and ethernet card and i can use either one if a certain one is easier to get working. 

I click on the Network icon in the tray and it says "no network devices" and I have to do a manual configuration and only shows the wire connection or the dial up option.

---

### Post by neurostu on 2008-04-04
I personally don't have any experience with Ubuntu on the PS3 but I'm sure that lots of people have gotten it working in the past. You might want to consider looking for some Ubuntu PS3 forums as undoubtably people there will already have faced and solved this problem...

just my 2 cents.

---

### Post by kjhud on 2008-04-04
it is a ps3 but i just thought that it is still a computer lol can you recommend any websites?

---

### Post by neurostu on 2008-04-04
Right, I understand that a PS3 is still a computer but unlike most computers it probably doesn't carry mainstream hardware and the configuration might be a little more difficult, but totally doable.

I did a simple google search for "PS3 ubuntu" and this was the first hit
[https://help.ubuntu.com/community/PlayStation_3](https://help.ubuntu.com/community/PlayStation_3)

Here is another guide I found:
[http://news.softpedia.com/news/Ubuntu-7-10-on-PS3-73272.shtml](http://news.softpedia.com/news/Ubuntu-7-10-on-PS3-73272.shtml)

Google is your friend!

---

### Post by kjhud on 2008-04-04
Ok well I have been messing around all that I can do with my knowledge and I put the following as a static ip setup

IP: 192.168.1.222
Subnet: 255.255.255.0
Gateway: 192.168.1.254
Domain: gateway.2wire.net
DNS Server: 192.168.1.254
Search Domains: gateway.2wire.net
Hosts: 127.0.0.1 and 192.168.1.222

Now i might have put in some repetitive info but I was just trying to fill in the blanks. I now have internet but the icon still has a ! over it and when i click on it it still says no network devices. I guess this is ok for now but it isn't perfect... Now to work on the resolution and Bluetooth :-(

---

### Post by kjhud on 2008-04-04
Ok well I have been messing around all that I can do with my knowledge and I put the following as a static ip setup

IP: 192.168.1.222
Subnet: 255.255.255.0
Gateway: 192.168.1.254
Domain: gateway.2wire.net
DNS Server: 192.168.1.254
Search Domains: gateway.2wire.net
Hosts: 127.0.0.1 and 192.168.1.222

Now i might have put in some repetitive info but I was just trying to fill in the blanks. I now have internet but the icon still has a ! over it and when i click on it it still says no network devices. I guess this is ok for now but it isn't perfect... Now to work on the resolution and Bluetooth :-(

---

