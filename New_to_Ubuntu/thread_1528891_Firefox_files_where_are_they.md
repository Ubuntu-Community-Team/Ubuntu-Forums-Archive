---
title: "Firefox files: where are they?"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by Autodave on 2010-07-11
Computer crashed yesterday, but I was able to save some files from it.  What I am hoping I saved is my bookmarks in Firefox.  Where exactly would that be located and what would it be called?

---

### Post by techunit on 2010-07-11
```
home/user-name/.mozilla/firefox/tru815rq.default/bookmarkbackups
```

this is where alot of data for firefox's bookmarks is stored. at yourhome screen click "alt-f2" a dialogue box will pop up and type the following into it.

```
nautilus /home/**your-username**/.mozilla/firefox/
``` from there open tru815rq.default (or similar folder name) and copy the "bookmarksbackups" folder.

---

### Post by Shazaam on 2010-07-11
/home/yourusername/.mozilla/firefox/*********.default/bookmarks.html
where the *'s is your Firefox user id (numbers and letters mixed).

You will have to have "show hidden files" enabled in nautilus preferences or use CTRL+h to show them.




*durnnit, out-typed lol.

---

### Post by Autodave on 2010-07-11
Thank you both!

---

### Post by lovinglinux on 2010-07-11
> **Shazaam said:**
> /home/yourusername/.mozilla/firefox/*********.default/bookmarks.html
where the *'s is your Firefox user id (numbers and letters mixed).

Firefox bookmarks are not stored in the bookmarks.html. That is an old file from Firefox 2, kept for compatibility issues.

Bookmarks are stored in a sqlite database, name **places.sqlite**.

> **techunit said:**
> ```
home/user-name/.mozilla/firefox/tru815rq.default/bookmarkbackups
```

this is where alot of data for firefox's bookmarks is stored. at yourhome screen click "alt-f2" a dialogue box will pop up and type the following into it.

```
nautilus /home/**your-username**/.mozilla/firefox/
``` from there open tru815rq.default (or similar folder name) and copy the "bookmarksbackups" folder.

The folder bookmarksbackups is where firefox saves backups, which are created once a day, if you change any bookmarks. As already mentioned above, bookmarks are stored in the file places.sqlite. 

To restore a backup from an old profile, copy the backup folder as already explained by techunit, then click “Bookmarks >> Organize Bookmarks” then select “Import and Backup”, then "Restore", then select on of the backup files available.

I recommend making backups of your entire profile regularly. See more info [here](http://firefox-tutorials.blogspot.com/2010/05/backups.html).

BTW, Firefox 4 will have an online service for syncing bookmarks, passwords, history, tabs and preferences.

---

