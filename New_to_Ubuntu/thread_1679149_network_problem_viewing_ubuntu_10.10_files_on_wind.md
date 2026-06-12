---
title: "network problem viewing ubuntu 10.10 files on windows"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by Adriano9966 on 2011-01-31
:D greetings fellow ubuntu users this is my very first post on this forum even though I have been using ubuntu for a number of years 

I recently passed my amatuer radio exam and set up my shack outside complete with amilo pro laptop that has a broken screen but that I use on ubuntu with an external lcd monitor for ham radio logging qrz.com and hopefully soon psk31   my wife uses windows vista and I also have another netbook  that works on windows xp 

although I have set up my wireless network and it works beautifully on samba when viewing files from both the xp and the vista machines I cant open files from ubuntu with either of the windows computers and I receive the following error message ......ubuntu server(samba,ubuntu)is not accessible.you might not have permission to use this network resource](*,)

really infuriating ! did think of using wubi on the other two laptops but wife says no regarding her vista machine and the netbook did not want to co-operate(freezes up even with xubuntu) any ideas please people:) my os is ubuntu 10.10

---

### Post by PunkLV on 2011-01-31
This is just a guess based on my frustration sometime back: did you add "UNIX-based File/Printer Sharing Service" in Add/Remove programs on your XP machine?

---

### Post by Adriano9966 on 2011-01-31
> **PunkLV said:**
> This is just a guess based on my frustration sometime back: did you add "UNIX-based File/Printer Sharing Service" in Add/Remove programs on your XP machine?

:)thank you for the reply no cant say I have on either windows machines 
I just checked in the add/remove windows components dialogue box and its not installed

---

### Post by davidmohammed on 2011-01-31
can I just check -

you are on windows xp or vista and you are trying to view the files on ubuntu?

You have shared the folder on ubuntu - what was the share name?

on windows use 

start - run

then type 

\\<ubuntu name>\<share name>

e.g.

\\myhost\mysharename


what error messages do you see?

---

### Post by Adriano9966 on 2011-02-01
;)I have resolved it I cant conceive why but by changing the hostname on the computer to something else everything worked   

I now have perfect networking between all computers in my house thank you for the replys guys your help was appreciated:popcorn:

:lolflag: now I need to get psk31 working from ubuntu on my icom 703 I have already obtained the relevent interface so hopefully I will be chatting to Japan on 20m soon using my computer keyboard

thanks again

---

