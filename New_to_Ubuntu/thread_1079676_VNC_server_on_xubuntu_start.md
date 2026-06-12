---
title: "VNC server on xubuntu start"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by 4JOKE4 on 2009-02-24
I need to setup vncserver to run when Xubuntu automaticaly logon.

I have script "**vncserver**". I tryed to put link of this script to **rc3.d** as S99vncserver. When Xubuntu starts nothing happen. I also tryed command "**update-rc.d S99vncserver**", but that didn't helped too.

Then I tryed to open Applications/Settings... /**Autostarted Apps** and put there command "**vncserver**". But everythime when I started Xubuntu, it run vncserver **6 times**... I don't understand that...

Can somebody help me ?!

---

### Post by Peter09 on 2009-02-24
The trouble with VNC is that it needs you to be logged in the host before it really runs properly. Have you tried ssh? What are you actually trying to do?

---

### Post by 4JOKE4 on 2009-02-25
I don't need to run VNC before logging in.... I only need to run VNC, when Xubuntu is completely started and all services are loaded.

---

### Post by Peter09 on 2009-02-25
You should not need to do anything, goto System->Admin->Login and enable the remote login function. This should give your remote access to the machine.

---

### Post by 4JOKE4 on 2009-02-25
No, I don't need that. I have installed REAL VNC and I need to run this VNC by command "vncserver"...

---

### Post by Peter09 on 2009-02-25
I do not know XUbuntu at all, this would be done in the System->Preferences->Session menu in Ubuntu where you can enter command lines to run at the start of your session.

---

### Post by 4JOKE4 on 2009-02-27
Yes I know, but I didn't find any Session menu in Ubuntu. I only found "Autostarted Apps", but as I said, It ran vncserver 6 times at start.

---

### Post by Peter09 on 2009-02-27
Beware, you may be just seeing a multithreaded task. Many task spawn threads which are also labeled as the same name as the original task.

---

