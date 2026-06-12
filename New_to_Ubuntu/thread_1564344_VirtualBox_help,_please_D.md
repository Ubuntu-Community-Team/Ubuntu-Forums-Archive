---
title: "VirtualBox help, please :D"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by soulja96 on 2010-08-30
Hey guys, i was wondering for those who use virtual box, is it possible for a hard drive to be useable?. Eg, When i use virtual box for windows XP, and i plug in the hardrive nothing happens? Help appreciated :D:D

---

### Post by stlsaint on 2010-08-30
Are you referring to the plugging up an external harddrive while running a xp vm and wanting to use that external drive in the xp virtual machine? If so than you need to manually select in the machine vbox settings for that harddrive to be "captured" by the xp machine. The should be a devices tab up top in your machine window for vbox. (not at my system right now so i cant give more detailed instructions)

---

### Post by jerome1232 on 2010-08-30
Found this on Oracles site

[http://www.virtualbox.org/manual/ch09.html#rawdisk](http://www.virtualbox.org/manual/ch09.html#rawdisk)

Hope that helps you out. If you don't understand what to do post back maybe we can help clear up whatever looks like mud to you.

--edit--

I didn't even think of what stlsaint is talking about, your plugging in usb disk and just trying to access it in the guest OS?

---

### Post by soulja96 on 2010-08-31
Eg, External hard drive plugged into PC, i open VB windows XP and nothing appears. What do i have to do?:confused:

---

### Post by varunendra on 2010-09-02
I guess [this]("http://ubuntuforums.org/showthread.php?t=1015474") is what you want. (refer to post #3 on the link)

---

### Post by Verbeck on 2010-09-02
Or another way is to share the /media directory (from the Devices menu) and then map network drive on xp. So when a drive is mounted on the host it should appear within the network drive in xp. to do this, the guest additions should be installed.

[IMG]http://i52.tinypic.com/mtpgjt.png[/IMG]

[IMG]http://i55.tinypic.com/zxjk1j.png[/IMG]


*might not be what you are looking for.... :-?

---

### Post by Calash on 2010-09-02
Is the external hard drive connected via USB?

If so you need to make sure you have the version of Virtualbox that supports USB, not the one from the default Repo.

I believe this is covered in one of the linked posts above.


Once you have the correct version you need to start your guest OS, plug in the device, and then click on the Devices menu, the USB.  Your device should be listed there with no check mark.  Check it off and wait a bit and it will dismount from the Host OS and mount to the Guest OS.

---

