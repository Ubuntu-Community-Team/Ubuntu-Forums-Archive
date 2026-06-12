---
title: "Open File From Inside External Hard drive with terminal"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by imortalninja161 on 2011-08-08
hay all so okie dokie i have plugged my external hard drive in to my laptop specs as follows

[LIST]
[*]NTFS
[*]USB
[*]500
[*]Seagate
[/LIST]
with terminal i have located the device something like this

imortalninja@######/media/portable$ now when i ls -a it i see a folder i want to open from inside the external hard drive eg meows :P so i do this....

imortalninja@######/media/portable$ cd meows 

but instead of getting this 
imortalninja@######/media/portable/meows$ 

i get error 
bash: cd: wii: No such file or directory

please help

Thanks 
imortalninja

---

### Post by DrScum on 2011-08-08
I think you need to add the /

i.e. cd /meows

---

### Post by Paqman on 2011-08-08
> **DrScum said:**
> I think you need to add the /

i.e. cd /meows

No, because that would look for a directory called meows under the root directory.

imortalninja161: Linux is case-sensitive, maybe your directory is called something like Meows? You can use TAB to autocomplete directory names. It's not only quicker, but makes sure you get the name right. Double-tapping TAB will list all the folders, too.

---

### Post by haqking on 2011-08-08
> **DrScum said:**
> I think you need to add the /

i.e. cd /meows

no you can use cd meows.

however linux is case sensitive so make sure your meows folder is all lower case if you are typing lower case.

show us a screen dump of your listing if you still have issues


edit: Ninja's above ^ ;-)

---

### Post by dcsoldschool53 on 2011-08-08
> **imortalninja161 said:**
> hay all so okie dokie i have plugged my external hard drive in to my laptop specs as follows

[LIST]
[*]NTFS
[*]USB
[*]500
[*]Seagate
[/LIST]
with terminal i have located the device something like this

imortalninja@######/media/portable$ now when i ls -a it i see a folder i want to open from inside the external hard drive eg meows :P so i do this....

imortalninja@######/media/portable$ cd meows 

but instead of getting this 
imortalninja@######/media/portable/meows$ 

i get error 
bash: cd: wii: No such file or directory

please help

Thanks 
imortalninja

No @imortalninja161, what you need to do, is continue writting it using the full path, like this```
cd /media/portable/meow
``` When you are in an external device, I do not know any shortcuts that you can use, other then typing the full path each time you want to change directories. If there is a folder inside meow that you want to goto, then```
 cd /media/portable/meow/name-of-new-folder
```

---

### Post by haqking on 2011-08-08
> **dcsoldschool53 said:**
> No @imortalninja161, what you need to do, is continue writting it using the full path, like this```
cd /media/portable/meow
``` When you are in an external device, I do not know any shortcuts that you can use, other then typing the full path each time you want to change directories. If there is a folder inside meow that you want to goto, then```
 cd /media/portable/meow/name-of-new-folder
```


shortcuts work the same way.

If you change to a portable device and can see the folder listed using ls

then you can just:

cd <foldername> or use tab completion same as if internal HDD
so if he can see meow then he can

cd meow

without use of / path

I do it all the time, i would assume it is a case sensitivity issue as mentioned previously.

---

### Post by dcsoldschool53 on 2011-08-08
yes @haqking It did work, because I just tried what you said. So on the command line cd meow will get you into the new folder too. Which means, both ways will work for them.

---

### Post by imortalninja161 on 2011-08-09
hay guys thanks for all you help and i have resolved the issue  :D

my example was not the exact command and syntax so it made it harder for you all to help figure it out so i will past the exact command next time.

i was aware that terminal is case sensitive but i was not aware of the / for spaces the  name of the folder i was trying to open was 

"home work" so i needed to > cd home\ work

instead of > cd homework

one again thanks guys for all the help

Peace Out 
imortalninja

---

