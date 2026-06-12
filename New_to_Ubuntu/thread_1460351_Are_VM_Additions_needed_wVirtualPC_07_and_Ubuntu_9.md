---
title: "Are VM Additions needed w/VirtualPC 07 and Ubuntu 9.10?"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by TNWAsher on 2010-04-22
I have been trying to install VM Additions for the past week following instructions from posts that haven't been updated in a year.  Is VM Additions really needed?  And if so, I have got to get some easier way of installing other then the vmadditionsforlinux.iso on the microsoft website.  Please Help!!

---

### Post by empty_spaces on 2010-04-22
I thought VirtualPC did not support linux hosts/guests.
[http://www.microsoft.com/downloads/details.aspx?familyid=2B6D5C18-1441-47EA-8309-2545B08E11DD&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=2B6D5C18-1441-47EA-8309-2545B08E11DD&displaylang=en)

I apologize if my information is wrong.

Edit: I'm having a hell of a time navigating the VirtualPC 2007 website, both Firefox and Chrome keep crashing.

---

### Post by spydeyrch on 2010-04-22
I would recommend not using Virtual PC from Microsoft. Try VMWare or virtual Box. I use virtual box and it is awesome!! Installing the virtual machine addons is easy.

they are needed for mouse pointer integration between the two OSs and also for sharing the clipboard, sound, better visuals, etc.
Let us know how it goes. :-)

-Spydey:guitar:

---

### Post by TNWAsher on 2010-04-22
oops...yea I'm not running the newest version of Virtual PC.  Actually its version 6.0.156.0.  I think my boss wrote the wrong number on the CD.

---

### Post by ChazZeromus on 2010-11-07
Well they're VM additions but they seem to be designated towards redhat and suse. I've been trying to get these packages to install on ubuntu 9.04. I found the additions here: [http://www.microsoft.com/downloads/en/details.aspx?FamilyId=BF12642F-77DC-4D45-AE4E-E1B05E0A2674&displaylang=en]("http://www.microsoft.com/downloads/en/details.aspx?FamilyId=BF12642F-77DC-4D45-AE4E-E1B05E0A2674&displaylang=en")
All the services install correctly after having to convert the RPM packages using alien into .deb packages, but the main service "vmadd" always ends with this error from dpkg:
```
subprocess installed post-installation script returned error exit status 1
```
Maybe forced package conversion was a bad idea?

---

