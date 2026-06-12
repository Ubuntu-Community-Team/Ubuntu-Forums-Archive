---
title: "ATI conflicting with compiz fusion/Visual Effects?"
date: 2010-02-21
forum: New to Ubuntu
---

### Post by summersource on 2010-02-21
Sorry to bug you guys again but I seem to be having some trouble with some of the applications in Ubuntu after a full install on a new system.  I did not have these problems before I think it may have to do with my Graphics card ATI Radeon HD 4200.
First issue is after downloading compiz fusion it is not showing up under System > Preferences all I have is the compiz fusion icon. 
I am also unable to change my Visual Effects to "Extra" or even "Normal"   I get this error message (Desktop effects could not be enabled).

Another problem I am having is I keep getting the red icon on my tool bar for crash reports, and I don't really understand why. 
I've used Ubuntu for about a month now on another system and liked it so much the first thing I did was wiped Windows 7 from my new system and installed Ubuntu. Anyway none of these were an issue before, so it seems like it has to be an issue with my system.

AMD Turion IIX2 M500

If someone could help shed some light on this I would appreciate it greatly.

---

### Post by tom.swartz07 on 2010-02-21
> **summersource said:**
> Sorry to bug you guys again but I seem to be having some trouble with some of the applications in Ubuntu after a full install on a new system.  I did not have these problems before I think it may have to do with my Graphics card ATI Radeon HD 4200.
First issue is after downloading compiz fusion it is not showing up under System > Preferences all I have is the compiz fusion icon. 
I am also unable to change my Visual Effects to "Extra" or even "Normal"   I get this error message (Desktop effects could not be enabled).

Another problem I am having is I keep getting the red icon on my tool bar for crash reports, and I don't really understand why. 
I've used Ubuntu for about a month now on another system and liked it so much the first thing I did was wiped Windows 7 from my new system and installed Ubuntu. Anyway none of these problems were an issue before, so it seems like it has to be an issue with my system.

AMD Turion IIX2 M500

If someone could help shed some light on this I would appreciate it greatly.

ATI is notorious for not supporting Linux systems.

Make sure that you have all of your updates installed.

Also, could you specify what exactly is crashing to give you the reports? click on it and it should tell you what broke.



Lastly, try looking in system>admin>hardware drivers to see if you have any additional support for your card. It might be the case that your card, (similar to mine) is put on legacy support and is only supported in Ubuntu 8.04

---

### Post by summersource on 2010-02-22
That fixed my driver issue thanks. I will make a note of the next crash report and post it's not happened again since yesterday. I am having horrible wireless issues, to the point that it's driven my to my Windows box just so I can post this. I'm on a Westell router and it has been dropping signal every since I did firmware updates. Any ideas?

---

### Post by doas777 on 2010-02-22
> **summersource said:**
> Sorry to bug you guys again but I seem to be having some trouble with some of the applications in Ubuntu after a full install on a new system.  I did not have these problems before I think it may have to do with my Graphics card ATI Radeon HD 4200.
First issue is after downloading compiz fusion it is not showing up under System > Preferences all I have is the compiz fusion icon. 
I am also unable to change my Visual Effects to "Extra" or even "Normal"   I get this error message (Desktop effects could not be enabled).

Another problem I am having is I keep getting the red icon on my tool bar for crash reports, and I don't really understand why. 
I've used Ubuntu for about a month now on another system and liked it so much the first thing I did was wiped Windows 7 from my new system and installed Ubuntu. Anyway none of these were an issue before, so it seems like it has to be an issue with my system.

AMD Turion IIX2 M500

If someone could help shed some light on this I would appreciate it greatly.

for a radeon HD 4200, you need to install the driver from ATI itself (is not supported by the driver in the repos). They just put out a new version last week that seems much smoother for me.
the other thing to keep in mind is that after most kernel updates, you will have to manually reinstall the driver (just run the installer again). you may have installed a driver some time in the past, but it may no longer be in use.

you should never have to manually install compiz, so if you did install compiz-fusion packages, you may have conflicting software installed. this may be the cause of the crash reports. try removing them, reinstall the ATI drivers from their site, and then try to turn on the desktop effects. you may initially get a message that it needs to download a driver (if you don't reboot after the driver install), but click cancel (since you know you just installed one), and your changes shoudl apply anyway. if not, reboot and try turning compiz again.

lastly, the 4200, just doesn't seem to be all that robust a card. you probably won't get it looking perfect, without purchasing a non-integrated vid card.

---

### Post by summersource on 2010-02-22
thx I will give that a try any thoughts on my wireless issue above b/c as of right now I can't connect on my Linux box?

---

