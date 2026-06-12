---
title: "Help! dumb mistake"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by TigerEar on 2010-04-09
dudes, 

I tried to under clock my hot gpu with a startup script. problem is, I think I set my clock values too low. 

now when I boot ubuntu I get the login screen for a second then everything goes black. I don't have a boot menu and i don't know how to get into safe mode to undo this stupid mistake. 

can anyone help? 

cheers. 

tiger

---

### Post by Mykk on 2010-04-09
> **TigerEar said:**
> dudes, 

I tried to under clock my hot gpu with a startup script. problem is, I think I set my clock values too low. 

now when I boot ubuntu I get the login screen for a second then everything goes black. I don't have a boot menu and i don't know how to get into safe mode to undo this stupid mistake. 

can anyone help? 

cheers. 

tiger

Have your tried changing it in your bios?

---

### Post by joao82 on 2010-04-09
Could you run a live CD and delete/edit the script?

---

### Post by TigerEar on 2010-04-09
when i try toload a live cd from the same cd I installed from yesterday I get I/o error - error reading boot cd

there aren't any options for my video card in the bios either

---

### Post by Mykk on 2010-04-09
> **TigerEar said:**
> when i try toload a live cd from the same cd I installed from yesterday I get I/o error - error reading boot cd

there aren't any options for my video card in the bios either

Have you got an on-board video card you can use?

---

### Post by TigerEar on 2010-04-09
not even a little bit

---

### Post by Mykk on 2010-04-09
> **TigerEar said:**
> not even a little bit

Im not sure if its related to the OS or the computer itself.

If its OS related, you may need to format/reinstall

If its the computer itself you could try removing the graphics card and cmos battery for a few minutes and see if that resets it. If you are going to remove the cmos battery make sure you take it out carefully and make sure it goes back in the same way it came out. Also touch a radiator to earth yourself of any static you may be holding.

---

### Post by TigerEar on 2010-04-09
Okay, I'm on Ubuntu using a Live CD (I needed to burn a new CD for some reason)

I can't change any of the values of the script or delete it - when I try to it tells me I'm not the owner and don't have permission.

Any ideas?

Cheers

---

### Post by Mykk on 2010-04-09
> **TigerEar said:**
> Okay, I'm on Ubuntu using a Live CD (I needed to burn a new CD for some reason)

I can't change any of the values of the script or delete it - when I try to it tells me I'm not the owner and don't have permission.

Any ideas?

Cheers

Ohh i thought the live cd didnt work. 

Hmmm can you run as sudo?

---

### Post by TigerEar on 2010-04-09
Fixed!

Ran nautilus as root.

If anyone else needs to delete a bad file through a Live CD, the command in terminal to open up the file browser as a superuser is:

```
sudo nautilus
```

Thanks for your help guys!

---

### Post by lisati on 2010-04-09
> **TigerEar said:**
> Fixed!

Ran nautilus as root.

If anyone else needs to delete a bad file through a Live CD, the command in terminal to open up the file browser as a superuser is:

```
sudo nautilus
```

Thanks for your help guys!

For graphical apps, gksudo is usually better:```
gksudo nautilus
```

---

