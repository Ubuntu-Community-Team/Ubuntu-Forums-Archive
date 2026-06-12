---
title: "Logitech webcam help?"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by Asgi on 2011-02-05
I have a Logitech HD Webcam C270. I was able to install it onto Windows, but seeing as I use Ubuntu 90% of the time, I would like to be able to install it on Ubuntu also. The CD doesn't work for installation (pretty much windows installation files), and the webcam is not detected when I plug it in. 
I am lost when it comes to installing most things on Ubuntu... Can someone please give me guidance? Do I need to use terminal, download drivers, what?
Thank you in advance for any help.

---

### Post by Wtower on 2011-02-05
> **Asgi said:**
> I have a Logitech HD Webcam C270. I was able to  install it onto Windows, but seeing as I use Ubuntu 90% of the time, I  would like to be able to install it on Ubuntu also. The CD doesn't work  for installation (pretty much windows installation files), and the  webcam is not detected when I plug it in. 


Install Cheese from the Software Centre and give a try.

> **Asgi said:**
> I am lost when it comes to installing most things on Ubuntu... Can  someone please give me guidance? Do I need to use terminal, download  drivers, what?
Thank you in advance for any help.

Personally I prefer buying and using hardware that works natively with the kernel without troubling myself with downloading and installing stuff, unless it worths it. Besides, there is hardware for which the drivers even in Windows may not be certified. Here is a list of most compatible web cameras:

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

This is useful as well:

[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

---

### Post by Asgi on 2011-02-05
Uhm... I just tried installing Cheese. "An unhandlable error occurred."
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

should I maybe just try sudo apt-get install cheese ?

---

### Post by natman on 2011-02-05
always try [HTML]sudo apt-get install package_name[/HTML]first its the safest way to install for your system

---

### Post by Asgi on 2011-02-05
Got it! 
Is there anyway to use it do record audio on LMMS, or even Cheese? The webcam has a built in mic.

---

### Post by phorgan1 on 2011-02-15
I have a C270 and my audio doesn't work.  It is on the list of supported webcams.  When I plug it in the video is recognized, but not the audio.

When I plug it in I get this message on dmesg:
```
[420740.288084] usb 2-4: new high speed USB device using ehci_hcd and address 5
[420740.637295] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0825)
[420740.733957] input: UVC Camera (046d:0825) as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input14

```

lsusb says:
```
Bus 002 Device 005: ID 046d:0825 Logitech, Inc. 

```

Any ideas?

---

### Post by phorgan1 on 2011-02-15
All I had to do is sudo modprobe snd_usb_audio and the right device appeared.  After that I had to unmute it and select it for the software I was using, yay!

---

### Post by Paqman on 2011-02-15
I have the exact same webcam, and it worked as soon as I plugged it in. The only problem i've ever had is that Pulse seems to sometimes randomly decide to switch to the mic input on my mobo instead of the mic in the webcam.

---

### Post by sashko_s on 2012-10-02
[https://help.ubuntu.com/community/Webcam#See%20also](https://help.ubuntu.com/community/Webcam#See%20also)

---

### Post by sandyd on 2012-10-02
**Necromancy - thread closed**

As per the [Ubuntu Forums code of conduct]("http://ubuntuforums.org/index.php?page=policy"), please do not post in threads more than one year old

Thanks!

---

