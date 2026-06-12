---
title: "[SOLVED] HP Photosmart printer driver for Windows share"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by mogators on 2008-12-30
I have a server running Ubuntu 8.10 desktop 64bit.  It detected my printer and is working perfectly from the server.  My kids are still running Windows XP on their machines (I'm working on them though :D).  I am currently using this driver for Windows when connecting the printer (Generic/MS Publisher Color Printer).  Basic printing works fine, but I cannot tell it to print from the photo tray.  HP only has an install for the printer, not a driver only.  This installs a bunch of HP stuff and then wants me to plug in the printer to finish the install.  Is there any way to get just a plain driver to use for Windows?

---

### Post by zeronothing on 2008-12-30
I'm not sure what model of the photosmart you have but I have the 2610 and on the HP website they have a basic printer driver. They have the full software one available for download which is like 250mb. they also have a basic one which is like 35mb.

---

### Post by mogators on 2008-12-30
Sorry, forgot to specify the model.  It is the Photosmart 8250.  The only driver download HP has is this file:  		
enu_cdrom_A_nonnetwork.exe.  When opening this file it wants to install some HP apps and then have me plug in the printer into the Windows machine to finish the installation.

---

### Post by mogators on 2009-01-05
I have managed to solve my problem after chatting with an HP rep online.  At first they were ready to say sorry we don't support your setup.  But after a little prodding, I found out where the Windows driver is put during the install on a Windows machine.  
What I ended up having to do was:
1. Run the Windows installer on one of my Windows boxes.  
2. Copy the contents of C:\temp\photosmart8 folder to my server.
3. Add the Photosmart printer (shared on Ubuntu server) to windows machines and tell it I have the driver disk and point to where I copied the files in step 2.

I uninstalled all the HP stuff on the Windows box that I ran the HP installation on before re-adding the shared printer back on.

Hopefully this will help someone else in the future.

---

