---
title: "GUI display problem in local windows machine when using ssh"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by botot on 2010-06-06
Hi,

I was trying to use setup a Windows machine to connect to a remote Ubuntu host by using ssh. So I installed the Cygwin/X package according to the website instruction. I hope to be able to view the GUI windows, such as Firefox when I use the local Windows machine.

I can log into the Ubuntu machine using either
```
ssh username@machinename
```or  ```
ssh -X username@machineame
```but when I type in command firefox, error will return and say:
```
Gtk-WARNING **: cannot open display:
```But if I type in
```
export DISPLAY=:0
```and try to call firefox again, a firefox window will be opened on the **remote** Ubuntu machine, but I still cannot see it on my local Ubuntu machine.

Does anyone can help on this, please? I am really new to linux and cannot figure out what the problem is. I tried using PuTTY as well, and ran into the same problem... Is there any setting that I need to change on the host Ubuntu machine?

Thanks very much!

---

### Post by nubee602 on 2010-06-06
Use team viewer for linux works perfectly without all the hassle. I am running the latest distro maveric and it is awesome:guitar:

---

### Post by lisati on 2010-06-06
> **nubee602 said:**
> Use team viewer for linux works perfectly without all the hassle. I am running the latest distro maveric and it is awesome:guitar

Please use the default font for the forum unless you're highlighting something. 

By the way, "Maverick" isn't the latest official release, it's still in testing/development.

---

### Post by botot on 2010-06-06
Thanks nubee602... will try it.

but I really hope to do it through the X server

---

