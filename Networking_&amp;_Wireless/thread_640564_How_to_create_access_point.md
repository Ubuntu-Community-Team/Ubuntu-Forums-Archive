---
title: "How to create access point ?"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by dinoc on 2007-12-14
Hi guys,

Is there a simple tutorial to create a Access Point in Ubuntu ?

I have an Atheros PCI card which worked for me as an AP in an OpenBSD box , all I had to enable the access point was to edit the /etc/hostname.ath0 lie this :
" inet 10.10.10.1 255.255.255.0 NONE media autoselect mediaopt hostap nwid "bla bla" nwkey 0xblablablabla chan 10"

Is there a simple way to create an AP (with the same card) in Ubuntu ? 
Nothing found in the Docs about this ?

Cheers

---

### Post by olejorgen on 2007-12-14
Not a complete answer, but I guess you should look into iwconfig
iwconfig <dev> mode master maybe?

---

### Post by dinoc on 2007-12-18
Well it looks like it doesn't work:
```

iwconfig ath0 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.

```

It looks like the card doesn't support "master" mode in Ubuntu. Tough the Open BSD does support Access Point mode for the "ath" drivers  ...

Maybe I need other drivers for Ubuntu ?

---

### Post by ways on 2008-04-16
something like this, perhaps? but i havent quite gotten it right myself yet.

iwconfig ath0 mode master essid "name" channel auto key off

---

### Post by porterusaf on 2008-04-16
This is exactly what your looking for...

[http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283)

I've got my atheos card working, but I'm stuck on trying to set it up with encryption, so if you get that figured out, let me know! =)

-Porter

---

