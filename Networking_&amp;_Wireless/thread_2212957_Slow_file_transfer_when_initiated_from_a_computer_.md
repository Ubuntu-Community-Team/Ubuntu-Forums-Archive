---
title: "Slow file transfer when initiated from a computer not sending or receiving"
date: 2014-03-24
forum: Networking &amp; Wireless
---

### Post by Tony_Lillie on 2014-03-24
Computer A is running Ubuntu 12.04 Server with a Unity desktop, computer B is Windows 7, and computer C is Ubuntu 13.10. All of these computers can see each other and access shares on one another without issue. A & B are hardwired ethernet 1000MB and C is wireless N 150MB

If I am sitting at B and copy files from A to B or B to A, the transfer speeds are great (60-80 MB), but here's where it gets weird. If I am sitting at computer C and copy files from A to B or B to A the transfer speeds plummet to 3 MB. WHY?

The transfer is between the same 2 computers, but when initiated from C (not sending or receiving) the transfer is terribly slow. I could understand a mild 10% drop in speed (just grabbing that from the air) because maybe some packets need to be sent to C from A and/or B during the transfer to report the status, but the 3MB transfer speed suggests something else is going on. Is there an explanation for this?

---

### Post by slooksterpsv on 2014-03-24
How are you copying files between the computers? - Specifically how?

---

### Post by Tony_Lillie on 2014-03-24
Copy and Paste from within Nautilus where I can view both A & B's shares.

---

### Post by slooksterpsv on 2014-03-24
Doing it that way will copy it to your computer first, then copy it to the other computer

A -> C over wireless; C -> B over wireless.

That's why.

A copies the file to C, C then copies the files to B.

EDIT: A faster way would be to either ssh and copy via terminal, or do a remote desktop and copy that way.

---

### Post by Tony_Lillie on 2014-03-24
Are you sure about that? I know it would explain the tremendous latency, but that just seems completely mental. Why would a copy of the file need to ever touch the C machine? I'm merely telling the files to go from A to B, not dragging them into C at all.

---

### Post by slooksterpsv on 2014-03-24
The machine recognizes that you want to get files from A and copy them to B so what happens is this:
A is queried for the files you chose to copy.
You select the location which is location B.
The computer copies the files into temporary storage on C while it's transferring to B.
B recognizes what its receiving and notes where the files are being copied to.

It's just like when you sync music from lets say amazon to your mp3 player:
Amazon is asked for the file, it may buffer on the computer, and then sent to the mp3 player.

---

### Post by Tony_Lillie on 2014-03-24
Makes perfect sense now that you put it that way. Thanks for having patience with my skepticism.

---

