---
title: "Annoying problem with NetworkManager in Feisty"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by marcelop on 2007-04-23
Hi all,

Feisty was out and in less than 5 hours I had it installed on my computer.   Due to some work commitments, I've been stuck with Windows for 6 months and was dying to come back to the good side of the force again.  I have to confess that I am terribly disappointed, though.  I am having some very annoying problems connecting to my wireless network using the NetworkManager, and this, from what I've read, was supposed to be one of the main advances on Feisty.  Anyhow... stop ranting and describe the problem dude ;-)

Machine:

[LIST]
[*]Thinkpad T60 (2007-83U)
[*]Fresh Ubuntu Feisty install from a CD image
[*]Intel Pro Wireless 3945 using the "proprietary" driver (the one installed when we click on the "green hardware")
[*]Edited the interfaces files so it only has the adapters I use
[*]Followed the tips described here to be able to suspend the TP: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T60)
[/LIST]

Router:

[LIST]
[*]Doesn't broadcast SSID
[*]Uses WEP (128bit)
[/LIST]

Problem:

Every time I start my machine (either from a clean boot or resuming from standby), I have to try to connect to my network from 5 to 10 times.  On each attempt I have to enter both the SSID and the WEP key and wait for it to (probably) timeout.  Then, magically, Feisty connects for 2 secs and, guess what, disconnects again.  Another 2 or 3 attempts, and I am up and running.  Randomly it asks for the Keyring password, which,btw, does have the WEP key for my network.

Any ideas on how to fix the problem?  At least reduce the amount of connection attempts?


What I was expecting:

[LIST=1]
[*]Start my machine (boot or from standby)
[*]Wait a few seconds
[*]Click on the NetworkManager
[*]See all the available networks + mine (I know it is hidden but it is available and I have already entered the details)
[*]Click on my network, wait a few seconds, maybe be asked for the keyring password
[*]Be up and running
[/LIST]

Am I expecting too much?

---

### Post by Kobalt on 2007-04-23
I have experienced the same problem actually... I think it comes from Network-Manager. What I've done is to remove it and use the good old configuration through editing /etc/network/interfaces. My wireless interfaces is configured this way : 
> auto wlan0
iface wlan0 inet dhcp
wireless-essid MY-SSID
wireless-key MY-WEP-KEY
And it works flawlessly (I even get a better signal force than with network-manager...)

And i use the good old network-applet in my notification area.

---

### Post by cvmostert on 2007-04-23
> **Kobalt said:**
> I have experienced the same problem actually... I think it comes from Network-Manager. What I've done is to remove it and use the good old configuration through editing /etc/network/interfaces. My wireless interfaces is configured this way : 

And it works flawlessly (I even get a better signal force than with network-manager...)

And i use the good old network-applet in my notification area.

What do you do when you want to log onto a public hotspot?

edit the file again?

---

### Post by Kobalt on 2007-04-23
Unfortunately yes... I scan for networks and enter the SSID and wireless key manually. Then I comment my home network and restart my connection : ```
sudo ifdown wlan0
sudo ifup wlan0
```

---

### Post by marcelop on 2007-04-23
Thanks for the tip Kobalt.  It is great to be able to rely on a helpful and creative community!

But ... ;-)

About 2 years ago I wrote a script that would do all the network configuration for me.  My approach was to have almost nothing in the interfaces file and do every single setting calling ifconfig and iwconfig.  It worked fine and, I hope, would still do the trick today.

My problem is to handle the disappointment, though.  Call me a crying-baby ;-), but I was expecting that one of the most advertised feature of Feisty, as you can read [here]("https://wiki.ubuntu.com/7.04Tour"), would work like charm, right out of the box.

Given the amount of people reporting related problems, it would be awesome to hear that the Ubuntu developers are working on a fix to be released in the next few weeks.  Or even better, that there is something ready right now ;-)

---

### Post by Kobalt on 2007-04-23
You're surely not a crying-baby, I'm as desperate as you are to finally have a graphical networking tool rock solid... 
And I'm wondering when is that to come : Gusty, Gutsy+1, ...

---

### Post by agurk on 2007-04-23
T60 1951-F3G here, and all I can offer a fellow thinkpadder is sympathy and some random stabbing in the dark.

* I have *not* disabled powernowd as described in thinkwiki, yet I don't have any problems with suspend/resume. Perhaps it's worth removing those hacks to see if it improves your wireless situation? I guess not though, since you probably added them to be able to susp/resm at all.
* BIOS updates can do some funky things sometimes, perhaps try up- or downgrading?
* FWIW, I upgraded from Edgy, I didn't do a clean install.
* FWIW, my /etc/network/interfaces looks as follows:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

---

### Post by sudo_t43p on 2007-04-24
Hi all,

Got rid of my Thinkpad T43P because of the GFX card (ATI, will never ever buy ATI again!) and got a  Thinkpad X60s. On my T43P WiFi worked like a charm (had an older WiFi card, 2200) but on my X60s I have the same problems you have.

Has anyone of you noticed that the 3945 card gets really hot? Is it possible to force this card run constantly on 11mbs etc (fingers crossed, it will take care of the heatproblem)?

Thanx!

BR,
Chrisse

---

### Post by agurk on 2007-04-24
> **sudo_t43p said:**
> Has anyone of you noticed that the 3945 card gets really hot?
Hmm, no, can't say that I have, nor do I know where it's actually located. Do you have some fancy temperature measuring application that tells you this, or can you actually feel that something other than the CPU is heating up inside the laptop?

