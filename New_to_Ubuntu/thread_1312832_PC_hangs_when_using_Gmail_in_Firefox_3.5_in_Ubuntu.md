---
title: "PC hangs when using Gmail in Firefox 3.5 in Ubuntu 9.10"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by linuxphoenix on 2009-11-03
Dear Friends,
                      Just started using Ubuntu 9.10 on my desktop. A strange problem has come up. I was replying to a mail in gmail using Firefox 3.5 and suddenly the cursor became a vertical line and the PC hung. I can move the cursor around with my mouse but can' click anything on my desktop / panel. Nothing helped and I had to reboot. The same thing happened several times, each time while I used gmail. I removed hibernating options in the Power Management but it didn't help. In all my years of using different flavours of linux, this has never happened. Is there some issue with Firefox 3.5 in Ubuntu 9.10?
Would appreciate any suggestions.
Thanks.

---

### Post by ukripper on 2009-11-03
> **linuxphoenix said:**
> Dear Friends,
                      Just started using Ubuntu 9.10 on my desktop. A strange problem has come up. I was replying to a mail in gmail using Firefox 3.5 and suddenly the cursor became a vertical line and the PC hung. I can move the cursor around with my mouse but can' click anything on my desktop / panel. Nothing helped and I had to reboot. The same thing happened several times, each time while I used gmail. I removed hibernating options in the Power Management but it didn't help. In all my years of using different flavours of linux, this has never happened. Is there some issue with Firefox 3.5 in Ubuntu 9.10?
Would appreciate any suggestions.
Thanks.

Problem seems to be more related towards the graphics card than firefox. Can you post output of the following commands after running in terminal:
```
sudo lspci
```
```
tail -n 30 /var/log/messages
```

---

### Post by Phil D. on 2009-11-03
ctrl+PrintScreen+k, to kill the current X-session
justmy2cents

---

### Post by linuxphoenix on 2009-11-04
This seems to have started after I installed the Flash plugin. Also it does not happen when I use the Opera browser or Galeon. I am not sure if this is a problem with Firefox 3.5 or the Flash Plug in or  Gmail or Ubuntu 9.10. Others seem to have had the same problem, as posted in these fora. 
A solution would be much appreciated.
Thanks

---

### Post by sldavid on 2009-11-04
linuxphoenix - 

Trying to help but unable to reproduce the problem - on FFox 3.5 with the Adobe Flash Plugin installed. I even tried setting Apperance Preferences > Visual Effects to None and Normal. No problems.

I noticed the Ubuntu Software Center has FFox 3.0 available. Maybe give it a try and see what happens.

---

### Post by linuxphoenix on 2009-11-05
The problem persisted on using Galeon and Opera. By now my wife was climbing the walls and telling me to remove Ubuntu! I tried removing the Flash plugin but failed first with Synaptic and then with the Terminal. Errors both time. Re-installed Ubuntu 9.10 after formatting the partition. Works fine now but I can't see anything that needs a Flash player!
My request to the Canonical team and the older users of this flavour of Linux: Please fix this issue with the Flash player. Sure to make a newbie run miles from Ubuntu. I have been using other flavours of Linux for six years, yet I was sorely tempted to turn my back on Ubuntu for good. Still hanging on in there!

---

### Post by lindix on 2009-11-05
> **linuxphoenix said:**
> The problem persisted on using Galeon and Opera. By now my wife was climbing the walls and telling me to remove Ubuntu! I tried removing the Flash plugin but failed first with Synaptic and then with the Terminal. Errors both time. Re-installed Ubuntu 9.10 after formatting the partition. Works fine now but I can't see anything that needs a Flash player!
My request to the Canonical team and the older users of this flavour of Linux: Please fix this issue with the Flash player. Sure to make a newbie run miles from Ubuntu. I have been using other flavours of Linux for six years, yet I was sorely tempted to turn my back on Ubuntu for good. Still hanging on in there!

It’s the same old story. A new Ubuntu release, a new series of pain and frustration.

---

### Post by ukripper on 2009-11-05
> **lindix said:**
> It&#8217;s the same old story. A new Ubuntu release, a new series of pain and frustration.

Thus everyone is encouraged to report bugs to launchpad - [https://launchpad.net/](https://launchpad.net/) and make the release better.

---

### Post by ukripper on 2009-11-13
linuxphoenix - I got your PM, can you do as i suggested in post #2

---

