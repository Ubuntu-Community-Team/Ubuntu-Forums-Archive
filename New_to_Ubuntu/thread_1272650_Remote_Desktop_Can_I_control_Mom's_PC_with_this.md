---
title: "Remote Desktop: Can I control Mom's PC with this?"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by fiver22 on 2009-09-22
I've enabled Remote Desktop on my Mom's PC (Ubuntu 9.04), set up a password, and noted her IP -will this allow me to control her desktop (fix issues, get updates, etc) from my own Ubuntu 9.04? If so -How? Any tutorials out there? I've got her IP, Remote Desktop password, and her permission -what's next?
Thanks!

---

### Post by saj0577 on 2009-09-22
If on here system through 

On her system:
SYSTEM > ADMINISTRATION > LOGIN WINDOW
Then there is an option to enable remote login.

Now on your menu use Applications/ Internet/ Terminal Server Client (tsclient)
and then input her ip address for example 192.168.0.5 and then click connect and it should bring up the gdm and ask for the username and password. 

You should then be able to use the system as if you were sat there (apart from a little bit of latency.) On a side note I also believe if your mom is on her computer it will not let you use gnome as your environment.


I dont run gnome anymore but if there are any problems just let me know and I will look into it.

Saj

---

### Post by fiver22 on 2009-09-22
Just to clarify: This is totally WITH her permission. I just want to be able to help her out when she asks for help.
Any help would be appreciated.

---

### Post by XCan on 2009-09-22
Connect to it using a vncviewer, for example, the "Remote Desktop Viewer" that's preinstalled in your Ubuntu. I have to say though, at the very least you should change the default port of your VNC server.

---

### Post by fiver22 on 2009-09-22
-Thanks, saj0577.
Any help you can offer would be great.
-fiver22.

> **saj0577 said:**
> totally miss read the post sorry my bad.

Wil re read and edit this so its relevant :)

---

### Post by cybergalvez on 2009-09-22
> **XCan said:**
> Connect to it using a vncviewer, for example, the "Remote Desktop Viewer" that's preinstalled in your Ubuntu. I have to say though, at the very least you should change the default port of your VNC server.

I think you're better off using an ssh tunnel to do this, this way you don't even have to expose the vnc port to the outside.  install sshd on her machine, make sure you have an account on her computer, then use "ssh tunnel manager" to help you set up the correct tunnel to your mom's computer.  After that you all you do is point vncviewer to localhost which should be redirected to your moms computer.

This has the advantage of not exposing vnc to the outside (as already stated) and encrypting the stream

---

### Post by XCan on 2009-09-22
Hehe, in that case I have to say though, at the very least you should change the default port of your VNC server.

Still if you do that, you'll have to block off the VNCserver from taking connections from the outside, either with a firewall or through some setting (I forgot how to make Vino only listen to local connection).

---

