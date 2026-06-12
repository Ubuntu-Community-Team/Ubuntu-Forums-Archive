---
title: "3 installs and none of them will boot up"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by targets on 2011-03-14
i have downloaded the 10.10 and put it onto a USB stick loaded it on to 3 different computers with sata and ide drives ,and it all goes well with the installation to completion.
The wifi works and all looks good .then i turn off with shutdown.
then when i go to boot up i just get a message that theres no boot up media and asking for a boot disk and asking for a boot disk and to press a key !
one was a Toshiba netbook ,one was my xp installtion which is now screwed up and wont do anything,another was a fresh install onto a spare 30gig IDE drive which wont boot up either  .

whats going on here ??

---

### Post by oldfred on 2011-03-14
Welcome to the forums.

Mixed SATA & PATA drives cause confusion. Not all BIOS report drives in the same order.

Grub normally defaults to the boot drive usually sda when you install. Are you booting from sda which most BIOS report as the IDE drive. Or just try booting from the other drive. On my system I have a one time boot key f12 to choose what to boot without editing BIOS.

To see exact configuration:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

