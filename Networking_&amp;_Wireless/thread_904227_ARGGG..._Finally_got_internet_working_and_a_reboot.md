---
title: "ARGGG... Finally got internet working and a reboot wipes it all... help please."
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by jamorama on 2008-08-29
ok, so after getting a driver update from ubuntu (automatic), the blue light on my compaq v2000(yes, its old, so i installed ubuntu) finally turned on. I was able to see the networks but was unable to connect. After running the command "sudo /etc/init.d/networking restart" I finally got it connected. Then, I restarted... and it wiped the driver that was updated from ubuntu(fwcutter43 or something) and now the blue light won't turn on... please help? 

~Cause the driver I installed wasn't there after I rebooted... its weird...

---

### Post by Sam Lars on 2008-08-29
Could you post the output of
```
lspci | grep Network
```
I'm not sure what you need yet, but you could try
```
sudo rmmod b43
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo rmmod ssb
sudo modprobe b43
```
That may not all be necessary, but we'll start there.

---

### Post by jamorama on 2008-08-29
As I said, I could get the internet to work, but only after ubuntu downloaded a driver for me (it notified me that I needed a driver) and it worked after i installed it. After I shut down and then booted up, the driver was gone... how do I get the driver to stay installed? 

~I am using Wubi, if that affects anything...

---

### Post by Sam Lars on 2008-08-29
I don't think it's "uninstalled."  It may be that it doesn't work anymore or that it's not being loaded anymore.
I'd like to know the output of
```
lspci | grep Network
```
so that I know what driver you should/could be using.
You mentioned what is probably b43-fwcutter.  That's why I thought you may need the b43 driver, and so I suggested that you try reloading it and making sure nothing is conflicting with it.
Also, you should check
```
/etc/modules
```
to see if at the end one of the drivers I mentioned in the last post are set to load at boot.
And
```
/etc/modprobe.d/blacklist
```
to see if any of the drivers I mentioned in the last post are set to not load automatically on boot.

---

