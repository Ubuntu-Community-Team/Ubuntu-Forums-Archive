---
title: "ekiga fails to see my eyetoy webcam (cheese sees it just fine)"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by nanotube on 2009-02-12
Hi all

So, i have a webcam, sony eyetoy, and it works well with cheese. Using ubuntu intrepid 32bit, which comes with ekiga 2.0.12.

However, trying to set up ekiga, it fails to find the video input device. just says "no device found" using either v4l or v4l2

it does find the audio input on the camera, but not the video.

running ekiga with -d 6, the following debug messages are seen:
```

2009/02/12 02:46:19.809	  0:19.136	                  ekiga	Detected audio plugins: ALSA
2009/02/12 02:46:19.811	  0:19.138	                  ekiga	Detected video plugins: Picture,V4L2,V4L
2009/02/12 02:46:19.813	  0:19.140	                  ekiga	Detected audio plugins: ALSA
2009/02/12 02:46:19.815	  0:19.142	                  ekiga	Detected video plugins: Picture,V4L2,V4L
2009/02/12 02:46:19.818	  0:19.145	                  ekiga	Detecting V4L2 devices
2009/02/12 02:46:19.827	  0:19.154	                  ekiga	PV4L2Plugin	detected device metadata at /sys/class/video4linux/
2009/02/12 02:46:20.115	  0:19.442	                  ekiga	Detected the following audio input devices: Default,EyeToy USB camera Namtai,Intel 82801DB-ICH4 with plugin ALSA
2009/02/12 02:46:20.116	  0:19.443	                  ekiga	Detected the following audio output devices: Default,Intel 82801DB-ICH4 with plugin ALSA
2009/02/12 02:46:20.117	  0:19.444	                  ekiga	Detected the following video input devices: No device found with plugin V4L2
2009/02/12 02:46:20.118	  0:19.446	                  ekiga	Detected the following audio input devices: Default,EyeToy USB camera Namtai,Intel 82801DB-ICH4 with plugin ALSA
2009/02/12 02:46:20.120	  0:19.447	                  ekiga	Detected the following audio output devices: Default,Intel 82801DB-ICH4 with plugin ALSA
2009/02/12 02:46:20.121	  0:19.448	                  ekiga	Detected the following video input devices: No device found with plugin V4L2

```

(same thing with v4l)

/sys/class/video4linux does have the video0 symlink in it:
```

lrwxrwxrwx  1 root root 0 2009-02-12 13:41 video0 -> ../../devices/pci0000:00/0000:00:1d.0/usb1/1-1/video4linux/video0

```

would appreciate any suggestions as to how to make ekiga recognize the webcam... if i could even somehow point it directly to /dev/video0 or something... 

thanks!

---

### Post by nanotube on 2009-02-13
bump? :)

---

### Post by nanotube on 2009-02-13
bump...

---

### Post by Captain_Glen on 2009-04-16
I have exactly the same problem.  It works in cheese but not ekiga.

---

### Post by andersja on 2009-05-26
Out of curiosity - does it work in Skype?

Whilst being a proprietary application, they do pretty decent video calls...

---

