---
title: "Wireless On Lenovo Yoga 13"
date: 2013-10-04
forum: Networking &amp; Wireless
---

### Post by Rami_Saber on 2013-10-04
Hi,

I am having problems running wireless on my lenovo Yoga 13, I have followed some threads but with no luck.

It would be very helpful if someone could describe the needed steps in some details to solve this as I am new to Ubuntu.

Some info:
uname -r
3.8.0-19-generic

lsusb
[COLOR=#323232][FONT=Helvetica]Bus 001 Device 005: ID 0bda:1724 Realtek Semiconductor Corp.  [/FONT][/COLOR]

---

### Post by chili555 on 2013-10-04
Please see posts #6-8 here: [http://ubuntuforums.org/showthread.php?t=2149012](http://ubuntuforums.org/showthread.php?t=2149012)

---

### Post by Annodes on 2013-10-04
Try this !!

Download source (zip) from here...... [https://github.com/lwfinger/rtl8723au](https://github.com/lwfinger/rtl8723au)

Extract to home folder.

In the terminal type and hit ENTER

cd rtl8723au-master

make clean

make

sudo make install

sudo modprobe 8723au


You will have to repeat these steps every time you upgrade your kernel.

---

### Post by Rami_Saber on 2013-10-04
Thanks Annodes,

Working now, that was simple :)

---

### Post by Annodes on 2013-10-04
Glad to know that all is WELL !!;)
If the issue is resolved, please mark the thread as solved.

---

### Post by kowalski2 on 2013-10-17
Newbie question:  How do I "extract to home folder"?


Thanks.

---

### Post by chili555 on 2013-10-17
> **kowalski2 said:**
> Newbie question:  How do I "extract to home folder"?


Thanks.When you download the zip file, drag and drop it to your user directory instead of Downloads. Then right-click it and select 'Extract here.' Proceed as above.

---

