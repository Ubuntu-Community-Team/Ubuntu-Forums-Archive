---
title: "Xirlink IBM C-it Webcam"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by tmyakal on 2011-06-05
So I've been scouring the internet for a good few hours now. I've found a lot of people with the same problem as me, but no one telling as to how they solved it (if they did).

I found an old IBM C-it Webcam. I cannot get it to actually, you know, do anything you'd expect a webcam to do, though. It will not be recognized by Camorama, Kamoso, Skype, or Cheese. I've heard of people having it mysteriously run perfectly with XawTV, but XawTV doesn't seem to start up for me.

I've been to [http://www.linux-usb.org/ibmcam/](http://www.linux-usb.org/ibmcam/) which is where every article I could find on this sort of thing inevitably pointed. I can tell you that, according to that website, I've got a Model 2. When I **lsusb** the read-out is

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0545:8080 Xirlink, Inc. IBM C-It Webcam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I already have the ibmcam module, and user access to the video group, which are the other two common problems I saw. I really don't know what else I'm missing.

If you can help me, that would be fantastic. Just try to talk to me like I'm an idiot, because I'm very, very a newbie on Ubuntu.

---

### Post by jtarin on 2011-06-05
[Have you been to this page?]("http://www.linux-usb.org/ibmcam/ibmcamFAQ.html")

---

### Post by tmyakal on 2011-06-05
Yes, I had been to that page. Since, like I said, I'm not even remotely competent with Linux, I wasn't able to glean any helpful information from it. The things there that I understood, I had already done, for example: I already have the ibmcam module loaded. When I **/sbin/lsmod** I can see
```
Module                  Size  Used by
ibmcam                 45417  0 
usbvideo               23703  1 ibmcam
videodev               34361  1 usbvideo
v4l1_compat            13251  1 videodev

```

However, that site also recommends seeing if the driver is loaded by typing **/proc/bus/usb/devices**, but when I do that, I'm told "**No Such File or Directory**." So that site, too, is a bit of a dead end for me. Thank you for the suggestion, though.

Anyone have any further ideas? I'd really appreciate it.

---

### Post by jtarin on 2011-06-05
> **tmyakal said:**
> Yes, I had been to that page. Since, like I said, I'm not even remotely competent with Linux, I wasn't able to glean any helpful information from it. The things there that I understood, I had already done, for example: I already have the ibmcam module loaded. When I **/sbin/lsmod** I can see
```
Module                  Size  Used by
ibmcam                 45417  0 
usbvideo               23703  1 ibmcam
videodev               34361  1 usbvideo
v4l1_compat            13251  1 videodev

```

However, that site also recommends seeing if the driver is loaded by typing **/proc/bus/usb/devices**, but when I do that, I'm told "**No Such File or Directory**." So that site, too, is a bit of a dead end for me. Thank you for the suggestion, though.

Anyone have any further ideas? I'd really appreciate it.

OK your command of "lsusb" supersedes the command "/proc/bus/usb/devices". It seems you have the correct modules loaded. [Have you visited this page?]("https://help.ubuntu.com/community/Webcam")

---

### Post by tmyakal on 2011-06-05
No, I hadn't seen that page. If I'm understanding it correctly, the issue might be that the software doesn't know which /dev/video* to use? But I tried doing the **ls /dev/video*** both without the camera plugged in and with, and I got the same output both times. It was:
```
ls /dev/video*
/dev/video    /dev/video2   /dev/video31  /dev/video43  /dev/video55
/dev/video0   /dev/video20  /dev/video32  /dev/video44  /dev/video56
/dev/video1   /dev/video21  /dev/video33  /dev/video45  /dev/video57
/dev/video10  /dev/video22  /dev/video34  /dev/video46  /dev/video58
/dev/video11  /dev/video23  /dev/video35  /dev/video47  /dev/video59
/dev/video12  /dev/video24  /dev/video36  /dev/video48  /dev/video6
/dev/video13  /dev/video25  /dev/video37  /dev/video49  /dev/video60
/dev/video14  /dev/video26  /dev/video38  /dev/video5   /dev/video61
/dev/video15  /dev/video27  /dev/video39  /dev/video50  /dev/video62
/dev/video16  /dev/video28  /dev/video4   /dev/video51  /dev/video63
/dev/video17  /dev/video29  /dev/video40  /dev/video52  /dev/video7
/dev/video18  /dev/video3   /dev/video41  /dev/video53  /dev/video8
/dev/video19  /dev/video30  /dev/video42  /dev/video54  /dev/video9
```

Which, from what I've seen, that seems like way too much output, no? I tried running the cam through VLC like they said, with the **$ vlc v4l2:///dev/video0**, but replacing the last bit with a couple of different video numbers. Do I just need to sit down and try each and every one of the, like, sixty-odd options? It seems like their ought to be an easier way.

Thank you for continuing to offer help. I hope that we can figure this out.

---

### Post by jtarin on 2011-06-05
> **tmyakal said:**
> No, I hadn't seen that page. If I'm understanding it correctly, the issue might be that the software doesn't know which /dev/video* to use? But I tried doing the **ls /dev/video*** both without the camera plugged in and with, and I got the same output both times.From the page:If nothing new appears, you may need to switch your webcam on. For a built-in webcam, you may have a function key to do so.

---

### Post by tmyakal on 2011-06-05
It isn't a built-in webcam. It's a relatively ancient USB camera. There isn't any sort of switches or anything on it: it's supposed to just plug in and automatically come on. I know it works because  I did (after several other headaches) get it working on my Windows computer, but it doesn't seem to want to cooperate with this one. Any other ideas?

---

### Post by jtarin on 2011-06-05
You know now that I think about it this camera ....if I remember correctly is the same as the VEO stingray webcam I had about 10 years ago....or so. I could never get it to work. Came close, as a guy had written instructions on making your own driver as nobody wanted to support it. Man, I spent days on that. I think it was just passed by as it was a cheap camera and there was a new model of webcam coming out every week.
[Here's another good source]("http://tldp.org/HOWTO/html_single/Webcam-HOWTO/") ..if you like pain.:D

---

### Post by jtarin on 2011-06-05
> **tmyakal said:**
> It isn't a built-in webcam. It's a relatively ancient USB camera. There isn't any sort of switches or anything on it: it's supposed to just plug in and automatically come on. I know it works because  I did (after several other headaches) get it working on my Windows computer, but it doesn't seem to want to cooperate with this one. Any other ideas?Yea it only worked about half the time on my Windows install of 98 and XP. It's a coaster. Get another and have matching bookends.:D

---

### Post by tmyakal on 2011-06-05
Yeah, I guess I'll need to. I was just hoping for a lucky break, seeing as, like I said, I got it for free. Thanks for trying, though.

---

### Post by jtarin on 2011-06-05
> **tmyakal said:**
> Yeah, I guess I'll need to. I was just hoping for a lucky break, seeing as, like I said, I got it for free. Thanks for trying, though.FREE!!! I shelled out $8 for mine ...new.

---

