---
title: "Did Ubuntu f`cked up my laptop?"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by j_penac13 on 2009-02-20
Hey guys!
Im new to Ubuntu. I installed it like 2-3 days ago. At that time, it was great. Better than Vista, I gotta say. 
BUT, today, I was using Ubuntu and then I noticed I needed to use a windows program, so I click on restart so I can go to the Vista partition.
Now, what happened next is that the laptop never started up. Not even the HP logo that loads at start.

So, I was wondering, was it Ubuntus fault? I noticed that when I restart/shut down while in Ubuntu, the laptop turned off as If I manually turned it off.

I have a HP Pavilion dv6000z CTO. With AMD Turion X2 Dual Core 2.0 GHz, 2GB RAM, NVIDIA GeForce 6500.

Hope you guys give me your thoughts about this :)

---

### Post by jahhulbert on 2009-02-20
If your HP logo isn't showing that seems like something in the BIOS is messed up. Ubuntu should only mess with your hard drive (partitions, partition table, and mbr) I would assume...I've never had any linux distro that could screw up the bios.

Should not be Ubuntu's fault. I guess just make sure the battery is all the way out and its all the way off then try it up again.

---

### Post by gymophett on 2009-02-20
This sounds more like a hardware problem. Mine did that too. My ram got burned out actually. But it could be your BIOS.

---

### Post by j_penac13 on 2009-02-20
I contacted HP and they say its a problem with the dv6000 series. So, no blame to Ubuntu :)

Anyways, that really made me think. When I used Ubuntu, the laptop turned off as if I was the one turning it off pushing the power button (the "wrong" way of turning off a computer). 
So, Im wondering, is that normal? Cuz that may be a factor of why the board f*cked up :S

---

### Post by HammerOfDoubt on 2009-02-20
Definitely not normal. I've put Ubuntu on 5 machines. It always goes through a shut down process.

---

### Post by jerome1232 on 2009-02-20
I'm really not sure what you mean, that's just how computers shutdown, When you tell Ubuntu to shutdown it'll stop running services, unmount the disks and shutdown the computer. The only reason just powering off a computer suddenly while it's working is bad is because you could halt it while it was in the middle of writing to disc and you end up with a corrupted and inconsistent filesystem, which can cause data loss, it doesn't physically harm the computer.

---

### Post by j_penac13 on 2009-02-20
> **jerome1232 said:**
> I'm really not sure what you mean, that's just how computers shutdown, When you tell Ubuntu to shutdown it'll stop running services, unmount the disks and shutdown the computer. The only reason just powering off a computer suddenly while it's working is bad is because you could halt it while it was in the middle of writing to disc and you end up with a corrupted and inconsistent filesystem, which can cause data loss, it doesn't physically harm the computer.

So, anyone can turn off their computers through the Power button any time they want, it wont hurt the hardware, but it will corrupt the filesystem?
If thats so, then I guess, Ubuntu had no participation on the damage of my laptops board. Thank you for clearing this up for me.

---

### Post by trlkly on 2009-02-20
On most computers that exist today, the power button (by default) does exactly the same thing as clicking shutdown. But it can cause problems on older computers.

---

### Post by HammerOfDoubt on 2009-02-20
> **jerome1232 said:**
> I'm really not sure what you mean, that's just how computers shutdown, When you tell Ubuntu to shutdown it'll stop running services, unmount the disks and shutdown the computer. The only reason just powering off a computer suddenly while it's working is bad is because you could halt it while it was in the middle of writing to disc and you end up with a corrupted and inconsistent filesystem, which can cause data loss, it doesn't physically harm the computer.

I think he meant that it would shut down _as if_ he had just shut it off "the wrong way".

---

### Post by halitech on 2009-02-20
I've got a Toshiba satelitte 1800 laptop that will not reboot if I select the reboot option but works fine if I do a shut down. I don't remember where I found it but it was/is a bug in the kernal that doesn't reboot it the way its supposed to. It goes throught the shutdown and the lights stay on and requires me to hit the power button to actually turn it off. Not sure if this is the same issue you have or not.

---

