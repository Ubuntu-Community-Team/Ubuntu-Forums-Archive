---
title: "i cant rename or delete some files after a failed copy"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by kiraku on 2010-05-09
**hi:**

i have an external hd of 500 Gb and the other day i was copying some files on it when suddenly stoped for some error..

now, there are some files with extrange character, other ones disappear and i cant eliminate them because they doesnt exist and i cant rename those with the extrange characters or either eliminate those who remain...

this is what i get:

[B]kira@death-note:/media/Iomega HDD/anime/Hanamaru Youchien$ ls
ls: no se puede acceder a [Ctrl-Znf]_Hanamaru Youchien_04.mp4: No existe el fichero ó directorio
ls: no se puede acceder a [Ctrl-Znf]_Hanamaru Youchien_05.mp4: No existe el fichero ó directorio
ls: no se puede acceder a [Ctrl-Znf]_Hanamaru Youchien_06.mp4: No existe el fichero ó directorio
ls: no se puede acceder a [Ctrl-Znf]_Hanamaru Youchien_07.mp4: No existe el fichero ó directorio
ls: no se puede acceder a [Ctrl-Znf]_Hanamaru Youchien_08.mp4: No existe el fichero ó directorio
[Ctrl-Znf]_Hanamaru Youchien_01.mp4  [Ctrl-Znf]_Hanamaru Youchien_04.mp4  [Ctrl-Znf]_Hanamaru Youchien_06.mp4  [Ctrl-Znf]_Hanamaru Youchien_08.mp4
[Ctrl-Znf]_Hanamaru Youchien_02.mp4  [Ctrl-Znf]_Hanamaru Youchien_05.mp4  [Ctrl-Znf]_Hanamaru Youchien_07.mp4 [COLOR=Red][Ctrl-Znf]_Hanamaru Youchien_0&#9821;.mp4[/COLOR][/B]

the red file is the one ther with the extrange character...

when i try to erase them...

[B]kira@death-note:/media/Iomega HDD/anime/Hanamaru Youchien$ rm *
rm: no se puede borrar «[Ctrl-Znf]_Hanamaru Youchien_01.mp4»: Error de entrada/salida
rm: no se puede borrar «[Ctrl-Znf]_Hanamaru Youchien_02.mp4»: Error de entrada/salida
rm: no se puede borrar «[Ctrl-Znf]_Hanamaru Youchien_04.mp4»: No existe el fichero ó directorio
rm: no se puede borrar «[Ctrl-Znf]_Hanamaru Youchien_05.mp4»: No existe el fichero ó directorio
rm: no se puede borrar «[Ctrl-Znf]_Hanamaru Youchien_06.mp4»: No existe el fichero ó directorio
rm: no se puede borrar «[Ctrl-Znf]_Hanamaru Youchien_07.mp4»: No existe el fichero ó directorio
rm: no se puede borrar «[Ctrl-Znf]_Hanamaru Youchien_08.mp4»: No existe el fichero ó directorio
rm: no se puede borrar «[Ctrl-Znf]_Hanamaru Youchien_0&#9821;.mp4»: No existe el fichero ó directorio[/B]

in this directory i get the same...

[B]kira@death-note:/media/Iomega HDD/anime/Saint Seiya The Lost Canvas$ ls
ls: no se puede acceder a [JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 05 - Rosas Venenosas [BDRip][720p].mp4: No existe el fichero ó directorio
ls: no se puede acceder a [JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 07 - Frutos del Mokurenji [BDRip][720p].mp4: No existe el fichero ó directorio
ls: no se puede acceder a [JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 08 - Un Dia Agradable [BDRip][720p].mp4: No existe el fichero ó directorio
ls: no se puede acceder a [JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 09 - Gran Estrella [BDRip][720p].mp4: No existe el fichero ó directorio
ls: no se puede acceder a [JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 10 - Advenimiento [BDRip][720p].mp4: No existe el fichero ó directorio
ls: no se puede acceder a [JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 11 - Tan Inalcanzable [BDRip][720p].mp4: No existe el fichero ó directorio
ls: no se puede acceder a [JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 12 - Un Sacrificio Perdurable [BDRip][720p].mp4: No existe el fichero ó directorio
[COLOR=Red][JPU] Sain&#61922;  Seiya - The Lost Canvas Meiou Shinwa - Ova 06 - Rosas Fúnebres [BDRip][720p].mp4[/COLOR]
[JPU] Saint Seiya - The Lost Canva? Meiou Shinwa - Ova 04 - Guirnalda de Oraciones [BDRip][720p].mp4
[JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - 01 [BDRip][720p].mp4
[COLOR=Red] [JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 02 - El Despert&#61922; r de hades [BDRip][720p].mp4[/COLOR]
[JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 03 - El Comienzo de la Guerra Santa [BDRip][720p].mp4
[JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 05 - Rosas Venenosas [BDRip][720p].mp4
[JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 07 - Frutos del Mokurenji [BDRip][720p].mp4
[JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 08 - Un Dia Agradable [BDRip][720p].mp4
[JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 09 - Gran Estrella [BDRip][720p].mp4
[JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 10 - Advenimiento [BDRip][720p].mp4
[JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 11 - Tan Inalcanzable [BDRip][720p].mp4
[JPU] Saint Seiya - The Lost Canvas Meiou Shinwa - Ova 12 - Un Sacrificio Perdurable [BDRip][720p].mp4
[/B] 
so, anyone have an idea of what happen or what can i do to recover the lost files o how to erase the files at least??

---

### Post by kellemes on 2010-05-09
Hi there,
  I remember having this issue some years ago..
I believe I fixed it by adding "iocharset=utf8" to the mountline in /etc/fstab

So now I mount one of my nas-drives like so..
```
//nasdrive /mnt/nasdrive cifs user, uid=1000, iocharset=utf8, rw, suid, credentials=filename  0  0
```

This fixed it for me..

Old [bugreport]("https://bugs.launchpad.net/ubuntu/+bug/200595").

---

### Post by quadproc on 2010-05-09
> **kiraku said:**
> **hi:**
...
now, there are some files with extrange character, other ones disappear and i cant eliminate them because they doesnt exist and i cant rename those with the extrange characters or either eliminate those who remain...
...
so, anyone have an idea of what happen or what can i do to recover the lost files o how to erase the files at least??
First thought: try using the graphical application called "Places" at the top of your screen.  When you navigate to the file of interest then you may be able to rename it or move it to trash by right clicking on it and selecting the desired action.

If you want to do it using a command line then you could change to the directory which contains the problem files, rm -i * and answer whether you want the file removed for each file in the directory.  If you just say y to the ones with problems then they will be removed.

Another thing that might work is to highlight the name of the offending file and then mv it to some new name.

quadproc

---

### Post by kiraku on 2010-05-21
hi:

i try both suggestion and thei didnt work...

any other ideas??

---

