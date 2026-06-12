---
title: "Wireless/Gnome network manager troubles"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by kcyanks1 on 2006-09-14
I posted about this problem over on the alt.os.linux.ubuntu newsgroups and received some replies, but since I have been unable to resolve it, I thought I might try here.  Sorry for anyone seeing it twice:

A few nights ago I set up a wireless network and had it working (albeit
slowly, for whatever reason).  The following morning when I turned on my laptop I couldn't connect to any wireless networks.  When I left-clicked my
"gnomenetwork manager applet", no wireless networks showed up.  The night I set up the router and in the past I would see a whole list of networks that are around me.  Now there is nothing relating to wireless; I don't even see the option to enable wireless networking.  All that is there is "Wired Network"  with a radio button selected to the left.  It seems that somehow my wireless networking has been totally shut off, even though if I go into "Network settings" it says that my wireless connection/eth1 is active.

I know that my computer can do wireless fine, because in the few days before I had connected to a couple different wireless networks perfectly, and I also saw many other networks at various times that I did not try to connect to.

My computer is a Dell Latitude D620 with the Intel PRO/Wireless 3945ABG.

Thanks ahead of time for the help.

Edit:  I am using Ubuntu 6.06.  I have Gnome and KDE installed, though I use Gnome the majority of the time.  If I run iwconfig, I get, for eth1:
eth1      unassociated  ESSID:"ksc-laptop"
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11428   Missed beacon:0

---

### Post by wieman01 on 2006-09-14
Mmm... Could you post **"/etc/network/interfaces"** please? Your problem could lie there.

---

### Post by kcyanks1 on 2006-09-14
> **wieman01 said:**
> Mmm... Could you post **"/etc/network/interfaces"** please? Your problem could lie there.

Thanks for the reply.  Here is the contents of that file:

ksc@ksc-laptop:~$ more /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth1 inet dhcp
wireless-essid ksc-laptop

auto eth1

---

### Post by wieman01 on 2006-09-14
Ok... It's like I have suspected. If you're using (Gnome) NetworkManager, you need to remove these lines (as NetworkManager is taking care of your network interfaces/adapter):
> iface eth1 inet dhcp
wireless-essid ksc-laptop

auto eth1
Restart the computer and see how it goes. If that does not work, remove all other lines and only leave these two:
> auto lo
iface lo inet loopback
That should do (after a restart).

---

### Post by kcyanks1 on 2006-09-14
Thanks!  It seems to work, the networks are visible again. I followed your advice and removed (commented out) the following lines (only):

# iface eth1 inet dhcp
# wireless-essid ksc-laptop

# auto eth1

Thanks very much for the quick replies and help!

---

### Post by wieman01 on 2006-09-14
Great! I saw this happen to others as well. This kind of problem seems to frequently appear after system upgrades, etc. Hope this helps others as well.

---

### Post by kcyanks1 on 2006-09-14
I may have spoke to soon, but only in part.  The wireless networks all are visible again, which was my main problem, and thanks again for solving it.

Now, though, when I try to connect to my wireless network, I connect and have full signal strength, but nothing works.  I'm currently plugged in through my router, if that is important to show that the router isn't totally bad.  When I first set up the router a few nights back, it was working, though slower than I would've hoped (at least as far as uploading--even sending emails seemed to take a while).  Now I have nothing (page not found errors in Firefox, host not found for newsgroups, etc.).

Is there something obvious software-wise dealing with linux, as opposed to the router, that might be causing the problem?  I hope to try and find a wireless network that I can test my computer on that I know works to see if it is my network or something with my computer setup, so if getting those results would be important for diagnosing my issue, feel free to wait until I am able to test it and post again.

The router is a TRENDnet TEW-432BRP.

Thanks.

---

### Post by wieman01 on 2006-09-14
Can you poing your router? Are you connected? 

If so, there is an issue with "ipv6"... Known issue. You need to disable "ipv6" in the kernel and Firefox. There a lots of post concerning this in the forum.

