---
title: "Geting java programs too run"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by cudayne on 2010-08-09
Hi I am knoew too the kde veriant of the os i usually use the gnome veriant an this is an easy too do operation. Just right click on the *.jre file tell it too open with sun java check the run as a program box an your off. 

Its a bit differnt in kbuntu I se but havnt been able too figure it out. 

I installed teh sun java by using the walk through after using the package installer failed. Though using the terminal the installer went as the walk through said.

now how do I tell the operating system too run these files as the programs they are. 

I am using kbuntu 10.04 64 bit os. any help would be apperciated.

solved me being stupid an using wrong file.

---

### Post by nebu on 2010-08-09
just run the command
```

java -jar <filename>

```

---

### Post by cudayne on 2010-08-10
there is no way too make a file too run it without going into terminal?

also this is what i get when i go too cd Desktop cd tacops an then lastly java -jar MekWarsClient.jre


The jave file is called MekWarsClient.jre

Unable to access jarfile MekWarsClient.jre

---

### Post by bprins on 2010-08-10
does it need execution rights?

chmod +x filename.jre

---

### Post by cudayne on 2010-08-10
after going too linux mint an gnome I used the same command an it opend perfectily. 

I am assuming its due too the fact that the computer isnt associating the *.jre file with java to run it. 

I looked it up an java is installed correctly on the kde side. I just need too figure out how too get the associaans right.

nuthing happend after i enterd this command  chmod +x MekWarsClient.jar

---

### Post by nebu on 2010-08-10
i have never heard of a jre file.... where did u get this from?

---

### Post by bprins on 2010-08-10
i guess he means a jar file

---

### Post by cudayne on 2010-08-10
yes the *.jar

---

### Post by sandyd on 2010-08-10
> **cudayne said:**
> Hi I am knoew too the kde veriant of the os i usually use the gnome veriant an this is an easy too do operation. Just right click on the *.jre file tell it too open with sun java check the run as a program box an your off. 

Its a bit differnt in kbuntu I se but havnt been able too figure it out. 

I installed teh sun java by using the walk through after using the package installer failed. Though using the terminal the installer went as the walk through said.

now how do I tell the operating system too run these files as the programs they are. 

I am using kbuntu 10.04 64 bit os. any help would be apperciated.
.

---

