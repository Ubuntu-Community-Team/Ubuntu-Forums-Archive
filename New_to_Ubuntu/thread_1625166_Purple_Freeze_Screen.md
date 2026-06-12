---
title: "Purple Freeze Screen?"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by Bunnies on 2010-11-18
Hiya, I keep getting a screen that I can't do anything about that looks like this:

[IMG]http://picpaste.com/pics/purplescreen-M7OoWv61.1290124609.png[/IMG]

Does anybody know what it is or how to prevent it?

[Link]("http://picpaste.com/pics/purplescreen-M7OoWv61.1290124772.png")

---

### Post by Bunnies on 2010-11-18
Has no one else received this?

---

### Post by sandyd on 2010-11-18
> **Bunnies said:**
> Has no one else received this?

monitor might not be synced with computer.

when booting up, try pressing ESC or Shift until you get the grub menu.
press 'e'

add 'nomodeset' to the end of the line that has "kernel" in it. Make sure theirs a space in between the last entry and nomodeset.

---

