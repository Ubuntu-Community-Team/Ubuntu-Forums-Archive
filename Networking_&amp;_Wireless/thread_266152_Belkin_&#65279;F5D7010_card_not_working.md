---
title: "Belkin &#65279;F5D7010 card not working"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by DenKain on 2006-09-26
Ubuntu Version: 6.06

I installed the windows driver via ndiswrapper from my CD. The Windows Wireless Drivers tool says the hardware is present. I go into Networking and it says the card is not active. So I click on activate and it takes its time and says it is active. I click ok and it takes forever to close Networking. When I open Networking up again it says it is not active, the lights on the card never come on or blink.

---

### Post by neoroses on 2006-09-27
hey up mate, had thos problem as well but follow this guide, i no its for a differant card but it still works -: [http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide](http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide)

the only problem i have now is that i have to dectivate it then reactivat it everytime i turn on the pc :S

---

### Post by DenKain on 2006-09-27
I hate to say it but the information from that link/site did not work for me. When I type in "sudo ndiswrapper -i /home/user/Desktop/bcmwl5.inf"  it says "Installing bcmwl5". I type in "sudo ndiswrapper -l" and it say:
"Installed ndis drivers:
bcmwl5 invalid driver!".
This is when I use the driver from the CD and when I use the same driver from Dell's website. Any ideas?

---

### Post by bloodniece on 2006-09-27
Does your card have the Ralink or Broadcom chipset?
```
lspci
```

---

### Post by neoroses on 2006-09-28
just compleatly remove the driver then follow that guide again...it did that for me 2 but worked the second time round :)

---

### Post by Fitzcarraldo on 2006-10-07
*DenKain*,

See if the procedure in the following thread is of any help (my brother had a terrible job getting a Belkin F5D7010 card working in his Dell notebook PC):

[http://www.ubuntuforums.org/showthread.php?t=272813](http://www.ubuntuforums.org/showthread.php?t=272813)

---

