---
title: "Grub"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by damnupdates on 2011-05-06
ok i have been having some issues with startup-manager.
I am on 11.04 and i wanted it too boot directly to windows vista, so i set it to that option. 
when i restart my laptop it get in to grub and windows vista recovery is highlighted. so i tried again, i made sure that windows vista was selected and not vista recovery and i got same results. 
so i thought if i can beet it join it. i tried setting recovery as my default boot up operating system. now when it was restarted grub has ubuntu first option selected. 
is there any way to do this manually were it will do it correctly?

---

### Post by launchy on 2011-05-06
try this: restart ur system and locate what position ur windows vista is from the grub list so staring from top is 0, 1, 2 etc .. say ur windows vista is number 5 on the list then edit ur grub in a terminal type sudo gedit /etc/default/grub

then replace "GRUB_DEFAULT=0" with "GRUB_DEFAULT=5" 5 being its position on the grub list. run sudo update-grub then restart ur system. more info here [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by damnupdates on 2011-05-07
thank you. that was both easy and fast. think it can be marked as resolved.

---

### Post by Dutch70 on 2011-05-07
Yes, please mark it solved if you're satisfied. 

Just so you know, there is a program called Grub Customizer that you may be interested in. It's in the repo's.
[[COLOR="Red"]HOWTO: Grub Customizer[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1664134&highlight=grub+customizer")

---

