---
title: "Running in Circles ~ ubuntu what is my signing key"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by Andavane on 2011-08-09
I've trying to add the repository lorenzo-carbone/atareao to 11.04 and am getting this:

> andavane@andavane-VGN-S3HP:~$ sudo add-apt-repository ppa:lorenzo-carbonell/atareao
[sudo] password for andavane: 
Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~lorenzo-carbonell/+archive/atareao](https://launchpad.net/api/1.0/~lorenzo-carbonell/+archive/atareao)
andavane@andavane-VGN-S3HP:~$ 

The problem is is don't know what a "signing key" is, let alone a "fingerprint". I've looked all over the net and the Ubuntu wiki, but all the posts seem to assume that everyone knows the basics! :confused:

---

### Post by Paqman on 2011-08-09
Judging from that guys Launchpad page that PPA isn't around any more. The list of what he's got in PPAs is [here]("https://launchpad.net/~lorenzo-carbonell/+ppa-packages"). What packages did you want to install?

---

### Post by Andavane on 2011-08-09
> **Paqman said:**
> Judging from that guys Launchpad page that PPA isn't around any more. The list of what he's got in PPAs is [here]("https://launchpad.net/~lorenzo-carbonell/+ppa-packages"). What packages did you want to install?

It's called My Weather Indicator and apparently it's got all sorts of data you can look at. I want it cos I miss the old gnome weather applet which isn't available on Unity.

---

### Post by Paqman on 2011-08-09
It's available for Natty in one of those PPAs: 
```
sudo add-apt-repository ppa:atareao/test
```

If that's a testing repo the software may be a little rough around the edges.

---

### Post by moorhead98 on 2011-08-09
To get it, after adding that ppa, type in
```
 sudo apt-get update
```
and then
```
 sudo apt-get install my-weather-indicator
```
Then find the program (my weather indicator) by searching the via the dash, and select your city/location. 
also make sure you hit "autostart on login" so it will automatically start

---

