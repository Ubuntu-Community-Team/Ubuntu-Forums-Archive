---
title: "Adobe flash issues"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by blairm on 2010-02-23
Hi,

Since doing a clean install of Karmic my mouse has been unresponsive in the calendar portion of Google Analytics, used to select date ranges etc; a right click on the calendar shows it's Adobe Flash 10, and clicking on that takes me to an Adobe site that says I have version 10.0.45.2 installed.

Oddly enough, Analytics worked previously when I upgraded from Jaunty to Karmic, and all other parts of the site seem okay.

Anyone have any ideas on how I might fix this? Happy to provide more info but not entirely sure what info I should be providing...

Blair

---

### Post by thecliff on 2010-02-23
Are you running a 64 bit machine?  If so, you'll have to upgrade Flash to the 64 bit addition.

---

### Post by tom.swartz07 on 2010-02-23
> **thecliff said:**
> Are you running a 64 bit machine?  If so, you'll have to upgrade Flash to the 64 bit addition.

Theres a link in my sig if you need x64 flash

---

### Post by blairm on 2010-02-23
Hi,

Yes, it is 64-bit; should have thought of that. Pretty sure I removed all existing flash components (for some reason couldn't run the script in the signature above - probably my own incompetence).
Instead I used a series of commands in terminal based on the script and checked in synaptic; but still no joy.
Interestingly, YouTube works fine; it's just the Google site I've struck issues with so far.

About:plugins in Firefox provides the following under flash:

Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r45


application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Any further ideas would be appreciated.

Blair 

PS: On the bright side, things have certainly improved since last time I tried 64-bit (admittedly a long time ago); this is  only issue I've struck.

---

### Post by tom.swartz07 on 2010-02-24
> **blairm said:**
> Hi,

Yes, it is 64-bit; should have thought of that. Pretty sure I removed all existing flash components (for some reason couldn't run the script in the signature above - probably my own incompetence).
Instead I used a series of commands in terminal based on the script and checked in synaptic; but still no joy.
Interestingly, YouTube works fine; it's just the Google site I've struck issues with so far.

About:plugins in Firefox provides the following under flash:

Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r45


application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Any further ideas would be appreciated.

Blair 

PS: On the bright side, things have certainly improved since last time I tried 64-bit (admittedly a long time ago); this is  only issue I've struck.

Thats strange. it seems that youre still using the 32bit plugin with npwrapper.

Try going in to synaptic package manager and removing everything that says flash, including gnash and swfdec too. Then try the method described in my post again. Once you get rid of everything, its not too hard to put the new ones in the right spot- its just trying to hunt down the lone offender thats giving problems. 


Also, if youre using google chrome, you could also plop a copy of the plugin in
```
~/.config/google-chrome/Plugins/
``` (you might need to make the folder) and Chrome will load the plugins from there.

---

### Post by sandyd on 2010-02-24
see sig.
click the "remove flash" button first.

---

