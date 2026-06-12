---
title: "Epson DX7400 Problems with Lucid"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by Peterfc on 2010-06-10
Hi 

Since updating to Lucid and applying all updates as they arrive i have had a problem with my usb devices.

The only way i can find my Usb devices is to go to System then administration and then Disk Utilities. Then i can open my device.

I have an Epson Dx7400 Multi Function device. This device is listed in the Administration then Printing the device is found in the printing option.

When i go to Applications Graphics and simple scan then I get no scanner detected.

If i use Xsane image scanner i get No devices available 


If i go to the [http://www.sane-project.org/man/sane-epson2.5.html](http://www.sane-project.org/man/sane-epson2.5.html) then it says that the device is  At present, the following scanners are known to work with this backend:

Thanks

---

### Post by ellgor on 2010-06-10
Hi,

Go to the "Avasys" site and get their Imagescan package, go through the form filling in bit and when you get to the download page scroll right down until you see "Iscan or Imagescan deb" which is a completely seperate app  from the full printing package, once downloaded use gdebi to automatically install it, needs a reboot to work properly.  

Regards, Ellgor.

---

### Post by Peterfc on 2010-06-10
Thanks Ellgor

Job sorted 

Thanks

---

### Post by alecive on 2010-09-16
Hi! sorry if I resume this thread, but I went on avasys home and then i clicked on "linux drivers" (i.e. here: [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)). Now I searched my model under "inkjet printers" and "multifuncion" but I cannot find it!

My model is the same of the thread title (epson DX7400)

Thanks for any help!

---

### Post by sisco311 on 2010-09-16
> **alecive said:**
> Hi! sorry if I resume this thread, but I went on avasys home and then i clicked on "linux drivers" (i.e. here: [http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)). Now I searched my model under "inkjet printers" and "multifuncion" but I cannot find it!

My model is the same of the thread title (epson DX7400)

Thanks for any help!

DX7400 is an All-in-One "Multifunction Inkjet Printer":

[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

---

