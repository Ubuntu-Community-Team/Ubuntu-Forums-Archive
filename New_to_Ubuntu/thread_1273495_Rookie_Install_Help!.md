---
title: "Rookie Install Help!"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by cptexas on 2009-09-23
Recently had hard drive replaced in an Toshiba Satellite A215 running an AMD processor. Don;t have Windows CD so wanted to use Linux - first time ever. Burned Ubuntu to DVD as directed (I think). Pressed F12 key while booting laptop and and boot priority to CD - saved setting and exited.
 
Put disk in drive, powered on, hear DVD drive spinning for approx. 4-5 seconds - yippee we're in business - Nope. Get same message every time - some PXE dialogs, then "operating system not found". 
 
I've tried several different linux distributions, believe I'm buring them correctly, believe I've set boot drive priority correctly - but nothing. 
 
I wondered if when my HDD was replaced my DVD was "reconnected" but assume it wouldn't spin if not. Help?!

---

### Post by atomizer on 2009-09-23
Did you burn an ISO? else it is just a datacd without the boot-files.

If you can boot from USB, you also can try [unetbootin]("http://unetbootin.sourceforge.net/"), make a bootable USB and try it from there.

---

### Post by NightwishFan on 2009-09-23
How to Burn an ISO on Windows:

[LIST=1]
[*]Download and install Infrarecorder ([LINK]("http://infrarecorder.org/?page_id=5"))
[*]After staring Infrarecorder go to the Actions -> Burn Image menu option.
[*]Select the Ubuntu ISO image, and set the burning speed to 2x (or slowest possible)
[*]Press OK and wait for the process to finish.
[/LIST]


After the iso is burned, reboot. If your machine boots from CD/DVD first in BIOS, then you should see an Ubuntu menu. Choose check disc for defects. If the check passes, then you can 'Try Ubuntu'. That will allow you to test it right from the CD. If you like it, we can try to install it. It is a fairly easy process, but requires some mild preparation to dual boot safely. If you want to install only Ubuntu it is very easy.

---

### Post by LewRockwell on 2009-09-23
> **cptexas said:**
> Pressed F12 key while booting laptop and and boot priority to CD - saved setting and exited.

The F12 manual boot device selection function must be utilized each time the operator desires to boot in a different order than is selected as default in the BIOS.

We go into the BIOS and set the boot device priority so that the optical drive is first, USB devices are second, and the internal hard drive is third.
(the F2 key at power-up is used by many machines to access the BIOS settings)


> **cptexas said:**
> Get same message every time - some PXE dialogs, then "operating system not found".

Many machines will NOT proceed past the hard drive for operating system discovery when the hard drive is set as the first boot device and it does not contain a good bootable system.

 
> **cptexas said:**
> I've tried several different linux distributions, believe I'm buring them correctly, believe I've set boot drive priority correctly - but nothing.

This would more fully support our commentary above.


> **cptexas said:**
> I wondered if when my HDD was replaced my DVD was "reconnected" but assume it wouldn't spin if not. Help?!

We're guessing it's connected properly but you can keep it in mind if all else fails.

.

---

