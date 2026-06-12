---
title: "Just installed Libre Office and I have a white background ..."
date: 2011-07-22
forum: New to Ubuntu
---

### Post by hamstermoon on 2011-07-22
I have everything else (as set up in the 'input box' colour preference in appearance) a nice sky-blue colour to help with dyslexia / eyesight problems. MS Office follows that with no problem using the wine colours script I picked up on OMG Ubuntu a while back.

Libreoffice however is still giving me white backrounds to my pages (ow my eyes!) - any suggestions what I might do so it follows the system colours I set up?

---

### Post by roololing on 2011-07-22
Open LibreOffice Writer and go to **Tools > Options** and in the **LibreOffice** dropdown, select **Appearance**. Then you can change the **Document Background** color to a light blue, or whatever color you want it.

---

### Post by cybergalvez on 2011-07-22
> **roololing said:**
> Open LibreOffice Writer and go to **Tools > Options** and in the **LibreOffice** dropdown, select **Appearance**. Then you can change the **Document Background** color to a light blue, or whatever color you want it.

Thanks my Daughter has dyslexia and I have never thought of changing the background color, but that makes so much sense!

---

### Post by hamstermoon on 2011-07-23
> **roololing said:**
> Open LibreOffice Writer and go to **Tools > Options** and in the **LibreOffice** dropdown, select **Appearance**. Then you can change the **Document Background** color to a light blue, or whatever color you want it.

I thought Libreoffice was supposed to follow the Ubuntu system preferences along with all the other programs running on my computer? THEY all have blue backgrounds / boxes to fill in. This was why I started using Linux in the first place because it was possible to do that system wide.

---

### Post by hamstermoon on 2011-07-24
Replying to my own post here but I realised when I was installing Libre Office via terminal I missed out an important step. What I should have done was 

```
sudo apt-get install libreoffice libreoffice-gnome
```

because I only had the gtk and not the gnome package installed (oops!).

Now I have a nice blue background.

---

