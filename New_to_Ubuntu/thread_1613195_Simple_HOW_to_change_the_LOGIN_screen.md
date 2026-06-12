---
title: "Simple HOW to change the LOGIN screen"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by shuttleworthwannabe on 2010-11-04
[http://www.n00bsonubuntu.net/content/how-to-change-login-screen-ubuntu-1010-maverick-meerkat](http://www.n00bsonubuntu.net/content/how-to-change-login-screen-ubuntu-1010-maverick-meerkat)

I thought it may help some one.

Credit to Source.

Update: the site has moved the original link to the HOWTO, so I have copied and pasted the relevant part here:
> First open a Terminal window (Applications -> Accessories -> Terminal) then copy+paste the following line:

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

Now close the Terminal window and logout, when logged out the Appearance window pops up. Here you can make the changes you want and when your done you can login as usual. To prevent the Appearance Manager from opening when you login, open a Terminal window (Applications -> Accessories -> Terminal) then copy+paste the following line:

sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

S

---

### Post by cariboo on 2010-11-05
Wouldn't it just be easier to copy the picture you want to /usr/share/backgrounds, and rename it warty-final-ubuntu.png?

---

### Post by shuttleworthwannabe on 2010-11-06
I problem was that the login screen did not honor the dpi settings and font preferences set in the GnomeDesktop Environment (under preferences>appearance)--in this way I could get the login screen to look like my rest of the settings.

---

### Post by tajiknomi on 2010-11-06
*[SIZE=2]Thanks for posting this...its much easier way....:P[/SIZE]*

---

