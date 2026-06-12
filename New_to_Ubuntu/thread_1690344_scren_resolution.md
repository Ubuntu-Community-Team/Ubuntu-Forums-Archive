---
title: "scren resolution"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by Brooksbrooks on 2011-02-18
I've read other messages but not sure what applies to my problem. I have just installed Ubuntu and everything works well but after installing latest driver for Nvidia FX5700 I can't get a resolution above 640 x 480. I have a Samtron 72v monitor but cannot find a linux driver if there is one. I want to change to 1024 x 768. Any help would be appreciated. My monitor is listed as unknown.

---

### Post by sikander3786 on 2011-02-18
Welcome to the forums :-)

You've an older Nvidia graphics card, which version of drivers did you activate.

In addition to posting the driver version, try reconfiguring your graphics. Copy/paste these commands to your Terminal and reboot and let us know how that goes.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

If it says file not found, no problem. Proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

And when you type your password in Terminal, you won't see any asterisks. Just type blindly and hit <Enter>.

---

### Post by Brooksbrooks on 2011-02-18
I activated Nvidia driver version 173 - this was listed as recommended. 

Re the codes - there was no file found. Put in other codes and rebooted.That got me back to where I was before with what looks like 1024x768. That's good. I tried to enable effects to make the most of the Nvidia but it wouldn't have it. Anyway I'm more than satisfied with it as it is. Many thanks for your help.

---

