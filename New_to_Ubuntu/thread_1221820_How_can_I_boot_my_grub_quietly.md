---
title: "How can I boot my grub quietly?"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by 311005901 on 2009-07-24
I am triple booting OSX, Jaunty, and Vista with rEFIt controlling the boot. When I select OSX or Vista from the rEFIt menu, it boots directly into that OS. When I select Jaunty, a GRUB window like this comes up:[IMG]http://tugulab.files.wordpress.com/2008/02/grub_prima_t.png[/IMG]
It's a bit of a hangup. I don't really care which version of the kernel I'm loading, I just want to boot Jaunty.

Is there a way to simply boot to Jaunty without seeing this menu? I've done it before, but I'm scared to copy and paste the wrong command and mess up my triple boot.

If anyone has the command that would be greatly appreciated. :popcorn:

---

### Post by drs305 on 2009-07-24
I think with your boot setup when you are in Jaunty you should be able to tweak the menu.lst file with StartUp-Manager. The command line/terminal is nothing to be afraid of, but there is a gui app called StartUp-Manager than can edit grub's menu for you. It has lots of tweaks and it's all done via a nice gui interface (for grub legacy). Click on the "SUM" link in my signature line to go to a guide on how to install and run SUM. 

It can set the kernel you want to use and the timeout period you 
want. Personnally, I'd leave the display at 1 or 2 seconds so you have a chance to interrupt it if that becomes necessary.

---

