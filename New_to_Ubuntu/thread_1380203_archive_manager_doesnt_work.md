---
title: "archive manager doesnt work"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by libihero on 2010-01-13
when i try to open .tar or .zip or any other compressed files, a window opens and says "error while loading archive: command exited abnormally"
i can access the files by mounting the archive, but it wont just let me open them

---

### Post by warfacegod on 2010-01-13
Go to Synaptic under Edit and select Fix broken packages.

If that doesn't work.

Try reinstalling it. If you can do it from synaptic choose mark for complete removal.

---

### Post by libihero on 2010-01-13
neither worked :(

---

### Post by warfacegod on 2010-01-13
Is it just a handful of compressed files or everyone you ever tried.

---

### Post by libihero on 2010-01-13
well the .tar.gz works now but the .zip still doesnt

---

### Post by warfacegod on 2010-01-13
I believe you need to add .zip support manually .rar as well. Go to:

System> Admin.> Synaptic and search zip and rar and install something for both.

Hang on a few and I'll look to find out what I'm using.

---

### Post by warfacegod on 2010-01-13
I'm using unrar and unzip.

---

### Post by tom.swartz07 on 2010-01-13
> **warfacegod said:**
> I'm using unrar and unzip.

+1

Just add them from synaptic, and you should be able to open them then.

---

### Post by warfacegod on 2010-01-13
> **tom.swartz07 said:**
> +1

Just add them from synaptic, and you should be able to open them then.

Cool. +1

Um.... What does +1 mean?

---

### Post by k64 on 2010-01-13
> **libihero said:**
> well the .tar.gz works now but the .zip still doesnt

```
sudo apt-get install unrar unzip
```

---

### Post by libihero on 2010-01-13
both are already installed :(
```
unrar is already the newest version.
unzip is already the newest version.
```

---

### Post by tom.swartz07 on 2010-01-13
> **libihero said:**
> both are already installed :(
```
unrar is already the newest version.
unzip is already the newest version.
```

move the file you want unzipped to your desktop

in a terminal```
cd ~/Desktop
```
```
unzip "filename"
```

or
```
unrar "filename"
```

That'll do it for ya!

---

### Post by libihero on 2010-01-13
here's what happens when i tried unzipping something random
```
unzip ./Desktop/a.zip
Segmentation fault

```

---

### Post by warfacegod on 2010-01-13
> **libihero said:**
> both are already installed :(
```
unrar is already the newest version.
unzip is already the newest version.
```

Well that's just perfect. (Sarcasm intended) Back to square one.

It would be great if  tom.swartz07's last post works for you. Fortunately, if it did, it would also expose more closely what the problem is. More specifically, why on Earth do you need to move compressed folders to the desktop to get them to open?

---

### Post by warfacegod on 2010-01-13
I'm wondering those .zip files are corrupt.

---

### Post by tom.swartz07 on 2010-01-13
> **warfacegod said:**
> Well that's just perfect. (Sarcasm intended) Back to square one.

It would be great if  tom.swartz07's last post works for you. Fortunately, if it did, it would also expose more closely what the problem is. More specifically, why on Earth do you need to move compressed folders to the desktop to get them to open?

i suggested moving them to the desktop for ease of access. you could really unzip anywhere. 

Warfacegod might be right- the zip file might be corrupt?

---

### Post by libihero on 2010-01-13
nope its all zip files, i even made some and it wont unzip

---

### Post by warfacegod on 2010-01-13
> **libihero said:**
> nope its all zip files, i even made some and it wont unzip

Oh! Good grief! 

(warfacegod quickly decides to bow out gracefully before having to admit he now knows nothing at all)

---

### Post by warfacegod on 2010-01-13
Yes, I just referred to me as though I were standing next to me. I guess I'm beside myself over this.

---

### Post by libihero on 2010-01-13
^LOL
thanks tho :)

---

