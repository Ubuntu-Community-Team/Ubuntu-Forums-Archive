---
title: "The Speed of N"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by bmachia on 2008-08-02
I've been use Kubuntu now for about 8-10 months.  I LOVE it and no longer use MS products at this house.

My laptop currently connects to my home network using 802.11G and WPA2, via ndiswrapper.   It works fine and has for a long time.  However both my network card (Netgear WN150B) and Linksys router are Type N compatible.  I have never understood what it takes to get the full N connection speeds, I always settled for 802.11g.

An 'iwlist scan' output is below
*******************iwlist scan output*************************
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:6D:7D:FF
                    ESSID:"Linksys7xx123N"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1F:33:29:09:90
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
************************* iwlist scan output end **************************

What should I be looking at to connect at 802.11N speeds?

And

As you can see from the iwlist scan about, I have 2 cells.  Cell 02 is from
an old Netgear router I used a few weeks back.  It will never be on-line again.  Is
there any way to remove 'Cell 02 (old NetGear router)'?  Should I even worry about a Cell 02
listing?

Thx
Bill

---

### Post by pytheas22 on 2008-08-02
I think that ndiswrapper doesn't support N speeds, even if the Windows driver that it's wrapped around does.  Do you know what kind of chipset your card has?  If not, post the output of:
```

lspci
```

or if it's an external USB card:
```

lsusb
```

There may be a native driver available that does support N speeds.  If the only way to make your card work is with ndiswrapper, however, you may be out of luck until a better native driver is written.
> 
As you can see from the iwlist scan about, I have 2 cells. Cell 02 is from
an old Netgear router I used a few weeks back. It will never be on-line again. Is there any way to remove 'Cell 02 (old NetGear router)'? Should I even worry about a Cell 02
listing?

I'm not sure what you mean...don't you own both routers and therefore have the capability to turn Cell 02 off?  A router functioning in N mode should still be compatible with G mode (provided you configure it that way), so you don't need Cell 02 just for the G card.  Otherwise, please clarify what you want to do.

---

### Post by bmachia on 2008-08-03
Thanks pytheas22 for getting back to me.

Below is the output from lspci
******************************************************
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [RadeonMobility 7500]
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
07:00.0 Network controller: Broadcom Corporation BCM43XG (rev 01)
******************************************************
Post Script:
Is fw-cutter a possible solution?  If yes, Can anyone provide a reading/informational link? 


Concerning Cell 02;
This was an old router that was turned off and disconnected from my Network weeks ago.  The laptop that is providing the iwlist scan information has not seen it on the network for weeks.  Yet, it still shows with an iwlist scan. ?Why?? I honestly have no idea.

I have rebooted and turned the laptop off/on a couple of times since the router within Cell 02 was removed.  I don&#8217;t understand why the laptop keeps showing this old Cell 2 information. 
Does this help?  I know I was as clear as mud in my initial explanation.

Looking forward to your response

Bill

---

### Post by pytheas22 on 2008-08-03
fw-cutter (which means using the native Linux driver for your card, b43, instead of ndiswrapper) would probably work with your card.  But I don't think that b43 has support for 11n mode yet either.  I can't seem to find official confirmation of that on the b43 website, but I did find this on the aircrack forums (those people usually know what they're talking about with Linux wireless), in a [post]("http://tinyshell.be/aircrackng/forum/index.php?topic=3597.0") from May 2008:
> 
b43 is a mac80211 driver. b43 offers a newer codebase and hardware crypto support than bcm43xx. With patches the injection speed is at least 700pps. Also, all attacks work, including fragmentation. **There is no support for any Draft 802.11n** features right now.

So I don't think that using b43 is going to allow you to use 11n speeds.

BUT I'm second-guessing myself about whether or ndiswrapper supports 11n speeds.  See this [thread]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_fireboard/Itemid,34/func,view/catid,3/id,1231/"); they say it does as long as your card and windows drivers do.

In addition, I'm noticing that the iwlist output for your 11n router doesn't mention 11n speeds being supported:
```

Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
```

It could be that the card is interpreting the information incorrectly, but I'm wondering if maybe your router isn't really supporting 11n speeds.  You may want to double-check the configuration.  Is there any way you could test (i.e., do you have access to a device that you know definitely supports 11n speeds)?
> 
Concerning Cell 02;
This was an old router that was turned off and disconnected from my Network weeks ago. The laptop that is providing the iwlist scan information has not seen it on the network for weeks. Yet, it still shows with an iwlist scan. ?Why?? I honestly have no idea.

I understand the question better now.  I have no idea what could be going on here either other than that your wireless card itself is broadcasting that signal instead of a router.  The reason I think that is that I notice this line:
```

Cell 02 - Address: 00:1F:33:29:09:90
ESSID:"NETGEAR"
Protocol:IEEE 802.11g
**Mode:Managed**
Frequency:2.412 GHz (Channel 1)
```

Normally that line should say "Mode:Master."  A device in managed mode is one that's connected to a router; a master device is the router itself.  If you turn off all wireless devices in your house and boot to the Ubuntu live CD (so that you're using a clean slate), do you still see that cell mentioned?

