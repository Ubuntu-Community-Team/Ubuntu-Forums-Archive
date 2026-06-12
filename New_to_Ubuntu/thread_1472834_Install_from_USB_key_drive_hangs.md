---
title: "Install from USB key drive hangs"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by jrlii on 2010-05-04
I can boot from my USB key drive, but the installer seems to hang after selecting the keyboard.

No activity showing on the drive light, so I think it may be looking for a CD drive, which isn't there.

---

### Post by WiReIs on 2010-05-04
Have you selected your usb drive as the primary boot up in the BIOS

---

### Post by jrlii on 2010-05-04
The USB drive is first in the boot list.

---

### Post by jrlii on 2010-05-05
OK, I solved this problem, 'though the solution is less than completely satisfactory.

Here is what I wound up doing:

1. I downloaded the alternate installation disk to the key drive.
2. Copied the ISO to the hard disk, in this case the Desktop.
3. Opened a terminal window.
4. Mounted the ISO as a CD-rom with the command:

[INDENT]sudo mount -o loop ~Desktop/ubuntu-10.04-alternate-i386.iso media/cdrom0[/INDENT]

5. Ran the update manually with the command:

[INDENT]gksu "sh /cdrom/cdromupgrade"[/INDENT]

6. Answered the questions which popped up.

7. Re-booted & there was 10.04.

---

