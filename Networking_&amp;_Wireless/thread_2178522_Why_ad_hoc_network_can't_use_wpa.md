---
title: "Why ad hoc network can't use wpa?"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by salv-lorenzo on 2013-10-03
Hi, I'm doing some research for my university about my thesis. My professor ask me to inspect about the lack of possibility to create an ad hoc network with wpa and wpa2. You can only use wep. Maybe it's something obvious and I'm trying to ask here. It's a ubuntu lack, a linux lack, a standard lack or something deeper?
Thank you very much in advance :)

---

### Post by theDaveTheRave on 2013-10-04
Can I add a me too, I'm curious why it doens't work?

I wonder if it is something to do with WPA not being part of the TCP/IP network layer, or the 'size' of the keys.

from [wikipedia WPA page]("http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access")
>  The WPA protocol implements much of the IEEE 802.11i standard. Specifically, the Temporal Key Integrity Protocol (TKIP) was adopted for WPA. WEP used a 40-bit or 104-bit encryption key that must be manually entered on wireless access points and devices and does not change. TKIP employs a per-packet key, meaning that it dynamically generates a new 128-bit key for each packet and thus prevents the types of attacks that compromised WEP.


From which I summise....

WPA is continually renewing / changing it's key during communication, and hence expensive in terms of authentication, WEP doesn't change, so the link is 'weaker' but more flexible.

My assumption is that if you have a key with one access point, then move to another, it won't recognise the key that you generated (as this AP didn't issue or ack it), and so can't send / receive the packet.

Of course I could be wrong... ;)

David

---

### Post by salv-lorenzo on 2013-10-04
Could be something similar. But now, searching a little, I've found this[URL="https://help.ubuntu.com/community/WifiDocs/Adhoc"]
https://help.ubuntu.com/community/WifiDocs/Adhoc[/URL]
look under encryption.
Seems that in some way it's possible :/ Based on this seems that is a lack of wpa_supplicant that haven't it by default O_o

---

### Post by theDaveTheRave on 2013-10-06
Indeed, I think I read something similar on wiki.

It all seems to come down to WPA being a stronger encryption process, you may have a single password for the wifi hook, but each packet sent gets it's own ID / encryption tag.

However looking at the details of the link that you posted, it looks as though avahi-autoip may be a potential solution??

Also look at this thread on [Askubuntu]("http://askubuntu.com/questions/154779/why-is-wpa-encrypted-ad-hoc-mode-disabled-in-12-04"). As you mention is may be a bug in WPA, or a hardware issue.


On the [bug report]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/905748") linked to in the above thread, if you look at comment 14
> 
we can rely on that test because Android does support ad-hoc for WPA. WPA2 is another story ;)


So I must be a hardware or kernel / driver issue

I also found this on [qnx.org]("http://www.qnx.org.uk/developers/docs/6.4.1/io-pkt_en/user_guide/wpa_background.html")

[/quote]
Ad hoc mode lets you create a wireless network quickly by allowing wireless nodes within range (for example, the wireless devices in a room) to communicate directly with each other without the need for a wireless access point. While being easy to construct, it may not be appropriate for a large number of nodes because of performance degradation, limited range, non-central administration, and weak encryption. 
[/quote]

So the question then becomes how best to set up an ad-hoc network somewhere?

I guess the best solution would be as follows:
Have a well secured main network, running off a DHCP server, that would issue out the IP addresses - these addresses would only be given to 'known' clients (fix the clients via mac address).

Each client would then set itself up as a hot-spot on a 'less secure' WEP password, but would use the IP that was given to it via the DHCP server so no IP, no hot-spot, no connection - and hence should be secure ??

NOTE I say 'should be secure' as I'm not sure if this type of set up is possible (or may be too heavy in terms of config).

I did a little more reading, and I've arrived at the realisation that an ad-hoc wifi network is synonymous with Wifi Access Points, ie a 'hotspot'.

Hotspots are 'public' wifi connections, so having them encrypted would be a bit 'strange', and would make the whole thing a little silly. This is probably why when you go to certain places that claim to have 'public' wifi when you try to log on you find that there is a required code key, that you have to ask for (I've mostly found this in restaurants, and it prevents people from connecting who aren't eating at the restaurant).

More thinking.

When you log onto a 'hotspot' you are in fact hooking into a Wifi Access Point, and then creating yourself as another access point, that other can connect to, so everyone has to be able to 'see' that you are present.
So you are now acting as a wifi hook, and you are visible.
To be secure you should be invisible (not so helpfull if you want to be an ad-hoc network, where everyone can see everyone else), Also for security you should have a password, and issue out IP addresses, hence you need to be a dhcp also. So now you need every pc to be a DHCP, but to be configured so as they are slaves to the main master DHCP server.
That should be fine in a business setting, where all pc's can be set up the same way, but not so good if you head out to a public environment!

Then the question is how does Android support the ad-hoc mode, and how does it stay secure? it is something to do with the Java VM? or is it at the kernel level (my guess is it is in the Java VM somewhere). Then the second question is, if someone sets up an ad-hoc network from an adroid device, with a password, is that ad-hoc network actually correctly secured?

interesting reading....

I think i'll stick to true wifi networks, with a wpa2 PSK key. Although I may test the 'ad-hoc' thing if I ever get an adroid device....

David

---

