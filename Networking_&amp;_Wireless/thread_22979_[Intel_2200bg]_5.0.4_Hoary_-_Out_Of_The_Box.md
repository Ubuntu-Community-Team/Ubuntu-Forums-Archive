---
title: "[Intel 2200bg] 5.0.4 Hoary - Out Of The Box"
date: 2005-03-30
forum: Networking &amp; Wireless
---

### Post by Derek Djons on 2005-03-30
Hello all,

This is my first time using Ubuntu Linux. Yesterday I decided to swap the harddrives on my gaming machine and install Ubuntu. A friend of mine told me much about the Operating System's advantages. One of the biggest advantages in my opinion is that it's similar to Debian but much more user friendly.

Before Ubuntu I used SuSE Professional 7.3 till the current editon 9.2. As always I hook up on official forums in order to solve problems, share opinions and help where ever I can.

Well, yesterday I was really stoked on seeing Ubuntu working. And I must admit, I haven't seen a better Linux distro yet. I know it's a little flavour-question thing. But if you compare Ubuntu on installation / use / updating -ease it's just great. Today I decided to install it on to my notebook. It's a Acer Travelmate 290 clone. The only difference is the name of the shop instead of the Acer logo. As with all other Linux distributions I prepared myself for a long night installing and configuring Intel 2200bg drivers. But that wasn't needed I discovered really fast.

I tested a lot of distributions in the past. Redhat, Fedora, SuSE, Debian, etc. are all on my list. And yes, the most of these distributions do not support Wireless networking 'Out Of The Box' what means you'll have to use the famous sourgeforge drivers. SuSE Linux was one of the distro's I tried which supported the Intel 2200bg card automatically. This was just great. After installation, you had to make sure that two .rpm packages where installed (wireless tools and ipw2200) and it was time to roll.

Before installing Ubuntu on my notebook today I spend some time reading about the Intel 2200bg issues with Ubuntu. I assumed I would have to install the sourgeforge drivers too. But no. During installation I noticed that Ubuntu recognized the wireless adapter correctly. This was a good sign. After installation I immediately run Ubuntu Update Manager followed by Synaptic Package Manager which I both used to update my installed files to the newest version and download updates / patches. This all went down using a 10/100 cable.

After that it was time for wireless networking with my Intel 2200bg card. First thing I did was switching off the 'Encryption'. Further more I switched the Authentication mode to 'Open system'. This saves a lot of time when you're trying to find out why it doesn't works :)

When I looked in 'System -> Administration -> Networking' and selected my wireless adapter I immediately saw that all the necessary options were present.

- ESSID
- WEP
- Etc

When I selected the ESSID tab I immediately saw my essid name standing there. Since I disabled the encryption and authentication the only thing left to do was selecting DHCP. Within no time I was surfing wireless.

The reason I'm writing this is because there are still a lot of people who have all kinds of issues with the same wireless networking card. It's interesting to see that several people decide to use sourgeforge driver saying that it doesn't work 'Out Of The Box' while a few others also report that it worked immediately without installing sourgeforge drivers.

Keypoints which were important for me during installation:

* Router with disabled encryption and authentication
* root terminal -> iwlist eth1 scanning (information about found essid by the card)
* root terminal -> route (if your gateway isn't listed, it won't work)
* root terminal -> ifconfig eth1 (rx / tx info and ip address info)

I hope I added some value into the discussion and problem solving with the Intel 2200bg card.

---

