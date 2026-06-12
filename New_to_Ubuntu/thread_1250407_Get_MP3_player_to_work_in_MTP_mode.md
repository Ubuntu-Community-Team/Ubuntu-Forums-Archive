---
title: "Get MP3 player to work in MTP mode?"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by aharown07 on 2009-08-26
I've got a Creative Zen... not one of the older Zen-something models but the one they just call Zen. 
Looks to me like it has no option to run in msc mode.
When I plug it in (Jaunty), It shows up in Rhythm Box and Banshee, but doesn't show up as a drive anywhere.
And its contents don't show. Banshee shows a couple GB of "other" on the device but no "audio."

I've read in a few places that there is a newer [b]libmtp[/] that can be manually compiled into something or other and this makes a number of newer devices work properly. However, I'm nervous about this compile since I have no clue what all the commands mean (and that usually means that when I attempt it, things will happen that I don't know whether matter or not... and stuff gets really messy)

Anyway, here is one version of the instructions (after downloading latest libmtp from SourceForge). Maybe somebody can fill in missing info here and advise on What To Avoid before I attempt this?  
(I'm assuming the code lines here are entered verbatim in the terminal... am I right?)
[INDENT]```
./configure
make
sudo make install
```
By default, this installs:
:/usr/local/lib$ ls -l
-rw-r–r– 1 root root  839976 2009-05-04 18:46 libmtp.a
-rwxr-xr-x 1 root root     805 2009-05-04 18:46 libmtp.la
lrwxrwxrwx 1 root root      15 2009-05-04 18:46 libmtp.so -> libmtp.so.8.2.1
lrwxrwxrwx 1 root root      15 2009-05-04 18:46 libmtp.so.8 -> libmtp.so.8.2.1
the libmtps that come in Jaunty are in /usr/lib:
/usr/lib/libmtp.so.8
/usr/lib/libmtp.so.8.0.0


back these files up in some place in your home:
Remove those in /usr/lib and soft link to new ones:
If you are still in /usr/lib
```

ln -s /usr/local/lib/libmtp.so.8.2.1 libmtp.so.8
ln -s /usr/local/lib/libmtp.so.8.2.1 libmtp.so.8.0.0
```
Of course, you need to be root for that.
[/INDENT]I also have no idea what "soft link to new ones" means!

---

### Post by oldos2er on 2009-08-26
Maybe this will help: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by zombiepig on 2009-08-27
There's an better way to compile libmtp for ubuntu. But you might not need this, first, try downloading a pre-compiled version from 
[http://packages.ubuntu.com/en/karmic/i386/libmtp8/download](http://packages.ubuntu.com/en/karmic/i386/libmtp8/download)
It's not quite the latest version (1.0.0 was released a short while ago), but it should be enough for your zen player, and if it works, will save you a lot of work!

Let me know if you don't have any luck with this, and I'll post instructions for compiling the latest version. :P

---

### Post by aharown07 on 2009-08-28
> **zombiepig said:**
> There's an better way to compile libmtp for ubuntu. But you might not need this, first, try downloading a pre-compiled version from 
[http://packages.ubuntu.com/en/karmic/i386/libmtp8/download](http://packages.ubuntu.com/en/karmic/i386/libmtp8/download)
It's not quite the latest version (1.0.0 was released a short while ago), but it should be enough for your zen player, and if it works, will save you a lot of work!

Let me know if you don't have any luck with this, and I'll post instructions for compiling the latest version. :P 
Thanks. I installed libmtp8 1.0.0 ...  but now the Zen appears on the desktop like it should but *doesn't* show up in Banshee or Rhythmbox. (It was doing the opposite before). At least now, though, I can see the contents and stuff like a drive. It's like it's in MSC mode now, which I didn't think it could do.

Edit: OK, that was weird. Now it's back to the old behavior... no "mounted" icon on the desktop but it shows up in Banshee... but it's not properly displaying the contents.

---

### Post by aharown07 on 2009-09-04
> **zombiepig said:**
> There's an better way to compile libmtp for ubuntu. But you might not need this, first, try downloading a pre-compiled version from 
[http://packages.ubuntu.com/en/karmic/i386/libmtp8/download](http://packages.ubuntu.com/en/karmic/i386/libmtp8/download)
It's not quite the latest version (1.0.0 was released a short while ago), but it should be enough for your zen player, and if it works, will save you a lot of work!

Let me know if you don't have any luck with this, and I'll post instructions for compiling the latest version. :P

I'd like to give that compile a try. Can you detail for me?

---

### Post by zombiepig on 2009-09-04
> **aharown07 said:**
> Thanks. I installed libmtp8 1.0.0 ...  but now the Zen appears on the desktop like it should but *doesn't* show up in Banshee or Rhythmbox. (It was doing the opposite before). At least now, though, I can see the contents and stuff like a drive. It's like it's in MSC mode now, which I didn't think it could do.

Edit: OK, that was weird. Now it's back to the old behavior... no "mounted" icon on the desktop but it shows up in Banshee... but it's not properly displaying the contents.

Did you install libmtp8 1.0.0 or the version from the karmic packages? Because the karmic version should work ok with banshee & rhythmbox, but there's a bug somewhere with the 1.0.0 version which stops banshee from seeing any songs on the device.

---

### Post by aharown07 on 2009-09-04
I guess I'm not sure now. There must be a command to see what ver. I have installed, eh? I don't know it though.

Edit: nevermind. The version I have installed is 0.3.7-3 of libmtp8

Do I need to reformat the device and reload the songs maybe? 
I actually can't find my Zen at the moment, but I have a Sansa Clip also and it's also not behaving right. Both Banshee and R.box *see* the device but don't see the contents.

---

### Post by bryncoles on 2009-09-04
If you find the Zen, have you tried using gnomad or kzenexplorer with it? They're both in synaptic. It still wont mount as a drive, but you should be able to manipulate its contents...

---

