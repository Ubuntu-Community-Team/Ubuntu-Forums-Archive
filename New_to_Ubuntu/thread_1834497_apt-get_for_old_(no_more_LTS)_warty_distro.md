---
title: "apt-get for old (no more LTS) warty distro"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by gnometorule on 2011-08-27
Is it possible to adjust the sources.list such that I can either...

(1) Access sites for newer distros still at

[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu),

or

(2) Access the old site (which is commented out in my sources.list file after virtually installing warty in VirtualBox), 

or 

(3) Link any deb site that would allow me to add a line in the sources file and use that one?

I've tried (1) using the exact line I see in 10.04; (2) using the old site that was commented out in my warty sources file (however, that was clear not to work as, despite a different name, it links back to the same site of (1), which goes back to hardy only); and (3) using some other deb site. I get the same error message each time:

W: Couldn't stat source package list at (web address, as expanded using the apt-get macros), error code 2

apt-get/apt-cache works fine when linking to the iso image that virutalbox stores, for programs resident on it. Internet access is fine too from within my VM.

I need an easy to install source file for nasm. If none of the above works, what is the easiest to proceed? I already downloaded .rpm files, but would rather apt-get.

---

### Post by snowpine on 2011-08-27
1. Why are you using Warty? It is "end of life" and has had no security support whatsoever for **over 5 years**!

2. Warty repositories were moved to old-releases.ubuntu.com so you should be able to edit your /etc/apt/sources.list accordingly, changing all us.archive.ubuntu.com URLs to old-releases.ubuntu.com (for educational purposes only! not for a production machine.)

3. Source for nasm is here: [http://www.nasm.us/](http://www.nasm.us/) Will the latest version work in Warty? Who knows. ;)

---

### Post by gnometorule on 2011-08-27
Thank you very much. :) However, I still can't get it to run. As to your points...

!1) Exact reason why I run it: I'm working through "Smarhing the stack.." style classical writeups, which is a pain with the level of security ubuntu these days fortunately has.

(2) I still can't get it to work. here is what I added in my sources.list:

```

deb http://old-releases.ubuntu.com/ubuntu warty main restricted
deb-src http://old-releases.ubuntu.com/ubuntu warty main restricted
deb http://old-releases.ubuntu.com/ubuntu warty-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu warty-updates main restricted

deb http://old-releases.ubuntu.com/ubuntu warty universe
deb-src http://old-releases.ubuntu.com/ubuntu warty universe
deb http://old-releases.ubuntu.com/ubuntu lucic-updates warty universe
deb-src http://old-releases.ubuntu.com/ubuntu lucic-updates warty universe

deb http://old-releases.ubuntu.com/ubuntu warty multiverse
deb-src http://old-releases.ubuntu.com/ubuntu warty multivers
deb http://old-releases.ubuntu.com/ubuntu lucic-updates warty multiverse
deb-src http://old-releases.ubuntu.com/ubuntu lucic-updates warty multiverse

deb http://old-releases.canonical.com/ubuntu warty partner
deb-src http://old-releases.canonical.com/ubuntu warty partner

```

I get the same error message. I noticed that it seems that there is further expansion using  what looks like macros in my old distro, and simply are web-addresses in the more recent one  in /var/lib/apt/lists. Could this be related, or did I just do something stupid in the above? 

(3) Thanks much. :)

---

### Post by snowpine on 2011-08-27
> **gnometorule said:**
> Thank you very much. :) 

You're welcome! I'm not sure what you're trying to accomplish but wish you the best. :)

---

### Post by gnometorule on 2011-08-27
Well, it still doesn't work thought - see (2) above. Did I enter anything wrong  in the sources.list lines I copied in above? The .rpm would be a last resort for me, also as it will be useful to generally be able to use apt-get from within warty.

---

### Post by snowpine on 2011-08-27
> **gnometorule said:**
> Did I enter anything wrong  in the sources.list lines I copied in above? 

The main problem I see with your sources.list is "warty" which has been completely unsupported since 2006. I started using Ubuntu in 2007 so that's all the support I can offer, sorry. :(

---

### Post by CatKiller on 2011-08-27
You've mis-spelled a bunch of stuff, there isn't an old-releases.canonical and you don't want to be mixing lucid in with something as old as warty.

---

### Post by gnometorule on 2011-08-27
True that. But I get the same error message for each line, even those that are consistent (probing 'old-releases' with warty, which does exist). So something else would need to be done to get this to work.

I installed from the rpm file, but would still be curious to find out how to get this to work.

---

### Post by XubuRoxMySox on 2011-08-27
I may end up using Lucid probably long after it has reached end-of-life. It's just that awesome on this old 'puter, which I think is immortal considering the abuse I've put it through over the years. To prepare I'll have Aptoncd installed, and fill up a CD with the latest "Lucid versions" of any applications I'm likely to need. Just in case the next LTS is too much for it and in case other distros don't cut it.

But this mixture of old and new brings to mind an unforgettable image:
[IMG]http://img294.imageshack.us/img294/499/floppyfail.jpg[/IMG]

---

### Post by gnometorule on 2011-08-27
Forum replies need a 'like' button. :)

---

