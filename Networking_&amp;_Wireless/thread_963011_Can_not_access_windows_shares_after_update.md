---
title: "Can not access windows shares after update"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by Jakey The Avatar on 2008-10-29
I have media files shared on a Windows Vista machine.

I could access those files on my Ubuntu machine which I use to play them on the television

Today both Vista and Ubuntu recieved updates.

Tonight I cannot access any windows shares, on any of the three windows machines from either of my linux machines.

Worked fine yesterday...
nothing tonight.

---

### Post by dmizer on 2008-10-29
Check Vista for any new firewall or security features. Windows often resets/reconfigures/enables modified security settings after updates.

---

### Post by Jakey The Avatar on 2008-10-29
It's definitely a Vista problem.

I booted my windows machine into XP, and everything works fine there.

If anyone knows specifically what I should look for in Vista I'd appreciate it. I just upgraded last week and I haven't figured out where they hide all the settings.

Edit:
Oh, and thanks for the reply!

---

### Post by dmizer on 2008-10-29
Try looking here: [http://www.vistax64.com/vista-networking-sharing/100680-vista-firewall-port-445-a.html](http://www.vistax64.com/vista-networking-sharing/100680-vista-firewall-port-445-a.html)

---

### Post by Jakey The Avatar on 2008-10-30
Thanks for the link. Unfortunately, the material there did not provide a solution to my problem.

I posted a forum topic there, in the hopes that I can get this resolved.

Thanks again!

---

### Post by dmizer on 2008-10-30
> **Jakey The Avatar said:**
> Thanks for the link. Unfortunately, the material there did not provide a solution to my problem.

I posted a forum topic there, in the hopes that I can get this resolved.

Thanks again!

No problem. Good luck!

When you find the answer, please post back here.
Thank you.

---

### Post by Jakey The Avatar on 2008-10-31
Turns out I might have been the problem.

While I was having same problem with three machines running Ubuntu and the inablity to connect with the two machines running Vista, there may have been more than one reason.

My laptop, which connects wirelessly, was not connecting to my wireless network. I'm not sure why. I don't ever remember instucting it to connect to a different network, but it wouldn't be the first time I was up too late tinkering on the laptop and then couldn't remember what I had done the following day.

My media center was able to browse the shares by IP address (but not computer name) if I (correctly) entered the IP address in the file manager. I didn't even know this was an option until I started looking for solutions to my "problem". Since the first day I installed Ubuntu, I have always been able to freely browse all network computers and files simply by clicking on "Network" in the file manager.

However, I never managed to figure out why my Vista computers could not locate or browse the shared folders on the Ubuntu machines.

However, since installing Vista security updates yesterday, I no longer have any issues with any computers.

Admittedly this simultaneously frustrating and joyous.
On one hand I'm glad everything works the way it always had.
On the other hand I really wish I could figure out what exactly was causing all the problems.

---

