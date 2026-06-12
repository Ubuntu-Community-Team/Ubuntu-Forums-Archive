---
title: "acer wifi"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by kyanther22 on 2007-08-06
hi, can anyone help me please, i have an acer 3003lmi with wifi, but it seams to have hidden itself!!! although this is the first time i have tried to use it i do remember it telling me that there were people around when i first had the laptop. i havent seen these pop ups for some time now. i have enabled it with the button at the frount of the computor and it is switched on in the manager. but there is no wireless question in the new connection window and i have gone through the wireless wiz but nothing happened!! when i went back to the wiz it asked me if i wanted to add to the network that i had tried to set up so it did do something,

any help will be greatly recieved

ky

---

### Post by moore.bryan on 2007-08-06
*do you use network-manager or wicd?*

---

### Post by kyanther22 on 2007-08-10
Ive not got a clue, how would i tell

---

### Post by moore.bryan on 2007-08-10
[I]okay, let's go simpler than that...
if you're running gnome, you probably have network-manager, if you are running kde, knetwork.
i'd suggest going with [wicd]("http://wicd.sourceforge.net/")... read-up on the website and follow the directions and it should be no problem.  if you run into anything, just post and we can work it out.
[/I]

---

### Post by noob12 on 2007-08-10
Before running off and installing, I'd grab some diagnostics first.  Is the device even showing up?  Try these and tell us what happens.
```

lspci -nn

sudo lshw -C network

ifconfig -a

iwconfig

iwlist scan

```

---

