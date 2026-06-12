---
title: "Stuck On Loading Screen (Ubuntu 11.04)"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by unknowngal on 2011-04-30
Hi...another issue. :P Ubuntu is stuck on the loading screen and doesn't go beyond that. The only way I'm able to get into it is by accessing what I guess is Ubuntu's "safe mode" (where I am now).

If this helps at all: I got into the menu that allows for this safe mode to run and ran some repair/update packages (grub and something else, I forgot, sorry x_x), and that gave me the Ubuntu loading screen but nothing else.

***Before that***, all I had was a black screen and a lot of white text. What I caught towards the end of that was something about guard-dog firewall not being found, or something like that (I can't remember). I had installed guard-dog a while ago on Ubuntu 10.10, but then uninstalled it. I hadn't had any issues with that before this.

Thank you for any help. ^^;;

---

### Post by unknowngal on 2011-04-30
...*wondering why she didn't just stick with version 10.10*  If this new version of Ubuntu ends up being too buggy, is there anyway to downgrade back to 10.10? Or is there a more stable Ubuntu-like OS, like Kubuntu or Xubuntu? Maybe Debian or Fedora? Thanks again. ^^;;;

---

### Post by abnordude on 2011-04-30
> **unknowngal said:**
> ...*wondering why she didn't just stick with version 10.10*  If this new version of Ubuntu ends up being too buggy, is there anyway to downgrade back to 10.10? Or is there a more stable Ubuntu-like OS, like Kubuntu or Xubuntu? Maybe Debian or Fedora? Thanks again. ^^;;;


I dont know the solution to your problem.
But if you need to switch to a more ubuntu like OS.
Then I'd recommend linux mint.

---

### Post by Linux&amp;Gsus on 2011-04-30
AFAIK you can't downgrade, other then re-installing 10.10
I have no problem with Kubuntu. Have not made th switch though, to 11.04 yet. But it sure is a less radical change in KDE then it is with Gnome.

---

### Post by unknowngal on 2011-04-30
Thanks, abnordude and Linux&Gsus, I'll be checking those two distributions out. :) Though if there's still hope for my Ubuntu, I'm ready to tackle the issue. :3

---

### Post by unknowngal on 2011-04-30
Anybody? XD I'd really like to see if my Ubuntu can get fixed before I decide to just install Linux Mint over it instead. ^^;;

---

### Post by unknowngal on 2011-04-30
*headdesks* I guess I could just try out Linux Mint instead. ^^;;;

---

### Post by Meeyotch on 2011-04-30
Need more info. Do you have an nvidia graphics processor? 

If you made it to safe mode, chances are good it is a graphics issue. Good, not definite. 

Just to warn you, you may be in for as much of a headache with another distro. Since you have already gone this far with Ubuntu, might as well keep going

---

### Post by unknowngal on 2011-04-30
> **Meeyotch said:**
> Need more info. Do you have an nvidia graphics processor? 

If you made it to safe mode, chances are good it is a graphics issue. Good, not definite. 

Just to warn you, you may be in for as much of a headache with another distro. Since you have already gone this far with Ubuntu, might as well keep going

Just here to close some threads since I did end up switching to another distribution. *sheepish* For the time being anyway. :P I did end up getting into a big headache though, eh heh. ^^;; But we'll see how it works out. I may just end up coming back to Ubuntu...or installing it and having THREE OS on my computer...if I can't figure out what to do regarding merging partitions and I end up stuck with free space I can't do anything else with. :P

Thank you though for your reply! :)

---

### Post by dezzie-boy on 2011-05-13
Shamefully, this problem was not solved. I had a similar problem this morning on my Ubuntu 11.04 64 bit machine.

The grub worked fine, but I could not access the recovery system and the system would become stuck on the loading screen. It turned out it was not directly a monitor issue or a USB BUS issue. I loaded up Ubuntu from a cdrom, after several attempts, and tried mounting the hdd with the operating system installed, which returned an error. It is a ext4 drive under /dev/sda1

Running fsck.ext4 /dev/sda1 checked the filesystem for errors. It returned a few hundred block errors which were then fixed. Rebooting the system Ubuntu loaded fine.

I think this problem may have stemmed from my bad habit of hard-powering off.

---

