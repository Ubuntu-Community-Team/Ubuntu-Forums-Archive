---
title: "Achieve a clean netsta -ut. Localhost, ipp etc..."
date: 2015-03-02
forum: Networking &amp; Wireless
---

### Post by hey2 on 2015-03-02
Hi.

As the title says, i'm trying to achieve a clean netstat -ut when i start ubuntu.

On startup and on live  USB, when i run this command i see two established connections. something like this ip6-localhost:40526 and ip6-localhost:ipp.

From what i gathered it seems to be something related to a printer service, but why is it established?

What i want to know is if there's a gui solution to end wathever this service is doing and achieve a clean netstat command.

Thank you very much.

---

### Post by houstonbofh on 2015-03-03
Looks like the cups webserver on the loopback address.  If you really want it gone, you can kill cups, but there is not a real reason to.

---

### Post by hey2 on 2015-03-03
Hi

Thank a lot for your response.

Yeah it's probably normal, but since I'm used to windows, when i see something established in the command line i start to sweat :D

When I tried the live usb on a desktop, it didn't seem to happen. Maybe it's something related with the wireless network of the laptop.

I don't remember seeing the Cups in the processes when i opened the System Monitor.

I also tried to mess with some printer settings, but it didn't do anything.

Does this happen to you (Ubuntu 14.04). I've seen some more people with the same issue but no simple solution.

Anybody else have any idea how to stop this without uninstalling anything?

Thank you once again for your help.

---

### Post by houstonbofh on 2015-03-03
Anything connected to localhost is an internal loopback connection.  *nix uses loopback networking much like Windows uses ODBC to move stuff around sometimes.  It is not a real worry.  For example, here is my KVM stuff with the psudo network, but all internal.
tcp        0      0 localhost:5902          localhost:35422         ESTABLISHED
tcp       38      0 10.0.0.254:35376        client-14a.v.drop:https CLOSE_WAIT 
tcp        0      0 localhost:35422         localhost:5902          ESTABLISHED

---

