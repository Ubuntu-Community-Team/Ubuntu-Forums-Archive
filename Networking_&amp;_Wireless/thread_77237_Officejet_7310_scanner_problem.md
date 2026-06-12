---
title: "Officejet 7310 scanner problem"
date: 2005-10-16
forum: Networking &amp; Wireless
---

### Post by rancher_j on 2005-10-16
Hi,

I installed Ubuntu and I was thrilled. Nearly everything worked right away. Nevertheless I do have some problems with my Officejet7310 that is connected directly to the network. I got the printer part working, by choosing jetdirect and entering the IP address. The scanner does not seem to be recognized at all. Xsane tells me no devices available. I tried to load it manually by entering "xsane hpaio:/net/officejet-7300?ip=192.168.1.100" but I get the message: "Failed to open device 'xsane hpaio:/net/officejet-7300?ip=192.168.1.100'. Error during device I/O."

I'd appreciate some help with this

thanks, johann:???:

---

### Post by krupan on 2006-08-25
This is a pretty late reply to your question, but I just got an OfficeJet 7310 and got it working in Ubuntu Dapper Drake, and figured I should share how I did it.  There might be an easier way, but this is what worked for me.

First, find out the printer's ip address.  Then on the command-line:

```
hp-makeuri <ip-address>
```

You should get something like this:

```

$ hp-makeuri 10.0.0.102

 HP Linux Imaging and Printing System (ver. 0.9.7)
 Device URI Creation Utility ver. 2.5

 Copyright (c) 2003-5 Hewlett-Packard Development Company, LP
 This software comes with ABSOLUTELY NO WARRANTY.
 This is free software, and you are welcome to distribute it
 under certain conditions. See COPYING file for more details.

 Creating URIs for '10.0.0.102':
CUPS URI: hp:/net/Officejet_7300_series?ip=10.0.0.102
SANE URI: hpaio:/net/Officejet_7300_series?ip=10.0.0.102


```

Keep the output of this handy, you'll need it in a bit.

Next from the menus do: System -> Administration -> Printing

Double click New Printer.

Choose Network Printer: CUPS Printer (IPP)

Copy and paste the ```
hp:/net/Officejet_7300_series?ip=10.0.0.102
``` from hp-makeuri for the URI.

Click Forward

Choose HP for the Manufacturer, and OfficeJet 7300 for the Model.

Click Forward

Enter a Description and Location if you want.

Click Apply.

Now, back to the command-line:

```
sudo emacs /etc/cups/printers.conf
```

fix the URI for the 7310 by removing the ```
ipp://
``` from the front.  Make sure the ? didn't turn into %253F, and the = didn't turn into %253D like it did for me.

save and exit, then:

```
sudo /etc/init.d/cupsys restart
```

Now you can run ```
hp-toolbox
``` and the OfficeJet should show up in the list of printers.  You can print a test page from there (you can also print a test-page from the gnome Printers application if you like).

From the hp-toolbox you can now scan.  Click the "Scan..." button and it pops up xsane which works wonderfully.

From the hp-toolbox you can also check ink levels, change printer settings, align cartridges, clean cartridges, access photo cards, send faxes, etc., etc.  It's very nice.

---