---

### Post by bmachia on 2008-08-03
Post Script on Cell 02 question:
I had this old Netgear router that just wasn't reliable.  Sometimes my network would connect and run perfectly.  Sometimes I saw the strangest things like an IP address (If memory serves me correctly) in the 168.x.x.x range, I have always use 192.168.x.y.  I couldn't figure it out, so I took my Netgear router off my network and bought the Linksys WRT150N.

Now that I know my Netgear router is off-line and I still see a Netgear router with iwlist scan, I'm wondering if I have a neighbor with another Netgear router that uses the same out of box/default hostname and that was the reason for my crazy Netgear connection information.

Do you think this could be a possibility?


UPDATE - EDIT Addition
What a dummy I've been, regarding 802.11g to 802.11n.  Your suggestion pointing me back to the Router was the key/trigger.

I have never been able to get this laptop to connect to the router using 802.11n.  Even when the Linksys WRT150N is set to &#8220;Network Mode: MIXED&#8221; it won't connect.  BUT, if I set the Linksys to &#8220;Network Mode: Wireless G only&#8221; it works &#8211; fast and perfectly.  Thats why you were seeing the G speeds (only).

Regarding your test using another known N type device:  Since I no longer have any MS stuff in this house, I going to need to think about that one.  Is there any test I can perform if I switch the Router into &#8220;Network Mode: Wireless N only&#8221; or &#8220;Network Mode: MIXED&#8221; to verify router configuration?

Bill

---

### Post by pytheas22 on 2008-08-03
> Now that I know my Netgear router is off-line and I still see a Netgear router with iwlist scan, I'm wondering if I have a neighbor with another Netgear router that uses the same out of box/default hostname and that was the reason for my crazy Netgear connection information.

That could be possible; Netgear routers are popular and most people don't bother changing the essid (incidentally, I happen to be using a network named "NETGEAR" right now).  You could check by taking your Netgear router back out and seeing what the MAC address is--it's probably printed on the outside of the router somewhere so you shouldn't even need to turn it on; if not you should be able to find the MAC in the configuration utility.  The MAC of the Netgear router in the scan is 00:1F:33:29:09:90; see if it matches.  Also, the router from iwlist is on channel 1; see what happens if you change your router to operate on a different channel.
> 
Regarding your test using another known N type device: Since I no longer have any MS stuff in this house, I going to need to think about that one. Is there any test I can perform if I switch the Router into &#8220;Network Mode: Wireless N only&#8221; or &#8220;Network Mode: MIXED&#8221; to verify router configuration?

iwlist scan should still report the router configuration correctly even if your card isn't capable of connecting for whatever reason.  So switch the router to 11n mode and see what iwlist scan says about it then.

---

### Post by bmachia on 2008-08-04
Pytheas22
Will 1 questions solved, the other is still open for research.

I check my Netgear router the MAC address.  The label is totally different from the iwlist report.  My Netgear router’s MAC is 00:17:3F:3F:66:42.  So Cell 02 has to be a neighbor.  Problem solved.

Next I ran an iwlist scan with the Linksys WRT150N in 4 different configurations (i.e. B Only, G only, N Only, and MIXED).  

