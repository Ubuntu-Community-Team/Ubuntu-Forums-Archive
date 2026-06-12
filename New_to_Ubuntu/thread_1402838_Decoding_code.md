---
title: "Decoding code"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by Marc St Louis on 2010-02-09
Hello guys.  I don't want to make a pest of myself but I figure that this  is the place to post this since I am an absolute beginner.  I am still  trying to figure this wireless on Ubuntu.  I ran this is a code *$sudo lshw -c network*  through  the terminal and this is the result, unfortunately I haven't a clue what it means.  Could  someone with the know how tell me what this means?

Thank you

---

### Post by audiomick on 2010-02-09
Those are the details of your wireless network card and its' configuration.

edit:
I take that back: Details of a wired ethernet connector, and at the end a reference to the wireless connector without any details.

---

### Post by patchwork on 2010-02-09
First off, I'm not an expert, so take this with a grain of salt.  It appears that your system is not 'seeing' your wireless card.  The device listed in the output is for eth0, which is the wired ethernet port.

There seems to be an entry for the wireless below, but there is no more output for it...

---

### Post by Marc St Louis on 2010-02-09
Ok thanks.  I guess I have a ways to go before I can figure this out

---

### Post by halitech on 2010-02-09
is the computer you are working on a desktop or a laptop? is the wireless device a PCI card or a usb device?

---

