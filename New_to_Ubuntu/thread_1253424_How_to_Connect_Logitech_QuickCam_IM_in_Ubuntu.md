---
title: "How to Connect Logitech QuickCam IM in Ubuntu ?"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by SriLankanBoy on 2009-08-30
Hi,

I have a Logitech Quickcam IM and I got it working in XP. I just don't know how to connect it to ubuntu and get it working. :(


I searched in the internet. But I could not get a clear idea. I am a beginner to Ubuntu, so please explain descriptively. :)

My lsusb result :

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:08a0 **Logitech, Inc. QuickCam IM**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0451:6060 Texas Instruments, Inc. RNDIS/BeWAN ADSL2+
Bus 002 Device 002: ID 0583:a000 Padix Co., Ltd (Rockfire) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
```


**Thanks in Advance .... :)**

---

### Post by mikewhatever on 2009-08-30
Is that a wireless or bluetooth camera? lsusb output suggests it's a usb one, so what's the problem connecting it exactly?

---

### Post by rajeev1204 on 2009-08-30
> **SriLankanBoy said:**
> Hi,

I have a Logitech Quickcam IM and I got it working in XP. I just don't know how to connect it to ubuntu and get it working. :(


I searched in the internet. But I could not get a clear idea. I am a beginner to Ubuntu, so please explain descriptively. :)

My lsusb result :

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:08a0 **Logitech, Inc. QuickCam IM**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0451:6060 Texas Instruments, Inc. RNDIS/BeWAN ADSL2+
Bus 002 Device 002: ID 0583:a000 Padix Co., Ltd (Rockfire) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
```


**Thanks in Advance .... :)**

Logitech quickcams work without any problems in ubuntu.

Use a program like skype to test the webcam.

---

### Post by NoaHall on 2009-08-30
You won't need to install any extra software or drivers(except a IM app, like aMSN or skype), it will work from the start.

---

### Post by SriLankanBoy on 2009-08-30
> Is that a wireless or bluetooth camera? lsusb output suggests it's a usb one, so what's the problem connecting it exactly?

> Logitech quickcams work without any problems in ubuntu.Use a program like skype to test the webcam.

> You won't need to install any extra software or drivers(except a IM app, like aMSN or skype), it will work from the start.

I installed an application called Cheese which is recommended to capture images. In some websites, it is told that it should work without a problem. But I cannot get the web cam to work. It does not show anything. :(

---

### Post by jrox717 on 2009-08-30
>  Logitech quickcams work without any problems in ubuntu.Use a program like skype to test the webcam. 

This is not always correct! I know because I just had a few problems with my new Quickcam Connect but it is now working quite well. You will want to follow the directions from here: 
[https://answers.launchpad.net/ubuntu/+question/49739](https://answers.launchpad.net/ubuntu/+question/49739)

>  1. Download and unpack [http://people.atrpms.net/~hdegoede/libv4l-0.5.0.tar.gz](http://people.atrpms.net/~hdegoede/libv4l-0.5.0.tar.gz)
2. See README, and install: sudo make install 

To do this, note where you saved that tar.gz package. Double click on it to open up the archive manager, then extract it. I got a folder in my home directory called libv4l-0.5.0. So enter these commands in a terminal to intall the program (use your own username, or path to folder):

```
cd /home/user_name/libv4l-0.5.0
sudo make
sudo make install PREFIX=/usr/local 
```

> 
3. Open terminal window
4. $ export LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so
5. $ camstream
Start camera, should now work. 

To open cheese for example, type in 

```
export LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so
cheese 
```

Good luck!

---

### Post by SriLankanBoy on 2009-09-02
> **jrox717 said:**
> This is not always correct! I know because I just had a few problems with my new Quickcam Connect but it is now working quite well. You will want to follow the directions from here: 
[https://answers.launchpad.net/ubuntu/+question/49739](https://answers.launchpad.net/ubuntu/+question/49739)

To do this, note where you saved that tar.gz package. Double click on it to open up the archive manager, then extract it. I got a folder in my home directory called libv4l-0.5.0. So enter these commands in a terminal to intall the program (use your own username, or path to folder):

```
cd /home/user_name/libv4l-0.5.0
sudo make
sudo make install PREFIX=/usr/local 
```


To open cheese for example, type in 

```
export LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so
cheese 
```

Good luck!

I tried following your steps. Still it is not working ... :(

Here is the error the terminal shows all the time when I start cheese.
```
libv4l2: error dequeuing buf: Input/output error
```

---

### Post by jrox717 on 2009-09-02
Have you tried using another application besides cheese? Try skype or camstream (mentioned in the above link) and see how it goes from there. I have heard of times when one application works perfectly when another fails (though obviously it's better for them all to work)

---

