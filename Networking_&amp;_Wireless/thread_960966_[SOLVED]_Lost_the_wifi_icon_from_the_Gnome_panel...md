---
title: "[SOLVED] Lost the wifi icon from the Gnome panel.. how do I get it back?"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by vi1985 on 2008-10-27
Hey folks,

This comes from somewhat of a linux beginner. My issue is that I've made some changes to the Gnome Panel (v.2.22.2), and accidentally removed the wifi icon that was there. For some reason I can't get it back, and I'm not sure which program it stands for, so that I could create a launcher for it. In the meanwhile I partially learned how to use the iwconfig and iwlist programs, but due to a lack of knowledge I can't get the same functionality as I did using the program that was opened by the wifi icon... please, help me get it back :)

Thanks for your time,
vic.

---

### Post by nixscripter on 2008-10-28
It's called the network manager applet. Open a terminal and make sure it comes back with: ```
nm-applet
```

You should also make sure that the applet is enabled in: System -> Preferences -> Sessions -> Startup programs.

---

### Post by vi1985 on 2008-10-29
Great, thank you!

While this didn't solve the problem, it did provide some google-able information. Funny thing, the applet was already running, but the UI was completely inaccessible... After a bit of nosing around, the solution was found in the forum here: [link]("http://ubuntuforums.org/archive/index.php/t-109524.html").

thanks again :)

---

