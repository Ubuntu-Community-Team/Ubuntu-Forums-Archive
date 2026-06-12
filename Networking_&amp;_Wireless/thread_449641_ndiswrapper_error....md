---
title: "ndiswrapper error..."
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by computerjunkie on 2007-05-20
im following the instructions here: [http://dossy.org/archives/000110](http://dossy.org/archives/000110) and when I try to run the command  "ndiswrapper -i BCMWL5.inf" terminal responds with:

 "couldn't open bcmwl5.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174"

This is the driver that the person used in the tutorial so um what the hell does that error mean?

I also tried running the command as "ndiswrapper -i /home/*name*/Drivers/bcmwl5.inf" so I get "Installing bcmwl5...couldnt open /home/*name*/Drivers/bcmwl.inf: no such file or directory at /usr/sbin/ndiswrapper-1.9 line 174"

do I need an updated ndiswrapper? I downloaded 1.38.deb from [http://archive.ubuntu.com/ubuntu/pool/main/n/](http://archive.ubuntu.com/ubuntu/pool/main/n/)  because the computer i'm doing this on doesnt have internet i have to download packages through my win98 machine and transfer then using my flash drive. Sooooo unfortunately i cant use synaptic until i get my wireless card working. its the linksys 54g speedbooster, model wmp54gs.

My question is how the heck can i get this working???

I know line 174 refers to that line in the code and it says "open(INF, $filename) or die "couldn't opn $filename: $!";
Why cant it open the file path? is there a specific directory I need to put the files in so ndiswrapper can open them properly?

---

### Post by Floppyjoe on 2007-05-20
The filename in the command is case sensitive so you need to make sure you are using capitals where the filename has capitals and lower case letters where the filename has lower case letters.

---

### Post by computerjunkie on 2007-05-20
ok it installed thanx. I went through the stpes of adding everything to the /etc/network/interfaces file, but the "ifup wlan0" command doesnt work, it just produces a lot of errors. How do I make ubuntu use the driver i installed so it can use the card?

I typed iwconfig in terminal and it came up with "eth1" as wireless, so i changed the values in the /etc/network/interfaces file with dhcp enabled. then did "sudo ifup eth1" and it said the interface is already configured, but the essid that i entered in the file (linksys-dragonrt which is the name of the router) shows up as "l" so the access point is labeled as invalid in terminal. um yea and by setting fiesty fawns wireless thing to roam its not finding my access point, but its obviously operational because my laptop is connected to it which is how im typing this.... so yea confused help please.

When I do ifconfig eth1 isnt listed and when i do ifconfig /all it says that "error fetching information: device not found" so I'm asuming that is talking about the wireless card.

back to my original question, how do i get fiesty to use the driver i installed?

---

### Post by computerjunkie on 2007-05-21
Well I'm so good i managed to completely crash ubuntu...

I gave up on it for  while and came back to it later. driver was already installed. ok.I used modprobe to load the driver, then did ndiswrapper -m so it would load on boot and then restarted it. Yupp now ubuntu wont even start i get a beautiful white blinking cursor in the upper left hand corner of the screen. excellent. at this rate im going to have to go back to windows on my desktop. there is no connection to the internet in my room, except wireless and I really dont want to have to keep using my win98 laptop as it is quite limited and apps tend to crash often. (cant use blender or watch stuff on tv-links.co.uk et cetera)

is there anyway to fix ubuntu and how would I get my wireless card working in ubuntu if its possible?

---

### Post by Count Doofus on 2007-10-21
File name does not match because the case is wrong !


 had the same problem with my Marvell card. Looked for every kind of solution that concerned hardware interface on the PCI bus.

The Real Problem was every time I issued the 
blablabla:~$ sudo ndiswrapper -i mrv8000c.inf 
I got - No such file or directory at /usr/sbin/ndiswrapper-1.9 line 174

Until I typed the filename with the correct CASE - Mrv8000c.INF - 

GRRRRRRRRR!%@$#$###!$!@@!$@!@#!

---

