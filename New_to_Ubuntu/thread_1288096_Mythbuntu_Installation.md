---
title: "Mythbuntu Installation"
date: 2009-10-10
forum: New to Ubuntu
---

### Post by Amockineuropa on 2009-10-10
So I just downloaded Mythbuntu and it sits on my desktop bUT I am not sure HOW to install the program. I have 2 files: mythbuntu-9.04-desktop-amd64.iso and the other with same title "mythbuntu-9.04-desktop-amd64.iso". I opened the file in see listed 8 folders one labeled install. Do I just click this like a .exe file in Windows to install the entire program or how does this work?

---

### Post by 2ndgenesis on 2009-10-11
You should only need one of the .iso files and what u need to do is burn that iso file onto a cd or dvd which u can  then put in your cd drive and  an installation menu should come up.
atleast thats how mine worked using linux mint which is based off ubuntu.

if u dont know how to burn an .iso file to cd u just need to use a program like powerISO
drag the file from your desktop into the program and hit burn =P

For more information check out this link to ubuntu's burning ISO How To
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

hope that helps you out  ):P

---

### Post by laceration on 2009-10-12
> hope that helps you out 
Um, I don't think you helped out our OP, he is probably pretty confused. 

mythbuntu-9.04-desktop-amd64.iso is not the MythTV program!  It is a whole Ubuntu operating system wrapped around MythTV.  Since it is obvious you have Ubuntu already installed you can install MythTV from Add/Remove or Synaptic.
Installing MythTV is already difficult enough, reinstalling your operating system on top of that is way more grief than you need.

---

### Post by laceration on 2009-10-12
2ndgenesis,

Sorry if I was harsh, especially since I notice this was your first post on Ubuntuforums.  It was actually a very well written post and you could be helpful to people. I think in your enthusiasm to explain what what you know, you just missed that the original poster mistook the mythbuntu OS for the program.  I hope not to discourage you in any way.

---

### Post by OffAxis on 2009-10-12
This was hinted at, but never outright said, so I'll say it:
mythbuntu is the generic name for two different things; 
1. a complete ubuntu based operating system which has mythtv pre-installed and a number of wizards to help you configure it;
2. the ***desktop ***for this operating system (based on xfce4)

As a linux desktop (like gnome or kde) the mythbuntu desktop can be installed on the ubuntu system you already have easily enough from the repositories by running this at the command line (and, as mentioned, you can also use synaptic to install it).
```
sudo apt-get install mythbuntu-desktop
```

if you'd like to try out mythbuntu before making any changes to your current system, then it's easiest to burn that iso to disc, and boot from the resultant liveCD.

---

