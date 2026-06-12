---
title: "Changing permissions for the directory ttf-telugu-fonts"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by bharanik on 2009-06-26
Hi All, 

Kindly help me to install some specific Telugu fonts
I tried to move the fonts which I have downloaded from the Internet in the location...

usr/share/fonts/truetype/ttf-telugu-fonts.. 

However, when I move the specific fonts.. system is prompting that I dont have permission to move the file.

Hence, Kindly help me to install the fonts or help me to change the permissions of the directory..

Thanks in Advance.

---

### Post by ibizatunes on 2009-06-26
go to the command line and type 
```
sudo mv usr/share/fonts/truetype/ttf-telugu-font THE LOCATION YOU WANT!!
```

OR if you want to use a GUI type

alt + f2 and then type  

```
sudo nautilus
```

Are you trying to install restricted forts

go to the termial
and type 
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Ru$$i@N on 2009-06-26
> **ibizatunes said:**
> go to the command line and type 
```
sudo mv usr/share/fonts/truetype/ttf-telugu-font THE LOCATION YOU WANT!!
```


there seems to be an error.
```
sudo mv /path/to/source /path/to/destination
```
sudo - gives you root privileges (it will ask you for a password)
mv - the move command
and the paths are self-explanatory, so the source is where your fonts are, the destination is where you want to put them to.

---

