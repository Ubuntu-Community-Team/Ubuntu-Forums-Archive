---
title: "no wireless connection w/WNDA3100v2, 12.04"
date: 2014-03-30
forum: Networking &amp; Wireless
---

### Post by rskins43 on 2014-03-30
I followed this advice exactly, but adaptor didnt blink on reboot, still no connection. Please help! :


[COLOR=#333333][FONT=UbuntuRegular]I had exactly the same problem with my wna3100 and ubuntu 11.04 After two weeks of trying all suggestions I could find on the net, I succeeded. I hardly know anything about linux and found it quite simple. You just need the right driver.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Do the following step by step:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]-plug in the wna3100[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]-open the terminal and type: lsusb[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]-hit enter, you should see something like this: Bus 001 Device 002: ID 0846:9020 NetGear, Inc.[/FONT][/COLOR]

[LIST]
[*]if the answer is yes go on with the following
[*]create a folder somewhere you could find it easily (name it wifi driver or so)

[*]download the driver from here: (just copy the url, paste it in your web browser and hit enter if the link doesn't work)
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular][http://media.cdn.ubuntu-de.org/forum/attachments/2612284/Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/2612284/Broadcom_bcm43xx_USB_32_64bit_v2.tar.gz)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]-You will get a box that ask to open or save the driver file[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]-open it with whatever program you use to unzip (or save it somewhere and unzip it from there)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]-unzip it to the folder you created in the first step[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]-right click both .inf files, go to tab 'rights' and click on the make file executable box (mine is in dutch so I don't know if the translation is right)[/FONT][/COLOR]

[LIST]
[*]close that window

[*]do the same for the .sys files

[*]now open the windows wireless driver program (download it from ubuntu software center if you don't have it)
[*]browse the .inf file with that program and click install.
[*]never erase the folder where the .inf and .sys files are found
[*]pull out the wna3100
[*]reboot your computer
[*]plug in the wna3100, when it stops blinking open the network manager.
[*]You should be able to see your wireless network.
[/LIST]

---

