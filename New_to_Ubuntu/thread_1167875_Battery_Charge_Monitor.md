---
title: "Battery Charge Monitor"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by don_diego on 2009-05-23
When I fiirst installed Ubuntu 9.40 on this laptop about 3 weeks ago, I had an icon for the battery charge monitor on the top panel. Somehow, when I was setting up the wi-fi PMCIA card for Internet access, the battery monitor disappered from the panel but after putting it back, it no longer montors the battery. All it says is "System is running on battery power - 0 minutes (0%) remaining" - even when the laptop is is running on AC power. 

TIA for any help.

---

### Post by zhhansen on 2009-05-23
I had this problem once before, and eventually I just restore my ubuntu panels, so they could go back to default, which fixed the problem with the battery monitor.

I'm not sure if this will fix your problem, but let's hope so.

Open a terminal and type ```
gconftool-2 --shutdown

rm -rf ~/.gconf/apps/panel

pkill gnome-panel 
```I hope that helps!

zhhansen

---

### Post by don_diego on 2009-05-23
Unfortunately, it didn't. 

Thanks for trying to help.

---

### Post by mcduck on 2009-05-23
> **don_diego said:**
> When I fiirst installed Ubuntu 9.40 on this laptop about 3 weeks ago, I had an icon for the battery charge monitor on the top panel. Somehow, when I was setting up the wi-fi PMCIA card for Internet access, the battery monitor disappered from the panel but after putting it back, it no longer montors the battery. All it says is "System is running on battery power - 0 minutes (0%) remaining" - even when the laptop is is running on AC power. 

TIA for any help.

By default Ubuntu doesn't use the "Battery Charge Monitor"-applet. The default battery icon is created by Gnome's power manager, and sits inside the Notification Area-applet.

I bet you removed the Notification Area from your panel, and ten tried getting the battery icon back by adding Battery Charge Monitor to the panel.. Instead of that make sure you have Notification Area-applet in your panel, and if the icon still doesn't show inside it then go to System/Preferences/Power management, and on General-tab make sure the icon is enabled.

---

### Post by don_diego on 2009-05-23
> **mcduck said:**
> By default Ubuntu doesn't use the "Battery Charge Monitor"-applet. The default battery icon is created by Gnome's power manager, and sits inside the Notification Area-applet.

I bet you removed the Notification Area from your panel, and ten tried getting the battery icon back by adding Battery Charge Monitor to the panel.. Instead of that make sure you have Notification Area-applet in your panel, and if the icon still doesn't show inside it then go to System/Preferences/Power management, and on General-tab make sure the icon is enabled.

Mcduck, I did as you suggested and now have a new icon on the panel (next to the network icon) that says "Computer running on AC power" ---- even when the AC power is NOT connected.  ????

I might also mention that, while in power management, there was no "on Battery" tab. only AC power and General. I feel that somehow the system doesn't know this is a laptop.

Needless to say this newbie is totally stumped.

---

### Post by mcduck on 2009-05-23
In that case something you did when setting up the PCMCIA card must have broken the power management. If you can post the steps you did to do that here perhaps somebody will be able to spot what went wrong and how to fix it..

---

### Post by don_diego on 2009-05-23
> **mcduck said:**
> In that case something you did when setting up the PCMCIA card must have broken the power management. If you can post the steps you did to do that here perhaps somebody will be able to spot what went wrong and how to fix it..

Wow, that's a tall order. You want a 78-year old newbie to remember the steps he took to install his PCMCIA card a couple of weeks ago? Im afraid I can't. 

Would it be possible to check if power management is indeed broken without the need for  input from my obviously broken memory?

---

### Post by mcduck on 2009-05-23
> **don_diego said:**
> Wow, that's a tall order. You want a 78-year old newbie to remember the steps he took to install his PCMCIA card a couple of weeks ago? Im afraid I can't. 

Would it be possible to check if power management is indeed broken without the need for  input from my obviously broken memory?

Sorry, that's the only way how I could help figuring out what's broken. But yeah, I kind of guessed that unless you followed some specific guide to get the card working you really wouldn't be able to tell how you did it. I'm sure I wouldn't be able to do that. :)

I suppose your only hope is to wait if somebody with better knowledge about how power management is handled in current Ubuntu version sees this thread. The commands I've used to running don't even seem to be installed in 9.04.

---

### Post by don_diego on 2009-05-23
> **mcduck said:**
> Sorry, that's the only way how I could help figuring out what's broken. But yeah, I kind of guessed that unless you followed some specific guide to get the card working you really wouldn't be able to tell how you did it. I'm sure I wouldn't be able to do that. :)

I suppose your only hope is to wait if somebody with better knowledge about how power management is handled in current Ubuntu version sees this thread. The commands I've used to running don't even seem to be installed in 9.04.

I guess you are right and all I can do is hope and wait for somebody to chime in. 

Thanks much for trying to help with this issue.

---

### Post by don_diego on 2009-05-25
My apologies - I had the battery monitor when I first installed 8.10. It was after I upgraded to 9.04 when it disappeared. Have reinstalled 8.10 and everything is well again. 

I guess one can learn the basics of Ubuntu from an earlier version, too.

---

### Post by mprince on 2009-05-25
> **don_diego said:**
> I guess one can learn the basics of Ubuntu from an earlier version, too.

Eaxctly. You don't always need to have the latest and greatest version of ubuntu. If a earlier version works well for you, then you can stick with it until it is no longer being supported.

New releases fix some problems, but also introduce new ones.

---

