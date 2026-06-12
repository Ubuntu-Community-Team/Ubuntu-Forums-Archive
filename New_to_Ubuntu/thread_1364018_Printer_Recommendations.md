---
title: "Printer Recommendations"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-12-25
I'm going to buy myself a cheapo printer/scanner/copier in the January sales, and as I've never yet printed anything from Linux, I was wondering whether some brands are more notorious than others for being difficult to set up.

Anyone got any experiences they'd like to share?

---

### Post by audiomick on 2009-12-25
I think HP is supposed to work well. I know my old HP deskjet never gave me a problem.

I am now using a Samsung colour laser printer, and, whilst it works, the quality is marginal on linux. They supply linux drivers, but they turned out to be a complete pain. I gave up on them and am using the drivers from Ubuntu. On the other hand, someone else posted in a thread on more or less the same topic that he was happy with his B+W Samsung.

I am also generally a bit biased against samsung. I have a number of Samsung things, including the HDs in my computer and my NAS, and all in all I have had more annoyance than  satisfaction with them.

---

### Post by Teber on 2009-12-25
lexmark would seem to be not a very good idea for you.

as to printers, brother has been mentioned as suitable.

as to printers/scanners/all-in-ones hp gets a good press. IIRC drivers for fairly recent hp models are maintained by canonical ltd. hp drivers will be installed by ubuntu automagically. i myself use an hp deskjet 3740 series, no issues. 

i have no doubt some kind spirits will recommend other brands too :)

---

### Post by rburkartjo on 2009-12-25
roger i second that i never have had a problem using any hp  printer with linux

---

### Post by kellemes on 2009-12-25
Check the [printerdatabase of OpenPrinting]("http://www.openprinting.org/printer_list.cgi").

Cannot recommend any specific type of printer since I'm currently looking for a new one myself. But I always had HP printers, and **never** had issues, always plug and play on Linux.
Still.. before you buy, **always** check OpenPrinting for compatibility issues..

---

### Post by coffeecat on 2009-12-25
For the scanner part, check this site:

