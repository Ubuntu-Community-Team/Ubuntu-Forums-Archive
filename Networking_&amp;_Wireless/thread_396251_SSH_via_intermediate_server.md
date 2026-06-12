---
title: "SSH via intermediate server"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by valavanisalex on 2007-03-29
My Edgy Ubuntu desktop at work is configured as an SSH server.  If I want to access files from home however, I currently need to do so in two steps, as only one of the networked computers at work permits off-site access.  As a simple example, I do something like the following to get a PDF file from my work computer:

```
user@home:~$ ssh user@ext-server
user@ext-server:~$ scp user@work:example.pdf .
user@ext-server:~$ exit
user@home:~$ scp user@ext-server:example.pdf .
user@home:~$ evince example.pdf &

```

Using remote X is far too slow, so I have to copy files via this horrible five step process.

To save a bit of hassle, I have used sshfs to mount a folder on the external server to my home desktop.  This can save a little effort, as I now only need do the following...

```
user@home:~$ ssh user@ext-server
user@ext-server:~$ scp user@work:example.pdf .
user@ext-server:~$ exit
user@home:~$ evince /sshmountpoint/example.pdf &

```

It would be great however, if there was a way to mount a folder on my work computer to my home computer, so the entire process became transparent.  To make matters worse, I don't have root access to the external server, and sshfs is not installed.  Any genius suggestions for how to make my life easier would be appreciated!

---

### Post by valavanisalex on 2007-03-29
*

---

### Post by Mr. C. on 2007-03-29
If your site's server has gateway ports enabled, you can forward tunnels to another internal system, such as your desktop.  See man sshd_config (GatewayPorts) for more info.

If not enabled (and for security reasons it likely is not), you are going to be stuck with the two method copy.

You could write yourself a function or alias that ssh connects to the gateway server, copies from your system, exits, and then copies to your home system.

Can you ssh connect from your work system to your home system?  If so, you can reverse tunnel.

MrC

---

