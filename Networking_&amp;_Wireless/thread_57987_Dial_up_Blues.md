---
title: "Dial up Blues"
date: 2005-08-18
forum: Networking &amp; Wireless
---

### Post by Infatuated_iPod on 2005-08-18
I am having a lot of trouble trying to get my dial up connection to work. 

I ran the pppconfig and configured everything the correct way. Then when i do pon i get this error message. 

/usr/sbin/pppd: In File /etc/ppp/peers/provider:
unrecognized option ' /dev/modem'

Ok.. so then i tried to do wvdialconf /etc/wvdial.conf

and it said that no modem was detected. 

how do i get the computer to detect the modem?

I have a CONEXANT D480 MDC V.9x Modem.

Thanks for all your help.

---

### Post by BrianB on 2005-08-18
Sounds like a winmodem, try  downloading scanmodem (google it) and post what it says. Also have a look at [linmodems.org](http://www.linmodems.org/) .

---

### Post by Infatuated_iPod on 2005-08-18
Well i spent a good part of my day researching downloading and tryin stuff out on my own but now i am stuck. 

i did the scan modem and it pointed me to [www.linuxant.com](www.linuxant.com) where i got the HSF driver.. i tried to install it and thought that it was working, but when i did the final step it said that the kernel didnt match or something.. 

it said i needed to make sure that all the directories were pointing to the right tree or something like that, then it said that i need to recomplie my new kernel.. i have no idea how to do any of these things and i fear i have ventured into unknown territory.

I dont know what to do, please help.

Also, it is difficult to post any error messages on here, because i am workin off two computers, i will try my best though,

---

### Post by BrianB on 2005-08-19
Well it really would help if I could see exactly what it says. Try pasting it in a text file and put it on a floppy or mp3 player and what chipset does it say you have?

---

### Post by blastus on 2005-08-19
It would be a Conexant chipset. And you'd have to buy the drivers from [http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/) I think. I believe they limit your connection to 14Kbps but when you buy the driver it runs at full speed 56Kbps.

The problem is that since linuxant sells the drivers I would assume they only come in binary form. This means that you have to find the driver that was compiled against your kernel. This means that if you install a newer version of Ubuntu or do something with your kernel you'll probably need to download new drivers for your modem.

With a Lucent modem that has a DSP, the drivers are freely available in source form. So you would just compile them against your kernel which I did to get my Lucent modem to work in Ubuntu.

---