---

### Post by kcyanks1 on 2006-09-15
Here is my results for pinging.  First with my wired network, through the router (works fine), then when I'm "connected" to my wireless  network (get nothing):

WIRED:
ksc@ksc-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=127 time=0.929 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=127 time=0.770 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=127 time=0.760 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=127 time=0.773 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=127 time=0.754 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=127 time=0.737 ms

--- 192.168.1.1 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5005ms
rtt min/avg/max/mdev = 0.737/0.787/0.929/0.066 ms

WIRELESS:
ksc@ksc-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.1.1 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6013ms

I started to do some searching on the forums of ipv6 problems, and it appears to me that people having those issues have no connectivitiy at all, not just no wireless connectivity.  I'll continue doing some research there, but first later today I hope to go to a known working network and try that out.  My wireless connection was after all working less than a week ago at more than one location -- is it possible that an update I may have done caused problems? (That seemed to be the issue that you solved, though I honestly can't remember doing any updates between it working and not working.  I did do that kernel update yesterday.)

---

### Post by wieman01 on 2006-09-15
That's why I asked you to ping you router... "ipv6" does not seem to be your problem. Let me think for a while and get back to you.

---

### Post by wieman01 on 2006-09-15
Others have posted regarding this lately. Could it be related? If I were you, I would try without NetworkManager. I could guide you through the process of manually editing your "interfaces" configuration file... Just a thought... Perhaps that makes the difference.

---

### Post by kcyanks1 on 2006-09-15
I went to the library where they have free wireless, and I was able to connect using the network manager.  One odd thing is that the signal keeps on going from 0% to close to 90-something% (in a matter of seconds).  When it's high, I'm fine (I got to this page and posted this!), but when it's down, nothing works (no surprise).  I asked a person next to me and he didn't think he was having problems, but said he wasn't browsing too much.  Would be that my setup is OK and the library has a poor signal?  Or is there something in my setup that could affect this?

I also was able to try my home network with a Windows PC, and it appeared to connect, then drop, then connect, then drop, and I wasn't able to do anything.  Perhaps that can indicate something is wrong with my network, though the odd thing is that it was working (at least somewhat) a few nights back.

As for trying without NetworkManager, I guess I am willing to do whatever might get my network at home to work.  Though considering I have used NetworkManager on a couple occasions without trouble, and right now I'm guessing NetworkManager is not causing my signal at the library to go in-and-out, would you think that is the issue?  If so, I'll give it a shot.  I do like the convenience of NetworkManager though, it makes it easy to connect to a network wherever I am.  Also, my wireless network is WPA-encyrpted--is it possible to use WPA without NetworkManger?  My (perhaps faulty) understanding was that it was not.  I'd be happy to use WEP instead, except that for some reason, when I was in my router set-up, I was unable to set-up it for WEP.  It theoretically should work, but it wouldn't accept my changes to the settings when I chose WEP.  I could call tech support for the router if I'm forced to change to WEP, that's not something I'd want to bother you with.

Thanks so much for all the help so far.

---

### Post by wieman01 on 2006-09-15
Since you're saying that Windows encounters the same problem, I don't think this relates to NetworkManager at all. I must agree. Perhaps it's the router but before you start changing it's settings would there be any other (open) network near you to test it?

The router has a number of settings (beacon interval, fragmentation threshold, etc.) you can play with. It's an option at this stage.

---

### Post by kcyanks1 on 2006-09-15
Sorry for not trying out the Windows machine earlier. I figured that since it was working for me once, and since when you first helped me I wasn't seeing any wireless networks, it probably wasn't an issue with the router, but with my linux setup.

There are some open networks around me.  I tried connecting (in linux), and in a couple cases I connected, but no luck on getting anything.  I didn't try to connect to any with my windows machine recently, but on another occasion a month or so back, I did, with limited luck, manage to connect to some.  They'd work for a few minutes and go out generally--the signals weren't strong enough, I don't think.  The odd thing with my network is that it did work the first night I installed it.  

