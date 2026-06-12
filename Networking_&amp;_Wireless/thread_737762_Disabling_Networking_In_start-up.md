---
title: "Disabling Networking In start-up"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by und3rgnd9er on 2008-03-27
I RECENTLY THOUGHT I COULD NETWORK MY HOME MADE PC(ASUS MOBO) TO A MAC. Big problems. I could actually control the PC with the Mac. Nice feature but not needed for my uses.

I created a network with the Ubuntu PC machine and the Mac. My basic problem is that I somehow locked the PC's HDD a( WesternDigital 500gb). 

The MOBO is fine and everything is operational. How I know is that on a separate HDD I have the same Ubuntu just none of my programs and files. I can access these files but it time consuming and would rather get all my hard work back. 

I ran the boot grub and it stops at the Networking part. If I could disable the networking on start-up then i would be able to log in and change the settings and hopefully continue using my favorite programs and whatnot

questions-

1) How to either disable the networking for a one time boot or fully disable until later changed:confused: 

2) Any sudo codes or links would be helpful.

3) Yes i'm a newbe and i know i royal messed myself with this project lol.

Thanks everyone for any help!

---

### Post by diegosouza on 2008-03-27
1) I think there are many ways to do it. The main script is /etc/init.d/networking, The default is it starts with S and stops with runlevels 0 and 6. Read more about upstart, runlevels, system v init.

The command i manage it on debian systems is the update-rc.d. So: $  man update-rc.d  :-)

If you turn off the exec permission to /etc/init.d/networking i think your network doesn't up. 

2) [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers) and [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good luck and send us a reply.

---

