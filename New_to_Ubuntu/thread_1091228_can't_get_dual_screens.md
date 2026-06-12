---
title: "can't get dual screens"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by keens on 2009-03-09
hey.

i have a ati 3850 and i have the drivers installed that ubuntu told me too, but i can't get dual screens too work, it just always has clone, and then when i set it too big screen it just stays cloned and scrolls.

i tried all the tutorials but none of them make any sense.

can someone who has already done it tell me how?

also tried downloading a new driver thing, but how the hell do you open a .run package, it says sh to open or something but it doesnt work.

---

### Post by Nxion on 2009-03-09
When you say you set it to big screen, how did you do this and where? Was it in the ATI control panel or in the Ubuntu screen resolution control panel?

As for your second question. To run a .run you have to make it executable first other wise nothing will work. To do that:

```
sudo chmod a+x /path/to/file.run
```

And to run it:

```
sudo ./filename.run
```

---

### Post by TheLunticIsInMyHead on 2009-03-09
I had a similar problem, I think that if your screen size (combined) is greater than a number in the file /etc/X11/xorg.conf (I think thats the one, its in X11 somewhere) then it doesn't work.

I fixed this, and now it doesn't just clone, my computer still doesn't deal with the graphical effets great (I have to turn compiz off).

Try it and see, I'm about to go look in the folder and see what I can do.

Mike

---