I'll try looking at the settings you suggested playing around with.  I guess this is what I get for buying the $43 router with a $30 mail in rebate :-(

---

### Post by wieman01 on 2006-09-16
What brand is your router again? Do you think you can get a firmware update for it? 

Perhaps it does still relates to ipv6. I would disable it anyway (also in Firefox) which will boost your system's performance and exclude this one as a potential bottleneck/stumbling-block.

---

### Post by kcyanks1 on 2006-09-16
Router is a TRENDnet TEW-432BRP.  I searched on the site and could not find 
updated firmware -- but I couldn't find any firmware downloads at all, so I'm  not sure I was looking in the right place.  I tried googling to find it but to no avail.

I disabled ipv6 in Firefox and globally, and I as before connect to my network but cannot do anything.  Thanks.

---

### Post by wieman01 on 2006-09-17
This morning I realized that my Internet connection kept dropping and reconnecting constantly. The reason - I figured - is that I had moved the router to another spot in my apartment the night before. 

So I did what I had suggested to you... I simply changed the router's wireless settings (beacon, etc.) and surprisingly this did the job. The network has been stable for the last 2 hours or so.

---

### Post by kcyanks1 on 2006-09-17
I hope you don't want to kill me, but I managed to get it working.  You were very helpful in solving the gnome-network manager issue, and I realized from searching for new drivers that I could call for free tech support.  So I did that, and they managed to help me.  We did a couple things.  First (1) DCHP Renew in the router setup, (2) ensure my firewall (software-based) was disabled.  As for (2), I *think* it might have been enabled before, but I actually didn't notice and just hit disable.  So it's possible it was already disabled and it was just the DCHP renew that did it.  Either way, there is a firewall in the router, so I'm not concerned, and the problem seems to be fixed.  I apologize for not calling tech support sooner, and for wasting your time after you helped me with the initial problem with the network manager (which I assume they'd never be able to do as it had nothing to do with the router). Thanks!

Edit: I recalled there was one thing that the tech rep had me do before the two steps above.  So what I'll call "Step (0)" was to Clone my MAC address.

---

### Post by wieman01 on 2006-09-17
Don't worry... Sh@#$ does happen all the time. And networking is one of the greatest challenges when it comes to Linux. At least you could confirm that this had to do with the router's settings, not Linux. 

What firewall are you using? "Firestarter" by chance? Man, I should have asked that question before. :-) This sounds oddly familiar.

Glad you got it solved.

---

### Post by kcyanks1 on 2006-09-17
Yes, I have Firestarter installed.  I had seen it the package in Synaptec, and figured, why not?  I know Linux is secure, but didn't think the added protection would cause problems.  At the time I also was just plugged directly to my modem, which to my knowledge didn't have a firewall.  It hadn't crossed my mind to mention it.

---

### Post by quail-linux on 2006-12-01
> **wieman01 said:**
> Ok... It's like I have suspected. If you're using (Gnome) NetworkManager, you need to remove these lines (as NetworkManager is taking care of your network interfaces/adapter):

Restart the computer and see how it goes. If that does not work, remove all other lines and only leave these two:

That should do (after a restart).
Thanks for the help, it help me fix a prob i had with gnm where my wired stuff was not showing.

---

### Post by 4ebees on 2007-10-12
> **wieman01 said:**
> Great! I saw this happen to others as well. This kind of problem seems to frequently appear after system upgrades, etc. Hope this helps others as well.

Hi there,

I had the same problem on the s/father's laptop - removing all but the first couple of lines worked well.

Thanks for that :)

:popcorn:

---

### Post by LiquidShadow on 2007-10-17
Me too had this problem yesterday. The solution was simple and dummy... I unintentionally blocked some connection playing too much with iptables... maybe this can help some of you!

---

