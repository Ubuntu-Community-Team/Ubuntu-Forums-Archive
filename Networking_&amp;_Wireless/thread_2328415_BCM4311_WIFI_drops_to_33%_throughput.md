---
title: "BCM4311 WIFI drops to 33% throughput"
date: 2016-06-20
forum: Networking &amp; Wireless
---

### Post by DuckHook on 2016-06-20
I have an old Dell Latitude D830 with the BCM4311 WIFI chip running the ssb module and b43-pci-bridge driver on Xubuntu Xenial. When doing large transfers it drops to 220 kB/s after about 1 minute of heavy use (i.e. kernel upgrades). My connection from the ISP maxes out at 660 kB/s which the Latitude achieves through wired connection, so the problem does not appear to be with the router. Also, I routinely achieve maximum throughput with other WIFI devices like phones and tablets.

It almost feels as if some buffer in the BCM gets filled up within a minute's time after which the throughput gets hit hard. That's only a guess.

I've done a pretty extensive Google search but my Google-Foo has called in sick today. Can't find anything useful that bears on this problem, so am appealing to better minds than mine for help.

Wireless script results are in pastebin: [http://paste.ubuntu.com/17390780/](http://paste.ubuntu.com/17390780/)

or attached as compressed text file: [ATTACH]269685[/ATTACH]

---

### Post by jeremy31 on 2016-06-21
There are only two things I can think of.  Go into Network Manager for your wireless connection and set IPv6 to ignore and set your country code with
```

sudo iw reg set CA
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda

```

Everything else looks good, your wifi is on a channel by itself with CCMP encryption only.  If this still happens after a big download run the script again before rebooting, then we might find something in dmesg.

---

### Post by DuckHook on 2016-06-21
Thx, jeremy31. Am not close to the problem [S]child[/S] laptop right now, so will do these things and report tonight.

---

### Post by Hadaka on 2016-06-21
Hi, your current wireless report shows in "Dmesg"
```
#b43-phy0 warning: 5 GHz band is unsupported on this PHY
```
So, It may be a broadcom issue or a kernel issue,Jeremy31 has more knowledge
than i in that area. Mean time, try this..
```
echo "options b43 nohwcrypt=1" | sudo tee -a /etc/modprobe.d/b43.conf
sudo modprobe -r b43
sudo modprobe -vv b43
```
And as jeremy31 suggested set your IPv4 and IPv6 like the attached.
[ATTACH=CONFIG]269697[/ATTACH][ATTACH=CONFIG]269698[/ATTACH]

---

### Post by DuckHook on 2016-06-21
Firstly, thanks for the help, jeremy31 & Hadaka.

I have implemented the all of the suggestions above. Still no joy. Results of speedtest.net as follows:

Changes only to network manager (ignore IPv6, define DNS servers) and setting CA location:
1st run = 5.41 Mbps
2nd run = 5.45 Mbps
3rd run = 5.38 Mbps
4th run = 2.02 Mbps
5th run = 2.02 Mbps

After creating b43.conf, disabling hw encrypt, unloading/reloading b43 module but not rebooting
1st run = 3.90 Mbps
2nd run = 2.02 Mbps
3rd run = 2.05 Mbps

After reboot with all new settings
1st run = 5.62 Mbps
2nd run = 5.55 Mbps
3rd run = 1.98 Mbps
4th run = 2.08 Mbps

The drop in throughput occurs after a period of intense WIFI activity like watching a YouTube video (I've had more than my fill of Selena Gomez karaoke carpool). However, this is standard occurrence with all heavy downloads (epubs, music, photos, kernel updates) and not just YouTube.

I have attached a new wireless-info file run immediately after the last slowdown: [ATTACH]269702[/ATTACH] (sorry, foregoing pastebin this time)

I will reverse changes made so far since they are not the solution and I want to revert to a baseline.

*EDIT*

On a hunch, with further detective work: the following three lines show up at the end of dmesg, well after boot:```
[  233.274352] perf interrupt took too long (2509 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  395.546745] perf interrupt took too long (5003 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[  663.316562] perf interrupt took too long (10007 > 10000), lowering kernel.perf_event_max_sample_rate to 12500
```*FURTHER EDIT*

After Googling, this dmesg output seems pretty standard/innocuous and doesn't appear to have a connection to my problem.

---

### Post by Hadaka on 2016-06-22
DuckHook, your dmesg is saying that the wifi card is seen, and its information about it is
being received,and then gives a *warning., sorry, there is no 5GHz to attach to. soooo you
must have set your ac point..chowpad,,to 5 ghz, and you have no 5 ghz support.
##### dmesg #############################
[    5.572682] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[    5.634858] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[    5.634879] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[    5.634881] b43-phy0 warning: 5 GHz band is unsupported on this PHY

Here are your current channel and frequency choices...there is no 5GHz
##### iwlist channels ###################
wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.422 GHz (Channel 3) <- your current channel and freq.
So, with your b43 card,16.04 and not having 5GHz its not likely you are going to get
any better speed than you have. I would suggest changing the 5 ghz choice in the router.
keep us posted.

---

### Post by jeremy31 on 2016-06-22
See if disabling bluetooth with ```
rfkill block bluetooth
```
Helps any as I see a rather big number in ifconfig results under Invalid misc

---

### Post by DuckHook on 2016-06-22
> **Hadaka said:**
> ...you must have set your ac point..chowpad,,to 5 ghz, and you have no 5 ghz support...I would suggest changing the 5 ghz choice in the router.I use dd-wrt on an old Linksys router. It has no option for turning off 5GHz support except to set the wireless mode to "G only", which, by definition, operates only on the 2.4 GHz band. If there is a command-line option to set the frequency band, I am not aware of it, but will search the dd-wrt site and try Googling it.

> **jeremy31 said:**
> See if disabling bluetooth with ```
rfkill block bluetooth
```
Helps any as I see a rather big number in ifconfig results under Invalid miscDisabling bluetooth through software did not help, but it twigged me to try disabling through BIOS so that it is HW disabled. Still no joy. However, I don't want bluetooth anyway, to close off a security hole I had neglected, so thanks for serendipitously reminding me to carry out some needed housekeeping. I also tried disabling the BIOS cell module and a Dell feature called WIFI Catcher. None of those settings make any difference.

@Hadaka

I would resign myself to 2Mbps speeds (and might still do so in any case) if my laptop never reached more than that speed from the get-go. But it always achieves 5.4Mbps after a fresh boot and stays that way as long as I don't make any lengthy or taxing downloads. Therefore, I know that it is *capable* of the higher speed. I just don't know how to make it sustain that speed. Or perhaps more accurately, I don't know what is degrading that speed after a taxing download.

I'll leave this thread unsolved and will happily try solutions from all parties. Many thanks to both jeremy31 and Hadaka for your help. I really appreciate it and please don't feel obligated to spend more time than you want on this one. The laptop is functional. Just not optimal.

---

### Post by QLee on 2016-06-24
> **DuckHook said:**
> 
I'll leave this thread unsolved and will happily try solutions from all parties. Many thanks to both jeremy31 and Hadaka for your help. I really appreciate it and please don't feel obligated to spend more time than you want on this one. The laptop is functional. Just not optimal.

OK, since no one else is suggesting anything I will make some WAGs.

There are quite a few, Invalid misc:30331, shown in the second wireless text which you say is just after a problem download, might indicate impairment, I see you use channel 3 and there is a pretty strong signal on channel 1 which might be affecting your transmissions only two channels away. Do things change if you set your router to use channel 6? (Of course I don't see how impairment would only happen coincidently with a big download and I assume you've ruled out coincidence)

Another thing, that link local address shown as the IP4 route for the wireless card in the Network Manager info of the wireless text. I would expect it to be to the gateway address, assigned by DHCP from the router, rather than that link local address which I assume was assigned to the NIC which likely didn't have a cable plugged in when things were enumerated. I wonder if that metric of 1000 rather than 100 might affect the way the router handles the download and somehow cause a slowdown when it was on a big download. 
This is speculation on my part, I don't have the in-depth knowledge to say for sure that it could cause the symptoms you experienced. The others watching may be able to confirm or deny my speculation.

Your wireless card is listed as a dual-band card a,b,g, but clearly the messages indicate that it's only using 2.4Ghz. I wonder if the devices, phone and tablet that are getting the full throughput are using the 5GHz band.

Good Luck, Duck

---

### Post by DuckHook on 2016-06-24
Thanks for the suggestions, QLee.

I will try switching router channel to one of the other open ones to see if that helps.

Regarding your other questions, to my knowledge, all of a, b and g modes are in the 2.4 GHz band. Also, my router (Linksys WRT54G)  is physically incapable of operating in the 5 GHz band as it doesn't have the needed HW. Finally, the BCM4311 can't operate at 5GHz either and the B43 driver is not designed for N-band. Further Googling reveals that the 5GHz may be a mis-reference due to a driver bug and should be ignored.

Your reference to link local is above my head. I gather you are referring to the line:```
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
```...with the accompanying metric, but I don't know what significance this has, nor how to change or influence this setting. Googling tells me that link local is sort of like a fallback link when my system cannot resolve a DNS server, but aside from slow download speeds, everything else works. I can surf, ping, download and email out of the machine with full name resolution, so I don't know how this would impact my system.

---

### Post by QLee on 2016-06-25
> **DuckHook said:**
> I will try switching router channel to one of the other open ones to see if that helps.

Your reference to link local is above my head. I gather you are referring to the line:```
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
```

Yup, that was what I was referencing.

I suggest to try using channel 6 first.

One of the problems with WAGs is that sometimes they are Wild A... Wrong. <chuckle>.

I just look for what I think are anomalies. Most of this I didn't notice on my first reading of your wireless texts, when I didn't have any other ideas I reread more carefully.


In the iwconfig section of the second wireless text

```
 Link Quality=57/70  Signal level=-53 dBm  
 Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:319  Invalid misc:30331   Missed beacon:0

Compare that with the result from the interface on the computer I'm currently using

Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:20   Missed beacon:0
```

I see those retries and invalid misc and that's what made me wonder about impairment. Now, I may be closer to my router than you. 

If those figures mean that there is impairment then the loss of throughput might be due to having to ask for retransmission of a lot of packets.

I'm still bothered by that IPV4 route shown in the Network Manager info. I'm fairly sure that, that field has the gateway IP address in the other wireless texts I've read and I think that makes common sense too, I can't think why it would be to a NIC that wasn't connected. I wonder if that is somehow left over from when you had the system hardwired for testing.

This is interesting enough that I wish I was in the meatspace room with you to test this rather than virtually. I hope you do find something, it would satisfy my curiosity too.

Any other devices in your location not related to computing operating in the 2.4 band, cordless phone, etc? I don't need an answer for that, just something to think about. If I have any other ideas I will post back.

[Edit] Bluetooth keyboard, or speakers or mouse, that might be interfering is another thing to think about when considering possible radio frequency interference .

---

### Post by QLee on 2016-06-25
I found another thread that has a wireless text with "IP4.ROUTE[1]:   dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000"

[http://ubuntuforums.org/showthread.php?t=2326800](http://ubuntuforums.org/showthread.php?t=2326800)

And, interestingly enough, that poster is also reporting a slow wireless connection, but with a very different wireless NIC. Might want to monitor that one too as the helper Chilli55, is very good with wireless, if a solution is found, it might be a good idea to see if it applies to your situation.

---

### Post by QLee on 2016-06-27
I hope you don't mind me bumping this again but I did some research and came up with this which might be worth trying if you haven't found anything else. I don't know how much time you have for this, you're busy here and probably have a life too. I can remember the days when if I could have had a 2M connection I would have been overjoyed. 

My knowledge of TCP is very thin but I found this site about TCP tuning (circa 2009). One thing stated was:
> "By default, TCP saves various connection metrics in the route cache when the connection closes, so that connections established in the near future can use these to set initial conditions. Usually, this increases overall performance, but may sometimes cause performance degradation."

If that is correct (and they didn't cite any documentation), it is a possible explanation for the symptom of "slow sometimes". It goes on to say, "If set, TCP will not cache metrics on closing connections.
```
# echo 'net.ipv4.tcp_no_metrics_save = 1' >> /etc/sysctl.conf
``` Now, Systemd does honour sysctl.conf, so if that hasn't been deprecated since 2009 it might be worth a try, as long as you aren't sick of testing. ;-)

I think you could get that recognised by systemctl restart systemd-sysctl but Systemd is still pretty much like magic to me so maybe you might have to reboot.

I hope you have some luck keeping your wireless running at full speed so you can watch utube video, it seems odd, your Duck atavar doesn't seem to be the correct age to be a Selina Gomez fan. :-)

---

### Post by DuckHook on 2016-06-27
> **QLee said:**
> I hope you don't mind me bumping this again...Not at all. I am very appreciative of your continuing interest.> ...I don't know how much time you have for this...I'm retired and love tinkering, so no problem. However, it is not my production machine and Mrs DuckHook does expect me to pull my weight on other things, so I do work on this only intermittently when I find the time.> ..."If set, TCP will not cache metrics on closing connections.
```
# echo 'net.ipv4.tcp_no_metrics_save = 1' >> /etc/sysctl.conf
```This is straightforward enough and I will give it a try. Easy to reverse if it's not the solution.> ...as long as you aren't sick of testing...I'll let you know when I am. ;)> ...it seems odd, your Duck atavar doesn't seem to be the correct age to be a Selina Gomez fan. :-)*chuckle*

I didn't even know who she was. Had to ask Mrs. DuckHook about her. Her's was just the first youtube video I pressed in the effort to max out download speeds. But now that I've seen her, she's really quite cute. A rather nice incentive to keep testing. :grin:

---

### Post by QLee on 2016-06-28
I've got an old laptop with Broadcom 4306 (the slightly older "cousin" of your chip), I don't have any trouble running consistently at or above the higher speeds that you achieve sometimes (>5). But it isn't directly comparable, my D600 is running Debian Wheezy LTS and I am in a stray radio frequency "clean" environment so I'm confident impairment isn't a factor.

By the way, that is an old laptop, have you considered reseating the mini pci card? Sometimes odd problems disappear after that or carefully cleaning the contacts with a pink pearl eraser. (an outside chance that this might help)

> **DuckHook said:**
> I didn't even know who she was. Had to ask Mrs. DuckHook about her. Her's was just the first youtube video I pressed in the effort to max out download speeds. But now that I've seen her, she's really quite cute. A rather nice incentive to keep testing. :grin:

I have to agree, she is a pretty young woman. I think she's smart too, makes her even more attractive.

---

### Post by Leon A on 2016-06-29
How are you measuring throughput?  I'm wondering if your problem is the same as I've found using bcm43 series with 16.04 (and also on 15.10 but not on 14.04).  If I PING the router via wireless connection, it starts out fine with 100% response, but after some period of time (perhaps related to certain quantity of data passed?) it sometimes starts missing PING responses and eventually get to the point of failing, either due to "destination host unreachable" or "send msg: no buffer space available".  When it starts, I have frequently seen it missing every other PING packet, or sometimes 2 out of 3, which effectively cuts throughput in half or to a third.  Depending on your network traffic, missing packets are either discarded or resent, in which case even further throughput hit occurs. The other point worth noting is that I've seen this issue on machines that are identical except that one used BCM43 series card while other used Realtek rtl8723be, so  maybe it is bug in the kernel rather than in wireless drivers?

---

### Post by DuckHook on 2016-06-29
> **Leon A said:**
> How are you measuring throughput?...using speedtest.net, but also reported by *apt* during kernel upgrades.> ...If I PING the router via wireless connection, it starts out fine with 100% response, but after some period of time (perhaps related to certain quantity of data passed?) it sometimes starts missing PING responses and eventually get to the point of failing, either due to "destination host unreachable" or "send msg: no buffer space available".I don't get this behaviour. Pings continue to be fine except when WIFI is stressed by another app accessing the network (which is expected behaviour) but then settles back down. However, I am intrigued by your:```
sendmsg: no buffer space available
```This hints at the sort of behaviour I am experiencing, where it's as if some buffer gets filled up in the first 40 to 60 seconds and thereafter WIFI speeds get choked.> ...missing every other PING packet, or sometimes 2 out of 3...maybe it is bug in the kernel rather than in wireless drivers?This is distinctly possible. It is also possible that the cause of my problem is different than yours.

/Moderator hat on/
You may wish to post this info in your own thread. I don't recall seeing it there and it would be very valuable to those trying to help you.
/Moderator hat off/

You have spurred me to research further (I had put this one on the back burner) and I came across the following links.
[https://doc.pfsense.org/index.php/No_buffer_space_available](https://doc.pfsense.org/index.php/No_buffer_space_available)
[http://pifuge.com/ubuntu/Hqi-what-does-ping-sendmsg-no-buffer-space-available-mean](http://pifuge.com/ubuntu/Hqi-what-does-ping-sendmsg-no-buffer-space-available-mean)
[http://askubuntu.com/questions/193264/wifi-connected-but-no-data-transfer-ping-sendmsg-no-buffer-space-available](http://askubuntu.com/questions/193264/wifi-connected-but-no-data-transfer-ping-sendmsg-no-buffer-space-available)

Most importantly was this:
[http://www.cyberciti.biz/faq/linux-tcp-tuning/](http://www.cyberciti.biz/faq/linux-tcp-tuning/)

I am going to try some of these parameter changes in my machine. They are not difficult to reverse and my curiosity has now been piqued. Of course, I will post back if results are favourable.

---

### Post by DuckHook on 2016-06-30
**!!Sweet success!!**

By following instructions in this link:
[http://www.cyberciti.biz/faq/linux-tcp-tuning/](http://www.cyberciti.biz/faq/linux-tcp-tuning/)

I got stable maxed-out throughput for a whole Selena Gomez HD video&#8213;a sustained 12 minutes&#8213;which was not possible before. Confirmed by speedtest.net at max offered by ISP. So cool. 8-)

To summarize:

Ubuntu sets low default values for network buffers with the objective of preserving RAM. When connections are ethernet (wired), low defaults are fine. With newer WIFI chips, or WIFI chips with good drivers, or on relatively powerful machines, low defaults are also fine. But with BCM43 series and its ilk&#8213;old, decrepit, lousy drivers, slower CPU, etc&#8213;the buffers need to be increased to make up for the limitations of the hardware. Some of this is conjecture on my part, but I'd bet money that it's pretty close to the truth. The steps to working around the limitations of old chipsets are contained in the link. For sake of completeness, I reproduce them here:```
sudo nano /etc/sysctl.conf
```Add the following stanza at the very bottom:```
# Added by user on 2016-06-30 to allow sustained max WIFI throughput:

net.core.wmem_max = 12582912
net.core.rmem_max = 12582912
net.ipv4.tcp_rmem = 10240 87380 12582912
net.ipv4.tcp_wmem = 10240 87380 12582912
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_sack = 1
net.ipv4.tcp_no_metrics_save = 1
net.core.netdev_max_backlog = 5000
```...save the file, <Ctrl>+<o>, and exit nano, <Ctrl>+<x>. Then reload changes:```
sudo sysctl -p
```...or simply reboot.

It should be noted that I went whole-hog and put in all suggested parameters. It could be that only a subset (maybe even just one) was needed in my case. If I get the inclination, I might back out the changes one by one to isolate the important ones. But I'm probably disinclined to do so because my WIFI now works at max, and that's all I really care about.

Fix is further confirmed by the fact that iwconfig no longer shows too many *Tx excessive retries* or *Invalid misc.* I am one happy camper. :guitar:

It should also be noted that the values for the above parameters are lifted straight out of the linked thread with no further adjustment or tweaking. Obviously, there is all sorts of room for these numbers to be tweaked to the most efficient value. It should be noted that whatever memory you devote to TCP buffers will be memory unavailable to apps. It's now permanently reserved for system TCP use, and indeed, a comparison of free memory before and after shows more used RAM and less free RAM.

As a final conjecture, I wonder if this process might also have some positive impact on large NFS file transfers.  :-k I have noticed that on some of my machines, such file transfers are far below the theoretical max speeds of my network. Since NFS runs on top of TCP, these changes might also benefit NFS.

Anyhow, I'm marking this one *solved*. It has been an especially sweet fix.

---

