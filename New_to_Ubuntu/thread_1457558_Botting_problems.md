---
title: "Botting problems"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by maleleco on 2010-04-18
I am an Ubuntu beginner. I am having a problem booting Ubuntu. I installed a webcam yesterday and it worked great, but when I restart Ubuntu it stays/freezes in the log in screen. However when I unplug the webcam from the usb port and turn the computer back on the Ubuntu will boot as usual. How can I fix this problem? Thanks

---

### Post by Jon Monreal on 2010-04-18
Does everything work if you plug the webcam in and use it after you boot?

Thanks.

---

### Post by maleleco on 2010-04-18
Yes everything works fine after I plug the camera back in. Thanks

---

### Post by Paqman on 2010-04-18
Check the boot order in your BIOS, make sure USB either isn't in the list, or has a lower priority than your hard drive. Having USB devices plugged in can confuse some motherboards if they're set to boot from USB.

---

### Post by Jon Monreal on 2010-04-18
> **Paqman said:**
> Check the boot order in your BIOS, make sure USB either isn't in the list, or has a lower priority than your hard drive. Having USB devices plugged in can confuse some motherboards if they're set to boot from USB.

I would disable it entire if the option is given (after all, he is getting to the login screen before it freezes so it is booting from the HDD).

---

### Post by maleleco on 2010-04-18
I disabled the USB booting option in the BIOS and still does the same thing. As soon as the Ubuntu log in starts, the webcam turns on and then it freezes the the system. It does not go beyond this point. Then I turned the computer off and unplug the usb cable for the camera and started normally.

---

### Post by maleleco on 2010-04-19
Is there any way to disable the webcam, so is not set up as an start up application. I think that the problem is there, because once the ubuntu log in comes up, the camera turns on and the  booting process freezes up and if I unplug the camera it will continue to boot.

---

### Post by spiky001 on 2010-04-19
If you go into system preferences there is a tab start up applications have a look in there for camara then untick it see if that works

---

### Post by maleleco on 2010-04-19
Thanks for your help. I found one that was referring to the camera. I unchecked it and it worked!

---

