---
title: "Is there a way to save Firefox seetings and bookmarks to transfer them on new OS?"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by oingk on 2010-02-13
Hi guys.

I'm going to have to make a clean reinstall of my operating systems and I have a question. I don't want to lose my Firefox settings and bookmarks etc. Is there a way to save all these as a file somewhere and transfer them on my new operating system ?


Thanks.

---

### Post by kgarbutt on 2010-02-13
Yes, follow this:

Bookmarks/Organize Bookmarks/Import and Backup/Backup to backup,

then use restore to restore them.

---

### Post by iponeverything on 2010-02-13
```
cd ~
tar -cvf mozilla.tar .mozilla


```
copy ~/mozilla.tar to a pen drive.
On the new install copy mozilla.tar to ~

```

tar -xvf mozilla.tar
chown -R yourusername.yourusername .mozilla

```
and fire up firefox.

---

### Post by 73ckn797 on 2010-02-13
Another way that will save all of the data, not just bookmarks is to backup or copy your profile folder. That will be located in:
```
/home/yourname/.mozilla/firefox/*.default
```"yourname" is your home folder.
The  "*.default" folder is your Firefox info. You will also want to backup the "profile.ini" file in the ```
/home/yourname/.mozilla/firefox
``` folder.

Copy the contents to a flash drive or CD.

You can do the same for Thunderbird if you want to save that info. This would also apply to any other folder in your /home folder for other programs if you plan on re-installing those programs.

Best thing would be to create a separate /home partition when you re-install. That way if a later install is needed, you will already have your settings and will not lose them at all.

---

### Post by Bluppie on 2010-02-13
You can also use Xmarks to keep your bookmarks and passwords up to date. Xmarks is an firefox extension. :)

---

### Post by ajgreeny on 2010-02-13
And the extension FEBE will do all that and more.
[https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)

---

### Post by switch10 on 2010-02-13
> **Bluppie said:**
> You can also use Xmarks to keep your bookmarks and passwords up to date. Xmarks is an firefox extension. :)

+1  xmarks is awesome.  Saves passwords and bookmarks.

---

### Post by oingk on 2010-02-13
thanks guys you always help me.

---

