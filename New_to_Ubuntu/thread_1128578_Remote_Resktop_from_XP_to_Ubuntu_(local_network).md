---
title: "Remote Resktop from XP to Ubuntu (local network)"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by zcacogp on 2009-04-17
Chaps, 

I've built a Ubuntu machine, on my desktop computer. It runs. (It runs very slowly, but that's a different matter and there is another thread running about that. ;) ) 

I also have two lappies, both running XP. I use Remote Desktop alot to connect from one machine to another within the network. 

I have managed to connect from Ubuntu to an XP machine very easily (remarkably easily actually). And very nice it was too >ReachesForBeer<.

Things get trickier when I try to go the other way; from XP to Ubuntu. I have enabled Remote Desktop on the Ubuntu machine, set a password I need to enter when connecting remotely and set such that it doesn't need permission from the Ubuntu machine to connect. 

I downloaded UltraVNC onto one XP machine (tried viewer only AND the whole installation), and run it, pointing it at 102.168.10.6 (IP of the Ubuntu machine), but get the error "Failed to connect to server!"

I have tried both wireless and with the network cable plugged in (to the XP lappie), and it makes no difference. The lappie definitely is on the network, and I can ping 192.168.10.6 from the lappie (and the reverse - pinging 192.168.10.8 from the Ubuntu machine.) Both work fine. 

I have tried it with the firewall on the XP machine turned off as well as on. It makes no difference. 

(I have yet to try the other XP machine to see if it makes any difference.)

Any suggestions? All welcome. I am aware that I have provided very little troubleshooting information here; tell me what to test and I'll post up the results. 

Thanks. 


Oli.

---

### Post by bodhi.zazen on 2009-04-17
Sometimes you need to specify the port in the ip address,

so : 192.168.10.6:5900 or 192.168.10.6:0

---

### Post by zcacogp on 2009-04-18
Bodhi, 

Thanks ... I've now tried that (both for 0 and 5900, and both with one ':' and with two '::'s), and now tried it on the other XP lappie as well, and no joy. 

I have specified on the Ubuntu machine that Remote Desktop should use port 5900, so I know that's correct. 

I have tried using the following in Terminal on Ubuntu (don't know how to make this display in boxes, sorry): 

sudo apt-get install vino
 
and: 

/usr/lib/vino/vino-server


... which tells me that vino server is installed and working as it should. But I still can't connect. 

Should I be setting the workgroup on the Ubuntu machine to be the same as on the XP machines? (I don't know whether "Workgroup" is a concept that has any meaning in Ubuntu, although I can make remote desktop work the other way - i.e. from Ubuntu to XP without needing to enter a Workgroup.) 

It almost feels as if there is a firewall getting in the way, although this is tried with the firewalls on the XP machines off. (Is there a firewall in Ubuntu which I should be turning off? I am using I.Ibix.) 

Thanks for your help. 


Oli.

---

### Post by zcacogp on 2009-04-19
Anyone have any ideas? 


Oli.

---

### Post by zcacogp on 2009-04-19
OK. It now works. 

I don't understand why, but having the "Only allow local connections" box ticked in the "Advanced" tab of "Remote Desktop" prevented any connection being formed from Ultra VNC on XP. 

Unticking the box made it all work as it should. 

I don't understand why this is so, but I am happy that it now works. 

Thanks Bodhi for your input. 


Oli.

---

### Post by halitech on 2009-04-19
```
Only allow local connections
```

in this case, local really means local as in the system that it is running on. You have to remember, *nix is built from the ground up as a network OS so to it, local network means the connections inside itself because everything operates as a network. With that checked, it thinks its only supposed to allow connections from the local system, not the LAN.

---

### Post by zcacogp on 2009-04-19
Halitech, 

Thanks. That makes sense. Well, it makes sense now you explain it - for someone who (hiterto) has XP drummed into them it didn't make any sense at all at first! 

Only slight snag (and it may be insurmountable) is that the Remote Desktop connection won't fit on the screen on the lappie. Lappie is running 1024x768 (it's an ultaportable with a small screen), and the desktop (Ubuntu machine, which is being remote-d to) is 1680x1050. When you use "Remote Desktop", the display on the remote machine either needs scrolling around to see the edges of the screen, or you can set it so that the whole screen is visible, but at such a small size as to be pretty much useless. When you use Remote Desktop from XP to XP, the displayed screen re-sizes to something sensible; not so when going from XP to Ubuntu. Is there any way 'round this, or is this one of the bugbears of remote-ing across screen size and operating system? 

Thanks again. 


Oli. 

(I hope that explanation made sense! Do ask if it sounded like gibberish - and I apologise if it did!)

---

### Post by halitech on 2009-04-19
no worries, didn't make sense to me either at first until I did some reading on it :)

I remember reading a way of passing screen sizes to remote connections using vnc but I don't recall exactly how or what the settings were and I don't know if it would be the same with remote desktop or not.

---

### Post by zcacogp on 2009-04-19
I may be barking up the wrong tree here, but I suspect that it would be difficult to arrange the passing of screen sizes as when you do the Remote Login thing, the screen on the Ubuntu box carries on displaying. 

If you were therefore to try and display that screen at a different aspect ratio (on the remote computer) then you would have a problem - the same information is being displayed at two different aspect ratios. OK, that wouldn't be *impossible* to arrange, but it would make things a smidge trickier. 

On XP this problem doesn't happen as the machine being connected to locks-up, and you cannot see what is happening (the screen just says something like "I'm locked, push off." Or words to that effect.) 


Oli.

---

