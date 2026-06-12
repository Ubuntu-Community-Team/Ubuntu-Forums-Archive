---
title: "help installing Brother MFC-420CN printer"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by hdenie on 2010-06-17
I recently downloaded and installed UBUNTU 
to attempt using my network Brother MFC-420CN printer, I folowed the next instructions 


Go to your toolbar,  System, Administration, Synaptic Package Manager

In Synaptic Package Manager(SPM) search for "Brother" 

No Brother is listed in the SPM search

Anybody outthere can help me to make it to show up in the search?

Hans

---

### Post by wintermoon on 2010-06-17
> **hdenie said:**
> I recently downloaded and installed UBUNTU 
to attempt using my network Brother MFC-420CN printer, I folowed the next instructions 


Go to your toolbar,  System, Administration, Synaptic Package Manager

In Synaptic Package Manager(SPM) search for "Brother" 

No Brother is listed in the SPM search

Anybody outthere can help me to make it to show up in the search?

Hans
Try going to System, Administration, Printing. Assuming you know your printer's hostname or IP address, you *might* be able to set it up from there. Good luck - network printer setup in Ubuntu is not easy (to say the least).

---

### Post by WinterRain on 2010-06-17
From Brother's website [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-420CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-420CN)

---

### Post by plucky on 2010-06-17
> **hdenie said:**
> I recently downloaded and installed UBUNTU 
to attempt using my network Brother MFC-420CN printer, I folowed the next instructions 


Go to your toolbar,  System, Administration, Synaptic Package Manager

In Synaptic Package Manager(SPM) search for "Brother" 

No Brother is listed in the SPM search

Anybody outthere can help me to make it to show up in the search?

Hans

Do you have the **Multiverse** repository enabled?

Open **System > Administration > Software Sources** and make sure the four repository boxes are ticked on the first page,then reload and see if it now shows up in SPM.

You have to install both the cupswrapper and LPR drivers.

The website also shows how to connect a network printer.


Good Luck

---

### Post by cjazz on 2010-06-17
In Synaptic, navigate to settings and then repositories. Make sure the box is checked next to "Software restricted by copyright or legal issues (multiverse."

---

### Post by ukripper on 2010-06-17
> **WinterRain said:**
> From Brother's website [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-420CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-420CN)

This ^^^

---

### Post by hdenie on 2010-06-17
Boy I have never seen such a response thank you all .

I reinstalled UBUNTU 10.04lts and was able to search, found and installed both files  "brother-cups-wrapper-extra" and "brothers-lpr-drivers-extra".
Both files have a green field and are marked as installed.
So far so good .
I click system/admin/printing
click "+", highlight " find network printer" and click on find .
It searches and it is unable to find my Brother MFC-420cn.
I repeated again by typing the network printer's IP address and again up comes the message, "No printer was found at that address"  
So I am stuck again.
Any suggestions

---

### Post by oldsoundguy on 2010-06-17
Have you gone to the computer that hosts the printer and enabled sharing?

IF NOT .. do so and re-boot BOTH machines.

---

### Post by hdenie on 2010-06-17
Thanks again I may start liking Ubuntu and become a apostle.
I Unpluged the printer, and replug, restart ubuntu
click "+", highlight " find network printer" and click on find .
It searches and ALAS it found and installed the drivers for my Brother MFC-420cn.

Not yet finished , I need some step by step guidance how to in-stall the scanning function
Any suggestions

---

### Post by oldsoundguy on 2010-06-17
Scanning requires a two way function.  From my understanding, scanning can only be done on the home computer.  I have two scanners and neither can be accessed in scan mode from any computer on my home net except the computers they are plugged into and that includes both Windows and Linux machines.

So I scan and save to the shared folder and pick THAT up at the final destination.

---

### Post by hdenie on 2010-06-17
> **oldsoundguy said:**
> Scanning requires a two way function.  From my understanding, scanning can only be done on the home computer.  I have two scanners and neither can be accessed in scan mode from any computer on my home net except the computers they are plugged into and that includes both Windows and Linux machines.

So I scan and save to the shared folder and pick THAT up at the final destination.

Thanks all of you at least I can print . 
I am sharing the computer with others on the network and with winxp it was no problem. I did find [http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)  and I got as far as step 4 .
At that point, I hoped "simple scan"would have found the scanner but it did not.
I did not want to continue with step 5 , because I got lost in the lingo which I am not yet familiar with.
Hope fully some one with the same printer will read this and off-coarse any help is appreciated .

Thanks to all

---

### Post by manny43 on 2010-06-17
GO TO Synaptic Package Manager in quick search type MFC-420CN and install brother-cups-wrapper extra

---

### Post by ukripper on 2010-06-18
> **hdenie said:**
> Thanks again I may start liking Ubuntu and become a apostle.
I Unpluged the printer, and replug, restart ubuntu
click "+", highlight " find network printer" and click on find .
It searches and ALAS it found and installed the drivers for my Brother MFC-420cn.

Not yet finished , I need some step by step guidance how to in-stall the scanning function
Any suggestions

When i had Brother printer about 2 years back that is how i used to install scanner, the below package should be included with the download of brother drivers:

Go to drivers directory and run in terminal:

```
sudo dpkg -i brscan2-0.0.1-0.i386.deb
```

edit the /etc/fstab file 

```
sudo gedit /etc/fstab
```

add the following line to the end of the file:


> none /proc/bus/usb usbfs auto,devmode=0666 0 0

save

modify the USB access control:

```
sudo umount /proc/bus/usb
```
```
sudo mount /proc/bus/usb
```
```
sudo mknod -m 666 /dev/usbscanner c 180 48
```

Your scanner should now be recognized by xSane when you navigate to Applications -> Graphics -> XSane.

Hope it works for you.

---

