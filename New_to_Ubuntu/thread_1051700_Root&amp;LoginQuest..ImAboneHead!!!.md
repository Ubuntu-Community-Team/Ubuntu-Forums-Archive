---
title: "Root&amp;LoginQuest..ImAboneHead!!!"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by mbele3000 on 2009-01-27
Hi Earth People

  I am riding the wave again and have well fallen off the wagon as far as remambering my commands.. So any way I can change my root password but not my root name or my login. I know it has to be dumb simple but it's been a coupe months since I got my PC back so any help would be great! And if there are any essential books(or ebooks) for morons (myself) that give a pretty good laymans stepby step that would be great. Again Thank You and Peace!

---

### Post by mikewhatever on 2009-01-27
Ubuntu doesn't use root passwords, in fact, doesn't have root account enabled, so, just use your admin password.

---

### Post by mbele3000 on 2009-01-27
Ok heres the problem I set up my Moms comper and she was the admin (shes 76 and clicks alot bad idea I know)! When i 1st ran the install the line up was root@marybarry-desktop:home/marybarry.
But in the "users & groups" I cannot change the username (it let me change the password) it still says marybarry so every time i start the (admin) login is still marybarry when I just want to wipe that out all together and set her up so that she can not install or deleat applications or go wily nilly in the home folder (I love her but God help us all if that happend). 
   So ad nauseum Im sorry
 
When I had the root termiinal open it said:

root@marybarry-desktop:home/marybarry

and the regular terminal said:

marybarry@marybarry-desktop:~$

Now in root terminal I have got it to: 

root@mynewname-desktop:/home/mbele

and the regular terminal says:

marybarry@mbelenaziryusef-desktop:~$ 

 now the new password i have works but I still have to write marybarry at login and well I want to change that so that I can re establish that under a more limited capacity user... Sorry it's late and well I not that smart! Th:Danks for the quick response BTW

---

### Post by Temposs on 2009-01-27
I see what you're trying to do...in general don't use root terminal as it lets you type in powerful commands very quickly.

Please use the Users and Groups GUI to manage this kind of thing. Go to System->Administration->Users and Groups

Click Unlock and then you can add and delete users and change their priveleges very easily.

---

### Post by Tek-E on 2009-01-27
Agreed!! I wouldnt use a root account either if I were you.  I made the mistake of having one and managed to have to re-install quite often.

---

