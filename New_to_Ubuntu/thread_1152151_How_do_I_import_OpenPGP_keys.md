---
title: "How do I import OpenPGP keys?"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by J03y on 2009-05-07
Hello, Im trying to add the gnome do repository but it says that its signed with a OpenPGP key. So how do I import the key? :(

---

### Post by Hospadar on 2009-05-07
Which repository?
Ususally maintainers will have instructions on how to do that.

It typically involves the "apt-key" utility
do a "man apt-key"

I believe you can also add the key in System->Administration->Software Sources

---

### Post by SunnyRabbiera on 2009-05-07
> **Hospadar said:**
> Which repository?
Ususally maintainers will have instructions on how to do that.

It typically involves the "apt-key" utility
do a "man apt-key"

I believe you can also add the key in System->Administration->Software Sources

Indeed, thats mostly how its done.

---

### Post by waspbr on 2009-05-07
there is a noobier way to do this, at the (in this case gnome-do)  ppa page there is a line that reads

> 
This repository is signed with 1024R/77558DD0 OpenPGP key. Follow these instructions for installing packages from this PPA.


click on the link at the 1024R/77558DD0 text, this will take you to another page with a line that reads

> pub  1024R/77558DD0 2009-01-20 Launchpad PPA for GNOME Do Core Team

click on the 77558DD0 link, this will open up a page with a funky text, this is the gpg key, all you have to do is copy the text as follows

> -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXUVdQEEAN8ALfH3wueKsSgDwA/HVEHdB7nlppqGKW/tubvGTy0ayf4M9ylX45szZK97
uL9/UHh5/B7eGMSB45EMJ0/qvTiflS6SwCxRCoKCW1PpYZlVcOLh5UUBkyREPJZcki1lK7pf
xvG9LkYKnvBP89s2PnO5LlDheEsVR4SqDGEtich/ABEBAAG0JExhdW5jaHBhZCBQUEEgZm9y
IEdOT01FIERvIENvcmUgVGVhbYi2BBMBAgAgBQJJdRV1AhsDBgsJCAcDAgQVAggDBBYCAwEC
HgECF4AACgkQKKggUHdVjdCVeAP+ONJtMFx9MGSJe33YiskagXEG5cQGYdDi5sWWUAP80bP1
Qe+Dsnjs3VKQ9ZZW3M8UNXsoFFN501hgJFBwUUCWIRSGZkzVgKoZZtZOe0Dws39xfV//8JFS
Te/r0oPzrr10iTFupTe/wBR0M9JbKGdY7SvooyqU+W2rf8/LldGx7KE=
=3C2V
-----END PGP PUBLIC KEY BLOCK-----


load a new text editor session (gedit) and paste the text onto it. Then save it was a .gpg file. I would normally save it as key.gpg at my home directory or the desktop.

when that is done, go to System>Admin>Software Sources

there at the authentication tab click on the button "import key file", this will open a root file browser, navigate to your /home/yourHomeName/Desktop (or wherever you have placed your key.gpg file), select your key.gpg file and press ok. 

You should be sorted now,

After all this is done, go to the fridge, open a cold beer and enjoy

---

### Post by jastonas on 2009-06-12
Is there a way to adding the key using terminal and apt-key instead of having to create a txt file every time..?

---

### Post by Cheesemill on 2009-06-12
[https://help.launchpad.net/Packaging/PPA#Adding%20the%20keys%20in%20the%20terminal](https://help.launchpad.net/Packaging/PPA#Adding%20the%20keys%20in%20the%20terminal)

Cheesemill

---

### Post by jastonas on 2009-10-19
Import ppa key from terminal - Ubuntu

> Adding the PPA's key to Ubuntu

Now Ubuntu knows about the PPA. It also needs to know how to check the software hasn't changed since Launchpad built it.

Note: This is not an endorsement of any of the software in PPAs. You must make sure you trust the PPA owner before installing their software.

Step 1: On the PPA's overview page you'll see the PPA's OpenPGP key id. It'll look something like this: 1024/12345678. Copy it, or make a note of, the portion after the slash, e.g: 12345678.

Step 2: Open your terminal and enter:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 12345678

Replace 12345678 with the key id you copied in step 1.

Step 3: Finally, tell Ubuntu to re-load the details of each software archive it knows about:

sudo apt-get update

You're now ready to install software from the PPA, using a tool such as apt-get in the Terminal or Synaptic. 

---

