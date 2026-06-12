---
title: "Trying to install a &quot;.run&quot; file."
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Captain Legless on 2009-01-30
I'm trying to install "Wolfenstein: Enemy Territory" which is a ".run" file.

I've searched through Google and various forums to work out hos it should be done but have had no luck.

I've tried right clicking on it and going to the "*permissions*" tab and ticking the "*Allow executing file as a progra*m" box then double clicking it and going through the terminal window. This hangs up part way through giving me the message that I don't have *write permissions* for the chosen installation path.:confused:

I've also tried ```
sudo chmod 777 et-linux-2.60.x86.run && ./et-linux-2.60.x86.run
```  in a terminal screen but this just returns the message:- ```
chmod: cannot access `et-linux-2.60.x86.run': No such file or directory
```

What's the secret to installing it then?:???:

---

### Post by sisco311 on 2009-01-30
> **Captain Legless said:**
> I'm trying to install "Wolfenstein: Enemy Territory" which is a ".run" file.

I've searched through Google and various forums to work out hos it should be done but have had no luck.

I've tried right clicking on it and going to the "*permissions*" tab and ticking the "*Allow executing file as a progra*m" box then double clicking it and going through the terminal window. This hangs up part way through giving me the message that I don't have *write permissions* for the chosen installation path.:confused:

I've also tried ```
sudo chmod 777 et-linux-2.60.x86.run && ./et-linux-2.60.x86.run
```  in a terminal screen but this just returns the message:- ```
chmod: cannot access `et-linux-2.60.x86.run': No such file or directory
```

What's the secret to installing it then?:???:

Type "sudo" then a space in the terminal. Drag and drop the .run file in the terminal window and press Enter. Type your password and press Enter again.

[uhelp]community/UsingTheTerminal[/uhelp]

---

### Post by PointyWombat on 2009-01-30
from the cli, try just 'sh et-linux-2.60.x86.run'

---

### Post by 3rdalbum on 2009-01-30
> **PointyWombat said:**
> from the cli, try just 'sh et-linux-2.60.x86.run'

The installer needs to be run as root. This won't work unless you put "sudo" in front of it.

---

### Post by Captain Legless on 2009-01-30
Thanks guys for the ideas but after much messing and fumbling I accidentally found that the following worked:-

```
/home/myname/Desktop/et-linux-2.60.x86.run
```

Probably because the run file was sitting on my desktop!!

Having got the thing installed it now looks like my graphics card can't handle it!!!!!!!!  ](*,)

---

