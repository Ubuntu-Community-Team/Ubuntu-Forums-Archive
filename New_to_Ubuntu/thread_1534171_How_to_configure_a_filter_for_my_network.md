---
title: "How to configure a filter for my network"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by HumbleandDevout on 2010-07-19
Can somebody please explain how to do this in beginner's terms? [http://www.linux.com/archive/articles/113733](http://www.linux.com/archive/articles/113733)

Thanks.

---

### Post by Iowan on 2010-07-19
Moved to Absolute Beginner Talk

Which part is causing problems?

---

### Post by bodhi.zazen on 2010-07-19
> **HumbleandDevout said:**
> Can somebody please explain how to do this in beginner's terms? [http://www.linux.com/archive/articles/113733](http://www.linux.com/archive/articles/113733)

Thanks.

Squid is almost certainly overkill

You can do this with Privoxy + Dansguardian which is much much easier (IMO).

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

---

### Post by HumbleandDevout on 2010-07-20
I cant find the places in the .conf files to configure them. Thanks.

---

### Post by evstevemd on 2010-07-20
> **HumbleandDevout said:**
> I cant find the places in the .conf files to configure them. Thanks.
I think saying something like i canot move files from xxx to yy will help us who didn't take time to read whole link to throw in our cents ;)

---

### Post by Paqman on 2010-07-20
Probably the easiest way to set up content filtering on one machine is to add the [repository for Ubuntu CE]("http://ubuntuforums.org/showthread.php?t=1492885") and install their app dansguardian-gui-squid. That will give you a nice graphical tool to set up content filtering on your Ubuntu machine.

If you want to filter the whole network, just switch your DNS settings in your router to [Open DNS]("http://www.opendns.com/"). It's free and doesn't involve any messing about installing and configuring software. Plus it might even be quicker than the DNS you're currently getting from your ISP.

---

### Post by bodhi.zazen on 2010-07-20
> **HumbleandDevout said:**
> I cant find the places in the .conf files to configure them. Thanks.

I can't understand what you are trying to configure and what you need assistance with.

Squid ? dansguardian ? Privoxy ?

Squid has a huge configuration file, I think 4,000 + lines, you just need to read it .

That is the main problem with Squid, long complex config file with, IMO, sketchy documentation. Most of the configuration options do not apply to the average home user.

Privoxy is easier to configure and should work out of the box.

There is some (minor) configuration needed with dansguardian.

---

