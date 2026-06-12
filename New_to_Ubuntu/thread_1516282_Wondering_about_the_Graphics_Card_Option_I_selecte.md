---
title: "Wondering about the Graphics Card Option I selected"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by Andavane on 2010-06-23
Yesterday I installed 10.04 on my Sony Vaio VGN-S3HP.
During the installation there was (I think) a question about which Graphics or Video card option I wanted.

It was set on some option but I changed that to another one which said "Recommended". Now when I boot up the PC I am getting green flickerings, and when I open an Open Office File I get smudgy menus (us seen in screen shot below).

So I am wondering if I should just have continued without changing thw graphics to recommended, and if I can change it now.

I have looked in the NVidia X Server settings and can't see anything there which could be changed.

I'd be grateful for suggestions, as smudgy Open Open is tricky to interpret!

Regards

John

---

### Post by -humanaut- on 2010-06-23
Hit alt+f2 and type gksu gtk-jockey and see if your "current" is selected another possibility depending on your card (6*** + series) You could add the xswat-xorg repo and get the current driver (256.**) which has worked excellent on my card.

---

### Post by Andavane on 2010-06-26
> **-humanaut- said:**
> Hit alt+f2 and type gksu gtk-jockey and see if your "current" is selected another possibility depending on your card (6*** + series) You could add the xswat-xorg repo and get the current driver (256.**) which has worked excellent on my card.

Thank you
When I do that, I get the following:

---

### Post by sandyd on 2010-06-26
> **Andavane said:**
> Thank you
When I do that, I get the following:
go to system -> administration -> hardwaredrivers

---

### Post by Andavane on 2010-06-27
> **carlee said:**
> go to system -> administration -> hardwaredrivers

Thanks.
I'm very at sea with hardware drivers as it reminds me of Windows - if I clicked the wrong thing, nothing would work.

I hope this doesn't happen here.
Here's what I get:

---

### Post by sandyd on 2010-06-28
> **Andavane said:**
> Thanks.
I'm very at sea with hardware drivers as it reminds me of Windows - if I clicked the wrong thing, nothing would work.

I hope this doesn't happen here.
Here's what I get:
Your currently using the latest version of the nvidia drivers.
Try deactivating them, and installing the nvidia drivers from nvidia.com instead

---

### Post by philinux on 2010-06-28
It would help if we new which nVidia card is in the machines. Unless we assume it's this one.

# NVIDIA GeForce Go 6200 128MB dedicated graphics

---

