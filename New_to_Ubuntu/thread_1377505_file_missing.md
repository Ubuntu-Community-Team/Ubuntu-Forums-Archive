---
title: "file missing"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by arunkmohan18 on 2010-01-10
hi
yesterday i downloaded some in ubuntu and save it in another partition (ntfs) after i restart system i missed all downloaded files please help me about this

---

### Post by akand074 on 2010-01-10
Was the other partition you downloaded it to mounted when you did the download? if not it will instantly say the download is complete even though it was never downloaded.

---

### Post by arunkmohan18 on 2010-01-10
it's downloaded and run it one time(i aborted installation) after that i restart the system and i missed that files

---

### Post by garryknight on 2010-01-10
If the directory you downloaded the files into wasn't mounted when you downloaded them, but now is mounted, then the files will be hidden. Look at it this way: let's say you usually mount the NTFS partition on /mnt/ntfs. Before mounting, /mnt/ntfs is empty. You download a file (or move or copy it from somewhere else). Now /mnt/ntfs contains that file and only that file. Now you mount the partition and /mnt/ntfs contains all of the files on the remote machine. The file you downloaded is hidden. If you unmount the partition, the hidden file will be revealed again.

I'm not saying that this is what happened in your case; there are several possible reasons for your problem. You've given so little information that all anyone can do is guess. You say you've saved it in "another partition (ntfs)"; is that partition on the same machine or is it a network share? Was it mounted when you did the download? Can you be sure about that? Is the partition usually mounted when you start the system? Was it mounted when you looked for the files?

---

### Post by arunkmohan18 on 2010-01-10
i am using ubuntu and windows xp for linux i give 5 gb space so when i downloading files it saves in another filesystem and i'm sure that i mounted this all but after i saved this file i try to write files it's take long time so i abort that then shutdown next day i start system but i cannot see the file it's saying folder is empty

---

### Post by garryknight on 2010-01-11
Ok, slow down, take a deep breath, and go back and edit your last post so that it has some punctuation. It's impossible to understand what you're trying to say unless you do that.

---

