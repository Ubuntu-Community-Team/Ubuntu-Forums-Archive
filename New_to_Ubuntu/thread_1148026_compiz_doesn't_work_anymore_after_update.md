---
title: "compiz doesn't work anymore after update"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by sneakyB on 2009-05-03
hi all,

after the upgrade, which I almost regret now, my wifi and compiz are not working anymore.

I think something got messed up with my drivers or so, not sure(very new to all this)

anybody any advice on the compiz?
the app is still there, but just won't launch...

thanks

---

### Post by lavinog on 2009-05-05
What video card do you have?
What are the symptoms?
can you post your /var/log/Xorg.0.log

---

### Post by sneakyB on 2009-05-05
bert@bert:~$ /var/log/Xorg.0.log
bash: /var/log/Xorg.0.log: Permission denied

is what I get... :s (I'm very new to all this)

is this of any help?


bert@bert:~$ sudo lspci |more
[sudo] password for bert:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controlle
r Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Grap
hics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Control
ler #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
(rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (r
ev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (r
ev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (r
ev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
bert@bert:~$ 


the compiz is not launching at all, and I also notice that minimizing windows etc is slow and not the way it was on 8.10


thanks for the help

---

### Post by sneakyB on 2009-05-05
found the solution here: [http://ubuntuforums.org/showpost.php?p=4202892&postcount=6](http://ubuntuforums.org/showpost.php?p=4202892&postcount=6)

works like a charm again

---

### Post by lavinog on 2009-05-05
glad it works.
Sorry about not explaining how to post Xorg.0.log
cat will output a file to the screen
```
cat /var/log/Xorg.0.log
```
you can also use **less** in place of cat to make it easier to scroll through the text.

also it is better to post the output inside code tags
```
 this is code 
```

---

