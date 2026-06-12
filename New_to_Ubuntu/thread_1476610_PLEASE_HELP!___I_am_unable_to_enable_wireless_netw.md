---
title: "PLEASE HELP!   I am unable to enable wireless networking"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by robot_chicken_parm on 2010-05-08
I am currenty accessing this site from my windows xp pc because i cant conect to the net on my ubuntu laptop.  i can connect through auto etho, but for some reason wireless networking is disabled.  when i right click on the networking icon in the notification area, the box for enable wireless is un-clickable. i dont iknow what i did to screw this up.  PLEASE HELP!!!   thanks in advance.

---

### Post by robot_chicken_parm on 2010-05-08
aso on a completly unrelated topic, i have a small question:  why doesnt my avitar shiow up to the left of my posts in ubuntuforums like everybody else's?

---

### Post by sir_nasty on 2010-05-08
first things first, click ... um I'm going from memory so don't quote me 100% on this... System, preferences hardware drivers and see if it finds a wireless driver for you... if not then post some system specs about what you have

---

### Post by cariboo on 2010-05-08
That's your profile picture on the left, when you have your avatar set up right it will be on the right side of the user cp  page

---

### Post by lavinog on 2010-05-08
What version of ubuntu are you using.  If you are using Lucid, did you upgrade from karmic, or did you do a fresh install?

Does your laptop have a wireless switch or button?  after attempting to activate the wireless, type dmesg in a terminal and look at the last couple of messages...sometimes dmesg will give you a hint as to what is going on.

My neighbor's wireless stopped working recently...it turned out that the plastic switch face dislocated from the actual switch....It took us a while to figure that one out.

---

### Post by sir_nasty on 2010-05-08
> **lavinog said:**
> What version of ubuntu are you using.  If you are using Lucid, did you upgrade from karmic, or did you do a fresh install?

Does your laptop have a wireless switch or button?  after attempting to activate the wireless, type dmesg in a terminal and look at the last couple of messages...sometimes dmesg will give you a hint as to what is going on.

My neighbor's wireless stopped working recently...it turned out that the plastic switch face dislocated from the actual switch....It took us a while to figure that one out.

LMAO... I've been there.... Things like that always remind me to check the physical layer first... start at the bottom... good solid points.

---

### Post by robot_chicken_parm on 2010-05-08
first of all, thanks guys for replying so quicklyit is much appreciated. hopefully i wi figure this out.  i am usaing karmic and i did it as a fresh instal.  everything worked right "out of the box" so to say from the start.  this problem only occured a few mins ago.  tried the sys->admin->Hardware Drivers but to no avail.  funny but i have never found any thing in there it has always said "no proprietary dfrivers are in use..."  ok so my specs.

im using a dell latitude d520 and my internal wireless card is an  Intel PRO/Wireless 2200 802.11a/g WLAN.  its aways worked before.  i thing the ast thing i did before it stoppped working was a sudo apt installl for this program to try to undelete files..  ummm i typed dmesg in the terminal.  theres a lot of text there.  i could email it to myself and copy and paste it into here if u think i should.  i think im just going to do a new fresh install of karmic and start from scratch again.  this was my first time with linux and i think i know what i want to do again and what i dont want to do again with my comp this time.  the ony thing is i reay dont want to lose my files from the home folder like music and vids and pics and stuff.  is there a way i can keep that stuff while doing a fresh install?

---

### Post by robot_chicken_parm on 2010-05-08
also if i do a fresh installl which version should i do?  im reallly used to karmic but do u think its worth the jump to 10.04 yet?  also i just made an 8.04 iso disk because it says its a long term releaase which i thought mught be better.  any thoughts about that stuff? also thanks you guys are realy coo for helping a newb out like this.  can i add u guys to my ubuntuforums buddy list or whatever?

---

### Post by robot_chicken_parm on 2010-05-08
oh and byw if you dont mind could u tell me or link me to a page that tells me how to get an avitar on here?  thanks in advance

---

### Post by sadaruwan12 on 2010-05-08
> **robot_chicken_parm said:**
> oh and byw if you dont mind could u tell me or link me to a page that tells me how to get an avitar on here?  thanks in advance

[Fo your Avatar problem]("http://www.free-avatars.com/")

Regarding the Wi-Fi does your laptop have a function button or a switch where you've turn the Wi-Fi on. If there is one check that to so if it's on.

---

