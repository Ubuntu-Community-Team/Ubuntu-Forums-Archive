---
title: "How to install wine without internet access?"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by thetwobob on 2011-05-19
I've recently installed Ubuntu 11.04 on a computer and don't have access to the internet on that computer. All the instructions that I've seen on how to install wine involve being connected to the internet, which I am not. So is there a way that I could just download the needed files on the computer which I am using now (which runs Vista) and just use my flash drive to send the files to the computer running Ubuntu?

---

### Post by hhh on 2011-05-19
Yes, but you might have to do a bunch of running back and forth to install all the dependencies...
[http://packages.ubuntu.com/natty/wine1.3](http://packages.ubuntu.com/natty/wine1.3)

---

### Post by thetwobob on 2011-05-19
In your opinion would it be impractical to install all of those dependencies?

---

### Post by hhh on 2011-05-19
Give it a shot, a lot of them might already be installed.

---

### Post by oldos2er on 2011-05-19
You could try Keryx: [http://keryxproject.org/](http://keryxproject.org/)

---

### Post by scorpious on 2011-05-19
I tried doing that myself a while back. gave up after a while, took my pc into town and used the internet:o

---

### Post by fritz269 on 2011-05-19
starbucks has free wifi, of course that only works if you have a laptop, or you could be "that Guy"

---

### Post by jfreak_ on 2011-05-20
I am not sure how safe this is or even if it is recommended but [http://dev.carbon-project.org/debian/wine-unstable/](http://dev.carbon-project.org/debian/wine-unstable/) gives the package and its dependencies for download for Debian Sid. Perhaps other forum members may advise you further on its viability.

---

### Post by jre6 on 2011-05-20
Installing all of the dependencies is not needed. You can just download these to install wine:
cabextract : [http://packages.ubuntu.com/natty/cabextract](http://packages.ubuntu.com/natty/cabextract)
gettext : [http://packages.ubuntu.com/natty/gettext](http://packages.ubuntu.com/natty/gettext)
libmpg123-0 : [http://packages.ubuntu.com/natty/libmpg123-0](http://packages.ubuntu.com/natty/libmpg123-0)
libopenal1 : [http://packages.ubuntu.com/natty/libopenal1](http://packages.ubuntu.com/natty/libopenal1)
wine1.3 : [http://packages.ubuntu.com/natty/wine1.3]("http://packages.ubuntu.com/natty/wine")

Transfer these packages to your home folder, and type in a terminal:
```

cd ~
sudo dpkg -i cabextract*.deb gettext*.deb libmpg123-0*.deb libopenal1*.deb wine1.3*.deb

```And wine will be installed

---

### Post by 3rdalbum on 2011-05-20
I see you have a thread about a non-functioning Ethernet card. I just want to check that you're not trying to use Wine to install Windows drivers for your Ethernet card, because **Wine will not work for this purpose**.

After shutting down completely and starting up again, did the suggestion given by PowerBarry in the earlier thread ([http://ubuntuforums.org/showthread.php?t=1761947](http://ubuntuforums.org/showthread.php?t=1761947)) work? Did anything change in your 'ifconfig' output?

---

### Post by 1991sudarshan on 2011-05-20
> **thetwobob said:**
> I've recently installed Ubuntu 11.04 on a computer and don't have access to the internet on that computer. All the instructions that I've seen on how to install wine involve being connected to the internet, which I am not. So is there a way that I could just download the needed files on the computer which I am using now (which runs Vista) and just use my flash drive to send the files to the computer running Ubuntu?


You can the APT-OFFLINE! with that you can download and install any debian offline 
[http://ubuntuforums.org/showthread.php?t=12289](http://ubuntuforums.org/showthread.php?t=12289)

---

### Post by TAspr on 2011-05-20
Ou[QUOTE=jre6;10839467]Installing all of the dependencies is not needed. You can just download these to install wine:
cabextract : [http://packages.ubuntu.com/natty/cabextract](http://packages.ubuntu.com/natty/cabextract)
gettext : [http://packages.ubuntu.com/natty/gettext](http://packages.ubuntu.com/natty/gettext)
libmpg123-0 : [http://packages.ubuntu.com/natty/libmpg123-0](http://packages.ubuntu.com/natty/libmpg123-0)
libopenal1 : [http://packages.ubuntu.com/natty/libopenal1](http://packages.ubuntu.com/natty/libopenal1)
wine1.3 : [http://packages.ubuntu.com/natty/wine1.3]("http://packages.ubuntu.com/natty/wine")

Transfer these packages to your home folder, and type in a terminal:
```

cd ~
sudo dpkg -i cabextract*.deb gettext*.deb libmpg123-0*.deb libopenal1*.deb wine1.3*.deb

```And wine will be installed[/CODE]

You are amazing!

---

### Post by Dayyan on 2013-05-03
These links are not opening giving error please tell me,
[COLOR=#000000]I've recently installed Ubuntu 12.10 on a computer and don't have access to the internet on that computer. All the instructions that I've seen on how to install wine involve being connected to the internet, which I am not. So is there a way that I could just download the needed files on the computer which I am using now (which runs xp) and just use my flash drive to send the files to the computer running Ubuntu?

[/COLOR]

---

### Post by matt_symes on 2013-05-03
This is an old thread so **Thread Closed**.

@Dyyan - please start a new thread with your query and reference this thread if you think it will give context.

A lot can change in a small period of time in the software world.

---

