---
title: "Copy a Folder Structure, no files..."
date: 2009-03-26
forum: New to Ubuntu
---

### Post by cfree220 on 2009-03-26
Is there a way that I can copy a folder structure without copying any of the files inside of it?

For example, if I have a directory:
~/Music/1flac/A\ Whole\ Bunch\ of\ Artists/Those\ Artists\ Albums/
and I want to move those folders to:
~/Music/1wav/A\ Whole\ Bunch\ of\ Artists/Those\ Artists\ Albums/

Can I do that?

Also, if I wanted to then move files from the source folders into those directories (only certain file types), could I do something like:

```

cd ~/Music/1flac/
sudo mv ./*/*/*.wav ../1wav/*/*/

```
And have it copy the only those .wav files into the correct directories?

---

### Post by ibuclaw on 2009-03-26
1) for copying a directory structure...

More or less, this is how it is done.
```
cd **olddir/** && find . -type d -exec mkdir ../**newdir/**{} \;
```

2) for certain file types... you would use **find** again
```
cd **olddir/** && find . -type f -iname "*.wav" -exec cp {} ../**newdir/**{} \;
```

Regards
Iain

---

### Post by cfree220 on 2009-03-26
Thanks for the quick response!

Just out of curiosity, does anything go inside the {brackets}?

---

### Post by lloyd_b on 2009-03-26
> **cfree220 said:**
> Thanks for the quick response!

Just out of curiosity, does anything go inside the {brackets}?

Nope.  They are a place holder that are dynamically replaced with an actual directory/file name.  The "find" command will execute the command following "-exec" for each directory/file it finds, substituting the actual directory/file name for the "{}".

Lloyd B.

---

