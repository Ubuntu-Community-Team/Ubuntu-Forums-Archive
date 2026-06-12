---
title: "ubuntu on windows 7 ?"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by fartofagony on 2011-05-14
my computer/programming termology is bad but i will try to explain:

i was runniing ubuntu 10.10 on win7 with vmware workstation. everything seemed to work fine untill i restarted the virtual machine. it would not start again so i tried ubuntu 10.10 on win7 with virtualbox but it did not feel as good as vmware and i could not get either of the VM programs or what they are called to identify my graphic card. it identified everything except graphic card but i think i am giong off topic! ok my question is:what virtual machine program like those i mentioned above are there that work and dont mess things up? if you know what i mean. and what version of ubuntu should i start learning from? i had alot of problems getting GUIs to work so i couldnt continue following instructions from beginner books etc etc.
i would love to ask about VMware workstation errors but i dont think i am allowed in this thread i just made!
thank you for your attention and i appreciate any help!

---

### Post by fidamehran on 2011-05-14
> **fartofagony said:**
> my computer/programming termology is bad but i will try to explain:

i was runniing ubuntu 10.10 on win7 with vmware workstation. everything seemed to work fine untill i restarted the virtual machine. it would not start again so i tried ubuntu 10.10 on win7 with virtualbox but it did not feel as good as vmware and i could not get either of the VM programs or what they are called to identify my graphic card. it identified everything except graphic card but i think i am giong off topic! ok my question is:what virtual machine program like those i mentioned above are there that work and dont mess things up? if you know what i mean. and what version of ubuntu should i start learning from? i had alot of problems getting GUIs to work so i couldnt continue following instructions from beginner books etc etc.
i would love to ask about VMware workstation errors but i dont think i am allowed in this thread i just made!
thank you for your attention and i appreciate any help!

Why go to the trouble of virtualization? You have a perfectly good solution of "Wubi".

It's a program that helps you install Ubuntu within Windows. Of course, you don't get to peek at the both OSs at the same time, but, you get a completely hassle free Ubuntu installation and still, very much under Windows 7.

I'm sure you already know it. But, well, here it goes:
1. Keep the Ubuntu ISO ([http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download")) and the latest Wubi ([http://www.ubuntu.com/download/ubuntu/windows-installer]("http://www.ubuntu.com/download/ubuntu/windows-installer")) in the same folder in Windows.

2. Right click Wubi.exe and select "Run as Administrator". Then go on with the installation, install in the drive you wish and with the size that you wish.

3. PC restarts and you get a bootloader option in the Windows bootloader to go to Ubuntu or Windows (Windows by default). Select Ubuntu and the installation will continue and get finished at one point of time.

I'm sure you wanted the VMWare Solution, but, I consider Wubi to be the better option.

Sorry if I babbled about something you already know and don't want to practice.

---

### Post by fartofagony on 2011-05-14
> **fidamehran said:**
> Why go to the trouble of virtualization? You have a perfectly good solution of "Wubi".

It's a program that helps you install Ubuntu within Windows. Of course, you don't get to peek at the both OSs at the same time, but, you get a completely hassle free Ubuntu installation and still, very much under Windows 7.

I'm sure you already know it. But, well, here it goes:
1. Keep the Ubuntu ISO ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)) and the latest Wubi ([http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)) in the same folder in Windows.

2. Right click Wubi.exe and select "Run as Administrator". Then go on with the installation, install in the drive you wish and with the size that you wish.

3. PC restarts and you get a bootloader option in the Windows bootloader to go to Ubuntu or Windows (Windows by default). Select Ubuntu and the installation will continue and get finished at one point of time.

I'm sure you wanted the VMWare Solution, but, I consider Wubi to be the better option.

Sorry if I babbled about something you already know and don't want to practice.
thank you!
i knew about wubi and even tried it but couldnt switch between the two OSs as smoothly as i could with virtualiztion.
maybe you wonder what i want from all this? it is that i dont trust windows anymore and i wnat to become as anonym as possible.
i dont know if wubi has any cons if compared with (example) vmware workstation but if it is what most experienced users would pick, then i just follow your/their footsteps.
i noticed that the ip adress or whatever it is changes with vmware so thats good? lol, i have been wasting my life playing games and now i m becoming interested in linux OSs and such.
thats what i get for not having a mentor smacking me in the back of my head saying "hey... learn something!" :)
is wubi what most experienced ubuntu users use?

---

### Post by wildmanne39 on 2011-05-14
> **fartofagony said:**
> thank you!
i knew about wubi and even tried it but couldnt switch between the two OSs as smoothly as i could with virtualiztion.
maybe you wonder what i want from all this? it is that i dont trust windows anymore and i wnat to become as anonym as possible.
i dont know if wubi has any cons if compared with (example) vmware workstation but if it is what most experienced users would pick, then i just follow your/their footsteps.
i noticed that the ip adress or whatever it is changes with vmware so thats good? lol, i have been wasting my life playing games and now i m becoming interested in linux OSs and such.
thats what i get for not having a mentor smacking me in the back of my head saying "hey... learn something!" :)
is wubi what most experienced ubuntu users use?
Hi, I use virtualbox, I run it in ubuntu natty and I love it the only issue is it does not play games well, but I do not play games ether so it  is good for me. It run windows 7 as good or better then running windows 7 on its own, but you do have to download the extension pack to get usb working. You can go to virtualbox.org to download the one you need for your system do not use the one in the repos for ubuntu. Also read all the instructions for setting up and using virtualbox before you install an operating system.:D

---

