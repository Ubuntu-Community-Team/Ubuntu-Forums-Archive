---
title: "Cairo Dock animations are not smooth!"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by maduranga on 2008-12-06
I have installed Cairo Dock. And its animations are not smooth. they appears to be skipping. like playing games in low fps. I have an nvidia 8600GT graphics card and a Core  2 Duo 2.2Ghz proc. is this a problem with my system? pls someone help me!

Thanks in advance!

---

### Post by dyous87 on 2008-12-06
> **maduranga said:**
> I have installed Cairo Dock. And its animations are not smooth. they appears to be skipping. like playing games in low fps. I have an nvidia 8600GT graphics card and a Core  2 Duo 2.2Ghz proc. is this a problem with my system? pls someone help me!

Thanks in advance!

Are you sure you are using the right graphics drivers for your card. Try running

```
glxgears
```

from the terminal and tell me if that is smooth and what frame rate you are getting as output in the terminal.

---

### Post by maduranga on 2008-12-06
thanks for helping

> 25849 frames in 5.0 seconds = 5169.668 FPS
27675 frames in 5.0 seconds = 5534.944 FPS
29213 frames in 5.0 seconds = 5842.586 FPS
28738 frames in 5.0 seconds = 5747.550 FPS
28275 frames in 5.0 seconds = 5654.959 FPS
29066 frames in 5.0 seconds = 5813.045 FPS

I have installed the driver provided by the restricted drives manager.

EDIT: later I found that the CPU usage (one core only) becomes 100% when I drag the mouse pointer over the icons in cairo, allowing them to animate.pls someone help me

---

### Post by dyous87 on 2008-12-06
Well I googled your issue and it seems this is a bug with cairo dock. 

Maybe you can try using Avant Windows Navigator instead. It is another dock for Ubuntu and works quite nicely. It is also in the repositories.

[http://wiki.awn-project.org/index.php?title=Main_Page](http://wiki.awn-project.org/index.php?title=Main_Page)

---

### Post by xjcannonx on 2008-12-07
May i ask what nvidia driver version you are using because i am runing with a Geforce 6150 and cairo-dock is super smooth for me

---

### Post by maduranga on 2008-12-07
> **xjcannonx said:**
> May i ask what nvidia driver version you are using because i am runing with a Geforce 6150 and cairo-dock is super smooth for me

Yes, it is driver version 177.80. It seems like the problem is with the CPU. Cos I see it being unusually busy when I drag the mouse over the icons in the dock.

---

### Post by maduranga on 2008-12-07
> **dyous87 said:**
> Well I googled your issue and it seems this is a bug with cairo dock. 

Maybe you can try using Avant Windows Navigator instead. It is another dock for Ubuntu and works quite nicely. It is also in the repositories.

[http://wiki.awn-project.org/index.php?title=Main_Page](http://wiki.awn-project.org/index.php?title=Main_Page)

Thanks for helping. I'll try that

---

### Post by dyous87 on 2008-12-07
No problem, let me know how it goes!

---

### Post by xjcannonx on 2008-12-07
Yeah looks like you got the right version driver, still i don't think cairo-dock should be that slow and installing another program still may not work to solve the problem, Do you run a lot of screenlets and other intensive stuff? I know iv'e read about this problem on the forums before i just can't remember where
Have you tried the command 'top' in a terminal and see what it comes up with?

---

### Post by Twitch6000 on 2008-12-07
Yes this is a bug with cairo dock you could try avant or kiba dock :).

---

### Post by meg23 on 2008-12-07
cairo dock is really buggy now.

---

### Post by maduranga on 2008-12-07
what is the best dock available for linux?

---

### Post by dyous87 on 2008-12-07
In my opinion it is Avant Window Navigator:

[http://wiki.awn-project.org/index.php?title=Main_Page](http://wiki.awn-project.org/index.php?title=Main_Page)

It is nice and smooth, doesn't take too many resources, it is fully themeable and it is available in the repositories.

---

