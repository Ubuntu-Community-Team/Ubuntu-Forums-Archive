---
title: "gnomad2  and creative zen problem"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-06-10
i am using gnomad2 2.9.1 and have been having this problem since i upgraded to 9.04. when i plug my creative zen in i get the following errors

no jukeboxes found usb bus

and 

unable to mount creative tech, ltd creative zen v plus
error initializing camera:-1:unspecifed error

really strange because the zen player is not a camera

lost trying to fix for my daughter 
any ideas?

---

### Post by rburkartjo on 2009-06-10
note the zen player shows as mounted when i plug it in

---

### Post by rburkartjo on 2009-06-12
okay i need some advise i have been looking for hours after this post and cant get the zen to work. okay can someone recommend an mp3 player that will work in ubuntu 9.04. i know there has to be one that will. it is for my daughter and would greatly appreciate it. seems that zen and gnomad2 just dont like each other anymore. tks

---

### Post by rburkartjo on 2009-06-12
i refuse to go back to windows to get this to work. ubuntu rocks

---

### Post by rburkartjo on 2009-06-12
i know that someone on this form has a good suggestion. going camping for the weekend hopefully when i get back sunday someone has a suggestion. i have never been let down when i asked a question here.

---

### Post by 14x on 2009-06-14
hi,
i dont have a solution but the same problem. 

if you browse the folder of the mounted zen, are you able to copy music there and actually hear it?

i can browse it like an usb stick, copy music there but it wont appear once i disconnect the player and try to listen to it....

anyone any solutions?
-sven

*update*

I found a solution.. it is somehow trivial.. dismount the zen and THEN open it with gnomad2...

---

### Post by aphirst on 2009-06-14
I get an error which I *think* is the same as yours. I.e. I plug in my Zen, then open Gnomad2, then it says "No Jukeboxes found".

I solve this problem by, while Gnomad2 is still open, unplugging and reconnecting my Zen. At this point, either Gnomad2 automatically recognises the Zen, or I simply press Ctrl+R (rescan Jukebox).

Hope that helps. ^_^

---

### Post by Roving Sign on 2009-06-14
Menu > Administration > Users and Groups

Select and unlock your username

Properties > User Priviliges

Make sure the the "Use Audio Devices" box is checked

If it doesnt work after that - reboot - and it should.(or maybe just log off and back on?)

---

### Post by rburkartjo on 2009-06-14
tks everyone for your answers. what 14x suggested worked for me

---

### Post by rburkartjo on 2009-06-14
oh by the way my daughter is the one that greatly sends her tks

---

### Post by wpwend42 on 2009-07-19
*I solve this problem by, while Gnomad2 is still open, unplugging and reconnecting my Zen. At this point, either Gnomad2 automatically recognises the Zen, or I simply press Ctrl+R (rescan Jukebox).*

I tried this, but my Zen V Plus freezes when Gnomad2 opens.

---

### Post by Elep.Repu on 2009-08-06
My issue was that I was selecting Data Transfer, instead of Music Transfer in Gnomad2.
So, after unmounting the automounted Creative Zen, and letting Gnomad2 mount it by scanning, I was able to transfer, and everything worked out wonderfully.

---

