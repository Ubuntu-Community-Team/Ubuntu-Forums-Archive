---
title: "Questions about my desktop computer's cooling fan"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by hanzj on 2011-07-05
Hello,
1. How can I find out what size my cooling fan is? (Without having to opening the case, I hope)
2. How can I determine the "specs" of my cooling fan? (Again, I hope I wouldn't have to open up the case. I hope there's a way I can find these things out via "terminal".)

3. How can I find out what sizes and types of cooling fans will work with my computer?

4. How can I determine whether a fan with these specs:
> 92mm, 1500rpm, 3 pin/2 wires, 4 screws
is better than the fan in my computer?

---

### Post by Matt__ on 2011-07-05
I'm afraid the only way is to open your case, and you dont say if thats a cpu fan or case fan.
What are your PC specs/make and model?

If you've never done this and use an off the shelf pc then you will most likely have a 'stock' heatsink and cpu fan. Obviously the fan must fit the heatsink and the heatsink must fit the processor.

To determine what new fan/heatsink combo to buy use hardinfo (sudo  apt-get install hardinfo) and find out what processor you use.

If you want to add case fans, either look on the mother board/in its  manual/online to find out how many 2 or 3 pin fans you can plug into it.
Other 3rd party fans can be plugged into the 4 pin power supplies that run your IDE cd and hard drives.

//edit: you can also look in the bios which may show your fan(s), the rpm and the cpu temp.

---

### Post by dFlyer on 2011-07-05
The only way I know of is to open the case unless you still have the spec sheet for your computer it may be listed there. You might also be able to enter you computers make and model on a google search that will list it's components.

---

