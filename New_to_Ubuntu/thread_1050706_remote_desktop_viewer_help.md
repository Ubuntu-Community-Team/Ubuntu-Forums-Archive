---
title: "remote desktop viewer help"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by rm06 on 2009-01-25
I've been attempting to get my remote desktop viewer to work now going on a couple of days without success. I am running Ubuntu 8.10 on both machines (both Dells, a GX260 and XPS400) which are connected to my DSL modem via a Netgear FS105 switch. Both boxes are also running Firestarter, on which both have policy exceptions to allow port 5900. 

I don't know if/how there is anyway to modify port settings on the switch. I am able to ping one machine from the other but I cannot "see" the other.

---

### Post by Hospadar on 2009-01-25
Hellos, I really can't help you with vnc (remote desktop), but i might suggest you take a look into ssh with X11 forwarding.  if you don't know:

ssh is a protocol that allows secure remote logins.  It won't give you remote desktop access, but it'll allow you to use any program as if you were at your machine, without the weight on your network of the whole desktop.  If you choose to use it, you need to make sure port 22 is open, and install the "ssh" package from synaptic or "sudo apt-get install ssh" from a command line.

X11 forwarding means that your ssh client (what you log into your machine with) is able to draw graphical interfaces for the programs you run on your server.

This setup will require a couple things:

your server has ssh installed and the port is open as above

you have an ssh client: all ubuntu installations have the ssh client installed by default.  On windows you can use a program like putty to log into a machine with ssh.

an X server: All linux desktop graphics are based on X, so ubuntu or any other linux distro will have X already.  On windows, you can install an xserver like xming.

X11 forwarding:
when logging in from linux, you'll add an extra command line argument
in windows, if you use putty, you'll have to enable x11 forwarding in the "tunneling" section of the options

To actually log in:
from ubuntu, open up a terminal, and then use a command like ```
ssh -Y <your username on the server>@<the ip of your server>
```
for putty, just type the same info into the boxes provided.

---

### Post by rm06 on 2009-01-26
Hospadar,

Thanks for the ssh mini-tutorial - that is indeed a useful and handy tool. Still no dice on the VNC however. . . any advice is appreciated.

---

