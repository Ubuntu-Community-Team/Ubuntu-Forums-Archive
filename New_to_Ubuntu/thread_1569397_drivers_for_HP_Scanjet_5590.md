---
title: "drivers for HP Scanjet 5590"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by JuliaHenson on 2010-09-06
Dear Sirs,
I am a total neophyte and am not a programmer, unfortunately.  I have a slight brain injury from a car accident, which certainly doesn't help.

I have been unable to get a decent scan from either XSane or SimpleScan, since I purchased a new computer using only Linux Ubuntu.  Right now, I have 10.04 LTS.  I use my scanner for _everything_ in my life.  

I did a search for this scanner, and even the supposedly already titled "scanning with HP scanners or???", said there was nothing.  I probably don't know how to use this, nor will my brain cooperate with me.

I have had this computer for about 2 months and am desperate to find a way to use my scanner adequately.  The quality of the scan is so poor that it is worth virtually nothing.  I am so frustrated at this point, that I am probably not expressing myself correctly.

But please - is there really a way to make my scanner create _good_ scans with Linux?  Does anybody know and if so, is it possible to give me enough detail to allow me to do it?

Thank you,
Julia Henson
Ubuntu 10.04 LTS Lucid Lynx
ASUS M4A79T Deluxe Motherboard, AMD Phenom II Multi-Core Processor, 4GB DIMM RAM, Zogis GEForce 9400 (NVIDIA)

---

### Post by sandyd on 2010-09-06
> **JuliaHenson said:**
> Dear Sirs,
I am a total neophyte and am not a programmer, unfortunately.  I have a slight brain injury from a car accident, which certainly doesn't help.

I have been unable to get a decent scan from either XSane or SimpleScan, since I purchased a new computer using only Linux Ubuntu.  Right now, I have 10.04 LTS.  I use my scanner for _everything_ in my life.  

I did a search for this scanner, and even the supposedly already titled "scanning with HP scanners or???", said there was nothing.  I probably don't know how to use this, nor will my brain cooperate with me.

I have had this computer for about 2 months and am desperate to find a way to use my scanner adequately.  The quality of the scan is so poor that it is worth virtually nothing.  I am so frustrated at this point, that I am probably not expressing myself correctly.

But please - is there really a way to make my scanner create _good_ scans with Linux?  Does anybody know and if so, is it possible to give me enough detail to allow me to do it?

Thank you,
Julia Henson
Ubuntu 10.04 LTS Lucid Lynx
ASUS M4A79T Deluxe Motherboard, AMD Phenom II Multi-Core Processor, 4GB DIMM RAM, Zogis GEForce 9400 (NVIDIA)
Try increasing the scan resolution (indicated by the black arrow)

---

### Post by thatguruguy on 2010-09-06
Also, in SimpleScan you can change the default dpi (dots per inch) by clicking on "Document" in the top menu and then "Preferences".  The higher dpi, the better scan you will get.

Other than that, I must admit that I am unfamiliar with the HP Scanject 5590.  However, I use an HP OfficeJet 6500 all-in-one, and the drivers that came with ubuntu work flawlessly.

---

### Post by JuliaHenson on 2010-09-07
Thank you both for your responses.  However, I am already using the highest resolution in every place imaginable - SimpleScan and XSane.  I am using whatever is highest both in the software and in my printer and the darkest print in my printer.  
When I have a light copy, it simply can't do it.  Many documents I get simply are not dark - some barely readable.  Previously, with Window, I could get everything with no problems.  Here, even with the highest resolutions everywhere, frequently, I don't get anything usable.
Perhaps someone else has a suggestion?  
I don't mind paying for better software - I am saving money with the Linux operating system, so I'll spend it on software that allows me to do what I need to do.
Thanks very much,

---

### Post by mapes12 on 2010-09-07
Go System>admin>Synaptic and search for hplip and make sure it's installed. To make life easier also install hplip-gui for a user friendly front end.

Mark

---

### Post by JuliaHenson on 2010-09-07
Dear Mapes12,
    Thank you very much for your response.  I checked as you suggested, and I have hplip 3.10.2-2ubuntu2 installed.  I contacted my Linux technician and he told me to double-click over the "hplip-gui" if I wished to install it and to "accept" if it says that I need additional packages.  However, I will have to speak further with Luis about it, because there might be a reason that he had not already installed it.

Thank you very much!

---

### Post by JuliaHenson on 2010-11-12
[SIZE=5]Dear everyone, Yesterday, my computer technician showed me how to get great quality from my HP Scanjet 5590 by showing me how to use XSane and GMP properly.  

I hope I can remember all the information he gave me.  There is a manual available and videos on YouTube.  I haven't checked those yet, but hopefully, that will help me remember his instructions.

Thank you all,
Julia 
[/SIZE]

---

