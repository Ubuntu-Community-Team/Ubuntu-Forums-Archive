---
title: "How do I create a hidden directory?"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-14
How do I create a hidden directory (i.e., one I can't see by default in Nautilis but can access through the terminal).

Also - are there settings in Nautilis to see hidden directories?

Can I make a directory hidden in Nautilis or do I need to use the command line?

---

### Post by Bölvaður on 2009-10-14
name it something like .hidden_directory.

the trick is having a . in front of the name.


to see the directory/file again you press ctrl+h (you can just find it under View in the menu also.)
or in terminal it was something like ls -a just add the "a" as a flag... so ls -al also works.

---

### Post by s.fox on 2009-10-14
Hello,

Put a period (.) at the start of the folder name.

To see hidden folders in GNOME, go to the View menu and choose Show Hidden Files.

-Silver Fox

---

### Post by jacksaff on 2009-10-14
Rename the directory with a . at the start of it's name.
eg rename bunchofstuff to .bunchofstuff

---

### Post by vipulkelkar on 2009-10-14
you can view the hidden directories from the command

ls -a

---

### Post by smileyguy on 2009-10-14
Thanks. Too easy:)

---

