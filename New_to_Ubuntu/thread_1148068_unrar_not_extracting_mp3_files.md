---
title: "unrar not extracting mp3 files"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by abben on 2009-05-04
trying to move my music to this fresh xfce install, and having some never-before seen unrar problems. Observe:

```
[me]@[computer]:~/downloads$ unrar x Job\ For\ A\ Cowboy\ -\ 2007\ -\ Genesis_by_74261700027_\[metalarea.org\].rar 

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/abben/downloads/Job For A Cowboy - 2007 - Genesis_by_74261700027_[metalarea.org].rar

Extracting  Job For A Cowboy/2007 - Genesis/#dummy.mp3                Failed    
Extracting  Job For A Cowboy/2007 - Genesis/01. Bearing the Serpent's Lamb.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/02. Reduced to Mere Filth.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/03. Altered From Catechization.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/04. Upheaval.mp3          Failed    
Extracting  Job For A Cowboy/2007 - Genesis/05. Embedded.mp3          Failed    
Extracting  Job For A Cowboy/2007 - Genesis/06. Strings of Hypocrisy.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/07. Martyrdom Unsealed.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/08. Blasphemy.mp3         Failed    
Extracting  Job For A Cowboy/2007 - Genesis/09. The Divine Falsehood.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/10. Coalescing Prophecy.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/Job For A Cowboy - Genesis (2007).jpg OK        
Extracting  Job For A Cowboy/2007 - Genesis/Thumbs.db          
```

Thankfully, it decided I deserved to see the jpg file. This has happened for various rar files, I'm pretty sure there is no corrupt archive issue. Has anyone seen anything like this before?

---

### Post by nhasian on 2009-05-04
when i type unrar mine says:

```
UNRAR 3.80 freeware      Copyright (c) 1993-2008 Alexander Roshal

```

make sure you are using the package called unrar and not unrar-free

```
sudo apt-get remove unrar-free && sudo apt-get install unrar
```

---

### Post by colau on 2009-08-15
> **abben said:**
> trying to move my music to this fresh xfce install, and having some never-before seen unrar problems. Observe:

```
[me]@[computer]:~/downloads$ unrar x Job\ For\ A\ Cowboy\ -\ 2007\ -\ Genesis_by_74261700027_\[metalarea.org\].rar 

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/abben/downloads/Job For A Cowboy - 2007 - Genesis_by_74261700027_[metalarea.org].rar

Extracting  Job For A Cowboy/2007 - Genesis/#dummy.mp3                Failed    
Extracting  Job For A Cowboy/2007 - Genesis/01. Bearing the Serpent's Lamb.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/02. Reduced to Mere Filth.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/03. Altered From Catechization.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/04. Upheaval.mp3          Failed    
Extracting  Job For A Cowboy/2007 - Genesis/05. Embedded.mp3          Failed    
Extracting  Job For A Cowboy/2007 - Genesis/06. Strings of Hypocrisy.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/07. Martyrdom Unsealed.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/08. Blasphemy.mp3         Failed    
Extracting  Job For A Cowboy/2007 - Genesis/09. The Divine Falsehood.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/10. Coalescing Prophecy.mp3 Failed    
Extracting  Job For A Cowboy/2007 - Genesis/Job For A Cowboy - Genesis (2007).jpg OK        
Extracting  Job For A Cowboy/2007 - Genesis/Thumbs.db          
```

Thankfully, it decided I deserved to see the jpg file. This has happened for various rar files, I'm pretty sure there is no corrupt archive issue. Has anyone seen anything like this before?

Can you post:
```

dpkg -l | grep unrar

```

---

### Post by leogagliardi on 2009-10-30
unrar needs rar
First install rar

/sudo apt-get install rar

then (if you didn't erase unrar) try to unrar a file normally

---

### Post by Zakhafr on 2011-06-06
unrar-free is also awfully bugged when you have archive names or filenames in archives having non-ascii-7 characters such as:

Archive_Téléchargée.part01.rar
[
  => Film_à_la_télé.mkv
]

With such files, even if you rename them with ascii-7 letters, unrar-free will stop with unhelpful messages such as: 'failed'

... whereas unrar-nonfree works like a charm.

Conclusion, the unrar-free is really really so bad and obsolete, don't loose your time with that (unfortunately for freedom's sake)

---

