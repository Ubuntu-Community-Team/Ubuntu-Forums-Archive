---
title: "Decreasing File Transfer Speeds over WLAN"
date: 2014-11-27
forum: Networking &amp; Wireless
---

### Post by jdhamric on 2014-11-27
I recently started having a file transfer problem on Ubuntu 14.04 & now with 14.10.

While transferring a large file (2GB) from my Ubuntu laptop to my Vista machine via WLAN the file transfer speed start out very high (30+MB/s) but then rapidly falls off until it gets down into the KB/s range. Up until a few weeks ago I could get 3-5 MB/s. I can't think of anything I changed in this time. 

I have tried a new file manager (Nemo), network manager (Wicd) and changing the Samba configuration per instructions found in this forum and elsewhere on the web.None have had a positive effect.

I have a Toshiba C55t laptop with a Realtek RTL8188EE network card and a Netgear WNR2000v4 router. The router is set to 150Mb/s. Network Manager says the card is operating at 72 Mb/s. 

Does anyone else have this problem and solution?

---

### Post by irv on 2014-11-27
First, I don't have this problem, but there are a few things you can try to pinpoint where the problem is. Okay, did you try restarting your router? If you are doing this over the wifi then try it over a network cable plugged into your router and laptop? This will tell you if it is hardware or software. This is a good starting point.

---

### Post by Morbius1 on 2014-11-27
I don't have a samba specific solution for you although large file transfers seem to be a problem regardless of the protocol being used.

What I do under these conditions - need to copy something from a Linux machine to something else - is to use HTTP:

Let's say my Linux machine has an ip address of 192.168.0.100 and I want to from Windows or OSX or another Linux machine copy a large file from my Videos folder:

*** Open a terminal 
*** Change to my Videos folder:
```
cd /home/morbius/Videos
```
*** Then create a temporary http server at that location:
```
python -m SimpleHTTPServer
```
On the other machine:
*** Open your internet browser
*** For the URL:
```
http://192.168.0.100:8000
```
The contents of your Videos folder become downloadable links in the browser.

Note: Can't download a folder so you would need to create an archive like a zip file of that folder and then download that.

Even if this isn't a long term viable solution you have a reference point for speed since http will likely be the fastest protocol.

---

### Post by jdhamric on 2014-11-27
> **irv said:**
> First, I don't have this problem, but there are a few things you can try to pinpoint where the problem is. Okay, did you try restarting your router? If you are doing this over the wifi then try it over a network cable plugged into your router and laptop? This will tell you if it is hardware or software. This is a good starting point.

Thanks for the reply.

I have reset the router several times with no positive result. This problem seems to have cropped up in the last few weeks; can't figure out why. Router firmware up to date. Internet transfers OK (I have 15 Mb/s service that's steady). I will try your suggestion of a wired connection.

---

### Post by jdhamric on 2014-11-27
Morbius1,

Thanks for the suggestion. The file is being transferred at  about 2MB/s. Slower than I'd expect, but at least it's moving!

---

