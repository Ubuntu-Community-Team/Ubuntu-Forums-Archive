---
title: "Simple Scanner for Lucid?"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by Primus1 on 2010-06-10
Hi, anyone in the uk using a scanner that works well with Lucid? Just a standard low end scanner. My old one is not supported (xerox 2400).

Thanks.

---

### Post by alphacrucis2 on 2010-06-10
> **Primus1 said:**
> Hi, anyone in the uk using a scanner that works well with Lucid? Just a standard low end scanner. My old one is not supported (xerox 2400).

Thanks.

This might help:

[http://www.sane-project.org/sane-mfgs.html]("http://www.sane-project.org/sane-mfgs.html")

---

### Post by fatality_uk on 2010-06-10
That is an old scanner. Assuming it is connected via USB, what is the reuslt if you type **lsusb** into the terminal?

---

### Post by redbook4574 on 2010-06-10
> **Primus1 said:**
> Hi, anyone in the uk using a scanner that works well with Lucid? Just a standard low end scanner. My old one is not supported (xerox 2400).

Thanks.


To be honest I don't know of any standalone scanners anymore although I'm sure they exist, but I do find that cheap HP all in ones work great, I personally use the deskjet f4280 which cost me about £30.

---

### Post by howefield on 2010-06-10
> **Primus1 said:**
> a scanner that works well with Lucid?

Epson Perfection 1260 works flawlessly. Probably unavailable now, it is about 5 years old.

---

### Post by Primus1 on 2010-06-10
Hi alphacrucis2, lsusb: Bus 004 Device 002: ID 0461:038b Primax Electronics, Ltd Xerox 2400 Onetouch.

Yes it's an old scanner, I only need one to scan letters, documents, a few photos that's all, don't need anything fancy.

@ redbook4574, can't see deskjet f4280 listed, still if it works with Lucid I'll look into it, thanks.
@ howefield, will check out the Epson too, thanks.

Cheers guys.

---

### Post by Paddy Landau on 2010-06-10
I've had fantastic experience with HP. Check them out too.

---

### Post by crispy_420 on 2010-06-10
I second just about any cheap HP all-in-one. Don't know if it has gotten popular over there yet but you can look at craigslist for a used scanner and check compatibility with the SANE project.

---

### Post by Primus1 on 2010-06-10
Thanks, will check it out.

---

### Post by kaibob on 2010-06-11
I received an Epson Perfection V30 scanner about a week ago and have been happy with it so far. The price in the US is about $80.00. I just checked the Epson UK site, and it is available. You can find some of my thoughts on this scanner at:

[http://ubuntuforums.org/showthread.php?t=1447789](http://ubuntuforums.org/showthread.php?t=1447789)

---

### Post by anewguy on 2010-06-11
Do me a favor and try running xsane from a terminal as sudo xsane - if it finds the scanner then let us know.

Dave ;)

---

### Post by rajeev1204 on 2010-06-11
I vouch for hp all in ones too, they all work simple and easy.

---

### Post by lemmy999 on 2010-06-11
I use an Epson CX3200 and it scans and prints superbly OOTB with 10.4.

There's a couple of them on Ebay currently for very little money.

---

### Post by Primus1 on 2010-06-11
Thanks for all the replies. I really only want a scanner rather than an all-in-one, just for scanning documents, but will look at all the leads given here, thanks for the help all.

---

### Post by rajeev1204 on 2010-06-11
What everyone is saying is that, if you stick with the brands known to work with linux, then standalone scanners also should work as good.

---

### Post by Primus1 on 2010-06-11
This page:
 [http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)
has each make with results from 'unsupported' to 'complete'.

---

### Post by rajeev1204 on 2010-06-11
> **Primus1 said:**
> This page:
 [http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)
has each make with results from 'unsupported' to 'complete'.


Complete of course means it supports all scanning / color options etc. 

Is there a particular model you have liked aand want to pick up ? Maybe print this page and carry it along so you can be sure .

HP , epson seem a safe bet.

Or if possible, take a ubuntu laptop and do a scan and see how that works.

---

### Post by Primus1 on 2010-06-11
No particular model Rageev, just a simple scanner. It's just that within the makes, eg Epson, some work and some don't, so it's a roll of the dice. Good idea to take a print of the information, thanks I'll do that :).

---

### Post by anewguy on 2010-06-13
Please provide the information I requested - there is a valid reason for wanting it.  Some USB devices, and in the past this has included some scanners, etc., get mounted with root only priviledges.  This means that the "normal" users won't be able to even see the printer.  That is why I wanted you to try running xsane as super user in a terminal window - if you are able to see the scanner then it would indicate a permissions problem we can fix easily.  So, if you try it and are able to see the scanner, then please also post back the output of:

sudo lsusb

Thanks

Dave ;)

---

### Post by Primus1 on 2010-06-14
> **anewguy said:**
> Do me a favor and try running xsane from a terminal as sudo xsane - if it finds the scanner then let us know.

Dave ;)

"You try to run XSane as ROOT, that really is DANGEROUS!
Do not send any bug reports when you
have any problems while running XSane as root:
YOU ARE ALONE!"

I'm sure you are wishing to help me but the above is the result when I typed your request into the Terminal. The warning couldn't be more *explicit*. As a complete beginner I hope you can see my *dilema*.

Perhaps you have not noticed, I typed lsusb in the terminal and posted the result on page 1.

Thanks .

---

### Post by desertdog on 2010-06-22
I might be able to help you get your Xerox 2400 scanner working with Ubuntu.

I have reason to believe that it may be a clone of another scanner (MD5345), which is already supported by the genesys backend.

To test this hypothesis, you would need to download and compile the sane source code, then edit a couple of lines of code in a few places, then compile the source code a second time.

This wiki describes how to download and compile the latest source code. [https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)

Then to "hijack" the MD5345 settings, there are a couple of lines of code to edit in the files /etc/sane.d/genesys.conf and ~/sane-backends/backend/genesys_devices.c. (Basically change usb id of the md5345 from 0x0461/0x0377 to 0x461/0x038b). Then recompile.  If you are interested in trying, I can write up a more complete tutorial.

Edit:
There is now a wiki that explains how to check to see if your scanner is a clone of a supported scanner at [https://help.ubuntu.com/community/CheckIfScannerIsClone](https://help.ubuntu.com/community/CheckIfScannerIsClone). Let us know if it works or if you need help.

---

