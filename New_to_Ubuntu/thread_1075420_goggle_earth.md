---
title: "goggle earth"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by lil_bunny on 2009-02-20
hi
im trying to get goggle earth to work i have tried a few things from this thread [http://ubuntuforums.org/showthread.php?t=916188](http://ubuntuforums.org/showthread.php?t=916188) cant remember which one i got to install it lol , 
Problem is it opens up then closes and wont stay open help please .

---

### Post by binbash on 2009-02-20
If you are trying google earth beta 5, you have to go google-earth folder and rename libcrypto.so.0.9.8 to anything you want

---

### Post by lil_bunny on 2009-02-20
well i assume i saved it to desktop ..... renamed the desktop folder that probably not what u ment but i cant seem to find it any where but there ..... so still not working.

---

### Post by binbash on 2009-02-20
sudo updatedb
then after it finishes : 

locate libcrypto.so.0.9.8

---

### Post by lil_bunny on 2009-02-20
now im lost :-? well i did what i thought you ment in terminal asks for password what password is this??? i dont have one ,

---

### Post by sydbat on 2009-02-20
Yes you do. Just enter the password you use to log in when you boot/reboot your computer. It will not show up when you type it, but should give you the sudo access you require.

---

### Post by lil_bunny on 2009-02-20
well nothing comes up when im typing so i press return and type it and then it tells me its wrong ,

---

### Post by lil_bunny on 2009-02-20
oooooooo i get it lol sorry bimbo here , so this is what i have done .....
 open terminal pasted: 
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

done password all fine but i still dont get what to do with the locate libcrypto.so.0.9.8 ???

---

### Post by lil_bunny on 2009-02-20
i still cant get it to workkkkkkkkk

---

