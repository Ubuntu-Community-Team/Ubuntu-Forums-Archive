---
title: "firefox 3.6 from terminal"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by 3948ctyj on 2010-04-03
Synaptic doesnt have newer firefox... I cant see it anyhow.....
 how can I get newest Fox from terminal..???  need deb or self installing file..
need exact command...

---

### Post by takisan on 2010-04-03
Well, if it's not in the repos, then it's going to be hard to get.
You'll have to head to the mozilla site and get it via either a wget ([ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.3/linux-i686/en-GB/firefox-3.6.3.tar.bz2](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.3/linux-i686/en-GB/firefox-3.6.3.tar.bz2)) or a FTP transaction. Then extract that tar.bz2 in /usr/bin (with root permission.)
If it doesn't show up in synaptic, you'll have to just wait or get it from that method.

---

### Post by gocek on 2010-04-03
You can also use another repository:

Here's what you need to do on Ubuntu 9.10:

```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```

And you can run the upgrade's manager to download the newest firefox (which is 3.6)

---

### Post by bhmildy on 2010-04-03
Wow, noob here, but really don't recommend that you go install dailies into your computer.  I hosed my sources list, which gives me back errors, while trying to install the latest firefox manually.  Also, ended up installing an alpha, which was really unstable.  I don't think that that's good advice.

Ubuntu just pushed today or yesterday FF 3.6.2 down on me automatically.  Go to Synaptic and reload, and see if it's waiting out there before doing manual and daily install.  I'd consider living without it if you're new enough to Ubuntu to need instructions on how to do this, because it's a PITA to fix.

---

### Post by louieb on 2010-04-03
This guy knows Firefox - and here's  his thread.
[Firefox optimization and troubleshooting thread - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=firefox") 

BTW: I agree with bhmidly  > but really don't recommend that you go install dailies into your  computer. 

---

### Post by lovinglinux on 2010-04-03
> **louieb said:**
> This guy knows Firefox - and here's  his thread.
[Firefox optimization and troubleshooting thread - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=firefox") 

BTW: I agree with bhmidly

Thanks for your comment. ;)

> **bhmildy said:**
> Wow, noob here, but really don't recommend that you go install dailies into your computer.  I hosed my sources list, which gives me back errors, while trying to install the latest firefox manually.  Also, ended up installing an alpha, which was really unstable.  I don't think that that's good advice.

Ubuntu just pushed today or yesterday FF 3.6.2 down on me automatically.  Go to Synaptic and reload, and see if it's waiting out there before doing manual and daily install.  I'd consider living without it if you're new enough to Ubuntu to need instructions on how to do this, because it's a PITA to fix.

I also don't recommend the *ubuntu-mozilla-daily* anymore, mainly because it doesn't stop updating when it reaches a stable version and lots of people complain later. 

My advice, if you have 32 bit, use Ubuntuzilla. It will keep Firefox updated with the latest stable releases from Mozilla. If you have 64bit, download from Mozilla FTP nightlies directory and extract it to /opt/firefox. More info on my tutorial (quoted above).

---

### Post by 3948ctyj on 2010-04-03
what is the latest I can get from synaptic????  and exactly how in terminal....spaces,caps  etcc

---

### Post by lovinglinux on 2010-04-03
> **3948ctyj said:**
> what is the latest I can get from synaptic????  and exactly how in terminal....spaces,caps  etcc

See the [COLOR="Sienna"]**Installing Other Versions**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by 3948ctyj on 2010-04-03
I got the deb file fro ubun tuzilla

thats all I needed folks

---

