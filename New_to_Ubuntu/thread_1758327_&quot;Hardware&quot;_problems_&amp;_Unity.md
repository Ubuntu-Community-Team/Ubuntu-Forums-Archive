---
title: "&quot;Hardware&quot; problems &amp; Unity"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by leng215761 on 2011-05-14
I'm new to Ubuntu and just loaded 11.04 to boot from within Windows 7. Got a message that Ubuntu was switching me to the "classic" desktop view because of some "hardware" problem with my system. That was all the information provided. How can I research and resolve this problem?

---

### Post by coffeecat on 2011-05-14
Probably your graphics card, or at least the graphics card/driver combination. It must be 3d capable. The commonest issue here is with nvidia cards - the default open source nouveau driver doesn't support 3d out-of-the-box, and you have to install the proprietary driver or an experimental package. Most Intel and ATI cards will give you Unity out of the box with their respective open source drivers.

What graphics card do you have?

By the way, welcome to the forum. :)

---

### Post by ajgreeny on 2011-05-14
I got the same on my desktop with an ATI 9200SE card, even though it will run compiz fully with no problems.

Having booted to natty, open a terminal and copy or type ```
/usr/lib/nux/unity_support_test -p
```which will give you some output with several yes/no answers.  Any "no" in the list and unity will not run, I'm afraid.

You can however, download unity-2d and use that to give you a taste of what unity will be like, more or less, though it is a bit of a hybrid between the two as far as I can see, allowing icons on the desktop along with the launcher on the left hand side of the screen.

---

### Post by leng215761 on 2011-05-14
FYI, the graphics card I'm using is: NVIDA GeForce 9400 GT with a driver dated 2011.

---

### Post by coffeecat on 2011-05-14
You have a nvidia card. Go to System > Administration > Additional Drivers. See if it is offering you a proprietary nvidia driver. If so, enable that (it will take a few minutes) and then reboot.

When you get to the login screen, enter your username but before you enter your password, check the popup at the bottom of the screen. Make sure that "Ubuntu" is checked, enter your password and you should be taken to the Unity desktop.

---

### Post by leng215761 on 2011-05-14
Run the suggested utility and got three "No's": 
    Not software rendered
    GLX texture from pixmap
    Unity Supported

Other than Unity is not working, not sure what this is telling me or how/if I can fix the problem.

---

### Post by coffeecat on 2011-05-14
> **leng215761 said:**
> Run the suggested utility and got three "No's": 
    Not software rendered
    GLX texture from pixmap
    Unity Supported

Other than Unity is not working, not sure what this is telling me or how/if I can fix the problem.

Look at my post just before yours and enable the proprietary driver the way I describe.

---

### Post by leng215761 on 2011-05-15
Wonderful! Down loaded a proprietary driver as you suggested and the problem was solved. Can't thank you enough.

---

### Post by coffeecat on 2011-05-15
Glad it's working. Now you've got the Unity desktop, here's a useful couple of links for you:

[http://omgubuntu.co.uk/natty/](http://omgubuntu.co.uk/natty/)

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

Happy Ubuntu-ing!

---

