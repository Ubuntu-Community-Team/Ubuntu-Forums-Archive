---
title: "Talking to another computer"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Powdah on 2010-01-11
Is there a program that will allow me to connect my linux ubuntu laptop to my Windows XP desktop so I can log into files and run programs?

thks from a major newbie

---

### Post by DamenW on 2010-01-11
are you looking for a graphical interface like Remote Desktop or a text base command line style?

---

### Post by Powdah on 2010-01-12
Remote desktop

---

### Post by Darce on 2010-01-12
Hello Powdah,

I do exactly what your after using RealVNC installed on a WinXP machine at a remote site. You can D/L it free from here :

[http://www.realvnc.com/products/download.html](http://www.realvnc.com/products/download.html)

Once you've downloaded, installed, and set it up on your XP machine, go to your Ubuntu machine and go to Applications->Internet->Remote Desktop Viewer

Press 'Connect'

Set the protocol to VNC and punch in your XP machine's IP address into the host box.

Press the (new) 'Connect' button and you should be presented with a password request.

Enter it as you set it up during the RealVNC install and your DONE !!    :)


Cheers,

Tim

---

### Post by HermanAB on 2010-01-12
Enable remote desktop in Windows then do:
$ rdesktop -g 90% windowsboxipaddress

---

### Post by Powdah on 2010-01-12
Thks for help.  This forum is making my switch over much easier.

---

### Post by Dayofswords on 2010-01-12
with remote desktop enabled on windows, you can use the terminal server client that comes with ubuntu(at least in 9.04, forgot if it in 9.10) and choose the RDP protocal.

(not sure about all this, last remote desktop-ed 6 months ago.)

---

