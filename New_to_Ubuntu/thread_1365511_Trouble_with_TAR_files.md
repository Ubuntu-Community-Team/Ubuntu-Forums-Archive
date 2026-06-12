---
title: "Trouble with TAR files"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by mistypotato on 2009-12-27
Hello,

I have successfully created a TAR archive file and have trouble Extracting from it.

When I use the Archive Manager to view the Archive, the backed up files are there as exptected.

When I run the Extraction, and try to extract the files it goes through all the motions (verbose is on) and goes through all the files as if it is restoring them as I see them all listed...BUT....the files are never actually extracted :confused:

I TARRED the files using the "c" and "p" and "f" and "h" parameters.

When I extract, I use the "x" "p" and "f" parameters.

I did a full filesystem search and the files were not accidentally extracted to another location so I'm stumped.

Anyone see an obvious mistake here?

---

### Post by CharlesA on 2009-12-27
Perhaps try running:
```
tar -cf somefile.tar

tar -xf somefile.tar
```

---

### Post by apmcd47 on 2009-12-27
Stupid question, but where did you extract them to? If you extracted the tar file in the same directory as you created it the files probably overwrote the originals.

Andrew

---

### Post by mistypotato on 2009-12-27
> **CharlesA said:**
> Perhaps try running:
```
tar -cf somefile.tar

tar -xf somefile.tar
```

Charles,
I can't tell if you are making a guess or you see the problem?

---

### Post by mistypotato on 2009-12-27
> **apmcd47 said:**
> Stupid question, but where did you extract them to? If you extracted the tar file in the same directory as you created it the files probably overwrote the originals.Andrew

Hello, :KS
I have two servers...one is a backup of the other.

So, I'm COPYING them from location "mylocation" on server "A" to the same folder and location on server "B".

The folder names are all the same, the physical computer is different.

Maybe you're on to something ?

---

### Post by CharlesA on 2009-12-27
> **mistypotato said:**
> Charles,
I can't tell if you are making a guess or you see the problem?

Just checking to see if it might be a permission issue.

---

### Post by apmcd47 on 2009-12-27
> **mistypotato said:**
> Hello, :KS
I have two servers...one is a backup of the other.

So, I'm COPYING them from location "mylocation" on server "A" to the same folder and location on server "B".

The folder names are all the same, the physical computer is different.

Maybe you're on to something ?

So is the backup directory already populated? Try extracting into an empty directory to test tar. Tell us if you already are doing that, if only to stop stupid "do what you are already doing" posts :)

Be ready for the "why don't you use rsync" posts.
Andrew

---

### Post by CharlesA on 2009-12-27
> **apmcd47 said:**
> 
Be ready for the "why don't you use rsync" posts.

I was going to go thar but if they want to use tar, I'm sure they have their reasons. :)

---

