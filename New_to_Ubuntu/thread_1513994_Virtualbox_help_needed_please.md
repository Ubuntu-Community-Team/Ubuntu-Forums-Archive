---
title: "Virtualbox help needed please"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by blueghoti on 2010-06-20
Hi guys - 

I'm a total newbie to Virtualbox so need help - preferably in words of 1 syllable or less ;-)

I have Ubuntu 10.04 installed on a 320 gig HD taking the full partition.  I want to install Windows 7 in a virtual engine.  I will have infrequent use to Win 7 and need it specifically to run some Windows applications which cannot run in WINE.  When I am in Windows, I will need to access files in the Linux environment.  

I also need to synch my Nokia phone (specifically contacts / calendar).  As a temporary measure I have been using Evolution, but have been recommended Thunderbird for this.  I am not sure if my phone will synch with T'bird, in which case I might have to revert to Win / Outlook for this.

I think I have Virtualbox installed already.  Synaptic makes several references to 3.1.6-dfsg-2ubuntu2 when I search for Virtualbox.  However, I'm not really sure how to load it, configure it for my requirements, or get it to read from my Windows boot CD.

Any ideas on what I should do next?  I've tried several help pages but can't quite see my way through...

Chris

---

### Post by wgarider on 2010-06-20
First, let's be sure that Virtualbox is installed completely.... If you go to Applications, is there a System tools menu there? If so, is there an icon for Virtualbox or Sun Virtualbox?

If there is, there take a look at this: [http://www.ioncannon.net/system-administration/82/installing-windows-7-on-virtualbox/](http://www.ioncannon.net/system-administration/82/installing-windows-7-on-virtualbox/)
....this is a good visual tutorial on setting up Win7 in VB. The version of VB is a rev or two back but should get you started... Be sure and use an IDE drive controller and not the default choice of SATA.

Alternatively, here's a guide to installing VB 3.2: [http://www.ubuntugeek.com/virtualbox-3-2-released-and-ubuntu-installation-instructions-included.html](http://www.ubuntugeek.com/virtualbox-3-2-released-and-ubuntu-installation-instructions-included.html)
....I'm using VB 3.2 and have a Win7 VM running very well. Reply back if you need more help...

---

### Post by patchwork on 2010-06-20
> First, let's be sure that Virtualbox is installed completely.... If you  go to Applications, is there a** System tools menu** there? If so, is there  an icon for Virtualbox or Sun Virtualbox?

just a note:
on my 10.04 install virtualbox was added to the accessories menu

---

### Post by cmcanulty on 2010-06-20
On a related note, does VB require the CD to be running whenever windows is or can it be run from an iso iimage?

---

### Post by Merk42 on 2010-06-20
> **cmcanulty said:**
> On a related note, does VB require the CD to be running whenever windows is or can it be run from an iso iimage?
No and yes

The CD is only required like in a real machine, once Windows is installed the CD is no longer required.
Instead of a CD an iso can be used to accomplish the installation, after after would no longer be required.

It sounds like blughoti has the installtion CD for Windows 7 in which case Virtualbox would just use that to install.

---

