---
title: "removing admin user"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by coop_ec on 2009-02-04
hi, my tech-savy friend set up my ubuntu but and he convienently put himself in as an admin. When I go into system>admin>users and groups i see his login but it is grey and i can't access it. Could someone tell me how to remove it or change it to an account that is not an admin. (Everyone needs a little privacy). thx very much.

---

### Post by petervk on 2009-02-04
Is there an unlock button on the User Settings window? Because you have to hit that first to make any changes.

And if your talking about a "root" account, don't delete that, just change the password.

---

### Post by coop_ec on 2009-02-05
O.K., I found the unlock button and that helped so here's my new question. I took some screenshots. I am the admin "coop" and i was wondering if the login "lsd" (that's my friend) could access my computer via the internet without my permission or would i have to lgive him access. Thanks for the help.

---

### Post by cancerdude on 2009-02-05
> **coop_ec said:**
> O.K., I found the unlock button and that helped so here's my new question. I took some screenshots. I am the admin "coop" and i was wondering if the login "lsd" (that's my friend) could access my computer via the internet without my permission or would i have to lgive him access. Thanks for the help.

Reinstall yourself, he may be a friend but so am I.

---

### Post by Bölvaður on 2009-02-05
There are few ways he could have given him access. But you need to have static ip botn on your router and on your computer... unless if he did some trojan stuff but I'd doubt it.

1. VNC
2. NFS
3. SSH


1 - VNC (remote access to your desktop.. that is mouse/keyboard/"monitor")
open up synaptic package manager (system&#8594;administrator&#8594;synaptic..)
and type vnc in the edit box there to filter the list. If there is no package with dark green box next to it whose name includes "server" then you are safe.
But if you find a vnc server installed, you can click on the box next to it and choose "complete removal" and press apply.

2 - NFS (shared directories)
Have synaptic still open and search for "nfs-kernel-server".

3 - SSH
just do the same thing as above, just type in ssh and look for something named server. and if it does have a green box next to it indicating that it is installed.. uninstall it.

I think you should do your own installations in the future as it is very simple. You will trash your first installation any way by tweaking... and if you dont trash it then you arent trying enough stuff out ^^ that way you'll learn.... and follow this forum.. these forums are great help for knowing what is possible.

---

### Post by presence1960 on 2009-02-05
> I think you should do your own installations in the future as it is very simple. You will trash your first installation any way by tweaking... and if you dont trash it then you arent trying enough stuff out ^^ that way you'll learn.... and follow this forum.. these forums are great help for knowing what is possible.

+1

Trying stuff out is the key. If you hit any snags the community here is light years ahead of any tech support on this planet. Because of the help in here I learned how to create a separate /home partition which makes reinstallation or new install a snap with my data and settings preserved. Because of member Kilz's superb posts I stopped listening to the naysayers and went ahead and installed 64 bit. It was pretty easy too getting everything to work including flash & java. I was dual booting because I need Adobe Acrobat professional for work. I got rid of Windows partition and run XP in Sun Virtual Box with only Adobe installed. Eventually I hope to get good enough at open source to get rid of the XP in virtual box too. I am 99% free now and it feels great. The hard disk which had XP now has Linux Mint 64 bit on it. I like it and Kubuntu 8.10 64 bit. I haven't decided yet which one to keep so for now I dual boot those 2.
 If you mess up and have to reinstall this isn't like setting up windows, you won't need 2 pots of coffee. Here is how great this forum is : I never had to create a thread for any problem I have had and God knows I have had a few! I just did a search of the pertinent terms of my problem and I got previous threads which dealt with the same thing. A little reading and I find my answer and then the problem is solved. You can't beat that, no press 1 for English, no waiting on hold and no credit card to pay for the support call. Hope you find this as enjoyable as I have. Good luck and good learning.

---

### Post by Locutus_of_Borg on 2009-02-05
```
sudo -i
userdel LOGIN_NAME
exit

```


don't delete the login 'root' though

---

### Post by presence1960 on 2009-02-05
Locutus_of_Borg : Great name!!!! That episode is my fav  TNG episode. Just thought I'd tell you that.

---

### Post by Locutus_of_Borg on 2009-02-05
haha yeah it's a good one

---

### Post by coop_ec on 2009-02-06
Wow, thx for the replies, guys! O.K., Locutus I tried your command and here's what I get:(Screenshot 1) although the 1st time I put it in it asked for my password. So what should I do next? Thx.

This part is for bolvaour and presence, This is my 3rd install and the reason I had my friend help is b/c my video card not only needed proprietary drivers but I couldn't get compiz to work w/out them only when I would try to install my sys would mess up (not install correct, no display, etc..). so I would rather not reinstall but I am eager to learn as much as possible about Ubuntu/Linux/Computers. So much so I wiped win xp off my comp for now!(Microsoft is getting ridiculous about crashing, problems, etc...) I would also like to meet friends on here to help me and then I hope to return the favour. And bolvaour, don't I need: VNC, NFS,SSH, or something similar in case a friend (on here or otherwise) is able to fix my computer or show me something by accessing my desktop remotely? Well, thanks sooooooo much guys! Ubuntu is the BEST OS known to HUMANS!

---

### Post by Bölvaður on 2009-02-06
> **coop_ec said:**
> And bolvaour, don't I need: VNC, NFS,SSH, or something similar in case a friend (on here or otherwise) is able to fix my computer or show me something by accessing my desktop remotely?

Umm., well VNC and SSH might be useful for fixing small problems but I wouldn't do it. Much better to learn the system by copy and pasting commands your self instead of some random people doing random stuff to my system ^^.


btw that command "sudo -i" works fine. When you enter it you will be asked for a password, which is your password. You need to enter it even though you will not see typical ****  or other visual confirmation of you typing in stuff. They keyboard is still working.

You can also do "sudo su" and the second command he gives you, you obviously need to change the user name to the one you need to delete.

---

### Post by presence1960 on 2009-02-06
Coop, I tried locutus's command and it works on both Mint and kubuntu. It takes me to root@raz Desktop at which point I would then enter the command > userdel raz
Here is the shot of that terminal for you

---

### Post by coop_ec on 2009-03-04
Well, thanks to a little app called "envyng" or "envy" and using the 96 driver (nvidia) I was able to re-install and set up by myself! What a long way I've come......using terminal and everything! Well I hope this helps someone else.
Thx

---

