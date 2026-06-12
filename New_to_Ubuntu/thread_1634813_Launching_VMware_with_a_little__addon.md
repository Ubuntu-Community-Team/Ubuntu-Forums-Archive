---
title: "Launching VMware with a little  addon"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by DDemir on 2010-12-01
I need a little bit of advice:

History: I have an old all in one HP3150 printer and I lost the ability to print when I switched from WinXP to Win7. Then I discovered Ubuntu and now I run 10.10 and learning.
This damned printer does not know PCL nor anything else so I could not make it run in Ubuntu either. :(

The only way I could revive my old HP3150 was to install a VMware Player WinXP as a guest. It did not print from the very beginning but after some (rather long) research I found a solution: I have to tell Ubuntu to drop the lp completely and only after that the winXP guest is able to print.
In order to do that I need to run in terminal  a small command:

$ **sudo modprobe -r lp** 
Here is the link for the explanation:
 [http://www.brandonhutchinson.com/wiki/VMware_Player_in_Ubuntu](http://www.brandonhutchinson.com/wiki/VMware_Player_in_Ubuntu)

All good so far but now I would like to add this lifesaver line somewhere in the VMware launcher so I don't have to type it every time in the terminal before I start the virtual machine.

What would be the best method and where would be the best place to squeeze this line so I can start the virtual machine from the gnome application menu after I drop the lp process.

Since the significant other will want to print with little hassle I would prefer to integrate this somewhere so that once I launch the VMware she won't have to go through terminal, command line, etc. 

Thanks in advance!

---

