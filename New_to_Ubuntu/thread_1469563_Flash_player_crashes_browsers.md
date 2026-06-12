---
title: "Flash player crashes browsers"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by Experimental on 2010-05-02
Flash player crashes every browser that i try . A web page that 3-4 swf's totally ruins my day. I use the latest version of flash player . What can I do about it ?

---

### Post by llamabr on 2010-05-02
which flash player?  and how did you install it?  from the web page, or the repositories?

---

### Post by madjr on 2010-05-02
you can give us some more info to diagnose the problem

-hardware specs (memory, processor, video card, etc)
-ubuntu version (32 or 64bit?)
-system temperature when it crashes

happened with older versions of ubuntu or flash?

---

### Post by wojox on 2010-05-02
Download [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433") .

---

### Post by Experimental on 2010-05-02
I used both carmic coala and lucid lynx . I have Core 2Duo 2.8Ghz 2 gb ddr2 1066mhz ram using 32-bit ubuntu . I downloaded flash player 10.xxxx from adobe's web site

---

### Post by llamabr on 2010-05-02
I install by doing:

```
sudo apt-get install flashplugin-installer
```

I don't know if it installs something different.  Also, do:

sudo apt-get remove gnash mozilla-plugin-gnash

---

### Post by Experimental on 2010-05-02
nope still freezes some times . It's totally random

---

### Post by zenturion on 2010-05-04
> **llamabr said:**
> which flash player?  and how did you install it?  from the web page, or the repositories?
Go to [http://get.adobe.com/uk/reader/enterprise/](http://get.adobe.com/uk/reader/enterprise/)
and select OS/ linux  x-86 (.deb) .this theeasiest way .for ubuntu 10.04 . and works.

---

### Post by zenturion on 2010-05-04
> **zenturion said:**
> Go to [http://get.adobe.com/uk/reader/enterprise/](http://get.adobe.com/uk/reader/enterprise/)
and select OS/ linux  x-86 (.deb) .this theeasiest way .for ubuntu 10.04 . and works.

Sorry the above mentioned is for adobe reader.
For flash player: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
and select deb ubuntu 8.04+ .

---

### Post by QIII on 2010-05-04
By any chance do you have swfdec installed? Like gnash, it conflicts with Flash.

---

### Post by Experimental on 2010-05-04
I uninstalled gnash . uninstalled flash player and downloaded it from adobe.com but it still freezes . 

[http://finans.mynet.com/](http://finans.mynet.com/)

try it yourself. Maybe not in the first time but it will freeze in maybe 4. -5. times

---