[http://www.sane-project.org/](http://www.sane-project.org/)

Unfortunately, it's not nearly as well maintained as OpenPrinting, but it might stop you from buying a paperweight.

General rules: Avoid Lexmark. Avoid Canon. And with HP you are more likely to be OK (I'm happy with my HP all-in-one) but even HP produce machines that don't have Linux support.

---

### Post by Roger Allott on 2009-12-25
Thanks for your feedback, everyone. I think the general theme is that I wouldn't be a fool to buy an HP jobbie.

Which is good, because a particularly cheap one at the moment is the HP DeskJet F2480 All in One Printer - sold by Tesco for £33.97.

What I've seen though from [OpenPrinting]("http://forums.linux-foundation.org/read.php?20,10628,11004#msg-11004") is that it needs hplip 3.9.10, whereas I've only got hplip 3.9.8 from the Canonical repositories in Synaptic.

It would seem from [HP lip opensource]("http://hplipopensource.com/hplip-web/install/install/index.html") that 3.9.12 is the most recent version available, but that looks like I'd need to compile the driver myself.

Does anyone know where I can get the latest hplip as a deb?

---

### Post by coffeecat on 2009-12-25
> **Roger Allott said:**
> Does anyone know where I can get the latest hplip as a deb?

You can get an Ubuntu-compiled deb for 3.9.10 here:

[http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/)

Scroll right down to the end.

---

### Post by Bucky Ball on 2009-12-25
Most HP devices work 'out of the box'. HP have an easy setup programme you can download (HPLip). 

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Check this:

[http://h71028.www7.hp.com/enterprise/cache/309906-0-0-0-121.html](http://h71028.www7.hp.com/enterprise/cache/309906-0-0-0-121.html)

[http://h20180.www2.hp.com/apps/Nav?h_pagetype=s-001&h_lang=en&h_cc=us&h_product=18972&h_page=hpcom&cc=us&lang=en&h_client=S-A-R163-1](http://h20180.www2.hp.com/apps/Nav?h_pagetype=s-001&h_lang=en&h_cc=us&h_product=18972&h_page=hpcom&cc=us&lang=en&h_client=S-A-R163-1)

---

### Post by Dirtpile on 2009-12-25
Download hplip-3.9.12.run from [http://downloads.sourceforge.net/project/hplip/hplip/3.9.12/hplip-3.9.12.run?use_mirror=voxel](http://downloads.sourceforge.net/project/hplip/hplip/3.9.12/hplip-3.9.12.run?use_mirror=voxel)

Drag and drop that file into a shell and it should install.

I did this about an hour ago, but got a dependency missing error.  So i had to run this command:
```
sudo aptitude install --assume-yes libcupsys2 cupsddk cupsddk-drivers libcupsys2-dev cupsys-bsd libcupsimage2-dev libdbus-1-dev build-essential gs-esp openssl libjpeg62-dev libsnmp-dev libtool libusb-dev python-imaging policykit policykit-gnome python-qt4 python-qt4-dbus python-dbus python-gobject python-dev python-notify python python-reportlab libsane libsane-dev sane-utils xsane
```This should get you working if you get the same error.

Should that fail there is an excellent manual install walkthough here: [http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)

Then just restart your printer or computer if you prefer and run hp-setup in terminal.

BTW the manual install works perfectly, I know because i did it that way just for the experience.

---

### Post by fatality_uk on 2009-12-25
Pretty much anything HP will usually work out the box with Linux/Ubuntu thanks to HPLIB. I would avoid Xerox. Although they do have some Linux compatibility, it tends to be flaky.

---

### Post by Roger Allott on 2009-12-25
> **coffeecat said:**
> You can get an Ubuntu-compiled deb for 3.9.10 here:

[http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/)

Scroll right down to the end.

I downloaded hplip_3.9.10-3ubuntu4_i386.deb and opened it with GDebi, but I got the error message "[COLOR="Red"]Error: Breaks existing package 'hpijs' dependency hplip (= 3.9.8-1ubuntu2)[/COLOR]".

So I downloaded hpijs_3.9.10-3ubuntu4_i386 and opened it with GDebi. And then I got the error message "[COLOR="Red"]Error: Dependency is not satisfiable: hplip (= 3.9.10-3ubuntu4)[/COLOR]".

Anyone with any ideas on what to do now?

---

### Post by Roger Allott on 2009-12-25
Well, this is what I did. I found that hplip 3.9.10 has dependencies that have dependencies that need newer versions than those in karmic repositories.

So, I added "deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) lucid main" to my sources list, and installed 3.9.10 via Synaptic, which of course upgraded all of the dependencies as well.

Then I removed the lucid repository to avoid getting all the development stuff that I suppose is not fully tested yet.

---

### Post by Bucky Ball on 2009-12-26
Maybe you would want to get a printer and try all this out.

---

### Post by Roger Allott on 2009-12-26
> **Bucky Ball said:**
> Maybe you would want to get a printer and try all this out.

Yes, that was the plan. But I've just got back from a Boxing Day BBQ and some jolly nice friends of mine gave me an Epson Stylus DX6000 that has been sitting around in their garage for a month or so. So all the fannying around with getting the HP stuff has come to nought!

---

### Post by coffeecat on 2009-12-26
> **Roger Allott said:**
> Epson Stylus DX6000

It seems that you may have a bit of fiddling around to do with the Epson:

[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX6000](http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX6000)

Good luck with that, or does this mean a trip to Tesco after all? :wink:

---

### Post by Roger Allott on 2009-12-27
> **coffeecat said:**
> It seems that you may have a bit of fiddling around to do with the Epson:

[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX6000](http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX6000)

Good luck with that, or does this mean a trip to Tesco after all? :wink:

After reading that, I thought it best to install the printer on Windows Vista first. Even if I couldn't print from Ubuntu, printing and scanning would become the third and fourth reasons for me to retain Windows as a dual-boot option.

I plugged in the USB lead once Windows booted, expecting the drivers to be installed automatically. Windows didn't find them.

So I downloaded the Windows drivers from the Epson site and repeated. I told Windows to look for the drivers in the directory where I had them. It didn't find them.

The drivers were .exe files, so as a last resort, I double-clicked on one of them in Windows Explorer. It turned out to be a self-extracting zip file, and eventually my scanner driver was installed.

So I repeated with the other 4 .exe files I'd gotten from Epson, and the other functions got installed.

Then, I booted Ubuntu, thinking it was going to be one heck of a job to get it functioning.

System > Administration > Printing > Server > New > Printer. I found and correctly identified my printer as an Epson DX6000, and then offered me the choice to install drivers for the DX4850 or the DX7000. The openprinting page had said that DX4850 drivers work fine for the DX6000, so I chose that, and then I printed a test page.

What took me a couple of hours of head scratching for Windows was done and dusted in about 5 minutes in Ubuntu!

---

### Post by coffeecat on 2009-12-27
> **Roger Allott said:**
> What took me a couple of hours of head scratching for Windows was done and dusted in about 5 minutes in Ubuntu!

Excellent story! Thanks for posting that.

---

### Post by Teber on 2009-12-27
cool story!

here's my contribution:

i have a somewhat similar experience with installing my hp printer. under winxp i must run an install program from cd and connect my printer somewhere during the procedure. under ubuntu it's even easier than with that epson machine.

---

### Post by Georgia boy on 2009-12-27
I have a HP psc750. When I installed Ubuntu it picked up right away. I've seen in some threads elsewhere that a lot of people didn't like HP. However from the experience I've had and some others also if this printer does take a dive to the end I'll probably be replacing with another HP. 

Tom

---

