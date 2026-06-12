---
title: "stupid camera compact flash card"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by nachos99 on 2009-03-03
im new to ubuntu and have an old digital camera that i use(d) with my XP.

im trying to delete pics off the camera's compact flash card (filesystem type: msdos according to properties. according to GParted it's in fat16.)

it appears that i can seem to delete pics, in that i no longer see them anywhere inside the camera's folders. but when i click on properties, i see the free/used spaces havent changed and it's still on there even though i now cant see them. 

what makes this worse is that when i plug the camera into my xp laptop, it reads basically the same thing. i cant see what's taking up the space.  for example, it will only see 2 folders containing 10MBs of pics, but properties says 100 MB used.  now i can't delete them properly in XP or ubuntu.

will reformatting the compact flash solve this problem?  

and if so, should i be reformatting in fat16 or fat32?

thanks in advance.

---

### Post by nachos99 on 2009-03-03
by the way, my compact flash card is only about 132 MB.

is that too small for FAT32?

---

### Post by greyfox1 on 2009-03-03
Hi Nachos99, welcome to the forums!

When you delete items from a removable medium under Ubuntu, the files get moved to a hidden folder named .trash-1000 (the leading "." makes the folder hidden under Linux). The number may be different than 1000-- say 1001 for example-- depending on your setup.

At any rate, this is probably where your deleted files are.  Before you removed the flash card from its reader, did you eject it from Nautilus?  You should be prompted to empty the trash when you tell Nautilus to eject the card.  If you didn't do this (e.g. you just pulled the card out of the reader), the files are probably still in this hidden folder.

And to answer your question, yes, formatting the card would delete the data.  I'm not sure which filesystem you should use, though.  HTH

---

### Post by llamabr on 2009-03-03
I had a similar experience.  It turned out nautilus was creating a .Trash file, and storing them in there.

I believe that if you properly unmount it, it should ask if you want to delete the trash.  Just say yes, and there you are.

If not, open a terminal, and cd into the camera.  You might have to poke around the directories awhile, but probably if you do a:

```
ls -aL
```

you'll see it right in the main dir, and can delete it with a:

```
rm -rf .Trash/
```

Or whatever it's called.

Let us know what happens.

---

### Post by nachos99 on 2009-03-03
thank you for the suggestions. my problem is solved, i guess.

i had not been properly unmounting the camera so i understand the problem.

i did find and delete the the trash folder several times before posting, but the used space appeared to remain the same.  of course, i did not previously unmount the device properly a single time since i never thought about it(!).  i found the trash file and it was empty.  i took a few new pics and deleted them, unmounted device, told nautilus to delete items, etc.  that did not change the originally used space.  

since deleting the trash folder several times didnt change the situation, i got impatient and just ran GParted and wiped the flash card as fat16.  

the camera and ubuntu both read it ok.  

i will be sure to unmount and delete through nautilus from now on.

thanks for the tips.

---

