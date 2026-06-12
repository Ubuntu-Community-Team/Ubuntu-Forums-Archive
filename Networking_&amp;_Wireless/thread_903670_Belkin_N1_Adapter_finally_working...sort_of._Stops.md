---
title: "Belkin N1 Adapter finally working...sort of. Stops responding after opening a browser"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by MakingHeadway on 2008-08-28
I have a strange issue here (I'd like to thank a user named James for helping me get up and running; thanks again, friend). I finally got Ndiswrapper installed and, after having to re-purchase my network adapter to get the drivers from the disk, as there were absolutely none out there that worked, I was finally able to get online. My elation didn't last long, however, as shortly after downloading some packages and installing some mods I opened Firefox and found I was unable to navigate to any page.

I restarted, re-logged, re-everything several times. I can sudo apt-get all day long, but as soon as I start up a web browser my card stops responding and network-manager drops all networks from its list save the one I connect to -- which still shows a signal, but is obviously misleading as I can't even download packages at that point.

Another thing I've found is that my signal is extremely weak compared to when I'm running Vista -- I'm attributing this to the driver (Belkin N1 USB Adapter, if anyone has any insight on this please share), but is there anything I can do to improve both the signal and rectify this strange issue?

I'm trying to learn and do things on my own and only ask when I'm at my wits end, and I appreciate all the help that's been given thus far. Thanks a bunch.

---

### Post by james_vanb on 2008-08-29
Looks like my well wishes for wireless might have been a bit premature.  Hope at least that you are enjoying the pot-pies.

A couple of suggestions that might help you isolate the problem.  If you're router has security enabled, disable and see if that makes a difference.  Security settings sometimes have their own issues.

Install another browser either through Synaptic or command line, i.e.:

```
sudo apt-get install opera
```  

See if it's unique to firefox.  If Opera works, try re-installing firefox either through Synaptic or command:

```
sudo apt-get remove mozilla-firefox
sudo apt-get install mozilla-firefox
```

At least I think those are the commands.  When in doubt, open Synaptic and see how firefox (or any other program for that matter) is listed and replace as appropriate.

As for the weak signal - I agree that it is either driver and/or ndiswrapper related.  Search the ndiswrapper web-site for your driver.  Often times, it will list specifics for your driver installation including any pre-installed native drivers that may conflict and need to be blacklisted.

---

### Post by MakingHeadway on 2008-08-29
Thanks again James, I'll give all of these suggestions a try and post the results.

---

