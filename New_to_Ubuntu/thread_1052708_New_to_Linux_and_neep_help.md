---
title: "New to Linux and neep help"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by dcn427 on 2009-01-28
I just got my Ubuntu cd today and i installed with no problem at all. I then tried to activate my graphics card. it diwnloaded and installed the driver thn wanted a pc reboot. i did that and now when ubuntu loads all i see is a thin line across the top of the screen and cant see a thing. i can type my user nane and password and it will load, but i never get the screen back, any help? thanks

---

### Post by zvacet on 2009-01-28
Whitch card do you have and did you tried to install driver for it in **system>admin>restricted drivers**?

---

### Post by candtalan on 2009-01-28
Welcome!
Looks like the driver was not good fro your actual card....

Try booting into the initial grub menu choice of recovery mode, then try using the xfix option frm the small menu.

If that does not work then consider using the app
envyng-gtk
but maybe get comments from others first?

good luck

---

### Post by dcn427 on 2009-01-28
I have the Nvidia GeForce 6100 and from restrited drivers sounds right, Im too new to know exactly what is what also i for got to mention that if i move the mouse way up to the top of the screen, i can see the tip of it moving around.

---

### Post by dcn427 on 2009-01-28
i have no idea where to find that APP any one else available to help?

---

### Post by Bablefish on 2009-01-28
Some advice reinstall your OS, honestly there is another way to do this but reinstall is much earier.

---

### Post by dcn427 on 2009-01-28
ireinstalled ubuntu lastnight but when i went to activate it again same problem, and i dont really want to use the standard 800x600 screen

---

### Post by avtolle on 2009-01-28
When you reinstalled, I presume you also activated the appropriate restricted driver and then restarted? I'm guessing that the system indicated that the 177 driver was recommended, and that is the one you activated.

---

### Post by dcn427 on 2009-01-28
actually yes, was that a mistake?

---

### Post by avtolle on 2009-01-28
No, not a mistake; just trying to get a grasp on where you were at in the process.

---

### Post by Rabindranath on 2009-01-28
I have had problems like this before but it was due to an improper shutdown and not the graphics card driver. Just try to restart it again. If you have messed up the usplash theme, you can easily restore a similar one. 

[http://gnome-look.org/content/show.php?content=93386](http://gnome-look.org/content/show.php?content=93386)

I used to install the graphics driver through "Envy" in fiesty and gutsy and it worked nicely before. So, you can try to install the graphics driver through envy. And you can try to enable an older driver as they tend to be more stable.

---

### Post by dcn427 on 2009-01-28
i would ley ubuntu restart its self i would not do anything to it.  and what is envy and how can i use it/get it. im only on my first day using ubuntu and already think i am in way over my head

---

### Post by UbuntuNerd on 2009-01-28
check out this guide look to problem 3 and 4 for some graphical solutions
[http://my.opera.com/ubuntunerd1/blog/ubuntu-problem-and-solution-part1]("http://my.opera.com/ubuntunerd1/blog/ubuntu-problem-and-solution-part1")

---

### Post by dcn427 on 2009-01-28
i give it a shot and see what happens, but i dont get corrupted graphics, just none

---

### Post by Rabindranath on 2009-01-28
Before the "Restricted Driver management" tool was introduced in ubuntu, there was a program called envy which can install nvidia and ati drivers easily. 

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Just install it. It will identify the card and display the necessary drivers(including the latest ones unlike restricted driver management). Choose the driver you want and it will install the driver from the nvidia website.

---

### Post by dcn427 on 2009-01-28
ok do i wabt envy legacy or EnvyNG?

---

### Post by Rabindranath on 2009-01-28
Hardy Heron and Successors - EnvyNG

Others - Envy Legacy

---

### Post by dcn427 on 2009-01-28
ok, im so lost it aint funny, ill br back, hopefully in unbuntu and not windows next ime

---

### Post by dcn427 on 2009-01-28
ok one last question, do i type all of that stuff it has listed some where? or is there actually a program that i just download? and where can i get some backround info on how ubuntu uns, i know nothing about it

---

### Post by Rabindranath on 2009-01-28
It is just a program to automate everything. Just download it, install it, Select the driver and click apply. No need for any terminal. And I think you should experiment with ubuntu in order to find how it runs(even if it requires several reinstalls).;)

---

### Post by dcn427 on 2009-01-28
ok just did the envy install and allm, same problem happens again

---

