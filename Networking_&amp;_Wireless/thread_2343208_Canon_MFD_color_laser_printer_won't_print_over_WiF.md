---
title: "Canon MFD color laser printer won't print over WiFi"
date: 2016-11-14
forum: Networking &amp; Wireless
---

### Post by lozowy-gmail on 2016-11-14
Hello,

I just bought a Canon i-SENSYS MF724Cdw color laser printer for use via a local wireless network.
Checked the printer, it prints on its own and scans, all good there (very nice quality, btw).
My x64-bit computer is on Ubuntu 16.04.
I downloaded the printer driver from the Canon Web site and installed it, fired up the printer and connected it successfully to the WiFi router. A blue light below the LED screen is always on, indicating that the wireless connection is active.
Then I found the printer from my computer and connected to it, also successfully. I located the printer's IP address on its panel and entered that into my computer's browser and I can see the printer, check and change its settings, see its log of print jobs, etc. But when I try to print -- both from a text editor and as a "Print test page" from the "Printer Properties" panel -- the printer gives a very brief "beep" and nothing prints. When I checked the print job log via my computer's browser, that showed that all the wireless network print requests had returned an error, the same one: "#822". This is strange because, apparently, this error code is for:
[COLOR=#353535][FONT=&amp][COLOR=#D02B14]**An image file in a USB memory device could not be printed because the format of the image file is not supported.**[/COLOR][/FONT][/COLOR]
[COLOR=#353535][FONT=&amp]Check the supported file formats and save the file again.[/FONT][/COLOR]
[COLOR=#353535][FONT=&amp][Printing from USB Memory (USB Print)]("http://ug.oipsrv.net/eu-af-me-ru/manual/USRMA-0340-zz/contents/SS729_print_133printingfromusbmemoryusbprint.html#06020000")[/FONT][/COLOR]
(from [http://ug.oipsrv.net/eu-af-me-ru/manual/USRMA-0340-zz/contents/SS729_troubleshooting_291whenanerrorcodeappears.html](http://ug.oipsrv.net/eu-af-me-ru/manual/USRMA-0340-zz/contents/SS729_troubleshooting_291whenanerrorcodeappears.html))

Yet I am not printing from a USB memory device at all, but rather via a wireless network.
I tried going through the configurations, but both on the printer itself and on my computer there are probably over a hundred configuration options, so I am lost.

Any advice would be greatly appreciated.

---

