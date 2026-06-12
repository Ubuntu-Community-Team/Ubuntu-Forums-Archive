---
title: "How to send devede to applications?"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by SirOmega on 2010-05-14
Greetings Everyone, I downloaded DeVeDe so as I could make some but the only way it seems I can get it to work is to open up the Terminal and typing devede.

Is there a way I can fix it so as to have a DeVeDe icon in the Applications tab?

Thank you very much in advance, I have installed Ubuntu in the hopes that I can recover files on my wife's PC running Windows 7 (should it crash) but I am a HUGE beginner with Linux. This way I can recover them from the Linux side.

Also a huge plus are all the educational programs which are free on Linux that our 4 year old likes.

---

### Post by xumuk37 on 2010-05-14
Right mouse click on Apps Menu, choose Edit Menus, then go to Application and add New Item...

---

### Post by SirOmega on 2010-05-14
Thank you for the quick reply, I tried that but I do not know the command line to make it execute.

Type - Application
Name - DeVeDe
Command - ?
Comment ?

I get the first 2 and what goes there, but clueless as to what to place in the Command, any ideas? I found the folder and files in the /usr/lib but other than that i have no idea how to make a icon in applications.

---

### Post by lisati on 2010-05-14
> **SirOmega said:**
> Thank you for the quick reply, I tried that but I do not know the command line to make it execute.

Type - Application
Name - DeVeDe
Command - ?
Comment ?

I get the first 2 and what goes there, but clueless as to what to place in the Command, any ideas? I found the folder and files in the /usr/lib but other than that i have no idea how to make a icon in applications.


"Command" = what you'd type in the terminal
"Comment" = a description

---

### Post by SirOmega on 2010-05-14
> **lisati said:**
> "Command" = what you'd type in the terminal
"Comment" = a description

THANK YOU!!!!! I cannot believe it was that easy, I simply typed in "devede" (without the quotes) as that is what I was doing to get it to run in the terminal, anyways I typed it in the box Command and then clicked OK and there it was! Just amazed that it was that simple, really hard to wrap my head around it.



 I was "overthinking it", and as a windows user I am trying to 'simplify' my way of thinking but it is not as easy as I thought. Thinking simple is hard.

---

### Post by eltonw on 2010-05-14
> **SirOmega said:**
> Greetings Everyone, I downloaded DeVeDe so as I could make some but the only way it seems I can get it to work is to open up the Terminal and typing devede.

Is there a way I can fix it so as to have a DeVeDe icon in the Applications tab?

Thank you very much in advance, I have installed Ubuntu in the hopes that I can recover files on my wife's PC running Windows 7 (should it crash) but I am a HUGE beginner with Linux. This way I can recover them from the Linux side.

Also a huge plus are all the educational programs which are free on Linux that our 4 year old likes.
It helps if you indicated which release you installed: karmic 9.10? Lucid 10.4? 
An easier way (for you) to add DeVeDe to the menus, is to install the app by using **EITHER** Synaptic [System \ Administration \ **[COLOR=Sienna]Synaptic Package Manager[/COLOR]** **OR** Applications \ [COLOR=Sienna]**Ubuntu Software Center**[/COLOR]. 

SEARCH for DeVeDe, and it might show as already installed. Just  select "re-install". Of course, you will have to provide your superuser / root [sudo] password to run either package manager.

Seeing that you are new to LINUX [FONT=Trebuchet MS][COLOR=Red]the following links might be of interest to you[/COLOR][/FONT] 
(if so, bookmark them!)::arrow:
[http://www.linuxnewbieguide.org/](http://www.linuxnewbieguide.org/)

[http://sites.google.com/site/easylinuxtipsproject/](http://sites.google.com/site/easylinuxtipsproject/)

[http://www.linux.ie/newusers/beginners-linux-guide/](http://www.linux.ie/newusers/beginners-linux-guide/)

[http://www.linuxlots.com/~jam/]("http://www.linuxlots.com/%7Ejam/")

HTH ... and welcome to GNU/LINUX!):P

---

