---
title: "Printer issues in Vista/Change to ubuntu?"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by Iknownothing on 2009-08-01
Hi all

I have huge issues with my Vista on PC (ubuntu on notebook) virus it seems disguised as printer drivers have buggered things up. had a guy round who spent 6 hours over two night and was unable to get printer to work (hence my previous thread trying to get printer to work on ubuntu "printer not working" so i could get printing, still not resolved) 
will not even system restore. is it possiable to wipe Vista and replace with ubuntu and if so will the printer work or has the hard drive been damaged. At the moment I have two computers that wont print and i need to get the issue resolved be Monday :confused:

---

### Post by Bucky Ball on 2009-08-01
There is no way of answering this without knowing what printer you have. If it's a HP or Epson, there is a good chance it will work in Ubuntu. Let us know.

This should get you started:

[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

A more thorough search will dig up a handful more printers that aren't listed there.

---

### Post by Iknownothing on 2009-08-01
> **Bucky Ball said:**
> There is no way of answering this without knowing what printer you have. If it's a HP or Epson, there is a good chance it will work in Ubuntu. Let us know.

This should get you started:

[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

A more thorough search will dig up a handful more printers that aren't listed there.

It a HP 4272

---

### Post by Bucky Ball on 2009-08-01
Probably more details than that. Deskjet, Laserjet, Colour Laserjet? Some have letters first like HP CP1215. Have a look on the link I gave you and see if you can find it with their printer finder. Also, you could try here:

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

HPlip is the driver you will be hoping to work as it works great with Ubuntu in most cases. You will need to use it to install the printer. Make sure it is on the list at the above link.

The majority of their printers work with the HPLip driver alone. A few others need a seperate plug-in not included with HPLip and very few don't really work. So it looks promising for now.

---

### Post by Iknownothing on 2009-08-01
> **Bucky Ball said:**
> Probably more details than that. Deskjet, Laserjet, Colour Laserjet? Some have letters first like HP CP1215. Have a look on the link I gave you and see if you can find it with their printer finder. Also, you could try here:

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

HPlip is the driver you will be hoping to work as it works great with Ubuntu in most cases. You will need to use it to install the printer. Make sure it is on the list at the above link.

The majority of their printers work with the HPLip driver alone. A few others need a seperate plug-in not included with HPLip and very few don't really work. So it looks promising for now.

Hi, yeh sorry its a HP Deskjet F4272 All in one. Is it a good Idea to remove Vista?

---

### Post by Bucky Ball on 2009-08-01
All depends on whether you are going to want to use it for anything. If really bugged up, you might want to reinstall it and then Ubuntu if that is the case (install Vista on one partition, leave the rest empty for Ubuntu). A dual-boot is fine. 

If not, you can wipe the drive when you install Ubuntu anyhow. Would be a good idea to download the ISO (I suggest 8.04 LTS version; more stable as has been around longer and better suited for beginner), boot from it and try Ubuntu from the CD before you install to make sure your hardware is compatible and everything is running okay. Run the option in the CD menu 'Check CD for Defects' before installing.


*** Good news! You will find your printer in this list here:

[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f4200_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f4200_series.html)

Scroll down to Ubuntu and it shows that it works just fine and you only need HPLip. :)


Before any of that, though, you maybe should download and concentrate on installing and how to do that. At least you know the printer will work, how about everything else? How much RAM?

---

### Post by Sidewinder1 on 2009-08-01
You may find this thread informative...
[http://ubuntuforums.org/showthread.php?t=1083976&highlight=HP+Deskjet+F4272](http://ubuntuforums.org/showthread.php?t=1083976&highlight=HP+Deskjet+F4272)

HTH,
Side

---

### Post by Bucky Ball on 2009-08-01
The installation procedure has to be done just right. If you don't follow the steps precisely, you wind up in exactly the spot that person did. I speak from experience.

If you follow the screen and instructions it's fine. The crucial thing is when asked you MUST un-plug and re-plug the printer or the is in that link. I tried to get my mother-in-laws printer installed using hplip and the plug-in over phone and internet for six months to no avail. I recently went over for a visit and had the printer running in less than ten minutes. There are a couple of easy mistakes you can make but not if you are PAYING ATTENTION! lol  ;-)

A mistake that person made was trying to run the app again. You don't. You completely uninstall HPLip and start again. That is the only way as it won't 'fix' itself by doing just re-running HPLip (not in my experience).

---

