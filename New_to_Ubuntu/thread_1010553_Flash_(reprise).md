---
title: "Flash (reprise)"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by dinostabOMG on 2008-12-13
I done got myself a Dell Vostro 1500, and installed Hardy amd64 thereon. I got flashplugin-nonfree from the repositories, and it didn't work. Sites requiring Flash still tell me I need to install it.

I know that there are tons of HOWTOs about how to get Flash working. Most of them are out of date and many of them involve very different approaches with different degrees of convolution. I know those HOWTOs are supposed to make things easy but they are just compounding the confusion for me. Especially when one method doesn't work and then I have to worry about whether the failed installation is interfering with subsequent attempts.

One solution was very simple and worked for me on another computer. I downloaded the official .deb from Adobe. Double clicking it gives the "wrong architecture" error. I remember doing something pretty easy, maybe some switch using this .deb on the command line. But I don't remember exactly what this was - can anyone help?

---

### Post by bsharp on 2008-12-13
I don't know if this will work but the switch was probably:
```
sudo dpkg --force-architecture -i whatever.deb
```

A better way is to download the native x86_64 Flash 10 beta(remove flashplugin-nonfree first!):
[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)

and extract it into /usr/lib/mozilla/plugins

Restart firefox and it should work.

---

### Post by dinostabOMG on 2008-12-13
Thanks for this response. I looked in /usr/lib/mozilla/plugins and there was already a file called npwrapper.libflashplayer.so

I unpacked the file you linked to, and put it in the plugins folder. No go. I tried removing the one that was already there, but that didn't work either (I put it back after). Any ideas? Any way I can capture some errors or something?

By the way, I tried the force architecture switch on the i386 .deb, that hasn't worked this time either.

Hrmmm.

---

### Post by bsharp on 2008-12-13
That's what I get for trying to 'just remember'. Looking back, I found the old thread where I got it working:
[http://ubuntuforums.org/showthread.php?t=989906](http://ubuntuforums.org/showthread.php?t=989906)

Do these to install:
```
mkdir /usr/local/lib/flashplugin
mv flash-mozilla.so /usr/local/lib/flashplugin
cd /etc/alternatives
mv flash-mozilla.so flash-mozilla.so-old
ln -s /usr/local/lib/flashplugin/libflashplayer.so flash-mozilla.so
```

---

### Post by dinostabOMG on 2008-12-14
Hm, this code appears to reference flash-mozilla.so ? I don't seem to have this, where should it be? The archive contains only libflashplayer.so. Am I missing something?

---

### Post by Berethorn on 2008-12-14
This worked for me just now (I was surprised it was so easy) - you may have tried it already, but:

[http://ubuntuforums.org/showthread.php?t=772490&highlight=flash+hardy](http://ubuntuforums.org/showthread.php?t=772490&highlight=flash+hardy)

Scroll down to the Flash 10 Script under Hardy Heron, download the script and follow the steps. Of course, remove any other versions of flash you may have installed already. Good luck!

---

