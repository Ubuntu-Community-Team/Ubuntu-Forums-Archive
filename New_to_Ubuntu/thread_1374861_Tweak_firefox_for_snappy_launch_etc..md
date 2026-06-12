---
title: "Tweak firefox for snappy launch etc."
date: 2010-01-07
forum: New to Ubuntu
---

### Post by mvalviar on 2010-01-07
Is there a way to tweak firefox so that it launch faster? I launch opera seconds after I launch firefox and opera's window still shows up faster than firefox. The same holds true even in ms window$.

I shutdown ubuntu without closing firefox and it seems that firefox gets 'killed'. When I bring ubuntu up again and open firefox it shows my last open tabs instead of showing my homepage. I wish ubuntu would let firefox clean up before closing it entirely.

---

### Post by audiomick on 2010-01-07
hi.
Can't give you a definite answer, but you might find something here:
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by speedwell68 on 2010-01-07
Have you considered using Swiftfox?  It is an optimised release of Firefox.  You can get it here...

[http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by philinux on 2010-01-07
> **mvalviar said:**
> When I bring ubuntu up again and open firefox it shows my last open tabs instead of showing my homepage. 

Firefox toolbar
Edit>prefs>main

Simples

Having lot of addons makes FF slow down on loading.

---

### Post by mvalviar on 2010-01-07
I see. I have download helper, delicious, and firebug add-ons. That must be the reason why FF launches slow.

How about ubuntu killing firefox on shutdown?

---

### Post by philinux on 2010-01-07
> **mvalviar said:**
> I see. I have download helper, delicious, and firebug add-ons. That must be the reason why FF launches slow.

How about ubuntu killing firefox on shutdown?

Shutdown kills all running processes.

---

### Post by Cheesemill on 2010-01-07
You should check out lovinglinux's excellent Firefox optimization thread:
 
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Sidewinder1 on 2010-01-07
"When I bring ubuntu up again and open firefox it shows my last open tabs instead of showing my homepage. I wish ubuntu would let firefox clean up before closing it entirely."

Somewhere in Firefox preferences is the choice for it to load Home page or "Previously Open Tabs", simply tick the one you want.
HTH,
Side

---

### Post by Mr. Fantastic on 2010-01-07
To the best of my knowledge, the only way to make it load up faster is to remove add-ons.  But if you're looking for a way to make it run faster once it is active, try the Fasterfox add on. I'm not sure if it works with 3.0 though.

---

### Post by mvalviar on 2010-01-08
> **Sidewinder1 said:**
> "When I bring ubuntu up again and open firefox it shows my last open tabs instead of showing my homepage. I wish ubuntu would let firefox clean up before closing it entirely."

Somewhere in Firefox preferences is the choice for it to load Home page or "Previously Open Tabs", simply tick the one you want.
HTH,
Side

I do have it set to "Show home page". However Firefox only shows my homepage on start up only when I close firefox before I shutdown. If I shutdown while firefox is still open then when I bring it up again it will show my previously open tabs/pages.

I've tried the ff:

1. Open a few tabs.

2. Close firefox. (it no longer shows the prompt to save tabs since I already answered no and "don't ask me again" before)

3. Launch firefox

Result: Firefox shows my homepage on start up.

1. Open a few tabs.

2. kill firefox (via kill pid)

3. Launch firefox.

Result: Firefox shows my previously opened tabs

I wish ubuntu would "close" firefox instead of "kill". I mean what's the point of having "Show my homepage" option on under preferences when you never get what you expect? Shouldn't they change the option to "Show my homepage (be sure to close firefox before shutting down for this to work)"?

---

### Post by John Bean on 2010-01-08
> **mvalviar said:**
> Is there a way to tweak firefox so that it launch faster?

Move the cache to a ramdisk. There are several ways to do this, but I found it simplest to type *about:config* into the address bar then find the preference name  *browser.cache.disk.parent_directory* - create it if necessary by right-clicking and selecting "new" - then set it to */dev/shm* or other ramdisk of your choosing.

Makes a huge difference.

---

### Post by Sir Jasper on 2010-01-08
Hi,

I am using FF v 3.0.16 which takes about 12 seconds to load, but although I have only 640 MB of RAM fortunately I never run short of RAM so I do not close FF except when I shut down at night.

My regards

---

