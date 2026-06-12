---
title: "Kubuntu Text Large"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by Revo99 on 2010-03-28
Hello All,

Thank you in advance for your responses. This is a very difficult one to explain.

I have installed Ubuntu 9.10 server. I just installed Kubuntu as my GUI. However all the text is extra large. I cant access any menus as they dont show correctly. An example could be the clock it takes up 1 quarter of the bottom panel.

Any suggestions as this is going to have to be done via command line whatever it is. 

Regards,

Revo99

---

### Post by mgranet on 2010-03-28
You can change your font size settings graphically in System Settings--> Appearance--> Fonts.

---

### Post by underquark on 2010-03-28
You may have your display resolution set too low (which will make everything look bigger) or you may need to adjust the "Dots per inch" setting in Fonts if it is only the text that is too large.

---

### Post by Revo99 on 2010-03-28
Hello,

Thank you for the reply's. Unfortunately everything is too large to make any changes from the GUI. I would have to make them from the command line. Does anyone know how to do this?

Cheers,

Revo99

---

### Post by ankspo71 on 2010-03-28
Hi,
try using either command below in the terminal 
(or press Alt+F2 and enter either command):
```
xrandr -s 800x600
xrandr -s 1024x768
```
 This will temporarily change your screen size. 
Now all you need to do is to change the screen size in 'system settings' so that you will have a permanent setting.
Hope this helps.

---

