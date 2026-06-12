---
title: "wireless not detect"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by medivh on 2006-11-24
I cant see my connection on network settings windows under wireless connection settings page.But i can see it with the iwlist scan command.
You can see on the screenshot below.

[[IMG]http://img224.imageshack.us/img224/9701/screenshotou2.th.png[/IMG]](http://img224.imageshack.us/my.php?image=screenshotou2.png)
(while clicking the arrow near ssid list it was unable to take screen shot there is nothing in the list)

Using ubuntu Edgy Eft.
My wifi card is intel 2200bg.
When i close security on router i can connect by manualy writing ssid.
It doesnt work when WPA is open.

I have read a few posts.I dont want to set it manually in config files for each time i wanna connect to an ap. If i configure it for my home network what will i do in school.Will i have to change it every time i go school and come back.

---

### Post by FrodoB on 2006-11-24
You want to enable the universe repository in /etc/apt/sources.list and then get wifi-radar.

$ sudo gedit /etc/apt/sources.list

Uncomment the lines:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

by removing any "#" symbols in the first column of those lines and then run:

$ sudo apt-get update
$ sudo apt-get install wifi-radar

The menu Applications -> Internet

will now contain Wifi-radar and this will work for you on unsecured hotspots. If you need more than this then someone else will need to chime in.

---

### Post by cosmolee on 2006-12-22
Try "wireless assistant".   It may already be installed.  Click Applications->Internet


That network configuration tool under System->Administration->Networking PISSES ME OFF.   What is that piece of junk?  It doesn't have a Wireless Network scanner.](*,)   So, you have to know what the SSID is in advance before you can connect.  

Just try going into a coffee shop and asking the clerk what the "SSID" is without getting a blank stare.   I don't know what SSID's are available when I'm at a friend's apartment or office, or on a park bench.  People don't want to have to learn `iwconfig` at the command line to get their wireless working.  

That crummy applet in System->Administration->Networking is a great way to drive someone away from Ubuntu, cuz it Suks.  It makes Ubuntu seem impossible to use.  I really can't see how anybody checking out Ubuntu with a Live CD is going to get Ubuntu wireless running when that applet is all they get.  It makes Ubuntu seem like junk.  

Ubuntu management needs to know that this is a it doesn't "just work" deal killer.

---

