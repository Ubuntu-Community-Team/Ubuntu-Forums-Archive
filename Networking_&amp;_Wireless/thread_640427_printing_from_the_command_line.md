---
title: "printing from the command line"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by jopeto on 2007-12-14
Hello,

I have a question regarding printing from the command line in Ubuntu.

I am trying to print to a printer on the network whose ip address I know (but not the name). I was able to add it from the GUI interface and selected the appropriate drivers. Now I can print without a problem, however I have to do everything from the GUI. My question is what I need to do to print .ps files from the command line. More specifically what option should I use to send it to the particular IP address, printer driver, to select the paper size, duplex or single page, as well as color or black and white.

Thank you very much in advance.

---

### Post by jopeto on 2007-12-19
OK, I figured some stuff out myself, so I decided to post it here.

A really useful tool could be found by opening up konqueror and typing localhost:631 in the location bar. This brings up a module, which lists all the printers and has options to change the settings of the printers or add new ones. There is also a page with useful hints for printing from the command line. A good one is:

lpoptions -p <printer name> -l

which lists the available options for the printer called <printer name>. So basically for my printer I the defaults settings are color and duplex, so if I want to print black and white and single side, I need to use the oprtions:

lpr -p <printer name> -o PrintoutMode=Normal.Gray -o sides=one-sided <file name>

However I am still having trouble with scaling, as neither '-o fitplot' nor '-o scaling=100' seems to work when the document pages are smaller than A4 (which is the paper size that I am using). So if anyone has some input on that it will be very much appreciated.

Thanks.

---

