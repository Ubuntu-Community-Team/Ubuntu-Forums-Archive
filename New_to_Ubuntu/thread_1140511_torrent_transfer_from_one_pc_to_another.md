---
title: "torrent transfer from one pc to another?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by uraliss on 2009-04-27
Hi folks,
I currently have a large torrent that I am downloading to my laptop using Transmission.

My laptop is wireless and is not on all the time so the download looks like it might take 3 weeks to download. How would I go about moving this to my server which is permanently on and on a fast network?

Any ideas?

---

### Post by mkvnmtr on 2009-04-27
SSH if they are both Ubuntu. Samba if one is windows.

---

### Post by uraliss on 2009-04-27
Yes thanks... but which files do I move?

---

### Post by MrWES on 2009-04-27
Navigate to the directory with the file and use scp (secure copy) to move the file:

```
scp /path/to/file username@IP_of_Server:/path/to/copy/to
```

Make sure you have rw perms to where you are copying the file to.

Bill

---

### Post by llamabr on 2009-04-27
Why don't you just start the torrent on the desktop?

Whatever the file is, if you want the head start, you can use scp (secure copy) to send between them, like this:

```
scp file 192.168.0.101:~/
```

---

### Post by uraliss on 2009-04-27
cheers guys.
I have managed to locate the files which is what i really meant to ask.

sorry for being confusing :)

---

### Post by llamabr on 2009-04-27
Ahh, if it's more than one file, you can stop the torrent, tar up the directory that they're in, like this:

```
tar -cvf dir.tar directory/
```

and then scp, as above, then untar:

```
tar xvf dir.tar
```

---

