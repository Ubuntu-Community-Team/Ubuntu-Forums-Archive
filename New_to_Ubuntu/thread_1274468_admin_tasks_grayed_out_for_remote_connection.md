---
title: "admin tasks grayed out for remote connection"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by BaldNomad on 2009-09-24
I have a machine set up with Ubuntu 9.0.4.  I have been using NX from NoMachine to log in to the Linux machine from my Windows desktop.  The Linux machine is headless and I hate KVM switches so I decided that I could just perform the occasional task using a remote login.

However, the Ubuntu GUI does not seem to like this.  Pretty much everything is grayed out in terms of configuration settings, etc when I log in this way.  For example, the Unlock button is grayed out under System -> Administration -> Services.

From reading the docs, it looks like it's supposed to prompt me when I do admin-type things with my normal login account - but I think the remote connection may be a factor also.

How can I administer the machine remotely and actually do some administration?

---

### Post by rakete on 2009-09-24
A dirty thing you could do is to give your root account a password with sudo passwd root in console. Do your Admin Tasks by login in as root and set the root account passwordless again afterwards with sudo passwd -d root

Better way is to do things with console and the sudo command only...

---

### Post by BaldNomad on 2009-09-25
I know I could probably do everything I need right from the console, but my question is, why don't the GUI apps just prompt me for the admin pw when I'm connected via remote, and is this something I can change?

---

### Post by rakete on 2009-09-25
I am not firm with Windows Remote Desktop Clients. That's a Question you should ask the supporters of NX NoMachine.

My only experience with Windows Remote Desktop Clients was an associate who tried to connect to an ubuntu remote server via Windows, failed, and switched to ubuntu completely :)

---

### Post by erilidon on 2009-09-25
why not just use a vnc client? TightVNC is good and realvnc is alright.

---

