---
title: "How to change &quot;places&quot; menu items targets"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by webwiller on 2009-03-04
Hi all!:D
I try to explain...
I just dual-boot my laptop trying give-up windows...I made a 3partitioning with a c:\ partition for win, a "/" for ubuntu, & a /media/data as a shared partition between windows&ubuntu.
I dont want to use my home folder for all my docs, and I would like to delete music/videos/docs subfolders (I cant just delete /home, isn't it?) from the $HOME & replace them with docs/music/video/whatever under media/data.
I would like my "places" menu to show links targeting my /media/data partition and not my $HOME.
Thx in advance!:)

---

### Post by hammad1337 on 2009-03-04
to place /media/documents in /home/user/documents, use this:

```

sudo mount --bind /media/documents /home/user/documents

```

u can replace /media/documents and /home/user/documents with whatever directories you have to place.

hope this helps.

However, I have no idea for replacing things in the places menu...
I also feel the need to do that n will keep checking this thread to see if any one has a solution to offer.

---

### Post by binbash on 2009-03-04
open nautilus and go to bookmarks.You can add manage rename etc.

---

### Post by webwiller on 2009-03-04
cant get it right...it just goes on the following line as if I didnt type anything...
lets say my exact directories are
/media/data/Musica
&
/home/christian/Musica
what I typed in is:

sudo mount --bind /media/data/Musica /home/christian/Musica

but nothing happended:-%

---

### Post by markusf21 on 2009-03-04
navigate to your data partition, find the folder you want. right click it and make a shortcut. then cut the shortcut and place it in your home folder. delete the original folder in home and then rename the shortcut to what the deleted folder was called.

---

### Post by Jingle on 2009-03-04
I can confirm that what the previous poster suggested worked for me a couple of weeks ago,

I made shortcuts to the relevant folders and placed them in my home directory, deleted the original folders (which were empty anyway) and it worked beautifully.

However as the folders you want to link to are on a different partition you'll have to modify your fstab file to mount this partion on bootup otherwise you'll be entering your password all the time and it's REALLY annoying.

I can't remember exactly what I did to get to my fstab file as I'm still new at all this myself.

---

### Post by webwiller on 2009-03-04
when I try to create a shortcut inside my /media/data partition I get: operation not permitted
???

---

### Post by Jingle on 2009-03-04
You don't want to create the shortcut IN your data partition, you want to create the shortcut in your home folder and link it TO your data partition I think.

I'm not sure why you're getting not permitted error, is the partition mounted?

---

### Post by markusf21 on 2009-03-04
This will make you the owner of that partition
```
sudo chown -R username:username /media/data
```
Then try making the shortcuts again.

---

### Post by theozzlives on 2009-03-04
Your Places bookmarks co-inside with the folders in the lower left of your Nautilus window. You can right-click on folders and click remove, or you can drag folders and add them. No matter where they are.

---

### Post by sfehrman on 2009-03-12
The easiest way I just found, was previously mentioned. Open a Nautilus window and edit the "Bookmarks"  These are what I was wanting to change at least. Hope it helps.
Or as the last poster mentioned just drag and drop them onto the left pane of a nautilus window(these are the bookmarks)

---

