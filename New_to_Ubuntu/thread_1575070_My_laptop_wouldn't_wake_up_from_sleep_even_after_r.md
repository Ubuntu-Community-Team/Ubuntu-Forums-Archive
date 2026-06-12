---
title: "My laptop wouldn't wake up from sleep even after reboots"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by Julita on 2010-09-15
Hello! I have UNR 10.04 installed on my Asus netbook. The problem is that I can't boot into my Ubuntu partition. I am now writing from Windows. When the kernel is loaded I get many errors, and the last ones are something about USB devices, input/output... Anyway, I can't boot into my system, and recovery mode as well. It is the first time in half a year (and I use suspend every day) when such situation occurs. I have rebooted several times, but it doesn't help. I can access my ext3 partition from Windows, if this is of any help.

---

### Post by CharlesA on 2010-09-15
What are the exact errors you are getting? input/output errors normally mean the hard drive is going out.

---

### Post by Julita on 2010-09-15
The system is trying to locate EDD and other stuff (in reference to BIOS), it has numbers at the beginning of the lines. Then USB is mentioned, and then the list would stop. Nothing works, just the switch off button, if I press it long enough.

---

### Post by CharlesA on 2010-09-15
When you are at the grub screen, edit the Ubuntu option with "e" and add 'edd=off' after 'quiet splash' and see what happens (ctrl+x to boot).

Just a shot in the dark. [Source]("http://linux.derkeiler.com/Mailing-Lists/Debian/2008-11/msg02857.html").

---

### Post by Julita on 2010-09-15
I have added the line "noresume," and EDD was not mentioned at all. Now there is only a huge amount of numbers and  isapnp: no plug&play device found. usb 1-2: new high speed USB device using ehci_hed and address 2 1-2: configuration #1 chosen from 1 choice. The laptop remains unresponding to anything but switch off button.

---

### Post by CharlesA on 2010-09-15
Hrm. Maybe try booting off a livecd and see if it does the same thing.

---

### Post by Julita on 2010-09-15
Yes, I'll do that, thank you!

---

