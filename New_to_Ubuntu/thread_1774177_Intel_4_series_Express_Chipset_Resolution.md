---
title: "Intel 4 series Express Chipset Resolution"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by parthgadhia on 2011-06-03
Hello,

I have a Dell Inspiron 1545 15.1 inches, Core 2 Duo 2 GHz, 3 GB Ram with Intel 4 series express chipset integrated graphics card. 
Now, when I go to change my resolution, I only get one option- 1366x768. What I want to know is how do I know if this is the best resolution I can get?
Is there any way to go to a higher resolution, or is this the best my laptop can manage? I tried googling a lot, but couldn't find a solution to this.

Thanks. :)

---

### Post by Mariane on 2011-06-03
Funny you ask this, I only learnt how to do it yesterday :).
Open a terminal and type: 

```

xrandr

```

It will give you a list of possible resolutions for your screen. 

Mariane

---

### Post by parthgadhia on 2011-06-03
> **Mariane said:**
> Funny you ask this, I only learnt how to do it yesterday :).
Open a terminal and type: 

```

xrandr

```

It will give you a list of possible resolutions for your screen. 

Mariane


Thanks. :)

It says 60.0*- 1366x768, so that's the maximum I'm assuming?

---

### Post by Mariane on 2011-06-03
I think the * shows the current resolution. The resolutions are sorted, the highest possible resolution appears in the top row. So if 60.0*- 1366x768 is in the top row, yes, that's the highest. 

Mariane

---

### Post by parthgadhia on 2011-06-03
> **Mariane said:**
> I think the * shows the current resolution. The resolutions are sorted, the highest possible resolution appears in the top row. So if 60.0*- 1366x768 is in the top row, yes, that's the highest. 

Mariane

Thanks. :)

---

