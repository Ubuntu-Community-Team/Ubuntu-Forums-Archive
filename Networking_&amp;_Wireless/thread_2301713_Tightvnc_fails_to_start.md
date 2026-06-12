---
title: "Tightvnc fails to start"
date: 2015-11-04
forum: Networking &amp; Wireless
---

### Post by xendistar2 on 2015-11-04
I have installed ubuntu server with lubuntu desktop. I have also installed tightvncserver, but when I try to start the server with the following command

vncserver -geometery 1024x768 -depth 24:1

I get the following error

Couldn't start Xtightvnc; trying default font path.
Please set correct fontPath in the vncserver script.
Couldn't start Xtightvnc process

I have looked at the xstartup script in my .vnc folder but there is no font path listed and I am not sure what to use (a google search gave a myriad of variations), can anybody point me to the correct way to enter the font path please.

Tim

---

### Post by QIII on 2015-11-04
First, try removing the ":1"

-depth 24

I don't know if that was a C&P error, but you misspelled geometry.

This should be what you are left with:

```
vncserver -geometry 1024x768 -depth 24
```

---

### Post by xendistar2 on 2015-11-04
Cheers QIII, think I need to and get my eyes tested, now up and working.

For my next question, is there a way to start VNC on start up without the need to run the command from the cli?

---

### Post by QIII on 2015-11-04
You can do that.

But a word of advice:  Make sure you only allow VNC over SSH or some other secure channel.  One of the most common elements discovered when answering "Have I been hacked?" questions is the use of remote desktop software without good security.  Set up VNC to ONLY work over a secure channel -- even inside your home network.

I'm on my cell right now, so I can't be detailed.

How you do this depends on your flavor/DE, but you can create a script to do this and put that in your startup scripts or put that command in your startup commands.  (Hopefully someone will come along shortly and flesh that out for you!)

I reiterate:  **Secure VNC if you use it**.  Don't use it "in the open."

---