B Only, responded exactly as we thought.  It showed; 1 Mb/s, 2Mb/s, 5.5 Mb/s and 11 Mb/s at 2.414 GHz. 

G Only, responded like it should as well.  It showed; 1 Mb/s, 2Mb/s, 5.5 Mb/s, 11 Mb/s, 12 Mb/s, 18 Mb/s, 24 Mb/s, 36 Mb/s, 48 Mb/s, and 54 Mb/s at 2.414 GHz. 

However ‘N Only’ and MIXED told me a different story.  Both of these configurations showed; 1 Mb/s, 2Mb/s, 5.5 Mb/s, 11 Mb/s, 12 Mb/s, 18 Mb/s, 24 Mb/s, 36 Mb/s, 48 Mb/s, and 54 Mb/s at 2.414 GHz.  There was nothing above 54 MB/s and no notation of a 5 GHz frequency.  Something did not allow the PCMCIA NIC (Belkin WN511b) to receive 5 GHz.

Next, I updated my ndiswrapper WN511b driver to today’s current version (I was 1 version old) and the speed numbers stayed the same as above.


I read the articles/postings behind your links they seem to contradict each other on occasion.  So, I’m betting the research needs to continue to find the real answer.

If you find any more information pertaining to N limitations, is there any chance you could forward me the links?

Bill

---

### Post by pytheas22 on 2008-08-04
I'm glad that at least the Netgear enigma is resolved.

I'm not quite sure what could be going on with the other router.  One thought is that when the router is in mixed mode, it's really broadcasting on two frequencies (11g and 11n), and your card can only see the 11g frequency.  However this doesn't make much sense because if that were the case, then broadcasting on 11n only should make your card not see anything at all.  And I think that iwlist should be able to detect the bit rates correctly no matter what, so I don't know why it thinks the highest is 54M.

I was reading some stuff ([here]("http://www.internettablettalk.com/forums/showthread.php?p=77001") for example) that concludes that basically the implementation of 11n is still buggy on some routers and may not really work.  I have no idea if those people really know what they're talking about, but it seems plausible.  You may want to see if there's a firmware update available for your router and make sure you're using the most up-to-date stuff.

Beyond that, I guess that the only way to really test what's going on is to 1) bring your laptop in range of another 11n network and see if it detects it correctly; or 2) get a wireless card that you're certain supports 11n and see if it detects your router correctly.  Otherwise, it's hard to know whether the problem lies with your router or your wireless card/driver.  I'm leaning more towards your router, because it seems to be doing some strange things (by the way, I noticed that iwlist also reports your Linksys as being in managed mode, which is weird), but really it's hard to be certain.

---

### Post by Dougie187 on 2008-08-04
Something odd, I just posted something on an issue similar to this last night. Bascially for my case, I have a Linksys (WRT150N) router and an intel pro wireless (iwl4965) mini pci card. I as well, only see up to wireless g speeds using iwlist scan, and if I set my router to use only wireless N speeds, I can still see the router, but I cannot connect. I am stumped as to why this happens, mainly because I have the intel driver (which should support wireless n) and the router (which i know supports wireless n) and its not working. I am completely clueless as to what to do to try and fix it.

---

### Post by pytheas22 on 2008-08-04
> I am completely clueless as to what to do to try and fix it.

At least in your case, you're certain that your driver should support 11n (we think ndiswrapper should, but who knows for sure).  A good place to start troubleshooting why you can't connect in 11n mode is to try to connect, and then immediately run this command:
```

dmesg | tail
```

It should print error messages related to the failure to connect.

---

### Post by Dougie187 on 2008-08-04
well.. so i set my router to n only. And its really weird, the network-manager applet in the tray just turns all grey (signal 0%) and i can't do anything, but it still says that im connected. Also, when my router is wireless N, It becomes the only wireless network I can see, even though when I have it on mixed mode there are 9 networks available. also, here is the dmesg info that I got while my network was at 0%

