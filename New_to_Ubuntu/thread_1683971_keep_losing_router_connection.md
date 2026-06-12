---
title: "keep losing router connection?"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by gmenfan83 on 2011-02-08
i keep losing my router connection ,,,this has just started this morning and im not sure why ,,,,its not my router i know since my droid will mantain connection and so will my ps3 at the same time my laptop keeps losing it....it will be on for a short period hen go offline then either restart on its own or i have to manually reconnect,,,,any ideas?

---

### Post by robsoles on 2011-02-08
Assuming connection for laptop is wifi:

If it started this morning and you haven't been playing with power settings yesterday or something, then **perhaps** a neighbour has gotten themselves an (or reconfigured their) AP and it is now on the same channel as your wireless access point.

Handy you have that android :)

Go grab 'wifi analyzer' from the 'market place' on your droid phone and use it to see if there is a second wireless router broadcasting on the same channel as yours - take it to where the laptop is when it is giving you this trouble mostly.

---

### Post by gmenfan83 on 2011-02-08
> **robsoles said:**
> Assuming connection for laptop is wifi:

If it started this morning and you haven't been playing with power settings yesterday or something, then **perhaps** a neighbour has gotten themselves an (or reconfigured their) AP and it is now on the same channel as your wireless access point.

Handy you have that android :)

Go grab 'wifi analyzer' from the 'market place' on your droid phone and use it to see if there is a second wireless router broadcasting on the same channel as yours - take it to where the laptop is when it is giving you this trouble mostly.
thanks for the reply and yes i have just found more ways to use my awesome droid x lol thanks!!,,,it does have another user on the same channel but these are the same users that always have been there and i only know this since when i have scanned in the past for wifi those same users were there,,,,would you recommend switching channels?

---

### Post by robsoles on 2011-02-08
If the 'competing' signal is more than half of the strength of your own signal in the area you use your laptop then it is worth while to look for a channel that hasn't got nearby competitors on it.

If competing signals are less than a third of your own signal it is probable that your signal is 'winning' quite adequately and the competitor(s) isn't making this difference - we'll need to pursue something else if you have 'most of a channel' to yourself and still getting this problem.

---

### Post by gmenfan83 on 2011-02-08
> **robsoles said:**
> If the 'competing' signal is more than half of the strength of your own signal in the area you use your laptop then it is worth while to look for a channel that hasn't got nearby competitors on it.

If competing signals are less than a third of your own signal it is probable that your signal is 'winning' quite adequately and the competitor(s) isn't making this difference - we'll need to pursue something else if you have 'most of a channel' to yourself and still getting this problem.
i do indeed have the competing signals beat ,,,,they are not even a quarter of what my strength is at best,,,,whats odd is it happened about 5 times in a row like clockwork earlier when i first posted then stopped and has only happened once or twice since about 4pm,,,,i have checked my settings and didnt even ever mess with any of them ,,,lol it just happened go figure!!

---

### Post by Tiberion on 2011-02-09
this indeed is strange post back if it continues

---

### Post by robsoles on 2011-02-09
Although it could just be solar flares or similar, Let's climb further in then:

What are circumstance after disconnection? As in, is the wifi remaining apparently active and you just left click network icon and re-select your AP or do you have to re-activate the wifi device? (could say, "what do you mean by 'manually reconnect' above? :))

The more of the following questions you answer the quicker this will be fixed, one reason will be because details are like bait to people with more experience and to find the source of the problem for you I need bigger clues myself ;)

Were there updates from Canonical anytime within about 48 hours before this problem started?

What version of Ubuntu is it that you are using?

What make and model is the wifi device? (onboard/builtin, pcmcia, dongle etc)

What make and model is computer? (specifically motherboard details)


I am checking out my netbook to see if I can find options buried away as to something like 'inactivity disconnect period' or anything relating to depowering my wifi behind my back - So far with Ubuntu I haven't sprung 3 different laptops starting this kind of caper in just over a year.

---

### Post by gmenfan83 on 2011-02-09
> **robsoles said:**
> Although it could just be solar flares or similar, Let's climb further in then:

What are circumstance after disconnection? As in, is the wifi remaining apparently active and you just left click network icon and re-select your AP or do you have to re-activate the wifi device? (could say, "what do you mean by 'manually reconnect' above? :))

The more of the following questions you answer the quicker this will be fixed, one reason will be because details are like bait to people with more experience and to find the source of the problem for you I need bigger clues myself ;)

Were there updates from Canonical anytime within about 48 hours before this problem started?

What version of Ubuntu is it that you are using?


What make and model is the wifi device? (onboard/builtin, pcmcia, dongle etc)

What make and model is computer? (specifically motherboard details)


I am checking out my netbook to see if I can find options buried away as to something like 'inactivity disconnect period' or anything relating to depowering my wifi behind my back - So far with Ubuntu I haven't sprung 3 different laptops starting this kind of caper in just over a year.
ok there was an update about 3 days prior to this starting,,,,tere were a  lot of updates and i know i should have read each one but dummy me did  not so i cant tell you if a component that would affect this was even  updated,
i am using ubuntu 10.10
what i mean by manually reconnect is sometimes when it disconnects i will have to go to my signal/wifi/internet connection icon in my panel and select it then select where i want to get my wifi from according to what scans (me or my neighbors) then once i select to connect to my router it comes back on,,,one time it did not and i had to restart my laptop,then other times that it disconnects it will auto connect itself right after it disconnects (very odd),,,and again my settings have not changed or not that i have noticed at least,
i am at work away from my router so forgive me if i cant provide enough info on it but its a Linksys
my laptop is a Toshiba Satellite A205
..thanks for the help

---

### Post by robsoles on 2011-02-10
<snip> - sorry, wrong thread!

---

### Post by lew2110 on 2011-02-10
> **gmenfan83 said:**
> i keep losing my router connection ,,,this has just started this morning and im not sure why ,,,,its not my router i know since my droid will mantain connection and so will my ps3 at the same time my laptop keeps losing it....it will be on for a short period hen go offline then either restart on its own or i have to manually reconnect,,,,any ideas?

I also have this same problem.

I have found every time leave my computer on and inactive for half an hour or so, when I return I am sometimes disconnected from my router in which I need to reboot to connect again... I have recently enabled the firewall, I'm not sure if that has anything to do with it??

Like you, I no it's not a router problem because my iPhone and ps3 are always connected.

---

### Post by gmenfan83 on 2011-02-10
well i am happy to report that this has not happened to me in 2 days,,what was causing it one may never know lol but i will keep an eye on it and leave this thread opened a little longer since others are reporting the same issue

---

