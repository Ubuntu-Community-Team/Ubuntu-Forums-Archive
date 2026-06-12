---
title: "How to get Atheros AR5006EG (xp) AR5006X(vista) working in Fiesty"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by stuck on 2007-05-24
Now I'm on my 5th re-install this week, I though I would post this as it is the only way I've found to get my wireless card to work on a fresh (10mins old) install of Ubuntu 7.04.

XP calls the Card ATHEROS, Atheros AR5006EG.

Vista calls the card ATHEROS, Atheros AR5006X.

It doesnt work on a fresh install of Ubuntu 7.04.

So here goes how I fixed it (maybe if developers are looking they could fix it???)

When Ununtu starts for the first time a pop-up appears about restricted drivers.

Click on it, and un-check the box on: Atheros Hardware Access Layer (HAL), then press "Close"

Ignore the re-boot message.

Go Applications>>>Accessories>>>Terminal

Type:

Sudo bash

enter password when requested

Type

ifconfig wifi0 down
ifconfig ath0 down

Now you can close the Terminal and re-boot your machine.

You should now be able to connect wirelessly to the net. There is no need to re-enable Atheros Hardware Access Layer (HAL).

This is the quickest/only method Ive found that works.

Please copy, distribute, call it your own what ever. But all my googling didnt get me an answer. I only found this out by trail and error. So I hope this puts something back into the Ubuntu community.

Dont ask about madwifi-ng. I still havnt worked out how to get it working/installed yet.

---

### Post by mengfei on 2007-05-25
Hey thanks! I know my atheros is giving me trouble. It shows networks, but can't connect to any. I'll give this a shot.

---

### Post by stuck on 2007-05-25
Hope it helps, let me know. Sorry if you have any more problems I wont be able to help you as I'm a complete newbie to Ubuntu and finding it very difficult.

My wifi card wouldnt even see networks.

---

### Post by duphenix on 2007-08-04
Thanks for posting this info, it worked great on my everex xt5000t

---

### Post by neversummer32 on 2007-11-12
First off I am very new to linux, about 4 hours into it.  

I have loaded ubuntu on a xt5000t and had the sound issues however I finally got this somewhat resolved.  

Now Im having an issue with getting my wireless card to work.  

Has anyone been able to get this to work without reinstalling as suggested in this thread?  I just would like to not go through the setup again if at all possible.

Thanks

---

### Post by wilerk on 2007-11-20
The other day I had the wireless working, in Wifi Radar I saw networks around me, the very next day I can't see anything. My Dell Axim finds networks so they're up and running.

Could someone please help me in fixing this?

Thanks,

Xander

---

### Post by wilerk on 2007-11-20
Never mind...

When I switched it off and on at the front of the machine, I all of a sudden pick everything up. Weird how this works...

---

