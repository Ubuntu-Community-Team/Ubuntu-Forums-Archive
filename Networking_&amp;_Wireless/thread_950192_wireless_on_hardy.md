---
title: "wireless on hardy"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by lkc0987 on 2008-10-16
hi..i got a new hp-dv5t laptop..and am very much impressed by it..

i just installed ubuntu on it and everything works fine except the wireless..i have an intel 5100 card..could anyone help me with this..

i found some posts previously which said we gotta get the new kernal or somethin, but it was way too geeky :)..

help me out!

---

### Post by GuitarRocker2562 on 2008-10-16
While I would highly advise it, Ubuntu Intrepid Ibex should support your card, but it is still in Beta, you can use it, but you may get lost. Good news, the final should hit the end of the month.

---

### Post by lkc0987 on 2008-10-16
thats what i am waiting for...but i was hopin if i could find a solution...coz i cant always keep my laptop connected to a wired n/w!! :(

---

### Post by sam_delta on 2008-10-16
i have an intel 3945ABG
not the same as you, mine was a little flanky and 
installing linux backport modules got mine working
give it a shot, 
```

sudo apt-get install linux-backports-modules-hardy-generic
```
note that youlll need a internet connectioin to install them, so plug ur cable, and run the above command.

let us know how it goes
sam

---

### Post by linux6994 on 2008-10-16
I have Intrepid installed on a couple of laptops one is Dell 1520 the other an Averatec 4155. They both work great even though the load is Beta. Over all its a great Beta.

---

### Post by lkc0987 on 2008-10-18
> sudo apt-get install linux-backports-modules-hardy-generic

this didnt work for me man...but thanks for the help..


the network manager shows that it can configure even wireless networks..
[IMG]http://i19.photobucket.com/albums/b163/lkc0987/Screenshot.png[/IMG]

but i guess that is because the device manager recognises there is a wireless interface on my compy but it doesnot have the drivers for it...

so...any other brght ideas?? dont we have generic wireless drivers that may work for this?

---

### Post by cakmin on 2008-10-18
> **lkc0987 said:**
> this didnt work for me man...but thanks for the help..

so...any other brght ideas?? dont we have generic wireless drivers that may work for this?

Perhaps try installing the linux-backports-modules-hardy-generic from the unsupported updates first and see if it helps you or not. I used to have a problem with my wireless internet connection, I solved it today by following this instruction:
[http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/](http://linuxtechie.wordpress.com/2008/04/24/making-intel-wireless-3945abg-work-better-on-ubuntu-hardy/)

Sorry I forgot to add that my wireless card is Intel PRO/Wireless 3945ABG.

---

### Post by lkc0987 on 2008-10-18
also, the device manager shows that the card is recognised as an intel card and that its a wireless interface and all, and that it is also connected to a button(a touch button that toggles color of the led when wireless on/off)..this started working after i enabled the unsupported updates..and now i can see an updated dropdown in the network tools menu

[IMG]http://i19.photobucket.com/albums/b163/lkc0987/Screenshot-NetworkTools.png[/IMG]

i wonder what these new things would do..but you guys would probably know what these are and how they may work...

i would also appreciate it if anyone could help me regarding the various touch buttons that are on my lappy...**_is there a way i can configure them to work in ubuntu_**?except the volume, nothin els works..and that reminds me..the volume buttons reduce the volume of the MASTER volume, but that doesnt reduce the volume...**_i have to manually open the volume control and then reduce the volume in the FRONT_**...any help there?

---

### Post by lkc0987 on 2008-11-06
Finally started working after installing Intrepid..

---

