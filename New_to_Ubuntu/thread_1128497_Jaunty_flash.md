---
title: "Jaunty flash?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-17
Just upgraded my 8.10 amd64 system to the jaunty beta but one problem I have at the moment is websites in Firefox keep telling me to install the latest flash as I don't have it when infact according to synaptic I already do:(

already tried reinstalling via synaptic...

---

### Post by ssdt on 2009-04-17
This must be a bug that still isn't fixed. But no one seemed to faced this before.

---

### Post by James_Lochhead on 2009-04-17
[LIST]
[*]Download [this.]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz")
[*]Extract it.
[*]Place it in the folder ~/.mozilla/plugins. If plugins doesn't exist create it.
[/LIST]

There we go. You have (64 bit!) flash.

---

### Post by kamitsukai on 2009-04-17
> **James_Lochhead said:**
> [LIST]
[*]Download [this.]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz")
[*]Extract it.
[*]Place it in the folder ~/.mozilla/plugins. If plugins doesn't exist create it.
[/LIST]

There we go. You have (64 bit!) flash.

worked brilliantly! should I file a bug report for this?

---

### Post by James_Lochhead on 2009-04-17
I would be a good idea if you have a spare 10 minutes. It can't hurt. In case you haven't reported before: you need an account at launchpad.net.

---

### Post by kamitsukai on 2009-04-17
> **James_Lochhead said:**
> I would be a good idea if you have a spare 10 minutes. It can't hurt. In case you haven't reported before: you need an account at launchpad.net.

That's Ok, I already have an account bug posted here:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/363124](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/363124)

Thanks again:D

---

### Post by slimx3m on 2009-04-22
thnx for the help. awesome.

---

### Post by maqifrnswa on 2009-04-24
Since this is the #1 hit on google for "jaunty flash," I'd like to post this update from:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/363124](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/363124)

by John Vivirito:

> Please remove gnash and swfdec and than install flashplugin-installer. I am able to get it to work just fine with only flashplugin-installer installed please see screenshot. Your problem is not in flash it is the local set ups.

the screen shot he refers to is:
[http://launchpadlibrarian.net/25928498/bug%23363124.png](http://launchpadlibrarian.net/25928498/bug%23363124.png)

However, I had this problem and I don't have gnash nor swfdec. I installed it by getting the file from Adobe's website and placing it in my ~/.mozilla/plugins folder.


EDIT:
The bug is a duplicate of:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/144042](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/144042)
more information is there

---

### Post by ssdt on 2009-04-24
Did the flash problem in Jaunty get fixed in the final release? I'm thinking of getting it today and want to check it out. I just don't want to get into any problem with that.

---

### Post by Dougie187 on 2009-04-24
I had no problems with flash in Jaunty 64 bit fresh install. Just installed ubuntu-restricted-extras and it took care of everything.

---

### Post by ssdt on 2009-04-24
Could they make the new version so that it has Medibuntu preinstalled because from NY it takes a long time just to download it, installing wouldn't because I have 2 gig ram.

---

### Post by stchman on 2009-04-24
> **kamitsukai said:**
> worked brilliantly! should I file a bug report for this?

This is not really a bug per se.  64 bit Flash 10 for Linux is still under some development.

---

### Post by kamitsukai on 2009-04-24
> **ssdt said:**
> Could they make the new version so that it has Medibuntu preinstalled because from NY it takes a long time just to download it, installing wouldn't because I have 2 gig ram.

It's taking ages because the servers are being constantly hammered I'm afraid, normally it would take a couple of minutes on semi ok Broadband...

---

### Post by stonew508 on 2009-07-21
how do I get permission to place the file in the folder?

---

### Post by kamitsukai on 2009-07-23
> **stonew508 said:**
> how do I get permission to place the file in the folder?

go to terminal and type:

```
sudo nautilus
```

and then browse to the folder you want

---

