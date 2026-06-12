---
title: "Another permission problem..."
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Bkdoorbandit on 2009-03-24
I've recently changed to ubuntu and i'm having some problems with getting access to some .rar that i have on one of my old HDDs. I've tried to take control using TakeOwn in Vista and that didn't work. I've tried to use nautilus and "sudo cp <file_orig> <file_dest>", but the only thing i get is this --> "cp: cannot stat `/media/Extern': No such file or directory" and so on..

When i try to extract it i get an error msg telling me that permission is denied. Same thing when i just try to drag the files to the desktop.

These are files i really need and i don't know what to do =/

---

### Post by The-IRS on 2009-03-24
you will probably have to get used to the terminal in ubuntu.
using the "sudo" command will run any command after it as root. although, considering the fact that it was a RAR file, was it made in windows? you might also want to try installing wine and then installing WinRAR through that to extract the file

---

### Post by ktrnka on 2009-03-24
You probably need to install unrar and/or rar. It should be in your repositories. You can install it via Synaptic or you can install it from the terminal:

```
sudo apt-get install unrar rar
```

---

### Post by Bkdoorbandit on 2009-03-24
I have wine and i have unrar. Nothing works. And yes the files were made in windows.

---

### Post by Bkdoorbandit on 2009-03-24
My problem is that i'm not the owner anymore so i don't have access to the files. I can't change them in any way. Don't know if it helps but when i zipped the files (long time ago) i did something which i can't remember so that the names were in green, instead of in blue.

---

### Post by longtom on 2009-03-24
> **Bkdoorbandit said:**
> My problem is that i'm not the owner anymore so i don't have access to the files. I can't change them in any way. Don't know if it helps but when i zipped the files (long time ago) i did something which i can't remember so that the names were in green, instead of in blue.

When the data appears green in windows it means, that you have encrypted them.
That is what it means.  How to get rid of it I don't know.  If at all possible from ubuntu I am not sure.

Have you started Nautilus as administrator and tried to edit permissions of the files in question?

---

### Post by Bkdoorbandit on 2009-03-24
Yeah, no permission =/

---

### Post by romuald_geo on 2009-03-24
Perhaps you should change permissions on this files.With Windows partition it is done when mounting a partition.

---

### Post by GepettoBR on 2009-03-24
> **longtom said:**
> Have you started Nautilus as administrator and tried to edit permissions of the files in question?

> **Bkdoorbandit said:**
> Yeah, no permission =/

I don't think you got it. Open Nautilus as administrator (type "gksudo nautilus" in a terminal or in the Alt+F2 prompt), right-click the file in question and try to change the permissions in Properties.

Does that change anything?

---

### Post by Bkdoorbandit on 2009-03-24
> **GepettoBR said:**
> I don't think you got it. Open Nautilus as administrator (type "gksudo nautilus" in a terminal or in the Alt+F2 prompt), right-click the file in question and try to change the permissions in Properties.

Does that change anything?


That's what i've done. When the file browser opens i can see my desktop as root, but when i navigate to the HDD that the files are on the root disappears? And again no permission.

---

### Post by GepettoBR on 2009-03-24
The root disappears? As long as that particular Nautilus window is open, it will be open as root. Maybe you're talking about leaving the /root folder.

---

### Post by Bkdoorbandit on 2009-03-24
> **romuald_geo said:**
> Perhaps you should change permissions on this files.With Windows partition it is done when mounting a partition.

As root i changed so that i'm supposed to be able to read and write but i'm not the owner so i still get denied. I've mounted the HDD in vista and tried TakeOwn which didn't work.

Since they're encrypted, is there any way to decrypt the files? :S

---

### Post by Bkdoorbandit on 2009-03-24
> **GepettoBR said:**
> The root disappears? As long as that particular Nautilus window is open, it will be open as root. Maybe you're talking about leaving the /root folder.

Weel in the rootfolder i can only see desktop, so to get to the files i have to leave the root folder. Or how do i get to the files via the root folder? I never leave the file browser that  opens when i type in gksudo nautilus.

---

### Post by GepettoBR on 2009-03-24
> **Bkdoorbandit said:**
> Weel in the rootfolder i can only see desktop, so to get to the files i have to leave the root folder. Or how do i get to the files via the root folder? I never leave the file browser that  opens when i type in gksudo nautilus.

You don't have to be in the root folder.

gksudo nautilus opens the file manager as the root *user*, so in that specific window you'll be root no matter which folder you go to. Navigate normally to the folder where your file is, right-click, select properties, go to the permissions tab. There, change the owner of the file to your username and make sure he has read/write/execute permissions. Close the window and try extracting the file, it should work now.

---

### Post by Bkdoorbandit on 2009-03-24
Yes i've done that too but it still doesn't work. "Permission denied". Have to go to the dentist but i'll be back ;D

Can it have anything to do with that they're encrypted?

---

### Post by GepettoBR on 2009-03-24
> **Bkdoorbandit said:**
> Yes i've done that too but it still doesn't work. "Permission denied". Have to go to the dentist but i'll be back ;D

Can it have anything to do with that they're encrypted?

Possibly, but root should have access to everything. Is this particular file in a read-only drive?

---

### Post by Bkdoorbandit on 2009-03-24
"The permissions of Extern 2 could not be determined."

---

