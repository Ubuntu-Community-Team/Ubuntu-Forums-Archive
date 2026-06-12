---
title: "problem building rtmpdump 2.4"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by dddw on 2011-08-02
I´ve been trying to build rtmpdump 2.4 (so I can watch colbert nation on XBMC) but I just can´t seem to do it right.
Can anyone tell me step by step how to do this?

---

### Post by Redblade20XX on 2011-08-02
You git cloned the repository and in the directory of the git there should be a readme. Did you read the README?

---

### Post by ron999 on 2011-08-02
> **dddw said:**
> 
Can anyone tell me step by step how to do this?

Hi
This is the method I used with Lucid Lynx:-

Install dependencies:-
```
sudo apt-get install build-essential git-core checkinstall libssl-dev
```

Then used this ***single*** command:-

```
cd ~/ && \
git clone git://git.ffmpeg.org/rtmpdump && \
cd rtmpdump && \
version="$(git log -1 --abbrev-commit | grep commit | cut -d' ' -f2)" && \
make VERSION="v2.4\ $version~git" && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname rtmpdump \
--pkgversion "2.4-$version~git" --backup=no --default && sudo ldconfig
```

Result:-** rtmpdump_2.4-f1abda0~git-1_i386.deb**

---

### Post by shantiq on 2011-08-29
and thank you Ron

---

### Post by Cas07 on 2011-09-09
Thanks Ron :)

---

### Post by heyup on 2011-10-15
> **ron999 said:**
> Hi
This is the method I used with Lucid Lynx:-

Install dependencies:-
```
sudo apt-get install build-essential git-core checkinstall libssl-dev
```

Then used this ***single*** command:-

```
cd ~/ && \
git clone git://git.ffmpeg.org/rtmpdump && \
cd rtmpdump && \
version="$(git log -1 --abbrev-commit | grep commit | cut -d' ' -f2)" && \
make VERSION="v2.4\ $version~git" && \
sudo checkinstall --pakdir "$HOME/Desktop" --pkgname rtmpdump \
--pkgversion "2.4-$version~git" --backup=no --default && sudo ldconfig
```

Result:-** rtmpdump_2.4-f1abda0~git-1_i386.deb**

This installs rtmpdump 2.4 but it doesn't show up in Synaptic. 

When I tried to remove it with:

```
sudo dpkg - r packagename
```

dpkg complains that rtmpdump isn't installed, when it is.

How do I get Synaptic to show rtmpdump and to remove with dpkg?

---

### Post by Cas07 on 2011-10-15
> **heyup said:**
> 
dpkg complains that rtmpdump isn't installed, when it is.

How do I get Synaptic to show rtmpdump and to remove with dpkg?

What does this command show: 
```
dpkg -l | grep rtmpdump
```

Also what version is displayed when you run rtmpdump.

---

### Post by heyup on 2011-10-16
> **Cas07 said:**
> What does this command show: 
```
dpkg -l | grep rtmpdump
```

Also what version is displayed when you run rtmpdump.

> ii  rtmpdump                             2.4-60218d0~git-1                               Package created with checkinstall 1.6.1


and

> RTMPDump v2.4 60218d0~git

Apologies, I was wrong. I can remove rtmpdump with:

```
sudo dpkd -r rtmpdump
```

I tried to remove rtmpdump using packagename rtmpdump_2.4-60218d0~git-1

dkpg then complains that rtmpdump isn't installed.

But rtmpdump still doesn't show up in Synaptic.

---

### Post by heyup on 2011-10-16
> **heyup said:**
> 

But rtmpdump still doesn't show up in Synaptic.

Weird. I've now found rtmpdump in Synaptic.

Problem solved.

---

### Post by doogie04 on 2012-02-03
Sorry if this a bit off topic, but I stumbled across this post trying to get Amazon and Hulu streaming working with BlueCop's plug in on Ubuntu 11.10.  

The above commands upgraded my rtmpdump to 2.4 but 'handshake 9' problem persisted.  

It seems that the handshake 9 requires rtmpdump 2.4 and also librtmp0 to be upgraded 2.4.  RTMPDump does not have a dependency listed for librtmp0 2.4.   Running :

    ```
sudo apt-get install librtmp0
```

upgraded my librtmp0 and got amazon & hulu streaming working.  Just though I would share.

---

### Post by lytithwyn on 2012-02-04
Just a note, for this to work for me on Oneiric I had to
```
export LD_LIBRARY_PATH=/usr/local/lib:/usr/lib
```

If you find you need this, you might want to add it to your .bashrc so you don't have to worry about entering it again.

---

### Post by richgreene on 2012-03-31
[SIZE=2]After building the 2.4 version of rtmpdump, I found that I had to copy the excutable (and the librtmp.so.1) to system directories just to make sure XBMC picked them up, and then it worked great:
[/SIZE][INDENT][FONT=Fixedsys][SIZE=2]cd rtmpdump[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Fixedsys][SIZE=2]sudo make install[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Fixedsys][SIZE=2]sudo cp /usr/local/bin/rtmpdump /usr/bin/rtmpdump[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Fixedsys][SIZE=2]sudo cp /usr/local/lib/librtmp.* /usr/lib[/SIZE][/FONT][SIZE=2]
[/SIZE][FONT=Fixedsys][SIZE=2]sudo cp /usr/local/lib/librtmp.* /usr/lib/x86_64-linux-gnu[/SIZE][/FONT][SIZE=2]
[/SIZE][/INDENT]

---

### Post by ron999 on 2012-05-19
> **lytithwyn said:**
> Just a note, for this to work for me on Oneiric I had to
```
export LD_LIBRARY_PATH=/usr/local/lib:/usr/lib
```

If you find you need this, you might want to add it to your .bashrc so you don't have to worry about entering it again.

Hi
I've just compiled RTMPDump from git with a fresh install of Ubuntu 12.04 and RTMPDump didn't work!

This solved it...
add extra line
```
export LD_LIBRARY_PATH=/usr/local/lib:/usr/lib
```
to file /home/user/.bashrc and save.

Thanks lytithwyn.
:p

---

