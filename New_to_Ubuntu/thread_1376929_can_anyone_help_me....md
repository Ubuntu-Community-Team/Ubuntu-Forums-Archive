---
title: "can anyone help me..."
date: 2010-01-09
forum: New to Ubuntu
---

### Post by jenbalish84 on 2010-01-09
i have a problem with the linux system...my computer is very sloe asnd seem like it has some virus;s and i have no way to remove the problem..my screen blinks on the left side of my comouter screen and i just dont know what to do..someone please help me...:popcorn:

---

### Post by llawwehttam on 2010-01-09
I very much doubt is is a virus. lol. It sounds more like a graphics problem . What graphics card are you using and what driver do you have installed for it.
Also are their anymore symptoms of a 'virus'?

---

### Post by jenbalish84 on 2010-01-09
well i dont know ..i ahd smeoen install that on my cpmuter and i just dont know whats where..so...

---

### Post by Leppie on 2010-01-09
you can install a virs scanner and check your system on viruses:
```
sudo apt-get install clamav clamtk
```
in the menu you can find it going to System>Administration>Virus Scanner

---

### Post by cariboo on 2010-01-10
Installing a windows virus scanner is not going to help the op with his problem. 

To the op, we need much more information in order to help you with your problem. The first thing I would suggest is you contact the person that installed Ubuntu for you and explain the problem to him.

If that isn't possible, please open an Applications-->Accessories-->Terminal and type:

```
sudo lshw
```

and paste the output of the above command in your next post. To copy and paste the output, just highlight it with your mouse, then use your middle mouse button (wheel) to paste.

I've also move your thread to Absolute Beginner Talk, as you don't really have a security problem.

---

