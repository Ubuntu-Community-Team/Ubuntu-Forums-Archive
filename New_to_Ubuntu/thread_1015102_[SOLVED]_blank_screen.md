---
title: "[SOLVED] blank screen"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by garrydog on 2008-12-18
Hi
I am new to this forum ,and also new to ubuntu .I have instaled ubuntu on my hard drive along with windows xp .When i boot up i go for the ubuntu option ,i get the ubuntu sign and the bar under it then i here a small drum sound ,then the screen go's blank .
Can someone help me .
Thanks David .

---

### Post by lovelyvik293 on 2008-12-18
Just try to use the ALT+CTRL+F6
it will take you in the command mode.

---

### Post by donkyhotay on 2008-12-18
I've had this before myself, It's a display problem, most likely due to an improperly configured X server or a driver problem. As mentioned previous, pressing ctrl-alt-f# will get you into a terminal which will allow you to begin fixing it. First of all I would want to know what type of video card you have, second can you post the output of your xorg.conf file? To display this just type:
```
less /etc/X11/xorg.conf
```

---

### Post by garrydog on 2008-12-18
sorry but not very good on this machine ,trying to learn .
How do i find out the type of video card i have .

---

### Post by lovelyvik293 on 2008-12-18
Use 
```

lspci

```

---

### Post by donkyhotay on 2008-12-18
err... what he said

---

