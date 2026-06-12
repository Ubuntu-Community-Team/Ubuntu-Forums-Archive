---
title: "Copy Windows Network Setup to New Ubuntu Laptop?"
date: 2013-11-08
forum: Networking &amp; Wireless
---

### Post by mabo5184 on 2013-11-08
Is it possible to retrieve the required information from a Windows netbook to setup a new Ubuntu laptop?

I have bought a new school laptop for my son because the old (school provided) windows netbook has died, and the IT guys at the school say they don't know how to setup Ubuntu ...

We both have been using Linux at home for a few years now and feel confident we could find what we need to know from community resources on line, but just not sure where to start.

Any suggestions would be much appreciated ...

---

### Post by SeijiSensei on 2013-11-08
What specifically are you looking for help with?  

The biggest issue I would think is any software that the school requires that runs only on Windows.  Basic things like network connectivity should "just work" with Ubuntu.  One possible problem area is if the school runs a locked-down wifi network that requires the use of "certificates" to authenticate.  Have your son bring the machine to school and see if he can connect it to the network.

LibreOffice provides a fine alternative to Microsoft Office for most student tasks.  If your son's teachers will only accept files in MS formats, you can tell LibreOffice to save in those formats by default.  Even better is the ability to write a PDF document directly from LO.  

If the school requires particular Windows software, you have basically three options, two of which require that you own a licensed copy of Windows already.  If so, you can either configure the machine to "dual-boot" Windows and Ubuntu by first installing Windows, then installing Ubuntu.  It will detect the Windows partition and set it up for dual booting.  An even more convenient option is to install [VirtualBox]("http://virtualbox.org/"), which lets you run "virtual machines" on top of Ubuntu.  You can create a Windows VM, install your copy of Windows to it, and call up Windows when needed.  If you go this route, please follow the [instructions]("https://www.virtualbox.org/wiki/Linux_Downloads") for "Debian-based" distributions at the VirtualBox site.  Once you add the Oracle repository, your system will manage all updates to VirtualBox automatically like it does with the rest of the Ubuntu software.

Another alternative is to install [WINE]("http://www.winehq.org/download/ubuntu"), an environment that can run many Windows programs successfully.  Whether it will run the software he needs is a matter of experimentation.

---

### Post by mabo5184 on 2013-11-08
[QUOTE=SeijiSensei;12842722

 One possible problem area is if the school runs a locked-down wifi network that requires the use of "certificates" to authenticate.  Have your son bring the machine to school and see if he can connect it to the network.

We know that his ipod does not connect to the school wifi using his old netbook login credentials.

Is it possible to tell by looking at the windows registry file if it uses certifcates?

Would it be possible to move the certificate to the new laptop?

If we had a new certicate from the school can it be setup to work with Ubuntu?

---

### Post by SeijiSensei on 2013-11-09
I'd ask the school's technicians.  My daughter encountered this problem at college.  I tried to figure out how to obtain and install the certificate in Ubuntu without much success.  The IT help staff was no help.

I doubt there is any simple or obvious method to copy the configuration from Windows.  If you could find out what company provides the wifi authentication service, you might be able to see if they have any Linux instructions.

Did you ask the school about the iPod?  What did they say?

---

### Post by mabo5184 on 2013-11-09
The school said they would not allow the ipod to be connected.

While searching around I found this software wpa_supplicant, it's looks to me that it may the software I need ...

The readme for the software makes references to a .pfx file in relation to certificates.

We found only one "pfx" file on the old windows drive (8841-L410_019.pfx) so I think it may the certicate, but not sure if it can just be copied and used on another computer.

The other information like protocols we will need to extract from the windows registry, or if we are lucky the school will help us ...

Thanks for the feedback.

---

