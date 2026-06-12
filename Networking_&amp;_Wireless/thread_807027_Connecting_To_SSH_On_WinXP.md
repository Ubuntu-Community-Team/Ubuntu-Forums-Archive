---
title: "Connecting To SSH On WinXP"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by Kralnor on 2008-05-25
Howdy!

I've installed OpenSSH on my WinXP box and configured it successfully such that remote logins are possible. However, I cannot for the life of me seem to change the default login path when I attempt to mount it as a drive in Nautilus on Ubuntu 8.04. It stays as the installation directory for OpenSSH no matter what registry key I change.

In my case OpenSSH resides in ```
E:\Programmer\OpenSSH
``` but the directory I am trying to access or default to upon remote login is ```
G:\
```. When I mount the directory in Ubuntu I only have access to the install dir of SSH.

Changing the value of ```
HKEY_LOCAL_MACHINE\SOFTWARE\Cygnus Solutions\Cygwin\mounts v2\/home
``` in the WinXP registry does not seem to affect anything.

However, if I login via. a terminal in Ubuntu or do a local PuTTY login from Windows I am granted with a DOS command prompt where I can access everything.

I'm sorry if this isn't exactly a Ubuntu question but can anyone help me out?

---