### Post by theDaveTheRave on 2013-10-06
quick note I just found this in response to a windows 7 ad-hoc question over on [superuse]("http://superuser.com/questions/254872/i-cant-set-up-an-ad-hoc-network-anymore").....

> 
    The ad-hoc part of the 802.11 standard (wireless) is very poorly implemented by some wireless network device manufactures
    AdHoc does not support WPA, and many vendors have issues with using WEP on AdHoc
    It might be preferable to use something like Virtual Router or Connectify which would allow you to make an infrastructure (normal wifi) network using a Windows 7 Host

which got a rather tetchy reply
> 
AdHoc supports WPA2, get your facts straight. The 802.11-2007 and 2012 standard clearly specifies how to use RSN in IBSS mode. Whether it is implemented is another thing (if you wanna try, Linux supports IBSS RSN on more devices than windows)


So I guess you need to get a copy of the standards and confirm what the truth is... I guess you are an it student working on wifi and network security as your thesis, or maybe intending to write a kernel side patch to include WPA / WPA2 in ad-hoc mode.

I guess I'll need to grab a copy of the 802.11 standard and have a read at some point.... <yawn>

David

---

### Post by salv-lorenzo on 2013-10-06
Thank you very much for all the interest you are giving to this thing :)
Yes, I'm an it student and I'm investigating about possibility to use at least wpa encryption for manet.
About android professor said to me that with nexus 7 and cyano there was some problem to do that but I haven't seen anything about that cause he told me of something doing in the past. But reading around seems that with modded kernel should be possible.
I've found that thread on askubuntu too. Looking in the bug report page seems that the "fix" was the disabling of the wpa ad-hoc function. What I've understand is that too large number of nic doesn't work properly so it's better to disable the function.
Also, following your advice, I've read the standard 802.11 2007 and I've found this:

8.1.3 RSNA establishment
A STA&#8217;s SME establishes an RSNA in one of four ways:
a) ...
c) If an RSNA is based on a PSK in an IBSS, the STA&#8217;s SME executes the following sequence of
procedures:
...

If one of the way to establish a RSNA is using an IBSS this means that is possible to do.
So...for what I've understood it's an hardware problem; cause of this there's a software block; the standard isn't totally followed by the manufacturer; about android should work but maybe isn't obvious.
What do you think about this summary?

---

### Post by theDaveTheRave on 2013-10-07
Reasonable summary...

But does the standard state anywhere that this 'should' be possible in IBSS using RSNA, what are the sequence of events? The devil will be in the detail, and how the standards defines an-hoc network (it may have a clause somewhere about the state of the RSNA security, something along the lines of....

A security password should be able to be used when connecting to an IBSS, but the implementation is left to hardware / software vendors : So the connection must be able to have a password entered to connect to it, but in and ad-hoc network encryption of packets may be optional.

so now  you need to test if the ad-hoc network created via an android device truly is 'secured with WPA'

An ad-hoc network that requires security seems a bit counter to the idea where all equipment will communicate with other equipment automatically.

My thought was that this type of connecting should be silent, and require no user input ~ so needing a password would be a tad counter productive to the idea.

That said: An ad-hoc secure network would be idea in a business environment, reducing the need for specialised wifi access points.

If my understanding of ad-hoc is correct, the difference between using multiple access points and ad-hoc is that on an ad-hoc network each device is visible to all the other devices, and the device effectively becomes an access point.

Maybe that would be the way to implement it.

I a user accepts to use ad-hoc, the device would
~ connect to the nearest wifi access point (using WPA).
~ make itself visible to all other devices 
~ advertise to other devices that this devices can act as a wifi access point (this may or may not be an open access point)?

The problem here would be if this can done in software solution.
However if android works, you may be able to bend the implementation ~ I doubt that all mobile phones are using the same wifi chip (although google may be able to stipulate that to the manufacturers), or it may be a part of the radio communications that allready come with a mobile phone.

You really need to get a bunch of android devices and test them out... as you are a student you must have plenty around you all the time, just need to get your mates to test them all together.

The test would be that you connect the first device to the Wifi access point ~ using wpa or similar.
Then when you share the connection to others, that this connection is also secured (so the info is not sent unencrypted over the ether)
When you have connected multiple devices, they can all see and communicate directly with any of the other devices 
~the catch here is the 'directly'. It may be the connection does in fact go via the 'wifi access point' 
so the test would be for the wifi access point to be taken off line and all the devices to be able to continue to communicate with each other, then take the first device that connected (that was sharing its connection to the wifi access point) to be taken off line, and test again.

Remember that the wifi access point acts like a router, it will take a signal sent from one unit, and rout it out to another. If I correctly understand ad-hoc mode, each unit effectively becomes a router, so you can always find a direct one-2-one pathway.

I suspect that each unit will send the signal to ALL the units, with only the unit being interested showing any response (the question here is to capture and read the signal from all the units (and having that signal encrypted, and only being able to be decrypted by the exptected receiver).

It would be cool if you found that the ad-hoc network where actually 'not secure' ~ you'll need a desktop to capture the communications between phones are see if they are 'encrypted' or not - wireshark should do this for you.

I say it would be cool, but I mean it in a 'raise a bug with google' way, not a cool for the consumer way.

You could also look into the code for Mego / Tizen / Harmatan.... and see how they implement a solution (if they have one).

David

ps. quick thought.

Does the android device need a WPA password to connect to the primary 'wifi access point' but when passing the network connectivity to other this network is in fact an 'open' network.
Also c

---

