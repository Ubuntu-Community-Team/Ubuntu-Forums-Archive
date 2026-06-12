---
title: "Ubuntu Server 8.04 LTS will not log-in"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by heartshaped on 2009-09-19
My linux server 8.04 64 bit version wont stay logged in, ie i log in then it goes missing directory logging in as home=/... and then logs out, ive tried it on all concoles, not that it should make a difference. but hey i fugure it was worth a try.
 
 
this is just after i installed it and i have no idea why its doing this, i figure there is something wrong with the installation but i have no idea why :( 
 
im running a core 2 duo intel with 3 gb ram 200 gb hdd and a 500 gb hdd
and some random video card i think its 8600 GT Nvidia or something similar
and i have tried restarting ect ect
 
any help would be greatly appreciated:confused::confused:
btw it wont let my type in any commands.....

---

### Post by seshomaru samma on 2009-09-19
Can you paste the exact error message ?
also - did you get any errors during the install?
did you install a graphic environment ?

---

### Post by heartshaped on 2009-09-19
I didnt install any GUI, however i was using the basic ISO file from [www.ubuntu.com]("http://www.ubuntu.com"), 
    The only error message i got during the install was when tried to install some of the GUI interfaces (like Kbar which I presumed did not come with the standard "basic" install, and i tried to also use the first boot loader (i cant remember the name) from the menu it started the program got stuck at 2% and then gave me an error message simply saying that one of the desired components could not be installed :(,
 
  the exact error message... as i cant remember and im not at home to tell you, but from memory (i will update it when i get home tomorrow) it seemed to start give me the ubuntu disclaimer of "there is no warranty with ubuntu unless otherwise specified in your local law" or something along the lines of that, then
 
 
after that it says that
No Directory booting from home=/ and then it returns back to the login prompt

---

### Post by seshomaru samma on 2009-09-19
i think we will need the exact error message

also ,if you want to run a graphical app on ubuntu server you need to install a graphical environment , like gnome, kde, icewm ...
you can either do that by installing a package like "ubuntu-desktop" or you can go with something more minimal . if you need help with that let me know

---

### Post by heartshaped on 2009-09-20
okay here is the exact message i get on the screen (in fact i probably wouldnt call it an error message but hey)
Ubuntu 8.04.4 LTS home server tty1
     Homeserv login: Heartshaped
     Password:*****
Last login : sat sep 19 14-30-37 EST 2009 on tty2
linux home serv 2.6.24-24-server#1 SMP tue jul 9 19:39:26 UTC 2009 x86_64
then it goes on about how ubuntu is free ectect adn there are no warranties provided
 
Then it goes 
 
to access official ubuntu documentation please visit 
[http://help.ubuntu/com/](http://help.ubuntu/com/)
no directory, logging in with home=/
ubuntu 8.04.3 LTS homeserv tty1
Homeserv login:
 
then i type it again and it displays the same thing and asks for the login again. :(

---

### Post by heartshaped on 2009-09-20
Never mind guys problem solved, I reinstalled the OS and now it seems to be working fine, must have been a problem with the install
      thanks for the help!

---

