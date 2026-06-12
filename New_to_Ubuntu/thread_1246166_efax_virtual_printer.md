---
title: "efax virtual printer"
date: 2009-08-21
forum: New to Ubuntu
---

### Post by Chough39 on 2009-08-21
I have installed Ubuntu 9.04 and the efax and efax-gtk packages from Synaptic Package Manager. However I cannot get a virtual printer to appear in OpenOffice Writer. Some help to get sorted out in Ubuntu please. I am new to what seems to be a super system.

---

### Post by pvfjr on 2009-09-04
I was just trying to figure this out too.  It says it's an option in the documentation...

---

### Post by Windows Nerd on 2009-09-04
> **Chough39 said:**
> I have installed Ubuntu 9.04 and the efax and efax-gtk packages from Synaptic Package Manager. However I cannot get a virtual printer to appear in OpenOffice Writer. Some help to get sorted out in Ubuntu please. I am new to what seems to be a super system.

It is a super system alright. If you have been using Windows for a long time and are quite experienced with it, and are completely new to Linux, remember this: Linux is _very different than Windows._ Correcting problems are different, troubleshooting is different, and solutions that work in Windows wil not necessarly work in Ubuntu/Linux.

Have you tried connecting to it with Printing? Access it via System>Administration>Printing. Maybe Open Office cannot find your printer because Ubuntu cannot find it.

Scott

---

### Post by pvfjr on 2009-09-04
Ok, I figured it out.  I found some older instructions from cement_head for the 8.10 version, and things were a little bit different in this version, but I modified it a bit for you.

Go to System > Administration > Printing

Click on New > Printer

Select Network > Appsocket/HP Jetdirect

Type "localhost" for the host, and "9900" for the port, then click "forward". 

Ensure "Generic" is selected for the make, then click "Forward".

Select "Raw Queue" for the model, then click "Forward".

Enter a printer name and description of your choice, such as "eFax".  Then click "Apply".

Open eFax-gtk.  Where it says "Fax entry method", select the "socket" option.  Then you can close eFax.

Now you should be able to select "eFax" from your list of available printers from the program of your choice, such as a word processor.  It will "print" the job to the eFax program, then prompt you for a phone number and ask whether you want to send it or queue it.

---

### Post by Chough39 on 2009-09-30
Thanks every one, I have now found the printer.

---

