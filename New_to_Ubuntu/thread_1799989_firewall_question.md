---
title: "firewall question"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Guy Secretan on 2011-07-08
greetings

i have recently made the switch to ubuntu and i flipping well love it. it's ace. so so so so so so so so much better than windows, so stick that one in your pipe, bill gates.

the thing is, the only bit i prefer about windows is MS Word. 

libre office is ok but there are some functions i need that you can only get in word. so, i installed wine and was about to install the said beast when i suddenly remembered that ms word will want to connect to the internet, which i don't want it to do as i dont want billy-boy gates reading my love letters, secret recipe for coca-cola, etc. so how do i stop the thing connecting to the internet?

i have looked around the forum a fair bit but as i'm such a wet-behind-the-ears novice a lot of what i found in the security bit just went over my head.

is there a simple way of stopping software accessing the internet or do i have to type code into the terminal, and if so, what? will "sudo sod off microsoft" work? 

i'll buy you a pint if you can help me.

cheers and thanks in advance for any advice.

---

### Post by haqking on 2011-07-08
> **Guy Secretan said:**
> greetings

i have recently made the switch to ubuntu and i flipping well love it. it's ace. so so so so so so so so much better than windows, so stick that one in your pipe, bill gates.

the thing is, the only bit i prefer about windows is MS Word. 

libre office is ok but there are some functions i need that you can only get in word. so, i installed wine and was about to install the said beast when i suddenly remembered that ms word will want to connect to the internet, which i don't want it to do as i dont want billy-boy gates reading my love letters, secret recipe for coca-cola, etc. so how do i stop the thing connecting to the internet?

i have looked around the forum a fair bit but as i'm such a wet-behind-the-ears novice a lot of what i found in the security bit just went over my head.

is there a simple way of stopping software accessing the internet or do i have to type code into the terminal, and if so, what? will "sudo sod off microsoft" work? 

i'll buy you a pint if you can help me.

cheers and thanks in advance for any advice.

You mean it is an illegal copy of Word by any chance ?

Word works just fine offline without internet connection unless it is trying to register or update its custom.dic etc.

It also might be connecting to verisign

do you have auto update turned on ?

---

### Post by FormatSeize on 2011-07-08
> **Guy Secretan said:**
>  so how do i stop the thing connecting to the internet?
MS Word, in and of itself, does not access the internet on it's own. The user has to do something to make it go to the internet to find that resource. In MS Word 2003, there is a built in help menu, so when you push F1, it takes you to offline help files. In 2007, when you push F1, it immediately goes to the internet for help files. If you don't push F1, you won't go to the internet. That's one example.
 
Overall, if you don't access the internet, MS Word won't do it on it's own. It's not on the internet in the background behind your back or anything. 
 
Out of curiosity, what functions are there in MS Word that you can't find in Libre Office?

---

### Post by Guy Secretan on 2011-07-08
> **FormatSeize said:**
> MS Word, in and of itself, does not access the internet on it's own. The user has to do something to make it go to the internet to find that resource. In MS Word 2003, there is a built in help menu, so when you push F1, it takes you to offline help files. In 2007, when you push F1, it immediately goes to the internet for help files. If you don't push F1, you won't go to the internet. That's one example.
 
Overall, if you don't access the internet, MS Word won't do it on it's own. It's not on the internet in the background behind your back or anything. 
 
Out of curiosity, what functions are there in MS Word that you can't find in Libre Office?


are you sure? fair enough then. i'll give it a bash.

and no, it's not an illegal copy. it's actually legit and was suitably overpriced.

basically, the bits i like are to do with formatting. with libre office, when i copy and paste from pdfs and websites the formatting goes haywire no matter what i do (clear formattingt; run it through gedit etc). this drives me mad.

anyway, thank you both for the help.

regarding program control, though, is there a way of stopping individual progs accessing the internet? 

cheers

---

### Post by haqking on 2011-07-08
are you using paste special to keep formatting or just paste ?

and you could use apparmor

Or configure firestarter or gufw or iptables command line to configure the ports you want blocked from egress actions ?

---

### Post by Guy Secretan on 2011-07-08
> **haqking said:**
> are you using paste special to keep formatting or just paste ?

and you could use apparmor

Or configure firestarter or gufw or iptables command line to configure the ports you want blocked from egress actions ?

thanks for the help. 

i can see i'll have to do my homework on the firewall stuff. just looked at the apparmor wiki and it scared the hell out of me. more code than the kgb.

cheers again, though. i probably owe you a pint!

---

### Post by haqking on 2011-07-08
I am a fine malt whisky type of guy ;-)

if its a pint then Guiness only.......choose one and send them however you wish ;-)

---

### Post by Guy Secretan on 2011-07-08
Am uploading a pint of the black stuff right this minute...

might take a while for the head to download, mind.

---

