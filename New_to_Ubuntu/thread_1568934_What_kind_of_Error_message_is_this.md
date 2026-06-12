---
title: "What kind of Error message is this????"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by suomalainen on 2010-09-06
Ubunteros,

I received this error message and would like to know:

1. What it means ?
2. Is it serious ?
3. Is it possible to fix and if so how?

Thanks for your support!!!!

---

### Post by TNT1 on 2010-09-06
I got that at work the other day when they redid the AD and setup a new domain. I ignored it. It means you wont be logged onto the domain, which usually is not a problem. When you want to access shared network drives, you will be asked for your domain credentials.

---

### Post by suomalainen on 2010-09-06
I don't use any shared network drives.... I installed Ubuntu 10.04 on my laptop 6 months ago and never had this message before until today.

The only thing I did do today was set up a new broadband GSM wireless connection for my USB stick. But I've done this before too w/o such error message....

Any ideas or thoughts?

---

### Post by suomalainen on 2010-09-07
ding dong

---

### Post by silverglade00 on 2010-09-07
Avahi is the service that runs on your computer that goes out on the network and looks for other computers that it can talk to. If you have used iTunes, it's the thing that lets you share your music with others and lets you listen to their shared music. It looks like when you set up your GSM, it gave your computer a .local domain designation. Meaning if you named your computer suoma-computer, it created an entry in your hosts file that says suoma-computer.local. Avahi is not compatible with a .local entry in that file, so the Avahi service on your computer stopped running. That is what the error message is telling you. If you do not need that service, then you can safely ignore the error. If you want those features, then you can type
```
gksudo gedit /etc/hosts
```
and remove the part that says .local.

---

### Post by suomalainen on 2010-09-07
silverglade00,

Thanks for the great explanation and detail. Much appreciated!

I ran the command you gave and attached is the info I received back.

Apparently there is not .host file?

What's this mean then?

Thanks for your support!

---

### Post by silverglade00 on 2010-09-07
The only thing I can think of is to go into the settings for your GSM connection and make sure nothing there says o-laptop.local. I have never messed with a GSM connection, so I'm not sure how to do that.

---

### Post by suomalainen on 2010-09-07
I'm using NETWORK CONNECTION manager to make new broadband wireless gsm connection and it doesn't even ask for this nor does it even list it.

---

### Post by suomalainen on 2010-09-08
Can anyone answer my question in post #6??? as can be seen .local does not exist.....

---

