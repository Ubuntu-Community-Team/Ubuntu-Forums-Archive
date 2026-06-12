---
title: "How to add and edit files on ubuntu from windows computer?"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by RadiationHazard on 2009-02-26
I have just set up a LAMP server on a computer using Ubuntu. This is an old computer and I just basically want to stick it in the closet and be able to edit my site but not have to have a monitor or anything for it. It's connected to the same Internet as the computer I will be using to control this one. How would I do what it is that I'm wanting to do?

Thank You for your time and all help offered! :)

---

### Post by taurus on 2009-02-26
You need to install sshd (ssh server) so you can connect to your box/server from whatever machine you happen to be using.

---

### Post by smani on 2009-02-26
Enable remote-desktop under system->preferences and then on the windows box use vncviewer (you can download it from [www.realvnc.com](www.realvnc.com)) to connect to the linux box. You will then be able to display the screen of the linux box on your windows box's screen.

---

### Post by RadiationHazard on 2009-02-26
also is there a way that I can turn it off and on from my other computer? I will be keeping this computer in a back room on the other side of the house and I don't want it always on.

---

### Post by taurus on 2009-02-26
Turn it off (shutdown -h now), yes.  But I am not sure if you can turn it back on without physically there, pushing the on button.

---

### Post by halitech on 2009-02-26
off is no problem, turning it on remotely is going to be tricky if not impossible. Only thing I can think of to turn it on would be using WOL which is enabled (normally) in the BIOS. far as turning it off, just remote in and use the shut down command.

---

### Post by thtrgremlin on 2009-02-26
[http://packages.ubuntu.com/intrepid/etherwake](http://packages.ubuntu.com/intrepid/etherwake)

Etherwake is great for booting wake on lan compliant computers (most are) when you enable it in their bios. note that you use the hardware address to boot, and wake on lan packets are not routable (though you could ssh into a computer that is on in the same local network and wake computers on its network if, say, you are away from home)

I typically use 'sudo init 0' to shut down from CL myself.

cron jobs are useful for doing that stuff automatically too. You can also have one computer on that can boot up and shut down computers on a network automatically as necessary  :) I am sure you can imagine all the possibilities.

---

### Post by halitech on 2009-02-26
something just popped into my mind, why would you run a LAMP server if you didn't want it on all the time?

---

