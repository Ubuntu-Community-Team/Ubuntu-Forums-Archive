---
title: "Copy files in subdirectories without directory tree.. Just the Files.."
date: 2009-01-21
forum: New to Ubuntu
---

### Post by @B6Mwu8fN9M on 2009-01-21
What happened is that I downloaded many fonts. They came in the form of .zip. I unzipped everything and now I have some ttf files that are in no directory and some are in subdirectories. I want to copy them all at once to ~/.fonts using the terminal. Putting directories in ~/.fonts is not useful because the fonts are not detected if in subdirectories. Does anyone know what I have to do?


Thanks in advance.:)

---

### Post by yeats on 2009-01-21
In the terminal, go to the directory where the fonts are and do 

```
cp *.ttf ~/.fonts
```

---

### Post by b0b138 on 2009-01-21
That command won't copy anything in subdirectories.

However, fonts that are in your ~/.fonts or /usr/share/fonts should be found through subfolders. After you copy them there you have to update the font cache. ```
sudo fc-cache -f -v
```

---

### Post by sisco311 on 2009-01-21
<EDIT>: b0b138's solution should work.

</EDIT>

```
find /path/to/fonts -type f -name "*.ttf" -exec cp {} ~/.fonts \;
```

---

### Post by @B6Mwu8fN9M on 2009-01-21
Thanks! It seems that copying the folders into ~/.fonts worked. It didn't work when I tried it with different fonts a while ago but now it worked. 


Thanks.

---

