---
title: "Techkey 1200Mbps Dual Band USB Adapter intermitantly runs slow - Ubuntu 18.04.2"
date: 2019-02-15
forum: Networking &amp; Wireless
---

### Post by Natetronn on 2019-02-15
Hi,

My WIFI is running very slow on my Ubuntu 18.04.2 machine. Sometimes it speeds up but, for the most part, it's slow. As if I'm running a dial-up modem. This in both 2.4GHz and 5GHz.

[http://paste.ubuntu.com/p/fHfcw3v9ct/](http://paste.ubuntu.com/p/fHfcw3v9ct/)

This is the driver and its install procedure I used: [https://askubuntu.com/a/1049772/403296](https://askubuntu.com/a/1049772/403296)

Note: I'm not 100% sure that's the proper driver but, it did bring it to life.

Running this [Techkey USB WIFI adapter.]("https://www.amazon.com/gp/product/B07D9BBFV6/ref=oh_aui_search_asin_title?ie=UTF8&psc=1")

With this [ASUS 1750 router]("https://www.amazon.com/gp/product/B00R2AZLD2/ref=oh_aui_search_asin_title?ie=UTF8&psc=1").

Appreciate any help, thanks!

---

### Post by praseodym on 2019-02-15
Uninstall that driver

```
sudo dkms remove 8822bu/1.1 --all
```

and install this one

[https://ubuntuforums.org/showthread.php?t=2394372&p=13776566#post13776566](https://ubuntuforums.org/showthread.php?t=2394372&p=13776566#post13776566)

---

### Post by Natetronn on 2019-02-15
Thanks for the reply, [[COLOR=#000000]praseodym[/COLOR]]("https://ubuntuforums.org/member.php?u=1411497")!

I did as you suggested and it seemed to go off without out a hitch (I've heard of that Chili guy before.)

I'll need more time to verify if the issues has been addressed. In the mean time, here is my latest wireless-info paste:
[http://paste.ubuntu.com/p/NCZWNqmZcQ/](http://paste.ubuntu.com/p/NCZWNqmZcQ/)

Line 143 appears to include the new driver. Is that correct?

---

### Post by Natetronn on 2019-02-15
Looks like I may have spoke too soon. 

I turned off the WIFI in the settings and now it won't connect. I tried forgetting both frequencies and logging back into them but, keeps failing to connect.

---

### Post by praseodym on 2019-02-15
Try

```
sudo modprobe 88x2bu
```

again. SecureBoot is turned off?

---

### Post by Natetronn on 2019-02-15
I ran that but, nothing. 

All the Windows 8/8.1/10 Configuration were disabled. 

Here is that section of my mobo:  [http://www.manualsdir.com/manuals/467019/msi-z97s-sli-krait-edition-manual.html?page=70](http://www.manualsdir.com/manuals/467019/msi-z97s-sli-krait-edition-manual.html?page=70)  

Aaaand, looks like it started working after checking the bios and the restart, which I knew better to do and should have tired before posting, sorry. 

I'll update again should things change or not maintain stable speeds. 

Thanks again!

---

### Post by Natetronn on 2019-02-21
**Update**: It's working again. Removed the driver one more time, reinstalled it again and restarted and it seems to be working. Odd that it started spazzing out.

Not sure what changed but, this isn't working any longer. 

I tried removing it and installing the driver again and it's still not working properly. I can't get it to connect. When I start the pc it does happen to appear to be connected to 5ghz but, doesn't work. If I try to change to 2.4ghz it is unable to connect.

Any ideas by chance?

ETA
Not sure it's relevant or not:
```
dkms status
nvidia, 415.27, 4.18.0-15-generic, x86_64: installed
rtl88x2bu, 5.2.4.4, 4.18.0-15-generic, x86_64: installed (WARNING! Diff between built and installed module!)
```

---