```

[  744.301624] wlan0: authenticated
[  744.301628] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  744.301644] wlan0: authentication frame received from 00:1d:7e:cd:2c:e5, but not in authenticate state - ignored
[  744.302957] wlan0: authentication frame received from 00:1d:7e:cd:2c:e5, but not in authenticate state - ignored
[  744.304293] wlan0: invalid aid value 0; bits 15:14 not set
[  744.304303] wlan0: RX AssocResp from 00:1d:7e:cd:2c:e5 (capab=0x411 status=18 aid=0)
[  744.304307] wlan0: AP denied association (code=18)
[  744.310689] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  744.310864] wlan0: invalid aid value 0; bits 15:14 not set
[  744.310874] wlan0: RX AssocResp from 00:1d:7e:cd:2c:e5 (capab=0x411 status=18 aid=0)
[  744.310879] wlan0: AP denied association (code=18)
[  744.317610] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  744.318384] wlan0: invalid aid value 0; bits 15:14 not set
[  744.318393] wlan0: RX AssocResp from 00:1d:7e:cd:2c:e5 (capab=0x411 status=18 aid=0)
[  744.318397] wlan0: AP denied association (code=18)
[  744.330889] wlan0: association with AP 00:1d:7e:cd:2c:e5 timed out
[  745.174949] wlan0: Initial auth_alg=0
[  745.174961] wlan0: authenticate with AP 00:1d:7e:cd:2c:e5
[  745.176798] wlan0: Initial auth_alg=0
[  745.176806] wlan0: authenticate with AP 00:1d:7e:cd:2c:e5
[  745.176822] wlan0: RX authentication from 00:1d:7e:cd:2c:e5 (alg=0 transaction=2 status=0)
[  745.176827] wlan0: authenticated
[  745.176831] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  745.176849] wlan0: authentication frame received from 00:1d:7e:cd:2c:e5, but not in authenticate state - ignored
[  745.179303] wlan0: authentication frame received from 00:1d:7e:cd:2c:e5, but not in authenticate state - ignored
[  745.181317] wlan0: invalid aid value 0; bits 15:14 not set
[  745.181321] wlan0: RX AssocResp from 00:1d:7e:cd:2c:e5 (capab=0x411 status=18 aid=0)
[  745.181322] wlan0: AP denied association (code=18)
[  745.212894] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  745.213920] wlan0: invalid aid value 0; bits 15:14 not set
[  745.213924] wlan0: RX AssocResp from 00:1d:7e:cd:2c:e5 (capab=0x411 status=18 aid=0)
[  745.213926] wlan0: AP denied association (code=18)

```

Also, im not sure if this is related or not, but sometimes when i do an iwlist scan it just won't come back with anything. I have to do it like 10 times to get anything.

Either way, that isnt a big deal, im more worried about the wireless n thing.

---

### Post by pytheas22 on 2008-08-04
> Also, im not sure if this is related or not, but sometimes when i do an iwlist scan it just won't come back with anything. I have to do it like 10 times to get anything.

Sometimes iwlist doesn't pick up every network on every scan, especially if it's far from the routers in question.  But it shouldn't take as many as ten scans to see the network, so I'm not sure what's going on.

It does appear from dmesg that you have some driver issues--perhaps trouble negotiating the WPA key (you are using WPA, right?).  Does it work better with encryption turned off?

