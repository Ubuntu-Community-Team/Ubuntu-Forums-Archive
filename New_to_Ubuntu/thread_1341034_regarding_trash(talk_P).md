---
title: "regarding trash(talk :P)"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by abhigyan91 on 2009-11-29
hey every1.. sry for the cheezy subject :P
i wanted to know a command for emptying trash from terminal. i came across
```
rm -rf ~/.Trash/*
```

i tried it.. it didnt show an error however it dindt work...as in i checkd the trash folder from natilus and it was not empty

i double checkd if a hidden folder call .Trash exists in my home folder... it doesnt exist(!)

i did a bit of googling and found this file in my home folder:
> 
~/.local/share/Trash/files


i tried deleting the contents of this folder... surprise surprise. the deleted files came back!!!!!!!!

i then opened the Trash folder in nautilus(from the list of links on the left)in a new tab.. deleted files from
 > 
~/.local/share/Trash/files

and quickly cheked the other Trash tab.. the files were still there!! then i went back to the ".local...files" folder(all this happend in a duration of about 2 secs).. the deleted files came back..

what on earth is happening here??

i think i read somewhere that the rm -rf code given above works but not immediately.. is this true? how can u rm somthing from a folder which doesn't exist???

i kno this is all kinda useless since i can always empty trash from the icon in the bottom rite corner and be done with it.. neverthless.. plz help me out:P

(im using avant window manager so i dont have the bottom panel.. hence no trash icon... so u can c how all this strted..)

---

### Post by abhigyan91 on 2009-11-29
also.. i have two internal drives on my comp.. 1 is the main ext4 drive with 9.10.. another one with ntfs.. when i delete files from the ext4 drive.. it goes in the trash folder .. but when i delete files from the other ntfs drive, the files do not go in the trash folder but they have to deleted immediately.. y is that? is there a seperate trash folder for every drive?

also wts the lost+found folder?

---

