---
title: "Laptop Dual monitor setup issue"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by raphaeltsr on 2010-01-11
Hello,

I'm trying to setup this dual monitor on my laptop but I can only get them to work as mirror screens. Laptop is 15" and Monitor is 17" and the card is Intel one. (fresh 9.10 install)

It automatically detected both of them and made them work as mirror screens. As I try to change this settings both of the screens go black (system still running ok). Then I wait the 30s and it goes back normally to the mirror screens.

So, I'd like to make them work as separate screens. Laptop mode should be 1280x800 and monitor should be 1280x1024.

Here is my xrandr output.

> raphaeltsr@raphael-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 340mm x 270mm
   1280x1024      75.0 +
   1024x768       75.1*    70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0 +
   1024x768       85.0     75.0     70.1     60.0* 
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV1 disconnected (normal left inverted right x axis y axis)
I've tried changing the mode via xrandr but I can't get them two work good on different modes, only on a common one.

Bellow a screenshot of my actual mirror screen config.
[IMG]http://img35.imageshack.us/img35/4361/screenshotdisplayprefert.png[/IMG]

And the next two screenshots of how I'd like them to be working.
[IMG]http://img35.imageshack.us/img35/9703/screenshotdisplaypreferj.png[/IMG]

[IMG]http://img35.imageshack.us/img35/3268/screenshotdisplaypreferr.png[/IMG]

Sorry for this long post, but the configs screens and xrandr output made it so.


Thank you in advance for any help on getting this solved. :)

---

### Post by irishbreakfast on 2010-01-14
I've had some success using F8 to cycle through the screen 'modes' on my laptop until I get the one I want.

---

### Post by MoarningSun on 2010-01-14
I fiddled with xrandr too to get my dual monitor setup to work properly. I assume both monitors work in the preferred resolution when the other screen is set to 'off'? Maybe you have to adapt the virtual resolution of your system in the file "/etc/X11/xorg.conf" (although my Ubuntu 9.10 asks me to change this automatically) 
My config has only the following entry:
```
Section "Screen"
    Identifier    "Configured Screen Device"
    SubSection     "Display"
        Virtual    2680 1200
    EndSubSection
EndSection
```In my case the virtual resolution is 2680x1200 to allow for different configurations. I believe yours should be 2560x1024 minimally. Please check on this. Also try to log out or even restart and log back in to have the changes have affect (this is one the few occasions where my Ubuntu had any benefit from doing so).

---

