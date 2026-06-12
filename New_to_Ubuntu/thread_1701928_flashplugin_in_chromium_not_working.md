---
title: "flashplugin in chromium not working"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by abraxas334 on 2011-03-07
Hi, 
I have looked around but people seem to be having trouble with flash in firefox but not chrome. I experience the opposite. I can't watch any youtube videos using chrome. Firefox will work for a while but eventually crash. All this happened after a recent upgrade. I was using a better version of chrome but even reverting to a stable one no difference. I have tried both adobe flash plugin as well as the one chrome comes with. I am a bit lost now any ideas how to fix this?

Shockwave Flash (2 files)
Shockwave Flash 10.2 r152
Name:	Shockwave Flash
Description:	Shockwave Flash 10.2 r152
Version:	
Priority:	0
Location:	/usr/lib/chromium-browser/plugins/libflashplayer.so
 	(Disabled) Enable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Name:	Shockwave Flash
Description:	Shockwave Flash 10.2 r152
Version:	
Priority:	1
Location:	/usr/lib/adobe-flashplugin/libflashplayer.so
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl

what I use in chrome. 
My chrome version installed: 9.0.597.107 what ever that means.
firefox version: 3.6.14

---

### Post by josephmills on 2011-03-07
have you tryed flash aid? 
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by abraxas334 on 2011-03-07
That won't work for chrome! My flash in firefox is working fine! But chrome is my default browser...

---

### Post by abraxas334 on 2011-03-07
Here is the crash report I get every time:

---

### Post by runeh76 on 2011-03-07
Hi

Goto package manager and search **flash**
Remove everything flash what is installed, close it and install from terminal:

```
sudo apt-get install gsfonts gsfonts-x11 flashplugin-nonfree
```

---

### Post by BrandonAElam on 2011-03-07
I was having similar issues. I solved them by clearing out all my cookies, then doing this:

Click that wrench on the right.
Then Preferences->Under The Hood->Content Settings->Exceptions
Click Add... and type in [www.youtube.com](www.youtube.com) and select block.

Definitely worked for me. Hope it works for you too.

---

### Post by ddumanis on 2011-03-09
Thanks Brandon! Worked great for me. 

This thread should probably be marked SOLVED now...  :D

---

