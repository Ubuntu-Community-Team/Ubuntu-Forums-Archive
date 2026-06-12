---
title: "Pigdin"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by Autumnie88 on 2009-10-18
I am trying to use pigdin for yahoo instant messaging, but it won't ever connect.  It just keeps saying connecting...am I doing something wrong?

---

### Post by deancasino on 2009-10-18
> **Autumnie88 said:**
> I am trying to use pigdin for yahoo instant messaging, but it won't ever connect.  It just keeps saying connecting...am I doing something wrong?

Probably not mate, I'll tell you what, move to Empathy (it's in the Add/Remove section under Applications) in addition to supporting Yahoo messenger, Empathy also support the Webcam/Audio for it.

---

### Post by Autumnie88 on 2009-10-18
I'm trying to update pigdin as I can't find empathy, but the commands that it gives don't seem to be working.  These are the instructions
To setup the PPA, copy-and-paste these commands into a terminal:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8

echo deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list

After doing this, open Update Manager, check for updates, and then install the newly available Pidgin packages.

I did these things and it doesn't seem to be updated.

---

