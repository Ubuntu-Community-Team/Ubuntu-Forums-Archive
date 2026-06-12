---
title: "shiretoko (firefox) never updating."
date: 2009-10-20
forum: New to Ubuntu
---

### Post by jarongg on 2009-10-20
so i have had the beta firefox 3.5 running on my ubuntu for a while now. every time ubuntu tries to update, it says there are updates for firefox, firefox 3.5, firefox 3.5 branding, xulrunner 1.9.1, xulrunner 1.9.1 gnome support, xulrunner 1.9.2, xulrunner 1.9.3. about 27 megs worth. but once i download the updates nothing changes and if i run update manager again it will want to download it all again. does anybody else have this problem? do people even still use shiretoko? what can i do to fix this? thanks.

---

### Post by Bachstelze on 2009-10-20
)Open a terminal and paste the output of

```
sudo apt-get upgrade
```

---

### Post by jarongg on 2009-10-20
is that any different than the update manager gui? trying it right now, but everything it wants to upgrade is what i listed earlier. here's hoping it works.

---

### Post by Bachstelze on 2009-10-20
> **jarongg said:**
> is that any different than the update manager gui?

No, but it will let us see in more detail what goes wrong. ;)

---

### Post by jarongg on 2009-10-20
this is the list of errors i received. 

"Error: #include <abstractions/private-files> not found at line 85 in /etc/apparmor.d/usr.bin.firefox-3.5.
Error: #include <abstractions/ubuntu-email> not found at line 181 in /etc/apparmor.d/usr.bin.firefox-3.5.
Error: #include <abstractions/ubuntu-console-email> not found at line 182 in /etc/apparmor.d/usr.bin.firefox-3.5.
Error: #include <abstractions/ubuntu-gnome-terminal> not found at line 186 in /etc/apparmor.d/usr.bin.firefox-3.5."

it appears that almost everything updated. now it is telling me all i need tp update is xulrunner 1.9.1 and xulrunner 1.9.1 gnome support.

---

### Post by Teabicky on 2009-10-20
I used ubuntuzilla to install the latest version of firefox 3.5 with very little hassle.  To update I just run ubuntuzilla again.  Here a link explaining how.

[http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/](http://tombuntu.com/index.php/2009/07/15/install-firefox-35-in-ubuntu-904-using-ubuntuzilla/)

---

