---
title: "Karmic and Thunderbird 3 ppa"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by cjnkns on 2010-01-23
I want to install Thunderbird 3 and I was going to follow the directions here.

[http://digitizor.com/2009/12/10/how-to-install-thunderbird-3-shredder-in-ubuntu-9-10/]("http://digitizor.com/2009/12/10/how-to-install-thunderbird-3-shredder-in-ubuntu-9-10/")

The instructions say to add the ppa then remove the ppa after installation.

Why would we want to remove the ppa? We will not get any updates to Thunderbird if we do that correct?

---

### Post by ankspo71 on 2010-01-23
Hi,
I don't know why they would tell you to remove it, but I think they are telling you to do that to avoid continuous updates that could be buggy (alpha, beta, rc, etc).

I think this is the actual PPA page:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa")

Hope this helps.

Oh yeah, you don't have to actually remove the lines from /etc/apt/sources.list if you don't think you want updates
You can simply use # in the beginning of the lines to comment them out (to disable them)

---

### Post by lovinglinux on 2010-01-23
I use that method, since I have 64bit system, but I don't disable the PPA. Nevertheless, I will be continuously served with updates as already mentioned.

If you have 32bit, you could use [Ubuntuzilla](http://ubuntuzilla.wiki.sourceforge.net/). It will keep your Thunderbird and Firefox in sync with Mozilla releases.

---

### Post by Norm24 on 2010-01-23
+1 for Ubuntzilla.

---

### Post by cjnkns on 2010-01-23
OH nice! I never knew of Ubuntuzilla! Thanks!

---

### Post by aquascrotum on 2010-01-23
Not wanting to hijack the thread - I discovered Ubuntuzilla earlier today and jumped in with both feet.  I'd previously been running Shiretoko (Mozilla dailys).

However I'm not sure if my eyes are decieving me by the Ubuntuzilla build of Firefox seems to be rendering pages poorly, even the text on this page is blurry compared to before I changed.

Is this to be expected?

---

### Post by lovinglinux on 2010-01-23
> **aquascrotum said:**
> Not wanting to hijack the thread - I discovered Ubuntuzilla earlier today and jumped in with both feet.  I'd previously been running Shiretoko (Mozilla dailys).

However I'm not sure if my eyes are decieving me by the Ubuntuzilla build of Firefox seems to be rendering pages poorly, even the text on this page is blurry compared to before I changed.

Is this to be expected?

There are some reports of problems with Firefox 3.6 font rendering. I don't think it is ubuntuzilla's fault, since most complains comes from people using ubuntu-mozilla-daily ppa.

Anyway, see **Solution** [*[COLOR="Red"]**FOT012**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT012). I guess that could help.

---

### Post by FrancoNero on 2010-01-24
ubuntuzilla is quite useless if you have 64bit.

also, what's so hard about having a PPA or offering .deb files for download, Mozilla? i dont get it.

at least i found a firefox-stable PPA on launchpad now. so now all i have to do is find one for thunderbird, too.... finally wipe that evolution off my harddrive

---

