---
title: "identifying my modem"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by dckirba on 2006-10-31
Hello everyone,

I hope this is the right forum to ask this question...

A friend of mine just gave me a couple of old US robotics  modems. However, before I put them into my computer, I would like to know if they work with linux.

My problem is that I don't know where to look for the modems serial/model number.

The chip has a number on it, but there are loads of numbers all over the place.

Would an image help? If so, I'll take a couple of pictures and attach them.

Thanks for your help, I'm pretty clueless about this :)

Cheers,
David K

---

### Post by glotz on 2006-10-31
Try [http://linmodems.technion.ac.il/#scanmodem](http://linmodems.technion.ac.il/#scanmodem)

I hear that many hardware modems work fine whereas most software modems (=winmodems) don't as their vendors don't support Linux.

---

### Post by dckirba on 2006-10-31
Thank you :) I am aware of this. My problem is that I don't know what model the modem is and so I can't search for it and find out whether it is a hardware or a software modem :(

Cheers,
David K

---

### Post by dckirba on 2006-11-01
Hello again everyone,

I have a picture of my modem here and I would appreciate it if someone could point out where I'm supposed to look to find out what model it is. Then I can google that up and find out what the linux support for the modem is like.

Thanks guys,
David K

---

### Post by glotz on 2006-11-01
I couldn't ID it but those are Texas Instruments logos on those there chips. Sure looks quite a lot like some of those TIs but not exactly [http://64.126.95.102:8080/gromitkc/dips/roster.html](http://64.126.95.102:8080/gromitkc/dips/roster.html)

---

### Post by dckirba on 2006-11-03
Thanks for that link :) I'm still looking through it, kinda looks like this modem won't work with Linux :( 

Thanks a ton for the help,

cheers,
David

---

### Post by lwoodtri on 2006-11-03
I dont know if this will work, but if you put it in the system, and see if it is recognized? if not  leave it in the sytem and try to attach to it via a terminal session stright through the com port and run the AT command ATZ when the cursor is flashing it should return an OK . . . you might have to turn on terminal echo as well then type at&v to retrive the modem register settings. Hopefully it will give you a model type and info to help you out.

---

### Post by lwoodtri on 2006-11-03
oh yeah.. just remebered to turn on echo . . . use ate1 and that should put in echo mode to the screen.

---

### Post by dckirba on 2006-11-04
Thanks lwoodri! Could you please give me more detailed instructions because I'm still not too familiar with all the command-line commands and don't know how to use AT.

I have only one pc. Would I be able to put the modem in and run the AT command from the same machine?

I was thinking about putting the modem in today, you read my mind :)

Cheers,

David K

---

### Post by dckirba on 2006-11-05
H everyone,



thanks for all the help, but when I opened up my PC to put the modem in yesterday, i realised that I don't have any slot that will take it :( Bummer.

The hunt for another modem continues... :)

Cheers all,

David K

---

### Post by mips on 2006-11-05
Amazing. Should these things not be checked beforehand ?

---

### Post by dckirba on 2006-11-05
Hey mips, it's a long story. I'm hunting for a modme that's ot a winmodem and they're hard to find here. My friend found this one lying around so he gave it to me and asked me to try them out. Should've opened up the PC before asking all the questions I guess :)

Cheers,
David

---

### Post by mips on 2006-11-05
David,

Most, if not all **External Serial** modems should work. Should make your search a bit easier.

---

### Post by dckirba on 2006-11-05
Thanks Mips,

I do know this. However, in Ethiopia, an external serial modem is not that easy to find. That is partly why I am also looking at other alternatives. 

Cheers,
David

---

### Post by glotz on 2006-11-06
And it's unfortunately only most (external will work), not all. Good luck with it!

---

