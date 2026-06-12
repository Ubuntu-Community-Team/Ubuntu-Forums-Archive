---
title: "wireless connection before login"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by ivia77 on 2008-09-11
Is it possible to get a WPA wireless connection without logging in first?

I've tried playing around with /etc/network/interfaces by copying and pasting from whatever i can find on the interweb, but don't have the knowledge needed to get any results. Specifically, I'm trying to get an eeePC 901 to connect to my desktop using XDMCP, both are running Hardy. 

Any ideas or pointers will be greatly appreciated.

---

### Post by Another Monkey on 2009-01-31
I just fixed the exact same thing.

Messing with "/etc/network/interfaces" did not work for me at all.  I had to use NetworkManager.

You need "Connect Automatically" and "System setting" both checked for the wireless connection in NetworkManager.  However, NetworkManager seems to have a couple of bugs (what follows is just based on my experience and might not be 100% accurate).

[LIST=1]
[*]You can only have one adapter set as "System setting" at one time.
[*]Just clicking "System Setting" has no effect.
[/LIST]

What you need to do is check/uncheck "Connect Automatically" as well.  So, for example:
[LIST=1]
[*]Edit properties for ethernet
[*]Uncheck "Connect Automatically"
[*]Uncheck "System setting"
[*]OK.
[*]Edit properties for ethernet
[*]Check "Connect Automatically"
[*]Uncheck "System setting" again if you need to
[*]OK
[*]Edit properties for wireless
[*]Uncheck "Connect Automatically"
[*]Check "System setting"
[*]OK
[*]Edit properties for wireless
[*]Check "Connect Automatically"
[*]Check "System setting" again if needed
[*]OK
[/LIST]

You might need to repeat these steps in various orders before the changes actually take effect.  One of two things will happen when the changes take effect:
[LIST=1]
[*]NetworkManager will demand authentication
[*]The entry for the particular adapter will appear to "flash" briefly.
[/LIST]

Once you have "Connect Automatically" and "System setting" both checked, that adapter will be available before login.

The next problem is getting XDMCP to work over wireless - it's not doing so for me.

---

### Post by rydell on 2009-04-06
Another Monkey: Thanks for the tip! It worked, but only after I disabled the wireless connection: only then did it allow me to check the "System Setting" checkbox. After that - sweet auto connect to wifi without logging in!

:-)
Amir

---

