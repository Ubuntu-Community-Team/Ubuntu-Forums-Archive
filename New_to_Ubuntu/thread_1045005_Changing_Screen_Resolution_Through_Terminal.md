---
title: "Changing Screen Resolution Through Terminal"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by shaikdaddy on 2009-01-20
Hey all,

I'm very new to Ubuntu.

I'm running it on VMWare on a Macbook Pro and it defaults to show it in a standard screen view, not widescreen, leaving large black bars at either side of my screen during full-screen mode.

I found the screen resolution tool in the system menu, but unfortunately, I changed it by mistake to a resolution that does not allow me to view the window that opens fully.  In fact, it cuts off the bottom, not allowing me to press "apply" to the correct resolution.

I cannot resize it, move it, or press tab+enter to get the right button (for some reason...tab to cancel works fine).

Is there a way to change resolution in terminal, or to restore the display defaults (either one) so that I can use it again.  Right now, its almost unviewable.

Ben

---

### Post by diablo75 on 2009-01-20
You'll probably have better luck asking this in the Virtualization forum.  It's been a while since I used VMware, but they can probably tell you have to install the VMware Tools add-on in Ubuntu which will enable automatic resizeing (which will change your resolution to match the size of the VM window you have Ubuntu running in).  Providing that there is such an add-on available for Linux (I'm not sure if there is... there probably is though).

---

### Post by iaculallad on 2009-01-20
Using the terminal to change the screen resolution real-time:

```
sudo xrandr -s <x-res> x <y-res>
```

---

### Post by shaikdaddy on 2009-01-20
problem solved itself with a restart I guess...it works now.

I will make my way over to the virtualization forum to see what they have to say...


Ben

---

### Post by Jetro on 2013-03-20
Well I'm having big problems here as well. When I installed the - apparantly tested - nVidia drivers, the resolution went back to a horrible 640 x 480 or even smaller. You can't almost navigate at all. 
Just like the OP, I can't change the resolution and then select "Apply" or whatever it should say there. I see resolutions up to 1024 x 768 is supported, but when I try to do iaculallad's command in the terminal, this comes back: 
```
bash: syntax error near unexpected token `1024'
```
Or change 1024 for any number.

---

### Post by sandyd on 2013-03-20
**Necromancing - Thread Closed**

Please do not post in threads more than one year old as many things change between ubuntu releases

Thanks!

---

