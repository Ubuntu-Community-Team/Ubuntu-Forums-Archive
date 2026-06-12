---
title: "ubuntu 9.10"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by jrev on 2010-03-25
Hi all,
How can I find out the type and vendor of my DVD-RW drive in order to download a driver ?
Thanks in advance for your help ;)

---

### Post by byStanderone on 2010-03-25
...you can try sysinfo, here's the link:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=sysinfo](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=sysinfo)

---

### Post by 3rdalbum on 2010-03-25
There's no such thing as "downloading a DVD-RW driver". All optical drives communicate with the computer in exactly the same way, so the single driver is built-in to all operating systems. What problem exactly are you having?

---

### Post by jrev on 2010-05-18
I had recently the same problem with my sound card that Sysinfo gives as :

[SIZE="6"][COLOR="Blue"]ATI Technologies inc radeon X1200 series audio controller.[/SIZE][/COLOR]

The corner computer shop told me he found the driver on the site
"touslesdrivers.com"

I went to the site but couldn't find the way to download this specific Linux driver for  Ubuntu 10.04
this driver was part of the 9.10 version so I am not used to download a Linux driver.
Is there a tutorial to show us how to do it ?

Thanks for your answer :P

---

### Post by 3rdalbum on 2010-05-18
If the driver was present in Ubuntu 9.10, it should be present in 10.04.

Have you checked the 'alsamixer' program to see if all the audio output channels are turned up?

```
alsamixer
```

---

### Post by jrev on 2010-05-19
[SIZE="4"]You are right, but it was not the case.
Yes I did check alsamixer first.
I am still looking for the howto download a linux driver for my sound card 

Thanks[/SIZE]

---

