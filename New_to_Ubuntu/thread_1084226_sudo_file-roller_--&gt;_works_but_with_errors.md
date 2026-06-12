---
title: "sudo file-roller --&gt; works but with errors?"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by dorseye on 2009-03-01
Greetings,

I was unpacking an add-on library to Python 2.5 called Beautiful Soup.
I didn't have permission to run fileroller and unpack the tar.gz file into the correct place, so ran:

```
dorseye@ubu8:~$ gksudo fileroller
dorseye@ubu8:~$ cd /home/dorseye/VBoxShare/download_share
dorseye@ubu8:~/VBoxShare/download_share$ ls
BeautifulSoup.tar.gz
dorseye@ubu8:~/VBoxShare/download_share$ gksudo sudo file-roller
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:6622): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///usr/lib/python2.5/site-packages

(nautilus:6622): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:6622): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
Shutting down nautilus-share extension
seahorse nautilus module shutdown
dorseye@ubu8:~/VBoxShare/download_share$
```

What do all these warnings mean? Should I be concerned about any of that? Unable to add monitor? Does that mean a physical monitor, or some kind of BASH monitoring tool? And why was the GUI file browser Nautilus throwing in some Eel warnings of it's own? 

Sincerely,
Confused Ubuntu Noob

---

### Post by iaculallad on 2009-03-01
What about uncompressing the file using the terminal?

```
sudo tar -zxvf BeautifulSoup.tar.gz
```

---

### Post by RomeReactor on 2009-03-01
Hi. Not sure why you get those errors; was VirtualBox running while you ran file-roller?

To extract the .tar.gz file, you can do it like this:
```
tar -xvzf FILENAME.tar.gz /PATH/TO/EXTRACT
```
If you get permission errors when extracting to the destination folder, run tar with sudo, or copy the extracted folder using sudo:
```
sudo cp -R /PATH/TO/FOLDER /PATH/TO/DESTINATION
```

---

### Post by asmoore82 on 2009-03-01
I opened a root `nautilus` session and double-clicked an archive and extracted it -
got the same messages but the extraction worked.
I would say it's nothing to worry about.

```
**~$** gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:21160): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///home/asmoore

(nautilus:21160): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:21160): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
```

---

