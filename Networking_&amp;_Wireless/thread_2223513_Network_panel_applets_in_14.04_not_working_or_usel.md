---
title: "Network panel applets in 14.04 not working or useless"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by franter on 2014-05-11
I've been using Lubuntu from time to time during a few years, but now with the end of Windows XP and the poor screen experience that Windows 7 gives, I wanted to use Lubuntu more often. So I installed 14.04 only to find out that I couldn't use it because if I wanted to turn off networking I had to get around and take the connector out. There are two network panel applets in 14.04 but I don't understand anything about what information they give or how they work, if they work.

On Lubuntu 12.04 which I'm using now the network panel applet is quite good, a simple click and one is informed about the network connectors, if they're on or off, and it's easy to turn them on or off.

Is it possible to take an applet from 12.04 and install it on 14.04, or download it somewhere?

Is it possible to make those existing network panel applets in 14.04 more usable?

I always turn off the connection to the internet as soon as it's not needed, with 12.04 I've already experienced at least twice that Lubuntu get's so slow that it won't even turn off when being left unattended too long on the internet.

---

### Post by Dennis N on 2014-05-11
Here is how to fix the network manager applet in Lubuntu 14.04:

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

fix #1 is the one that I used.

(The two applets you can add to the panel through "Add Plugin to Panel" - 'Manage Networks' and 'Network Status Monitor' are not the same as the one above.)

---

### Post by bapoumba on 2014-05-11
Just for the record : [https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1308348](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1308348)

---

### Post by sudodus on 2014-05-11
If you make a fresh install, update and upgrade your Lubuntu 14.04 LTS to the current state and reboot, it should work to add the word **nm-applet** to the file [FONT=courier new]**$HOME/.config/lxsession/Lubuntu/autostart**[/FONT] which can be done with the following command line.

```
echo 'nm-applet' >> $HOME/.config/lxsession/Lubuntu/autostart
```

If you have two applet icons, it may be left from a bug, that appeared during the development of Trusty (at the alpha or beta stage). If you get  the 'wrong' meny from the applet, it may also be something that remains from an earlier stage. Did you make a fresh install of Lubuntu when released or during the alpha or beta stage, or did you upgrade from Lubuntu 13.10?

I was working with this issue during this weekend, and it should work, at least with the built-in free drivers for wifi and wired internet.

-o-

See this link [https://help.ubuntu.com/community/OBI/Lubuntu_14.04_OEM-nonPAE](https://help.ubuntu.com/community/OBI/Lubuntu_14.04_OEM-nonPAE) where I made a tarball for the One Button Installer that fixes the nm-applet almost automatically for the released version of Lubuntu 14.04 LTS.

I do not mean that you should do all the things described there, I only show what was done to tweak that particular system. In a fresh install it should work to activate nm-applet. You can run it 'now' by

```
nm-applet &
```

but then it will not start automatically after rebooting. I have seen people report that it works better for them to run nm-applet with superuser privileges, but it destroys the possibility to run it plainly without superuser privileges afterwards. I think some file is created somewhere, and I have not identified it. See also this link

[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1308348](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/1308348)

---

### Post by franter on 2014-05-13
Thank you all.

Bapoumba fix 2 worked for me, not fix 1, nor any other fixes, but then I'm not good at Linux so I may have done something wrong.

The new applet icon is maybe from an earlier version, it seems familiar, it is fully usable and understandable.

But both in 12.04 and with this new applet in 14.04 I don't get the same result for "Disconnect" in Lubuntu as for "Disable" in Windows XP or earlier.
In both cases I can't connect to the internet, but with "Disable" the connection is OFF on the ADSL box, while for "Disconnect" the connection appears as ON on the ADSL box. Shouldn't "Disconnect" close the connection totally down? Maybe it does so software wise, but it's more practical when a short look on the ADSL box may tell that it's off.

---

### Post by bapoumba on 2014-05-13
Strange adding it to the Prefs > Default Apps for lubuntu > Autostart did not work for you. Worked for me after a little help from a friend :)
[http://ubuntuforums.org/showthread.php?t=2220336](http://ubuntuforums.org/showthread.php?t=2220336)

---

