---
title: "Cant save resolution on Revo 3610"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by tdlucas on 2010-02-26
i have just installed Ubuntu 9.10 on the above machine. After installation the resolution choices were limited to 800x640 and below so I installed the NVIDIA driver.

Now i go to system > preferences > display and get the message 'It appears that your graphics driver does not support the necessary extensions to use this too. Do you want to use your graphics driver vendor's tool instead?'

On selecting 'yes' the NVIDIA X server settings window is launched. I choose 1024x768 in the X server Display configuration window and then attempt to 'save to X configuration file' but get the message 'failed to parse existing X config file '/etc/X11/xorg.conf''

Subsequently the settings aren't saved and every time I reboot I'm back to 800x600.

Any help please would be greatly appreciated.

Many thanks

---

### Post by cariboo on 2010-02-27
Run nvidia-settings as root, and you'll be able to save the settings. Press Alt-F2 and type:

```
gksu nvidia-settings
```

The above command will allow you to save the changes you make.

---

### Post by tdlucas on 2010-02-27
Thanks very much indeed. That seems to have done the trick. As a matter of interest, why did that work but I was unable to save the configuration by the previous method?

Anyway, I'm now trying to use via HDMI connected to a Samsung LCD TV (LA32R71BX) for home theatre use (which is the ultimate aim) but on every resolution setting the desktop is too big. It seems to have recognised that the TV is a Samsung but that's as far as it goes.

Any thoughts?

Thanks in advance.

---

