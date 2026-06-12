---
title: "Can I install fonts in Open Office??"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by sillyboy on 2009-08-04
I have free fonts I would like to install in O.O. They have an .otf extension.  Is it possible to install these or are there optional fonts for O.O.that I can install?

Thanks:)

---

### Post by mcduck on 2009-08-04
Sure, just put the fonts into .fonts (a hidden directory in your home, create it if it doesn't exist yet).

You might have to log out and back again before all programs recognize the new fonts.

---

### Post by fraser_m on 2009-08-04
Open a terminal, run:

```
mkdir ~/.fonts
mv FONTFILENAME ~/.fonts/
```

---

### Post by sillyboy on 2009-08-04
Terminal says that folder exists, but it cannot install the font I picked.  Could I have a little more info on how to install?  Please?

---

### Post by Chemical Imbalance on 2009-08-04
Just open Nautilus and press CTRL+H to show hidden folders.

Navigate to /home/username/.fonts and place your otf there.

---

### Post by sillyboy on 2009-08-04
Thanks chemical imbalance, but how do I open Nautilis.  I downloaded the Linux book, and looking quickly, found nothing in there.

Thanks

---

### Post by Chemical Imbalance on 2009-08-04
> **sillyboy said:**
> Thanks chemical imbalance, but how do I open Nautilis.  I downloaded the Linux book, and looking quickly, found nothing in there.

Thanks

Nautilus is just the name of Gnome's file manager (i.e. "Places, Home Folder".

Oh, and the Beginner's Guide is part of my signature, not my response.  :)

---

### Post by sillyboy on 2009-08-04
A thousand thanks C.I. Worked great!!

---

### Post by Chemical Imbalance on 2009-08-04
> **sillyboy said:**
> A thousand thanks C.I. Worked great!!

No problem!  Always glad to help.

---

### Post by rraj.be on 2009-08-04
Go to 

Places --> Home 

in your main menu

Or if you want to open with root privileges then press Alt + F2 and type
```

sudo nautilus 
```

---

### Post by mringer on 2009-11-01
> **mcduck said:**
> Sure, just put the fonts into .fonts (a hidden directory in your home, create it if it doesn't exist yet).

You might have to log out and back again before all programs recognize the new fonts.

Please, where should I install the fonts to make them available to all users? Thank you.

---

