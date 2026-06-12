---
title: "No route to host ? (Glenview)"
date: 2017-05-07
forum: Networking &amp; Wireless
---

### Post by oygle on 2017-05-07
Getting an error msg - 'No route to host" in Glenview when I open a .png file. Here is the system.log ..(critical errors)

```

8/05/2017 11:53 AM	**************	org.kde.kiod5[1318]	org.kde.kio.kpasswdserver: User = "" , WindowId = 0

8/05/2017 11:53 AM	**************	org.kde.KScreen[1318]	kscreen: Primary output changed from KScreen::Output(Id: 98 , Name: "VGA-1" ) ( "VGA-1" ) to KScreen::Output(Id: 98 , Name: "VGA-1" ) ( "VGA-1" )

8/05/2017 11:54 AM	*************	org.kde.KScreen[1318]	message repeated 31 times: [ kscreen: Primary output changed from KScreen::Output(Id: 98 , Name: "VGA-1" ) ( "VGA-1" ) to KScreen::Output(Id: 98 , Name: "VGA-1" ) ( "VGA-1" )]
```

Tried opening the same file in Ocular, ImageMagick and Gimp; no popup error message, but they all created entries in system.log

[ATTACH=CONFIG]274997[/ATTACH]

---

### Post by oygle on 2017-05-08
I don't think this is a Glenview thing at all now. This morning I was watching the logs and these 2 entries appeared as soon as I clicked on a path name that is remote ..

> 
[COLOR="#FF0000"]9/05/2017 9:20 AM	*************	org.kde.kiod5[1355]	org.kde.kio.kpasswdserver: User = "" , WindowId = 25165828
9/05/2017 9:20 AM	*************	org.kde.kiod5[1355]	org.kde.kio.kpasswdserver: User = "" , WindowId = 0[/COLOR]


It's a path name to a computer on the LAN. (I have openssh-server installed). Dolphin displayed 'No route to host' also, after attempting to click on the path name.

Found some other references ..

[http://opensuse.14.x6.nabble.com/system-log-fill-up-with-org-kde-passwdserver-td5077655.html](http://opensuse.14.x6.nabble.com/system-log-fill-up-with-org-kde-passwdserver-td5077655.html)

[https://www.mail-archive.com/kde-bugs-dist@kde.org/msg115329.html](https://www.mail-archive.com/kde-bugs-dist@kde.org/msg115329.html)

[http://www.linuxquestions.org/questions/linux-networking-3/samba-refuses-all-passwords-4175598130/page2.html](http://www.linuxquestions.org/questions/linux-networking-3/samba-refuses-all-passwords-4175598130/page2.html)

---

