---
title: "i3 processor"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by path_finder on 2010-03-16
I am using a laptop with Intel® Core™ i3 Processor. Main memory is 4GB. But it doesnot have a seperate VGA card. 
My problem is I cannot boot it from any of the Ubuntu versions, therefore I cannot install Ubuntu on my laptop. I greatly appreciate if anyone could suggest a option for this. Anyhow I want to have linux based OS in my PC.

---

### Post by ibuclaw on 2010-03-16
At what point does the boot fail?

Have you tried safeboot / the alternate CD?

---

### Post by Saghaulor on 2010-03-16
> **path_finder said:**
> I am using a laptop with Intel® Core™ i3 Processor. Main memory is 4GB. But it doesnot have a seperate VGA card. 
My problem is I cannot boot it from any of the Ubuntu versions, therefore I cannot install Ubuntu on my laptop. I greatly appreciate if anyone could suggest a option for this. Anyhow I want to have linux based OS in my PC.

I have the i5 family. I was having issues getting the livecd to install. Turns out I needed to use "safe graphics mode". I'm not sure if that's your problem, but it's a start.

---

### Post by walkerc88 on 2010-03-16
I have an i3 processor and 4G memory and had to provide the following boot parameter
acpi=ht
Again, not sure if this is your problem, but its a start.

---

### Post by kaibob on 2010-03-16
Have you tried Lucid Lynx. I know it's only in beta, but it appears to provide much better support for video on the i3 and i5 processor. 

[http://ubuntuforums.org/showthread.php?t=1402612](http://ubuntuforums.org/showthread.php?t=1402612)

---

### Post by path_finder on 2010-03-17
It asks me to select what option I like. Install ubuntu, try ubuntu... etc. when i select Install ubuntu or try ubuntu dark screen appears and stays for ever. Once i heard Ubuntu booting sound.

---

### Post by teh603 on 2010-03-17
Yeah, you've got the same problem I did with Karmic. Jaunty dumps you into some kind of safe graphics mode, right?

It turns out that the drivers for the Arrandale chipset are still very new, and thus didn't make the cut for Karmic. You *can* install them in Jaunty and Karmic, but that requires some Linux-fu that I'm not very familiar with, along with disabling compiz thru the command prompt. There's a thread on it somewhere...

I suggest waiting for Lucid. Beta 1 is due out tomorrow, and the bootsplash doesn't cause horrible crashes anymore.

---

### Post by path_finder on 2010-03-30
Thanks everyone. I downloaded the Lucid lynx which is absolutely the correct answer for my problem.

---

### Post by espen.john@gmail.com on 2011-03-22
should an i3 processor computer install 64bit or 32bit version?

---

### Post by Paqman on 2011-03-22
> **espen.john@gmail.com said:**
> should an i3 processor computer install 64bit or 32bit version?

This is a really old thread, but you should choose 64-bit.

I'd suggest using your email address as your username is not a good idea, you'll get spammed.

---

