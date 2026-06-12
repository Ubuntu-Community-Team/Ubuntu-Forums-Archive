---
title: "Help IDing &amp; installing external Wireless USB stick to get online?"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by at0micgirl on 2010-01-23
I probably could find the answer to this if I could ID my wireless card, but unfortunately Dell sucks royally, and I can't even view their technical details for this laptop (a Dell Inspiron 2200) b/c i'm using a Mac! (webpage actually says it won't display b/c i'm not using a version of windows) sad... :(

Anyhow, I've *just* wiped this HD, and installed Karmic Koala 9.10. Graphics are working great, but really hoping to get online soon. Wireless tab reports No Wireless Connections. 

I've been following the Pocket Guide to Ubuntu for install so far, but now I'm stuck. 

anyhow, all i've managed to gather from Dell is I've got a Chipset 7.2.2.1006, A09 (release 1/17/2000).

The USB stick that I plug into get wireless on our non-password-protected Linksys router is made by Logitech, and says 2.4Ghz. PIN # is 831120-2000. I google searched a bunch on this, and kept coming up with wireless mice. 

I can't download software onto the Dell b/c of this issue - can i download something on my mac and slip onto a USB drive? Will that even work without extra work?

Your help is much appreciated!!!
Carrie Anne

---

### Post by omarly on 2010-01-23
My experience is that you should be online to get the right updates. They will install the missing about hw aso.

I am not so experienced in mac, but in windows you can port your internet connection out of your ethernet connection, and I guess this is an option on mac too. then you only need a net-cable to do mashine to mashine connection.

I did an install on an acer? 10" once and checked the option for modem device, after a check on Hardware Drivers, with the result of missing the touch-pad, on next reboot. This made me confused and forgot about this, because I was doing extra installs; so if everything works after updates, be a bit sceptic about "strange"/unknown" devices showing up in the Hardware Device menu.

Hope you get it up and going soon!
and you got a little help/wiser from this

good times to come :)

---

### Post by at0micgirl on 2010-01-23
OK, thanks for the advice, but now I'm confused and would like to clarify...

so you're saying that i can attach an ethernet cable from my Mac Mini to my Dell Ubuntu laptop, and that I could connect online via that? :confused: really?

there must be something more to that... i imagine i'd need to change some settings on my mac for that to work, right?

and then you're saying once Ubuntu is online, I should be able to update directly... where exactly? ls there a built-in "Update Ubuntu" button? Or am I going to use Firefox and navigate to an Ubuntu page... (located where?)

Finally, what about if I get this done and my wireless card still isn't working?

I know there is software out there to ID it, can someone help me find that for Ubuntu?

Thanks!
Peace,
Carrie Anne

p.s. Normally I let typos go, but I *really* got confused trying to read the word "mashine". (which even out loud is MA-SHYNE). It's "machine"! :) thanks!

---

### Post by at0micgirl on 2010-01-24
Bump! Please, I still need help! Anyone???

---

### Post by brog45 on 2010-01-25
So you have a wifi card and a wifi USB stick?  What is the model of the card?  

Also, run System > Administration > Log File Viewer and use it to look at /var/log/syslog when you plug in the card (or stick).  Sometimes it recognizes the card's chipset but doesn't have a working driver for it or it picks the wrong driver.  When that happens, you can use the information the kernel logs to help find the right driver.

I also do not have any significant experience with Macs, but maybe it has an option to share your internet connection.  I think I have seen this called "connection sharing" and "connection bridging."  If you're going to connect one laptop to the other, though, you should either connect them both to a hub or use a cross-over cable.

---

### Post by Pablonius Monk on 2010-01-25
[INDENT]The USB stick that I plug into get wireless on our non-password-protected Linksys router is made by Logitech, and says 2.4Ghz. PIN # is 831120-2000. I google searched a bunch on this, and kept coming up with wireless mice.[/INDENT]

Double-check your USB wifi stick. Is it possible that your USB stick actually is a wireless mouse receiver? I've done that before. You probably also want to connect the laptop first & foremost to ethernet and get updates (>>System/Administration/Update Manager)

---

