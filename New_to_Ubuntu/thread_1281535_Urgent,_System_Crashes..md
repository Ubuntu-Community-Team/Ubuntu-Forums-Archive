---
title: "Urgent, System Crashes."
date: 2009-10-03
forum: New to Ubuntu
---

### Post by noveus on 2009-10-03
Ive just finish updating my Ubuntu 9.10 and install my Graphic Card. It requested for a restart, after restarting it, it crashes. Now it cant even log into my Ubuntu ( im dual booting)

---

### Post by halitech on 2009-10-03
what video card? Can you boot into single usermode from grub and run xfix?

---

### Post by noveus on 2009-10-03
Im sorry, im new to computer, how do i do that?
Edited : My graphic card is nVidia 9600M GT

---

### Post by halitech on 2009-10-03
when the computer first boots up, you should see something about press esc to enter grub, press escape and select singleusermode or recovery mode (not sure on the wording) but it should be the second option in the list

---

### Post by noveus on 2009-10-03
lemme take a pic of it and paste it here.

---

### Post by noveus on 2009-10-03
Ive tried recovery, still this things came out.

---

### Post by halitech on 2009-10-03
you've got an issue with the file system. My suggestion would be to boot from a live cd and manually run fsck /

---

### Post by noveus on 2009-10-03
What is fsck?

---

### Post by halitech on 2009-10-03
fsck - file system checker

basically its about the same idea as chkdsk for windows

---

### Post by Paddy Landau on 2009-10-03
fsck means File System CHeck.

[LIST=1]
[*]Boot from your Live CD.
[*]Open a terminal (Applications > Accessories > Terminal).
[*]Type *sudo fsck -CMf /dev/sda5* (this assumes that your Ubuntu is on partition sda5, which it seems to be from the screenshot. Also note the capitalisation).
[/LIST]
Let us know what happens.

---

