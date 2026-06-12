---
title: "Ubuntu 10.10 Headless server help"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by G_force on 2011-01-15
Hi all,

I am trying to setup a headless server to stream media and act as a print server etc. (Hence i don't need a screen or keyboard, just a wired network connection and power)

I have a few questions in regards to this type of set-up;

I searched the forums and found that Ubuntu wont boot without a monitor with gdm enabled, so i edited grub config (added text to quiet splash in grub.list and reloaded the config).

Will Ubuntu now boot with no monitor attached?

Additionally if Ubuntu does start, will it automatically configure network connection?

I have searched the forums, and a lot of the information is outdated. However if there is a guide somewhere to create this setup could someone point it out to me?

Thanks in Advance.

---

### Post by cariboo on 2011-01-16
IF you are running a headless server, you don't need gdm to start on boot, unless you are using the remote desktop application to access it. The easiest way to solve your problem is use ssh plus X-forwarding to manage the server eg:

```
ssh -X user@server
```

then at the prompt type the name of the application you want to use. 

Using the remote desktop application, just enable auto login and you shouldn't have a problem connecting to the desktop. To eanble it just use the ssh command above, then at the prompt type:

```
gdmsetup
```

set the user, and reboot.

---

### Post by 1clue on 2011-01-16
I've done more headless linux boxes than I have desktop environments.  I've been using Linux well over a decade.

There is nothing about Linux that requires a keyboard, mouse or monitor.  The X server requires a monitor at least, since its purpose is to provide a user interface to whoever is logged in.

Install Ubuntu Server.  There's no reason to have any X code at all on a server.

If your system won't boot without the keyboard/monitor/mouse then it's something in your BIOS that you can change.

---

### Post by G_force on 2011-01-20
Thanks for the info, got it running in no time.(Had to change bios settings)

---

