---
title: "HP Laserjet 6p will not print"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by Researcher1 on 2011-01-01
I just installed Ubuntu 10.10 on an HP Desktop.  It uses the old parallel cable.  This laserjet 6P looked like the driver installed just fine.  But when I print the test page or a single page the printer does not print the correct info.  Some strange looking text appears on the first page and then it just keeps pushing pages through the printer and it won't stop unless I cancel the job.

Is there some other printer driver I should use other than the one the ubuntu system finds and installs when it sees my printer?

Or is there something within the printer properties I can adjust?

---

### Post by khelben1979 on 2011-01-01
It should be working. [HP LaserJet 6P at LinuxPrinting.org]("http://www.openprinting.org/printer/HP/HP-LaserJet_6P").

You can test and install the driver from the link above to see if it works better. Have you ever tried the printer with Windows to know if it works correctly with that?

---

### Post by oldsoundguy on 2011-01-01
I left my 6MP plugged into my Windows/Adobe machine rather than move it to a Linux box.  Then set the Windows as a print server on my home net.  Works just fine that way.  So the Cups drivers work for the machine for me.

---

### Post by jcthei on 2011-08-14
I'm having an issue with my HP Laserjet 6P connected through my network using a Linksys Wireless G USB print server. I have the correct IP address and set the printer using hpcups3.11.7, but doesn't print. I can plug the print in to any USB port, and prints fine.

Any help would be great, as I use Linux now more then Windows. Running Ubuntu 10.04LTS x32 with kernel 2.6.32-33.

Thank you for your help in advance.

---

### Post by Matt__ on 2011-08-14
you could download and install the latest [HPLIP imaging and printing]("http://hplipopensource.com/hplip-web/install_wizard/index.html").

Its a .run file that auto resolves dependencies/package versions etc etc.

[step by step instructions on how to install]("http://hplipopensource.com/hplip-web/install/install/index.html")

---

### Post by adsbaer12 on 2011-10-19
downloaded and installed HPLIP imaging and printing - no success!
everything worked fine out of the box in ubuntu 11.04 x64. now I have to boot into ubuntu 11.04 live-mode via usb-pendrive every time I want to print. this su*ks!
help any1?

---

### Post by adsbaer12 on 2011-10-22
my problem with HP LaserJet 6MP was solved today by switched permanently to linux mint 11 as my primary operating system (where my printer was again correctly recognized out of the box).
thanks for my first linux years, ubuntu! but I think I'm gonna move on and stick with linux mint from now on... ):P

---

### Post by weezyrider on 2011-10-22
HP printers seem to have a problem with printing Gibberish. I've had inkjets do it, laserjets do it and a large TOL color laser do it. 

My 1300 Laserjet is slower than molasses in January printing anything from the internet. If you do anything else, like use Office, Inkscape it prints immediately. Even the Canon Pixma 6000 doesn't do well with printing from the internet. That printer rarely gives me any problems in Windows. 

If you do a printer test - both printers print immediately.

---

### Post by cornelis spronk on 2012-06-29
I had a similar nonprinting problem with a parallel connected LaserJet 6MP when I installed Ubuntu Precise 12.04.  I sent a bug report to Lauchpad along with a printout of 'hp-check -t'.  I got an personal email reponse from Sarbeswar Meher at Launchpad with the following information:

There are lots of dependencies missing which is shown by 'hp-check'.

I request you install the latest hplip from

 [http://hplipopensource.com](http://hplipopensource.com)/hplip-web/install/install/index.html

 and follow the instructions from their website.

 Parallel port support in HPLIP has been made passive, hence you need to
make a custom build.

After installation is done, go to the folder Downloads/hplip-3.12.6

- Run in terminal :
   $ cd ~/Downloads/hplip-3.12.6
   $ ./configure --prefix=/usr --enable-pp-build
   $ make
   $ sudo make install

 - After this, connect the printer and run in teminal 'hp-setup'.

A box will appear with four choices.  Choose the parallel one (the lowest one down).

Then install the printer going into Dash home-->Printing-->Add new printer.

Then choose the proper drivers and your printer as presented by the printer install program.


These instructions worked for me.

Hope this is usefull for someone else.

---

