---
title: "Trash will not empty"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by thebarisaxkid on 2010-10-05
I have a card reader with a card in it (2gb) attached to my computer.  I am deleting all the photos off of it.  They are all being moved to my trash can but they aren't being deleted.  When I try to delete them (even if I try individually) it gives me an error saying: 
Could not delete "filename"
Details: Failed to delete from trash bin

What do I have to do?  How can I delete them?  What is wrong?

---

### Post by sandyd on 2010-10-05
> **thebarisaxkid said:**
> I have a card reader with a card in it (2gb) attached to my computer.  I am deleting all the photos off of it.  They are all being moved to my trash can but they aren't being deleted.  When I try to delete them (even if I try individually) it gives me an error saying: 
Could not delete "filename"
Details: Failed to delete from trash bin

What do I have to do?  How can I delete them?  What is wrong?
To clean out the trash
```

rm -rf ~/.local/share/Trash/files
```

---

### Post by thebarisaxkid on 2010-10-05
Umm, that command is part of the "Malicious command thread"

Nice try!

---

### Post by aeronutt on 2010-10-05
I've seen the same characteristic when deleting files from solid state drives.  Do you have the drive mounted when you try to empty the trash?

---

### Post by Darkness Des on 2010-10-05
Alright, I'll give you props on that. But they over-dramatized rm -rf. rm -r is remove recursively, which means it's okay to delete the directory if it's not empty. The f, basically, tells it to include files. Now, the following command (DO NOT RUN IT! I CANNOT STRESS THIS ENOUGH) deletes your system with only a few minor changes: sudo rm -rf /

DO NOT RUN THAT.

The command that he gave you empties the trash.

---

### Post by thebarisaxkid on 2010-10-06
> **Darkness Des said:**
> Alright, I'll give you props on that. But they over-dramatized rm -rf. rm -r is remove recursively, which means it's okay to delete the directory if it's not empty. The f, basically, tells it to include files. Now, the following command (DO NOT RUN IT! I CANNOT STRESS THIS ENOUGH) deletes your system with only a few minor changes: sudo rm -rf /

DO NOT RUN THAT.

The command that he gave you empties the trash.

Hmm, now it makes sense.  I thought about that after I posted the reply, and then it clicked.

---

### Post by thebarisaxkid on 2010-10-06
> **aeronutt said:**
> I've seen the same characteristic when deleting files from solid state drives.  Do you have the drive mounted when you try to empty the trash?

In this situation, it is a card reader with a "CF I/II" card plugged in.  Yes it is mounted.  When I tried to eject the card, it told me that there is trash related to the card.  It asked whether or not I wanted to delete the trash from this device, I clicked yes and it worked.

---

### Post by thebarisaxkid on 2010-10-06
Sandyd, sorry for accusing you.  I should have thought before I wrote.

---

### Post by DayLite on 2010-10-06
> **sandyd said:**
> To clean out the trash
```

rm -rf ~/.local/share/Trash/files
```

 **DANGEROUS COMMANDS -- look but DO NOT RUN**

Delete all files, delete current directory, and delete visible files in current directory. It's quite obvious why these commands can be dangerous to execute.

rm -rf /
rm -rf .
rm -rf *

It is good to check before you run anything in the terminal. A helpful post can be found [here]("http://ubuntuforums.org/announcement.php?f=326").

---

### Post by AldenIsZen on 2010-11-07
I too was unable to emtpy the trash. I ened up doing this solution [here]("https://answers.launchpad.net/ubuntu/+question/35412"). I unmounted it, and then was able to cancel as I had transmission running and files on that partition. But the files did delete. I was getting a unable ot modiy files in the trash error when attempting to move and delete them from another folder, but that had been a usable workaround until today. Maybe I need to reboot to use the other work around again. Solution in the link is below:

Problem solved:
The original file was in one of the volumes. I searched the volume's trash and found it there, tried to delete and it wouldn't. So I unmounted the volume. It gave the offer to empty the trash, which I accepted. Then it refused to unmount (permissions) and I said OK. But the trash deleted from all the bins on all the computers. Obviously the bin with the trash being shared was screwed up by the trash applet thing. An interesting little thing, but probably of no great value to anyone.

---

