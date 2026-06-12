---
title: "Hardy &amp; Linksys Problems"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by CoCoKnots on 2009-02-10
Interesting issue: I'm running Hardy on my Sony VAIO Notebook with an Intel Wireless interface using a Linksys Wireless system. The first time I found a problem was when I noticed I had lost my wireless. I needed to do some work and made a trip to the local library & found the wireless worked, (to my surprise). I went home & the Linksys wireless systen still did not work. 

I also have a desktop using a wired LAN cable directly to the router & works fine. The folks at Linksys walked me through a setup procedure to re-set the router & my notebook worked fine again... Until I returned to the library to do some more research. When I got home, the wireless quit working again. When I tried the reset routine as I had once before, it did not work. *This is where it gets real interesting...* When I made another trip to the library, the wireless began working fine again and continued to work when I returned home. It's like a ghost which comes & goes at will, or possibly some odd issue which 'toggles' the wireless specific with Linkysy. I never have an issue with the wireless service at the library. Any Ideas ? Is this something which should be reported as a 'Bug'.

---

### Post by ugm6hr on 2009-02-10
Very bizarre.

It's always difficult to get to the bottom of problems you can't reproduce reliably.

Are you sure it's not specific websites that are the problem?

And when the home network doesn't work, can you get an IP address, or does it not connect at all?

---

### Post by CoCoKnots on 2009-02-10
> **ugm6hr said:**
> Very bizarre.

It's always difficult to get to the bottom of problems you can't reproduce reliably.

Are you sure it's not specific websites that are the problem?

And when the home network doesn't work, can you get an IP address, or does it not connect at all?

It's not web site wireless... I do not have wireless at all. (Unable to get on).

The only way I can get an IP address is to connect via cable.

Strange eh ?

---

### Post by ugm6hr on 2009-02-10
Do you have any other wifi-enabled computers?

Perhaps this is a hardware fault with your home router.

I have an old wifi router that only works wired now, although I never had intermittent problems with it first.

---

### Post by CoCoKnots on 2009-02-10
> **ugm6hr said:**
> Do you have any other wifi-enabled computers?

Perhaps this is a hardware fault with your home router.

I have an old wifi router that only works wired now, although I never had intermittent problems with it first.

That thought crossed my mind. However, I'm using the Linksys wireless at home as I type this & is working fine. It appears that when it decides to 'malfunction' again, I will most likely be able to take it to the local library again to re-activate what ever needs to be triggered, bring it home again for another 500 miles or when ever it dies... then (hopefully) repeat.

---

### Post by jimv on 2009-02-10
What model is the router?

---

### Post by niteshifter on 2009-02-10
Hi,

Both of those wireless access points (home and library) wouldn't happen to have the same SSID (human readable name) of linksys would they?

If not, nevermind :)

If so, change your home router's name to something different. Then use the GNOME configuration tool (gconf-editor in Terminal) to remove the existing wireless network named linksys info:
Start gconf-editor.
Click the triangle beside system in the left pane to expand it.
Click the triangle beside networking to expand it.
Click the triangle beside wireless to expand it.
Click the triangle beside networks to expand it.

Now you should see under networks "linksys". Click on it and settings for that network appear in the left pane. On each item in the right pane, right click on the item and and left click on Unset Key.

Quit the configuration editor.

Now setup for each wireless access and all should be good.

---

