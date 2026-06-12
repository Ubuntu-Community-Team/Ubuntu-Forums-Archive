---
title: "can't install Brother printer DPC-197C"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by Petronius on 2011-05-23
I have tried to add a Brother printer DPC-197C. It appears to detect and install, but in "Make & Model" it says DCP-1200 Footmatic/hl1250 which seems to be some kind of Poscript printer. Is it perhaps that there is no driver for this model (a combined printer/scanner/copier) and that it just does its best?

---

### Post by Fedz on 2011-05-23
Hi, are you saying your DPC-197C doesn't work with what Ubuntu has installed?

---

### Post by ajgreeny on 2011-05-23
What have you installed, if anything, in order to use the printer?  A quick look on the brother website does not seem to help, so I suspect there are no drivers available for that model.
[http://www.brother-store.co.uk/category/brother-linux-printer-fax-dcp-mfc-software-drivers_MjQzMg==.html](http://www.brother-store.co.uk/category/brother-linux-printer-fax-dcp-mfc-software-drivers_MjQzMg==.html)

---

### Post by Petronius on 2011-05-24
> **Fedz said:**
> Hi, are you saying your DPC-197C doesn't work with what Ubuntu has installed?
Yes.

---

### Post by Petronius on 2011-05-24
> **ajgreeny said:**
> What have you installed, if anything, in order to use the printer?  A quick look on the brother website does not seem to help, so I suspect there are no drivers available for that model.
[http://www.brother-store.co.uk/category/brother-linux-printer-fax-dcp-mfc-software-drivers_MjQzMg==.html](http://www.brother-store.co.uk/category/brother-linux-printer-fax-dcp-mfc-software-drivers_MjQzMg==.html)
I didn't install anything. I couldn't find anything on the Brother site or Linux forums either. Perhaps Brother doesn't support this printer on Linux. Do you know if there is a Brother/Linux forum I should try? I can still print by tranferring my documents to a memory stick and printing on a Windows machine. Makes Linux a bit useless though.

---

### Post by migs73 on 2011-05-24
Here is the link to the Brother site listing all the printers they support with linux drivers.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)

Unfortunately yours is not there. You could find driver for a similar machine and try that. This at best would only give limited functionality.
I think the best bet would be to contact them directly (Brother support) and ask if hey are working on a Linux driver for that model, as new ones seem to be added quite often.

Regards

Mike

---

### Post by walt.smith1960 on 2011-05-24
I wonder how close the DCP195C is? If you are using 32 bit Ubuntu it's pretty easy to try installing DCP195C software if you're so inclined.  Scanner software is a separate install with Brother & Linux.

---

### Post by Petronius on 2011-05-24
> **walt.smith1960 said:**
> I wonder how close the DCP195C is? If you are using 32 bit Ubuntu it's pretty easy to try installing DCP195C software if you're so inclined.  Scanner software is a separate install with Brother & Linux.
Ah... thanks. The trouble is I am not even an atom removed from absolute beginner on linux, and a quick look shows me that is would be impossibly complicated for me to attempt an install. E.g concepts like lpr drivers, cups, super-user and so on, and using the terminal is something Windows (and I) left behind years ago (and I don't want to go back to!)

Has Ubuntu no graphics interface for installing drivers (or indeed a right click menu to delete them?)

I might email Brother support, that's a good idea. An even better idea might be to dump my Ubuntu netbook and buy a Windows one. After all it's only for travelling and I understand Windows. 

As an operating system I really, really like the basic simplicity of Ubuntu, but the issue of adding peripherals just seems to always be a stumbling block.

---

### Post by walt.smith1960 on 2011-05-24
I cannot address your device but I've installed two of my own Brother devices.  If you have 32 bit Ubuntu, there is indeed a graphical installer--two, actually.  One is included-Ubuntu software center-located in Applications if your using 10.10 or earlier. Ubuntu software center can be prickly about installing apps not from the Ubuntu repositories.  I also use Gdebi found in synaptic.  Do use caution about installing .deb files (much like .exe files in Windows).  Use only those from reputable sources because a .deb file can be malicious just as an .exe file can.

Brother is a a pain because they include pre-install instructions for .rpm and .deb installers in the same file.  Ubuntu is based on Debian and uses .deb files. I printed them out and crossed out those that don't apply.   I've found that only two commands need to be executed from the terminal:

**1. "sudo aa-complain cupsd"** command is required before the installation.[B]
2. "sudo mkdir /usr/share/cups/model"[/B] command (as it is) is required before the installation.

I'm not even certain these are necessary but there seems to be no harm in them.  There are two .deb files required. The first is the LPR file then the cupswrapper file.  Right-click on the downloaded .deb file and select "open with Gdebi" or words to that effect.  The printer should install then appear under System-> Administration ->Printing.  If you have a USB cable connected, it should establish the connection automatically. Installing the scanner should be similar.  Let us know how you get on please.

Edit:  If you get an error message mentioning architecture, you probably have a 64 bit OS installed.  You can still install but can't use the graphical installer, you must install from the command line and override the "but this is a 32 bit application!!" warning.  It will still function but is more involved.

---

### Post by Fedz on 2011-05-24
I have seperate printer scanner but, my printer (make/model) wasn't supported in Ubuntu so I installed the one nearest to it which was a model below. Luckily it worked - notably better than Windows lol

The scanner wasn't supported by Ubuntu at all but, figured if you copy the **.**usb from the scanners installation disk (or unpack the .zip if downloaded) then install it in XSane override config folder it worked a dream lol

Both now fully function & Ubuntu's gui is seriously better than the Windows installs :)

You can have a pop at it you want with yours, forum members will happily walk you through it if you're up for it but, if you don't feel confident enough that's fine. Things sound harder than they usually are :)

---

### Post by migs73 on 2011-05-24
> **walt.smith1960 said:**
> I cannot address your device but I've installed two of my own Brother devices.  If you have 32 bit Ubuntu, there is indeed a graphical installer--two, actually.  One is included-Ubuntu software center-located in Applications if your using 10.10 or earlier. Ubuntu software center can be prickly about installing apps not from the Ubuntu repositories.  I also use Gdebi found in synaptic.  Do use caution about installing .deb files (much like .exe files in Windows).  Use only those from reputable sources because a .deb file can be malicious just as an .exe file can.

Brother is a a pain because they include pre-install instructions for .rpm and .deb installers in the same file.  Ubuntu is based on Debian and uses .deb files. I printed them out and crossed out those that don't apply.   I've found that only two commands need to be executed from the terminal:

**1. "sudo aa-complain cupsd"** command is required before the installation.[B]
2. "sudo mkdir /usr/share/cups/model"[/B] command (as it is) is required before the installation.

I'm not even certain these are necessary but there seems to be no harm in them.  There are two .deb files required. The first is the LPR file then the cupswrapper file.  Right-click on the downloaded .deb file and select "open with Gdebi" or words to that effect.  The printer should install then appear under System-> Administration ->Printing.  If you have a USB cable connected, it should establish the connection automatically. Installing the scanner should be similar.  Let us know how you get on please.

Edit:  If you get an error message mentioning architecture, you probably have a 64 bit OS installed.  You can still install but can't use the graphical installer, you must install from the command line and override the "but this is a 32 bit application!!" warning.  It will still function but is more involved.

That is pretty much how I installed my driver too (MFC-255CW), the 'open with Gdebi' I'm sure is replaced now (since 10.04?) with 'open with Ubuntu Software Centre'. This does the same thing. 

BTW the Gdebi and USC both extract all the files in the .deb package and install them all into the correct folders. The reason the Brother website uses the CLI method, is that not all people use Ubuntu and other Debian based os's will require the CLI install method.

---

### Post by walt.smith1960 on 2011-05-24
> **migs73 said:**
> That is pretty much how I installed my driver too (MFC-255CW), the 'open with Gdebi' I'm sure is replaced now (since 10.04?) with 'open with Ubuntu Software Centre'. This does the same thing. 

BTW the Gdebi and USC both extract all the files in the .deb package and install them all into the correct folders. The reason the Brother website uses the CLI method, is that not all people use Ubuntu and other Debian based os's will require the CLI install method.

Makes perfect sense.  I tried to install something with the Software Center and got a message along the lines of "This doesn't meet our standards; we won't install it".  Better safe than sorry, I guess so I used Gdebi. I was pretty frustrated by the terminal until I discovered the wonders of cut & paste into terminal :).  I think the most frustrated I've ever been with Ubuntu is when I was starting out and trying to cd to desktop and got a "directory does not exist" message.  I knew bloody well that it DID exist. Eventually I figured out that unlike DOS/Windows, letter case DOES matter.:redface:

---

### Post by migs73 on 2011-05-24
> **walt.smith1960 said:**
>  I think the most frustrated I've ever been with Ubuntu is when I was starting out and trying to cd to desktop and got a "directory does not exist" message.  I knew bloody well that it DID exist. Eventually I figured out that unlike DOS/Windows, letter case DOES matter.:redface:

Lol...been there done that.

Who the hell decided to name the default directory with a capital 'D' anyway?

I find instead of cut and paste, I use the select then middle click to paste selected text extremely useful. Wish they had that in MS, I keep trying to use it in XP. :(

Mike

---

### Post by Petronius on 2011-05-25
In view of the relative completity of all this (relative to my beginner status on linux) I feel I should maybe take another tack, and try to wireless connect my netbook to my Windows 7 computer to try to print from my netbbook via my Windows connected Brother printer.

---

