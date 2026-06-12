---
title: "ubuntu on toughbook not reading external cd/dvd drive"
date: 2011-04-16
forum: New to Ubuntu
---

### Post by sonyofjapan on 2011-04-16
so i ave this toughbook with ubuntu gnome 9.04 install and i am a noob to ubuntu. got it back in december. but anyway. when i hook up a external cd/dvd drive, it says it cant find a media or something like it wouldnt read it.
my laptop is a toughbook cf-18 netbook. doesnt have cd/dvd drive

---

### Post by khelben1979 on 2011-04-16
Once it's connected, type: ```
lsusb
``` from a console window and post the output in this thread. I assume it's using USB, correct me if I'm wrong.

Will be interesting to see the brand of what you're trying to connect. In the worst case scenario the Linux kernel have no support for what you're trying to connect, but let's hope for the best!

---

### Post by sonyofjapan on 2011-04-16
yes, it is a usb. my netbook is a military/police grade computer that i bought from from craigslist. use to be windows. i was hooking up the drive to netbook and put usb drive on top of list at the bios menu and pop in xp cd but it did not read it. then i log onto the computer and pop in a movie on a cd and it says something abount not finding a media

---

### Post by khelben1979 on 2011-04-16
Okay! When you're looking at the USB DVD drive, is it marked with a brand like IOMega, LG or how does that look like?

---

### Post by sonyofjapan on 2011-04-16
its inland

---

### Post by Chrissd on 2011-04-16
Hi,

If it's the same Panasonic one as we used to use (UK Royal Air Force) then we had problems with the USBs not working properly. They would detect something connected to the USB but not read the device at all, regardless of what USB device it was, even if it was previously installed. 

My advice is just check the USB slot does work at a basic level. Apologies if you've confirmed the USB slot is working.

---

### Post by sonyofjapan on 2011-04-16
> **Chrissd said:**
> Hi,
 
If it's the same Panasonic one as we used to use (UK Royal Air Force) then we had problems with the USBs not working properly. They would detect something connected to the USB but not read the device at all, regardless of what USB device it was, even if it was previously installed. 
 
My advice is just check the USB slot does work at a basic level. Apologies if you've confirmed the USB slot is working.
 
yes. it is working. all of it. it may be my computer or the os software

---

### Post by fabricator4 on 2011-04-16
> **sonyofjapan said:**
> so i ave this toughbook with ubuntu gnome 9.04 install and i am a noob to ubuntu. got it back in december. but anyway. when i hook up a external cd/dvd drive, it says it cant find a media or something like it wouldnt read it.
my laptop is a toughbook cf-18 netbook. doesnt have cd/dvd drive

Some DVD drives need a lot of power - more than some portable devices can supply from just one USB port.  My Memorex Lightscribe drive will actually cause my EeePC to turn off if I plug it in while running on battery only.  Similarly, I've had problems with external hard drives and devices not working because the USB cannot supply enough power... it's one of the known limitations of USB 2.0 (1.1 was even worse) but the power specification has been increase for USB 3.0.  This may not help though, if the portable device just hasn't got the ability to power a demanding external device.  Even some USB pen drives may cause problems on some computers, and I had a BeBook that would not connect at all if the battery was not fully charged to start with. 

Try a 'Y' cable that plugs into two USB ports for more power, or better still plug a separate power supply into the external drive.  Certainly, I don't recommend you try plugging in the drive when running on battery only if it's using that much power.

More information on USB power [here]("http://en.wikipedia.org/wiki/Universal_Serial_Bus#Power").

Chris.

---

### Post by sonyofjapan on 2011-04-16
thanks, i will try that, if i can find a power supply for it

---

### Post by khelben1979 on 2011-04-17
What about getting a recommended external DVD/CD-RW Combo CF-VDRRT2W which is from Panasonic as well, I checked it up [here]("http://ixbtlabs.com/articles2/portopc/panas-cf-18.html"). Or a more modern one, if available.

Then you don't need to replace the powersupply.

---

