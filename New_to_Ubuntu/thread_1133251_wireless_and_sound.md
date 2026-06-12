---
title: "wireless and sound"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by crabclaw on 2009-04-22
I'm fairly ubuntly challenged and so when I was installing ubuntu on a friends computer (conversion no.3) and it automatically updated into ibex I was prepared to reinstall from scratch. Having given it a look I think the tweaks involved are really exceptional and I'm close to returning the computer except for 2 issues which need adressing:

[LIST=1]
[*]the wireless card doesn't seem to be recognised automatically and I don't know how to find out what hardware is on the computer. I know the wifi is working and the wired connection works perfectly.
[*]The sound is incredibly low & I know it should be louder
[/LIST]

I have googled the issue but the explanations tend to be quite complex with tech terms I need to research that potentially (read: do) lead to mistakes. If I need to reinstall ubuntu using an earlier version I will only I really like the look & feel of ibex and want my friend to enjoy conversion as much as I do.

Thanks.

---

### Post by anewguy on 2009-04-22
Let's start at the easier stuff first:

- open a terminal window (you do that by clicking on Applications in the top menu bar, then on Accessories from the menu that drops down, then over and on Terminal).

- type the following, and for each do a copy/paste of the output to a new reply here so we can see them:

- lspci <press enter>

- lsusb <press enter>

- lshw <press enter>

These will allow us to see more about the hardware, so we can get a stating point.

Thanks!
Dave :)

---

### Post by crabclaw on 2009-04-22
alright the replies were quite long so I stuck 'em in pastebin.

lspci:
[http://pastebin.com/m70869dd9]("http://pastebin.com/m70869dd9")

lsusb:
[http://pastebin.com/m2a11afd9]("http://pastebin.com/m2a11afd9")

lshw:
[http://pastebin.com/m41e69c01]("http://pastebin.com/m41e69c01")

---

### Post by crabclaw on 2009-04-22
some additional information:
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=12 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```




ifconfig:
[http://pastebin.com/m7d248374]("http://pastebin.com/m7d248374")

route -n:
[http://pastebin.com/m512f955d]("http://pastebin.com/m512f955d")

---

