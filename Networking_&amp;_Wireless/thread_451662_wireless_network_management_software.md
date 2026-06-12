---
title: "wireless network management software"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by band-aid on 2007-05-22
When I upgraded to 7.04 I switched to xubuntu rather than ubuntu because it was so much faster. Well, I'm really missing my wireless management software. In regular ubuntu nm-applet would start at startup and sit in the system tray and I could click it whenever I wanted to check for wireless networks. I have nm-applet right now but it pretty much fails at life. It won't search for wireless networks and I have had to resort to doing everything through the terminal.

```

sudo iwlist scanning
sudo iwconfig eth1 essid <essid>
sudo iwconfig eth1 ap <ap>
sudo iwconfig enc <key>
sudo /etc/init.d/networking restart

```

and that only works on my home access point. Is there any decent wireless software out there?
I know how to make the software I have start at startup but it refuses to see wireless connections. I hate to have to use windows when using a public access point. I wouldn't mind doing it through the terminal if I knew it would work all the time.

---

### Post by ugm6hr on 2007-05-22
Not sure how far you got - but I cracked this recently:

[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

I suspect the issue is to "enable roaming" - as explained in the link.

---

