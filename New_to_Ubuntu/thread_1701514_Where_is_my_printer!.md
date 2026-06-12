---
title: "Where is my printer?!"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by MHC on 2011-03-06
I have Ubuntu 10.04 and a Brother MFC-5490CN printer/copier/scanner. This worked well, with an icon at the bottom right of the screen to access the Brother and tell it what I wanted to do. But since the latest Debian update, this icon has disappeared, and I don't know how to access the scanner. Can anyone help please?

---

### Post by maqtanim on 2011-03-06
Printer:
System > Administration > Printing

Scanner:
Applications > Graphics > Simple Scan

---

### Post by MHC on 2011-03-06
The printer works fine, so is still connected properly. But when I try the scanner, I get the message: 

No scanners detected
Please check your scanner is connected and powered on

On the right bottom of my screen there is now only the Chrome icon, where there also used to be the Brother suite one. Can I get that back?

---

### Post by maqtanim on 2011-03-07
I donot use Brother Printer so I am not sure actually what icon you are talking about. But it seems that you have installed the **brother suit** in the first place. Can you please tell how did you install that suit earlier?

---

### Post by MHC on 2011-03-08
That was done by the shop I bought the PC and printer from, and who installed Linux. They showed me the suite icon and said that is the best way to use the printer. This would show how much ink I had left for each color, and let me choose printing, copying or scanning. 

When I try scanning from the printer's console, it tells me I have to tell it the PC connection.  Yet it prints from the PC fine.

---

### Post by c_cinq on 2011-03-08
the scanner may not be supported.
[http://www.sane-project.org/sane-mfgs.html#Z-BROTHER](http://www.sane-project.org/sane-mfgs.html#Z-BROTHER)

---

### Post by plucky on 2011-03-08
From a terminal post output of ```
dpkg -l | grep Brother
``` to see if the scanner driver is still installed. (-l is lowercase L not a 1)

---

### Post by MHC on 2011-03-08
ii  brother-cups-wrapper-common            1.0.0-10-0ubuntu5                               Common files for Brother cups wrapper packages
ii  mfc5490cncupswrapper                   1.1.2-2                                         Brother CUPS Inkjet Printer Definitions
ii  mfc5490cnlpr                           1.1.2-2                                         Brother lpr Inkjet Printer Definitions

---

### Post by plucky on 2011-03-09
You only have the printer drivers installed,you need to install the scanner driver.

Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html) and download the correct .deb file for your scanner and install.

Make sure you read the prerequisites for the install and the installation instructions.

Good Luck

---

### Post by MHC on 2011-03-09
Great, thanks :D

---

