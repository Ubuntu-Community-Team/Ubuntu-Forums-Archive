---
title: "Everything seems to work, but?"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by meepy on 2006-07-18
Hi everyone.

I am having a couple of problems with my wireless connection. Everything on Windows works as it should, and it LOOKS like it should work on Ubuntu aswell. But it dosen't. Can anyone tell me whats wrong?

This is what I have,

```
meep@meepy:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:DE:AE:E4
                    ESSID:"Hartmann"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:224  Signal level:0  Noise level:100
                    Extra: Last beacon: 8ms ago

meep@meepy:~$

```

And this is what my iwconfig looks like;

```
meep@meepy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     802.11b linked  ESSID:"Hartmann"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:DE:AE:E4
          Bit Rate=11 Mb/s   Sensitivity=80/85
          Retry:on   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-33 dBm  Noise level=-255 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

meep@meepy:~$

```

But how come I can not ping anything, as I can see it it SHOULD be working, but its like the connection is not default or something, so it can not be "used" - or I dont know, im a total newbie.

If I just plug the cable to eth0 everything works right on the spot. I have already tried using the "Networking" in the Gnome menu, and entered my WEP key and so, and still nothing - If you need any more info please ask for it and you should get it. Thanks!

---

### Post by tturrisi on 2006-07-18
wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:DE:AE:E4
                    ESSID:"Hartmann"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                   ** Quality:224  Signal level:0  Noise level:100**
                    Extra: Last beacon: 8ms ago

Those levels don't look right for some reason...

the below is from here: [http://www.stumbler.net/](http://www.stumbler.net/)

What signal level should I consider usable for a good wireless link?
Posted in FAQ by mariusm #
I get asked this question rather too often, so I'm posting my short answer here. The answer is rather more complex than it ought to be, and depends on a huge number of factors.

The most important is the receive sensitivity of your equipment. Many manufacturers fail to publish this data, but those that do will generally rate their radios by dBm at various data rates. As an example, let us take the venerable ORiNOCO Gold 802.11b "Classic" card. Its receive sensitivity is:

    * -94 dBm at 1 Mbps
    * -91 dBm at 2 Mbps
    * -87 dBm at 5.5 Mbps
    * -82 dBm at 11 Mbps

In theory this means, in order to operate at 11 Mbps, this card must be consistently receiving a minimum signal level of -82 dBm. Any less and it is likely to drop to one of the lower rates; if you get as low as -94 dBm then the connection may drop altogether. As I mentioned before, many manufacturers do not quote their receive sensitiviy for their adapters; if you have one of these, I suggest picking a conservative figure such as -76dBm at 11 Mbps, which is the number for the Belkin F5D6020.
The signal level you receive in an unobstructed environment depends on the transmitter power, the gain of the two antennas involved, and the distance between them, as well as any loss between the antenna and the radio at each end.

In practice, radio waves behave unpredictably in a number of ways. First, the signal will fade out due to multipath effects (radio waves that bounce off objects and increase or decrease the signal that you receive). The further the receiver is from the transmitter, and the more objects between them, the higher this effect will be. Walls, people, electronic equipment, rain/snow/ice/fog are all quite effective at decreasing your signal level. In a typical home or small office environment without too many obstructions, a 10dB variation in signal level is quite normal. So, if you are looking at a NetStumbler scan and the signal is consistently around -65 dBm, it could drop to -75 dBm when somebody comes over to talk to you.

Summary so far:
(Received signal) = (transmit power) - (loss between transmitter and antenna) + (transmit antenna gain) - (path loss) - (multipath and obstruction loss) + (receive antenna gain) - (loss between antenna and receiver)
In order to operate, (received signal) must be greater than (receiver sensitivity).

Another factor is noise. This is "background" radio-frequency junk that your receiver can "hear" but needs to reject. Sources of noise include other wireless networks, cordless phones, microwave ovens, radio hams, medical equipment, Like other radio phenomena, noise may be highly variable. Many wireless network adapters do not report noise, so if you're using NetStumbler with them then you can't even tell how much noise you have in your environment. A typical urban location these days might have an average noise level around -95 dBm. When you switch on the microwave oven or take a call on your 2.4GHz phone, this value will increase. I've seen a 2.4GHz phone produce -50 dBm of noise, which is enough to saturate some Wi-Fi radios and thus kill their connection completely.

Let's take these concepts and combine them. In order to operate, the actual signal level at your receiver needs to be higher than the noise level. The actual signal level varies depending on signal fade, so if you measured -75 dBm one day, it might drop to -85 dBm occasionally. On most radios this is sufficient to make it drop to a lower data rate, and on some it will cause the connection to drop altogether. Likewise your background noise might be around -98 dBm, but then your neighbor takes a call on her cordless phone and it jumps to -78 dBm. With multipath effects, this is sufficient to make your connection drop randomly.

My conclusion, therefore, is:
Q: What signal level should I consider usable for a good wireless link?
A: Depends on your equipment and your environment.

---

### Post by jamboarder on 2006-07-20
run "sudo dhclient wlan0"  in a terminal and see what happens.

---

