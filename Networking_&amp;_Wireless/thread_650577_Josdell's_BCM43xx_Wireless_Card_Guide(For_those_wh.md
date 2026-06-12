---
title: "Josdell's BCM43xx Wireless Card Guide(For those who still need help)"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by Josdell on 2007-12-26
This is a guide different than the other one stickied above, I hope this one helps to those still wanting Ubuntu to go Wireless!

This is not my original guide or created files. I'm just posting on Ubuntuforums.org for easy finding :) .

You can do this through terminal or not, depending on which one you like using. When I tried doing this on terminal it got a bit screwy, so you might want to type in terminal 

"gksudo nautilus" later on.

Okay now for the guide ! Please Vote!

For non-terminal users:
Go to [http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/)
bcm43xx-firmware_1.3-1ubuntu2_all.deb
and save it in your home folder.
Right click it and chose the Package Installer. Install Package.
For 32-bit users:

Go to website [http://linux-geek.org/files/bcm43xx.tar.bz2](http://linux-geek.org/files/bcm43xx.tar.bz2)
Save wherever. 
Okay now this is the only terminal part.
In terminal type:   gksudo nautilus
Then enter password. now go to the directory where you extracted bcm43xx.tar.bz2
copy bcm43xx.ko and in the address toolbar of nautilus, put in: 
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/bcm43xx
!!!WARNING!!! Only delete the file I'm going to tell you!!
delete the bcm43xx.ko file there and paste the other one you copied.
Your wireless should start working or you might have to reboot. Either, this should work!


For Terminal Users:( I found using the terminal for this was buggy, maybe it was me :) )

In Terminal:
    cd ~

    wget [http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/)
    bcm43xx-firmware_1.3-1ubuntu2_all.deb

In Terminal Again:
    sudo dpkg -i ./bcm43xx-firmware_1.3-1ubuntu2_all.deb

then:( the rm function in this deletes the installer package and nothing else)
    rm ./bcm43xx-firmware_1.3-1ubuntu2_all.deb

For 32 bit users:
    wget [http://linux-geek.org/files/bcm43xx.tar.bz2](http://linux-geek.org/files/bcm43xx.tar.bz2)

For 64 bit users:
    wget [http://www.linux-geek.org/files/bcm43xx-64bit.ko.tar.bz2](http://www.linux-geek.org/files/bcm43xx-64bit.ko.tar.bz2)

In Terminal:
sudo rm /lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko

Then(32 Bit Users):(On A Single line):
sudo tar xvjf ./bcm43xx.tar.bz2 -C /lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/bcm43xx/

Then(64 bit Users):(On A Single Line):
sudo tar xvjf ./bcm43xx-64bit.ko.tar.bz2 -C /lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/bcm43xx/

Either it should start working or you need to reboot.

[SIZE="5"]Make sure you are in the same directory for all things when running commands[/SIZE]

I Hope this helps some very sad and hopeful people.
Please Post outcomes, I dont know if this became a poll, so just post outcome on thread if its not a poll.

Sorry if it's hard to read, i don't know how to post a code box thingy-majig. :KS

---

