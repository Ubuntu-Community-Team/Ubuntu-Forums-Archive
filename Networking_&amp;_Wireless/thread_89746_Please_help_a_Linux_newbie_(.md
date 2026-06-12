---
title: "Please help a Linux newbie :("
date: 2005-11-13
forum: Networking &amp; Wireless
---

### Post by stealthdevil on 2005-11-13
Yesterday I finally made the switch from Windows to Linux. After starting uni i found myself using linux more and more for my course (computer science). After a year, I have finally installed Ubuntu 5.04. 

However one problem. I have no idea on how to configure and use Ubuntu. Installing it wasn't difficult. 

My main problem is my wireless card.

I am using a Netgear WG511 PCMCIA wireless card.
I have an Acer Aspire 1300 Laptop (AMD Athlon XP).

When I insert the card, the device manager detects something, but then nothing happens. I guess i'm too used to windows.

I have read a lot of tutorials. One method of using the Prism54 files and one using Linuxant DriverLoader, however I can't use either method.

I tried going the prism54 way, but i can't seem to compile a kernel and using the Ubuntu Wiki step by step procedure of compiling the kernel, it still wont. I simply the get the error that my password is wrong when I type sudo. I type the root password. If i type my own password, it gives me an error that I'm not in the sudoers file.

As for the DriverLoader. I have no idea what to do with the file. It's a .deb file with loads of other files in it.

My main priority before exploring other areas of Linux is trying to get the wireless card to work on it. I can use the internet on my other laptop (its using windows), but i want to completely stop using windows and just stick to linux.

Could please someone assist me on installing the wireless card (keeping in mind i dont really have any technical knowledge in configuring linux).

Thank you experts!

Rameen

---

### Post by Lambert on 2005-11-13
You shouldn't have to do anything as prism54 support is built into the kernel

Open a terminal Applications>accesories>terminal and type in this command

```
sudo lshw -C network 
```

You should see your card listed with a line like this.

```
 configuration: broadcast=yes driver=ath_pci d
```

Yours won't say ath_pci, probably prism54.

Open System>admin>networking. Highlight the wireless device, click on properties, enter in your network stuff, click ok, then click activate.

---

### Post by stealthdevil on 2005-11-13
I would try that but like mentioned in my post, i can't sudo. 
Also, a lot of things just wont load. Synaptic wont load, users and groups wont load, and neither does the networking.

When my ubuntu starts, it gives me an error that it couldn't lookup the voyager-linux (the name of the computer) and that I can manually add it to etc/hosts Not sure if that is related to anything?

When i type iwconfig, it says:
NOT READY! ESSID: OFF/ANY

And a lot of other gibberish. Access point is a bunch of 0's and so is signal level etc.

---

### Post by emperor on 2005-11-13
[quote=stealthdevil]I would try that but like mentioned in my post, i can't sudo. 
Also, a lot of things just wont load. Synaptic wont load, users and groups wont load, and neither does the networking.

When my ubuntu starts, it gives me an error that it couldn't lookup the voyager-linux (the name of the computer) and that I can manually add it to etc/hosts Not sure if that is related to anything?

When i type iwconfig, it says:
NOT READY! ESSID: OFF/ANY

And a lot of other gibberish. Access point is a bunch of 0's and so is signal level etc.[/quote]

It sounds like you created another user account after installation. If so, login as the orginal user; the name you used during installation of Ubuntu. After you do this you can add the new account to the sudo users list using "sudoedit".

---

### Post by Lambert on 2005-11-13
I take it you have a root account set up.

run this from terminal

```
gksu users-admin
```

It will ask you for your root password and open up a window. Select the groups tab, find Admin in the list, click properties, find your name in the list and click add. this will add you to the sudoers list.

---

### Post by stealthdevil on 2005-11-13
Via user-admins, i added myself to the root group and sudo group. I found no group called admin. I was already added to the group adm.
However, despite doing all this and relogging in, it still doesn't allow me to run sudo. Couldn't i just su to root?

When i type sudo lshw -C network it says:
sudo: unable to lookup voyager-linux via gethostbyname()
rameen is not in the sudoers file. This incident will be reported.

Where do i go from here?

---

### Post by stealthdevil on 2005-11-13
Just a quick addition. After a reboot, when i click on the applications that wouldnt previously load, it now asks for a password when i click on them. However, after typing either my password or the root pass, it says:
"failed to run /usr/sbin/synaptic:
Child terminated with 1 status"

---

### Post by taurus on 2005-11-13
I am not sure how you installed it but sounds like you have a misbehaving system!!!  The account that ubuntu asks to you create during the installing process can do sudo since it's in group adm in /etc/group.  All you have to do is type in your password when it asks you too, not root's password!!!

p.s.  Sometimes, reinstalling is the best solution to see if all those errors go away or not...

---

### Post by stealthdevil on 2005-11-13
This is the second installation. The cd integrity showed everything as fine and the cd was ordered from Ubuntu. Plus, i like solving problems by finding the cause as i think that's the best way to learn. Any ideas regarding how to fix whatever is up with my system is much appreciated...

---

### Post by stealthdevil on 2005-11-13
Ok, using ndiswrapper i managed to get the card working. It manages to connect to the router, however, firefox wont load any internet pages and i cant ping any websites from ssh....any clues as to what is wrong?

---

### Post by stealthdevil on 2005-11-13
FINALLY! I managed to fix everything!

For reference of future users here is how i fixed things:

hosts file was wrong (etc/hosts) Use pico to edit it.
Should be in the format: 
127.0.0.1 localhost.localdomain <computer name>

Was not in sudo list. Used su to switch to root in the terminal.
A root entry would already exist so i just added my username in the exact same format.

Wireless card wasn't installed. Downloaded and installed ndiswrapper.
Downloaded windows drivers and installed them via ndiswrapper in the terminal.

Opened networking and made sure it was enabled and configured.

Now all is working well!

Thanks for those that contributed :)

---

### Post by mips on 2005-11-13
Disable IPv6 in Firefox and see what happens. Look for a post by my username with Option1, 2 & 3.

---

