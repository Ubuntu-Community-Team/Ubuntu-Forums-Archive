---
title: "Help with Wicd Boot up but not the normall one."
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by Neej Suab on 2007-11-16
Ok, so i actually have two problems with wicd. Not major ones so if they are not solved no big deal. but here they are. First is when I boot my laptop everything is ready to go fairly fast. I can open any program i want. Except Wicd. It takes my computer two to five minuets before i can open wicd. I haven't actually timed it because most of the time i turn on my laptop and do something else for a while till it works. I don't have it set to auto start. it just takes that long untill i can click on the icon to make it run. It is very irritating. I saw some other posts about this but they didn't have a solution except for check if any autoconnect is enabled which none are. 
The other problem is that when i connect at home before i connect to my wep encrypted network i must run sudo iwconfig wlan0 essid "wiglaf" enc "xxxxxmywepkeyxxxxxx". or wicd will hang on obtaining ip address. I would like to fix these problems. Thanks for your help.

---

### Post by jacoor on 2007-12-19
I'm having very similar problem. After booting I can't use Wicd for quite long time - it is very annoying when I'm using my laptop away from home and searching for awailable wifi networks. I think that wicd is searching for known networks and when it finds none it alows me to open it and choose which one to connect to. 
Workaround is to open another wireless lan manager and connect to any network - wicd starts to work properly as soon as connection starts.
Any solutions for this? It's quite annoying when I have to start Wireless assistant evertyime when I am in a new place.

---

### Post by imdano on 2007-12-20
What version are you using jacoor?  Try upgrading to 1.3.6 or 1.3.8 and see if you still have the problem.  If you're already using an updated version, what exactly happens when you start wicd up?  Does the tray icon appear right away but won't work when you click it, or does it not appear at all?

---

### Post by jacoor on 2007-12-20
Problem shows up with latest stable release, 1.3.1. The icon appears but when I click on it it goes blank and nothing happens... Unless I open another wifi manager, for example Wireless Assistant and connect. When connection starts - wicd starts to work properly. Problem occurs only in area  with unknown networks - when moving from home to office it switches nicely, no action from me required. But when there is no known network available - be patient, or use another manager.
Anyway, I just upgraded to 1.3.8 to see how it works and I write about it after testing.

---

### Post by jacoor on 2007-12-20
Version 1.3.8 works from the box :-)
Great :-) I had no problem to connect to unknown network. 
There were minor problems while installing it:
- used apt-get remove to uninstall previous  version
- I installed this one but had no success while connecting - it hanged / freezed for some time on WPA file generation. 
- I removed all files related to this software from /opt and /etc and it started to work nicely :-)
Thanks for help!
And Merry Christmas!

Jacoor

---

