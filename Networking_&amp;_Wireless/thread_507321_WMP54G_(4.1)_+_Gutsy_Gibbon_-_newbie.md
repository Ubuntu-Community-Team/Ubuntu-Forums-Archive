---
title: "WMP54G (4.1) + Gutsy Gibbon - newbie"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by ash477 on 2007-07-22
I'm totally new to Ubuntu.  And I like to dive right in... so I've got Gutsy installed 7.10 and I'm trying now to get my LInksys WMP54G v4.1 installed.  I've read some posts about people getting 4.0 installed on earlier versions of Linux, and it auto-detects.  In Gutsy, I see it in Hardware as a wireless-G adapter.  But its not working.  Any instructions to help me out with this - in dummy language?

Thanks
ash477

---

### Post by madmetal on 2007-07-25
> **ash477 said:**
> I'm totally new to Ubuntu.  And I like to dive right in... so I've got Gutsy installed 7.10 and I'm trying now to get my LInksys WMP54G v4.1 installed.  I've read some posts about people getting 4.0 installed on earlier versions of Linux, and it auto-detects.  In Gutsy, I see it in Hardware as a wireless-G adapter.  But its not working.  Any instructions to help me out with this - in dummy language?

Thanks
ash477

welcome!
gutsy gibbon 7.10 is at tribe 3 so testing yet..
its better for you to install and use 7.04 till october when 7.10 will be officially released..
although you can use your card by installing bcm43xx-fwcutter driver..
[http://packages.ubuntu.com/gutsy/utils/bcm43xx-fwcutter](http://packages.ubuntu.com/gutsy/utils/bcm43xx-fwcutter)
more infos and help..
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by gluutbuntu on 2007-10-20
Hi Mad Metal,

Sorry for interupting here, but I think you are wrong in the advise to ash477.
The WMP54G v4.1 is using a RaLink chipset. Not a broadlink as you suggested.
The bcm43xx-fwclutter is not the correct driver.
Although I haven't got my WMP54G to work with gutsy gibbon (nor any other ubuntu/linux distribution) the different forums are suggesting to use ndiswrapper and the windows driver of the WMP54G. An other solution would be to use the serialmonkey RT2x00 driver.

In my case both don't work, the serial monkey RT2x00 doesn't compile it's code, so no build even of the driver. And the ndiswrapper is giving me a bad driver message.
And the rt61pci driver which ubuntu is using after an install is also not working when you are using WPA.

I'm beginning to believe that when you are using the WMP54g LINUX IS NOT AN OPTION as an OS.
Hopefully I'll get the WMP54G to work on linux, but I'm worried.

Kind regards,

gluutbuntu

Sadly

---

### Post by tck on 2007-10-23
I have this card also, Im setting it up for my sister.

Gutsy detects it and the wireless option is available for Network Manager also. 

Just doesn't seem to want to connect (using WPA2 / AES)

---

### Post by tck on 2007-10-23
Ok I got this to work

having used

sudo iwlist scan 

to search for networks and it detected those around but not mine (because my essid is disabled)

so I enabled it and that was it. A small sacrifice but if used with WPA2 with AES - should be safe for now :)

---

### Post by dnt4getdawld on 2007-12-01
sudo iwlist scan
it works. i looked for a little bit, and I managed to find MANY different ways of fixing this issue. some of them required gutting parts of ubuntu, others were long and had steps I didn't think were necessary. This simple 1 command fix worked amazing.

---

### Post by Seankel on 2008-04-09
sudo iwlist scan
Wow, can't believe it was that simple.  I switched wireless PCI cards from a DWL G510 to a WMP54G after numerous failed attempts to use ndiswrapper with the Dlink.  Has problems again with the Linksys until I used this one little command.  So simple.  I have no idea why that worked but I don't really care.  Thanks for the tip.  Lets just hope it will hold the signal.

---

