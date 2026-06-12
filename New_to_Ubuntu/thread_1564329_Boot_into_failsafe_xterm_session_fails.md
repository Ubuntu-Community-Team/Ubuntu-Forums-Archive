---
title: "Boot into failsafe xterm session fails"
date: 2010-08-30
forum: New to Ubuntu
---

### Post by JebusWankel on 2010-08-30
I wanted my machine to boot straight to terminal so I would have less distractions when I'm coding. So I went to System > Admin > Login Screen Settings and set it to automatically log me in to an xterm session. Now, when I reboot my computer freezes at the ubuntu splash screen with a borderless xterm window in the corner and it's unresponsive to any typing. ctrl-alt-backspace and ctrl-alt-delete do nothing. I'm using a livecd right now. What should I do?

---

### Post by andrewthomas on 2010-08-30
why don't you just CTL + ALT + F2 from the gdm login screen?

---

### Post by JebusWankel on 2010-08-30
I set it not to go to the gdm login screen.

---

### Post by andrewthomas on 2010-08-30
what happens when you select recovery mode from grub?

---

### Post by JebusWankel on 2010-08-30
How do I do that? I have a single boot so I set grub to not pop up.

---

### Post by andrewthomas on 2010-08-30
I think press escape after your bios splash (if you have one)

---

### Post by andrewthomas on 2010-08-30
if that does not work. You could edit /etc/default grub so GRUB_HIDDEN_TIMEOUT=0 is commented

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

---

### Post by JebusWankel on 2010-08-30
Turns out that ctrl-alt-F2 worked.

Also it turns out that what I thought was unresponsiveness was just having an xterm running with no window manager and not having focus. So I was able to mouse over, get focus and run gnome-panel, then undo the changes I had made previously.

It's quite hilarious the things I tried before figuring that out. I tried to chroot from a live cd to edit grub. I tried purging gdm, purging xterm, and replacing gdm with kdm.

Wow, thanks for your help andrewthomas. I will now never forget ctrl-alt-F2.

---

