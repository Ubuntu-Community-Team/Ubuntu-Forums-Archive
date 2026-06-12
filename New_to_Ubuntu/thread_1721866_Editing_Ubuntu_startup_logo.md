---
title: "Editing Ubuntu startup logo?"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-04-05
You know that purple screen that shows up when you are booting Ubuntu and it has the word "Ubuntu" in white with a few dots underneath it?

Is there a way to edit that?  Is it a file?

---

### Post by jtarin on 2011-04-05
[If you have Lucid 10.04.]("http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html") (read the comments for further info)

---

### Post by Learning Linux 2011 on 2011-04-06
> **Learning Linux 2011 said:**
> You know that purple screen that shows up when you are booting Ubuntu and it has the word "Ubuntu" in white with a few dots underneath it?

Is there a way to edit that?  Is it a file?


I think I found part of it, located in:
/lib/plymouth/themes/ubuntu-logo

That seems to have the actual word "Ubuntu" in white and the dots that change color.

Not sure about the purple background yet.

---

### Post by Learning Linux 2011 on 2011-04-06
There is something called "ubuntu-logo.script".

I wonder if that determines the color?

---

### Post by jtarin on 2011-04-06
> **Learning Linux 2011 said:**
> There is something called "ubuntu-logo.script".

I wonder if that determines the color?Did you read and try the link I posted?????

---

### Post by Learning Linux 2011 on 2011-04-06
> **jtarin said:**
> Did you read and try the link I posted?????


Yes, I did.  

I appreciate the effort, but none of that was relevant. 

That page was for changing GNOME at the login screen.  I am referring to what happens before that.

---

### Post by wojox on 2011-04-06
[[HOWTO] Change Ubuntu Pink/Purple Plymouth Boot screen to any color you like]("http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html") like this?

---

### Post by Learning Linux 2011 on 2011-04-06
> **wojox said:**
> [[HOWTO] Change Ubuntu Pink/Purple Plymouth Boot screen to any color you like]("http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html") like this?


Yes, I think that is closer to what I am talking about.

I'm pretty sure the color is located in the ubuntu-logo.script, but it is in terms of numbers, like red=16, blue=0, green=12, etc. rather than just "purple"
so I guess I will have to mess around with those numbers to change the actual color

And I am pretty sure that the white Ubuntu logo and the dots that change colors are located in /lib/plymouth/themes/ubuntu-logo, so those could be changed too.

---

### Post by bodhi.zazen on 2011-04-06
> **Learning Linux 2011 said:**
> Yes, I think that is closer to what I am talking about.

I'm pretty sure the color is located in the ubuntu-logo.script, but it is in terms of numbers, like red=16, blue=0, green=12, etc. rather than just "purple"
so I guess I will have to mess around with those numbers to change the actual color

And I am pretty sure that the white Ubuntu logo and the dots that change colors are located in /lib/plymouth/themes/ubuntu-logo, so those could be changed too.

This chart might come in handy

[http://www.web-source.net/216_color_chart.htm](http://www.web-source.net/216_color_chart.htm)

[http://www.avatar.se/molscript/doc/colour_names.html](http://www.avatar.se/molscript/doc/colour_names.html)

[http://www.easyrgb.com/index.php?X=HARM](http://www.easyrgb.com/index.php?X=HARM)

---

### Post by REMIX8604 on 2011-04-06
yea i install some program called plymouth splash screen and logger. them i uninstalled the purple ubuntu logo and found another one in the list called solar ubuntu logo. that one looks awesome! i did this all in the software center, just search for plymouth. since i updated to 11.04 beta 1. it hasnt shown it on start up only on shut down. anyways good luck

---

### Post by jmszr on 2011-04-06
Learning Linux 2011,

This may be of help: [https://launchpad.net/plymouth-manager/+download](https://launchpad.net/plymouth-manager/+download).
After installation it is found under Applications > System Tools

Or perhaps this: [http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html](http://www.khattam.info/howto-change-ubuntu-pinkpurple-plymouth-boot-screen-to-any-color-you-like-2010-11-09.html) .

---

