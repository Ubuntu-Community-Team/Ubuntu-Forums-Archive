---
title: "Atheros AR9485 no wireless connection, Ubuntu 15.10"
date: 2016-01-31
forum: Networking &amp; Wireless
---

### Post by jacek8 on 2016-01-31
Hello everyone,
i am newbe user of linux os, today first time i install linus os , ubuntu 15.10, it's alonside winows 10 ***which*** one i updated yesterday, everything with instalation ubuntu was ok, but i have problem with wireless internet conection, i try tips which i find in internet but nothing work, i really want use linux os but if not fix this problem with wireless internet connection I will be forced to give up. Ubuntu only connect with wired way, but i need wireless conection. Tis is my wireless-info.txt.If someone can help, please.

---

### Post by chili555 on 2016-01-31
> 3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yesIn this context, 'hard blocked' refers to the hardware wireless switch or key combination. Can you find it and switch it? Does it change the result of the terminal command:```
rfkill list all
```Welcome to the Ubuntu party! We have a lot of fun here and we're happy to have a new member!

---

### Post by jacek8 on 2016-01-31
heloo chili555, thanks for help, i don't know how swich it, can you say how do this, relly i'am newbe:), i have try commend sudo rfkill unblock all, and unbloked everything, but still i dont have any wireless conection, sorry i have checked ones again its still hard blocked:yes, mayby its windows generate this problem, i have win10 and connect to internet wireless too, i don't know, 
i try it fix still only change : 
5: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
phy0 to phy 1

---

### Post by chili555 on 2016-01-31
>  i don't know how swich it, can you say how do this,This wireless card is installed in some Asus laptop. On most every laptop, there is a switch or key combination to turn off and on the wireless; perhaps something like this: [http://i.fixya.net/uploads/images/an0n0mus_2.jpg](http://i.fixya.net/uploads/images/an0n0mus_2.jpg) Or maybe this: [http://1.bp.blogspot.com/_hM8AMxgJLzw/Ru5I_O60UgI/AAAAAAAAAQU/5FXYDv4iOaQ/s320/m5200aekillswitch.jpg](http://1.bp.blogspot.com/_hM8AMxgJLzw/Ru5I_O60UgI/AAAAAAAAAQU/5FXYDv4iOaQ/s320/m5200aekillswitch.jpg) Find it and change its position from 'OFF' to 'ON.'

Before you move the switch or press the key, run, in the terminal:```
rfkill list all
```Does it show as blocked? Now move the switch or press the key, and again run, in the terminal:```
rfkill list all
```Is it still hard blocked or is there a change in state?

---

### Post by jacek8 on 2016-01-31
still bloked i heve asus x75v, key combination nothing change, and i dont have any swich, [**[COLOR=#DD4814][B]chili555**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=35909") i'am going sick with this, i'am looking for fix and try it and nothing , you help and nothing, mayby you know other linux easy for newbe and with no internet connection problems? ubuntu looks fine but, wireless not work,

---

### Post by jacek8 on 2016-01-31
much thanks for your intresting my problm chil555, i have fixed problem using this 	sudo apt-get update
sudo apt-get dist-upgrade

i have upgared this code a coupe of hours ago but nothing happend, now hapend what i wont
it is from  [**[COLOR=#990303][B]bapoumba**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=171805") post ubuntuforums.org/showthread.php?t=370108bapoumba, thanks a lot, i thing many problems with linux befor me, but ihave positive attiude to this, thanks onece again

---

### Post by chili555 on 2016-01-31
I apologize but I don't understand your reply. Are you saying that your problem IS fixed now? Or are you saying your problem IS NOT fixed?

I have other suggestions and other things we might try so please don't give up.

---

### Post by Mel_Blakey on 2016-01-31
I think what he is trying to say is that he ran
```

sudo apt-get update

sudo apt-get dist-upgrade

```

From here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

[COLOR=#ff0000]bapoumba[/COLOR]'s thread

And it is OK now!

*Which is great because I've got a little job for you if you are not too busy* ;)

I'll start a new thread!

---

### Post by chili555 on 2016-01-31
> **Mel_Blakey said:**
> 

*Which is great because I've got a little job for you if you are not too busy* ;)

I'll start a new thread!Checking...

---

