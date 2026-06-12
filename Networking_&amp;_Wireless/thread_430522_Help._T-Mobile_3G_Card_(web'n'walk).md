---
title: "Help. T-Mobile 3G Card (web'n'walk)"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by cpdave on 2007-05-02
Hi - I've not installed ubuntu yet (just downloading the image). Before I do the install, can someone tell me whether my T-Mobile 3G card (web'n'walk) will work on my Dell D600 laptop. And if so, how do I go about configuring it?

TIA,

CPDave

---

### Post by dmizer on 2007-05-02
if this:[http://www.huawei.com/mobileweb/en/products/view.do?id=282](http://www.huawei.com/mobileweb/en/products/view.do?id=282) is the 3g device you're talking about

 without doing an in depth search ... i'd say no for the following reasons:

1) it's usb.
2) it's very new tech so linux drivers haven't been created for it yet.
3) it's still buggy even in windows.
4) it requires usb 2.0 (could cause conflicts in linux)
5) requires xp service pack 2 when running in windows.
6) difficult/impossible to get working in vista.

the above combined issues indicate that this device is largely software driven, and as such will likely be a huge pain/impossible in linux.

that said, you can always burn a live cd, and give it a shot before you take the leap with a full install.

---

### Post by cpdave on 2007-05-02
Hi, I installed ubuntu regardless (I'll use the card on my work laptop).

Its a PCMCIA card:

[http://www.trustedreviews.com/mobile-devices/review/2006/06/30/T-Mobile-Web-n-Walk-Card/p1]("http://www.trustedreviews.com/mobile-devices/review/2006/06/30/T-Mobile-Web-n-Walk-Card/p1")

Thanks anyway, CPDave.

---

### Post by cullwock on 2007-05-19
it does work, and it's actually not all that difficult to get it working...

Follow the instructions here: [http://mybroadband.co.za/vb/printthread.php?t=21726](http://mybroadband.co.za/vb/printthread.php?t=21726) The forum is active and Tazz_Tux is really helpful!

The card that I had (using T-Mobile Web'n'Walk) was a Option HSDPA Card. The Option HSDPA Driver (nozomi.tgz) was already installed with my Feisty (I think), so I didn't have to worry about that.

---

### Post by synapse321 on 2007-05-26
The drivers don't come pre-installed in feisty and it is not that straight forward for a beginner. I keep getting this error when compiling

make -C /lib/modules/2.6.15-28-686/build SUBDIRS=/home/synapse/nozomi modules
make: *** /lib/modules/2.6.15-28-686/build: No such file or directory. Stop.
make: *** [default] Error 2

Any ideas?:(

---

### Post by dmizer on 2007-05-27
to make something from source you need the source tools:
```
sudo aptitude install build-essential
```

---

### Post by synapse321 on 2007-05-27
Hi

I am now able to compile the drivers ok after downloading the kernel source headers via packet manager but don't know for sure what to do after that. I have followed the link you gave to the best of my ability but the card is still only showing one flashing blue light, the green light is out ( i know the card is functional)

---

