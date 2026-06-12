---
title: "How to download to desktop from backup CD"
date: 2010-02-03
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-02-03
The title says it all.  I feel lucky that I did make this backup CD, and now I'd like to download it so that I don't always have to access it from the CD itself.

---

### Post by audiomick on 2010-02-03
Hi.
What are you wanting to get off the CD onto the computer?

---

### Post by chaanakya_chiraag on 2010-02-03
If they are files, just open it in the File Browser (double-click on the icon on the Desktop), select all (Ctrl-A), copy them (Ctrl-C), open your home directory (Places->Home Folder), Create a new folder called "backup" or something (Ctrl-Shift-N), click on the folder, and paste the files (Ctrl-V).  That's it!

---

### Post by Chris Edgell on 2010-02-03
Well, I copied all my files from my other OS on that other computer.  

Oh, I bet this is what people talk about when they talk about going into the terminal to do something with all the files...but I'm just guessing that there is an easy way.

I can't even venture a guess as to a hard way.  Although asking here is always the easiest way for me.  (Even though someone may call me on it...)

Oh, while I was typing I have received an answer...from chaanakya_chiraag...Thank you...let me go and give it a try.

---

### Post by chaanakya_chiraag on 2010-02-03
The "easy" way is outline above.
The "hard" way is to open up a Terminal (Applications->Accessories->Terminal), mkdir backup, cd /mnt/cdrom0 or something like that, sudo cp ./* /home/$USER/backup :)

---

### Post by Chris Edgell on 2010-02-03
Oh, chaanakya, thank you for telling me the other way, just for reference and comparison.  I have already gone and done it the easy way.

And it was very easy, thanks SO much.

Christine

---

### Post by chaanakya_chiraag on 2010-02-03
No problem!! :)

---

