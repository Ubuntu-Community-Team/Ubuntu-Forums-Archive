---
title: "WiFi suddenly stopped working 18.04 LTS"
date: 2018-07-28
forum: Networking &amp; Wireless
---

### Post by isolated-thinker on 2018-07-28
Greetings!

I was trying to download and install an app from the Ubuntu store, when suddenly, my laptop showed that I was disconnected from my Wifi, and the install froze at 75%. I had to force shutdown and reboot.

My laptop now shows that I am connected to my wifi, however, I have ZERO data traffic.

As far as I can tel, all my settings are good, as far as I can see using the GUI. Terminal commands to check status is still a bit beyond me aside from basic installing and updating.

Any ideas?

thanks!

---

### Post by NM5TF on 2018-07-28
open a terminal and please post the output of

```
ip link
```

it should look something like this....

```
[tommy@tommy ~]$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp0s2f1u9: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 80:1f:02:b6:d2:ce brd ff:ff:ff:ff:ff:ff

```

line number 2 is the status of my wifi dongle.....the keywords to look for are [COLOR="#FF0000"]BROADCAST & UP[/COLOR].....this shows that the wifi
interface is recognized & operational....

---

### Post by isolated-thinker on 2018-07-29
> **NM5TF said:**
> open a terminal and please post the output of

```
ip link
```

it should look something like this....

```
[tommy@tommy ~]$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp0s2f1u9: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 80:1f:02:b6:d2:ce brd ff:ff:ff:ff:ff:ff

```

line number 2 is the status of my wifi dongle.....the keywords to look for are [COLOR=#FF0000]BROADCAST & UP[/COLOR].....this shows that the wifi
interface is recognized & operational....

Here is the screenshot from my laptop. Most of it, I guess, looks ok?
[IMG]https://uncommongeek.files.wordpress.com/2018/07/screenshot-from-2018-07-28-23-58-49.png[/IMG]

---

### Post by isolated-thinker on 2018-07-29
bump

---

### Post by howefield on 2018-07-29
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by Autodave on 2018-07-29
I don't know if this will help or not, but it is easy to do and ALWAYS the first thing that I try when I get a laptop that all of a sudden had some component stop functioning:

  	 	 	 	   1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by isolated-thinker on 2018-07-29
> **Autodave said:**
> I don't know if this will help or not, but it is easy to do and ALWAYS the first thing that I try when I get a laptop that all of a sudden had some component stop functioning:

                        1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

Thank you for the suggestions.

I attempted these steps with zero improvement in the situation.

The laptop, a Dell Vostro 2420, still is able to connect to my router, but still has no data transfer. 

All of my other wireless devices are not affected.

I believe this issue may be software related, and would rather not reload the OS if can be helped.

---

### Post by Autodave on 2018-07-29
OK. Then boot the laptop from a USB stick or DVD and see if the wifi works. If it does, then you know it is software. If it doesn't, then you know that the wifi adapter probably died.

---

### Post by praseodym on 2018-07-29
Please run the wireless script from the sticky thread and show the outputs

---

### Post by NM5TF on 2018-07-29
please print the result of

```
journalctl -xe
```

please use code tags for the output as they make it easier to read...go to advanced tab & use the [COLOR="#FF0000"]#[/COLOR] icon to insert
you answer

did you ever verify that dhcpcd is installed or not ???

tommy

---

### Post by isolated-thinker on 2018-08-01
Everything I tried did not work...

I performed a test where I connected my laptop to my Ethernet cable and made sure I had data connection. I then used a wwifi dongle I have and waited for it to load and connect to my wifi.

I had Zero data connection through the dongle.

I reloaded 18.04 and I now have 100% wireless data connection and transfer.

So, now I question is this...

Is there ANYTHING I can do software wise to prevent this from continually happening? I hardly install anything unless I need it which makes me fairly certain that I'm not unknowingly doing something wrong... :confused::confused::confused:

---

### Post by NM5TF on 2018-08-01
we are glad it is now working for you.....

but without knowing for certain what caused the problem in the first place, there is no way to guarantee it won't
happen again....my best guess is it had to do with the missing [COLOR="#FF0000"]dhcpcd[/COLOR] you mentioned earlier....this was resolved
when you reinstalled 18.04.....only a guess, but it seems to fit...

please mark the thread SOLVED by using the "thread tools" in upper right corner of first post....

tommy

---

