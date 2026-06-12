---
title: "setting up a HDD for install"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by ubunt2guy on 2009-01-03
I have a HDD that had a NTFS (windows) file system on it.  I ripped it out of my friends old computer to use as external storage.  Now I want to use the same HDD to setup up that same PC for a Ubuntu install.  

How do I setup up the HDD for a Ubuntu install after I formatted the HDD and wiped out the windows file system. 

thanks

---

### Post by jbrown96 on 2009-01-03
You can set it up during the installation process. I think it's like step 5 of 7. Are you looking for a guide on how to partition it?

---

### Post by ubunt2guy on 2009-01-03
> **jbrown96 said:**
> You can set it up during the installation process. I think it's like step 5 of 7. Are you looking for a guide on how to partition it?

I don't think so.  

When I power on, I get a message that reads,"NTDLR is missing".

---

### Post by ubunt2guy on 2009-01-03
I'm thinking it is something with the BIOS...

---

### Post by RealPSL on 2009-01-03
If you are getting that message you BIOS is still booting from the hard drive not the Ubuntu CD/DVD. You need to configure your BIOS to boot from the CD drive with the Ubuntu Live CD or other installation media in that drive. 

[https://help.ubuntu.com/8.10/installation-guide/i386/pre-install-bios-setup.html#boot-dev-select]("https://help.ubuntu.com/8.10/installation-guide/i386/pre-install-bios-setup.html#boot-dev-select")

The link above has instructions for booting from CD. If you know how to access your BIOS it is pretty easy. The above document says u use the Delete key to access the BIOS but it is BIOS dependent. I have seen F2 and F12 as well (I think).

---

### Post by teh_yodeler on 2009-01-03
RealPSL is right.  Just make sure you boot from the CD drive.  Then, let ubuntu use the entire disk (it will ask you during setup).  This will wipe out anything you have on the drive, and the partitions will set themselves up.

---