### Post by brog45 on 2010-01-26
If I am mistaken and the card is an internal card, run ```
lspci
``` (to list PCI devices).  If that is the case, it looks like ndiswrapper is the way to go.  

Here are some links I have found that look helpful:
[http://tuxmobil.org/dell.html](http://tuxmobil.org/dell.html)

Especially the last post in this thread:
[http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/my-success-dell-inspiron-2200-lfs.-364781](http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/my-success-dell-inspiron-2200-lfs.-364781)

---

### Post by at0micgirl on 2010-02-05
Hey thank you everybody! I am happy to report that **I am writing this reply using wireless on Ubuntu! **YEA!!!

knowing the lspci was very helpful, but i was unsuccessful at getting the ethernet cable to work off my mac, so... i finally met someone here in the city who has used Ubuntu, and let me plug my laptop straight into his cable connection off of Windows 7, which got us online.

and YES, that damned little usb stick* is* just a wireless mouse antenna which really makes me mad, b/c i don't use one and constantly have been plugging that thing in and not trying to lose it when i travel. ah! how funny! :p

**downloading the updates for Ubuntu is what really did the trick**, but we forgot to do that til the end(!), so I learned a few things along the way.

we went through using ndiswrapper, modprobe, etc. so i became a little more familiar (and refreshed my brain a bit) on loading drivers from the command line interface. also learned of the existence of echo and tee, and concept of blacklisting drivers so they don't interfere.

**so far, many things are working well** (and so much faster than XP on this little machine!).
 
I know of two small issues so far *(if you want to know: playing DVD's using OpenMovie OR VLCPlayer are not working; *AND* full screen video using Flash "flashes" weird dropout boxes over the video, but normal res is fine)*, but I'm going to post these issues separately after I try a bit more research. 

I thank you all for your help and your thoughtfulness to this issue!

Peace,
Carrie Anne

---

### Post by brog45 on 2010-02-05
Glad to hear you got it working!  Is ndiswrapper still in place?  Or does it work with vanilla Ubuntu 9.10 after installing updates?

---

### Post by omarly on 2010-02-05
> **at0micgirl said:**
> Hey thank you everybody! I am happy to report that **I am writing this reply using wireless on Ubuntu! **YEA!!!

knowing the lspci was very helpful, but i was unsuccessful at getting the ethernet cable to work off my mac, so... i finally met someone here in the city who has used Ubuntu, and let me plug my laptop straight into his cable connection off of Windows 7, which got us online.

and YES, that damned little usb stick* is* just a wireless mouse antenna which really makes me mad, b/c i don't use one and constantly have been plugging that thing in and not trying to lose it when i travel. ah! how funny! :p

**downloading the updates for Ubuntu is what really did the trick**, but we forgot to do that til the end(!), so I learned a few things along the way.

we went through using ndiswrapper, modprobe, etc. so i became a little more familiar (and refreshed my brain a bit) on loading drivers from the command line interface. also learned of the existence of echo and tee, and concept of blacklisting drivers so they don't interfere.

**so far, many things are working well** (and so much faster than XP on this little machine!).
 
I know of two small issues so far *(if you want to know: playing DVD's using OpenMovie OR VLCPlayer are not working; *AND* full screen video using Flash "flashes" weird dropout boxes over the video, but normal res is fine)*, but I'm going to post these issues separately after I try a bit more research. 

I thank you all for your help and your thoughtfulness to this issue!

Peace,
Carrie Anne
updates is the trick ;) at0micgirl

u'll find new horizons

---

### Post by Pablonius Monk on 2010-02-07
That's good to hear, Carrie Anne. As for playing your DVDs, be sure to follow these steps: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

DVDs should play fine on VLC Player after the restricted formats stuff has been installed.

As for Flash bugginess, I hear you. It's buggy...particularly on computers with slower processors.

---

### Post by at0micgirl on 2010-02-09
> **brog45 said:**
> Glad to hear you got it working!  Is ndiswrapper still in place?  Or does it work with vanilla Ubuntu 9.10 after installing updates?

Hey Brian,

I hate to admit this, but I have no clue! How do I know? All I know is wi-fi worked after 42+ updates were installed. :redface:

Thanks for everything!
Carrie Anne

---

