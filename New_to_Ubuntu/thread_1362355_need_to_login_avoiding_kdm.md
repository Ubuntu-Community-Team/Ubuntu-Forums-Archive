---
title: "need to login avoiding kdm"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by santiagorf on 2009-12-23
Hi all,
When I enter user/password via kdm, I'm kick back again to the login screen after a few seconds. If I choose, from kdm, to login from the terminal, it doesn't let me do it.

To solve the kdm login problem, I need to have access to the terminal. How can I start kubuntu avoiding kdm?

thank you!!!
santiagorf

---

### Post by lloyd_b on 2009-12-23
> **santiagorf said:**
> Hi all,
When I enter user/password via kdm, I'm kick back again to the login screen after a few seconds. If I choose, from kdm, to login from the terminal, it doesn't let me do it.

To solve the kdm login problem, I need to have access to the terminal. How can I start kubuntu avoiding kdm?

thank you!!!
santiagorf

Have you tried <CTRL><ALT><F2> to bring up one of the virtual consoles?  If not, give it a try and see if it will let you log in.

If not, your Grub boot menu should have a "Recovery" option - this will boot the system, leaving you logged in as root where you can fix whatever you need to.

And if all else fails, you can boot from the install CD, selecting "Rescue" mode.

Lloyd B.

---

### Post by bodhi.zazen on 2009-12-23
Your other option is to boot a live CD and access your HD from there, using chroot if needed.

Mount your Kubuntu partition at /mnt

```
sudo mount /dev/sdxy /mnt
```

where /dev/sdxy is your Kubuntu partition.

---

