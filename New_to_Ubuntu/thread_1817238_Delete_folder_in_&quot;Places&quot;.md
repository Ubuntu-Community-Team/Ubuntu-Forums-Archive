---
title: "Delete folder in &quot;Places&quot;?"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by Smaug95swe on 2011-08-03
I accidently added a folder to my "Places" Bar... and ive even deleted it so i cant open it... how do i remove it? (Gnome)

---

### Post by nothingspecial on 2011-08-03
Right click

---

### Post by plucky on 2011-08-03
> **Smaug95swe said:**
> I accidently added a folder to my "Places" Bar... and ive even deleted it so i cant open it... how do i remove it? (Gnome)

Open Nautilus and **Edit Bookmarks**

---

### Post by Wim Sturkenboom on 2011-08-03
edit .gtk-bookmarks, e.g like below
```

vi .gtk-bookmarks

```
works in Ubuntu 10.04

---

### Post by Smaug95swe on 2011-08-03
First post: No it just says i can open that folder...
Second: How do i do that? Lol cant find it... -.-
Third: Yea that listed them but how do i delete them?

---

### Post by tommpogg on 2011-08-03
> **Smaug95swe said:**
> 
First post: No it just says i can open that folder...

I agree. Right clicking just opens the folder.

> **Smaug95swe said:**
> 
Second: How do i do that? Lol cant find it... -.-

Type nautilus in a terminal to open your home directory. On the left side there is a panel showing the links to your bookmarks. Remove those you don't like.

> **Smaug95swe said:**
> 
Third: Yea that listed them but how do i delete them?

I don't know. Removing the corresponding lines doesn't work.

---

### Post by nothingspecial on 2011-08-03
Sorry, I wasn't clear.

The folders in your places menu are the same folders that are in the left hand side bar when you are using the file browser.

If you right click the entry in the side bar of your file browser and choose remove, then it will also disappear from your places menu.

My fault for assuming things.

---

### Post by Wim Sturkenboom on 2011-08-03
> **Smaug95swe said:**
> 
Third: Yea that listed them but how do i delete them?
> **tommpogg said:**
> I don't know. Removing the corresponding lines doesn't work.

Worked for me; delete the line and save the file removed it immediately. Tested it with the 'standard' Documents that is in there.

Ubuntu 10.04

---

### Post by Smaug95swe on 2011-08-03
It does not show up where you guys said it should... but the other folders do like downloads etc and okey i deleted the rows with the "code" how do i save it? didnt work to just shut itoff

---

### Post by jtarin on 2011-08-03
Pretty straight forward:
Nautilus>(top menu)Bookmarks>Edit Bookmarks>Highlight the one you want to remove and click "Remove".

---

### Post by jtarin on 2011-08-03
> **Smaug95swe said:**
> It does not show up where you guys said it should... but the other folders do like downloads etc and okey i deleted the rows with the "code" how do i save it? didnt work to just shut itoffVi can be difficult for new users. Use Nano instead.
Open a terminal and type ```
nano .gtk-bookmarks
``` use the arrow keys to maneuver to the offending line and the delete key to remove it. Then a combination of the CTRL + O (letter) keys will write the new file. It will ask you to confirm...just hit the enter key then Ctrl + X keys to exit.

---

### Post by Smaug95swe on 2011-08-03
Thanks!

---

