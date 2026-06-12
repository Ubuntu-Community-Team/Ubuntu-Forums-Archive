---
title: "Nintendo WiFi USB Adaptor"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by RATM_Owns on 2008-05-28
I'm having a lot of trouble getting it to work.
The guides don't work. Tried most of them.

Anyone who got it to work?

---

### Post by MattHelm on 2008-06-11
I got it, but it took a little magic.

The device is based off of the Buffalo WLI-U2-KG54-AI adapter, but its not quite the same.  Uses the same drivers with a slight modification.

The drivers can be found here:
[http://www.buffalotech.com/support/getfile/?U2KG54_1-01-02-0002.zip]("http://www.buffalotech.com/support/getfile/?U2KG54_1-01-02-0002.zip")

The only problem is, they don't work without some modifications.

Unzip the file after download and navigate to the newly extracted Win2000 directory.  Change the NETU2G54.INF from read only to read/write, and open it up with your favorite text editor.

Near the top of this file you will see a section that has the heading,
[Adapters]. As you may of guessed, this is the list of devices that the
driver will associate itself with.

The section will look like this in the stock driver:

```
 [Adapters]
 ; DisplayName               Section               DeviceID
 ; -----------               -------               --------
 %rt2500usb.DeviceDesc% =       rt2500usb.ndi,           USB\VID_0411&PID_005E
 %rt2500usb_nai.DeviceDesc% =   rt2500usb.ndi,           USB\VID_0411&PID_0066
 %rt2500usb_ai.DeviceDesc% =    rt2500usb.ndi,           USB\VID_0411&PID_0067
```

All you need to do is add the following line:

```
%rt2500usb.DeviceDesc% =       rt2500usb.ndi,           USB\VID_0411&PID_008B
```

So the [Adapters] section should look like this when you are done:

 ```
[Adapters]
 ; DisplayName               Section               DeviceID
 ; -----------               -------               --------
 %rt2500usb.DeviceDesc% =       rt2500usb.ndi,           USB\VID_0411&PID_005E
 %rt2500usb_nai.DeviceDesc% =   rt2500usb.ndi,           USB\VID_0411&PID_0066
 %rt2500usb_ai.DeviceDesc% =    rt2500usb.ndi,           USB\VID_0411&PID_0067
 %rt2500usb.DeviceDesc% =       rt2500usb.ndi,           USB\VID_0411&PID_008B

```
After you have added the correct line, save the file and close it.

Now that you have modified the driver itself, we can proceed with the actual
installation of the driver, which is explained in this tutorial.
[http://ubuntuforums.org/showthread.php?t=564419]("http://ubuntuforums.org/showthread.php?t=564419")

Hope it works for you!

---

