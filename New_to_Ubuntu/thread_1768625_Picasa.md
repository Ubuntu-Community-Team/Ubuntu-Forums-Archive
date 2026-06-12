---
title: "Picasa"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by Grierson on 2011-05-27
As a total novice I recently installed Ubuntu 11.04. No problem with that however when I downloaded Picasa I see the icon in 'Applications' but it will not launch. I downloaded Gimp which works fine. Can anyone suggest what I am doing wrong. - John

---

### Post by frankbooth on 2011-05-27
How did you install it?
There's a guide for installing Picasa on 11.04 at:

[http://blog.sudobits.com/2011/04/24/how-to-install-picasa-on-ubuntu-11-04/](http://blog.sudobits.com/2011/04/24/how-to-install-picasa-on-ubuntu-11-04/)

---

### Post by hakermania on 2011-05-27
If you mean the image management application from google, then the error is that the shortcut isn't installed properly.
So, create a file containing the following and make it executable:
```

echo "[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Picasa
Comment=The Photo Organizer from Google
Exec=/opt/google/picasa/3.0/bin/picasa
Terminal=false
Icon=/opt/google/picasa/3.0/desktop/picasa.xpm
Type=Application" > /usr/share/applications/picasa.desktop

```
Run it as root and then try to rerun the picasa. If this won't work, you can always run picasa by giving Alt+F2, typing picasa and pressing enter

---

### Post by Grierson on 2011-05-27
Thank you for the replies. I did install the software via the Software Centre but I have now copied this script from the location suggested by frankbooth:  
wget [http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb](http://dl.google.com/linux/deb/pool/non-free/p/picasa/picasa_3.0-current_i386.deb) sudo dpkg -i picasa_3.0-current_i386.deb

and I have un-installed Picasa and installed it again from the Command Line. It now appears
to work perfectly. I am grateful to you both for taking the time to respond - John

---

