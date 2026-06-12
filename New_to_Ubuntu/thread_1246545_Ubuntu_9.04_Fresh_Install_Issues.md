---
title: "Ubuntu 9.04 Fresh Install Issues"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by Spoken on 2009-08-21
Alright, i only have 2 problems left.  I just did a fresh install of 9.04, only with a couple tweaks left to do.

1)My screen resolution is currently 1440x900.  When i try to lower it to say...1360x768...it changes..but with black borders around the entire screen...instead of the desktop actually filling up my screen.  why???




EDIT! IVE FIXED THE DNS SETTINGS ISSUE...THANK GOD.
Automatic DHCP (Adresses Only) is the one you need to put your dns settings into....the reason i was having issues is because i picked the "manual" option to put the dns servers into.

Hope this helps anyone else with the similar problem.

SYSTEM SPECS:
Dual Core 2.2ghz processor
2 gb ram
intel media accelorator 2100x

---

### Post by Spoken on 2009-08-21
woot woot where is everyone :O

---

### Post by sandyd on 2009-08-21
i can only amswer #2, but
```

gksudo gedit /etc/dhcp3/dhclient.conf

```
will allow you to edit your network config.

---

### Post by Old Old Duffers on 2009-08-21
Same problem here....

---

### Post by kerry_s on 2009-08-21
> woot woot where is everyone :O 

we're still sleeping. :lolflag:

1. is "1360x768" the native resolution?

2. i go straight to the /etc/dhcp3/dhclient.conf

press-> alt+f2
type-> gksudo gedit /etc/dhcp3/dhclient.conf
or
use your right click script if you got one.

uncomment line 20 & change to your dns.
**prepend domain-name-servers 127.0.0.1;**
to
**prepend domain-name-servers #.#.#.#;**
use a "," to separate if you have more than 1
**prepend domain-name-servers 127.0.0.1,127.0.0.1,127.0.0.1;**

example of opendns:
**prepend domain-name-servers 208.67.222.222,208.67.220.220;**

---

### Post by Spoken on 2009-08-21
> **kerry_s said:**
> we're still sleeping. :lolflag:

1. is "1360x768" the native resolution?

2. i go straight to the /etc/dhcp3/dhclient.conf

press-> alt+f2
type-> gksudo gedit /etc/dhcp3/dhclient.conf
or
use your right click script if you got one.

uncomment line 20 & change to your dns.
**prepend domain-name-servers 127.0.0.1;**
to
**prepend domain-name-servers #.#.#.#;**
use a "," to separate if you have more than 1
**prepend domain-name-servers 127.0.0.1,127.0.0.1,127.0.0.1;**

example of opendns:
**prepend domain-name-servers 208.67.222.222,208.67.220.220;**

Im not sure what you mean by a "native" resolution.  However, my default resolution is 1400x900. and if i change it to ANY other res.  it gives me solid black borders. so... thats where im at on that.

As far as the DNS settings go.  i did as you suggested, but even with replacing that line with the other settings in "proper" order, it is still as slow as it was. :l

sigh.

---

### Post by kerry_s on 2009-08-21
> **Spoken said:**
> Im not sure what you mean by a "native" resolution.  However, my default resolution is 1400x900. and if i change it to ANY other res.  it gives me solid black borders. so... thats where im at on that.

As far as the DNS settings go.  i did as you suggested, but even with replacing that line with the other settings in "proper" order, it is still as slow as it was. :l

sigh.

then that means your vid is just not set up to stretch to fit, its best to run at the native resolution.

oops, i forgot a step. the network needs to be restarted.
in a terminal:
**sudo /etc/init.d/networking restart**
or 
just reboot

---

### Post by JoshStrobl on 2009-08-21
click mirror screen, pick the resolution.

---

### Post by Spoken on 2009-08-21
yea the resolution isnt that big of a deal. 

however, ive done everything you have said as far as changing the dns settings. which are changed, but the performance is still slow.

let me give you a better example so we can find a solution easier.

on 8.04, i had to change my dns settings "order" before internet use, every time i booted, otherwise it would be slow.  there were 3 different dns servers in the list that i rotated upon ever bootup. one ended in ".30", the 2nd one ended in ".2" and the 3rd one ended in ".29". now, i had to move the ".2" one to the top of the list in order for the internet to work properly.  how to i perform this same action on 9.04 instead.

---

### Post by Spoken on 2009-08-21
> **JoshStrobl said:**
> click mirror screen, pick the resolution.

ive tried ticking the mirror screen option. still giving me black borders when i change resolutions.

---

### Post by kerry_s on 2009-08-21
> EDIT! IVE FIXED THE DNS SETTINGS ISSUE...THANK GOD.

could you put what you did, just in case other people are looking.

---

### Post by Spoken on 2009-08-22
oh yes ofcourse

---

### Post by Buuntu on 2009-08-22
Are you sure the black borders aren't just the screen not fitting to your monitor?
You've probably tried this, but if you haven't try stretching the screen to fit your monitor.
You should probably stick with your native resolution though, images will be nicer and more clear.

---

### Post by Spoken on 2009-08-22
im on a laptop, not a desktop, i dont have the buttons on the screen to stretch it.

---

### Post by kerry_s on 2009-08-22
i suspect thats just another problem with the intel driver.
although mine works fine for lower resolutions, it stretches out, gets that zoomed look, i don't use them but they work. i just installed this evening to.

---

