---
title: "how do i check graphics card? graphics problems"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by ni ni on 2009-03-25
Hello Everyone!

my problem is about every 20 minutes whether i'm surfing the net or writing in open office my screen goes blank, and i have to roll the mouse over all my icons in the panel to make them reapear, and mimimise and re-maximise my page to make that reappear.

in Visual Effects it won't allow me to choose Normal or Extra - I get the message "desktop effects could not be enabled".

How do i check my graphics card? Or could the problem be something else? I know my laptop is old :-(

Thanks in advance for any suggestions!

Ni xxxxxxx:KS:KS:KS:KS:KS:KS

---

### Post by balaknair on 2009-03-25
Open a terminal(Applications menu> Accessories> Terminal) and enter the command
***lspci | grep VGA***

This will tell you what graphics card you have.

Older cards might not be capable of 3D acceleration and therefore be unable to support desktop effects.

---

### Post by ni ni on 2009-03-25
thank you.

here is the ouput:
```
niamh@niamh-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN400/PM800/PM880/PN800/PN880 [S3 UniChrome Pro] (rev 02)
niamh@niamh-laptop:~$ 

```

is it a bad card?  Sorry for my lack of technical knowledge :-(

---

### Post by KCG102282 on 2009-03-25
I personally wouldnt be caought dead having a VIA card in my computer, but since its a laptop you are stuck with it which is why I HATE laptops!

---

### Post by ni ni on 2009-03-25
LOL What's gonna happen when Jackelope is released??? will i be screwed???

am i screwed as it is???? i'm so confused!!!

---

### Post by balaknair on 2009-03-25
Your card does not support 3D. So I'm afraid desktop effects won't be possible. You can still use metacity compositing if you want to get some minimal effects and run eyecandy apps like the AWN dock and Screenlets widgets. To enable metacity compositing via gconf-editor, press alt-F2--> type ***gconf editor*** and click 'Run'--> this opens gconf-editor, now browse to Apps> metacity> general--> find the check-box that says 'compositing_manager' enable it. I've used it on my old desktop(with an integrated VIA card, it worked quite well without too many problems till the motherboard finally died a week ago).

As for the other problems you mention, it could be either a bug with the drivers (not very likely if you're using a fully updated version of Intrepid Ibex with the openchrome drivers), or it might just be your video card hardware showing its age.

If it is a driver bug, IMO things will get better with Jaunty, since the new kernel is much better at managing graphics resources.

---

### Post by balaknair on 2009-03-25
I think I found a solution to the disappearing icons and stuff here
( [https://help.ubuntu.com/community/OpenChrome#Problems%20and%20solutions](https://help.ubuntu.com/community/OpenChrome#Problems%20and%20solutions) ) the very last one.

Try alt-F2--> type ***gksudo gedit /etc/X11/xorg.conf*** and click 'Run'--> Scroll down to the section 'Device', and set the value of option "EnableAGPDMA" as "True", "False", "On", "Off"(try the different values one by one to see what works for you).
 
Hope this is helpful.

All the best.

---

### Post by ni ni on 2009-03-25
balaknair, you are so kind, thank you very much!

---

### Post by balaknair on 2009-03-25
> **ni ni said:**
> balaknair, you are so kind, thank you very much!

You're welcome :D

Glad to help. Hope that it fixes your problem.

---

