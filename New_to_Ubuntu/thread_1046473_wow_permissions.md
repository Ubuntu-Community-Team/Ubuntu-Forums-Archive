---
title: "wow permissions"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by sirdrakey on 2009-01-21
this always makes me feel like a n00b but i'm having wow patch update problems and before you seen me to the gaming section listen.

I installed wow across a network so the user of the files is unknown when the new patch ran it needs to create a .tmp of course it can't be cause it doesn't have permission I was going to just copy over the files but i don't have permission so i need permission have tryed the chmod and got this

>  sudo chmod -R a+w /home/deanna/.wine/dosdevices/c:/Program Files/wow

chmod: cannot access `/home/deanna/.wine/dosdevices/c:/Program': No such file or directory
chmod: cannot access `Files/wow': No such file or directory 


to solve my problem I need to give my self sudo outside the terminal, or change the files so they are permissioned to me or anyone so in the future updates they will be able to write .tmp and new files

thanks for the help

---

### Post by Malalo on 2009-01-21
It seems to consider that the space between "Program" and "Files" sperates 2 different folders....
Maybe put the entire access path between quotes ?

sudo chmod -R a+w "/home/deanna/.wine/dosdevices/c:/Program Files/wow"

---

### Post by opscure on 2009-01-21
try putting a \ after c and Program like this:

sudo chmod -R a+w /home/deanna/.wine/dosdevices/c\:/Program\ Files/wow

if that doesn't work right get rid of the \ after c and try again.

chmod was looking for the file /home/deanna/.wine/dosdevices/c:/Program 
not the full path since there was a space in there.

---

### Post by Ender Black on 2009-01-21
Try:
```
sudo chmod -R a+w /home/deanna/.wine/dosdevices/c:/Program\ Files/wow
```

---

### Post by achase79 on 2009-01-21
```
sudo chmod -R a+w "/home/deanna/.wine/dosdevices/c:/Program Files/wow"
```
or
```
sudo chmod -R a+w /home/deanna/.wine/dosdevices/c:/Program\ Files/wow
```

---

### Post by sirdrakey on 2009-01-21
It was the front slash thanks guys that blu the locks off

Ender Black's code hit it

thanks everyone for the quick response this is why i love ubuntu we just need open source directx and we would be rocking

---

### Post by mister_pink on 2009-01-21
Thought I'd mention that the best option wouldn't be to chmod it at all - havent a freely accessible folder in your home directory isn't advised. Instead I'd use chown to make it so you own the files with 
```

sudo chown deanna:deanna "/home/deanna/.wine/dosdevices/c:/Program Files/wow"

```
then put the permissions back to normal:
```

sudo chmod 755 "/home/deanna/.wine/dosdevices/c:/Program Files/wow"

```

---

