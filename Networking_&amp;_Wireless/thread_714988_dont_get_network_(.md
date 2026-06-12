---
title: "dont get network :("
date: 2008-03-04
forum: Networking &amp; Wireless
---

### Post by jrockpunk1 on 2008-03-04
hi ive got windows XP on one computer, and ubuntu on my laptop. ive got a belkin wireless G router connected to XP, however everythings messed up on it, and i would need to set up everything again if i wanted to make a new network. i dont know anything about how to set up wireless networks on ubuntu, and have googled to no avail on setting up wireless networks. could someone please explain to me how to set this up? i know i have to go to system>administration>network>wireless network>change the settings>and check the box. but i have no idea how to configure the belkin router to work with my ubuntu PC, or what i need to change the settings to.

any help much appreciated,

jrockpunk1

---

### Post by hookzilla on 2008-03-05
I'm a newbie too and know how you feel.  Linux is not like Windows in many ways.  Wireless is tough.  I've still not got it working.  However, this may be due to my adapters chipsets.   I suggest you do a search in this forum for your card brand and model.   That well get you started

---

### Post by schmildo on 2008-03-05
Yeah post as much information as you can such as the router model, and your wireless card model (if you can find it, sometimes that's not so easy)

You don't normally need to change your router's setup at all to use linux, it should be the same as windows. (mine is)

But naturally configuring wireless on windows is not the same as linux.

It's important no matter what operating system you're running to find out what your wireless security settings are set to on the router, and what they 'can' be set to. I don't know much about the belkin routers myself but the manual should have the information you need, look for encryption & authentication of wireless networks , there will only be about 4 settings or so to worry about.

Once you have that information it won't be hard to find someone here to help you with connecting to the router with those settings. Sometimes it's easier to try turning off the wireless security on the router while you attempt to connect from linux for the first time, just so that you know it will work at all. Then once that's working, enable the security settings on the router and adjust linux to suit.

Run a few commands from the console of linux:

sudo ifconfig -a
sudo lshw -C network
sudo iwconfig

and print the output for others to see here (we might be able to see problems  for you)

---

