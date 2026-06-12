---
title: "Madwifi Install Help, Please!"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by JeffoOfMetal on 2008-02-16
I have had great trouble figuring out exactly what I have to do to make my Atheros wireless chip work. I know it has something to do with Madwifi, but I have never understood what to do. I'm sorry that this is another Madwifi post, but I am desperate to get this working. Could I be shown what exactly I must do and download to get my wireless working, step by step, please? 

This is terribly confusing. :(

I have an Atheros 5007eg with Ubuntu installed.

---

### Post by JeffoOfMetal on 2008-02-16
Please! This means a lot to me. At least may I know how you configured Madwifi, if you did?

---

### Post by tturrisi on 2008-02-16
You cannot stably use madwifi with the AR5007 chipsets, you will have to use the windows driver and ndiswrapper.
[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

Ther is a madwifi "snapshot" patched driver that supposedly works w/ that chipset:
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

---

### Post by JeffoOfMetal on 2008-02-17
Ok, so I downloaded the tarball for the "snapshot," but I can't install it. I put in: 
```
jeffobazoni@ubuntu:~$ make '/home/jeffobazoni/Desktop/madwifi-ng-r2756+ar5007' 
]
``` 

into the terminal, but all I get is:

```
make: Nothing to be done for `/home/jeffobazoni/Desktop/madwifi-ng-r2756+ar5007'.
]
```

What am I doing wrong? I am so frustrated because I don't understand how to compile tarballs. Please, help! :(

---

### Post by JeffoOfMetal on 2008-02-17
Ok, nevermind, I got it installed, but now, I am lost at how to make it work. The readme says to type in "modprobe ath_pci" but I got absolutely no output whatsoever. This is a pain in the neck. Please, what do I do?

---

### Post by JeffoOfMetal on 2008-02-17
Oh my god! YES! Thank you *so much!*. I had been using this laptop with a USB wireless adapter for ages, and when I finally restarted, I rejoiced to see that I had connectivity without it! Thank you very much, and sorry to trouble you. Thank you, thank you! :):):):)

---

