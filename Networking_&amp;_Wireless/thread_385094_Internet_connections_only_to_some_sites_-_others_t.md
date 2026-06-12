---
title: "Internet connections only to some sites - others timeout"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by celdar on 2007-03-15
This is a rewritten post originally put in the Feisty forum ([http://www.ubuntuforums.org/showthread.php?t=383390)](http://www.ubuntuforums.org/showthread.php?t=383390)). I cleaned it up, and submit it here since it is a networking problem. 

I have a small home network behind a Linksys WRT54G - four systems: WinXP wired, WinXP wireless, Win2000 wired, Ubuntu Edgy/Feisty wired. All systems have full internet access across the router (no restrictions on the router). The Linksys is setup to provide IP and DNS addresses via DHCP.

After my upgrade from Edgy to Feisty, I have the following connectivity problem with the Ubuntu workstation (Windows systems all continue to work as before):

(1) apt-get update no longer works - times out on connecting to sources
(2) Most internet sites no longer load - including ubuntufoums.com

but:

(3) Some internet sites do load - consistently Google (and blogspot)
(4) Email connections to my isp seem OK for sending, but not for retrieving emails

Here is the tracepath from my Feisty box to ubuntuforums, for example:

[FONT="Courier New"][SIZE="1"]user@athlon1:~$ nslookup [www.ubuntuforums.com](www.ubuntuforums.com)
Server: 216.207.12.14
Address: 216.207.12.14#53

Non-authoritative answer:
[www.ubuntuforums.com](www.ubuntuforums.com) canonical name = ubuntuforums.com.
Name: ubuntuforums.com
Address: 82.211.81.186

user@athlon1:~$ tracepath [www.ubuntuforums.com](www.ubuntuforums.com)
1: athlon1.local (192.168.1.104) 0.276ms pmtu 1500
1: 192.168.1.1 (192.168.1.1) 1.145ms
2: cisco1.mechcom.net (216.207.12.1) 221.901ms
3: chi-edge-18.inet.qwest.net (65.121.248.73) asymm 4 249.917ms
4: chi-core-01.inet.qwest.net (205.171.20.1) asymm 5 120.944ms
5: ewr-core-02.inet.qwest.net (67.14.7.14) asymm 6 80.530ms
6: ewr-brdr-02.inet.qwest.net (205.171.17.130) 233.134ms
7: 205.171.1.98 (205.171.1.98 ) asymm 8 108.639ms
8: ae-1-55.bbr1.NewYork1.Level3.net (4.68.97.129) asymm 9 260.597ms
9: as-0-0.bbr2.London2.Level3.net (4.68.128.110) asymm 12 306.417ms
10: ae-15-55.car1.London2.Level3.net (4.68.117.143) asymm 11 341.062ms
11: tge9-3-146.core-r-1.lon2.mnet.net.uk (212.187.196.82) asymm 12 158.807ms
12: 85.133.32.134 (85.133.32.134) 372.070ms
13: 82.211.81.76 (82.211.81.76) 265.080ms
14: no reply
15: no reply
16: no reply
17: no reply . . . through the max number of hops, until timeout.[/SIZE][/FONT]

For comparison, here is the tracert from my Windows box on the same network:

[FONT="Courier New"][SIZE="1"]C:\Documents and Settings\Owner>tracert [www.ubuntuforums.com](www.ubuntuforums.com)

Tracing route to ubuntuforums.com [82.211.81.186]
over a maximum of 30 hops:

1 1 ms <1 ms <1 ms 192.168.1.1
2 31 ms 14 ms 12 ms cisco1.mechcom.net [216.207.12.1]
3 227 ms 241 ms 227 ms chi-edge-18.inet.qwest.net [65.121.248.73]
4 301 ms 252 ms 259 ms chi-core-01.inet.qwest.net [205.171.20.1]
5 144 ms 218 ms 229 ms ewr-core-02.inet.qwest.net [67.14.7.14]
6 168 ms 316 ms 228 ms ewr-brdr-02.inet.qwest.net [205.171.17.130]
7 238 ms 184 ms 349 ms 205.171.1.98
8 187 ms 173 ms 333 ms ae-1-53.bbr1.NewYork1.Level3.net [4.68.97.65]
9 233 ms 197 ms 146 ms ae-1-0.bbr1.London2.Level3.net [212.187.128.46]
10 181 ms 406 ms 200 ms ae-15-51.car1.London2.Level3.net [4.68.117.15]
11 110 ms 111 ms 111 ms tge9-3-146.core-r-1.lon2.mnet.net.uk [212.187.196.82]
12 112 ms 112 ms 110 ms 85.133.32.134
13 113 ms 112 ms 138 ms 82.211.81.76
14 111 ms 112 ms 112 ms ohiggins.ubuntu.com [82.211.81.186]

Trace complete.[/SIZE][/FONT]

You can see that both systems take the same route, and end up at the same target network. But the Feisty connection does not finish the path.

Here are things I've tried, based on searches here in the forums:
(1) I've rebooted the Feisty box, and did a further upgrade from the 3/12 alternate ISO CD. 
(2) Disabled IPV6 in Firefox - no change 
(3) Disabled IPV6 entirely (blacklist method) - no change
(4) Confirmed that my ISP DNS server IPs are hard coded in my router config
(5) Confirmed that Feisty's DHCP is collecting the correct DNS IPs, and inserting them correctly in /etc/resolv.conf
(6) Added opendns address to the dns server list - no help
(7) Dropped the network connection (ifdown) and manually reassigned a new address and default route
(8 ) Tested FTP connections - same problems as apt and http - timeouts or "waiting for reply"

I'll be glad to provide other information or do other tests, if someone can point me in the right direction. Thanks....

C

---

### Post by Kilz on 2007-03-15
Just one question...... Why on earth did you upgrade a release version (Edgy) to an ALPHA (Feisty) version? Didnt you see the big green bar on the front page of the forum that says its not ready for every day use?

---

### Post by celdar on 2007-03-15
Um... because I wanted to test it. And help with troubleshooting. Like, in a community of people who help each other make things better. 

Am I in the wrong place?

Seriously - I've been upgrading to alpha Ubuntus since Hoary, and helping/contributing in what small way I can. I thought this was a really curious networking problem, that others might be seeing, or have had experience with. I find it an interesting technical problem. 

But apparently it's not one that others are seeing, or care to investigate, since all I got in the Feisty forum was <sound of crickets> silence, and all I got here (so far) was snark.

C

---

### Post by Penfold1234 on 2007-03-15
I'm getting exactly the same problem!

Slightly different setup to yours, by the sounds of it... 
I've got Edgy installed on an older PC (P700 era) with a wireless card (Belkin card, RT61 chipset, not using Ndiswrapper or anything like that) , behind a D-Link router. 

Same as you, I can sucessfully ping out to any internet site that I try, and I can also tracert fine... 

However, when I try to connect to the internet through FireFox, it times out 9 times out of 10. Occasionally, it works absolutely fine for one or two tries, and then goes back to timing out.

I'm a total Ubuntu noob (first install of ANY flavour of Linux), so I'd really appreciate some help... Please let me know if you need me to provide any further information.

Cheers,
Penfold

---

### Post by celdar on 2007-03-15
Actually, your symptoms sound more like they are firefox-specific, and might be related to the known issue with IPv6 in firefox. This thread contains the basic commands for dealing with ipv6 and firefox:

[http://www.ubuntuforums.org/showthread.php?t=265897](http://www.ubuntuforums.org/showthread.php?t=265897)

There are many other similar conversations - it seems a common kind of problem. Do a search here in the Networking Forum for "ipv6" "firefox" and "blacklist".

C

---

### Post by Penfold1234 on 2007-03-15
Bingo! All working correctly now...

Thanks very much for your help, and sorry for the inadvertant thread hijack.
:)

---

### Post by Kilz on 2007-03-15
> **celdar said:**
> Um... because I wanted to test it. And help with troubleshooting. Like, in a community of people who help each other make things better. 

Am I in the wrong place?

Seriously - I've been upgrading to alpha Ubuntus since Hoary, and helping/contributing in what small way I can. I thought this was a really curious networking problem, that others might be seeing, or have had experience with. I find it an interesting technical problem. 

But apparently it's not one that others are seeing, or care to investigate, since all I got in the Feisty forum was <sound of crickets> silence, and all I got here (so far) was snark.

C

There is a difference in helping and testing , and tossing yourself under a train. A separate partition or a virtual machine would have let you try things before messing with your main install.

---

### Post by celdar on 2007-03-16
Kilz - are you being intentionally unhelpful? This IS my test environment. I tried to say clearly in my last post that I regularly use this box to install and work with pre-release Ubuntu versions. I did not "toss myself under a train." 

I'm sorry that you are more interested in rebuking a fellow-user, than in actually looking at the technical problem involved. 

I remain curious about what is happening with the networking components of Ubuntu. Hopefully there are others who will also find it curious, and work with me to resolve the problem. Perhaps we will uncover something that needs to be fixed before release. Or perhaps I will find I've done something wrong, and there is no underlying problem. 

Either way, it's clear that you are not wanting to investigate any further. Feel free to move along...

C

PS -> Penfold1234: I'm glad the fixes suggested worked for you. Good luck...

---

### Post by CSandman on 2007-03-20
celder I seem to be having the same problem as you! My traceroute times out, any of the packaging clients are having a slow time if they work at all and although I can sometimes connect through firefox to some websites more often than not that times out too.  

I too am running Feisty and am pretty happy with the way its shaping up its just this and a small sound snaffu that I believe I could fix if I could recieve the necessary downloads :S

I hope somebody posts something more helpful than the judgemental critisism shown by Kils, just for clarification purposes, I too am running feisty on a secondary machine!

---

### Post by celdar on 2007-03-21
Thanks for the note. By way of update, I have done the following in working this problem:

(1) Removed the Linksys router from the equasion, and attempted to connect my Feisty box directly to my broadband connection with a static IP. This I was actually not successful with - the IP and related addresses were set correctly, but I could not get a live connection. I suspect NetworkManager was getting in the way, and if I try this again I'll need to disable it. Because I have production systems using the router, I could not work this test for long, and had to give up.

(2) Updated the router firmware to the latest level available from Linksys

(3) Re-enabled ipv6 (in firefox, and by removing the blacklist file). 

(4) I manually pinged my way through a number of the ubuntu repository mirrors, and finally hit one (vi.archive.ubuntu.com) that did not time out with apt-get - though throughput was extremelly slow (in the 300B/sec range tops). 

It seems to me that something in my Feisty is handling subnet routing differently than in Edgy, since it appears to scoot out to some subnets without hesitation (google related sites especially have no trouble, and I've stumbled across a few others). 

It also seems that this is not a broad problem - I've found no bug reports in Launchpad that match these symptoms, and there are very few other posts here that match. But since tcp/ip networking is not an area of expertise for me, I feel a little hobbled in troubleshooting it.

I am thinking of submitting this to Launchpad as a bug report, but I'm not sure I have enough real facts - or isolated symptoms - to do so yet. 

C

---

### Post by CSandman on 2007-03-21
So to further complicate things I have a mild success story for this problem, which in my opinion sets my problem in a different area than yours.  I disabled ipv6 to no avail and fiddled with the dhcp settings, also to no avail.  This morning in however I planned to take my laptop to the compE club at the university I go to and voila not only could I connect to the wireless systems but I had full connectivity, no problems whatsoever with slow loading of anything!  Now this is really confusing because my desktop is running XP and has no problems with my D-link router in any respect, wireless or not, and edgy had no problems with my router on a wired connection, so I believe it has something to do with the network settings in feisty... but I haven't the faintest what it could be!?

Have you tried another network all together?  This may make the bug even harder to track down if it only shows up on some networks?
Anyways thats my two cents!

---

### Post by ngreene on 2007-03-22
I'm having the same problems.  I can get sites like [www.speakeasy.net](www.speakeasy.net), google sites and various others.  I waited long enough and adobe.com loaded.  It appears that the computer is resolving DNS very quickly but the page content takes forever to arrive.  I've also tried opendns, ipv6 disable, and some firefox tweaking.  I'm going to try a different network to see if it has something to do with my firewall.

---

### Post by celdar on 2007-03-24
Hi CSandman - unfortunately, my ubunutu test systems is a clunky desktop - not at all handy to move to a different site to try a different network. I think I want to try a direct connection again to my broadband modem - bypass the router altogether - but I need to schedule that for a time when my other systems can be offline.

I did try disabling the firewall on the router, to see if that was getting in the way. No luck there.

With the new beta of feisty out, I downloaded the alternate install version ISO (on one of my other systems), then mounted the ISO on my feisty box. I then did an apt-get dist-upgrade against the ISO, and upgraded my test installation to the 3/22 beta. No problems with the install, but it also did not resolve my networking problem. 

Hi ngreene - thanks for posting a confirmation. Let me know how your experiments go. 

C

---

### Post by Sajmon75 on 2007-03-25
Hi,
same problem for me.
I found the solution, after so many searches,  in this post:
[http://ubuntuforums.org/showpost.php?p=2338947&postcount=8](http://ubuntuforums.org/showpost.php?p=2338947&postcount=8)

Or, to be quick:
---
vi /etc/sysctl.conf

add the following two lines

net.ipv4.tcp_wmem = 4096 16384 131072
net.ipv4.tcp_rmem = 4096 87380 174760

sysctl -p
---

Let me know! I think this is a big problem for many people, i'm new in the forum and in bug reporting.. so i hope someone takes care of this little\big problem. Thanks!

---

### Post by celdar on 2007-03-25
Bingo, that appears to have been the issue here. I'll have to keep an eye on the Linksys site, so see if they release a firmware fix for this. Thanks for posting. I'll update my other thread too...

C

PS -> Ha! The post you linked to is my other thread for this problem, in the Feisty forum. :)

---

### Post by celdar on 2007-03-26
If anyone wants to read more about this particular problem, and alternate workarounds, here are a couple good discussion links:

[http://lwn.net/Articles/92727](http://lwn.net/Articles/92727)
[http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/](http://inodes.org/blog/2006/09/06/tcp-window-scaling-and-kernel-2617/)

---

### Post by celdar on 2007-03-30
I'll mention that I still have some odd timeout problems, even with the workarounds in place. I changed to one of the other workaround methouds:

    echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

And that cleared up some of the additional timeout trouble I was having - especially with apt-get. But I wish Linksys would fix the router... :)

C

---

### Post by rlgoddard on 2007-03-31
> **celdar said:**
> I'll mention that I still have some odd timeout problems, even with the workarounds in place. I changed to one of the other workaround methouds:

    echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

And that cleared up some of the additional timeout trouble I was having - especially with apt-get. But I wish Linksys would fix the router... :)

C

I have a very similar setup, except that both my Windows MCE computers and dual boot Windows XP/Feisty are wireless.  When I enter the above command, this is what I get:

```
joey@joey:~$ echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
bash: /proc/sys/net/ipv4/tcp_window_scaling: Permission denied
joey@joey:~$ sudo echo 0 > /proc/sys/net/ipv4/tcp_window_scaling
bash: /proc/sys/net/ipv4/tcp_window_scaling: Permission denied
```How did you manage to set the tcp_window_scaling without the permission denied message?

Take care,
Russ

---

### Post by T-Dizzle on 2007-04-09
Thanks, Sajmon75!  I've been having the same problem on my Feisty beta machine.  Your solution solved it!

T./

---

### Post by celdar on 2007-04-12
Hi Russ - 

Sorry, should have mentioned that I was in a root terminal at the time. You can issue the command as root, or just stick a sudo at the front of the command:

sudo echo 0 > /proc/sys/net/ipv4/tcp_window_scaling

BTW - I did revert back to the other method of workaround, after using this method for awhile. Things seem "mostly" normal for me now, though I still find the occasional page that will not load, and some of the apt-get repositories I try are really slow. Not sure whether to blame that on this particular router-scaling problem, or on something else at this point.

C

---

### Post by Vevmesteren on 2007-11-20
a friend of mine actually reverted his kernel from 22 to 17 and that fixed it, if that helps anyone? I have the same problem myself. I connect just fine anywhere, except one place, at work, which sux. I run gutsy...

---

