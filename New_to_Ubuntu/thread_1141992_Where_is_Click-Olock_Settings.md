---
title: "Where is Click-Olock Settings?"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Muggz on 2009-04-28
Where are the settings for click-lock in 9.04? Anybody know?

---

### Post by MontelEdwards on 2009-04-28
> **Muggz said:**
> Where are the settings for click-lock in 9.04? Anybody know?
Umm, What?

---

### Post by Muggz on 2009-04-28
Eg.,:
[http://clicklock-ppc.mac.findmysoft.com/](http://clicklock-ppc.mac.findmysoft.com/)
[http://www.microsoft.com/windowsxp/using/accessibility/clicklock.mspx](http://www.microsoft.com/windowsxp/using/accessibility/clicklock.mspx)

Common accessibility feature. It's been around 10+ years. I've never used a mouse/trackball supported PC where it wasn't supported.

---

### Post by dgzimmerman on 2009-04-30
Up to Ubuntu 8.10 this was handled in the etc/X11/xorg.conf file

See the following link:

[http://www.xfree86.org/current/mouse5.html](http://www.xfree86.org/current/mouse5.html)

Now everything has changed. In my xorg.conf file in Ubuntu 9.04 the lines pertaining to the mouse are commented out (* at start of line to disable the following instructions).  there's also comment that these functions are now handled by HAL the hald demonn.  I'm still trying to find out how to achieve this function in Ubuntu 9.04

in the meantime, you can try the dwell click function under System>Preferences>Assistive Technologies> Mouse Accessibility>Dwell click

I'm trying to learn to use it. It seems awkward compared to the old drag lock buttons.

Does anyone else have anything to add?

---

### Post by dgzimmerman on 2009-06-06
> **Muggz said:**
> Where are the settings for click-lock in 9.04? Anybody know?

I've got drag lock working now with my Kensington Expert mouse on Ubuntu 9.04 Help came from these threads:

[INDENT][http://ubuntuforums.org/showthread.php?t=1058482](http://ubuntuforums.org/showthread.php?t=1058482)

[http://ubuntuforums.org/showthread.php?t=1034803](http://ubuntuforums.org/showthread.php?t=1034803)[/INDENT]

I ran the following command:

[INDENT]dale@dale-desktop:~$ lshal | grep input.product[/INDENT]

Here's the results:

[INDENT]input.product = 'Macintosh mouse button emulation'  (string)
input.product = 'Power Button (CM)'  (string)
input.product = 'Power Button (FF)'  (string)
input.product = 'PC Speaker'  (string)
input.product = 'Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)'  (string)
input.product = 'InSync Speech Technologies Buddy USB 5G'  (string)
input.product = 'Kensington      Kensington Expert Mouse'  (string)
input.product = 'Microsoft Microsoft? Digital Media oard 3000'  (string)
input.product = 'Microsoft Microsoft? Digital Media oard 3000'  (string)
[/INDENT]

note the line with the Expert Mouse.  I copied the exact name of the Kensington Expert mouse from between the single quotes, and used it in between the double quotes on the second line of the fdi file below.

I created a new fdi file named draglock.fdi in the /etc/hal/fdi/policy directory as follows:


[INDENT]gedit /etc/hal/fdi/policy/draglock.fdi[/INDENT]

I typed the following text into the file:

[INDENT]<?xml version="1.0" encoding="UTF-8"?> 

<match key="info.product" string="Kensington      Kensington Expert Mouse">

<merge key="input.x11_options.DragLockButtons" type="string">2 1</merge>

<merge key="input.x11_options.Buttons" type="string">8</merge>

</match>
[/INDENT]
The above info was taken from /etc/X11/xorg.conf where I used to configue my drag block buttons.

[INDENT]# commented out by update-manager, HAL is now used

#Section "InputDevice"

#    Identifier     "Configured Mouse"

#    Driver         "mouse"

#    Option         "CorePointer"

#    Option         "DragLockButtons" "2 1"

#    Option         "Buttons" "8"

#EndSection
[/INDENT]

Following a restart, my Kensington Expert Mouse worked as desired!

I hope this helps someone else.

---

