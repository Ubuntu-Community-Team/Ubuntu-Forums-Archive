---
title: "[SOLVED] Limited to slow wireless download speed"
date: 2008-08-06
forum: Networking &amp; Wireless
---

### Post by moogleking on 2008-08-06
**See Reply #3 below**

Hi all,

I have been configuring and re-configuring Ubuntu 8.04 all this week and I love it. However, I've been having an extremely difficult time troubleshooting my slow wireless download speed. 

I know it's not my router or wireless card because the connection works fine in Windows Vista (see attachment). Also, my wired speed is fine in Ubuntu, and works at full speed. 

I am using a Dell m1210 laptop with an Intel Wireless Pro 3945abg card.

As far as drivers go, the wireless didn't work out-of-the-box, but after some research, managed to get my wireless working by using:

> sudo apt-get install linux-backports-modules-hardy-generic

The problem now is that all downloads (including browser activity to downloading packages) seems to be limited to around 16-20kb/s maximum. 

iwconfig brings up:

> 
wlan0     IEEE 802.11g  ESSID:"3SP"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:20:5C:6F   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=97/100  Signal level=-27 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The only error I see above is that I am running a 802.11b line, not G. 

I've done the following troubleshooting steps already to no avail:
- checked bitrate in iwconfig
- tested wireless speed in Vista and works fine
- used both the natively installed Network Manager and Wicd
- globally disabled ipv6 via:
> 
/etc/modprobe.d/aliases from
alias net-pf-10 ipv6
to
alias net-pf-10 off


Please help. I really love Ubuntu, and would hate to give up on it over this wireless slowdown. 

Included in attachments are my speed tests for wireless in Vista and Ubuntu Hardy Heron. 

Thanks

---

### Post by caljohnsmith on 2008-08-06
Moogleking, I have an interesting test you could run to get a clue if the problem is between your computer and your router or between your computer and the internet:
```
sudo ping -f -s 1400 -w 5 <router IP address>
```
Where <router IP address> will most likely be 192.168.1.1 or similar. What the above does is flood ping your router with a packet size of 1400+28=1428 Bytes, for a duration of 5 seconds. To find out the data transfer speed from the above test, do as in the following example:
```
john@TECH5321:~$ sudo ping -f -s 1400 -w 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 1400(1428) bytes of data.
.
--- 192.168.1.1 ping statistics ---
[COLOR="Red"]2077[/COLOR] packets transmitted, [COLOR="Red"]2076[/color] received, [COLOR="Red"]0% packet loss[/COLOR], time [COLOR="Red"]4997ms[/COLOR]
[COLOR="Red"]rtt[/COLOR] min/avg/max/mdev = 1.968/[COLOR="Red"]2.318[/COLOR]/10.531/0.513 ms, ipg/ewma 2.407/2.255 ms
```
First of all, you should have virtually no packet loss, and the "rtt" or round-trip time should be on the order of a few milliseconds like in the above example. To figure out the data rate:
```
2077 + 2076 packets * 1428 Bytes/packet * 8 bits/Byte / 5 seconds = 9.5 Mbits/s
```
Now that data rate includes the round-trip time for each packet, so we are not continuously sending and receiving data between the computer and router, which is what we would need to do to get a true data rate test. But if your data rate with the above example is really pathetic, say on the order of 100 kbits/s or less, you probably have a problem between your computer and router. If not, then your problem lies further upstream. Anyway, that should help you narrow down your problem hopefully.

---

### Post by moogleking on 2008-08-06
I seem to have fixed this problem!

Here's what I did:

1. Blacklisted the offending iwl3945 driver:
> sudo gedit /etc/modprobe.d/blacklist
added line: blacklist iwl3945

2. Installed ndiswrapper 1.5 via System > Admin > Synaptic Package Manager 

3. Downloaded and extracted the netw4x32.sys and netw4x32.inf files from [Dell's Intel Wireless PRO 3945ABG A12 driver]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R164255&SystemID=XPS_M1210&servicetag=&os=WW1&osl=en&deviceid=9540&devlib=0&typecnt=0&vercnt=7&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=220545")

(Intel's newest and Dell's A13 driver for the same component *did not* work!)

4.Installed the drivers: 
> sudo ndiswrapper -i /path-to-driver/netw4x32.inf
ndiswrapper -l (to verify if it installed drivers correctly)

5.Modified modules:
> sudo gedit /etc/modules
added line: ndiswrapper

sudo rmmod iwl3945
sudo modprobe ndiswrapper
sudo reboot

5. Configured WEP and connected! Went to DSLreports.com/speedtest and now my wireless speeds are normal! 

I hope this helps others who may have the same problem in the future.

---

### Post by djRif on 2008-08-18
hi there moogleking
I have been having the same problem since upgrading to Ubuntu 8.04. I am somewhat of a newbie to Linux and don't know how to extract those drivers from the A12 driver... Any directions on that are much appreciated.

Rif

---

### Post by djRif on 2008-08-18
Moogleking
Many thanks.. I was able to extract the files and install the driver... I am currently on Flores Island and have no wireless (but do have satellite wired connections) and will try it tomorrow when I return to the mainland. I'll let you know how it all worked. The wireless card is working however and all seems good. I can't wait to see if my problem with Hardy is fixed (at last!!!) after months of trying...

---

### Post by djRif on 2008-08-19
thanks! Wireless working like a charm with the windows drivers. Your solution made my life so much better!

---

### Post by moogleking on 2008-08-19
glad my posting helped,

regards

---

### Post by Jamikest on 2008-09-07
Thanks again, your post helped solve another wireless problem.

I was having normal upload rates, about 4-5 Mbits/s.
My downloads were about 500 Kbits/s.

A little research and I found that the native linux driver is problematic, so off to using a windows driver with ndiswrapper.

FYI, there is a graphical ndis configuration tool available through synaptic:  ndisgtk

Up and running full speed now, Thanks again!

---

### Post by mfb52 on 2008-09-07
Are there any known issues using ndiswrapper for this card? Any stability issues? Does it work with hibernation/standby?

---

### Post by virtualo on 2009-06-18
Thanks for the info... Used linksys driver with ndiswrapper and now my speed is great... Ping from 88ms to 7ms... Download from 300k to 5mbps... Many thanks

---

### Post by chekhovs1 on 2009-06-21
For my Lenovo T400 laptop with Intel 5350 AGN wireless a similar problem went away after installing the latest wireless drivers package, see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/211094/comments/18](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/211094/comments/18)

---

