---
title: "brightness info of monitor"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by angellika on 2010-05-29
How can I get brightness info of my monitor setting? I did not find it anywhere. I need it to my thesis in cd/m2. I have Karmic Koala on Toshiba Satellite L-515 S4925.

Thanks for any help,

Jaro

---

### Post by angellika on 2010-05-31
bumb

---

### Post by freak42 on 2010-05-31
on a laptop try the brightness applet, with an external monitor I think you well need to use the monitor's own menu to determine brightness/contrast settings

---

### Post by saakeman on 2010-05-31
> **angellika said:**
> How can I get brightness info of my monitor setting? I did not find it anywhere. I need it to my thesis in cd/m2. I have Karmic Koala on Toshiba Satellite L-515 S4925.

Thanks for any help,

Jaro


try compize manager and go to 
* accessible 
*brightness / contras 

--------------------------------------------------------**
** join facebook's dustbin of history **
that's 
** DUSTBIN OF HISTORY ** :)

---

### Post by angellika on 2010-06-01
> **freak42 said:**
> on a laptop try the brightness applet, with an external monitor I think you well need to use the monitor's own menu to determine brightness/contrast settings

I have no brightness applet,  what means according to this page [http://library.gnome.org/users/gnome-power-manager/stable/applets-general.html.en]("http://library.gnome.org/users/gnome-power-manager/stable/applets-general.html.en") that my hardware is not supported. But I made my own way. Brightness is set to 100 % in Power Management so I will use this info without specific cd/m2 info, which is not so important after all.

I was just curious if there is any command in terminal that one can get some brightness value. Here [http://ubuntuforums.org/showthread.php?t=858368]("http://ubuntuforums.org/showthread.php?t=858368") the man found some brightness info, but my system does not have "/proc/acpi/video/VID/LCD/brightness". I found that for Toshiba laptops one can use  command *toshset -lcd*, but this did not work cause my *required kernel toshiba support not enabled.*, so I just let it go. Anyway brightness 100% is 100% info for my ).

Thanks for your hints folks .O

---

