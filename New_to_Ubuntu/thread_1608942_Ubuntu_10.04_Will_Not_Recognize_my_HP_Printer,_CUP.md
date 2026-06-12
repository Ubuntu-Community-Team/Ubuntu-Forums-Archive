---
title: "Ubuntu 10.04 Will Not Recognize my HP Printer, CUPS not enabled"
date: 2010-10-29
forum: New to Ubuntu
---

### Post by SignatureSeriesOwner on 2010-10-29
Hi all, This is a bit odd, to say the least. For over a month,  Linux did not recognize my HP Photosmart C3150 printer. Then, all of a sudden, for about 4 days, it did.  Now, it doesn't again.  Iam trying to troubleshoot the issue, and have no idea where to go, as I am still very new to Linux.  I use the Troubleshooting guide on the "Printing" page, and it says I need to go to System>Admin>Settings to enable it.  Great,  I go to System>Admin. and Settings is not on the list.  Is there another way to get to the CUPS section?  I tried using a command online (here) to download CUPS, but it failed. Said something about "Unable to lock directory" or something similar.


Any assistance would be much appreciated.

---

### Post by 73ckn797 on 2010-10-29
Install "hplip" from Synaptic.

---

### Post by SignatureSeriesOwner on 2010-10-29
I did, however, I cannot seem to find the PPD file I need for my printer to set it up. The setup detects the printer, but I cannot install it, due to the PPD issue.  I don't see any HP PhotoSmart printers listed there, period.

---

### Post by kelvinator on 2010-10-29
> **SignatureSeriesOwner said:**
> I did, however, I cannot seem to find the PPD file I need for my printer to set it up. The setup detects the printer, but I cannot install it, due to the PPD issue.  I don't see any HP PhotoSmart printers listed there, period.

I own a Photosmart wireless printer that worked flawlessly with the installation of hplip. I searched for your model at this link and found a link to the download that you would need:

[http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c3100_series.html](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c3100_series.html)

---

### Post by 73ckn797 on 2010-10-29
Is "hplip-gui" also installed? In Synaptic there are several other HP related packages.

---

### Post by SignatureSeriesOwner on 2010-10-31
HP-GUI was also installed, but it did not help.


Thank you Kelvinator, that download was exactly what I need.  Works great now!  Thank you!

---

