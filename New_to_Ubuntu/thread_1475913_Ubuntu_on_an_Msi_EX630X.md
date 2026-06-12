---
title: "Ubuntu on an Msi EX630X"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Valleyman1988 on 2010-05-07
Hello,

I've been running Ubuntu for a while now on an Msi EX630X laptop running the Nvidia drivers, Gnome, Compiz, ... Got it rigged up to look a little like Mac yet not so expensive :-)

I was quite happy with it true the previous releases but since I updated to 10.04 it has got some issues :

 - When booting, after grub and the "Starting" message I just see a black screen until finally the login window comes trough, I mean I used to get just text at least like on a CLI-only system, now I don't even see anything anymore.

- Firefox seems crashes these days and after the "killall firefox" command it still says there's already an instance running and I have to close that window... I've been searching around using different process managers, I can't find it, the only thing that helps is a reboot, anyone else seen this yet or is it just the laptop?

- I've got some of those "soft touch buttons", the one for the wifi seems to work, the rest don't even light up, is there a way to fix this?

- The buttons to close, maximize of minimize windows seem to be on the right hand side again although the already installed theme before the upgrade has them on the left side.

- When I reboot, my date and clock sometimes change of position with some icons.

A little help or hint would be appreciated, the last "upgrade" seems to have really downgraded my laptop :lolflag:

---

### Post by madjr on 2010-05-07
> **Valleyman1988 said:**
> Hello,

I've been running Ubuntu for a while now on an Msi EX630X laptop running the Nvidia drivers, Gnome, Compiz, ... Got it rigged up to look a little like Mac yet not so expensive :-)

I was quite happy with it true the previous releases but since I updated to 10.04 it has got some issues :

 - When booting, after grub and the "Starting" message I just see a black screen until finally the login window comes trough, I mean I used to get just text at least like on a CLI-only system, now I don't even see anything anymore.

- Firefox seems crashes these days and after the "killall firefox" command it still says there's already an instance running and I have to close that window... I've been searching around using different process managers, I can't find it, the only thing that helps is a reboot, anyone else seen this yet or is it just the laptop?

- I've got some of those "soft touch buttons", the one for the wifi seems to work, the rest don't even light up, is there a way to fix this?

- The buttons to close, maximize of minimize windows seem to be on the right hand side again although the already installed theme before the upgrade has them on the left side.

- When I reboot, my date and clock sometimes change of position with some icons.

A little help or hint would be appreciated, the last "upgrade" seems to have really downgraded my laptop :lolflag:

1- yea the nvidia drivers have a few glitches with the new boot screen (plymouth), you may find fixes

2-you could try fully uninstall firefox and reinstall it, also try chromium / google chrome

3-if they worked with previous versions, there may be a fix

4-depends on the theme, some themes to the left and some to the right, with ubuntu-tweak you can change this or search for themes at gnome-look

5-if you leave it as default, the icons/applets usually never change positions, try not to place anything next to the notification area. this applet resizes constantly and moves your other icons/applets. It's a bug and should be 95% fixed by 10.10 as they are removing that applet

if you want to learn lots more you can always check here:
[http://ubuntuguide.org](http://ubuntuguide.org)

---

