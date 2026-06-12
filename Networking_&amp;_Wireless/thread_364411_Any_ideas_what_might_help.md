---
title: "Any ideas what might help ?"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by matoxxx on 2007-02-18
hi folks,
i ve tried it many times and in many ways, but it seems i will have no luck making my wireles working in kernel 2.6.17 and above. Id like to test edgy and feisty but my  wireless card isn t recognized by network manager, i ve tried ndiswrapper, no help at all.

```
lspci:
0000:02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
```
card i recognised by kernel 2.6.17 and 20 and it works flawless in 2.6.15 kernel,
is this old chipset not supported by new kernels ?

any ideas someone

---

### Post by chili555 on 2007-02-18
Perhaps this will help:
[http://www.ubuntuforums.org/showthread.php?t=288649](http://www.ubuntuforums.org/showthread.php?t=288649)

Good luck and post back if we can help.

---

### Post by ozPATT on 2007-03-01
Hi, 

I checked out the above link and did as suggested, but no joy here :(

```
lspci: 01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
```

I had wireless working like a dream before this update, using ndiswrapper. Currently I am forever pressing escape when it starts to load the previous kernel, which works fine - but is a pain... and I guess when a new kernel comes out, i will be stuck.. so any help would be greatl appreciated :D

Thanks

Patrick

---

### Post by chili555 on 2007-03-01
His question and my reply are related to Prism cards, which is not your case. I suggest you read this: [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174). I was especially interested in this part:

> The reason the card shows up but doesn't work is because ubuntu is only distributed with its driver (so it can recognize it) not with its firmware (so it can USE it) for legal reasons.

However you can take the firmware out of the windows drivers and put them into ubuntu and make the card work!


If you previously had the card working with firmware in the 2.6.17-10 kernel, the firmware needs to be placed in the appropriate place in the 2.6.17-11 file.

Good luck and post back if you get stuck.

---

### Post by stani on 2007-03-15
Help this bug out on Feisty, contribute by passing your details to launchpad:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)

> Can everyone affected please attach (do not paste into comment) the output of "lspci -vv" and "lspci -vvn", make sure to name the file something like lspci-vv-<yourname>.txt

There is not much time left, please participate!

Stani

---

