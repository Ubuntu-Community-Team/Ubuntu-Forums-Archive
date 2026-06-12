---
title: "Grub problem/question after updates today"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by Orographic on 2010-07-23
Hi all,

I've had a bit of a problem with some biggish updates today (around 80mb) for Lucid. Here is the message given during installation of updates and then what I did:

Message:

configuring grub-pc

GRUB Install Devices:

[] /dev/sda/ (500107mb, ST35004185)

[] -/dev/sda1 (489666mb, /)

'The Grub boot loader was previously installed to a disk that is no longer present or whose normally unique indentifier was changed for some reason. It is important to make sure that the installed grub stays in sync with other components such as the grub-cfg or with newer linux images it will have to load, and so you should check again, to make sure that GRUB is installed to the appropriate boot devices.

If you are unsure which drive is designated as boot drive, by your bios, it is often a good idea to install GRUB to all of them.

Note: It is possible to install GRUB to partition boot records as well, and some appropriate partitions are offered here. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore not recommended.'

I chose the first option '/dev/sda/...' and all seems well.

Does this sound right? I'm no expert with this. I think the problem may have been that some weeks ago I restored Lucid via Clonezilla to another identical drive but with a different identifier in this computer.

I can always re-install Lucid on this drive if needed.

Thanks all. :)

---

### Post by matrixblue on 2010-07-23
Use a live Cd then run **sudo grub-install**

---

### Post by Ozymandias_117 on 2010-07-23
You didn't actually say anything about having problems... Are you just trying to make sure that was correct before rebooting? If so, everything looks right based on what you've posted.

---

### Post by Orographic on 2010-07-23
> **Ozymandias_117 said:**
> You didn't actually say anything about having problems... Are you just trying to make sure that was correct before rebooting? If so, everything looks right based on what you've posted.

Thanks for the replies, I appreciate it. Not having any problems but to avoid them in the future with updates or Clonezilla restores, I wanted to just be clear on what I did from those more in the know.

Yes, perhaps I should have been more clear. I selected the first option in my first post, which is the only drive I have connected. 

I did a default install of Lucid originally so /dev/sda is the only place to install Grub, correct?

---

### Post by Ozymandias_117 on 2010-07-28
Yes. The only reason you would put it on /dev/sda1 is if you had a partition dedicated for grub, and you then wanted to chainload to your operating system. For normal operations, you want it on your MBR, which is /dev/sda. Sorry it took so long for me to post back.

---

