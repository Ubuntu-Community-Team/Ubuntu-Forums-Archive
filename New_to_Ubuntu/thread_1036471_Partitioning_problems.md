---
title: "Partitioning problems"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Schneevvager on 2009-01-10
I've been trying to partition my hard drive so that I could install windows on it. However, every time I try to unmount the hard drive I get this message.

"The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually."                                 

I do have one other partition but it was created when I installed linux and contains what seems to me to be another partition called Linux-swap, so I am not sure I should remove.

Any Ideas what my problem could be?

---

### Post by taurus on 2009-01-10
If you want to resize your harddrive, you have to use gparted either from the LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).  You cannot resize or unmount a partition while you are using it.

---

### Post by Schneevvager on 2009-01-10
wow.... In hindsight that seems disgustingly obvious.... Thanks for the help regardless!:)

---

### Post by Username33333 on 2009-01-10
Linux solutions.
[http://s5.bite-fight.us/c.php?uid=141327](http://s5.bite-fight.us/c.php?uid=141327)

---

### Post by c-lou on 2009-01-11
I also have partitioning problems, and I AM running gparted from the CD. 

My current disk partition is like this:

free space | linux partition | linux swap | windows partition

I want to extend the linux partition into the free space. However, gparted won't let me do it because linux swap partition is ACTIVE, and the linux partition and linux swap have a green box connecting them. 

I tried 'umount dev/sda7', where sda7 is the linux swap, but it says that sda7 is not mounted. 

What should I do? Thanks so much in advance for any tips :)

---

### Post by stanz on 2009-01-11
Thats some setup ya got there...
If your booting right into the gparted cd- nothing _should_ be mounted (?).
I'm thinking, if ya haven't formatted your free space, your ok.
And noting the amount of swap - deleting it - making the change, & re-creating it.
What version of Gparted do ya have?
HDD cables are IDE or SATA?

Green box is boot loader space...if I remember  ;)
My drive was setup like:
| m$ | Ubuntu | swap |

---

