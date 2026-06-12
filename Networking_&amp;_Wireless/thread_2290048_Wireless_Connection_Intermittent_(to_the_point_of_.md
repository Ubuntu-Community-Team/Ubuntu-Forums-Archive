---
title: "Wireless Connection Intermittent (to the point of being unuseable)"
date: 2015-08-08
forum: Networking &amp; Wireless
---

### Post by johnnyboy on 2015-08-08
Hello!  This is an old hat that's been tossed around on here for a while, although I can find many, many posts relating to the same wireless card I cannot find one with respect to Ubuntu 15.04.

**The issue: Wifi signals are very, very weak (relative to Windows 10 on this same machine), drop out frequently. **

Specs: Hewlett-Packard "HP Notebook"
Realtek RTL8723BE Wireless Network Adapter <---- common theme here
Ubuntu 15.04

From reading previous posts and responses that are related I get the feeling this is an age old problem - the RTL8723BE chipsets do not play well with Linux machines (I had the same problem with Linux Mint before deciding to switch back to Ubuntu).  I'm a little worried that this is an issue that is unsolvable, and that I will just have to use a hard-wired ethernet cable if I want to use this machine with Linux.

A little more info: When I run "inxi -nx" command from the terminal, the response is often that the state of the card is "down".  If I try to force the card back up with "sudo ifconfig wlan0 up" there is no response.  When I run "sudo rfkill list all" everything is listed as unblocked.  Airplane mode is turned off.  I've tried a few suggestions relating to setting up configuration files to disable power management, but it doesn't seem to help.

If you have any suggestions, even something very similar to what I've tried, please toss them out to me - I'm pretty desperate at this point and willing to try just about anything, even if it means wrecking my linux installation (it's very fresh, so I won't lose anything really if that's the case... but if linux is unable to run wifi on my laptop I'll just have to stick with windows 10...the horror).

Any thoughts?  Thanks in advance!

---

### Post by weatherman2 on 2015-08-08
My recommendation would be to go back to Ubuntu 14.04 LTS, which will be supported until April 2019.  If you manage to get a solution to work for 15.04 (non-LTS), who is to say it will work after you must upgrade to 15.10 in January 2016?

Because there seem to be some good solutions for 14.04, like this one:

[http://ubuntuforums.org/showthread.php?t=2205497](http://ubuntuforums.org/showthread.php?t=2205497)

I'd probably go down that road - unless you have some overriding need for 15.04.

---

### Post by johnnyboy on 2015-08-09
> **weatherman2 said:**
> My recommendation would be to go back to Ubuntu 14.04 LTS, which will be supported until April 2019.  If you manage to get a solution to work for 15.04 (non-LTS), who is to say it will work after you must upgrade to 15.10 in January 2016?

Because there seem to be some good solutions for 14.04, like this one:

[http://ubuntuforums.org/showthread.php?t=2205497](http://ubuntuforums.org/showthread.php?t=2205497)

I'd probably go down that road - unless you have some overriding need for 15.04.

I'm tempted to take up your suggestion simply because it's such a fresh start and at this point wiping (again) and installing a different linux (again) is pretty easy (I just switched from Linux Mint to Ubuntu this afternoon).  However, is it a pretty good guarantee I wouldn't have the exact same issue, again, that I've had on the last 2 distros I've tried?  I'm really wondering if I lost the hardware lottery and it just so happens that my particular wifi card is linux's shortcoming.  I don't know, I might give 14.04 a shot but I don't think I've got another attempt in me if it falls through again.

As for the link - thanks for providing that, I did try the section of code where you recompile the driver and it helped a bit for an hour or so (ran a bit faster than the old dial-ups, probably comparable to the old 256k cable modems) but it didn't feel quite like the cure-all

---

### Post by weatherman2 on 2015-08-09
Read through that entire thread.  There were other suggestions I think such as disabling power management or something to that effect.

I can't guarantee that 14.04 LTS will be an better.  But, can you guarantee whatever fixes you put in place now with 15.04 will work when you upgrade to 15.10 in January?  Do you really feel like going through this all over again every nine months?  (Or I suppose 15.10 or some future version may include a better/more stable driver that WILL fix it for real - who knows?  It's a roll of the dice.)

I prefer the LTS versions for the stability.  I may have to do some tweaks after the first install to get the hardware to work, but then I can forget it for about it for a few years.

---

### Post by johnnyboy on 2015-08-09
> **weatherman2 said:**
> Read through that entire thread.  There were other suggestions I think such as disabling power management or something to that effect.

I can't guarantee that 14.04 LTS will be an better.  But, can you guarantee whatever fixes you put in place now with 15.04 will work when you upgrade to 15.10 in January?  Do you really feel like going through this all over again every nine months?  (Or I suppose 15.10 or some future version may include a better/more stable driver that WILL fix it for real - who knows?  It's a roll of the dice.)

I prefer the LTS versions for the stability.  I may have to do some tweaks after the first install to get the hardware to work, but then I can forget it for about it for a few years.

I did do the power management disabling to little effect but regardless, I'm picking up what you're putting down and I think it's a better option.  It's not much trouble for me to do one last clean install, followed by a final hurrah to get my wifi working.  I'm doing it now, starting fresh with 14.04 and seeing how it treats me.  Thanks for the replies.

---

