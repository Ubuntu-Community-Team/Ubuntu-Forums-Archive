---
title: "SMC2835W v1 pcmcia/cardbus Ndiswrapper Edgy RC Works."
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by Jon@bayleys.org.uk on 2006-10-28
OS: Edgy RC
Card: SMC2835w
Chipset: Prism GT / Duette

This isn't my knowledge, and I'm using bits and pieces I found from other peoples effort in this forum and others, but seeing as other people are still having difficulties, I thought I'd write an 'idiots guide', i.e. something I can understand...

After doing battle with an SMC2835W v1 cardbus adaptor for several days, trying both native drivers and ndiswrapper,  I eventually decided to stop trying to unbreak stuff I'd already broken and forgotten about.:rolleyes: So back to the drawing board, downloaded an iso of 
edgy, installed it. Everything worked really well. 

 1. Install Edgy. ( I did  say it was idiots guide...)
 2. Once computer has rebooted after install, log in.
 3. Insert the ubuntu CD into the drive, it will start the CD for you automatically, and ask you if you want the CD to start the package manager. Say Yes
 4. do a search for 'ndis' (no quotes)
 5. Select ndiswrapper, ndis-utils common, ndis-utils 1.1, and ndis-utils 1.8
 6. Apply, close synaptic
 7. open a terminal window (accessories-> terminal)
 8. type 'sudo rmmod prism54' (no quotes), enter password
 9. type 'sudo ndiswrapper -i [path to your windows drivers for your card, if they're on a CD, it's probably something like /media/cdrom0/driver folder/driver remember, CASE SENSITIVE]
 10.type 'ndiswrapper -l' (no quotes) should list the driver name, and say, driver present, hardware present.
 11. type 'ndiswrapper -m'
 12. type 'sudo modprobe ndiswrapper'
 13. Hurrah. Little flashy lights on the card! All is well with the world.

Cheers.

---

### Post by Jack73 on 2006-10-29
Thanks, this works and it is easy to use.
I have SMC2835W EU -version of that card and it works now. :)

---

### Post by javierfh on 2006-11-05
> **Jon@bayleys.org.uk said:**
> OS: Edgy RC
Card: SMC2835w
Chipset: Prism GT / Duette

This isn't my knowledge, and I'm using bits and pieces I found from other peoples effort in this forum and others, but seeing as other people are still having difficulties, I thought I'd write an 'idiots guide', i.e. something I can understand...

After doing battle with an SMC2835W v1 cardbus adaptor for several days, trying both native drivers and ndiswrapper,  I eventually decided to stop trying to unbreak stuff I'd already broken and forgotten about.:rolleyes: So back to the drawing board, downloaded an iso of 
edgy, installed it. Everything worked really well. 

 1. Install Edgy. ( I did  say it was idiots guide...)
 2. Once computer has rebooted after install, log in.
 3. Insert the ubuntu CD into the drive, it will start the CD for you automatically, and ask you if you want the CD to start the package manager. Say Yes
 4. do a search for 'ndis' (no quotes)
 5. Select ndiswrapper, ndis-utils common, ndis-utils 1.1, and ndis-utils 1.8
 6. Apply, close synaptic
 7. open a terminal window (accessories-> terminal)
 8. type 'sudo rmmod prism54' (no quotes), enter password
 9. type 'sudo ndiswrapper -i [path to your windows drivers for your card, if they're on a CD, it's probably something like /media/cdrom0/driver folder/driver remember, CASE SENSITIVE]
 10.type 'ndiswrapper -l' (no quotes) should list the driver name, and say, driver present, hardware present.
 11. type 'ndiswrapper -m'
 12. type 'sudo modprobe ndiswrapper'
 13. Hurrah. Little flashy lights on the card! All is well with the world.

Cheers.

Hello,

i have done all these steps and at some point i saw one of the lights flashing couple of times, after that nothing..
is there anything im doing wrong? is there any way to check if everything should be working?
Is there any way to make the wlan card to check the available networks, i guess the card is not doing anything now.

Any help will be more than welcome, i guess im very close to it, but still not working.

Thanks in advance,

Javi

---

