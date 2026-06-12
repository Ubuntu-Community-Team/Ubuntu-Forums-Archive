---
title: "unable to update system"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by lerichardson on 2009-11-24
Hi, I have a Mini Dell with Ubuntu 8.04. I bought it for my daughter but Ive been using it because its easy to carry. I recently was prompted that there were updates to download and when I tried to do this it asked me to give permission by entering an admin. password. I dont ever remember setting this when I first set it up for my daughter. Soooo, I tried remembering freq. used passwords with out luck, tried just clicking ok still no luck. I also want toplay one of my favorite games on facebook and I cant because I need to, again, enter the admin. password to update the new game.
So frusterated. Someone told me to reboot into the system in safe mode or something? I tried to do this- holding shift down with reboot put up a black screen with MBA_. It does not offer me any menu.
If anyone can help me bypass the admin. password just for updates that would work. 
Thanks Lis

---

### Post by MelDJ on 2009-11-24
try looking through the laptop manual to see what the default password is

---

### Post by ricardo.gloe on 2009-11-24
Have a look at these articles

[http://www.whatsmypass.com/recover-lost-ubuntu-password](http://www.whatsmypass.com/recover-lost-ubuntu-password)

[http://www.linuxquestions.org/questions/ubuntu-63/oh-noes-lost-my-username-and-password-523164/](http://www.linuxquestions.org/questions/ubuntu-63/oh-noes-lost-my-username-and-password-523164/)

[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

---

### Post by QLee on 2009-11-24
> **lerichardson said:**
> Hi, I have a Mini Dell with Ubuntu 8.04. I bought it for my daughter but Ive been using it because its easy to carry. I recently was prompted that there were updates to download and when I tried to do this it asked me to give permission by entering an admin. password. I dont ever remember setting this when I first set it up for my daughter. Soooo, I tried remembering freq. used passwords with out luck, tried just clicking ok still no luck. I also want toplay one of my favorite games on facebook and I cant because I need to, again, enter the admin. password to update the new game.
So frusterated. Someone told me to reboot into the system in safe mode or something? I tried to do this- holding shift down with reboot put up a black screen with MBA_. It does not offer me any menu.
If anyone can help me bypass the admin. password just for updates that would work. 
Thanks Lis

If your daughter was the first user added to the system then what the system is probably asking for is the password under which you logged onto the system. The first user added is in the admin group.

Ubuntu systems by default don't use a "root" password, they are setup to do root commands with sudo. So, if you haven't followed what I would consider bad advice from somewhere and changed the system, try her password.

Another option is ask Dell how they setup the system or consult their documentation.

---

### Post by karthik120 on 2009-11-24
Another way is to take a look at the sudoers file in /etc directory. Please issue the command 

         sudo vi /etc/sudoers. It will ask for the password. Use your daughter account password and the file opens up. Please copy the contents of the file and paste it here. 




Regards,
Karthik

---

### Post by lerichardson on 2009-11-24
ok, i have not done anything with it yet. I tried entering the only passwords I could think of. My daughter was only 8 at the time and has never set up or changed any part of the system. she just played games. after turning it on. 
When the computer turns on, I go to the drop down start menu, then I go to administartor and then to users. When im in ths box it does say a username and password. I have tried using these and they dont work. Im so stumped.

---

### Post by lerichardson on 2009-11-24
Im totally new to ubuntu and its set up. In windows you have a box to type a command from the start menu. When I click on the start menu I do not have a place to type any command. where do i find this?

---

### Post by McFarley on 2009-11-24
Have you tried your own password, or the password of the "default" account which is created during O/S installation?  Once that account is created, it's got sudo access.

---

### Post by lerichardson on 2009-11-24
Yes- I spent time entering every possible password I could think of,  mine and something I may have used for her. Is there a way that changing some sort of security setting to allow just for updates? Im computer basic and need step by step instruction- sorry! 
If I can not remember or find the password, what do I do next? Ive tried Dell and they want me to pay a fee to get advice. That would be my last resort. 
Someone above said to not use root to sign in. would that be the next way?

---

### Post by kansasnoob on 2009-11-24
> **lerichardson said:**
> Im totally new to ubuntu and its set up. In windows you have a box to type a command from the start menu. When I click on the start menu I do not have a place to type any command. where do i find this?

[http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

Specific to your original problem:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Aysiu did an excellent job with Psychocats! I would have been lost without it when I started using Ubuntu.

---

### Post by Alxl on 2009-11-24
as already said:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) 

[http://www.whatsmypass.com/recover-lost-ubuntu-password](http://www.whatsmypass.com/recover-lost-ubuntu-password)

let us know

---

