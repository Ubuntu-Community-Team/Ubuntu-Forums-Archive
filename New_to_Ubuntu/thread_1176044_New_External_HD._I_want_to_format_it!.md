---
title: "New External HD. I want to format it!"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by piousp on 2009-06-01
Hi again folks!
I bought a WD 1TB external HD recently. So, to my surprise, the FS is fat32 and i really dont want to have fat32 to handle my important files. Anyway, i tried to format it using JFS first (with gparted... well, its kde counterpart) and it finished alright. So, i was eager to start using the HD, but i noticed something weird: I was unable to create a directory!!! "What the heck" I thought. Oh well, i'll just format it again. So, this time used XFS instead of JFS; same result. 3rd formatting,this time with good 'ol EXT3... but same result! I could not create a single directory!! Let alone copy/move files into it! Somehow, i check the file mode bits (user permissions) and there was my problem: they are only accesible for the owner and his group. So, how's that a problem you say? Well, to use gparted, you gotta open it with sudo privilegies, so, of course, the owner this time is.... SUDO! YAY! :KS :lolflag:

So, my question is: "How can i format my HD so i can use it like a pendrive??" Or is it a mount option?? As you can see, i'm kinda confused here. Just in case, i let my DE mount the HD as soon as I plug it (since it uses an usb connection).

Any ideas??? Thanks in advance!

---

### Post by MichaelSammels on 2009-06-01
Run this from the terminal:

```
sudo gparted
```

Also noticed the permission problems:

```
sudo pysdm
```

Allows you to edit your drive privelages/mounts, etc.

---

### Post by piousp on 2009-06-01
Thanks!!! Right now i'm checking [pySDM]("http://pysdm.sourceforge.net/"). I hope i dont have to download all the gtk packages! ^_^
*-Edit*
And i didn't have to:

```

piousp@QVANTVM:~$ sudo apt-get install pysdm                                             
Leyendo lista de paquetes... Hecho                                                       
Creando árbol de dependencias                                                            
Leyendo la información de estado... Hecho                                                
Se instalarán los siguientes paquetes extras:                                            
  gksu libgksu2-0 libgtop2-7 libgtop2-common python-cairo python-glade2 python-gtk2      
Paquetes sugeridos:                                                                      
  python-gtk2-doc python-numpy                                                           
Se instalarán los siguientes paquetes NUEVOS:                                            
  gksu libgksu2-0 libgtop2-7 libgtop2-common pysdm python-cairo python-glade2 python-gtk2
0 actualizados, 8 se instalarán, 0 para eliminar y 5 no actualizados.                    
Necesito descargar 2009kB de archivos. 

```

---

### Post by MichaelSammels on 2009-06-01
You shouldn't do, most of them come with Ubuntu. :) Glad I could help you.

---

### Post by piousp on 2009-06-01
But i use KDE ;)
I guess i must read pySDM manual.... i just tried and now i cant even mount it!!! :lolflag: :sigh
Well, back "to the drawing board" i guess.

---

### Post by MichaelSammels on 2009-06-01
Wow... erm, if it's formatted, make sure you run pysdm as root and click "mount". If you click options, check all the boxes which say stuff like "any user can mount", and uncheck "mount as read only"

---

