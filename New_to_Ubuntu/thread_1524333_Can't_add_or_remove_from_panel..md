---
title: "Can't add or remove from panel."
date: 2010-07-05
forum: New to Ubuntu
---

### Post by Stormed on 2010-07-05
I am a new Ubuntu/Linux user. I have installed the netbook remix on my laptop. I couldn't figure out how to switch to desktop mode. So I did the following things:


[LIST]
[*]Start-up Applications and disabled Maximus Window Manager and Netbook Launcher.
[*]gconf-editor and tried to check "show_desktop" but it said the key was locked, so I did sudo gconf-editor to turn it on.
[/LIST]
Now I have my desktop but my panel has that annoying Maximus Window Manager icon. If I click it then the maximus window management opens. "Remove From Panel" is grayed out and there is no "Add to Panel" option. If I use "sudo debconf gnome-panel" then the panel I want starts up. Although it is under root user, and my old panel keeps running. 

Can anyone help me out please? I just want to remove the Maximus Window Management/Netbook icon from the panel and add the Applications, Places and System items. How do I fix this silly restricted Panel?

Thank you for any help,
Stormed

---

### Post by kerry_s on 2010-07-05
log out
select your user
in the session menu select gnome
put your password & log in

---

### Post by Stormed on 2010-07-05
Great! Thank you!

---

