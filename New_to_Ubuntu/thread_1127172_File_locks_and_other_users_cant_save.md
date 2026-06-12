---
title: "File locks and other users cant save"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Hopelesslylost on 2009-04-16
Hi, I have been trawling through the forums but have as yet not found an answer.

We currently have 3 Admins working on a shared Excel Workbook, the problem (that some may be able to see straight away) is that when one Admin saves, the file gets locked to them and the others can't save the file.

I have created the user accounts as Admins (in the User and Groups section in Ubuntu) and added them to a group that has full admin rights.

I created the Samba share and added them all as users able to view and write to the files.

So far the only way around this is to go to the directory in Terminal and type;

sudo chmod 777 *Excel Workbook Name* 

This then removes the lock and others can save.

The Admins are using this as an excuse not to get any work done, really need some help and any you could provide would be greatly appeciated.

Thanks.

---

### Post by madverb on 2009-04-16
Sticky bit?

[http://en.wikipedia.org/wiki/Sticky_bit](http://en.wikipedia.org/wiki/Sticky_bit)

---

### Post by Hopelesslylost on 2009-04-16
Ok,

So just to make sure I got this right, I need to browse to the directory in Terminal then type

sudo chmod -t "NVQ Live & Control Sheet"

This would then let any user overwrite existing files regarless of owner?

Thanks

---

