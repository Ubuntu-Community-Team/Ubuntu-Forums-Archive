---
title: "Need help with a broadcom 4318"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by Rette on 2006-08-26
Yes, I'm yet another poor fool using a broadcom 4318 wireless card. I went through the whole ndiswrapper thing, blacklisted bcm43xx, yada-yada-yada. Naturally, I still can't connect to the internet.

I have, however, noticed something funky;

```
~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present
```

Notice the lack of "hardware present". I'm guessing I must have either a) skipped a step somewhere or b) done something really stupid.

I've tried going through the ndiswrapper steps again, and I've had no luck.

Could any of you wonderful, intelligent people help a poor newbie out?

---

### Post by Maylar on 2006-08-26
There is two different drivers. bcmwl5 and bcmwl5**a**

I had to use the later to get mine to work

```
~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5a         driver present, hardware present

```
Are you using 64 or 32bit? If it is 32, I can compress the folder (they are Acer drivers) and put them up for download

---

### Post by Rette on 2006-08-26
I'm using 64 bit. Thanks for the response though, I'll see if it works...

---

### Post by Maylar on 2006-08-26
I have compressed the whole folder from Acer (from my windows partition). These are 32 bit drivers. download [here]("http://www.maylar.net/ndiswrapper/802bg.tar.gz")

As for the 64bit drivers. They can be downloaded from Acer [here]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip")

---

### Post by Rette on 2006-08-26
alright, I think we're getting closer. I'm now getting both drivers and hardware detected. 

I'm now having problems with the old "eth1" issue. If I add "blacklist bcm43xx" to my blacklist, iwconfig doesn't show any wireless connections. If I take it off, it shows my card under eth1.

Any ideas?

---

### Post by Melcar on 2006-08-26
Just use bcm43xx-fwcutter.  It worked for me.  I tried ndiswrapper with little success myself.

---

### Post by Maylar on 2006-08-26
blacklist it and if it does not show, try

```
sudo modprobe ndiswrapper
```

I also recommend [this]("http://ubuntuforums.org/showpost.php?p=1189681&postcount=105") post

---

### Post by jd123 on 2008-02-21
Hi ALL,

[SIZE="4"]
There is two different drivers. bcmwl5 and bcmwl5a[/SIZE]

Im a Newbie, I have a dell inspiron 1300 laptop.with the wlan 1370 pci card. chipset broadcom 4318.

The driver files are importaant, i was having no luck also.

I then got bcmwl5a.ini from the hp website and installed this with the windows wireless drivers GUI menu. You will find this hp driver easy enough.

I had to change the .ini to bcmwl5a.inf to get it to work and suddenly I was on the pigs back and my driver worked. I now HAVE WIFI and am using ubuntu firefox to type this.

So use Ndiswrapper and use this guide.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

get your GUI running, ADD driver above and make sure to use the A version.

You will soon get there so keep at it.

Best of luck to All.

---

### Post by jd123 on 2008-02-21
Oh Yes by the way i am Using Gutsy 7.10 version of linux.

---

