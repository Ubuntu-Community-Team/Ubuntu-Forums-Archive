---
title: "SANE command for duplex scanning"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by topler on 2011-01-19
Hi everyone!

I have got a Canon P-150 scanner which works perfectly fine with Ubuntu 32-bit and Xsane. With Xsane I'm able to scan as many pages (via Automated Document Feeder) were it also scans both sides with one pass.

My problem is that I would like to do the same via command line. As far as I understand, XSANE is a GUI which is build on SANE. However, I'm not able to find a command line parameter to scan in duplex mode, neither can I explicidly access the upper nor the lower scanner.

Does SANE support duplex scanning?
Is there a possiblity to listen to what SANE receives from XSANE while running a sample/ test scan?

Thank you for your help!

---

### Post by wep940 on 2011-01-20
What happens when you put --duplex on the end of the command line?

---

### Post by topler on 2011-01-20
> **wep940 said:**
> What happens when you put --duplex on the end of the command line?

It says: scanimage: unrecognized option '--duplex'

---

### Post by wep940 on 2011-01-20
In searching the net, I've also found reference to specifying the source as "ADF Duplex" - perhaps that might work.

---

### Post by topler on 2011-01-21
I finally got to the bottom of it. To be honest, before writing this post I had searched the Internet up and down and checked dozens of possible parameter combinations without success. After all, it seems I should have better read the Man page for Scanimage comprehensively rather than only skimming through it.

To get to the point, SANEs Scanimage function has general and device specific parameters. The parameter for duplex scanning and some other stuff is depending on the scanner. To retrieve a full list of available parameters do the following.

Retrieve the device ID    Note: In my case it said "device `canondr:libusb:002:002' is a Canon P-150 sheetfed scanner"
$ scanimage -L           

Use the device ID to retrieve the list of available parameters
$ scanimage --help --device-name canondr:libusb:002:002

It will print out a long list of available parameters. Below are the two key parameters to make duplex scanning work for me.

-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format

    --ScanMode Simplex|Duplex [Simplex]
        scanmode,choose simplex or duplex scan

The command below scans both sides with one pass and saves the output files out1.tif, out2.tif and so on .......
scanimage -d canondr:libusb:002:002 --ScanMode Duplex --resolution 100 --format=tiff -b

---

### Post by wep940 on 2011-01-21
Glad you got it working, and the information you found will be helpful to a lot of people.  Sorry I couldn't be of more help to you.

---

