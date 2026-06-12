---
title: "New Camera"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by quietbear on 2009-03-04
Hello, just bought a new Panasonic SDR-S10.  It comes with some windows software, that is not compatible with Ubuntu obviously.

I tried to run the install through wine but it just freezes up when it gets to "Setup is starting the Installation Guide" or whatever, point is, it doesn't even get to the actual software installation, just freezes right when it starts to load the installer.

I would like to be able to link the camera to the PC (I can already xfer files and all whatnot) so that I can see on my screen what the camera sees (like a webcam sorta).

Any ideas???

I installed the wine package that is in the Add/Remove Programs area. (ubuntu 8.10)

---

### Post by ibizatunes on 2009-03-04
Best guess here!!
On my sony camera, there was different options in the camera to transfer data to your pc, change the setting and plug the camera in..... and see if it transfers
Most camera are well supported
Using WINES i would say is a waste of time for this sort of thing!!!

---

### Post by quietbear on 2009-03-04
Like I said, I can already xfer the files fine.  That is not what I want.  I want the software that it comes with that will allow me to see what I am recording on my computer, as opposed to in the mini-display.

I can get the recorded files over just fine, edit them, etc.

But, if say I am making a Youtube video, I would like to look at my monitor to see the frame and make sure I am in frame etc.  (Like a webcam)

---

### Post by rtom on 2009-03-04
As I understand, you want to use the camera as a webcam, this case plug the thing to the pc using the usb interface (when Ubuntu is running and cam in camera mode) and then in terminal check whether it is recognized as a webcam (use command "dmesg" for system messages). If it's OK, install cheese and you can see yourself. Hopefully...

---

### Post by jaminux on 2009-03-04
Not all windows programs are compatible with wine. Some require specific DLLs to run. You can try google it up and see if someone has managed to get it to work.

An alternative to wine is to emulate a version of windows in a virtualization program. 

If you have a copy of a windows CD (I find XP is best for virtualization), you can install a complete copy of Windows in Linux and run it in a window.

This is obviously much slower than wine as you are basically running an OS inside another OS, however you can run many more applications (only limit really is what your system can take, won't really do games as the processing would be too intense, although they will run).

A free Virtualization program is VirtualBox. A commercial one (which happens to be a lot better) is VMware workstation. However, there is a free version of VMware (it is harder though), VMware server, available as well. Alternatively, you can also do a trial of VMware workstation, make a vm (i.e. install windows), then use the free VMware player to play that vm. You might have to update if the linux kernel gets updated though. 

If you can afford it VMware workstation is very good. Believe it is $160 though.

See the virtualization forum for more information on Virtualization programs.

---

### Post by quietbear on 2009-03-04
> **rtom said:**
> As I understand, you want to use the camera as a webcam, this case plug the thing to the pc using the usb interface (when Ubuntu is running and cam in camera mode) and then in terminal check whether it is recognized as a webcam (use command "dmesg" for system messages). If it's OK, install cheese and you can see yourself. Hopefully...

Its recognised as a storage device.  Boy, that woulda been sweet though if that was the case.  Is there a way to tell ubuntu that it is both a storage device and a webcam?

---

### Post by rtom on 2009-03-04
I searched the net for the product details and found that there is NO webcam support for this camera, so it seems it won't work neither on Windows.

See: [http://uk.shoppydoo.com/price-digital_camcorder-panasonic_sdr_s10.html](http://uk.shoppydoo.com/price-digital_camcorder-panasonic_sdr_s10.html)

---

### Post by quietbear on 2009-03-04
OK, thanks, just wanted to know if maybe there was software out there that could do it, but from what I see it is just not possible with this camera.  Oh well, I will just use the TV, no biggie.

Thanks for the help.

---

