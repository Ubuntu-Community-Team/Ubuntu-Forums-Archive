---
title: "Grub menu shows incorrect partitions and OS, can I edit simply?"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by jotto! on 2010-08-10
I had a problem with an Ubuntu install on my daughters laptop in that I installed from windows Vista and all was working fine till I did an ubuntu update which caused a grub rescue prompt.

I fixed by sorting out the windows boot loader and then uninstalled ubuntu so I could install directly from a disc outside of windows.

Now I have it all working as it should except on the grub loader, the windows partitions are named back to front.
I have an acer recovery option and a windows Vista option but it boots in to the other one...ie select vista and it boots to the recovery process, select recovery and it boots in to vista!

Can I edit the grub loader simply or is it very involved?
TIA.

---

### Post by rollin on 2010-08-10
I guess you could edit the titles in the grub menu? You might want to get to the root of the problem for a better solution but the info here should help: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by jotto! on 2010-08-10
can I use
sudo chmod +w /boot/grub/grub.cfg
and then
sudo gedit /boot/grub/grub.cfg

and then simply edit the text for the names? ie changing vista to acer recovery and vice versa?

---

### Post by drs305 on 2010-08-10
The main problem with editing the grub.cfg file directly is that whenever grub gets updated it would overwrite your changes.

You have a couple of options. I've dealt with the convoluted way (ammending the scripts that generate the grub menu) in the "Title Tweaks" link in my signature line. You can edit /etc/grub/30_os-prober so the recovery option is either renamed or hidden.

An easier way would be to copy the Window menu entries you want from the grub.cfg file and paste them into /etc/grub/40_custom. Save the file as /etc/grub/06_custom and make the file executable.

The entries will appear at the top of the Grub 2 menu. If you don't expect to update any Window OSs and don't have multiple linux distributions on extra partitions, you can disable /etc/grub/30_os-prober so it won't find these extra OS's by making it unexecutable. In this case those entries won't even appear in the menu. If you make a custom menu but leave 30_os-prober active, you will see both your custom entries and the ones you currently have.

Ask if you need help doing what I've described.

---

### Post by Mark Phelps on 2010-08-11
> **jotto! said:**
> can I use
sudo chmod +w /boot/grub/grub.cfg
and then
sudo gedit /boot/grub/grub.cfg

and then simply edit the text for the names? ie changing vista to acer recovery and vice versa?

NO -- do NOT do this!

Next time you do a kernel update, or something as simple as removing an old kernel, grub.cfg will get AUTOMATICALLY rewritten -- effectively, wiping out your changes.

There's a reason there is text in the CFG file that tells you NOT to edit it.

---

### Post by jotto! on 2010-08-11
> **Mark Phelps said:**
> NO -- do NOT do this!

Next time you do a kernel update, or something as simple as removing an old kernel, grub.cfg will get AUTOMATICALLY rewritten -- effectively, wiping out your changes.

There's a reason there is text in the CFG file that tells you NOT to edit it.

I understand that editing the CFG file could cause all sorts of problems but all I want to do is find a simple way that a n00b like me can undersatand to change the text from windows vista to acer recovery and vice versa. i wouldnt touch any of the technical stuff telling it where to boot from and what image to use.

drs305, looks like it will be your way. have read the tweaks link and will read it again and post up a few questions.

Just out of interest, why did the grub pick up these 2 parts of the OS back to front? is it because the recovery part is on the first part of the disk or would that have nothing to do with it?

---

### Post by Mark Phelps on 2010-08-13
> **jotto! said:**
> I understand that editing the CFG file could cause all sorts of problems ...

Apart from rendering your machine unbootable if you edit it wrong, you would do better to heed the advice of those of us who are NOT n00b's -- instead of blinding charging ahead and doing what you want to do.

---

