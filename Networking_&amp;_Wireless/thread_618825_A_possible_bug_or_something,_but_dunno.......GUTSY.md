---
title: "A possible bug or something, but dunno.......GUTSY(Dell 1501 wireless)"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by zeus09 on 2007-11-20
Hi all,
I am new to Ubuntu Gutsy Gibbon 7.10, but had been using Feisty Fawn 7.04 for some time.
The reason for this post is that i've noticed something weird with Gutsy's Restricted Driver method to enable wireless support for Dell 1501's as illustrated on :

[http://www.ubuntu1501.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntu1501.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html)

I installed Gutsy and used to above mentioned article to enable wireless support on my computer, but after enabling the wireless i noticed something weird on the computer, the computer started to upload at an alarming rate, this was evident from the sent data in the system monitor, the number mentioned next to sent data in system monitor under resources would rise to as high as 1GB in a span of around 1 to 1 1/2 hours, i ended up reinstalling the system, but after enabling the wireless support again the problem reappeared. 
I used various programs like netstat etc to verify whether the computer was actually uploading or was it a bug in the system monitor program, but nothing would show up under netstat etc. I used Wireshark, the protocol analyzer, it captured packets at an alarming rate, though i am  not conversant enough with the Wireshark, but i figured out that there was something wrong with the computer, i used the wired connection to verify whether the computer was working fine, it turned out the computer would function normally on a wired connection but would upload only on the wireless connection. 

I had to disable the in built firmware method with gutsy and had to use the NDISWRAPPER method to enable wireless support after which the computer is working fine.

Dunno whether anyone else has faced this issue or was it the problem with my system only, but i still, i thought people who use ubuntu a lot should know......

If anyone know what this issue was or whether i was worried because no potential reason please lemme know.
Regards
Rishi

---

### Post by intelligentfool on 2007-11-20
if you can upload the wireshark session i'll take a look. i might not be able to find a fix, but i should be able to find the cause.

---

### Post by Quoy on 2008-02-06
I've noticed this happening on my machine too. Just tried a different wireless card with a different chipset and it's still doing it as is my laptop. Guess it must be a bug. Will try ndiswrapper for it..

---

### Post by freeatlast on 2008-02-06
any resolutions?  i have the exact same issue

---

### Post by Quoy on 2008-02-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/189899](https://bugs.launchpad.net/ubuntu/+bug/189899) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm still fighting with ndiswrapper,tried a few different firmware files with the restricted manager still have the unsolicited packets. Do you think it might be a 64-bit issue? I've submitted a report.

---

