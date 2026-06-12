---
title: "touchpad gets stucked"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by eskararriba on 2009-01-15
hi everybody,

I ve got a problem with my touchpad (on my HP pavilion dv2000, ubuntu 8.10) -  when I connect my external hard drive the touchpad stops working properly and just gets really slow, freezing every now and then for a second or so.
even when I disconnect the hard drive it only sometimes gets better. 


thanks for your help, cheers

---

### Post by cmnorton on 2009-01-17
Start by looking at /proc/interrupts by entering this command cat /proc/interrupts
to see if there is a conflict between the disk and touchpad.

Check your logs under /var/log

and talk with the hardware manufactuer.

---

### Post by seagullplayer77 on 2009-01-17
There's a program for controlling touchpads...I think it's called "gsynaptic" and you can get it by doing an apt-get or by using Synaptic. I'm not sure it would help in your particular case, but it's always worth a shot!

---

### Post by eskararriba on 2009-02-01
hey,

thanks for your replies and sorry for not responding, but I was too busy lately. 
the problem only occurs when I connect the external hard drive, so I don't think gsynaptics would do any good. 
on the other hand, I didn't really understand where and how to put the commands you mention - the terminal doesn't accept them; sorry, I'm rather new to linux.

thanks again

---

