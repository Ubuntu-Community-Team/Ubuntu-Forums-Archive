---
title: "Gaining Access to an External HD"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-12-16
I need to reinstall ubuntu so im backing up my home folder on the try ubuntu on the live CD. I dont have access to the HD i was told on a ubuntu help chat to gain root access to it by using a certian code, it was a while ago and i cant remember the code, it began with an N  Nuclious or something along those lines aha. someone lead me in the right direction?

---

### Post by bruno9779 on 2009-12-16
```
sudo mount /dev/sdb1
```

should do the trick.

If it doesn't, it means that your externa HDD is not called "sdb2" and has another name. find it with

```
sudo fdisk -l
```

---

### Post by Rave Gloves on 2009-12-16
it says its allready mounted, are you sure you dont have a code that will give me root access to the HD?

---

### Post by bruno9779 on 2009-12-16
> **Rave Gloves said:**
> it says its already mounted, are you sure you dont have a code that will give me root access to the HD?

if it is already mounted, you should be able to just access it.
The default mount point for devices like that is in /media

Maybe you should follow [this tutorial]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") to move your home.

---

### Post by Rave Gloves on 2009-12-16
> **bruno9779 said:**
> if it is already mounted, you should be able to just access it.
The default mount point for devices like that is in /media

Maybe you should follow [this tutorial]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/") to move your home.

You may have misunderstood, i need access to the External HD that is pluged in via USB, when i try to move the home folder to it, it tells me i dont have access

---

### Post by CaptainMark on 2009-12-16
your looking for ```
gksu nautilus
```i think, that gives you a file browser with root permissions

---

### Post by bruno9779 on 2009-12-16
He asked via terminal I think.

```
sudo cp -R /home /media/(the name of your HDD)
```

---

### Post by Rave Gloves on 2009-12-16
> **CaptainMark said:**
> your looking for ```
gksu nautilus
```i think, that gives you a file browser with root permissions

This is the code, it allowed me to drag the home folder into my External HD but it just wouldnt transfere the files over, it just frozze. Any other ways ? i really need all these files backed up.

---

### Post by bruno9779 on 2009-12-16
so, you wanted a terminal command to enable you to do that in GUI, instead of a terminal command that does it all in once ?

beats me

```
sudo cp -R /home /media/(the name of your HDD)
```

is still the best solution i think

---

### Post by CaptainMark on 2009-12-16
+1 on the terminal command, there may be a problem with how your hdd is mounted, both these methods should work fine, if the terminal command doesnt work you may have your hdd mounted without read/write privilige

---

### Post by VernonA on 2009-12-16
The OP didn't really say he wanted a terminal-based reply, he just wanted to be reminded of the name of the tool to use (Nautilus). He's on the Absolute Beginners forum, so a GUI tool is always going to be the best first choice. When he used it, it froze up. That doesn't immediately sound like a permissions problem, as that would have given an error msg. To diagnose the problem I would suggest going into the home directory and dragging one file across. If that works, drag a directory. Then the rest. If the file copy doesn't work, then (even on a LiveCD) the error msg will be shown fairly swiftly, and we can proceed from there.

---

### Post by CaptainMark on 2009-12-16
Read post #5 then tell me it doesnt sound like a permissions problem. 

Its mounted but the op is told he doesnt have access to it, sounds like permissions, but you go with your idea if you want.

---

### Post by VernonA on 2009-12-16
You're right, of course. I picked up on the "froze up" phrase, which reminded me of problems I have seen with Nautilus running from LiveCD on a small-memory PC. It does seem to freeze doing massive copies due to memory/swap issues, which is where I thought we were headed. Perhaps the OP would actually tell us what error message he is seeing, so we can avoid further guessing;-)

---

