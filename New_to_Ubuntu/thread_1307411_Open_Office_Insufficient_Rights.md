---
title: "Open Office Insufficient Rights"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-10-31
I had wipe out of my disk (setting up Karmic and so went back to Jaunty). In the process I restored all my documents. Now, however, I cannot make changes. I can only open my spreadsheets as read only. For example, I have a spreadsheet called Stocks.ods...I can only open it as a read only. If I edit it I can save it as xxstocks.ods and can save xxstocks.ods as xystocks.ods....but, even after deleting the original Stocks.ods, I cannot save it as Stocks.ods....it says that it is open for editing and that I have insufficient rights. I have changed the rights using root to read, write, execute by all....but still no joy....It just refuses to save as Stocks.ods....other programs call on Stocks.ods...so I need to keep the name.

What am I doing wrong?

---

### Post by NE Key on 2009-10-31
I know what you did. When you copied all your docs to a safe place and then back onto your drive after your install you managed to change the permissions so "you" don't own them anymore. (I once did the same).

There is a command to change the permissions of a folder and all its contents.....I cannot remember it exactly but a search in this forum will reveal it.

Or you could research the command *chown* which I think means "change owner".

use the command  *man chown*  to show you the manual for chown.

I cannot supply the full answer but I hope this gives you enough to find it.

---

### Post by dunbrokin on 2009-10-31
Tried doing that with chmod u+x stocks.ods but made no difference...can open all files except this one...is is closed for editing..whatever that means.

---

### Post by dunbrokin on 2009-10-31
There is a hidden file in each folder which you have to expose using the show hidden files under View. Delete the hidden locked file and you are away!!

---

### Post by Absorbed on 2009-10-31
> **dunbrokin said:**
> Tried doing that with chmod u+x stocks.ods but made no difference...can open all files except this one...is is closed for editing..whatever that means.

The "+x" gives you permission to execute the file, but not permission to read and write. To add read and write permission as well, you need to type the following:

```
chmod u+rwx [your file]
```

---

### Post by jrrader on 2009-10-31
If you move your files and then moved them back, you probably lost ownership of them. Some might be working now because you gave permissions to others.  This will give you ownership of everything in your home directory.

```
sudo chown -R [username:groupname] /home/[username]
```replace username and groupname with your username (and remove the brackets)

---

