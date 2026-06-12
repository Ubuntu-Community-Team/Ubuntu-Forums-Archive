---
title: "QUESTION about the .evolution folder"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by suomalainen on 2010-03-12
Ubunteros,

I'm running 8.04 LTS 64 bit. For some reason my version has become unstable and I need to do a re-install of the same version.

Before I do the re-install I would like to have a question answered.

If you go to:

1. Places
2. Home Folder
3. Ctrl + h
4. You will find a folder called ".evolution".

My question is this. Before re-installing 8.04 can I copy the .evolution folder to a safe location and then copy it back once the reinstall has finished?

If so, will I retain all my email? How about email account settings like outgoing server incoming server etc...?

Thanks for answering my question!

---

### Post by howefield on 2010-03-12
> **suomalainen said:**
> My question is this. Before re-installing 8.04 can I copy the .evolution folder to a safe location and then copy it back once the reinstall has finished?

If so, will I retain all my email? How about email account settings like outgoing server incoming server etc...?



Yes it will, you may also have the ability to back up your settings/email through the menu option.. File > Backup Settings.

---

### Post by 3rdalbum on 2010-03-12
Backup all the folders and files in your home directory that start with a dot (.), but only restore them if you find you need them. With the Evolution one, you'd obviously restore that one as soon as possible :-)

---

### Post by audiomick on 2010-03-12
For Evolution specifically, there is a function in the "file" menu called something like "save settings" and it's partner "recall settings" or something similar to that. Mine is in German, so the translation might be a bit off.

The "save" one creates a .tz file containing your account info, the mails you had stored on the computer, and how your grandmother likes to drink her tea. The "recall" one lets you choose the .tz you saved, opens it, and makes evolution like it had always been there.

---

### Post by suomalainen on 2010-03-12
I forgot to mention one important item.

I cannot boot up 8.04 anymore. HOWEVER, when I use live CD I can see my old 8.04 drive and the files it contains.

Question: Where exactly will be the .evolution file I'm looking for? I'm unsure as to which folder I must go to find it.

Also, I have dual displays using nvidia. How can I back up my dual display settings?

Thanks

---

### Post by audiomick on 2010-03-12
It is in /home/username. You have to select "show hidden files" in the "view" menu of the file manager (nautilus) to see it.

---

### Post by suomalainen on 2010-03-13
All,

Does "/home/username" also contain my nvidia settings for the dual displays I use??

Thanks!

---

### Post by howefield on 2010-03-13
> **suomalainen said:**
> Does "/home/username" also contain my nvidia settings for the dual displays I use??

Try

/etc/X11/xorg.conf

---

### Post by audiomick on 2010-03-13
> **howefield said:**
> Try

/etc/X11/xorg.conf
Correct. I have successfully saved mine across a couple of fresh installs. You need root privileges to access it. Open it with
```
gksu gedit /etc/X11/xorg.conf
```
and do "save as" /where/you/want/to/put/it/xorg.conf_backup_date
After you reinstall, it is likely that only one monitor will work or something else will be strange about the video. Install the proprietary nVidia driver. Open your backup the same way and do "save as" /etc/X11/xorg.conf and restart. You should then have your monitor setup back.

---

### Post by suomalainen on 2010-03-13
Thank you all for this very important information. I appreciate you helping me! Thank You!

---

