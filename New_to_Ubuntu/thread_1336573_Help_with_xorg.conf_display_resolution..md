---
title: "Help with xorg.conf display resolution."
date: 2009-11-24
forum: New to Ubuntu
---

### Post by jdc158 on 2009-11-24
I'm terrible at getting this xorg.conf file correct. Can anyone help me write it correctly? Im operating on 9.10

This is my video card. 

Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

Specs on my monitor. 

Product Manual PDF. [http://www.amazon.com/Microtek-710S-17-LCD-Monitor/dp/B00009MJK2](http://www.amazon.com/Microtek-710S-17-LCD-Monitor/dp/B00009MJK2)

Please help I hate this 800X600 display!!!

---

### Post by bkratz on 2009-11-24
> **jdc158 said:**
> I'm terrible at getting this xorg.conf file correct. Can anyone help me write it correctly? Im operating on 9.10

This is my video card. 

Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

Specs on my monitor. 

Product Manual PDF. [http://www.amazon.com/Microtek-710S-17-LCD-Monitor/dp/B00009MJK2](http://www.amazon.com/Microtek-710S-17-LCD-Monitor/dp/B00009MJK2)

Please help I hate this 800X600 display!!!


My monitor gave me out no EIDE so even though I have intel graphics I was stuck at 800x600 until I found this post.

[http://ubuntuforums.org/showpost.php?p=8279613&postcount=155](http://ubuntuforums.org/showpost.php?p=8279613&postcount=155)

The link for the monitor did not give specifications for horizontal or vertical refresh rates and the posting above will allow you to set values that will not work and you will not be able to easily recover from. DON'T SET IT TO HIGH!. Your monitor does say 1280x1024, but be careful. By the way, do you even have an xorg.conf file? Mine didn't in 9.10 and I had to create a blank one and transfer in this data, or an approximation there of.

---

### Post by jdc158 on 2009-11-24
9.10 doesn't come with it, but I made one. Just need help saving the right code.

---

### Post by phidia on 2009-11-24
Xorg and it's configuration has changed alot. Some of the previous methods of configuration are not effective.
Try this [ubuntu wiki]("https://wiki.ubuntu.com/X") and see if that helps you create an xorg.conf that will work for you.

---

### Post by bkratz on 2009-11-24
> **jdc158 said:**
> 9.10 doesn't come with it, but I made one. Just need help saving the right code.

The link I sent you was what I actually put in mine except that I was interested in a slightly higher resolution and changed the modes statement.  The horiz and vertical numbers are those for my monitor. Your link did not show those, just that they had no more available!  Just don't select anything to high or trouble will follow.

---

### Post by jdc158 on 2009-11-25
Acually the link does have all the info. You just have to download the user manual PDF to view it. 
 
[FONT=Times New Roman][SIZE=2][LEFT]Scan Frequencies:
Horizontal 31.47K to 80KHz
Vertical 60Hz to 75Hz[/LEFT]
 
thats what i need right?
[/SIZE][/FONT]

---

### Post by bkratz on 2009-11-25
> **jdc158 said:**
> Acually the link does have all the info. You just have to download the user manual PDF to view it. 
 
[FONT=Times New Roman][SIZE=2][LEFT]Scan Frequencies:
Horizontal 31.47K to 80KHz
Vertical 60Hz to 75Hz[/LEFT]
 
thats what i need right?
[/SIZE][/FONT]

Yes, I don't know if it will take a decimal or not, but you should be safe with 30-80 and 60-75 preventing any damage.  You will have to reboot to see a change.

---

