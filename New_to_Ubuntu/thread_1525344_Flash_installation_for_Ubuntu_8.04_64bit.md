---
title: "Flash installation for Ubuntu 8.04 64bit"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by aas452 on 2010-07-06
I looked at few online step through installations but it still not to work has anyone been successful in installing flash in Firefox for Ubuntu 8.04 64bit. Tried Flash-Aid as well, but no luck.\

Any Suggestions???

---

### Post by jtarin on 2010-07-06
> **aas452 said:**
> I looked at few online step through installations but it still not to work has anyone been successful in installing flash in Firefox for Ubuntu 8.04 64bit. Tried Flash-Aid as well, but no luck.\

Any Suggestions???Use synaptic and download the "Adobe Flash Player plugin installer".

---

### Post by aas452 on 2010-07-06
yea that downloads Flash 9, most websites are now upgrading to 10

---

### Post by philinux on 2010-07-06
```
sudo updatedb

then

locate libflashplayer.so
```

---

### Post by jtarin on 2010-07-06
> **aas452 said:**
> yea that downloads Flash 9, most websites are now upgrading to 10
You didn't mention version specific.Just download and manually install then if you want the latest version and the Linux installer doesn't work for you..

---

### Post by aas452 on 2010-07-06
/root/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

here is what the terminal spits...

---

### Post by aas452 on 2010-07-06
> **jtarin said:**
> You didn't mention version specific.Just download and manually install then if you want the latest version and the Linux installer doesn't work for you..

10 doesnt support 64bit and the libs for the hack are all jacked

---

### Post by jtarin on 2010-07-06
You didn't list specific hacks you tried so here's one that looks more than promising in several ways.Follow it to the letter for expected results and debugging purposes.
[[COLOR="Blue"]Additionally[/COLOR]]("http://labs.adobe.com/downloads/flashplayer10_64bit.html")

---

### Post by stmiller on 2010-07-07
All you need to do is this on any version of Ubuntu, 32bit or 64bit:

```

sudo apt-get install flashplugin-nonfree

```


Alternatively, just run this one command which will install all codecs and goodies that you need in one go:

```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by jtarin on 2010-07-07
> All you need to do is this on any version of Ubuntu, 32bit or 64bit:

Code:

```
sudo apt-get install flashplugin-nonfree
```


Alternatively, just run this one command which will install all codecs and goodies that you need in one go:

Code:

```
sudo apt-get install ubuntu-restricted-extras
```
Yes but I beleive that is not what he wants.....correct me if I'm wrong but I was under the assumption he wanted ver-10 and according to my link its not ready yet for Linux.

---

### Post by lovinglinux on 2010-07-07
Try the deb file from Adobe download page.

---

### Post by RiceMonster on 2010-07-07
> **jtarin said:**
> Yes but I beleive that is not what he wants.....correct me if I'm wrong but I was under the assumption he wanted ver-10 and according to my link its not ready yet for Linux.

No, version 10.1 is available on Linux.

---

### Post by jtarin on 2010-07-07
> **RiceMonster said:**
> No, version 10.1 is available on Linux.
Thanks for the announcement but Adobe does well enough on their own.The topic is about 64-bit which is not available as of yet in 10 much less 10.1.

> Flash Player 10 for 64-bit Linux

We have temporarily closed the Labs program of Flash Player 10 for 64-bit Linux, as we are making significant architectural changes to the 64-bit Linux Flash Player and additional security enhancements. We are fully committed to bringing native 64-bit Flash Player for the desktop by providing native support for Windows, Macintosh, and Linux 64-bit platforms in an upcoming [COLOR="Red"]major release[/COLOR] of Flash Player. We intend to provide more regular update information on our progress as we continue our work on 64-bit versions of Flash Player. Thank you for your continued help and support. Stay tuned to the Flash Player discussion forum for further announcements.

---

### Post by lovinglinux on 2010-07-07
> **jtarin said:**
> Thanks for the announcement but Adobe does well enough on their own.The topic is about 64-bit which is not available as of yet in 10 much less 10.1.

Install the 32bit version from the repositories, then download the 32bit tar.gz file from Adobe, extract it and move the libflashplayer.so to /usr/lib/flashplugin-installer

---

### Post by jtarin on 2010-07-08
Evidently I must be missing something....this is the first time I have been aware that a 32-bit will run on a 64-bit.....is there any special configuration to make this happen?

---

### Post by lovinglinux on 2010-07-08
> **jtarin said:**
> Evidently I must be missing something....this is the first time I have been aware that a 32-bit will run on a 64-bit.....is there any special configuration to make this happen?

You need to install from the repositories, so the dependencies are taken care of. It needs nspluginwrapper, that will handle the 32bit so on a 64bit machine.

So if you overwrite the /usr/lib/flashplugin-installer/libflashplayer.so with the version from Adobe, it might work.

---