---

### Post by eg-maverick on 2007-04-24
> **marcelop said:**
> Thanks for the tip Kobalt.  It is great to be able to rely on a helpful and creative community!

But ... ;-)

About 2 years ago I wrote a script that would do all the network configuration for me.  My approach was to have almost nothing in the interfaces file and do every single setting calling ifconfig and iwconfig.  It worked fine and, I hope, would still do the trick today.

My problem is to handle the disappointment, though.  Call me a crying-baby ;-), but I was expecting that one of the most advertised feature of Feisty, as you can read [here]("https://wiki.ubuntu.com/7.04Tour"), would work like charm, right out of the box.

Given the amount of people reporting related problems, it would be awesome to hear that the Ubuntu developers are working on a fix to be released in the next few weeks.  Or even better, that there is something ready right now ;-)

I don't consider you a cry-baby. The whole reason (1 reason and one reason only) for me to upgrade to Feisty was that all the wireless problems would be fixed. As best I can tell, it is no better. I am frustrated with the amount of time I wasted, not to mention the broken things I had to patch (i.e. VM) just to get back to where I was. I can't stand having to go through the keyring each time I change wireless networks.
Argh

---

### Post by marcelop on 2007-04-27
Thanks for the "you are not a cry-baby" support ;-)

I gave up and went back to Edgy without the NetworkManager.  Is this what I would like? Hell no.  But, again, if one of the most advertised features doesn't work, I'd rather stay with something I trust.

Anyways, I just found another post where other users are reporting the (almost) same problem:
[http://ubuntuforums.org/showthread.php?t=414793](http://ubuntuforums.org/showthread.php?t=414793)

I will be adding a link to this post there.

---

### Post by sudo_t43p on 2007-04-28
> **agurk said:**
> Hmm, no, can't say that I have, nor do I know where it's actually located. Do you have some fancy temperature measuring application that tells you this, or can you actually feel that something other than the CPU is heating up inside the laptop?

Well, actually I didn't find any pics on the web where CPU and WiFi card is located on my X60s so I grabbed a screwdriver and opened my computer (I have pics I someone is interested..). On my right side (where "IBM ThinkPad" logo is located) I found my WiFi card and it get's quite hot,  hotter than my CPU (CPU is about 42 - 48 celsius). Well, it is actually a wild guess that it is getting hottar than my cpu beacuse my laptop is very slim where WiFi is located = bad air flow.

But I would guess that by dropping WiFi from 54 to 22 (or 11) the card would be cooler? I'm never transfering big files over WLAN so I do not need 54.

So if anyone know how-to force WiFi card to work on 22 or 11 I would be glad. I noticed this is possible with kwifimanager (in KDE)..

BR,
Chrisse

---

### Post by agurk on 2007-04-28
I see. Well, 'man iwconfig' had this to say about bit rate:
> rate/bit[rate]
              For  cards  supporting  multiple  bit rates, set the bit-rate in
              b/s. The bit-rate is the speed at  which  bits  are  transmitted
              over  the  medium,  the  user  speed of the link is lower due to
              medium sharing and various overhead.
              You may append the suffix k, M or G to the value (decimal multi-
              plier  :  10^3,  10^6  and  10^9 b/s), or add enough '0'. Values
              below 1000 are card specific, usually an index in  the  bit-rate
              list.  Use  auto  to select automatic bit-rate mode (fallback to
              lower rate on noisy channels), which is  the  default  for  most
              cards, and fixed to revert back to fixed setting. If you specify
              a bit-rate value and append auto, the driver will use  all  bit-
              rates lower and equal than this value.
              Examples :
                   iwconfig eth0 rate 11M
                   iwconfig eth0 rate auto
                   iwconfig eth0 rate 5.5M auto
You'd probably have to write something somewhere to make such changes permanent to survive a reboot.

---

### Post by sudo_t43p on 2007-04-29
> **agurk said:**
> I see. Well, 'man iwconfig' had this to say about bit rate:

You'd probably have to write something somewhere to make such changes permanent to survive a reboot.

Auhm, why didn't I think on looking in the manual.. Thanx alot my friend! I'm now running my card on 11m and hopefully it will run cooler! I guess that if I want to run it when X starts, just copy to sessions.

Thanx again!

BR,
Chrisse

---

### Post by LoSt180 on 2007-07-10
> **eg-maverick said:**
> I ....I can't stand having to go through the keyring each time I change wireless networks.
Argh

I'm not sure if you've already found it or not, but this seems to be working for me to avoid entering the Keyring password every time:

I'm still using Edgy, so not positive this will work in Feisty.
taken from here: [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

> Automatic Keyring

To bypass having to enter the keyring password at every login when your keyring password is the same as your login password, follow the following instructions: 
```
naaman@freddo:~$ sudo apt-get install libpam-keyring
naaman@freddo:~$ echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm
```
To change keyring password, install libpam-keyring as above then run: 
```
naaman@freddo:~$ /usr/lib/libpam-keyring/pam-keyring-tool -c
```

After entering this I had to go to >System>Keyring Manager and it prompted/asked me if it was okay for the application to auto use the Keyring.

After that it works fine. Now I just need NetworkManager to auto sense/connect to Hidden SSID network on boot up.... **continues searching for a solution**

---

