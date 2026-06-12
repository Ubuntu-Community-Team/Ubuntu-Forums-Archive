---
title: "I accidently removed the network manager applet from the panel."
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by volksolwagen57 on 2007-04-12
i was customizing my panels to make eyecandy on my desktop and for some reason i removed the nm-applet (network monitor) from the panel. internet was working fine so i didn't use it. come reboot time i can't connect to the internet.
what i noticed from the applet is that I need to manually connect my wired connection. i tried to second click on the panel to try to add the applet again and it's not there. to get around this, in my own boneheaded way, i created a new user and switched to it. viola! it's there and i connected it manually and switched back. this is the only way i've been able to use the internet and it's annoying. 
i would like to use the applet because it's got a lot of cool features and plus, i can turn my internet connection off when i'm not using it.

How can i get the applet to show on my panel on bootup?
I tried to run "nm-applet" in the terminal and i get errors stating that the "spin" icon could not be found (i am using a different theme and i customized a lot of icons and i don't want to change it back).
Can anyone help? Thanks for your time.

---

### Post by Ateo on 2007-04-12
System -> Preferences -> Sessions

There, verify that Network Manager exists and is checked. If you must created it, the default command is 'nm-applet --sm-disable', which you can also execute from terminal to get the applet without restarting your gnome session.

HTH

---

### Post by volksolwagen57 on 2007-04-12
aha! thanks!

---

### Post by nike984 on 2007-04-12
or if it doesn't help,
add a applet to the panel, named "notification area" and restart gnome.
Network manger is in Notification area.

---

### Post by balayyoub on 2008-05-20
thank you very much
you are a life saver

---

