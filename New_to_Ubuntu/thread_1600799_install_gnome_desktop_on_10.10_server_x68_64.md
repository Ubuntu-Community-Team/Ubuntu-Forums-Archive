---
title: "install gnome desktop on 10.10 server x68_64"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by Ztoragefool on 2010-10-19
hello, 

did a lot of testing on 10.04 server concerning kvm - and found it somewhat disappointing. so i decided to give it a last shot on brand new 10.10. 

now my problem is i get a dead console after i have installed gnome via the ubuntu-desktop package. for a tenth of a second, i see the pink wallpaper, then the screen turns black, only showing the mouse pointer. no response on mouse or keyboard actions, strg-alt-f1 or -backspace or even toggling num lock - no reaction. the remaining system works fine, i can use ssh, cpu is idle, no probs but the dead console. 

installing ubuntu-desktop package worked amazingly well on server 10.04 on the same machine. 

now since i read read a lot about things changed concerning X configuration - which is the right way to get 10.10 mousing?

edit: i should mention i tried to fix this following some google links, but i´m really confused which way X is configured since 10.10... none of those well-known files seem to be there, like /etc/X11/xorg.conf is missing and files supposed to be under /usr/lib/X11 are missing too.

so i hope somebody could point the right way to troubleshoot this under 10.10... please?

---

### Post by cariboo on 2010-10-19
Hardware details would help, especially graphics adapter.

Also on a server, I would suggest a lighter-weight desktop like LXDE

---

### Post by Ztoragefool on 2010-10-19
yeah, right, my hardware:
  - amd x3 3ghz
  - quite new am3 mainboard
  - ati hd 4250 onboard graphics
  - 4gb ram
  - logitech usb mouse
  - ps2- and usb keyboard, same problem

lxde - i considered so, but as i regard this as my "finally getting wet with linux" project, i´d like to go with the flow at first.

---

