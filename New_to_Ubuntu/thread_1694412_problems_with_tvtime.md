---
title: "problems with tvtime"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by bulls_eye on 2011-02-24
[LEFT]hi 

I am trying to watch tv with tvtime on ubuntu. I have been trying hard from many days with no luck.

So any kind of help will be welcome. 

Below is the output to some of the codes which the enlightened ones are usually interested in.

$lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 002: ID 10fd:2535 Anubis Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


$tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/geet/.tvtime/tvtime.xml
videoinput: Driver won't tell us its norm: Invalid argument
videoinput: Can't get tuner info: Invalid argument

    Your capture card driver: uvcvideo [USB 2.0 Camera/usb-0000:00:1d.7-6/256]
    does not support full size studio-quality images required by tvtime.
    This is true for many low-quality webcams.  Please select a
    different video device for tvtime to use with the command line
    option --device.

mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
Segmentation fault

thank you for your time.[/LEFT]

---

### Post by bulls_eye on 2011-02-24
nothing yet... :(

eagerly awaiting reply...

---

### Post by LowSky on 2011-02-24
You possibly need the driver and/or firmware installed. What make and model is your tv tuner? 
Are you trying to watch digital of analog tv? You might want to look into using mythtv instead of tvtime for more control options.

---

### Post by bulls_eye on 2011-02-25
> **LowSky said:**
> You possibly need the driver and/or firmware installed. What make and model is your tv tuner? 
Are you trying to watch digital of analog tv? You might want to look into using mythtv instead of tvtime for more control options.

I am trying to watch analog tv.

I am having problems with driver installation and I think that following some random tutorial from google might harm my computer.

Please tell me how should I find out details about my tv-tuner card. I am using a lenovo y500 laptop with an inbuilt tv-tuner card.

---

