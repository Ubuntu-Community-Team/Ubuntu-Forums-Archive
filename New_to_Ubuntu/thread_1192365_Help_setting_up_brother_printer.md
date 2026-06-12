---
title: "Help setting up brother printer"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by ja660k on 2009-06-20
hey guys, 
I have a brother MFC-260C printer 
and i cant seem to find drivers for it anywhere. 
i still have the winblows partition on my laptop but i dont if/where the driver is on it.

can anyone help, i would need step by step instruction cos i have tried a few ways with no solution

Thanks :D

---

### Post by roger_1960 on 2009-06-20
Hi

Try looking here

[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-260C](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-260C)

The brother site is quite good and has got my brother all-in one working (different to yours)

---

### Post by plucky on 2009-06-20
> **ja660k said:**
> hey guys, 
I have a brother MFC-260C printer 
and i cant seem to find drivers for it anywhere. 
i still have the winblows partition on my laptop but i dont if/where the driver is on it.

can anyone help, i would need step by step instruction cos i have tried a few ways with no solution

Thanks :D

Open **Synaptic Package Manager** and search for **mfc-260c** and you should get "brother-cups-wrapper-extra" and "brother-lpr-drivers-extra".Tick the boxes and apply,will install the drivers.

Plug in the printer and power on and then go to **System > Administration > Printing** and select new printer.The system should then find and install your printer.


A good troubleshooting tool is to use Firefox browser to access the CUPS web interface.Just put ```
http://localhost:631
``` into the address bar will open the CUPS web interface.

Good Luck

---

### Post by jenelle on 2009-06-20
talking printers i know that my sisters cannon 160 won't work on this system as i have read others have found this too .

what brands of printers do i see brother does what others ? and what does not any others other then cannon ?? please thanks i want a printer but don't want to get it home to find it does not work with my computer

---

### Post by Scunnered on 2009-06-20
**jenelle**

Best point of contact for printing information is Linux Printing. There is an extensive list of manufacturers and printers listed.  Work only on the works perfectly list and all should be well.

---

### Post by CLomax on 2009-06-20
[http://www.uluga.ubuntuforums.org/showthread.php?t=590793](http://www.uluga.ubuntuforums.org/showthread.php?t=590793)

---

### Post by jenelle on 2009-06-20
> **Scunnered said:**
> **jenelle**

Best point of contact for printing information is Linux Printing. There is an extensive list of manufacturers and printers listed.  Work only on the works perfectly list and all should be well.

cool thanks :D 
now do i find that list in the add and remove  button of my computer ? sorry i am still finding my way around

---

### Post by plucky on 2009-06-20
> **jenelle said:**
> cool thanks :D 
now do i find that list in the add and remove  button of my computer ? sorry i am still finding my way around


[Click Here](http://www.linuxfoundation.org/en/OpenPrinting)

Good Luck

---

### Post by jenelle on 2009-06-20
> **plucky said:**
> [Click Here](http://www.linuxfoundation.org/en/OpenPrinting)

Good Luck

Thank you very much book marked list page for when i find a printer i can afford and check with the list :D

---

### Post by ja660k on 2009-06-20
> **plucky said:**
> Open **Synaptic Package Manager** and search for **mfc-260c** and you should get "brother-cups-wrapper-extra" and "brother-lpr-drivers-extra".Tick the boxes and apply,will install the drivers.

Plug in the printer and power on and then go to **System > Administration > Printing** and select new printer.The system should then find and install your printer.


A good troubleshooting tool is to use Firefox browser to access the CUPS web interface.Just put ```
http://localhost:631
``` into the address bar will open the CUPS web interface.

Good Luck

thankyou so much!!!

---

