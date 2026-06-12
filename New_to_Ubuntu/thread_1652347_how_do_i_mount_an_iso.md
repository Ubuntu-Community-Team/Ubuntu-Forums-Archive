---
title: "how do i mount an iso?"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by spoonlol on 2010-12-24
any help??

---

### Post by Sef on 2010-12-24
Read [Mount ISO]("https://help.ubuntu.com/community/MountIso#Mounting%20ISO%20Files").

---

### Post by t4thfavor on 2010-12-24
I was going to say you have to buy em a drink first, but your answer seems to have much more Christmas spirit!


Welcome to the forums Spoon!

---

### Post by spoonlol on 2010-12-24
omgggggggggggggggggggg this ****ing os
zzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzzz

---

### Post by t4thfavor on 2010-12-24
That was random, did you figure out what you were trying to do, or is there something else you need help with?

---

### Post by spoonlol on 2010-12-24
srry man just rly stoned
i dled gmount iso maybe ill figure it out from here

---

### Post by spoonlol on 2010-12-24
still no luck
know any apps for doing this?

---

### Post by mikewhatever on 2010-12-24
Just right click and select 'Open with archive mounter'.

Hope you can find the right click button. ;)

---

### Post by spoonlol on 2010-12-24
> **mikewhatever said:**
> Just right click and select 'Open with archive mounter'.

Hope you can find the right click button. ;)
**** happens man

---

### Post by spoonlol on 2010-12-24
i give up
im buying windows

---

### Post by ottosykora on 2010-12-24
why dont you try gisomount ? it is in the repository

---

### Post by |Eric| on 2010-12-24
sudo mount -o rw,loop Nameoftheisofile.iso /media/somefolderyoucreated

then your files would be under /media/somefolderyoucreated

you might have to use the -t option (mount -t iso9660 ... )  or somthing like that also the archiver may be able to open it (it depense witch program is used)  

note if i remember correctly the Joliette format ( in comparison with iso9660) is not supported or limited support available under linux . 

if this fail post the output in this tread so we can be of better help

---

### Post by rburkartjo on 2010-12-25
dont give up, if you cant understand any of the answers here. do a google search on how to mount and iso. you need to burn to disk first.

---

### Post by Verbeck on 2010-12-25
1. install gmountiso from the software center
2. create  a folder on your desktop
3. open gmountiso (applications>system tools) > select the .iso  as the image file and the folder as the mount point
4. click mount

edit:
> **spoonlol said:**
> i give up
im buying windows
oh. good luck then  ):P

---

### Post by mikewhatever on 2010-12-25
> **rburkartjo said:**
> dont give up, if you cant understand any of the answers here. do a google search on how to mount and iso. you need to burn to disk first.

Really? As if Google can provide simpler answers.
... and by the way, you don't need to burn to disk first. ;)

---

