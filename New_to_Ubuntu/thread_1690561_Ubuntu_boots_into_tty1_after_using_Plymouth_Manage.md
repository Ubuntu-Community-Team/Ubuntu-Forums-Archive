---
title: "Ubuntu boots into tty1 after using Plymouth Manager"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by ubun2geek on 2011-02-18
Hello everyone! I'm just a newbie, and I like ubuntu a lot. I have quite a bit of skill in Windows, but I like Ubuntu. Only problem is, it doesn't boot up now! :( It boots into tty1 or something like that. I used Plymouth Manager available from sourceforge.net, and must have messed something up. Please help! If you have any questions, please post them on the forum. Thank you! :D

---

### Post by TeoBigusGeekus on 2011-02-18
Once in command line, do you get any error messages when you give
```
startx
```
or
```
gnome-session
```
?

---

### Post by ubun2geek on 2011-02-18
Yes with startx
I haven't tried gnome-session
(that was a fast reply! :))

---

### Post by ubun2geek on 2011-02-18
i messed with something in Plymouth Manager and the login GDM does not show up

---

### Post by TeoBigusGeekus on 2011-02-18
Can you post us some, or at least the last error messages you get?

---

### Post by ubun2geek on 2011-02-18
I didnt get any. Just asked me to login, but it was more of a command line interface

---

### Post by TeoBigusGeekus on 2011-02-18
Well... login.
Give your username and password.

---

### Post by ubun2geek on 2011-02-18
I did that, and I got, well... nothing really except for a couple words i dont remember. I can get back to you in fifteen minutes with them if you ask me to. I am dual-booting, so right now i am in windows.

---

### Post by ubun2geek on 2011-02-18
> **TeoBigusGeekus said:**
> Can you post us some, or at least the last error messages you get?
(When it starts up) Ubuntu 10.10 tty1
ubuntu login ( I put in my username)
ubuntu password ( I put in password)
(Tells when I had my last login and says Welcome to Ubuntu! We are having fun scaring you out of your wits! Just kidding! :))
When I try gnome-session it says:
**(gnome-session:1622): WARNING** Cannot open display:
and when i try startx
Fatal error: No screens found!

---

### Post by TeoBigusGeekus on 2011-02-18
Try
```
sudo apt-get install --reinstall gdm
```

---

### Post by ubun2geek on 2011-02-18
are you sure that will work? (like your avatar :))

---

### Post by ubun2geek on 2011-02-18
tried it, said "command does not exist"
```
sudo apt-get install gdm
```that installed the gdm
it still didn't work
I think i need to reinstall something to the affect of plymouth themes or something
thank you for trying, though that was a good thought

---

### Post by SavageWolf on 2011-02-18
Try CTRL+ALT+F7?

Might work maybe!?

---

### Post by ubun2geek on 2011-02-18
Thanks, SavageWolf I did try that and the gdm did not show up. I still think the problem is plymouth related

---

### Post by TeoBigusGeekus on 2011-02-18
Ok, another idea...
How did you install plymouth?
Was it a deb file or source code?

---

### Post by vacco on 2011-02-18
My suggestion is ```
sudo dpkg-reconfigure gdm
```
This should start a wizard allowing you to select gdm as default login manager (providing you have it installed).

---

### Post by ubun2geek on 2011-02-18
I totally appreciate all these helpful ideas, but like I said, the problem is related to the plymouth boot screen.
Check out this link to see what messed up (if you are advenderous ;))
[URL="http://sourceforge.net/projects/plymouthmanager/"]http://sourceforge.net/projects/plymouthmanager/
[/URL]

---

### Post by TeoBigusGeekus on 2011-02-18
Try this 
```
sudo apt-get purge plymouth-manager
```

---

### Post by Mefrio on 2011-02-19
hi I am the developer of Plymouth Manager and I read your segnalation on PM's blog. In Italy another person had your problem because he used the closed video driver function with the open video driver. Probably this is your problem

---

### Post by ubun2geek on 2011-02-19
how do you fix the problem, mefrio?

---

### Post by Mefrio on 2011-02-19
post your /etc/default/grub file

---

### Post by ubun2geek on 2011-02-19
> **Mefrio said:**
> post your /etc/default/grub file
how do I do that? Someone please help!

---

### Post by ubun2geek on 2011-02-19
> **vacco said:**
> My suggestion is ```
sudo dpkg-reconfigure gdm
```This should start a wizard allowing you to select gdm as default login manager (providing you have it installed).
Yes I have it installed and it is the default login manager.

---

### Post by ubun2geek on 2011-04-19
[QUOTE= 				**Re: Re:Help!?** 			 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **OpenOffice.org** 					 				
 				[I] 	Quote:
 	 	 		 			 				 					Originally Posted by **Mefrio** 					 				
 				[I] 	Quote:
 	 	 		 			 				 					Originally Posted by **OpenOffice.org** 					 				
 				[I] 	Quote:
 	 	 		 			 				 					Originally Posted by **Mefrio** 					 				
 				[I] 	Quote:
 	 	 		 			 				 					Originally Posted by **OpenOffice.org** 					 				
 				[I] 	Quote:
 	 	 		 			 				 					Originally Posted by **Mefrio** 					 				
 				[I] 	Quote:
 	 	 		 			 				 					Originally Posted by **OpenOffice.org** 					 				
 				*How do i do that?*
 			 		 	 	 
you have to do a chroot in the sda where is your Ubuntu and with nano you open the file /etc/default/grub[/I]
 			 		 	 	 
please talk to me like a newbie, cause I am
I honestly have no clue what you are talking bout, and i am in tty1 mode![/I]
 			 		 	 	 
can you start gnome session whith startx?[/I]
 			 		 	 	 
No[/I]
 			 		 	 	 
follow 
[it]("http://wiki.ubuntu-it.org/AmministrazioneSistema/Grub/Ripristino") until to sudo chroot /mnt

then type nano /etc/default/grub and send me it...you need of a live session to do it[/I]
 			 		 	 	 
I am afraid that you were [COLOR=Red]_NO_[/COLOR] help. I reinstalled, lost all my information, and than used Zorin OS changer. :sad:[/I]
 			 		 	 	 
if you didn't read what you were doing I do not do miracles
[/QUOTE]
Well, here is the whole discussion, folks. Those of you who tried to help, Thank you very much. I still won"t close this as it is not solved.
Thanks!

---

