---
title: "will firefox automatically update to the newer 3.5 version?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by aszxcv on 2009-06-30
i have ubuntu 8.04 and it has update up the chain of the various 3.0.XXXX to now 3.0.11

---

### Post by xavierp94 on 2009-06-30
Last version of Firefox it took a day for Ubuntu to ask me for an update.

---

### Post by lovinglinux on 2009-06-30
Probably not. Updating version 3.0.x to 3.0.y is completely different than updating from 3.0.y to 3.w.z. This is a major release, but only security patches are incorporated into the repositories. Besides, Firefox 3.0.x won't be left unsupported for a while.

---

### Post by sadaruwan12 on 2009-06-30
Let the time decide it 'cos ubuntu normally takes the most stable version of softwares in to the repo's let the 3.5 get settled and it'll come around.

---

### Post by aszxcv on 2009-06-30
i really want to get 3.5 . but reading the post here it seem unsafe. is this true or not? i have the firefox-3.5.tar.bz2 sitting on my desktop but i am unsure on how to install it. i want to use the new features of 3.5 such as html5 goodies  etc...

---

### Post by mcduck on 2009-06-30
FF3.5 is already available in 9.04's repositories as separate package, so you can install it if you want. Time will show if it will replace FF3 completely or stay as optional extra.

(the basic rule is that packages are updated only for security reasons and to fix serious bugs, and that would mean that FF3.5 wouldn't replace FF3 as long as security updates for FF3 are possible..)

---

### Post by lovinglinux on 2009-06-30
For instructions on how to install Firefox 3.5 or upgrade the 3.0.11 version, check the [color=#CC0000]**Firefox Alternatives & Newer Versions**[/color] section of the [**[color=#CC0000]Firefox optimization and troubleshooting thread[/color]**](http://ubuntuforums.org/showthread.php?t=1193567).

For a list of other threads talking about the same subject, visit [http://ubuntuforums.org/showthread.php?t=1200781](http://ubuntuforums.org/showthread.php?t=1200781)

---

### Post by dpolehn on 2009-07-01
> **aszxcv said:**
> i really want to get 3.5 . but reading the post here it seem unsafe. is this true or not? i have the firefox-3.5.tar.bz2 sitting on my desktop but i am unsure on how to install it. i want to use the new features of 3.5 such as html5 goodies  etc...

just finished doing this on my machine.

```

cd Desktop/
tar -xjf firefox-3.5.tar.bz2
sudo mv ./firefox/ /usr/lib/firefox-3.5/
cd /usr/bin/
ln -s /usr/lib/firefox-3.5/firefox firefox-3.5

```

then close out of all of your open firefox windows and run

```
firefox-3.5
```

---

### Post by Sef on 2009-07-01
The easiest way to get Firefox 3.5 is to use Ubuntu's [PPA for Firefox]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").  That way you will get any updates too.

---

### Post by lovinglinux on 2009-07-01
> **Sef said:**
> The easiest way to get Firefox 3.5 is to use Ubuntu's [PPA for Firefox]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa").  That way you will get any updates too.

That didn't work for me. I already had firefox-3.5 (Shiretoko) installed, but when I used the PPA it only updated to rc2 and I wasn't able to open Shiretoko anymore. 

So I decided to try [Ubuntuzilla](http://ubuntuzilla.wiki.sourceforge.net/) and it works like charm. Easy to install and remove.

---

### Post by jou770d on 2009-07-01
> **lovinglinux said:**
> 
So I decided to try [Ubuntuzilla](http://ubuntuzilla.wiki.sourceforge.net/) and it works like charm. Easy to install and remove.

There's a small problem with Ubuntuzilla, if you're running a 64 machine it will still install a 32 version of Firefox.

---