### Post by fartofagony on 2011-05-14
> **wildmanne39 said:**
> Hi, I use virtualbox, I run it in ubuntu natty and I love it the only issue is it does not play games well, but I do not play games ether so it  is good for me. It run windows 7 as good or better then running windows 7 on its own, but you do have to download the extension pack to get usb working. You can go to virtualbox.org to download the one you need for your system do not use the one in the repos for ubuntu. Also read all the instructions for setting up and using virtualbox before you install an operating system.:D
should i cancel my wubi download and work via virtualbox? if one of these methods is more anonymous than the other, let me know, if you would know, or if theres a difference.
im downloading 11.04 now instead of using 10.10 because i remember alot of bugs in 10.10, correct me if im wrong!
to be as anonym as possible is what i prioritize. i am not hiding anthing but knowing that someone is setting my limits and such makes me sad.
have you useb wubi before? dont know what to chose between virtualbox and wubi. i was looking for nswers through google search but  i am still not 100% sure which one.
i could just try them both but my lack of computer skills would make me oblivious to the things that i should avoid and so on

---

### Post by fidamehran on 2011-05-14
> **fartofagony said:**
> thank you!
i knew about wubi and even tried it but couldnt switch between the two OSs as smoothly as i could with virtualiztion.
maybe you wonder what i want from all this? it is that i dont trust windows anymore and i wnat to become as anonym as possible.
i dont know if wubi has any cons if compared with (example) vmware workstation but if it is what most experienced users would pick, then i just follow your/their footsteps.
i noticed that the ip adress or whatever it is changes with vmware so thats good? lol, i have been wasting my life playing games and now i m becoming interested in linux OSs and such.
thats what i get for not having a mentor smacking me in the back of my head saying "hey... learn something!" :)
is wubi what most experienced ubuntu users use?

If you don't trust Windows anymore, why not switch to Ubuntu completely?
I am not too sure about your core intention. Hiding IPs, is it?

---

### Post by fartofagony on 2011-05-14
> **fidamehran said:**
> If you don't trust Windows anymore, why switch to Ubuntu completely?
I am not too sure about your core intention. Hiding IPs, is it?
my intensions re oure but i fully understand that it would sound suspicious me desperatly asking for help.
if the ip was completely hidden that wold be a bonus for me!

i want  working space like a base to learn too, and wht i fear is me learning it "the wrong way" by using a program or an OS etc etc so that i build a custom to that or develop bad habbits and such which i have a hard time shaking off.

i think hving  confortable starting space with all necessary things needed i (or other newbies like me) could learn, but in the "proper" way. i cant find the right words to describe :(

oh forgot to say:
with  vmware i was able to reinstall ubuntu very fast and smooth whenever i screwed up and it gave me the courage to experiment and test things i normally would dare on my primary OS.
just temporarily so that i get in harmony with ubuntu and then when i am confident enough i will switch places so that i have ubuntu as my primary OS

---

### Post by fidamehran on 2011-05-15
> **fartofagony said:**
> my intensions re oure but i fully understand that it would sound suspicious me desperatly asking for help.
if the ip was completely hidden that wold be a bonus for me!

i want  working space like a base to learn too, and wht i fear is me learning it "the wrong way" by using a program or an OS etc etc so that i build a custom to that or develop bad habbits and such which i have a hard time shaking off.

i think hving  confortable starting space with all necessary things needed i (or other newbies like me) could learn, but in the "proper" way. i cant find the right words to describe :(

oh forgot to say:
with  vmware i was able to reinstall ubuntu very fast and smooth whenever i screwed up and it gave me the courage to experiment and test things i normally would dare on my primary OS.
just temporarily so that i get in harmony with ubuntu and then when i am confident enough i will switch places so that i have ubuntu as my primary OS

Well, from what I get from your latest addition, you want to make the final switch to Ubuntu ultimately. So, in my opinion, Wubi would give you the complete installation flavor, while still controlling it from Windows.
Later, you can uninstall Wubi installation, and install Ubuntu in a separate drive as a separate real dual boot installation.
In any case, I believe in keeping a Windows installation in your PC, just in case something goes wrong. No harm in shrinking the Windows partition size and keeping it, just in case.
I, however, do not have the solution to the IP hiding issue.

---

### Post by wildmanne39 on 2011-05-15
> **fartofagony said:**
> my intensions re oure but i fully understand that it would sound suspicious me desperatly asking for help.
if the ip was completely hidden that wold be a bonus for me!

i want  working space like a base to learn too, and wht i fear is me learning it "the wrong way" by using a program or an OS etc etc so that i build a custom to that or develop bad habbits and such which i have a hard time shaking off.

i think hving  confortable starting space with all necessary things needed i (or other newbies like me) could learn, but in the "proper" way. i cant find the right words to describe :(

oh forgot to say:
with  vmware i was able to reinstall ubuntu very fast and smooth whenever i screwed up and it gave me the courage to experiment and test things i normally would dare on my primary OS.
just temporarily so that i get in harmony with ubuntu and then when i am confident enough i will switch places so that i have ubuntu as my primary OS
Hi, well it is what feels right to you I like virtualbox, yes partly because it you have a problem you can revert back to an earlier stage in a few seconds and be up and running again. As for hiding your ip address I am not sure about, I have never tried too hide mine, I am sure there are programs to do it. It does make me very suspicous of anyone that is trying too.

---

### Post by fartofagony on 2011-05-15
thank you so much guys! going to try both at the same time to have 2 identicly OSs and work differently with them

---

### Post by wildmanne39 on 2011-05-15
> **fartofagony said:**
> thank you so much guys! going to try both at the same time to have 2 identicly OSs and work differently with them
Hi, your welcome if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.:D

---

