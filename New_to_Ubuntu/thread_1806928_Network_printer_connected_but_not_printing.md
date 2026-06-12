---
title: "Network printer connected but not printing"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by aaron2209 on 2011-07-18
I am new to Ubuntu, having only downloaded it alongside Windows 7 yesterday. I have been systematically checking if Ubuntu can perform the tasks that Windows can. I seem to have hit a brick wall with my printer, a HP Photosmart C7280, the system effortlessly picked up the printer on the network and has connected to it, however, when I try to print or make a test print, the status remains on "processing" forever and the task never executes.

I have downloaded the HPlip Toolbox software and the problem remains. I also visited the hplipopensource.com website and after filling in the criteria I received the message:

"Ubuntu 11.04 supplies HPLIP 3.11.5 and it does support your printer."

However, I don't understand how the OS can connect to my printer but not be able to use use it. Printing is a vital aspect of my computer use and so I was wondering if anyone had a solution for me or have I reached a dead end.

---

### Post by roger_1960 on 2011-07-18
Hi

Does this thread help at all?

[http://www.linuxforums.org/forum/ubuntu-linux/147861-install-hp-c7280-photosmart-wirelss-printer.html](http://www.linuxforums.org/forum/ubuntu-linux/147861-install-hp-c7280-photosmart-wirelss-printer.html)

Its a bit old but seems to cover the normal process.

Roger

---

### Post by androssofer on 2011-07-18
I get the same for my brother printer... 

I had to change the driver to that of a completely different brother printer for it to work..

perhaps its the same with your hp?

I know its not a solution and is quite vague but might help point you in the right direction...

---

### Post by wojox on 2011-07-18
Try opening System Settings (gnome-control-center) and click on Printing.

Right click your printer and make sure the Location or Device URI is set properly.

---

### Post by Mark Phelps on 2011-07-18
I have a couple of different HP printers connected via Network -- and they both print without problems.

You should go into CUPS (open a browser to localhost:631) and open the screen for administering printers.

Then, for each printer, see what driver is being selected.

CUPS normally offers several driver for each model printer.  You may have to experiment with different drivers to get the ones that will work the best.

---

### Post by nimrodwebdesign on 2011-11-09
I had that problem. It turned out it was because I didn't think to assign the printer a static IP address (via it's web interface configuration), and CUPS was referencing it by it's IP. I switched it from DHCP to a manual IP and it's all good.

I hope that fixes it for you, it took me toooo long to work out.

---

