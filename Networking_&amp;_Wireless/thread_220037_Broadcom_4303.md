---
title: "Broadcom 4303"
date: 2006-07-20
forum: Networking &amp; Wireless
---

### Post by ubun00b on 2006-07-20
I have a bcm4303 chipset for my wireless adaptor inside a hp pavillion zx5000 laptop.  So far i've followed the directions from the following how-to's:

I've followed this one to the letter as far as i can tell yet no luck.
[http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://www.ubuntuforums.org/showthread.php?p=1071920&mode=linear)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)
In this one, i've followed the directions for Section 1.2 up to the point where it says "VERY IMPORTANT..." and i stop there because it gets into what appears to be editing of the /etc/network/interfaces file, which I've messed with some, but restored it to the original file.

At one point, when i did the sudo iwlist scan command, the following came back:

eth1      Scan completed :
          Cell 01 - Address: <edited>
                    ESSID:"<edited>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=100/100  Signal level=-182 dBm
                    Extra: Last beacon: 10ms ago
 
Additionally, the LED button on the keyboard for the wireless would "light up" for a few seconds and then drop off.  Now when i issue the sudo iwlist scan command, it comes back with:

eth1      No scan results

Yet the LED button on the keyboard still "lights up" everytime I do this for a few seconds and then shuts off.  Getting my hopes up temporarily and dousing them summarily.

My AP is broadcasting the essid and has no security settings (as to not add complication in the mix).  I've spent the past 3 days banging my head against a wall and with no luck so far.  I feel like im getting closer, but just missing the target.  Any luck would be greatly appreciated.  thanks!

---

### Post by ubun00b on 2006-07-20
UPDATE:

I can now get the card to scan and pickup the essid, but however it won't connect.  Am i missing the bigger picture?  Any help would be awesome.  Thanks in advance!

---

### Post by kaiyer on 2007-07-05
I have wireless networking on my HPO pavilion zx5000 working intermittently. I have dual boot.
When I start up windows, the radio button gets enabled via siftware.
If I then reboot and start up Fiesty UBUNTU, my ndiswrapper wireless config works. However the radio button is not on but only flashes when it goes to get data from the internet. 

However, when I shutdown the computer and start Fiesty, radio button does not turn on nor does wifi work.
Is there a way to turn on the radio button in fiesty during startup?

I have read many threads and applied the solutions to change the .conf files. 
Can you help or point me to a thread on this topic

thanks
K

---

