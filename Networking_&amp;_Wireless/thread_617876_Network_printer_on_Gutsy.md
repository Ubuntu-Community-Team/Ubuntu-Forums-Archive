---
title: "Network printer on Gutsy"
date: 2007-11-19
forum: Networking &amp; Wireless
---

### Post by leupi on 2007-11-19
I have a desktop with Gutsy (which has an HP 6110 AIO) and a laptop with Gutsy (both running Gnome) and I am trying to print to the HP with the laptop over the network and cannot seem to get it set up. In the printer set up box on the desktop I have the checkbox for 'Shared' checked, is that all that I have to do to share it over the network?

When I try to set up the printer as a network printer on the laptop I see no option for 'network printer'. Any thoughts on how to proceed?

Thanks,
Todd

---

### Post by spegru on 2007-11-20
Hi. I just did this with PCs running Feisty and Gutsy.

To set up printers to be networkable, you have to set up the PC that is locally connected to the printer: Under Gutsy this is by ticking the "share published printers connected to this sytem" under System, Admin, Printing. Under Feisty this is in system, admin, printing, and then selecting Share Printers under the Global settings tab. 

In order to access these printers you have to add a printer using your choice of network protocol, and hopefully your PC should find your shared printer.

When you find the printer you have to select the model etc just as with a local printer

I had to add the ip address of my PC manually but this may be because of a NAT problem

hope this helps

spegru

---

### Post by leupi on 2007-12-20
Sorry it took me so long to respond to this. I shared the printer on the 4500 as you described and all seemed to be well. I then went to the D600 and went to System > Admin > Printing and have checked "Show printers shared by other systems". The printer that is on the 4500 is not showing up on the 600. CUPS is running on the 4500 and I can ping the 4500 from the D600 via IP address and hostname. When I am in the Printer Configuration on the D600 I go to "Goto Server", enter the hostname, hit OK, and I see all of the printer info just as it is on the 4500.

At this point the printer is still not usable on the D600. I go to install the printer and hit "New Printer", it searches for a second and finds the HP, I hit forward and it searches for drivers. I use the recommended hpijs driver and proceed to where I name the printer. At this point I get a error message
> CUPS server error

There was an error during the CUPS operation: 'client-error-forbidden'.
I am not sure where I should be installing this printer. Should I try to install it after using the "Goto Server" option and entering the name of the server? That seems to be the only time that the printer shows up anywhere. Or should I not be 'Going to" the server but instead trying something else. Hope that what I have here makes sense.

Thanks for the help,
Todd

---

### Post by ahildoer on 2008-01-13
So here is the solution, all in one post.

First of all, I am pretty sure both computers need to be on the same subnet for this to work. If they are not, then there is no guarantee this will work. 

On the server (computer with the printer physically connected):
[LIST=1]
[*]From the system menu, click System -> Administration -> Printing
[*]From the window on the left of the printer configuration window, select "Server Settings".
[*]Add a check next to "Share published printers connected to this system".
[*]Click 'Apply' in the lower right corner, and close the printer configuration window.
[*]Open a terminal.
[*]Run ```
sudo /etc/init.d/cupsys restart
```
[/LIST]

On the client (computer needing to print on the server):
[LIST=1]
[*]From the system menu, click System -> Administration -> Printing
[*]From the window on the left of the printer configuration window, select "Server Settings".
[*]Add a check next to "Show printers shared by other systems".
[*]Click 'Apply' in the lower right corner.
[*]Shared printers should now appear in the window on the left, and in print dialogues in applications.
[/LIST]

If you have found an error in this, please e-mail me so that I can fix the post. Thanks.

---

