---
title: "NM applet wants access to default keyring?"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by pernodthecat on 2009-12-16
I installed Ubuntu 9.10 2 weeks ago on a spare lap top. Each time I switch on, the NM applet asks me for a password. The user name and password I entered during installation (for administrator) do not work for the NM applet. Is there a standard password to enter the first time the default keyring is used (which must be changed for security) like they have on mobile phones, ie 0000 or1111            :confused: I'm a newbee and need help

---

### Post by overdrank on 2009-12-16
Hi and welcome, Moved to Absolute Beginner Talk

---

### Post by cenzorrll on 2009-12-16
> **pernodthecat said:**
> I installed Ubuntu 9.10 2 weeks ago on a spare lap top. Each time I switch on, the NM applet asks me for a password. The user name and password I entered during installation (for administrator) do not work for the NM applet. Is there a standard password to enter the first time the default keyring is used (which must be changed for security) like they have on mobile phones, ie 0000 or1111            :confused: I'm a newbee and need help

The first time you connect to a network you should have entered a password in order to remember the wireless password (separate from the wireless password and user password).  I think there is some way to release your passwords from the keyring but i'm not sure how that's done.  if you do figure out how to do so, the next time you try to connect you will be asked to enter a new password, which is where you enter your new password of your choosing.

you may try entering the password to access your network in case you entered that by accident (I've done that a few times)

---

### Post by johwel on 2009-12-16
To reset the Keyring to create a new password, you can try to delete this directory in your home directory: (It may be a good idea to back it up first)

in Gnome:
/home/<user name>/.gnome2/keyrings

<CODE>
rm -r /home/<user name>/.gnome2/keyrings
</CODE>

Then log out and in again. When trying to connect, the Keyring should ask for a new password.

---

### Post by pernodthecat on 2009-12-22
Thank for this. I'll give it a go a soon as I have some time to myself and let you know how I got on.

---

