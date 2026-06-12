---
title: "De-dup files across a network? (Lacie hard drive)"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by blueghoti on 2010-09-06
Hi all - 

I'm running Ubuntu 10.04 and I know I have several duplicate files on my Lacie Internetspace drive, which is sitting on my home network.

I have some files (images, documents, spreadsheets etc) which are duplicated across my computer and harddrive.  

Is there a good de-duping application I can use that will identify these files and allow me to delete them?

Chris

---

### Post by yeats on 2010-09-06
Try fdupes - it's a command-line-based program, but it's pretty straightforward.  From a terminal:

```
sudo apt-get install fdupes
```

then 

```
man fdupes
```

to see the options.

---

### Post by blueghoti on 2010-09-08
Thanks Chris - will give that a try!

---

### Post by HermanAB on 2010-09-08
Hmm, fdupes seems to work - good suggestion - I wasn't aware of it.  

You should also try using rsync instead of ordinary cp to prevent dupes from happening in the first place.

---

### Post by blueghoti on 2010-09-12
> **chrissharp123 said:**
> Try fdupes - it's a command-line-based program, but it's pretty straightforward.  From a terminal:

```
sudo apt-get install fdupes
```then 

```
man fdupes
```to see the options.


Hi Chris - 

Am finally getting around to this :-)

BTW - I read the manpages, but don't quite understand how to instruct it to search in my network drive.  The path starts smb://hipserv/familylibrary/ - any ideas?

Chris

---

### Post by blueghoti on 2010-09-12
> **HermanAB said:**
> Hmm, fdupes seems to work - good suggestion - I wasn't aware of it.  

You should also try using rsync instead of ordinary cp to prevent dupes from happening in the first place.


Thanks Herman.  I've been looking for a good backup program for Linux.  I have a dup problem because I moved from Vista to Linux and couldn't figure out the right backup solution for Vista :-)

Will rsync work for timed and incremental backups?

Chris

---

### Post by TCHebb on 2010-09-12
> **blueghoti said:**
> Hi Chris - 

Am finally getting around to this :-)

BTW - I read the manpages, but don't quite understand how to instruct it to search in my network drive.  The path starts smb://hipserv/familylibrary/ - any ideas?

Chris
You have to mount the network drive first. In your case, I believe the command would be
```
mount -t cifs \\HIPSERV\familylibrary\ <directory name>
```Then the share will be mounted at <directory name>, and you can use normal commands from there.

---

