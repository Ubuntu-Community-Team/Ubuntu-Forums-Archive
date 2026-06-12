---
title: "Scsi?"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Irish1 on 2009-04-25
What is SCSI?

---

### Post by WatchingThePain on 2009-04-25
Hi,
Read this: [http://en.wikipedia.org/wiki/SCSI](http://en.wikipedia.org/wiki/SCSI)
You will see that scsi is gooood.

Scsi is a fast interface for data transfer.
For example faster that IDE.
A pc's motherboard or mainboard has different types of "bus" which are highways that data travel on.
The connectors used to connect a scsi hard drive to your pc would differ to those used to connect an ide hard drive (internally).

---

### Post by Irish1 on 2009-04-25
I see from the article that the SCSI driver? is what I need to make my scanner work, but I can't.  What should I do?

---

### Post by pbpersson on 2009-04-25
What sort of SCSI controller card do you have?

Is this a PCI card you added to your computer?

If Ubuntu does not recognize the controller, then Google it and preface it with Ubuntu to see what other people have done.

For instance:

```
Ubuntu "Adaptec 29320ALP-R"
```

---

### Post by WatchingThePain on 2009-04-25
Ok on Linux the first thing is to check your scanner documentation to see if Linux supports that hardware.
If no documentation find scanner model usually on label then google the website.
If so just plug it in to the pc, turn on and it should be recognised ( I usually would restart the pc with the scanner on).
If not post back any errors.
I don't know how familiar you are with the connectors and you may need to google some images.
Most modern scanners use the usb connection and also require a power cable.

---

### Post by pbpersson on 2009-04-25
Once you have the scanner connected to the computer, you can install and use a program called "XSane" for scanning.

When you start the program it should search for and find your scanner if all goes well.

---

### Post by Irish1 on 2009-04-25
Any suggestions if all goes not so well?

---

### Post by wizard10000 on 2009-04-25
> **Irish1 said:**
> Any suggestions if all goes not so well?

Yup.

If you don't know whether you have a SCSI scanner then you don't have one.  The guy who told you you had to install a SCSI driver for your scanner to work had no idea what he was talking about.

I know in Jaunty that you specifically have to enable sane in /etc/default/saned - can't remember whether I had to in Intrepid.

---

