---
title: "Switching between Ubuntu and Windows XP on a dual-boot?"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by CommuneOfLoon on 2010-10-07
Hi, is it possible to easily switch between the two OS's without having to completely turn off the computer? I remember reading something about hibernating Ubuntu, but I don't remember what or where. 

Thanks.

---

### Post by aeronutt on 2010-10-07
I don't know of anyway..unless you're running XP inside virtual box, which is what I do.

---

### Post by lbrty on 2010-10-07
No, you cannot. You can use a virtual machine such as VirtualBox or VMware Player. You can boot into Ubuntu and install Windows in a virtual machine or vice-versa (boot into Windows and install Ubuntu in a virtual machine).

You do not have to turn off the machine, just restart it. :)

---

### Post by CommuneOfLoon on 2010-10-07
Okay; not sure I'm up for trying the whole virtual computer thing yet, but I appreciate the info.

---

### Post by lbrty on 2010-10-07
It really quite simple. Do you have the Windows installation disc?

---

### Post by CommuneOfLoon on 2010-10-07
> **lbrty said:**
> It really quite simple. Do you have the Windows installation disc?

Yes, a XP SP3 disc.

---

### Post by lbrty on 2010-10-08
If you ever do decide that you would like to use a virtual machine, try using VirtualBox first then VMware Player (it is also free but requires registration).

Go to [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and download VirtualBox for your distribution. For example I have 10.04 32-bit so I would download Ubuntu 10.04 LTS ("Lucid Lynx") i386. If you have Ubuntu 64-bit you would download AMD64.

Once you download the .deb file (per the instructions above) to your machine, then double click the file as you would an .exe file in Windows. Once it finishes installing VirtualBox, restart the machine and go to System Tools and click Oracle VM VirtualBox.

Click New, select Windows and the version XP. Follow the prompts, insert the XP disc and the install process should begin.

---

### Post by CommuneOfLoon on 2010-10-08
Thanks for the info, I may try it out.

---

### Post by aeronutt on 2010-10-08
I'd never used virtual box prior to a few weeks ago, and installing and using virtual box was infinantely easier than the XP intstall within vbox. :)

---

### Post by CommuneOfLoon on 2010-10-19
> **aeronutt said:**
> I'd never used virtual box prior to a few weeks ago, and installing and using virtual box was infinantely easier than the XP intstall within vbox. :)

Are VirtualBox and VBox or did you mean something else?

---

### Post by HermanAB on 2010-10-19
Howdy,

There is a forum for Virtualization - tons of help there.  This the 21st Century method.

Regarding hibernating Ubuntu:
Yes you can switch between Windows and Ubuntu faster if you would use hibernate instead of complete shutdown, but this is still the 20th cnetury method.

---

### Post by aeronutt on 2010-10-19
Oracle VM Virtual Box.

---

