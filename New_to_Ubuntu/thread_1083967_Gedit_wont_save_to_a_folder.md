---
title: "Gedit wont save to a folder?"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by dorseye on 2009-03-01
I have a Ubuntu guest, which has a shared folder to my Vista host. Whenever I try to save a .txt file with Gedit it says "Unexpected error: Text file busy", and yet GVIM can save fine, GIMP can save to that folder with no issues, etc. It seems like its isolated to Gedit. Any ideas?

---

### Post by arochester on 2009-03-01
What command have you used to start Gedit? Try > gksudo gedit [name of file you are using or want to create] Thay will give you superuser rights...

---

### Post by whoop on 2009-03-01
What kind of file system is vista using?

---

### Post by dorseye on 2009-03-01
> **arochester said:**
> What command have you used to start Gedit? Try Thay will give you superuser rights...

I'm just clicking from the GUI/Xwindows.

Why would Gedit need sudo rights when none of the other programs do? I'd prefer not to be using sudo unless neccesary.

Vista is NTFS.

---

### Post by Xiong Chiamiov on 2009-03-01
Mm, launching applications as root without good reason is a bad idea.  First you should check the permissions on the file to see if you have write permission, although from the error you got, I'd think so.

Do you have any problems with saving that file using a different editor (nano, OpenOffice, whatever else is included with Ubuntu)?

---

### Post by dorseye on 2009-03-01
> **Xiong Chiamiov said:**
> 
Do you have any problems with saving that file using a different editor (nano, OpenOffice, whatever else is included with Ubuntu)?

No, that's what is so weird -- as I said, any other application can write to any file they please. GVIM, GIMP, etc all write fine to that folder, no super user permissions needed. 

When I view the permissions of the folder, it does show root as the owner, however, I've made everyone have read/write access. (see attached image)

---

### Post by Xiong Chiamiov on 2009-03-01
The only two things I can find on [the Googles](http://www.google.com/search?hl=en&q=%22Unexpected%20error%3A%20Text%20file%20busy%22&aq=f&oq=) indicate that it is a bug in Samba that will be fixed... sometime.

---

### Post by llamabr on 2009-03-01
Right.  So it looks like gedit is the culprit for now.

Have you tried using a different text editor?  Such as nano?

---

### Post by dorseye on 2009-03-01
> **llamabr said:**
> Right.  So it looks like gedit is the culprit for now.

Have you tried using a different text editor?  Such as nano?

I do use GVIM for coding Python, but for just dumping in a quick/copy paste I just went ahead and installed Scite, and it works without any of the conflicts/problems. Just kind of a bummer that the simple included text editor is broken with shared folders :/

On another note, I'll check out Nano too.

---

### Post by nshoham on 2009-03-03
I have the same problem with:
Ubuntu 8.10 guest
kernel-2.6.28.7
vbox-2.1.2
windowsXP-SP2

---

### Post by Kellemora on 2009-03-03
Hi Dorseye

Are you SURE other files are written?

I saw you named Gimp as one that can save a file to a remote folder.

If that's possible, PLEASE tell me HOW!

We can open an existing file from the file server, edit it and put it back on the file server.

However, a new file, shows it's saved, until you go to look for it, and it's never there.

So we have a very STRICT RULE around here!  NEVER PUT a new file onto the File Server, place it on your desktop shared folder and let the File Server FETCH that file from there on it's own.  Once it appears on the File Server, then you can save it back there after editing.

I've had a LOT of folks, some quite sharp study this problem to no avail.

We use Rsync to check all the computers for files running FROM the file server so it FETCHES files.  Even Rsync cannot PUT remote files away, it can only FETCH them.  Been that way for 6 months here now!

TTUL
Gary

---

### Post by dorseye on 2009-03-03
> **Kellemora said:**
> I saw you named Gimp as one that can save a file to a remote folder.

It's a shared folder from my Vista, this line in my rc.local allows (Virtualbox guest) Ubuntu to see and interact with it. I dont think that's the same thing you're doing with your fileserver and rsync is it?

```
mount -t vboxsf _VirtualBoxShared /home/dorseye/VBoxShare/
```

But yes, my other programs, Scite, Open Office, GIMP, can all save to the shared folder.

---

### Post by stchman on 2009-03-03
Try making you the owner of everything in your /home as it should be.

```
sudo chown -R $USER:$USER ~/
```

This will make all the files and folders in your home folder be owned by YOU.  There is no reason for root to own any files in your /home folder.

---

### Post by dorseye on 2009-03-03
> **stchman said:**
> Try making you the owner of everything in your /home as it should be.
```
sudo chown -R $USER:$USER ~/
```
This will make all the files and folders in your home folder be owned by YOU.  There is no reason for root to own any files in your /home folder.

This results in:
```
dorseye@ub:~$ sudo chown -R $USER:$USER ~/
chown: cannot access `/home/dorseye/.gvfs': Permission denied
dorseye@ub:~$
```

---

