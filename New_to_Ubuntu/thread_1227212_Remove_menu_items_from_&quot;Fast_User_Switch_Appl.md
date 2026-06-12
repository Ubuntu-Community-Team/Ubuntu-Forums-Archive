---
title: "Remove menu items from &quot;Fast User Switch Applet&quot;"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by n.hinton on 2009-07-30
Is it possible to remove &#8220;guest session&#8221;, &#8220;Log Out&#8221; and &#8220;Hibernate&#8221;, from Fast User Switch Applet.

When I installed Jaunty I opted to set it as single user automatic login, don't know if that is relevant!

Since that clean first time install of ubuntu selecting any of the above options causes &#8220;Authentication failed&#8221; when it tries to log me back in.

it would be better to remove these options from the menu to prevent inadvertent selection.

---

### Post by VCoolio on 2009-07-30
In gconf-editor, navigate to apps > fast-user-switch-applet. You can turn off the guest session option, but shutdown, logoff and hibernate are one option, so I guess it's not possible to delete one or two (you'll have to edit /etc/gdm/gdm.conf for that). If you only use shutdown you can also delete the whole applet and make a launcher for that.

---

### Post by n.hinton on 2009-07-30
Thanks VCoolio, its mainly “Log Out” and “Hibernate” that cause the “Authentication failed” I wonder why that should happen?

---

### Post by VCoolio on 2009-07-30
I think several things require your password one way or the other. You can enable automatic login but then (at least in my case) you'll still have to enter your password as soon as e.g. your mail client tries to get your passwords to connect to your mailservers. Maybe that's why logout and hibernate don't work, although it's strange that shutdown does work. Don't know. You could troubleshoot by disabling automatic login in system > administration > login window, then login with your password and see if logout works then.

---

### Post by n.hinton on 2009-07-30
I am using windows to post this as I disabled automatic login in system > administration > login window and now ubuntu will not boot past authentication failed screen how can I re enable automatic login? I can only access the ubuntu file system by booting with ubuntu CD - Please help -

---

### Post by n.hinton on 2009-07-30
have just booted from CD and used gksudo gedit and edited /etc/gdm/gdm.conf-custom

back to

AutomaticLoginEnable=true

all working again

---

### Post by VCoolio on 2009-08-03
You can remove hibernate and suspend from the applet with ubuntu-tweak (in the tab system > power management).

---

