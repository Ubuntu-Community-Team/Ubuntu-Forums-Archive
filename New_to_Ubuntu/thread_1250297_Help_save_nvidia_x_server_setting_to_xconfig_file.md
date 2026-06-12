---
title: "Help: save nvidia x server setting to xconfig file"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by aljoriz on 2009-08-26
I am using a nvdia ge6100 and updated the driver.  

When I try to save display resolution (800x600 to 1024x76 using the 'save to x configuration file' button.  I would get this error:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

Can someone help?
                                                                                                   
                                              [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]

---

### Post by NoaHall on 2009-08-26
You'll have to open /etc/X11/xorg.conf and take the config from nvidia and copy and paste into the file using sudo gedit /etc/X11/xorg.conf

---

### Post by zerhacke on 2009-08-26
> **NoaHall said:**
> You'll have to open /etc/X11/xorg.conf and take the config from nvidia and copy and paste into the file using sudo gedit /etc/X11/xorg.conf

Pray tell, what config does nVidia supply with their drivers?

---

### Post by NoaHall on 2009-08-26
I mean the setting you get from nvidia x server... which I guess is what he means.

Save to X configuration file -> Show preview
Copy the text shown there, go to terminal and type "sudo gedit /etc/X11/xorg.conf" , paste in what you copyed, and restart.

---

### Post by marshmallow1304 on 2009-08-26
You need to run NVIDIA settings as root in order to save to xorg.conf.
```
gksu nvidia-settings
```
You can also edit the menu entry if you don't want to type that every time.

---

### Post by aljoriz on 2009-08-26
@zerhacke:
My default resolution was 800x600 I was hoping that by saving changes to the xconf file I would have a 1024x768 resolution immediately from boot.

Thank so much, this is why I love ubuntu...  the support from fellow users is great (assuming you have the internet)

---

