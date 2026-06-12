---
title: "Yoga 13 Ubuntu13.1 Wifi problems"
date: 2013-10-23
forum: Networking &amp; Wireless
---

### Post by julianhatdieschnauzevoll on 2013-10-23
Hi,

I just installed Kubuntu 13.10 on my Lenovo Yoga 13. I knew that there will be problems setting it up proper on it. I found this guide to install my wireless chip ([http://askubuntu.com/questions/318608/lenovo-yoga-13-realtek-wireless-driver](http://askubuntu.com/questions/318608/lenovo-yoga-13-realtek-wireless-driver)). 

So i downloaded the driver, extracted it and tried to install it.After "make" im getting a huge list of errors and stuff, such as:

/urs/src/linux-headers-3.11.0-12-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/urs/src/linux-headers-3.11.0-12-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: gcc: command not found

I have tried to install many different packages such as the build essential package and gcc. The only one working were the linux headers (linux-headers-3.11.0-12-generic)

Im sorry, that this is not really precise, but im certainly absolutely unexperienced concerning unix systems.

---

### Post by wildmanne39 on 2013-10-23
*Thread moved to **Networking & Wireless**.*

---

### Post by ktkohl96 on 2013-10-23
same problem here after just upgrading to ubuntu 13.10.

UPDATE:  Nevermind.  I had an different driver version that I was using on 13.04.  With the one on the linked page, I have no problems with installation now.

---

### Post by varunendra on 2013-10-25
> **julianhatdieschnauzevoll said:**
> **[COLOR="#FF0000"]make[/COLOR]**[1]: gcc: [COLOR="#FF0000"]command not found[/COLOR]

It's gcc's way of saying - "I couldn't find 'make', means you don't have build-essential installed !". As its name suggests, it is "essential" to "build" modules. Try this -
```
apt-get install --print-uris build-essential
```
It will 'pretend' to install, but will actually print the URIs of the required package plus its dependencies at the bottom. Copy these URIs and use them to download the packages on a different computer with Internet connection. Then copy the downloaded ".deb" packages into a fresh, empty folder on your desktop (let's name it "julian"). Now install them with -
```
sudo dpkg -i Desktop/julian/*
```

Then retry the driver.

That being explained, be aware that even same models of laptops may have different wireless cards. So have you made sure the driver you are trying is indeed correct for the card? If not sure, post back the output of -
```
lspci -nnk | grep -iA2 net
```

---

