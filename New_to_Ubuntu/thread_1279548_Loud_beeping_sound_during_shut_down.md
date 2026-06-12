---
title: "Loud beeping sound during shut down"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by searcher1 on 2009-09-30
I recently installed Ubuntu 9.04 on an external hard drive and run it from there. Whenever I use Ubuntu I remove the internal hard drive which contains Win XP. The computer makes several loud beeping sounds whenever I shut down Ubuntu, although the shut down process seems to proceed smoothly after that. There are no error messages and everything else seems to be working fine. Is there anything wrong? Thanks for any advice.

---

### Post by renkinjutsu on 2009-09-30
That used to happen to me... very annoying, but didn't seem like there was anything to worry about

so.. i added `pcspkr` to the module blacklist in `/etc/modprobe.d/blacklist.conf`
```
sudo echo pcspkr >> /etc/modprobe.d/blacklist.conf
```
NOTE: that will take effect after a reboot..

for an immediate, albeit temporary effect, do ```
sudo modprobe -r pcspkr
```

---

### Post by searcher1 on 2009-10-01
Thanks for the quick response. I got the following:

searcher1@linux:~$ sudo echo pcspkr >> /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied

The other method you suggested works, but I'll need a more permanent solution. Thanks again!

---

### Post by desmane on 2009-10-01
I am not 100% sure about the permission issue but maybe do

```
sudo nano /etc/modprobe.d/blacklist.conf
```

(I think u can use any file in /etc/modprobe.d/ - folder)

and append a line: 

> blacklist pcspkr

---

### Post by wojox on 2009-10-01
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Then add to the bottom of the file:

```
blacklist pcspkr
```

---

### Post by searcher1 on 2009-10-01
Great!! Looks like you've solved my problem. Many thanks!

---

### Post by random turnip on 2009-10-01
I thought this was just something Ubuntu did, just like a system beep when shutting down.  I might take it off mine too, lol.  Thanks

---

