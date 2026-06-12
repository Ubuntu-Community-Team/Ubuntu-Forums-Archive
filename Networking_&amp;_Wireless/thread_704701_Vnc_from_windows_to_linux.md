---
title: "Vnc from windows to linux"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by larainzlo07 on 2008-02-22
I am trying to set up vnc so that i can access my linux pc from work. Does anyone know of any good guides that show how to set this up?

---

### Post by Rucas on 2008-02-22
Hi mate.
If im not incorrect.

On your Linux Machine you need to enable Remote Desktop (System>Preferences>Remote Desktop
Select both options under sharing.
Under Security DO NOT ENABLE  'ASK YOU FOR CONFIRMATION' this means that u have to be at the Ubuntu machine to allow. Instead just use the Password request.
Now i dont know what program you are using for VNC on the PC, so you may need to see its manual.
Hope this helps.

---

### Post by ahos on 2008-02-22
Hello

I am using RealVNC to access my Ubuntu 6.06 (look at [www.realvnc.com](www.realvnc.com)) and I don`t need to install the VNC server in Win PC. I only need the VNC viewer.

It work fine! :)

---

### Post by larainzlo07 on 2008-02-22
What port do i need to open under my router for vnc to work? Also do i need to install what vnc do i need to install on linux and what vnc do i need to install on my windows OS in order to access linux from windows?

---

### Post by larainzlo07 on 2008-02-25
bump

---

### Post by dmizer on 2008-02-25
here is a very good howto including directions for configuring your windows machine:

[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

keep in mind that using vnc over the internet is unbelievably dangerous unless it's encrypted.  and even then, you're probably better off not using remote desktop unless you absolutely need it.

what are your reasons for wanting to use remote desktop at home?  maybe there's a better alternative for you.

---

