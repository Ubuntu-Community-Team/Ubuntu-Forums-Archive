---
title: "Change boot script in menu.lst or in isolinux/grub?"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by nooby on 2010-02-14
I boot the CD live version of Ubuntu 9.10 and I tried to follow advices on different threads. To learn the process I tested something unimportant first. Setting the kbmap. Only as a test but it failed. 

Background

Something that works good when all is booted is to do in terminal 
sudo setxkbmap se that gives me Swedish keyboard but english at terms exactly what I need.

But would be cool if one could do it already with cheat codes at menu.lst 

I have tested one such but that one failed. Maybe the built in script has higher authority and run over the code or I got an old one that no longer works. 


[B]
More important than setting kbmap is to stop boot script from looking for index files after it has done the Adding Kubunty faves. It takes almost a minute of search to find some index files. I wish I knew what it is searching for I could give path to them or if they are not important to stop looking for them. [/B]

If it can't be done at menu.lst then I have to learn how to open the script and do some editing there. Is that easy or difficult?

---

### Post by cariboo on 2010-02-14
There is no menu.lst in Karmic (9.10). Karmic uses grub2 which now uses /boot/grub/grub.cfg

For more info on grub2, have a look [here]("https://help.ubuntu.com/community/Grub2").

---

### Post by nooby on 2010-02-15
Yes that is true but the code is very similar they have only added a script like 

{
} 

to include things in arguments formally. But the what is in these is very similar. So it doesn't change what I ask. 

I ask what to tell Grub2 or whatever boot version you use to stop 
the program from looking for index files in the wrong place. Takes almost 60 seconds to find it while if one give the better code then it take within a blink of the eye to find it. Huge difference. 

I apology for giving wrong impression in the title. Not sure what to write instead. 
[B]
What should boot script have to avoid wrong path search?  [/B]

My English fails me.

---

