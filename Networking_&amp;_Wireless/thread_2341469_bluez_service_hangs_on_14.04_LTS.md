---
title: "bluez service hangs on 14.04 LTS"
date: 2016-10-28
forum: Networking &amp; Wireless
---

### Post by saltydingo on 2016-10-28
The init script that comes with bluez 5.35 isn't working properly, and I can't figure out why. It hangs on initial start or stop, breaking things such as graceful reboot, upgrades, purges or reinstalls:
> user@host:~$ sudo start bluetooth
^Cuser@host:~$ sudo start bluetooth
start: Job is already running: bluetooth
user@host:~$ sudo stop bluetooth
^Cuser@host:~$ sudo stop bluetooth
stop: Job has already been stopped: bluetooth

I've had a really good look at /etc/init.d/bluetooth, /etc/init/bluetooth.conf and /etc/default/bluetooth, but I can't isolate the problem. Would appreciate some help.

---

### Post by saltydingo on 2016-11-09
> **saltydingo said:**
> Remember the good times when you were an unfathomable font of wisdom and helpfulness? I still believe you are that same internet. It's in there. You just have to believe in yourself again.
*Let's Go Internet Let's Go!*

---

### Post by howefield on 2016-11-09
Thread moved to the "*Networking & Wireless*" forum seeing as you are having no luck in *General Help*, you might fare better here.

(and removed a couple of the bumps.)

---

### Post by jeremy31 on 2016-11-11
I may have tried it in the past but I likely had bad results as some of my searches says doing this results in the GUI not working.  You may want to try Ubuntu 16.04 as my laptop shows bluez 5.37 installed

---

### Post by saltydingo on 2016-11-17
I'm not worried about the GUI - it's a media PC dedicated to running kodi. Thank you very much for responding though.

---

### Post by saltydingo on 2016-11-26
Give me a T!

---

### Post by wildmanne39 on 2016-11-26
> **saltydingo said:**
> Give me a T!If this is meant to be a bump please just write bump, otherwise people may ignore your post as nonsense or it may be jailed!
Thanks

---

### Post by saltydingo on 2016-11-27
> **wildmanne39 said:**
> If this is meant to be a bump please just write bump, otherwise people may ignore your post as nonsense or it may be jailed!
Thanks
If somebody reads the OP and thinks that this should be jailed, this is also an outcome of sorts. I want to know where this great community is I've heard so much about. I've linked this post on reddit and bumped regularly over the last month and not a single bit of help (except from a kind mod, who moved the thread after I got no response). Countless times before I have hit something like this and reinstalled - not this time. If something as common as a bluetooth service receives no assistance, I don't think this is a platform I want in my life. 

Also, give me an E!

---

### Post by saltydingo on 2016-11-30
Oh cool, I fixed it.

---

### Post by jeremy31 on 2016-11-30
Do you mind sharing the details?  This might be a unique situation but someone else might benefit from what you have found

---

### Post by z0rn on 2016-12-30
> **saltydingo said:**
> Oh cool, I fixed it.

 Please share your solutions. I also struggle with this problem.

---

### Post by antisol2 on 2017-05-10
I'm also having this problem and would love to hear how it is solved. So far I've been able to narrow it down to the call to initctl in the init script, but that's as far as I've managed to get

---

### Post by antisol2 on 2017-05-10
OK, so I managed to figure out a VERY UGLY and hacky workaround. It's very nasty and you may need to reapply it when bluez is updated. but it works for me

I figured out that bluez4 wasn't daemonizing, so I replaced the binary with a small wrapper script which runs the real binary in the background:
```


$ cd /usr/sbin
$ sudo mv bluetoothd bluetoothd.real
$ sudo vi bluetoothd
(insert script content below)
$ sudo chmod a+x bluetoothd
$ sudo service stop bluetooth
$ sudo service start bluetooth


```

Contents of the bluetoothd script:

```

#!/bin/bash
#run the real binary in the background:
# note that /usr/sbin/bluetoothd is a symlink on my system. the real binary may be in a different location on your machine (particularly if you're on 32bit)
/usr/lib/x86_64-linux-gnu/bluetooth/bluetoothd $* &

```

A better option would be to use the alternatives system ('update-alternatives') to point bluetoothd at the script.

---

