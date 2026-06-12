---
title: "Screen resolution resets after reboot"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by donescamillo on 2009-10-03
Hi,

I installed XUBUNTU on my PC. The installation set the resolution to 1280x800. I changed to 1024x768, but the change did not persist after reboot, it went back to 1280x800. 
When I install UBUNTU on this same PC I dont have this problem. I change to 1024x768 an i stays there. Clearly it is a problem with XUBUNTU.
But I want to work with XUBUNTU as the PC is old and weak for UBUNTU  :(.
How can I fix this problem?

Thank you
donescamillo

---

### Post by GeneralSpecific on 2009-10-22
I have the same problem, and it seems others have been as well:
[INDENT](check out the links)[/INDENT]

I was able to find a quick and dirty workaround for my install, but it was specific to **Fluxbox**.
You may be able to adapt it to **Xfce**...

[http://ubuntuforums.org/showthread.php?t=686326&highlight=xubuntu+screen+resolution+problem+reset]("http://ubuntuforums.org/showthread.php?t=686326&highlight=xubuntu+screen+resolution+problem+reset")

[INDENT]I added the line:

```
xrandr -s 1024x768
```

to my ~/.fluxbox/startup file[/INDENT]



A few other possible solutions:
[INDENT]It seems that for many people updating their _video drivers_, or editing their _xorg.conf_ file helped...

[http://ubuntuforums.org/showthread.php?t=1168840&highlight=xubuntu+screen+resolution+problem+reset]("http://ubuntuforums.org/showthread.php?t=1168840&highlight=xubuntu+screen+resolution+problem+reset")

Or trying _this command_ in Terminal:
```

sudo dpkg-reconfigure xserver-xorg
```

[http://ubuntuforums.org/showthread.php?t=974511&highlight=xubuntu+screen+resolution+problem+reset]("http://ubuntuforums.org/showthread.php?t=974511&highlight=xubuntu+screen+resolution+problem+reset")[/INDENT]

If you are using older hardware, I recommend Fluxbox. 
It can be easily added to Ubuntu or Xubuntu,
and in my experience it used 70mb less ram than even Xfce!

If you need any other help or advise, just ask.

-Ryan

---

