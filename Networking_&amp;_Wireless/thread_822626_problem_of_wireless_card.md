---
title: "problem of wireless card"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by zopanp on 2008-06-08
Hello evryone,

I have some problem to run wireshark or aircrack suite (for personal wep craking) .
I think it is due to my wireless card, it is an Minicarte Intel next-gen wireless-n in a dell xps m1530 .

would anyone know if this is the problem ?

thanks in advance for your wise answers .

zopa

---

### Post by rlzyoner on 2008-06-08
You should check that your wireless card supports monitor mode.
Assuming you have the aircrack-ng suite installed,
Try running airmon-ng start wlan0 7

wlan0 being the name of your wireless adaptor (change if necessary)
7 being the channel you wish to listen on (change accordingly)

Running iwlist scanning will determine of what channel your router is broadcasting on 

Hope that helps

---

### Post by confuded92 on 2008-06-08
With such a big amount of information about your: Kernel, system, hardware, release version and ACTUAL PROBLEM anyone can help you... :-k

Can you please at least tell us what Ubuntu release are you running? Hardy? Feitsy? Gutsy? It will be also helpful providing the kernel version and aircrack/wireshark version you are using...

The command 'sudo lshw' will give the output of the hardware in your laptop. 

As far as I understood, it is a built-in Mini PCI card. The intel mini PCI devices listed [_here_]("http://linux-wless.passys.nl") (link provided by aircrack-ng website) seem to be mostly supported by aircrack-ng (or packet injection). 

You might not have installed the correct drivers. ;)

~confuded

EDIT: rlzyoner, had posted right before me :). Just want to add to his post: try running 'sudo airmon-ng' by itself. This will show you if any device are already monitor mode enabled or don't support monitor mode at all. Also, if you get something like this:

wlan1     rtl8187 [phy1]

(referring to the phy1) it will probably result in an error when putting into monitor mode (in my experience). This happens because the loaded drivers don't support monitor mode.

---

### Post by zopanp on 2008-06-08
Hello and thanks for your diligent answer.
as you can see I did a *airmon-ng start wlan0*:[ATTACH]73389[/ATTACH]

So how bad is it doctor ?
do I have do buy a other card ?
and Wich one ?

thanks

zopa

---

### Post by zopanp on 2008-06-08
I am sorry,
I have a dell xps m1530 with a core 2 duo T9300,  4096MB 667MHz Dual Channel DDR2 SDRAM, an NVIDIA GeForce Go 8600m GT, and as you said a built-in wireless card.
I am running on Linux Ubuntu 8.04 - Hardy Heron with the gnome 2.22.2 interface .

Thanks

zopa

---

### Post by confuded92 on 2008-06-08
Told you :P. Uou havent got the correct driver... I asume you've got an Intel 4965AGN, judging by the loaded driver name.

[_These_]("http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-4.44.1.20.tgz") should do the job...

~confuded

EDIT: Darn! You guys beat my 3G dial up connection :D. No need to be sorry.., Just next time please provide the necessary info...

---

### Post by zopanp on 2008-06-08
I am sorry but i am a linux beginer and I don't understand how do I have to use the file once it is downloaded, would you kindly help me please ?

thanks.

ps: I love ubuntu and it's diligent, fast and gentle users .

---

### Post by confuded92 on 2008-06-08
My bad :D. i have got you the wrong link... Sorry! I will post another with instruction shortly...

EDIT: I will need your kernel version Just type in: 'uname -a' in the terminal.

---

### Post by zopanp on 2008-06-08
There is no problem and take your time .

thanks a lot .

---

### Post by confuded92 on 2008-06-08
OK, nerevmind with the kernle version. Try [_this_]("http://www.intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi"). I hope these instruction fit your level. Just when pasting commands provided in the above HOW-TO, don't paste them with the '%'. :)

Good luck and happy hacking! ;)

~confuded

P.S. I am unable to help further, since I have to go now.

---

### Post by zopanp on 2008-06-08
Linux zopa-laptop 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

---

### Post by zopanp on 2008-06-08
Thanks a lot i will try

---

### Post by zopanp on 2008-06-08
hello,
This is the result ... why is it doing that way  ?

[ATTACH]73396[/ATTACH]

thanks for your answwers

zopa



Please Help

---

