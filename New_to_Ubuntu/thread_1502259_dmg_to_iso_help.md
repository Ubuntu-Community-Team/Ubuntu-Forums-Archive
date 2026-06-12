---
title: "dmg to iso help"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by keylokes on 2010-06-05
So im trying to convert an img to iso ..

i did one a few days ago. i googled something and somehow found a program that is allready installed in ubuntu. but i forgot the command.. and now i cant find it!! 

i tried downloading dmg2iso.pl did chmod .. like 3 times form diferent sites ... one said chmod 777 .. another 755 and another +x .. but none work all i would get was .. "file or directory does not exist" or something like that.

would anyone know what program i used .?? i remember in the forum post it said somthing with ... " dmgiso cache .."

and yes ive looked for a good 2 hours now.. maybe someone knows what im talking about ....

thank you all...

---

### Post by NUboon2Age on 2010-06-05
Sorry I didn't see whatever previous thread you're referring to, but does this help?
[https://help.ubuntu.com/community/DMG2IMG](https://help.ubuntu.com/community/DMG2IMG)

or

[https://help.ubuntu.com/community/ManageDiscImages](https://help.ubuntu.com/community/ManageDiscImages)

That one talks about ccd2iso

On the "file or directory does not exist" 
I wonder if you're having trouble invoking the command because you're 
a) invoking it w/o it being on the path and 
b) the terminal's current working directory is not the same as where your program is and you didn't give the absolute path to it and  
c) you're didn't try ./<command>  

Of course you could set the 'executable' property in nautilus.

---

### Post by keylokes on 2010-06-06
thanks .. yeah i ended up doing that.dmg to img to iso. but i saw one that did it straight.. anyways.. 

yeah.. i did do the "./" in front of it.. i moved all the files to the same directory then .. "cd" to that directory .. and "ls" and all the files were there.. so i dont know what i did wrong with "dmg2iso.pl" .. 

anywho .. thanks..

---