Also, you don't mention which driver you're using; I'd assume Intel, but before I do that, please confirm, and let me know whether it's iwl4965 or iwl3945 (if you don't know, what does "lshw -C Network" say?).  Then I can do some research and see if it turns up anything.

---

### Post by Dougie187 on 2008-08-05
Well it looks like lshw -C Network gives me "driver=iwl4965"

I was thinking, that maybe the driver included in the current kernel doesn't support n speeds or something, but I didn't think that quite made sense. I guess I could always try updated to the one on intel's site.

do you think that would help at all?

Here is dmesg from when I had no encryption.

```

[  535.970289] wlan0: RX deauthentication from 00:1d:7e:cd:2c:e5 (reason=7)
[  535.973626] wlan0: Initial auth_alg=0
[  535.973635] wlan0: authenticate with AP 00:1d:7e:cd:2c:e5
[  535.973661] wlan0: RX deauthentication from 00:1d:7e:cd:2c:e5 (reason=7)
[  535.977288] wlan0: Initial auth_alg=0
[  535.977294] wlan0: authenticate with AP 00:1d:7e:cd:2c:e5
[  535.977312] wlan0: RX authentication from 00:1d:7e:cd:2c:e5 (alg=0 transaction=2 status=0)
[  535.977317] wlan0: authenticated
[  535.977322] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  535.982054] wlan0: Initial auth_alg=0
[  535.982063] wlan0: authenticate with AP 00:1d:7e:cd:2c:e5
[  535.982913] wlan0: RX authentication from 00:1d:7e:cd:2c:e5 (alg=0 transaction=2 status=0)
[  535.982920] wlan0: authenticated
[  535.982924] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  535.984735] wlan0: RX ReassocResp from 00:1d:7e:cd:2c:e5 (capab=0x401 status=0 aid=1)
[  535.984742] wlan0: associated
[  535.984800] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  535.984807] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  535.984813] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  535.984819] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  539.217032] wlan0: no IPv6 routers present

```

Also, iwlist scan didn't work any better. Although the weird problem with iwlist scan, is when my router is set to n, I dont see any networks, even in network manager, only my network which I can't connect to.

---

### Post by JanRa on 2008-08-05
I am in a similar situation.
I have a D-link 635 DIR router and my laptop has the intel 4965 wireless receiver. Both are N compatible.
In vista (i have a dual boot) i get speeds up to 144 Mbps and under Hardy Heron the maximum speed is 54 Mbps. 
Since it works under windows, i assume it has to do with the linux drivers. Any suggestions?

Jan

---

### Post by Dougie187 on 2008-08-05
Have you tried installing the drivers from the intel site under ubuntu?

---

### Post by pytheas22 on 2008-08-05
Dougie187,

Were you able to connect successfully when you turned off encryption?  Because it looks to me like you did, according to dmesg--you didn't get authentication errors like before.

Anyway, I think I may have figured out what's going on.  Read this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.24/+bug/203506").  It seems that, while the iwl4965 driver (the one in the kernel) does support 11n speeds, the build of the driver that shipped with Hardy doesn't.  They say that this should change in Intrepid.

Some guy in the bug report alludes to using the packages from his personal repository as a solution, but it's not explicitly clear that this is definitely the trick for getting 11n speeds; nor am I sure exactly which packages you'd need to download from his repository to get your wireless working on 11n mode--the guy's pretty vague.

I don't actually own any Intel wireless cards myself, but if any of you in this thread want to try getting the 11n stuff up, we can attempt to figure out how to do it.  As a warning, though, I can't guarantee that it won't end up breaking your current configuration and leave you with no wireless at all.  But if you can afford to experiment and have the time, we can try to get 11n going.

---

### Post by Dougie187 on 2008-08-05
@pytheas22:
I think i was able to connect, but I didn't have it set to wireless n only. I can try that as soon as I get home. I would have done it earlier, but I would have had to go reset it at my desktop (and thats a small pain, and I didnt have time this morning). 

That bug report is interesting.. too bad they couldn't get n into hardy. I wonder if installing the intel driver from their site would make it work. Also, Intrepid comes out in like 2 months, so then it should be working fine. 

I might mess with that guy's packages later. One question though, since they are just packages, couldn't I enable his repo, and if it doesnt fix  the wireless n stuff just disable it and remove the packages, then reinstall the packages from the ubuntu repos?

---

### Post by pytheas22 on 2008-08-05
> I might mess with that guy's packages later. One question though, since they are just packages, couldn't I enable his repo, and if it doesnt fix the wireless n stuff just disable it and remove the packages, then reinstall the packages from the ubuntu repos?

Sure, in principle, that would work.  Especially if you have a wired connection to fail back you, you should be pretty safe.  I just would caution you to play around with those repositories if wireless is your only means of getting online and you can't afford to have your machine break.
> 
I wonder if installing the intel driver from their site would make it work.

What's the link to the drivers you're referring to?  I didn't think Intel offered Linux drivers for 4965 on its site; I thought they only covered up to 3945.  But as I say, I don't have an Intel card myself, so don't quote me on anything.

---

### Post by Dougie187 on 2008-08-05
Here is that link i was talking about.
[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2753&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go)!

Also, I don't think it will fix the issue, because the release date is 8/xx/07, so thats a year old.

I'll have to check out the other guys stuff, and ill try to get that dmesg log for unencrypted n connection.

---

### Post by Dougie187 on 2008-08-05
Here is the log. Unencrypted Wireless N only.

```

[  276.399892] wlan0: authenticated
[  276.399896] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  276.402744] wlan0: authentication frame received from 00:1d:7e:cd:2c:e5, but not in authenticate state - ignored
[  276.404320] wlan0: invalid aid value 0; bits 15:14 not set
[  276.404331] wlan0: RX AssocResp from 00:1d:7e:cd:2c:e5 (capab=0x401 status=18 aid=0)
[  276.404336] wlan0: AP denied association (code=18)
[  276.436431] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  276.438757] wlan0: invalid aid value 0; bits 15:14 not set
[  276.438768] wlan0: RX AssocResp from 00:1d:7e:cd:2c:e5 (capab=0x401 status=18 aid=0)
[  276.438772] wlan0: AP denied association (code=18)
[  276.454236] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  276.455400] wlan0: invalid aid value 0; bits 15:14 not set
[  276.455411] wlan0: RX AssocResp from 00:1d:7e:cd:2c:e5 (capab=0x401 status=18 aid=0)
[  276.455416] wlan0: AP denied association (code=18)
[  276.494132] wlan0: association with AP 00:1d:7e:cd:2c:e5 timed out
[  277.657668] wlan0: Initial auth_alg=0
[  277.657679] wlan0: authenticate with AP 00:1d:7e:cd:2c:e5
[  277.659570] wlan0: Initial auth_alg=0
[  277.659577] wlan0: authenticate with AP 00:1d:7e:cd:2c:e5
[  277.659594] wlan0: RX authentication from 00:1d:7e:cd:2c:e5 (alg=0 transaction=2 status=0)
[  277.659599] wlan0: authenticated
[  277.659603] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  277.661170] wlan0: authentication frame received from 00:1d:7e:cd:2c:e5, but not in authenticate state - ignored
[  277.662195] wlan0: invalid aid value 0; bits 15:14 not set
[  277.662204] wlan0: RX AssocResp from 00:1d:7e:cd:2c:e5 (capab=0x401 status=18 aid=0)
[  277.662208] wlan0: AP denied association (code=18)
[  277.682989] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  277.684159] wlan0: invalid aid value 0; bits 15:14 not set
[  277.684170] wlan0: RX AssocResp from 00:1d:7e:cd:2c:e5 (capab=0x401 status=18 aid=0)
[  277.684175] wlan0: AP denied association (code=18)
[  277.700774] wlan0: associate with AP 00:1d:7e:cd:2c:e5
[  277.701938] wlan0: invalid aid value 0; bits 15:14 not set
[  277.701949] wlan0: RX AssocResp from 00:1d:7e:cd:2c:e5 (capab=0x401 status=18 aid=0)
[  277.701954] wlan0: AP denied association (code=18)
[  277.725847] wlan0: association with AP 00:1d:7e:cd:2c:e5 timed out

```

Again, No connection, although unlike before it didnt "connect" and say 0% signal. I just wouldnt connect at all. It stayed with the spinning ball thing, and iwlist scan gave g speeds as well.

---

### Post by Dougie187 on 2008-08-05
Well. I just went through the process of installing all the guys crap (its bascially custom compiled kernels and stuff...) and.... the result, is that it didnt change crap.

I wouldn't waste your time installing it, just wait for intrepid i guess.

---

### Post by Dougie187 on 2008-08-08
Has anyone else messed with this anymore? I still haven't got anywhere..

---

### Post by Dougie187 on 2008-10-20
Has anyone tried wireless n on ibex yet? I remember someone said it should have support, maybe it was in the buglist or something. But it would be cool to see if anyone had any experiences with this yet.

---

### Post by aleksabl on 2008-11-02
Hi there,

I've got Intel iwl4965 (ABGN), and 802.11n seems to be working here. Even though the network-manager applet and iwlist are only reporting 802.11g-speeds (maximum of 54mbits), the router says that my computer are connected with 802.11n and 130mbits..

---

### Post by Dougie187 on 2008-11-02
I have an iwl4965 (ABGN) as well, and a n router. But I'm not seeing anything that would make me think that I am getting n speeds. I have linux-backports installed too as per the recommendations in the release notes from ubuntu.com.

---

### Post by dbhsatx on 2008-11-29
I am using the iwl4965agn under intrepid. iwlist shows 54m as max speed but my D-link615 router shows the laptop is connected at 130m

---

### Post by Saneless on 2008-12-30
My router shows anywhere between 54 and 117-120..  But the actual transfer speed was still never faster than 2MB/s, same as it was with my G router.  Just because it says it connects at N doesn't mean ubuntu is flinging out data at that speed.

---

### Post by hansheijmans on 2010-01-16
Hi there,

I'm using the Netgear WN511B wireless card and the Netgear WNR834Bv2 router (both N capable) but I can't get N to work. The highest bitrate I can get is 54 Mb/s. I'm using the latest Broadcom STA drivers.

Any suggestions?

---

### Post by pytheas22 on 2010-01-16
> I'm using the Netgear WN511B wireless card and the Netgear WNR834Bv2 router (both N capable) but I can't get N to work. The highest bitrate I can get is 54 Mb/s. I'm using the latest Broadcom STA drivers.

What's the output of these commands:

```
iwconfig
lshw -C Network
lspci -nn | grep -i broadcom
```

---

### Post by Dougie187 on 2010-01-17
> **hansheijmans said:**
> Hi there,

I'm using the Netgear WN511B wireless card and the Netgear WNR834Bv2 router (both N capable) but I can't get N to work. The highest bitrate I can get is 54 Mb/s. I'm using the latest Broadcom STA drivers.

Any suggestions?

From what I have been able to tell, you get N speeds, even though you aren't told you are getting N speeds.

I have read in other places that iwconfig and such tools in a terminal don't accurately tell you the speed of N connections. Either way, I would go online and benchmark your connection to see if it's close to N, or at least better than G. You could also preform some benchmarks with another networked computer doing simple file transfers and watching peak transfer speed. Preferably the other computer would be hardlined.

---

### Post by hansheijmans on 2010-01-18
@pytheas22 and Dougie187,

Thanks guys for your responses!

> **pytheas22 said:**
> What's the output of these commands:

```
iwconfig
lshw -C Network
lspci -nn | grep -i broadcom
```
I ran these command as root:

```
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11bgn  ESSID:"HeijmansNet"  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1E:2A:71:41:A2   
          Bit Rate=24 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
vboxnet0  no wireless extensions.

``````
# lshw -C Network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:19:6c:f4
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:dfcf0000-dfcfffff
  *-network
       description: Wireless interface
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 01
       serial: 00:18:4d:87:5e:3c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=10.0.0.3 latency=64 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:44000000-44003fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

``````
# lspci -nn | grep -i broadcom
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
04:00.0 Network controller [0280]: Broadcom Corporation BCM43XG [14e4:4329] (rev 01)

```> **Dougie187 said:**
> From what I have been able to tell, you get N speeds, even though you aren't told you are getting N speeds.

I have read in other places that iwconfig and such tools in a terminal don't accurately tell you the speed of N connections. Either way, I would go online and benchmark your connection to see if it's close to N, or at least better than G. You could also preform some benchmarks with another networked computer doing simple file transfers and watching peak transfer speed. Preferably the other computer would be hardlined.

I've included a screenshot of a file transfer from one of my NFS directories on my desktop computer (also running Karmic, using Broadcom Gigabit hardware, wired to my router). I performed the transfer several times to make sure the file was properly cached on my desktop (does that make a difference?). The tranfer rate the first time was approximately 7.8 MB/s, the last time up to 11.3 MB/s (which is close to the actual 100 Mb/s my Netgear WNR834Bv2 router is capable of).

Strangely enough my connection speed  is 24 Mb/s (as shown in the other attachment). The speed can fluctuate between 2 Mb/s and 54 Mb/s. If I set my router to use G only my connection speed is fixed at 54 Mb/s, but then the connection drops from time to time, so I set it back to N.

With my current router hardware I know 100 Mb/s is the limit, but I'm still not sure I can reach this speed over wireless.

Thanks in advance!

P.S.: I apologise for my late answers 'cause there's a 6 hour time difference between where you guys live and where I come from :redface:

---

