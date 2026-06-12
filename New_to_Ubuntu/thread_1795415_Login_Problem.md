---
title: "Login Problem"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by JASONFUSARO on 2011-07-02
I re-installed UbuntuStudio 

I backed up the Ubuntu partition and Root partition using lucky backup.

I dd a MBR backup

I then proceeded to try and make a boot USB so I could experiment with Grub on the USB.


In the course of doing that I tried to copy a file from the hard drive to the USB and did not have permission so I ran chmod on the subdirectory and that started the ball rolling again with more permission acces errors and before correcting them I did a reboot and now I can't even access the internet nor can I run lucky backup to restore anything because It's telling me I don't have permission to run that either!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!


The chmod I ran 777 which I assumed would give total access, now I can't run su, sudo, smooo, grooo, fu


this linux crap is starting to get tiresome, I have been rebooting and re-installing for the past month or so. I am not productive at all.


I at least was productive running windows.


There must be a way of running the system and bypassing all the damned password restictions, I mean they don't seem to be making any difference you can still screw up the system while they are in place, so it makes more sense that you have total access and at least you won't be slowed down by the accumulation of problem upon problem.


Scouring the internet for help is also no help, if you are not sure of the Grub or system that the help is being put out there then typing any of those commands unless your absolutely  certain they will run in your environment is like having some c4 on your computer one wrong command entry and  kaboom!!!!!!


The error I am getting at login is 

Permission to setuid helper is not correct


now I never set anything on that all I did was ran chmod 777 -p / 



How the hell can I bypass and overide the damned access permisions???


I thought my setting my username in all the groups and even putting my self in the root group would stop this stuff from happening, yet I am still running into problems.



Why  if I belong to every group from adm to Hong Kong Jong is this happening???????????


PLease, Please, Please help

---

### Post by JASONFUSARO on 2011-07-02
I just did a search on that error and ubuntu has to one asking for help the other offering help

```
 				 				**Re: "The permission of the setuid helper is not correct"** 			
 			 			 		   		 		 		Bit late, but may help someone. I also got the same error recently and it seems like a problem with dbus.
Here's how I fixed it :
log in tty1 console as root
stop gdm
startx
Now if you are able to see the desktop, connect to the internet and reinstall dbus related stuff from synaptic.

```



Now my question is this how the helll do you log into tty1 console as root


explain please, now I have to scan damn google listings, how many 2, 10 , 20  before I fgure out what the help means.

and in the course of the google search I undoubtably will become more confused.


then I have to search gdm


then startx



a simple damn explanation at the beginning of the command list would be more than helpful, thats what help is all about helping not confusing the situation. It appears that this is the case over and over again. The help tends to be more problematic than helpful. Everyone offering help tends to assume you know what the hell they are talking about 9 times out of ten. 

If that were the damned case why would I be looking for help.


This would appear that I am rambling on again but if you get anything at all out of reading this is that if you offer some assistance to anyone please take some time to explain the commands, what tehy are attempting to accomplish, what system, version, etc. your running, what dependencie packages might have to be installed before they will work etc..


Otherwise it might not be help but a wolf in helps clothing

---

### Post by JASONFUSARO on 2011-07-02
> **JASONFUSARO said:**
> I just did a search on that error and ubuntu has to one asking for help the other offering help

```
                                  **Re: "The permission of the setuid helper is not correct"**             
                                                                Bit late, but may help someone. I also got the same error recently and it seems like a problem with dbus.
Here's how I fixed it :
log in tty1 console as root
stop gdm
startx
Now if you are able to see the desktop, connect to the internet and reinstall dbus related stuff from synaptic.

```Now my question is this how the helll do you log into tty1 console as root


explain please, now I have to scan damn google listings, how many 2, 10 , 20  before I fgure out what the help means.

and in the course of the google search I undoubtably will become more confused.


then I have to search gdm


then startx



a simple damn explanation at the beginning of the command list would be more than helpful, thats what help is all about helping not confusing the situation. It appears that this is the case over and over again. The help tends to be more problematic than helpful. Everyone offering help tends to assume you know what the hell they are talking about 9 times out of ten. 

If that were the damned case why would I be looking for help.


This would appear that I am rambling on again but if you get anything at all out of reading this is that if you offer some assistance to anyone please take some time to explain the commands, what tehy are attempting to accomplish, what system, version, etc. your running, what dependencie packages might have to be installed before they will work etc..


Otherwise it might not be help but a wolf in helps clothing





I tried it but have no idea what the root password is I thought I did but after entering it and was told It wasn't I now have no clue.


stop gdm gives errors


so this help as I thought is useless, uterly!!!!!

and now I think I am possibly looking at another &&&&&(*& re-install!!!!!!!!!!!!!!!!!!


:guitar::lolflag:  :-\" =D>  :biggrin:  :roll:  \\:D/ :-({|=

---

### Post by JASONFUSARO on 2011-07-02
apparently this is how you stop gdm


sudo /etc/init.d/gdm stop

remember the last post he said

Here's how I fixed it : log in tty1 console as root stop gdm startx

now I am going to reboot and try that, I may or may not be back???

---

### Post by JASONFUSARO on 2011-07-02
I tried 

sudo /etc/init.d/gdm stop


and guess what


sudo: must be setuid root



I would probably be having more fun if someone slipped LSD in my drink blindfolded me and dropped me off in the Bronx at midnight







I am glad that I have Toorox instaled on USB, it takes just under a minute to bootup and get me logged on to the internet.



I am starting to think it might be better to just run a system off a USB and forget installing on my Hard Drive. Might get rid of the headaches.


I think I'll start searching that, I wonder if you can have just you home on the hard drive and just attach it after bootup, might be easier that way. 


If you can decipher this post and offer any suggestions I would be greatful.


Until then I'll be G):P:-\"gling

---

### Post by JASONFUSARO on 2011-07-09
I did it I did a complete re-install starting from windows on up so that's the end of this post, but I have still run into problems, see my ne unsolved post.

---

