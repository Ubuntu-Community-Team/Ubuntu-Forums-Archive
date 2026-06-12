---
title: "New problem- can install but..."
date: 2010-05-27
forum: New to Ubuntu
---

### Post by Mezzoberanen on 2010-05-27
So I finally got it installed by selecting nomode on the install screen, but as soon as I try to start it up properly it goes back to the same issue (monitor goes to sleep because it's not getting any input from the pc). Can I force a start-up to go nomode by chance, or is there another trick?

I have a feeling it has something to do with the onboard graphics (which are nvidia) talking to kubuntu/ubuntu but I don't know how exactly to fix.

---

### Post by Catharsis on 2010-05-27
Hold down Shift while booting to get the grub menu. Press 'e' and replace "quiet splash" with "nomodeset". Ctrl+x to boot. Then install your nVidia driver through System->Administration->Hardware Drivers.

---

### Post by Gone fishing on 2010-05-27
> monitor goes to sleep because it's not getting any input from the pc

Or it's using a resolution,frequency? that your monitor does not support. Is this an old monitor? have you tried another?

---

### Post by Mezzoberanen on 2010-05-27
> **Gone fishing said:**
> Or it's using a resolution,frequency? that your monitor does not support. Is this an old monitor? have you tried another?
.
It's an older monitor so possibly. I can try another, but all I have around are CRTs.

---

### Post by Mezzoberanen on 2010-05-27
> **Catharsis said:**
> Hold down Shift while booting to get the grub menu. Press 'e' and replace "quiet splash" with "nomodeset". Ctrl+x to boot. Then install your nVidia driver through System->Administration->Hardware Drivers.  

I'll try this too thanks.

This is the one that worked- THANKS!!!!!

---

