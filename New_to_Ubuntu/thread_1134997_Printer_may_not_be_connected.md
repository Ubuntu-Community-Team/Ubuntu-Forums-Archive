---
title: "Printer may not be connected"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Scunnered on 2009-04-24
Yesterday I accepted the Update Manager offering and am now working with Jaunty and immediately I have a problem.  I attempted to print only to receive the above message. The printer is correctly identified by manufacturer and name and shows when I check System > Administration > Printing. The print queue identified that a page was partially printing showing 17% but despite this statement nothing was happening.

I used the troubleshoot option on the printer only to discover that this only confirmed the error.  I append the text file of the outcome for your info and trust this assists

PS have made another 2 attempts to print and in each case all fails. The printer accepts what is offered and shows the item being sent in each instance. When checking the items are sitting in the print queue

---

### Post by gettinoriginal on 2009-04-24
I had the same problem after a clean install of Jaunty.  Mine was the result of Jaunty recognizing the printer, but only functioning as root.  I went into System > Admin > Users and Groups, and added myself to the root group, now all works fine.

---

### Post by Scunnered on 2009-04-25
Many thanks for your kind reply.  I had a look at this and found that I was unable to make any change on my system.  No doubt I am not doing something right.

Can you please advise how I effect this change.

Many thanks

---

### Post by Screwdriver0815 on 2009-04-25
> **Scunnered said:**
> Many thanks for your kind reply.  I had a look at this and found that I was unable to make any change on my system.  No doubt I am not doing something right.

Can you please advise how I effect this change.

Many thanks

you can do it on two ways:

either: 

you go to "SYstem" -> Administration -> Users and Groups 

then a dialogue will be opened where you can choose your username. Click on "unlock" and then choose your username and click on "properties". Then click on the tab "permissions" and set the hook for the category printers.

(Maybe the text in the menus is a little bit different as I have another language on the system.)

or:

you open a terminal and type into it:

```
sudo adduser yourusername printer
``` 

you have to replace "yourusername" with your actual username which you are using in the system.

You will be asked for the password and then you will be added to the printers-group.

But maybe the rootcause for your problem is a different one?

if you switch on the printer and type 

```
lsusb
``` 

into the terminal (assuming its a usb-printer, you have) you can see the USB-port which it is connected to.
Then you open a web browser and type into the address bar:  [http://localhost:631](http://localhost:631) 

After that the CUPS configuration menu comes up. When you go to "manage printers" (or similar) you can check, if the printer has the same USB-port in there. If not, you should try to change it to the one "lsusb" has printed out.

---

### Post by Scunnered on 2009-04-26
**Screwdriver0815**

Thanks for your suggestions.  I have tried these but am no further forward.

Firstly I followed user groups and clicking in name lonin name home/name and unlocking and properties I found user privileges and in this secton found that configure printers was ticked.  I closed this section and tried printing again only to have the same error message.

I then used the sudo option and this resulted in "adduser: The group `printer' does not exist."

Finally using lsusb displayed

"Bus 002 Device 003: ID 04b8:0007 Seiko Epson Corp. Printer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub"

which only adds to the confusion.

From looking at the default printer and printing sections it clearly shows that the printer has been identified by CUPS.  I add a further 2 screenshots in the hope that this may be of assistance.

I hope this may assist you in solving this problem for me as I am keen to work with Jaunty as the wireless connection is excellent and beats 8.10 hands down.

Once again my sincere thanks for your kind assistance

---

### Post by Screwdriver0815 on 2009-04-26
okay, then try in the terminal

```
groups
```

and check if the output says "plugdev" and "lpadmin". If not, then add yourself to the plugdev-group and to the lpadmin-group:

```
sudo adduser yourusername plugdev lpadmin
```

restart and try again. 

if this doesn't work too, I come to the end of my knowledge and experience... the only thing I would try then, would be the windows-way: uninstall the printerdriver, restart, re-install the printerdriver with the printer switched off.

maybe someone else has some better ideas

---

### Post by Scunnered on 2009-04-26
**Screwdriver0815**

My sincere thanks to you, the problem is now solved.  Followed your 2 points and re-booted - did not work.  Finally deleted printer and rebooted. Printer immediately listed and this time worked OK.

Once again thanks.

---

