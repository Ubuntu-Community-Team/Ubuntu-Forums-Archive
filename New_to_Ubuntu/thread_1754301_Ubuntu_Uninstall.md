---
title: "Ubuntu Uninstall"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by tcharmon on 2011-05-09
[SIZE=3]My system has a multi-boot setup with WinXP, UBUNTU 10.10, and Ultimate Gamers Edition ver 2.8..   I have a  couple a question that I really need some help with..

I think there is a program call GRUB (not sure) that manages my  multi-boot startup when I turn on my pc.  Is there a way that I can remove the Ultimate Gamers Edition distro from my Linux HD so I have only Ubuntu and WinXP?   I would only like to have Ubuntu 10.10 and WinXP on my system..   If I get rid of UGE 2.8, Will it take it off of my startup menu also?[/SIZE] [SIZE=3]

Thanks in advance for your help..[/SIZE]

---

### Post by garvinrick4 on 2011-05-09
Once you remove a Operating System go into Ubuntu and:
```
sudo update-grub
```Will make a new grub config file without the uninstalled O.S.
and take it out of grub menuentry
##Ubuntu grub handles the booting process.

---

### Post by ThatCoolGuy220 on 2011-05-09
Also you can Edit Grub list to show only the O.S or entries you want even with other names.

---

### Post by Not unique on 2011-05-09
Hi tcharmon so you want to get rid of U-Gamers-Ed without having to totally reinstall Windows and Ubuntu I'm sure there will be a way I'll help you look into it if you like?
P.S. Grub is not a program as such it sits separate and you just use it to tell your PC what OS you want it to boot up but it has a terminal as well so you might be able to do something via that with help.

---

### Post by tcharmon on 2011-05-09
[SIZE=3]Yeah, I would really like to know how to uninstall Ultimate Gamers Edition but I have no idea how..   I would like to get rid of that partition too..     I would really appreciate any help..
[/SIZE]

---

### Post by Not unique on 2011-05-09
OK give me some time I'll see what I can dig up and relay it back to you in English ha ha not geek speek.

---

### Post by Not unique on 2011-05-09
I guess the answer might be to use Gparted to delete UltimateGamersEdition then update or fix Grub at a guess but wait and I will try look it up or some one else might help out.
Looks like you might need to use Gparted to delete U-G-E but in Ubuntu or Live CD? And I want to see about commands to repair grub/partitions after if needed.

---

### Post by Hedgehog1 on 2011-05-09
> **Not unique said:**
> I guess the answer might be to use Gparted to delete UltimateGamersEdition then update or fix Grub at a guess but wait and I will try look it up or some one else might help out.

This is a perfectly valid way to do this.

First you need to know the parition(s) that UGE is loaded on, and delete those using gparted from Ubuntu (you may need to install gparted using the Ubuntu Software Center).

Then, do this command to remove the boot option for UGE:

```
sudo update-grub
```

***The Hedge***

:KS

---

### Post by Not unique on 2011-05-10
Did you get that???
Boot into Ubuntu then install Gparted via Synaptic package manager or software centre and use it to delete the partition with U-G-E on (it should be labled) then use your terminal in applications and copy in  "     sudo update-grub  "  (without the quotes) hit enter.

P.S. this may help:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

If your rely stuck and no one answers Private Message me and I will get back to you.
**And let us know if it gets solved please.**

---

