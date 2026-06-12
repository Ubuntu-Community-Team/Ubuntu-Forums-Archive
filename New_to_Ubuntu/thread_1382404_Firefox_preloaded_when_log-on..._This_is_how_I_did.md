---
title: "Firefox preloaded when log-on... This is how I did..."
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Panama2305 on 2010-01-15
Hi friends!!!

I have a way to preload Firefox... As everybody know, if you have activated the option to save the screen when you shutdown, this will keep every single window or application that you have open before shutdown or restart, so, based on this I figured out that if I have mi firefox open before shutdown I will have the firefox open when I logon again, but I didn't wanna have the firefox window open whe I logon (and I thing nobody want this either) and knowing that firefox have an extension to minimize firefox (FireTray) to the system tray I instaled this extension and minimized one window to the system tray and keep it there and everytime I logon I have mi firefox running and this make a new firefox's window open faster, because actually firefox is already running.
The window at the tray have a blank page open. This method is working perfectly for me and is doing the same work as Firefox Preloader do in windows...

Hope this could help you...

Note: I also have installed the PRELOAD through apt-get install preload. Whit these two appication firefox is going to open faster than ever...

[IMG]http://img686.imageshack.us/img686/576/snapshot1n.png[/IMG]
Here the Firefox running at the system tray

[IMG]http://img686.imageshack.us/img686/6748/snapshot2y.png[/IMG]
And here you can see Firefox's new window open and the previous Firefox's windows running at the system tray.

[[URL="https://addons.mozilla.org/en-US/firefox/downloads/latest/4868/platform:2/addon-4868-latest.xpi?src=addondetail"][SIZE=5]_[IMG]https://addons.mozilla.org/en-US/firefox/images/addon_icon/4868/1246274653[/IMG]_[/SIZE]]("https://addons.mozilla.org/en-US/firefox/downloads/latest/4868/platform:2/addon-4868-latest.xpi?src=addondetail")[SIZE=5]Download FireTray 0.2.3[/SIZE][/URL] 

[SIZE=2][COLOR=DarkRed]In the FireTray options you must select ***Start the program minimized.***[/COLOR][/SIZE]


My distro is Kubuntu Netbook 9.10 Karmic Koala :popcorn:

---

### Post by Panama2305 on 2010-01-15
If you like this threat and was worthily for you, please coment...

---

### Post by lovinglinux on 2010-01-16
If works for you then great, but you could have achieved the same result with Autostart.

I'm not using a Netbook, so i don't know if there is any difference, but on regular KDE  go to "System Settings >> Advanced User Settings >> Autostart", then click "Add Program" and select the Firefox from the menu. This way, you don't have to keep Firefox open during shutdown, because it will be started on every boot, independently of your saved session.

While I see the benefit of having Firefox already opened when logging in, I personally don't feel the need to do it. My Firefox, which has 43 extensions installed, starts up in only 5 seconds.

The major problem with Firefox starting/closing times are due to database performance and extra functions performed by extensions during startup or shutdown. If you want some tips on how to optimize it and make it faster (page loading, startup and performance), see [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Ferux on 2010-04-18
I think it is a good idea, but Firetray prevents my Firefox from working..

9.10 Karmic Koala x64, Firefox 3.5.5


Mozilla/5.0 (X11; U; Linux x86_64; nl; rv:1.9.1.5) Gecko/20091109 Ubuntu/9.10 (karmic) Firefox/3.5.5

---

