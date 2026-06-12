---
title: "Printing"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by April1212 on 2009-09-15
I have a MFC-240C Brother printer.. and for some reason i cant get my computer to register and connect with my printer? My printers saying that it is receiving data but nothing is printing? Can anyone help me?

Thanks April

---

### Post by durand on 2009-09-15
It sounds like a problem at the printer's end if it recieves the data successfully. When you go to System > Administration > Printing (I think), can you see the printer properly? If you plug it in, does the status show any error? I can't be more specific because I'm not on ubuntu at the moment. You could try testing printing on another OS, like windows if you have it?

---

### Post by plucky on 2009-09-15
> **April1212 said:**
> I have a MFC-240C Brother printer.. and for some reason i cant get my computer to register and connect with my printer? My printers saying that it is receiving data but nothing is printing? Can anyone help me?

Thanks April

Have you installed the drivers?

Open **Synaptic Package Manager** and search for "MFC-240C" and you should find "brother-cups-wrapper-bh7" and "brother-lpr-drivers-bh7".

Select both and apply.

After they are installed,power on your printer and plug in USB cable,open **System > Administration > Printing** and select new printer.You then have to select the correct driver and install.

The printer should then work.


A good troubleshooting tool is to open the cups interface in Firefox.Just type this into the address bar ```
http://localhost:631/
```

Good Luck

---

