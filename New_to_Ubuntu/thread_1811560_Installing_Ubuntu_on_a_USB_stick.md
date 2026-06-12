---
title: "Installing Ubuntu on a USB stick"
date: 2011-07-25
forum: New to Ubuntu
---

### Post by suomalainen on 2011-07-25
Ubunteros,

I have Ubuntu 10.04 LTS installed on a USB stick.

I wanted to ask if the following is possible:

1. I would like to have my settings in both "NewtorkManager Applet" AND "GNOME PPP" immediately available so that I do not need to reconfigure each and every time I boot the stick

2. How can I make my firefox bookmarks available?

Thank you very much!

---

### Post by kaldor on 2011-07-25
Hyvää huomenta :)

What method did you use to create the Ubuntu LiveUSB? If you used the Startup Disk Creator available in Ubuntu you can create what is called a Persistence File. This way, your settings will stay every time you log into the LiveUSB. If you do that, you can just copy your .mozilla folder from your main Ubuntu install to the liveUSB's. Use the Ubuntu One or Dropbox service for file syncing if you need to.

---

### Post by beew on 2011-07-25
Creating a live usb with persistence and installing into a usb are two different things.

If you just want a live usb with persistence and you already have a Ubuntu install you can use the Startup Disk Creator as Kaldor said. If you are on Windows then use LILI
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

If you want a full install in a usb, check out this guide.
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by sadaruwan12 on 2011-07-25
Please, let us know what method you used to create the live USB then we could help you more.

---

### Post by suomalainen on 2011-07-25
Thank you everyone for your help thus far.

When I boot up my USB stick it's the one that say's:

"You can try Ubuntu 10.04 LTS from this USB w/o making any changes to your system".

Then two options are available 1) Try or 2) Install.


Perhaps it's easier to just reinstall? I'm flexible!

Thank you again!!!

---

### Post by suomalainen on 2011-07-25
Hello Again!

I found an on line resource and following it I was able to install Ubuntu 10.04 LTS onto my 4GB USB stick. I then created a second partition for the file "casper-rw".

I then tested the install and everything booted up fine. I could even choose between just trying Ubuntu to installing it.

I did the following 3 things.

1. Added additional keyboard layout
2. Installed GNOME PPP
3. Enabled wireless broadband connection.

Subsequent reboots proved that the settings/installs were saved and all works fine.

However, when I configured GNOME PPP the following error came up as presented in the log. I attached it.

Secondly, I went to my home folder and copied the file .mozilla to the casper-rw folder and into the home sub folder but it's not working.

Are their specific steps to adhere to when moving this file?

Thanks again!!!!

---

