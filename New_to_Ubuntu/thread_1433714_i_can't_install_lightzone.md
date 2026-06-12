---
title: "i can't install lightzone"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by myrnamynkoff on 2010-03-19
Hi.... I'm new over here and this is the first time that I try to install something without using Ubuntu Software center. So this is what happened and i really don't understand what I should do..

I downloaded LightZone... and the installation read-me document says: 
Open terminal as ROOT in this folder :
                 ====

tar xzvf LightZone-3.5.tar.gz -C /opt
cd /opt/LightZone
sh LightZone


SO... i opened the terminal as root.. and i typed.... tar xzvf LightZone-3.5.tar.gz -C /opt
and the terminal replied: tar:
 LightZone-3.5.tar.gz: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Saliendo con fallos debido a errores anteriores

(translation: can't open: file or dir doesn't exist
the error can't be recovered: exit now
child returned status 2
exit with failure due to previous error)

:(

can you help me? what am i doing wrong?

thank you thank you thank you..

---

### Post by sandyd on 2010-03-19
> **myrnamynkoff said:**
> Hi.... I'm new over here and this is the first time that I try to install something without using Ubuntu Software center. So this is what happened and i really don't understand what I should do..

I downloaded LightZone... and the installation read-me document says: 
Open terminal as ROOT in this folder :
                 ====

tar xzvf LightZone-3.5.tar.gz -C /opt
cd /opt/LightZone
sh LightZone


SO... i opened the terminal as root.. and i typed.... tar xzvf LightZone-3.5.tar.gz -C /opt
and the terminal replied: tar:
 LightZone-3.5.tar.gz: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Saliendo con fallos debido a errores anteriores

(translation: can't open: file or dir doesn't exist
the error can't be recovered: exit now
child returned status 2
exit with failure due to previous error)

:(

can you help me? what am i doing wrong?

thank you thank you thank you..
where did you ave the file to?

---

### Post by 2hot6ft2 on 2010-03-19
Move the file to your home folder and try again.
Places > Home Folder

---

### Post by Penguin Guy on 2010-03-19
You will need to naviagte the directory the LightZone archive is in using [FONT="Courier New"]cd /path/to/archive[/FONT] before you use the [FONT="Courier New"]tar[/FONT] command.

---

### Post by myrnamynkoff on 2010-03-19
mmm.... what's 'ave'? :/

i downloaded the file from a torrent (yes..) and then i put it in the folder 'documents', and from there it is that i'm trying to install it :S

---

### Post by 2hot6ft2 on 2010-03-19
> **myrnamynkoff said:**
> mmm.... what's 'ave'? :/

i downloaded the file from a torrent (yes..) and then i put it in the folder 'documents', and from there it is that i'm trying to install it :S
When you open a terminal it opens in /home/<yourusername>/
by default so use
```
cd Documents
```
then you will be in the Documents folder where the file is.

---

### Post by myrnamynkoff on 2010-03-19
thank you so much for answering, i still can't find the solution though.... i tried changing the file to the home folder, still same answer from the terminal... then i tried cd path/to/archive, and same answer: file or dir doesn't exist. 
Finally i tried to go to the folder myself as I know it is on the home folder so I tried cd home/myrna and i got in there but i don't know the command here for dir /p on this terminal. for some reason almost everything i try to type in there answers back 'file or dir doesn't exit', is that normal because I'm an ubuntu ignorant or there's something wrong?

thanks again for helping me :)

---

### Post by myrnamynkoff on 2010-03-19
_just for you to know:_ I took the program back to the documents folder. i tried installing but it still gives the original answer. (tar: LightZone-3.5.tar.gz: No se puede open: No existe el fichero ó directorio
tar: El error no es recuperable: salida ahora
tar: Child returned status 2
tar: Saliendo con fallos debido a errores anteriores)

the folder that i downloaded is called LightZone 3.5(9420) for Linux. Inside of it, there's a file INSTALLATION.txt with the following installation steps:  

Open terminal as ROOT in this folder :
                 ====
tar xzvf LightZone-3.5.tar.gz -C /opt
cd /opt/LightZone
sh LightZone

and then also a folder called LightZone-3.5.tar.gz

question:
what is **-C **on the command to the terminal? 
i tried tar --help and it didn't say so.

anyways... thank you again :) :)

---

### Post by 2hot6ft2 on 2010-03-19
The command to list the contents of the folder that you are in is
```
ls
```
That's a lower case LS
and to run as root start the command with "sudo"
type your password in when prompted, it wont be displayed just type it in and hit enter.
>      -C, --directory DIR
           change to directory DIR
Try
```
man <applicationsname>
```

---

### Post by myrnamynkoff on 2010-03-19
it's there! but i still can't install it :(

i'm pasting what i got 

root@noelia-laptop:~# cd /home/myrna/Documentos
root@noelia-laptop:~/Documentos# ls
bakery menu
LightZone 3.5(9420) for Linux
The Complete Book of Self Sufficiency by John Seymour
root@noelia-laptop:~/Documentos# ^C
root@noelia-laptop:~/Documentos#

---

### Post by 2hot6ft2 on 2010-03-19
> **myrnamynkoff said:**
> 
and then also a folder called LightZone-3.5.tar.gz

That may be the problem, get rid of the folder so just the archive is there. It should have said something like LightZone-3.5.tar.gz is not an archive if that's the case though.

---

### Post by 2hot6ft2 on 2010-03-19
Maybe this will help.
[[SOLVED] install lightzone]("http://ubuntuforums.org/showthread.php?t=1037136")

---

### Post by myrnamynkoff on 2010-03-19
YEY! that was it! i'm using the program right now!!!

thank youu so much 2hot6ft2!

love health and happiness for you! :D

---

### Post by 2hot6ft2 on 2010-03-19
> **myrnamynkoff said:**
> YEY! that was it! i'm using the program right now!!!

thank youu so much 2hot6ft2!

love health and happiness for you! :D
Glad to hear it, you're welcome and enjoy.

---

