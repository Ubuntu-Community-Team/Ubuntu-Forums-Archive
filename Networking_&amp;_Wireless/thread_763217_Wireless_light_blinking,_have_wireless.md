---
title: "Wireless light blinking, have wireless"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by steveneddy on 2008-04-22
Upgraded to Hardy tonight.

Worked great.

I have a wireless connection, but the wireless light is blinking, driving me NUTS!

Intel Wireless, System76 Serval Performance Type 1

It worked great on Gutsy.

How can I get the light to stop blinking?

Is the Intel Wireless driver part of the kernel now?

---

### Post by steveneddy on 2008-04-23
I hate to bump.

The laptop is working fine on the internet, there are no performance issues.

The light is blinking and before, in Gutsy, is would burn solid with no blinking. It is a slow blink, not fast.

It is using the iwp3945 wireless drivers for my Intel wireless.

Any help appreciated.

---

### Post by markbegleyuk on 2008-04-23
Blinking! My light is not even blinking, it worked as it should on gutsy i.e. blinking while connecting and solid while connecting now with an up to update RC its always off.

---

### Post by steveneddy on 2008-04-23
> **markbegleyuk said:**
> Blinking! My light is not even blinking, it worked as it should on gutsy i.e. blinking while connecting and solid while connecting now with an up to update RC its always off.

Mine stops blinking after I stop using the Bluetooth mouse and internet for a couple of minutes, but continues to blink if I start surfing or move the mouse.

---

### Post by steveneddy on 2008-04-23
Fixed

```

sudo apt-get install linux-backports-modules-hardy-generic

```

---

### Post by another_sam on 2008-09-17
wifi light is blinking for me since I upgraded to Intrepid Ibex (8.10) one week ago. and it is not pleasant.

I noticed that blinks when there is Tx or Rx. As indicator is technically ok, but my PC is a laptop and the wifi led is 3cm below the screen, so I can perceive it constantly blinking and becomes uncomfortable.

any of you have also this issue?

---

### Post by anpu1 on 2008-10-05
hy!!

i have the same problem with ubuntu 8.10! before on 8.04 and 7.10 there was no blinking!!! But for now it is not anoing because the LED is almost under the keypad and i can't see it :) but if there will be any fixes great!!

bye

---

### Post by knottyboy on 2008-10-06
Same here since the 8.10 install. Works great but keeps blinking at me in odd intervals.

Used the...
> sudo apt-get install linux-backports-modules-hardy-generic
fix but said
> Couldn't find package linux-backports-modules-hardy-generic

As all of us have asked, help would be greatly appreciated.
Cheers,
kb

---

### Post by nickzeff on 2008-10-08
Yes. Crazy blinking since the upgrade to Intrepid for me too. Have a Dell D820 - can furnish more details if required!

Cheers

N

---

### Post by chadlewis on 2008-10-09
Steady, annoying blinking in Ibex as well.

---

### Post by steveneddy on 2008-10-11
To get the linux kernel backports you have to enable backports in your repos.

Go to

System --> Administration --> Software Sources

Click the third tab over that is labeled "Updates"

go down the list and click the box for unsupported updates (**hardy**-backports) or **Ibex** if that applies to you.

---

### Post by 4Play on 2008-11-01
unfortunatly the "sudo apt-get install linux-backports-modules-intrepid-generic" solution does not work on intrepid ibex :( installed the backport, restarted, and I am still staring at a very, very annoying blinking wifi led (blinks on tx and rx, as someone stated earlier)

I hope to find a solution to this quickly, it really annoys me.
I also hope they release a more bug-free compiz for intrepid, the current one is giving me hell :(

update: this bug is posted on [lauchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/250211"). There are some workarounds, like turning the led off, or reducing its blink cycle.

one of the posts on the bugreport recommends [this]("http://blog.drinsama.de/erich/en/linux/2008052101-iwlwifi-blinking.html") workaround. Didnt work for me, but I got the idea od the script and will modify it to my notebook (XPS m1530) when I have more time.

All I can say, is **DAMN** how the hell did they let this get into the final release?!?! its not exactly a hard to find bug, and plenty of people are having this problem!
Anyway, will post back here once I get a solution that works for me.

---

### Post by jpg_ny on 2008-11-01
Same problem on a Dell D620 led is blinking.

I tried the backports module without no luck
same as adding a none to in the /trigger

It is still a quite annoying continuous blinking.

---

### Post by steveneddy on 2008-11-02
This is an old thread regarding Hardy.

It should actually be closed at this point because I don't think that it matters after the -21 kernel update.

You may want to post a thread about this issue that actually involves Intrepid.

---

### Post by overdrank on 2008-11-02
Thread Closed at the request of the original poster.

---

