---
title: "WMP54gs Can't get it to work"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by bomb182 on 2007-04-25
I hate to post yet another thread. I have been working on t his now for a bout 6 hours, I have tried everything that I could find in the forums and other places, 
I have used ndiswrapper to no avail. 
I used to the drivers from my install cd. Went through the direction in another post.

"This is what I did:

I installed ndiswrapper-utils using the System->Administration->Synaptic Package Manager 
I inserted the CD that came with the card in the laptop 
In a terminal window, typed "sudo ndiswrapper -i /cdrom/lsbcmnds.inf" (you must be root) 
If everything goes OK, if you type "ndiswrapper -l" you should see the newly installed driver 
Then I typed "sudo ndiswrapper -m" to make this driver load every time the machine boots up (that's what I understood that the thing did... maybe I'm wrong!) 
Then I typed "sudo depmod -a"; if no errors appear, then everything is OK 
Then I typed "sudo modprobe ndiswrapper" which loads the module in memory, right now."

That didn't work. I don't know what esle to do, This is my first linux try, and I would really like to give Ubuntu the try that it deserves

Any help at all would be greatly appreciated

---

### Post by kevdog on 2007-04-25
Can you post the output of:

```
lspci 
```

Thanks

---

### Post by bomb182 on 2007-04-25
This is the card that I have Sorry i can't post the exact out put I have to reboot back and forth right now as This is my only machine.

Broadcom  BCM 4318 airforce one 54g Rev 02

---

### Post by bomb182 on 2007-04-26
Ok found the info I needed in another thread thanks for the reply anyway

---

