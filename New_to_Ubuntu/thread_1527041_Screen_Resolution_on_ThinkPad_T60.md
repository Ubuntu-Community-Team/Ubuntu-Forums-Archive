---
title: "Screen Resolution on ThinkPad T60"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by mtickle on 2010-07-08
Hello everyone,

I am new to Ubuntu, coming over from the Windows world. I am excited to see how far Linux has come and am really getting a kick out of NOT using Windows.

I have successfully installed 10.04 on an IBM ThinkPad T60, but I am unable to get a screen resolution greater that 1024x768. I'd really like to be at least 1280x1024, which I know this laptop supports in Windows.

I've done quite a bit of searching, but everything I can come up with involves modifying the "xorg.conf" file, which does not exist in this build. Is there some other way to trick the OS to thinking that a higher resolution is available, or are there some third-party drivers?

Thanks,
Mike

---

### Post by tgalati4 on 2010-07-08
What type of graphics card on your machine?  Open a terminal and post the following:

lspci | grep VGA

---

### Post by mtickle on 2010-07-08
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by LowSky on 2010-07-09
> **mtickle said:**
> VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
Just to point out the T60 had many options for screen sizes and 1280x1024 wasn't an option. Windows might allow you to use it but it isn't a native screen resolution.

Displays
[LIST]
[*]14.1" TFT display with 1024x768 resolution
[*] 14.1" TFT display with 1400x1050 resolution
[*]15.0" TFT display with 1024x768 resolution
[*]15.0" TFT IPS display with 1400x1050 resolution
[*]15.0" TFT IPS display with 1600x1200 resolution
[*]15.4" TFT display with 1680x1050 resolution (widescreen)
[/LIST]

It also had many options for graphic chips, for instance mine has a ATI x1300

[http://www.thinkwiki.org/wiki/Category:T60](http://www.thinkwiki.org/wiki/Category:T60)

---

### Post by mtickle on 2010-07-09
Thanks for the tips, achuowner and LowSky. It looks like this T60 series (1953) really only supports 1024x768. I still will use it over a Windows PC any day of the week.

Thanks again!

-Mike

---

### Post by tgalati4 on 2010-07-09
If you run 1280x1024 in Windows is the display crisp?  Are text characters rendered clearly?  Normally you run a laptop LCD at its native resolution to get the best display.  My T43p has an ATI FireGL card and it runs at 1400x1050.

---

