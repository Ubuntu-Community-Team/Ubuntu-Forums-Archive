---
title: "clickpad multi touch problem on ubuntu!urgent help needed!"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by human75 on 2010-08-13
hi guys.
i bought hp 4520s pro book and has got new technology clickpad which supports multi touch scrooling etc...i am having 2 major problem now.could you please help?
1-clickpad(touch pad) right click is not  working?is there anyway to fix this?
2-how can i make multi touch and two finger scrooling working?
Thanks in advance

---

### Post by jtarin on 2010-08-13
No time to help but [here ]("http://ubuntuforums.org/showthread.php?t=1388164")is a read on the subject and a fix for some....

---

### Post by Joe of loath on 2010-08-13
Just a tip, don't put 'URGENT!' or similar in your thread title, especially when it's not urgent in the slightest. It won't make people click on your thread first, and often people will skip past it, as they see you as a bit of an idiot ;)

---

### Post by human75 on 2010-08-13
> **Joe of loath said:**
> Just a tip, don't put 'URGENT!' or similar in your thread title, especially when it's not urgent in the slightest. It won't make people click on your thread first, and often people will skip past it, as they see you as a bit of an idiot ;)
Thanks for advise:)i will do so.

---

### Post by human75 on 2010-08-13
> **jtarin said:**
> o time to help but [here ]("http://ubuntuforums.org/showthread.php?t=1388164")is a read on the subjedt and a fix for some....
thanks for your quick response.i will try this solutions.have a nice day.

---

### Post by warfacegod on 2010-08-13
Have you looked in System> Preferences> Mouse> Touchpad tab?

---

### Post by Mike Krall on 2010-08-13
> **warfacegod said:**
> Have you looked in System> Preferences> Mouse> Touchpad tab?

I've got an ASUS UL50Ag with ELAN Smart-Pad and there is no Touchpad tab under Mouse and there isn't a Touchpad area separately under Preference... running brand new, unmodified 10.04 32bit.

Mike

---

### Post by warfacegod on 2010-08-14
You may find this useful: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by human75 on 2010-09-03
**Re: HP Mini 210 touchpad right click not working** 			
 			 			 		   		 		 		To get the  trackpad working correctly you need to use the terminal and enter in the  below commands. Make sure you press enter after each command:

     	Code:
 	sudo su 
     	Code:
 	echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe 
     	Code:
 	reboot 

Once the computer reboots your trackpad will be able to do left click and drag and right clicking.
-----------------
after i applied this commands my right click start to work again but i lost my edge scrooling now.is there anyway to fix edge scooling?thanks a lot..

---

### Post by pr1vatepiles on 2010-09-07
> **human75 said:**
> **Re: HP Mini 210 touchpad right click not working**             
                                                                To get the  trackpad working correctly you need to use the terminal and enter in the  below commands. Make sure you press enter after each command:

         Code:
     sudo su 
         Code:
     echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe 
         Code:
     reboot 

Once the computer reboots your trackpad will be able to do left click and drag and right clicking.
-----------------
after i applied this commands my right click start to work again but i lost my edge scrooling now.is there anyway to fix edge scooling?thanks a lot..

thanks for that got me working great. never liked the scrolling on the edge anyhow so i can live without. isn't there an option in mouse settings for that anyhow if you wanted it back?

---

