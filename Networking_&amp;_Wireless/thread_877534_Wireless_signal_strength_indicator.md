---
title: "Wireless signal strength indicator"
date: 2008-08-01
forum: Networking &amp; Wireless
---

### Post by mikex on 2008-08-01
I need an application to show me the signal strength I'm getting on my laptop. Is one available?

---

### Post by mb_webguy on 2008-08-01
When you click on the Network Manager applet to view the available networks, it should show the signal strength for each network, and once you connect, the applet icon should change from the standard networking icon to two dots (which turn from gray to green as you connect), and then to signal strength bars once you're connected.

*However*, on my computer, this is only true if I'm in roaming mode.  If I'm using a manual configuration, it shows the standard networking icon all of the time.  I have no indication of signal strength, and have to open up the System Monitor to even know when I'm connected.  It's pretty inconvenient.  I was actually about to create a thread about it when I noticed this one...

---

### Post by pytheas22 on 2008-08-01
If you left-click on Network Manager (the applet in the top-right corner of the screen that looks like two computer screens when you're not connected wirelessly), it will show a list of wireless networks in range and a bar to indicate their signal strength.

You can also type at a command line:
```

iwlist scan
```

and it will give you a list of networks in range in the format below, including a line telling you the signal strength (in bold):

Cell 01 - Address: 00:18:4D:56:7D:C8
                    ESSID:"NETGEAR"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    **Quality=21/70  Signal level=-74 dBm  Noise level=-95 dBm**
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

Keep in mind that there are still some wireless cards that have issues reporting signal strength on Linux.  If you think the reports you're getting are inaccurate, let us know which card you have and maybe there's a way to solve the problem.

---

### Post by cdtech on 2008-08-01
I just use this command:
```
iwconfig wlan0 | sed 's/  /\n/g' | grep Quality | sed 's/Link Quality://' | sed 's/Link Quality=//' | sed 's/ //g'
```

and use conky to display to status on my desktop.

---

### Post by elundmark on 2012-04-28
wavemon (terminal app)
```
sudo apt-get install wavemon
```
[IMG]http://elundmark.se/filer/wavemon.jpg[/IMG]

---

### Post by Rhizoid on 2013-01-14
A slight addition to the second answer, but which makes it a little easier to read:

```
sudo watch -n 1 "iwlist wlan0 scan | grep -e Quality -e ESSID -e Mode"
```Using the -e <pattern> option with grep you can report just the output of iwlist which you wish to see, a fair proportion of it on my system was less use than Pope's testicles :)

Output looks like:

```
Every 1.0s: iwlist wlan0 scan | grep -e Quality -e ...  Mon Jan 14 09:28:46 2013

                    Quality=89/100  Signal level=89/100
                    ESSID:"GET ORF MY LAN"
                    Mode:Master
                    Quality=47/100  Signal level=47/100
                    ESSID:"BTHomeHub2-5X7S"
                    Mode:Master
                    Quality=47/100  Signal level=47/100
                    ESSID:"BTWiFi-with-FON"
                    Mode:Master
                    Quality=47/100  Signal level=47/100
                    ESSID:"BTWiFi"
                    Mode:Master
                    Quality=13/100  Signal level=13/100
                    ESSID:"Espace"
                    Mode:Master

```Wavemon works well - if it's just a quick look you're after then the above doesn't need an install.

---

