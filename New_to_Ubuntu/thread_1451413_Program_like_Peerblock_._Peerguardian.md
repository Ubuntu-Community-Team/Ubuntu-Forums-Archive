---
title: "Program like: Peerblock . Peerguardian"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by RaceNChase on 2010-04-10
Hello,

First post

Switching to ubuntu with the help of a friend, so I have been getting some help.  However, in the windows world I used a program called peergaurdian.  What is the Linux equivalent?

Thanks

---

### Post by uRock on 2010-04-10
Welcome to the forums:)

What does peerguardian do?

If you are looking for a DNS server that filters out the "bad sites" then Dansguardian may what you are looking for. If so, check out this link and scroll down to the dansguardian tutorial. [http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

Cheers,
Ronnie

---

### Post by WinterRain on 2010-04-10
Transmission, which is included in ubuntu, has a peerguardian type blocker program built in. Just go to edit>preferences>privacy and turn it on and update it.

---

### Post by EssexEagle on 2010-04-10
> **RaceNChase said:**
> Hello,

First post

Switching to ubuntu with the help of a friend, so I have been getting some help.  However, in the windows world I used a program called peergaurdian.  What is the Linux equivalent?

Thanks

I've never used PeerGuardian or anything like it, but I Googled and found MoBlock which appears to be an equivalent: official Ubuntu documentation [here]("https://help.ubuntu.com/community/MoBlock").

---

### Post by uljanow on 2010-04-10
Checkout [http://ubuntuforums.org/showthread.php?t=530183](http://ubuntuforums.org/showthread.php?t=530183)

---

### Post by RaceNChase on 2010-04-10
wow thanks for the ultra fast responses.  I am looking at these iplist, mobloquer, they look the easiest, however none of them show to be for 10.04 can I use a previous version.

---

### Post by uRock on 2010-04-10
> **RaceNChase said:**
> wow thanks for the ultra fast responses.  I am looking at these iplist, mobloquer, they look the easiest, however none of them show to be for 10.04 can I use a previous version.

You may not find much on those for 10.04 until after it releases.

---

### Post by 2hot6ft2 on 2010-04-10
Deluge has it built in but I don't know what version if any 10.04 has yet in the repos. but in some the url for the blocklist needs to be changed from pointing to a .com or .org I forget which to .info the rest of the url stays the same. It will automatically update and load it for you once setup.

First you have to activate the blocklist plugin then it will be available to configure.

---

### Post by RaceNChase on 2010-04-10
well i did the transmission plugin for torrents but i was looking for a blocker to use in conjunction with frostwire.  So the iplist or the mobloquer would probably work best but it appears that a 10.04 release is not available yet.

---

### Post by uljanow on 2010-04-10
Actually iplist is available for 10.04. 

Updated instructions:
```
sudo wget http://iplist.sf.net/sources.list.d/lucid.list -O /etc/apt/sources.list.d/iplist.list
```
Or
```
deb http://ppa.launchpad.net/ssakar/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/ssakar/ppa/ubuntu lucid main
```

---

### Post by mkvnmtr on 2010-04-10
I use IPBlocker on 10.04. Works fine. it is for more than just torrenting. It bIf you wish it blocks many sites.

---

### Post by RaceNChase on 2010-04-10
thank you!

---

