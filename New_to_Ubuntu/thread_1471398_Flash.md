---
title: "Flash"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by G33k-N-Tr@!niNg on 2010-05-03
I recently kicked windows to the curb for Ubuntu 9.10.  I am taking a class that requires flash, so I installed it. While taking a test I had some drag and drop questions and some simlets that all use flash but would not work.  Is there anything else i need to do just short of using virtual box?

Thanks in advance!!

---

### Post by Scunnered on 2010-05-03
You can find in System > Administration > Synaptic the flashplugin installer which is for the 32 bit system.

You can also find directions for the 64 bit version via [http://ubuntuforums.org/showthread.php?t=1468743](http://ubuntuforums.org/showthread.php?t=1468743).  This worked for me.

Hope this assists

---

### Post by G33k-N-Tr@!niNg on 2010-05-03
I uninstalled the plugin I got from the software center and followed post #9 in the link you gave to me.  When I went to the site it told me that I needed flash player installed.... I am at a loss.

The plugin from software center will get me into the site and view the flash objects but can't interact. Any other advice?
:confused:

---

### Post by nhasian on 2010-05-03
G33k-N-Tr@!niNg,

you didnt mention whether you were using 32bit or 64bit ubuntu.  are you still using 9.10 or did you upgrade to 10.04 yet?

in firefox type the url:

```
about:plugins
```

see what software and what version you are using for flash.  mine says:

>     File: libflashplayer.so
    Version:     Shockwave Flash 10.0 r45

---

### Post by G33k-N-Tr@!niNg on 2010-05-03
I am running the 64 bit of 9.10 and chrome.  I tried the site in firefox and had the same issue below is the result of your code:

> Shockwave Flash

File name: npwrapper.libflashplayer.so
Shockwave Flash 10.0 r45
MIME Type	Description	Suffixes	Enabled
application/x-shockwave-flash	Shockwave Flash	swf	Yes
application/futuresplash	FutureSplash Player	spl	Yes


---

### Post by nhasian on 2010-05-04
ah there you go.  you are using the 32bit version of flash with ubuntu 64bit.  

uninstall all instances of flash from your computer.  make sure there is no libflashplayer.so anywhere on your hard disk and make sure when you restart firefox in about:plugins it has no entries for flash.

THEN you can proceed to download the 64 bit flash from adobe labs (not synaptic) 

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

after you extract it move the file with:

```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by G33k-N-Tr@!niNg on 2010-05-04
Thank you for all of your help!! the issue is resolved in Fire Fox..now just to get it fixed in google chrome...i can google that.  Thank you both again for all your help!!

---

### Post by xumuk37 on 2010-05-04
this should solve this problem for chrome too... just try to restart it...

---

### Post by 0004tom on 2010-05-04
I don't use google chrome, I use Chromium and I have flash installed to 

/usr/lib/chromium-browser/plugins

Is there a folder for google chrome in /usr/lib?

---

### Post by xumuk37 on 2010-05-04
no, chrome uses mozilla's plugins.

---

### Post by G33k-N-Tr@!niNg on 2010-05-04
xumuk37 is correct.  all I had to do was restart chrome.

---

