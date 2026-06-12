---
title: "teamviewer q"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by neil_1 on 2011-06-16
synopsis
i have teamviewer installed ,
my friend has teamviewer installed on her _windows_
problem
i can see and control her desktop
she cant see my desktop (all she gets is a blank screen)

do i need to install some plugin or something ?

---

### Post by GWBouge on 2011-06-16
What version of Windows is she running, and is it up to date?  Are you at the computer when she tries to access it?

My first thought was to check your Remote Control/Presentation options to make sure you're sharing the right desktop/workspace, but I also came across [this]("http://www.qlickcafe.com/blogs/qlick-solutions/how-to-deal-with-teamviewer-blank-screen-problem/"), which suggests that the Teamviewer connection isn't killing the screensaver on the remote end, and just displaying a black screen to the guest.

---

### Post by neil_1 on 2011-06-16
> **GWBouge said:**
> What version of Windows is she running, and is it up to date?  Are you at the computer when she tries to access it?

My first thought was to check your Remote Control/Presentation options to make sure you're sharing the right desktop/workspace, but I also came across [this]("http://www.qlickcafe.com/blogs/qlick-solutions/how-to-deal-with-teamviewer-blank-screen-problem/"), which suggests that the Teamviewer connection isn't killing the screensaver on the remote end, and just displaying a black screen to the guest.
win7
yes im at the comp when she tries to access it 
everything in options is set to allow

---

### Post by neil_1 on 2011-06-21
*bump*
anyone ?

---

### Post by BugBuster on 2011-06-21
Try after disabling the Desktop Effects on your Ubuntu system if they are enabled.

---

### Post by howefield on 2011-06-21
Try toggling the xdamage option.

Press the Alt + F2 keys and type

```
gconf-editor
```

Navigate to desktop > gnome > remote_access > disable_xdamage. If it doesn't work, easy enough to go back and uncheck. You may need to reboot for the option to take effect.

---

### Post by jakrzys on 2011-07-01
> **howefield said:**
> Try toggling the xdamage option.

Press the Alt + F2 keys and type

```
gconf-editor
```Navigate to desktop > gnome > remote_access > disable_xdamage. If it doesn't work, easy enough to go back and uncheck. You may need to reboot for the option to take effect.

Dosn't help :(

---

### Post by neil_1 on 2011-07-21
> **jakrzys said:**
> Dosn't help :(
same

---

