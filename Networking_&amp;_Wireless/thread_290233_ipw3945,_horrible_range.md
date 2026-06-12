---
title: "ipw3945, horrible range"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by TorchlightJay on 2006-10-31
So this is the scenario. I am running edgy on a core 2 duo processor. I am using the 2.6.17.10-generic. I just installed an ipw3945 mini pci express card into my notebook. I am using KNetwork Manager and it reads my card (eth1) but it has HORRIBLE range. Horrible of course being the understatement of the year. unless I am right by the router or maybe 3 feet from it. Any further, it sucks. I know it's not the router because on my previous notebook, things worked just fine. I was able to go to my bedroom and do work on my notebook with no problem. Now I have not installed IPW3945 because mine worked out of the box. I didn't need to install them. Maybe I should but when I try, it won't work, it keeps saying that something is wrong ith my ieee80211 but I know I installed it. 
  If anyone has any idea what's wrong, I'd like to hear it. This is really frustrating.

---

### Post by TorchlightJay on 2006-11-01
come on someone must have an idea

---

### Post by TorchlightJay on 2006-11-02
I think I may have solved some of it. The card is fine and has 54 capabilites but my kwireless tells me that it only goes up to 11. This sucks for me and the range is still about 4 or 5 feet. I am using the default ipw3945 driver within EDGY (I am using an ipw3945ABG). I don't know if there is a setting I need to change or something. Everytime I try to install the driver, it fails. it keeps telling me that something is wrong with ieee80211. Oh well. Help me fix it.

---

### Post by usererror on 2006-11-17
This is a really dumb question and I don't mean to insult anyone, but when you installed the 3935 card into the laptop did you reconnect the antenna's?  my brother had a similar problem when he got his laptop back from dell...they forgot to plug in the antenna's on the damn card!

on a side now, i have a question?

I'm running the 3945 card as well.  but i can't see my A-Radio...i was going to install the driver from intel's website do i just need to add the IEEE80211 package?  or do i have to recompile my kernel also?  I read the kernel part in this thread:

[http://www.ubuntuforums.org/showthread.php?t=294842&highlight=ieee80211](http://www.ubuntuforums.org/showthread.php?t=294842&highlight=ieee80211)

thanks!

---

