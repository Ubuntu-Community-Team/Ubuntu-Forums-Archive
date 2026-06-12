---
title: "Printer won't print"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by Ellinelés on 2011-04-15
I've installed the drivers for my printer (Canon PIXMA MP270) and it says that it's connected, but when I prints it appears in the print queue as completed but **it doesn't actually print something physical**. I'm working on a desktop computer connected directly to the printer by a USB cable.

Could anyone please help me? I've searched around and found nothing that help. Thanks.

---

### Post by rosencrantz on 2011-04-15
[http://ubuntuforums.org/showthread.php?t=1674756&highlight=pixma+mp270](http://ubuntuforums.org/showthread.php?t=1674756&highlight=pixma+mp270)

Hint: search the forums. Much more Ubuntu focussed than Google.

---

### Post by Ellinelés on 2011-04-15
Thanks for telling me, but I uninstalled the drivers and reinstalled them from the canon site (following the link's directions) and I still have the same problem.

---

### Post by rosencrantz on 2011-04-16
It's difficult to find out what's wrong if you don't actually have the model -  mine is a well-behaved Samsung. Quite a lot of forum users get a 'pretends to print but nothing happens' error, and usually it's resolved by getting an up-to-date driver.
Where exactly did you download yours from?
Here is a more wordy howto:
> **Maddog Battie said:**
> The drivers are also on the European website:
[http://software.canon-europe.com/products/0010753.asp](http://software.canon-europe.com/products/0010753.asp)

The all graphical install process:

[LIST]
[*]Download the printer driver (debian printer driver 3.2) and open in archive manager.

[*]Double click on cnijfilter-mp270series-3.20-1-i386-deb.tar.gz to open that.

[*]Double click on the packages directory.

[*]Double click on the cnijfilter-common_3.20-1_i386.deb file.

[*]Hit install then quit out.

[*]Double click on the cnijfilter-mp270series_3.20-1_i386.deb file.

[*]Hit install then quit out.

[*]Go System->Administration->Printing.

[*]Click on Add. Wait a while... (10 secs)

[*]Hopefully something like USB Printer #1 with status readback for Canon IJ will appear. Select it and then hit forward.

[*]Adjust names if required. Hit apply. You should now be up and running for printing.
[/LIST]

---

