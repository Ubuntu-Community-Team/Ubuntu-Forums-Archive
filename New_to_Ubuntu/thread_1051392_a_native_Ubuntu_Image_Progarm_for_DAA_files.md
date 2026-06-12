---
title: "a native Ubuntu Image Progarm for DAA files"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by manuleka on 2009-01-26
i know .daa files are PowerIso archive files and can only be run by PowerIso but i realise that AcetoneISO can also mount this file type... i looked up on the synaptic repository and couldn't find either poweriso or acetoneiso in it... can someone recommend me another Ubuntu native alternative that can mount .daa file format?

if there's no other program available i'll have to download PowerISO or AcetoneISO and install it, i'm just abit worried about their stability since they aren't in the synaptic repository

---

### Post by bwang on 2009-01-26
```

wget http://poweriso.com/poweriso-1.2.tar.gz
tar -zxvf poweriso-1.2.tar.gz
./poweriso convert image.daa -o image.iso -ot iso

```

will convert image.daa to image.iso. I think PowerISO should be stable, as it seems to be a commercial program.

---

### Post by TheLions on 2009-01-26
cdemu can mount almoust any cd/dvd image file even PowerIso ones:

[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

---

### Post by mkvnmtr on 2009-01-26
I had to download and install. I could not find anything in the repositories. It was not hard. Acetone would not install on my mac fut it will on x86.

---

### Post by manuleka on 2009-01-26
> **bwang said:**
> ```

wget http://poweriso.com/poweriso-1.2.tar.gz
tar -zxvf poweriso-1.2.tar.gz
./poweriso convert image.daa -o image.iso -ot iso

```

will convert image.daa to image.iso. I think PowerISO should be stable, as it seems to be a commercial program.

thanks guys..

latest version is poweriso-1.3.tar.gz

manage to convert .daa to .iso but wondering if i want to mount it as virtual drive, does Ubuntu have a daemon tool like program(s)?

---

### Post by mkvnmtr on 2009-01-26
I seem to remember two or three in the package manager. I don't recall the names. in the search box put in something like converting files. Until you find what works for you. You can also try just iso.

---

### Post by manuleka on 2009-01-27
manage to get hold of Furius ISO... doesn't support .DAA files tho but does for most other ISO formats

---

### Post by bulletxt on 2009-01-29
AcetoneISO :

[http://www.acetoneteam.org](http://www.acetoneteam.org)

---

### Post by espc on 2009-05-22
Ive been pullin my hair out of my head trying to open the following file:

50+ Linux Books.daa

I downloaded poweriso and tried the following command:

 ./poweriso convert /folder/file.daa -o file.iso -ot iso

can someone please explain to my noobie self how to ?

---

