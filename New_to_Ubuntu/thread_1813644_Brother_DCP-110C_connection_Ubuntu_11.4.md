---
title: "Brother DCP-110C connection Ubuntu 11.4"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by jobrimal on 2011-07-28
[FONT="Garamond"][SIZE="4"]**[/SIZE][/FONT]

Hello there,
           I am a newbie on XP/UBUNTU 11.4, XP no problem.
BUT.How do I connect my Brother DCP-110C Printer to the
11.4 side of my computerhttp://ubuntuforums.org/images/smilies/confused.gif
my wish is to phase out the XP,But no joy if I cannot connect Printer to Ubuntu.
      Have fun jobrimal.

---

### Post by plucky on 2011-07-28
> **jobrimal said:**
> [FONT="Garamond"][SIZE="4"]**[/SIZE][/FONT]

Hello there,
           I am a newbie on XP/UBUNTU 11.4, XP no problem.
BUT.How do I connect my Brother DCP-110C Printer to the
11.4 side of my computerhttp://ubuntuforums.org/images/smilies/confused.gif
my wish is to phase out the XP,But no joy if I cannot connect Printer to Ubuntu.
      Have fun jobrimal.

Welcome to the Forum.

You need to install the drivers for your printer.

Open Synaptic Package Manager and search for **dcp-110c** and it should find ```
brother-cups-wrapper-extra
brother-lpr-drivers-extra
```

Mark both for installation and Apply.

Then Connect the printer to a USB port and power on.
Go To **System > Administration > Printing** and Add a new printer and it should then go and look for drivers.Select the ones for your printer.

Useful Links

[Brother Linux Drivers](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

[Brother Driver Packaging](https://wiki.ubuntu.com/BrotherDriverPackaging)


If your printer has a scanner,you will have to download the correct scanner driver from the Brother Website and install.Instructions are on the website.

Good Luck

---

### Post by jobrimal on 2011-08-01
*[FONT="Garamond"][SIZE="3"][/SIZE][/FONT]*Thank you plucky you have been a great help:phttp://ubuntuforums.org/images/smilies/icon_razz.gifHowever I came to a full stop when my TERMINAL refused to accept my password,the same password that I logged on with!!!!

---

### Post by plucky on 2011-08-02
> **jobrimal said:**
> *[FONT="Garamond"][SIZE="3"][/SIZE][/FONT]*Thank you plucky you have been a great help:phttp://ubuntuforums.org/images/smilies/icon_razz.gifHowever I came to a full stop when my TERMINAL refused to accept my password,the same password that I logged on with!!!!

The Terminal does not echo anything as you type in your password,just type it in and press **Enter**.

Does your password still work with Synaptic Package Manager or Update Manager?

---

### Post by jobrimal on 2011-08-04
[FONT="Georgia"][SIZE="3"]**[/SIZE][/FONT]

Hi plucky,
         yes my password works in both,I also logon with the same
password.
       have fun,jobrimal

---

