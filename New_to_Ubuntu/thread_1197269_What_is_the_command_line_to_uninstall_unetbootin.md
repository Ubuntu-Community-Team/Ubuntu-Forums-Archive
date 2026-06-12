---
title: "What is the command line to uninstall unetbootin?"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by tpgames on 2009-06-25
The Real Question: I know sudo means root. But, what is the full command I use to uninstall unetbootin on a soft harddrive installation? (And no, don't give me their uninformative site that doesn't give me the command line. Thanks!) Can I uninstall it using terminal? That is what I'd like to do if I get the full command line. :)  If not, then how to I get into root mode without using terminal? 

I did a soft live 9.04  install of unetbootin to my harddrive to see if I could get sound working but I lacked space. This was a last ditch attempt to see if I have sound drivers that are damaged or if I configured something wrong. :(

---

### Post by Bachstelze on 2009-06-25
How did you install that program?

---

### Post by colau on 2009-08-31
> **tpgames said:**
> The Real Question: I know sudo means root. But, what is the full command I use to uninstall unetbootin on a soft harddrive installation? (And no, don't give me their uninformative site that doesn't give me the command line. Thanks!) Can I uninstall it using terminal? That is what I'd like to do if I get the full command line. :)  If not, then how to I get into root mode without using terminal? 

I did a soft live 9.04  install of unetbootin to my harddrive to see if I could get sound working but I lacked space. This was a last ditch attempt to see if I have sound drivers that are damaged or if I configured something wrong. :(
```

sudo aptitude remove unetbootin

```

---

### Post by Cheezespread on 2009-08-31
> **colau said:**
> ```

sudo aptitude remove unetbootin

```

As "HymnToLife" mentioned , dont we need to know how he installed it ?. If he had installed it using apt-get or Synaptic , I believe you can't remove the dependencies with aptitude.

---

### Post by colau on 2009-08-31
```

sudo apt-get autoremoe unetbootin

```

---

### Post by nhasian on 2009-08-31
isnt unetbootin just an executeable you download from their website?  if so then just delete the file.  thats all there is to it.  I think it is recommended that pk7zip be installed as well so you would need to manually remove that with:

```
sudo apt-get remove p7zip
```

---

### Post by colau on 2009-08-31
> **nhasian said:**
> isnt unetbootin just an executeable you download from their website?  if so then just delete the file.  thats all there is to it.  I think it is recommended that **[COLOR="Red"]pk7zip[/COLOR]** be installed as well so you would need to manually remove that with:

```
sudo apt-get remove p7zip
```
Typo: **[COLOR="Red"]pk7zip[/COLOR]**

---

