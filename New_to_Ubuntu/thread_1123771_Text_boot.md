---
title: "Text boot"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by tanha on 2009-04-12
Is there a way to have the text boot up look like knoppix does?

Thanks.

---

### Post by zvacet on 2009-04-12
Edit your grub menu list

```
sudo gedit /boot/grub/menu.lst
```

and in the line root=UUID=xxxxxxxxxxxxxxxxxxx quiet splash

remove quiet and save and close file.After that you should boot and see all the lines going down.

---

### Post by tanha on 2009-04-12
> **zvacet said:**
> Edit your grub menu list

```
sudo gedit /boot/grub/menu.lst
```

and in the line root=UUID=xxxxxxxxxxxxxxxxxxx quiet splash

remove quiet and save and close file.After that you should boot and see all the lines going down.

Yes, that part I know, thank you, but, what I meant was that I'm interested in having that text look like knoppix has its text -- with all the colours and whatnot. Right now it's just white... Do you know how to make it look like this [http://img.tomshardware.com/us/2005/01/12/windows_xp_a_goner/knoppix_boot.gif](http://img.tomshardware.com/us/2005/01/12/windows_xp_a_goner/knoppix_boot.gif) for example?

---

### Post by zvacet on 2009-04-12
Maybe [this]("http://ubuntuforums.org/showthread.php?t=1093655") is what you want.

---

