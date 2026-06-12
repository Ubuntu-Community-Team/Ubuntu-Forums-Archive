---
title: "can't connect to linksys nslu2 - connection refused"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by ike on 2007-06-25
Hello,

This is actually not very Ubuntu related, but i thought i'll give it a shot anyway. At least it's debian related ;)

I recently bought myself a linksys nslu2 (aka "slug", [http://en.wikipedia.org/wiki/NSLU2](http://en.wikipedia.org/wiki/NSLU2)). Since the default firmware uses a proprietary file system i had to throw it out and install debian instead. After some struggling with it i finally got through the install process.

When the install (via ssh) finishes, you are disconnected. The device reboots, and you are supposed to connect to it again. But, just as the install finished, my modem freaked out, and I lost all connections between my computer and the slug as well as the net. A few hours later, when my internet connection was working again, the slug had gotten a new IP. Since it has no screen, you can't see the ip address anywhere, if you're not already connected. (i will install some kind of dynamic dns solution though, once I'm able)

I called my ISP and got the IP of the slug, but now it says "connection refused" when I'm trying to
```
$ ssh [slug ip address]
```

Great. So now I'm locked out of the slug, but I have no idea why. I also tried connecting with ftp, but that just gave me another "connection refused". I can ping it, btw..

I can connect the usb drive that holds the slug root partition to my laptop and edit configuration files, but I'm not sure what to edit.. I guess the default debian installation disallows remote logins from anywhere but the local network (and it probably thinks that my laptop is from outside the lan, since they both have public IP's, probably on different subnets..), but how do I change that?

Any ideas?

Thanks in advance.

---

### Post by ike on 2007-06-25
Solved! I found the solution here:
[http://www.nslu2-linux.org/wiki/Debian/FAQ:](http://www.nslu2-linux.org/wiki/Debian/FAQ:)

Also, by looking at the logs I could get hold of the correct ip.
hint: try something like
> sudo cat /path/to/usbdrive/var/log/* | grep DHCP

---

