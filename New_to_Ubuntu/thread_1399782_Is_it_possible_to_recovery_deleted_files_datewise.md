---
title: "Is it possible to recovery deleted files datewise"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by leemur on 2010-02-06
I did the following steps which resulted in missing of my folder. I have dual boot in my system (windows vista & Ubuntu 9.10 64bit)

- I was in windows and i came out of window by using the hibernate option (no shutdown)
- After my laptop was powered off, i switched on and booted in Ubuntu9.10
- I moved one folder from my home directory in ubuntu to a NTFS partition in my harddisk. This NTFS partition is used by my window vista
- I shutdown from ubuntu and next time when i started my laptop, i booted in windows vista.
- The vista was resuming from my previous session.
- **[COLOR=Red]Now I am not able to see the folder which i moved to the NTFS drive using ubuntu[/COLOR]**
- When i logged in Ubuntu again the folder is lost as I moved the folder instead copy. (i did cut & paste)
- now both the OS is not finding my folder.


- How to bring back the missing folder link in Ubuntu
- Is it possible to recovery the deleted file by date
- Is it possible to recovery the deleted file from a particular folder instead of recovering from entire drive.

---

### Post by mushwars on 2010-02-06
log back into ubuntu and see if you can still see the files. sometimes if you copy files to a folder that are not mounted then mount the drive they wont be there.

---

### Post by leemur on 2010-02-06
Yes, I tried that. I logged back in Ubuntu, but my folder is still missing.

---

### Post by mushwars on 2010-02-06
I dont really know how that is even possible. Your drive mounted your windows partition and you expolored to it in nautilus then you moved some files to it instead of copying them, they moved fine no errors, then you booted into vista they wern't there, and you booted back into ubuntu adn they werent there either?

Sufficeive to say, you either unmounted your drives wrong or I am missing something, turning off the computer without unmoutning the drive could do that ( dont worry it does it automattically if you shut it down right)

---

### Post by leemur on 2010-02-06
Sorry I missed some more info

After moving the folder using ubuntu and when i logged back to windows (windows was resuming), I was able to only see my folder. But window  was giving an error when i tried to open that folder and  it was showing the folder size as zero (actaull size was 2 GB).Then I did a complete shutdown of window.  I logged back in ubuntu to check the folder, but it was not there (both source and destination location). Then, I once again tried to boot in window to check the folder. But this time the window was prompting for scandisk during startup stating that C driver would have corrupt. I allowed scandisk to check my driver. During scandisk it was printing some message related to  "deleting some missing link file" (sorry i didnt remember the exact message).Scandisk did some fixing and after that when the windows started the folder was missing.

---

