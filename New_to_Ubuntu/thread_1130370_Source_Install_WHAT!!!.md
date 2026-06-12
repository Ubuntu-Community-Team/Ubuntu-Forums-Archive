---
title: "Source Install? WHAT!!!"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-04-19
Hi, I have a problem. While iv'e been using ubuntu for about half a year, I dont know how to install this program from source. What it does is capture pictochat conversations and displays them. I would like to test this because it seems awsome, but its only been run in freebsd but all linux is the same right? So heres the softpedia page and the source download. Any comments would be appreciated!

[http://linux.softpedia.com/get/System/Networking/PictoSniff-3474.shtml](http://linux.softpedia.com/get/System/Networking/PictoSniff-3474.shtml)

---

### Post by Tibuda on 2009-04-19
What program? Can you post a link?

---

### Post by ibutho on 2009-04-19
FreeBSD is not a Linux based OS although software for Linux will generally work on FreeBSD and vice versa. What is the program you are trying to install?

---

### Post by taylor102387 on 2009-04-19
Sorry, Opera crashed, used firefox to put up the link and source.

---

### Post by Tibuda on 2009-04-19
Extract that file in an empty folder and open a terminal in that folder. Then run these commands:
```

# Install libpcap and gtk+ development headers
sudo apt-get install libpcap-dev libgtk2.0-dev

# Compile
make

# Install
sudo install pictosniff /usr/bin

```

Then type "pictosniff" to run it.

---

### Post by camper365 on 2009-04-19
Usually what you do is this:
Open the archive in GNOME (the graphics) and unzip it to your home directory.
After that, open a terminal.
do the following:
```
cd pictosniff-0.2
./configure

```Make sure that the output doesn't give you any errors.
I can tell you that resolving dependencies manually is a nightmare.
If it does tell you that you need to install a library, try:
```
sudo aptitude install libasdf-dev
```in addition to libasdf.
After that (with no errors)
```
make
```This could take a while depending on the complexity of the program.
```
sudo make install
```If all goes well, it should work.

---

### Post by taylor102387 on 2009-04-19
For some reason this is what I get when I run make:

```
taylor@taylor-laptop:~$ cd pictosniff-0.2
taylor@taylor-laptop:~/pictosniff-0.2$ make
gcc -Wall -g `pkg-config --cflags gtk+-2.0` -c pictosniff.c
pictosniff.c:35:26: error: net/if_media.h: No such file or directory
pictosniff.c:37:32: error: net80211/ieee80211.h: No such file or directory
pictosniff.c:38:38: error: net80211/ieee80211_ioctl.h: No such file or directory
pictosniff.c: In function ‘set80211’:
pictosniff.c:45: error: storage size of ‘ireq’ isn’t known
pictosniff.c:53: error: ‘SIOCS80211’ undeclared (first use in this function)
pictosniff.c:53: error: (Each undeclared identifier is reported only once
pictosniff.c:53: error: for each function it appears in.)
pictosniff.c:45: warning: unused variable ‘ireq’
pictosniff.c: In function ‘setmediaopt’:
pictosniff.c:75: error: storage size of ‘ifmr’ isn’t known
pictosniff.c:82: error: ‘SIOCGIFMEDIA’ undeclared (first use in this function)
pictosniff.c:104: error: ‘struct ifreq’ has no member named ‘ifr_media’
pictosniff.c:104: error: ‘IFM_OMASK’ undeclared (first use in this function)
pictosniff.c:105: error: ‘struct ifreq’ has no member named ‘ifr_media’
pictosniff.c:105: error: ‘struct ifreq’ has no member named ‘ifr_media’
pictosniff.c:105: error: ‘IFM_MMASK’ undeclared (first use in this function)
pictosniff.c:105: warning: implicit declaration of function ‘IFM_MAKEMODE’
pictosniff.c:107: error: ‘SIOCSIFMEDIA’ undeclared (first use in this function)
pictosniff.c:75: warning: unused variable ‘ifmr’
pictosniff.c: In function ‘getifflags’:
pictosniff.c:123: error: ‘struct ifreq’ has no member named ‘ifr_flagshigh’
pictosniff.c: In function ‘setifflags’:
pictosniff.c:134: error: ‘struct ifreq’ has no member named ‘ifr_flagshigh’
pictosniff.c: In function ‘add_message’:
pictosniff.c:244: warning: pointer targets in passing argument 1 of ‘gdk_pixbuf_new_from_data’ differ in signedness
pictosniff.c: In function ‘channel_change’:
pictosniff.c:278: error: ‘IEEE80211_IOC_CHANNEL’ undeclared (first use in this function)
pictosniff.c: In function ‘save_button_press’:
pictosniff.c:313: warning: implicit declaration of function ‘asprintf’
pictosniff.c: In function ‘main’:
pictosniff.c:361: error: ‘IFM_IEEE80211_MONITOR’ undeclared (first use in this function)
pictosniff.c:361: error: ‘IFM_AUTO’ undeclared (first use in this function)
pictosniff.c:365: error: ‘IEEE80211_IOC_CHANNEL’ undeclared (first use in this function)
pictosniff.c:373: error: ‘IFF_PPROMISC’ undeclared (first use in this function)
make: *** [pictosniff.o] Error 1
taylor@taylor-laptop:~/pictosniff-0.2$ 

```

---

### Post by taylor102387 on 2009-04-19
Hello?

---

### Post by taylor102387 on 2009-04-19
When I run make on this source :

[http://linux.softpedia.com/get/Syste...iff-3474.shtml](http://linux.softpedia.com/get/Syste...iff-3474.shtml)

I get :

[CODE]taylor@taylor-laptop:~/pictosniff-0.2$ make
gcc -Wall -g `pkg-config --cflags gtk+-2.0` -c pictosniff.c
pictosniff.c:35:26: error: net/if_media.h: No such file or directory
pictosniff.c:37:32: error: net80211/ieee80211.h: No such file or directory
pictosniff.c:38:38: error: net80211/ieee80211_ioctl.h: No such file or directory
pictosniff.c: In function ‘set80211’:
pictosniff.c:45: error: storage size of ‘ireq’ isn’t known
pictosniff.c:53: error: ‘SIOCS80211’ undeclared (first use in this function)
pictosniff.c:53: error: (Each undeclared identifier is reported only once
pictosniff.c:53: error: for each function it appears in.)
pictosniff.c:45: warning: unused variable ‘ireq’
pictosniff.c: In function ‘setmediaopt’:
pictosniff.c:75: error: storage size of ‘ifmr’ isn’t known
pictosniff.c:82: error: ‘SIOCGIFMEDIA’ undeclared (first use in this function)
pictosniff.c:104: error: ‘struct ifreq’ has no member named ‘ifr_media’
pictosniff.c:104: error: ‘IFM_OMASK’ undeclared (first use in this function)
pictosniff.c:105: error: ‘struct ifreq’ has no member named ‘ifr_media’
pictosniff.c:105: error: ‘struct ifreq’ has no member named ‘ifr_media’
pictosniff.c:105: error: ‘IFM_MMASK’ undeclared (first use in this function)
pictosniff.c:105: warning: implicit declaration of function ‘IFM_MAKEMODE’
pictosniff.c:107: error: ‘SIOCSIFMEDIA’ undeclared (first use in this function)
pictosniff.c:75: warning: unused variable ‘ifmr’
pictosniff.c: In function ‘getifflags’:
pictosniff.c:123: error: ‘struct ifreq’ has no member named ‘ifr_flagshigh’
pictosniff.c: In function ‘setifflags’:
pictosniff.c:134: error: ‘struct ifreq’ has no member named ‘ifr_flagshigh’
pictosniff.c: In function ‘add_message’:
pictosniff.c:244: warning: pointer targets in passing argument 1 of ‘gdk_pixbuf_new_from_data’ differ in signedness
pictosniff.c: In function ‘channel_change’:
pictosniff.c:278: error: ‘IEEE80211_IOC_CHANNEL’ undeclared (first use in this function)
pictosniff.c: In function ‘save_button_press’:
pictosniff.c:313: warning: implicit declaration of function ‘asprintf’
pictosniff.c: In function ‘main’:
pictosniff.c:361: error: ‘IFM_IEEE80211_MONITOR’ undeclared (first use in this function)
pictosniff.c:361: error: ‘IFM_AUTO’ undeclared (first use in this function)
pictosniff.c:365: error: ‘IEEE80211_IOC_CHANNEL’ undeclared (first use in this function)
pictosniff.c:373: error: ‘IFF_PPROMISC’ undeclared (first use in this function)
make: *** [pictosniff.o] Error 1
[CODE]

Any ideas?

Original: 

http://ubuntuforums.org/showthread.php?p=7102838#post7102838

---

### Post by Tibuda on 2009-04-19
I get the same error as you. I think it needs another dependency, but I have no clue. The relevant error is the first one:
```
pictosniff.c:35:26: error: net/if_media.h: No such file or directory
```

Try asking PictoSniff developers. Do you know if they have an official website?

---

### Post by taylor102387 on 2009-04-19
Yes, but it is a long outsourced project... and the websites down. :(

---

### Post by inxygnuu on 2009-04-19
it sounds like you might be missing part of the code, but I am a newbie when it comes to this.

---

### Post by Gen2ly on 2009-04-19
Actually I'd guess this is more likely a dependency.  Use google cache on the website:

cache:linux.org

And try to find the dependencies.  Also developers a lot of list dependencies, instructions in a README or INSTALL file.

---

### Post by Tibuda on 2009-04-20
> **Dirk.R.Gently said:**
> Actually I'd guess this is more likely a dependency.  Use google cache on the website:

cache:linux.org

And try to find the dependencies.  Also developers a lot of list dependencies, instructions in a README or INSTALL file.

There's no README or INSTALL in the archive. Softpedia says it needs libpcap and GTK2, so I suggested him to install libpcap-dev and libgtk2.0-dev, but it still misses some headers.

---

### Post by gali98 on 2009-04-20
There is probably no way you could get this to work, even if you could get it to compile. It is based a a specific driver, and probably will not work with a linux kernel.
Kory

---

