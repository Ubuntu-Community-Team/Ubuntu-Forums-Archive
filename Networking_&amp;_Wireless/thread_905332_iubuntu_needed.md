---
title: "iubuntu needed"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by Neil_The_Newbie on 2008-08-30
After another update i have now lost internet connection through wifi connection and through the cable connection. My system is dual boot and windows vista works just fine when connecting to the net. 

So - i'm left with 2 options.

1 - trawl round the forums and type in code i don't understand reboot my pc in ubuntu make aforementioned changes. find that that doesnt works, reboot computer in windows, go online, trawl the forums again - and repeat the process until (or if) i get it to work. sigh!

2 - back up my system, reinstall, set up my email router settings, fonts etc. sigh!

Its a timely process either way but i think i will go for option 2. 

So i have 2 questions. 

1 - Is there anyway i can disable updates so this doesnt happen again?
2 - Could anyone do an IUBUNTU? One that works reliably with the internet. :-)

"would you want to drive a sports car where the steering came off  every time it had a service?"

Rant over! :-)

---

### Post by coffeecat on 2008-08-30
> **Neil_The_Newbie said:**
> 1 - Is there anyway i can disable updates so this doesnt happen again?

You could open Synaptic and go to Settings > Repositories and click on the Updates tab. Now untick all the Ubuntu updates lines. I'm not sure I would want to do that though - at least I wouldn't want to disable the 'Important Security updates'.

As far as I remember, the most recent update was a new -19 kernel. A question therefore. Did your wireless and cable connections work out of the box when you first installed Ubuntu or did you have to install extra drivers? If the extra installation involved compiling them as kernel modules, then I'm afraid a kernel upgrade will break them. Usually, all that is required is to recompile them against the newer kernel and reinstall. What wireless hardware have you got? And what is involved with your cable connection? I have no experience of cable, but I thought you connected through your ethernet port and that shouldn't break with a kernel upgrade.

**Edit:** just a thought. While you are in Synaptic > ... Updates, check that you haven't got Proposed Updates enabled. If you have, uncheck it. Recent kernels from the proposed repository have broken some things.

---

### Post by scratman on 2008-08-30
You do not state that you have managed to get your internet connection working in Ubuntu again.  Is your nm-applet on your panel at the top of your screen?  It will either look like two black monitors, or a 4 bar chart.  If this is not there, go into termil and and type 
```

nm-applet

```
Now look again at your panel to see if it is there, it may be a swirling blue circle between two dots for a few moments.  If it connects automatically,ie, becomes the blue bar chart then left click it and ensure that it has connected to your network, and not somebody elses.  If not, Right click and enable Networking and Wireless Networking.  You may need to scan for available networks, and re-enter your password.

Any problems, please let me know.

---

### Post by Neil_The_Newbie on 2008-08-31
Thanks for your help.

the applet shows 4 bars when it does connect but - it seems to connect to the net about once every 20 times i boot up.

So it looks like I will have to do a full reinstall though. if this doesnt work this will be the last time i try ubuntu for at least another couple of releases. which is a shame. but it is kind of ironic that updates to make a computer more secure or run better actually do the opposite and stop things from working.

So if ubuntu fails i will probably try OpenSUSE. From an end users point of view i think more effort needs to be made to make it more stable rather than trying to add new features. I have read some harsh words on these forums for Ubuntu's lack of stability and problems with wifi. I'm getting to the point where I almost agree - and i'm not a windows fan either!

hmmm.... theres always apple mac.

---

