---
title: "how to register .reg files?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by ayastona on 2009-04-18
in windows i just double click the .reg file and it automatically does what it has to do..

how do i accomplish the same thing in linux? im using wine to open the program..

---

### Post by supersonicdarky on 2009-04-18
run **wine regedit**, then import the key there

---

### Post by ayastona on 2009-04-18
i tried that it doesnt work

---

### Post by linuxuser21 on 2009-04-18
You can also right-click it > Open With Other Program > Wine Windows Loader.

---

### Post by ayastona on 2009-04-18
it didnt work..

---

### Post by alfplayer on 2009-04-18
Have you seen this: [http://ubuntuforums.org/showthread.php?t=885182](http://ubuntuforums.org/showthread.php?t=885182)

---

### Post by ayastona on 2009-04-18
that didn't work either, apparently...

---

### Post by hesjnet on 2009-04-18
How familiar are you with the terminal? It needs to be in the same directory as the file or else you have to spell the entire path

```
wine regedit /home/YOURUSERNAME/Desktop/registerfile.reg
```

Remember that it is case sEnSiTivE. :popcorn:

---

### Post by doas777 on 2009-04-18
do you have execute permission on the file? not sure if you need it or not

---

### Post by ayastona on 2009-04-18
im pretty familiar with terminal/console.. i was in the correct directory.. if there was an error i would have let you known that...
i know its case sensitive...

also, no permissions necessary.. its already taken care of..

when i run any of the suggested remedies given above.. it seems like there is no error and that it "did wat it was supposed to" but the affect hasn't taken place...

i even tried reinstalling the program in question into its default folder (i was using my own specified folder before so i uninstalled that first and then reinstalled into default directory)

---

### Post by Bölvaður on 2009-04-18
this is all probably very silly but you can just do it this way.
type into the terminal

```
nautilus ~/.wine/dosdevices/c:/windows
```

and double click regedit.exe

the reason I will not make the terminal command open regedit is for you to understand where important programs are stored ;) have a look around there.

After you have opened the program click **Registry** and then **Import registry file**

---

### Post by linuxuser21 on 2009-04-19
If none of these work, there might be something wrong with it.  What is happening that is makes you believe it's not working properly?

---

### Post by anjilslaire on 2009-04-19
If all else fails, .reg files are simply text files fill the registry keys affected inside. 
Open the .reg with notepad or gedit, and manually add the relevant registry keys/values to the registry via regedit.

---

