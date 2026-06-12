---
title: "how do i use my scripts in kubuntu"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-05-02
i have scripts that i wrote to use under nautlis gnome file manager and thundar how do i use them under dolphin kubuntu's file manager

i found this
[http://tuxtweaks.com/2010/04/customizing-file-manager-menus-in-kde4/](http://tuxtweaks.com/2010/04/customizing-file-manager-menus-in-kde4/)

i have it setup like
/home/acer/.kde/share/kde4/services/ServiceMenus/encrypt.desktop

[Desktop Entry]
Encoding=UTF-8
ServiceTypes=KonqPopupMenu/Plugin,image/*
TryExec=/home/acer/.gnome2/nautilus-scripts/_Encrypt-Decrypt
Type=Service
Actions=encrypt-decrypt;
TryExec=/home/acer/.gnome2/nautilus-scripts/_Encrypt-Decrypt

[Desktop Action watermark]
Name=encrypt-decrypt
Icon=ksplash
Exec=/home/acer/.gnome2/nautilus-scripts/_Encrypt-Decrypt %f

nothing shows up

---

