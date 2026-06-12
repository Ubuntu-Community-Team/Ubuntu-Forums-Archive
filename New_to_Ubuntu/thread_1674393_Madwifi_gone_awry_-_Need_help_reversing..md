---
title: "Madwifi gone awry - Need help reversing."
date: 2011-01-23
forum: New to Ubuntu
---

### Post by jd2012 on 2011-01-23
Hello all, and thanx for reading. This is my first time posting as you can probably see.

Straight to the point, i recently installed ubuntu 10.10, and am totally new to linux in general (and i love it). My PC has an Atheros ar9825 card built in, and out of the box ubuntu has drivers, but speeds were very slow. 1.9Mb/s in  vista; 300kb/s in ubuntu.

Upon further research i decided my nix distro needed madwifi, being a newbie i dumped any command i thought was helpful in the terminal, specifically this one 

[http://ubuntuforums.org/showthread.php?t=942195](http://ubuntuforums.org/showthread.php?t=942195)

You have to give me some credit this is not THE guide i followed, as THE guide i followed just said "This is a guide to help you install madwifi for atheros based cards". Although the instructions [commands] are identical. 

Basically i dont want to reinstall ubuntu because of this but it has rendered my card unusable. Just a simple way to reverse would be AWESOME.

Any one shed any light?

---

### Post by jd2012 on 2011-01-23
sorry, found solution.
used my noggin + search feature.
Would delete if i knew how.

---

### Post by jd2012 on 2011-01-26
Sorry for bumping, but this issue isnt fully resolved. After searching for hours i have not found a straight-forward solution to this problem.

Basically I followed the instructions on this thread:

[http://ubuntuforums.org/showthread.php?t=942195](http://ubuntuforums.org/showthread.php?t=942195)

And upon reboot the wlan did not work. 
The so-called "Solution" I found was entering [at bootup] in a terminal
```

sudo modprobe ath9k

```I get some kind or error saying something about files being ignored, but the wlan works.
But doing so at every start up is frustrating. Any ideas on how to reverse the instructions?
Thx in advance.


Asus K50IJ-Best Buy edition.
Atheros Wireless AR9285
Ubuntu 10.10 Maverick Meerkat


[B][COLOR=Red]********EDIT********

[/COLOR][/B][COLOR=Red][COLOR=Black]Upon second look at instructions what i did was "blacklist" my ath9k drivers, thats why they dont launch at startup [duh]

For anyone else having the same problem simply:
In terminal
```

sudo gedit /etc/modprobe.d/blacklist

```

And delete the following:

```

#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k

```

Save.
Reboot. It worked for me. 
[/COLOR][/COLOR]

---

