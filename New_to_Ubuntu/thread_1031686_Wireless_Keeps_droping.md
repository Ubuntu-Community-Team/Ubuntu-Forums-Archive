---
title: "Wireless Keeps droping"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by cerealtx on 2009-01-05
im here at the library and it constantly drops like every 4-5 min very anoying any idea why? is it a driver problem?

---

### Post by donkyhotay on 2009-01-05
Possibly, but it's more likely something else. My guess would be the various radio waves cancelling each other out from all the other laptops around you. Do you only have this problem while connecting to the library system or does it happen with any wireless network?

---

### Post by cerealtx on 2009-01-05
just here is the only time ive noticed it

---

### Post by porchrat on 2009-01-05
perhaps it is just a weak signal.  The range of wireless is not exactly massive.

---

### Post by 2hot6ft2 on 2009-01-05
Mine will drop signal from time to time if I boot using kernel 2.6.27-9 but will stay connected if I boot using kernel 2.6.27-7. Go figure.

---

### Post by cerealtx on 2009-01-05
its not the wireless signal, i have done ISP techsupport for 2 years i would have figured it out if it was that, + i have a friend next to me on windows with no problems

---

### Post by 2hot6ft2 on 2009-01-05
If your choices are kernels lower you can update them using this in a terminal.
Applications>Accessories>Terminal
```
sudo apt-get install linux-backports-modules-intrepid-generic
```
Assuming you're using Intrepid 8.10

---

### Post by donkyhotay on 2009-01-05
Not a weak signal, just signal wave interference. Radio waves can cancel each other out, think of two pebbles dropped in a pont intersecting and cancelling each other. Take a look at a ham radio book or you might want to take a look at this:
[http://encarta.msn.com/encyclopedia_761565332/Interference_(wave_motion).html](http://encarta.msn.com/encyclopedia_761565332/Interference_(wave_motion).html)

---

### Post by cerealtx on 2009-01-05
nvm

---

### Post by 2hot6ft2 on 2009-01-05
> **cerealtx said:**
> nvm
Not in my English dictionary. I'll move on to someone that can make sense. Good luck.

---

### Post by donkyhotay on 2009-01-05
> **cerealtx said:**
> good in theory but not likely with wireless signals, radio waves are everywhere, wireless waves are send from the computer to the router, not broadcast everywhere

Umm... no, Unless you are using line of sight (which wifi isn't designed for) the radio wave is broadcast. Your computer just ignores all the signals it picks up meant for other computers but it does recognize them (thats why encryption is so important with wifi). The problem with radio wave interference is a physical limitation of radio waves. If you get too many of them, especially in a closed in area where they can bounce off the walls, then they will start interfering and canceling each other. The signal strength is strong but both the AP and your computer loses packets because this. Although there is some leeway and error correction, depending on the system if you lose enough packets you may be dropped from the system. This is most likely whats going on because you are:
1: in an enclosed space
2: in a public are which likely to have many radio waves on the same frequency all around you
3: not having this problem on other wireless networks
You might try moving around a little bit and see if another location helps at all but I don't think there is much you can do unless the number of users in your area drops.

---

### Post by cerealtx on 2009-01-05
good in theory but not likely with wireless signals, radio waves are everywhere, wireless waves are send from the computer to the router, not broadcast everywhere

---

### Post by donkyhotay on 2009-01-05
You also might want to take a look at this
[http://en.wikipedia.org/wiki/Interference#Constructive_and_destructive_interference](http://en.wikipedia.org/wiki/Interference#Constructive_and_destructive_interference)

---

