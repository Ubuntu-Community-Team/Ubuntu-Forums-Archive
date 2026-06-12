---
title: "Non-consistant internet speeds"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by cartisdm on 2009-12-29
I'm working at my boss' house in his office downstairs and I've noticed I can't get a consistent internet download speed (using speedtest.net).  Up in his office his computer is getting about 14Mb/sec download and about 2Mb/sec upload.  Downstairs where I am working I'm getting about 1-2Mb/sec and the same 2Mb/sec upload.

If I go outside to the driveway or something I can get like 10-12Mb/sec download.  I've tried this in Ubuntu, Mac OSX, and Windows using firefox and safari.  What would cause me to get weird connection speeds for download but upload staying the same? I am only about 20 feet from the router...

---

### Post by FinalCoyote on 2009-12-29
That is very strange sir.

Perhaps it's a problem on the router end, not the OS?

Actually, what occurs to me is, what hardware are you using?

It may be the fact that the wireless card in your laptop, etc, is limiting the DL speed, or is just outmoded in respect to your router.

I wish i got 14Mb/Sec download, i'm barely getting 1 Mb

---

### Post by Zzl1xndd on 2009-12-29
If you are using Wireless this isn't all that uncommon. The more Items causing interference between you and the transceiver  the slower and more erratic your Speeds/connection will be.

Can you tell us where the router is located, and if you know what is in the floor between the basement and the equipment.

---

### Post by cartisdm on 2009-12-29
> **FinalCoyote said:**
> That is very strange sir.

Perhaps it's a problem on the router end, not the OS?

Actually, what occurs to me is, what hardware are you using?

It may be the fact that the wireless card in your laptop, etc, is limiting the DL speed, or is just outmoded in respect to your router.


Can't be the wireless card, I've tried it with three of my own laptops.  And two of his desktops down here have the same problem and all the machines very between .8Mb - 2.5Mb...so strange


> 
I wish i got 14Mb/Sec download, i'm barely getting 1 Mb

You're telling me! I am lucky if I get 1Mb at my own house.  Whenever I have to download large files I be sure to bring my external HD and do them while I work:)

---

### Post by sting3r on 2009-12-29
Is it consistent when wired? I would try to change the router to higher channel just incase someone around you is using the same one..

---

### Post by cenzorrll on 2009-12-29
well, at such high speeds there are a number of things that could cause a bottleneck.  thick walls could mess with the signal, the server may have traffic, drivers may not be quite up to snuff, etc. (just a note, i have a broadcom 4322 wireless n card that doesn't work well with network manager, instead i have to use wicd)

another thing to note is that if you're on a wireless g network, the fastest downloads you're going to see are around 2.5mbps, whereas ethernet blows that away. 1 Gbit lan can max out at around 100 MB/s, I believe.

---

### Post by HarrisonNapper on 2009-12-29
> **tweakedenigma said:**
> If you are using Wireless this isn't all that uncommon. The more Items causing interference between you and the transceiver  the slower and more erratic your Speeds/connection will be.

Can you tell us where the router is located, and if you know what is in the floor between the basement and the equipment.

Ditto to this. Log in to the router and change the "channel" it broadcasts on. A lot of people leave it on default and the result is that microwaving a pizza or calling grandma throttles the wireless connection (there's a wonderful xkcd strip about that, actually). Speaking of which, I would make sure it's not positioned too close to other equipment that might cause interference (mostly referring to electronics, but also walls).

---

### Post by FinalCoyote on 2009-12-29
> **cartisdm said:**
> Can't be the wireless card, I've tried it with three of my own laptops.  And two of his desktops down here have the same problem and all the machines very between .8Mb - 2.5Mb...so strange

Well that's just odd. 

As [tweakedenigma]("http://ubuntuforums.org/member.php?u=161141") says, y'know, wireless connections fluctuate all the ******* time, so maybe there's lead in the ceiling :P

Sorry can't be more help here.

> **cartisdm said:**
> You're telling me! I am lucky if I get 1Mb at my own house.  Whenever I have to download large files I be sure to bring my external HD and do them while I work:)

And that's a good idea- well done!
Believe me I'd be doing that, if the hospital ever allowed us through the firewall.

---

### Post by cartisdm on 2009-12-29
I think I will take my best shot at changing the channel in hopes that something is simply interferring with the frequency.  Problem is the linksys router doesn't have the default Username & Password and my boss has absolutely no idea what it could be.

If that doesn't fix it it must be something in the walls in the basement the between the floor of the first level and basement ceiling.  Not much I could do about that other than maybe getting a wireless booster

---

### Post by Zzl1xndd on 2009-12-29
> **cartisdm said:**
> 
If that doesn't fix it it must be something in the walls in the basement the between the floor of the first level and basement ceiling.  Not much I could do about that other than maybe getting a wireless booster

If you really wanted to go all out you could run some wire. Although I'm not sure how your boss would feel about ripping open his walls. But Running some Cat6E through the whole house would be worth it.

---

### Post by cartisdm on 2009-12-29
Believe it or not I actually struck gold by find a .txt file with all the router settings in it on a random harddrive up in his office (this is amazing considering he has literally over 30 external HDDs laying around...).

It's set to broadcast on channel 3 but I can't change this setting.  Check out the screenshot and let me know which settings I could adjust that might help out

---

### Post by HarrisonNapper on 2009-12-29
> **cartisdm said:**
> Believe it or not I actually struck gold by find a .txt file with all the router settings in it on a random harddrive up in his office (this is amazing considering he has literally over 30 external HDDs laying around...).

It's set to broadcast on channel 3 but I can't change this setting.  Check out the screenshot and let me know which settings I could adjust that might help out

Looks like you have to change to Wide (400Hz) before it will let you change the channel. Just don't crank it up above channel 11 or, assuming the channels are the standard channels, you'll be in violation of the cap set by the FCC for power usage. 3 is probably a little too close to 1, try 6.

Cheers.

---

### Post by Zzl1xndd on 2009-12-29
> **HarrisonNapper said:**
>  3 is probably a little too close to 1, try 6.

Cheers.

There is a lot of Wifi Interference in my area and 6 has worked well for me

---

