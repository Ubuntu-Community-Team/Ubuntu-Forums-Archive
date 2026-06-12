---
title: "Updating to the latest Kernal"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Norm24 on 2009-01-29
I did this and it works fine.When I went to remove the older kernal this is what I got:

```
E: linux-image-2.6.27-9-generic: subprocess pre-removal script returned error exit status 2
```

When I click on details I get this:

---

### Post by cariboo on 2009-01-29
Go to Synaptic-->Edit-->Fix Broken PAckages. This should solve your problem.

Jim

---

### Post by Norm24 on 2009-01-29
> **cariboo907 said:**
> Go to Synaptic-->Edit-->Fix Broken PAckages. This should solve your problem.

Jim

No go Jim.Still can't remove the old kernal.I also tried removing the latest kernal and get the same error message.

Its really no big deal but I just don't see having both.

---

### Post by Norm24 on 2009-01-29
Would it make a difference if I have Grub2 installed?

---

### Post by ChildOfMana on 2009-01-29
Alternatively, if you just don't want to see a large list of kernels in your GRUB menu when you boot, you can edit your GRUB menu.lst with;

```
sudo gedit /boot/grub/menu.lst
```

Look for the line *# howmany=all* uncomment it and change it to *howmany=1*

This will then only show the latest kernel in your GRUB menu at boot time.

I appreciate this may not be what you're looking for exactly, but just a suggestion.

Dave.

---

### Post by bruce89 on 2009-01-29
*sudo rm linux-image-2.6.27-9** will force removal of the dodgy pre/post install/rm scripts that are broken.

---

### Post by Norm24 on 2009-01-29
> **ChildOfMana said:**
> Alternatively, if you just don't want to see a large list of kernels in your GRUB menu when you boot, you can edit your GRUB menu.lst with;

```
sudo gedit /boot/grub/menu.lst
```

Look for the line *# howmany=all* uncomment it and change it to *howmany=1*

This will then only show the latest kernel in your GRUB menu at boot time.

I appreciate this may not be what you're looking for exactly, but just a suggestion.

Dave.

The newest kernal isn't listed.I do appreciate the effort but one kernal is enough.

---

### Post by Norm24 on 2009-01-29
> **bruce89 said:**
> *sudo rm linux-image-2.6.27-9** will force removal of the dodgy pre/post install/rm scripts that are broken.

No go again bruce.

---

### Post by Norm24 on 2009-01-30
Any ideas guys?

---

### Post by Norm24 on 2009-01-31
I've spent a fair portion of my day trying why I can't remove one or the other.

Somebody here has to know what these error messages mean and a way to a solution.

---

### Post by Norm24 on 2009-02-04
I've let this one sit.

I can only assume there's no way to fix this?No one here can help?

---

### Post by Norm24 on 2009-02-05
Truly,there is no solution here?

---

### Post by Norm24 on 2009-02-06
Anybody?...anybody?........any?.........body?................................

---

### Post by MarblePanther on 2009-02-06
I don't really know the answer, but perhaps installing grub2 is a good idea....idk, try it?

---

