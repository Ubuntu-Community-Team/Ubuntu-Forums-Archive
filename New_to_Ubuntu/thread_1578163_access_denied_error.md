---
title: "access denied error"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by orangesoda22 on 2010-09-20
hi everyone!
im new to ubuntu and am looking for some help getting it installed.

im running vista and using a partitioned section to install with wubi.


the first time i tried to install it it gave me an error that said:


an error occured
permission denied
see c:\users etc etc

well i tried to find the file it was pointing me to but couldnt so i reinstalled it.

the same thing happened again but this time i looked up how to fix it online, and i believe i did (the folder it was pointing me to was hidden, so i made it.........not hidden.........and not reaad only.)

so i have the files downloaded, but cant figure out how to install them.

the only file i can make sense of is the iso one but cant figure out what to use it. when i double click it it gives me the option to burn it to a disc but i dont have blank ones.

i dont want to run wubi again, at least not if its going to re-download the whole thing again (which takes about 3 hours for me)


so what can i do?

---

### Post by orangesoda22 on 2010-09-20
im just gonna go ahead and...........*cough*bump*cough*

---

### Post by k33bz on 2010-09-20
Not sure what you are asking. As far as the files you downloaded, can you elaborate on what files you are talking about. 

The iso file yes you can burn to a disk, but since you stated you dont have any blank ones you can put it on a usb stick.

---

### Post by orangesoda22 on 2010-09-20
i downloaded ubuntu using wubi and it didnt install because it gave me that error. but i cant get it to install the files it downloaded without erasing them and redownloading them.

---

### Post by k33bz on 2010-09-20
> **orangesoda22 said:**
> i downloaded ubuntu using wubi and it didnt install because it gave me that error. but i cant get it to install the files it downloaded without erasing them and redownloading them.

I personally never have dealt with wubi, so I cant really help you with to much. Like I am not sure what it all Downloads, and dont understand why you cant install with out erasing and downloading again.

However I have heard that there is complications using wubi, but personally I dont know.

---

### Post by orangesoda22 on 2010-09-20
well, i burned the iso onto a cd but when i boot up with it in the drive i get

uncompression error
system halted


then i tried running the disk from inside windows and got the same permission denied error.

im getting a little bit pissed about this. ive been working on installing this damn thing for about 8 hours off and on now and still havent gotten anywhere.

so please, if anyone has any help to offer, go right ahead.

---

### Post by k33bz on 2010-09-20
When you burned the iso, did you burn it as an image? Or as a data file?

---

### Post by orangesoda22 on 2010-09-20
im not sure actually. when i open "my computer" it shows up as "install ubuntu"

---

### Post by k33bz on 2010-09-20
> **orangesoda22 said:**
> im not sure actually. when i open "my computer" it shows up as "install ubuntu"

ok, I will ask in a different way. With your windows machine on, when you put the disc in, open the disc, do you see the iso file? Or do you see other files and folders?

---

### Post by orangesoda22 on 2010-09-20
files and folders

---

### Post by k33bz on 2010-09-20
ok, then it sounds like you burned it as an image.
Did you check it with md5 making sure it was a good download and not corrupted?

---

### Post by orangesoda22 on 2010-09-20
i didnt. googling md5 now.

---

### Post by k33bz on 2010-09-20
ok, after you verify the integrity of the download let us know.

---

### Post by orangesoda22 on 2010-09-20
> **orangesoda22 said:**
> i didnt. googling md5 now.

ok that didnt get me anywhere...

so what is this md5 you speak of and how do i use it?

---

### Post by CaptainMark on 2010-09-20
your download may have corrupt before you burnt it to disk, download it again from fresh and run md5sum check on it before burning, this page tells you about them, [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) google for windows md5sum to find a windows program if you need it

* way too slow typing

---

### Post by k33bz on 2010-09-20
> **CaptainMark said:**
> your download may have corrupt before you burnt it to disk, download it again from fresh and run md5sum check on it before burning, this page tells you about them, [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) google for windows md5sum to find a windows program if you need it

* way too slow typing
sad thing is, I think he said it takes him 3 hours to download :(

---

### Post by orangesoda22 on 2010-09-20
yeah. but im doing it anyway. directly from the ubuntu site. screw wubi.

---

### Post by orangesoda22 on 2010-09-20
> **orangesoda22 said:**
> yeah. but im doing it anyway. directly from the ubuntu site. screw wubi.
its going a bit faster downloading the file directly instead of as a torrent (which is how wubi does it)

---

### Post by k33bz on 2010-09-20
> **orangesoda22 said:**
> its going a bit faster downloading the file directly instead of as a torrent (which is how wubi does it)

Thats good to hear :)

BTW why were you using Wubi?

---

### Post by orangesoda22 on 2010-09-20
> **k33bz said:**
> Thats good to hear :)

BTW why were you using Wubi?
because it was supposed to be the "easiest" way

---

### Post by k33bz on 2010-09-20
lol, not from what I heard :)

Sorry couldnt resist :popcorn:

---

### Post by orangesoda22 on 2010-09-20
no trust me i know what you mean.

thanks so much for your help btw. ill let you know if it works when i get all this done.

---

### Post by k33bz on 2010-09-20
> **orangesoda22 said:**
> no trust me i know what you mean.

thanks so much for your help btw. ill let you know if it works when i get all this done.

sounds good, shoot an email, I may be getting off here soon, have to get some rest, lots of work to do in the morning.

---

### Post by orangesoda22 on 2010-09-20
just to update and see if anyone else can help, i got it downloaded and verified with md5, burnt image to disk, and rebooted.

everything went fine until i got to a screen that said


prepare disk space

and gives me the option of either

erase and use the entire disk (which i dont want to do)

or

specify partitions manually (which i dont know how to do)

it originally had another option where i could install alongside the other OS but when i picked that option then tried to resize the partition, it never got past 0% and then gave me an error.



so im lost. what do?

---

### Post by CaptainMark on 2010-09-20
i would maybe give it a few tries just in case it was having a funny 5mins, partitioning manually isnt too tricky (saying that ive never tried to dual boot with windows) if you need help post back. ive heard its a good idea to defragment your windows first

---

### Post by orangesoda22 on 2010-09-20
i managed to get it installed, but now i have a new problem. its posted up in my other thread "no kernel exists"

---

