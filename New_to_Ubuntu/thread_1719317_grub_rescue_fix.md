---
title: "grub rescue fix"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by Rambokill on 2011-04-01
There was a link of a thread in this forum which was talking about grub rescue fix where you had to write some commands in the terminal and it would actually work.Can someone give that link or give me those commands.

---

### Post by tm222 on 2011-04-01
What do you want to do? Do you want to reinstall Grub on your computer?

---

### Post by Jinda on 2011-04-01
I use:
$ls
$set root=(hdo,X) *as shown by ls command*
$linux /vmlinuz root=/dev/sdaX ro quiet splash
$boot

This works for me all the time

---

### Post by Rambokill on 2011-04-02
I am using grub2 btw.Do you mean that I have to run those commands when it says grub rescue> or at the terminal using ubuntu live cd

---

