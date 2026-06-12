---
title: "I have Wireless Card SMC 2802W and SMC2870W Wireless Adapter will it be ok for ubuntu"
date: 2005-07-25
forum: Networking &amp; Wireless
---

### Post by Spyware on 2005-07-25
I have Wireless Card SMC 2802W and SMC2870W Wireless Adapter will it be ok for ubuntu?

Will i be abile to use internet?

thanks in adwance for help

 :mrgreen:

---

### Post by majikstreet on 2005-07-25
[QUOTE=Spyware]I have Wireless Card SMC 2802W and SMC2870W Wireless Adapter will it be ok for ubuntu?

Will i be abile to use internet?

thanks in adwance for help

 :mrgreen:[/QUOTE]
 I'm not sure if it will work out-of-the box but I'm sure with ndiswrapper it should work.

btw, there are plenty of posts about ndiswrapper to help you.

---

### Post by Spyware on 2005-09-14
I have Wireless Card SMC 2802W and SMC2870W Wireless Adapter will it be ok for ubuntu?  Breezy Badger ?

Will i be abile to use internet?

and how to find out if my card is detected?

thanks in adwance for help

---

### Post by Spyware on 2005-09-14
if you want more information please ask

---

### Post by Spyware on 2005-09-28
call to all ubuntu developers

please support Wireless Card SMC 2802W and SMC2870W Wireless Adapter in this ubuntu release

---

### Post by az on 2005-09-28
If they are the 802.11g cards, I think they are prism54 based, which have GPL drivers in the linux kernel.  You should be good to go.

If not, you can use ndiswrapper.

---

### Post by Spyware on 2005-11-05
[]("http://www.ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=31588")I have Wireless Card _**[COLOR=Red]SMC 2802W[/COLOR]**_ and SMC2870W Wireless Adapter will it be ok for ubuntu?  Breezy Badger ?
[CENTER][LEFT]  
 Will i be able to use [COLOR=Red]**internet?**[/COLOR]
 
 and how to find out if my card is detected?
 
 thanks in advance for help

call to all ubuntu developers
 
 please support Wireless Card SMC 2802W and SMC2870W Wireless Adapter in this ubuntu release

[/LEFT]
  [/CENTER]

---

### Post by Spyware on 2005-11-05
Wireless, wireless, wireless...all I got to say..It was impossible for me to set up my Wireless Card _**[COLOR=Red]SMC 2802W[/COLOR]**_ and SMC2870W Wireless Adapter on hoary, thought breezy would fix that but nope. No internet on ubuntu isn't gonna work for me, not being able to get upgrades, updates, packages and whatnot...sorry just not gonna work..the new ubuntu NEEDS better wireless support..
 
 I have Wireless Card _**[COLOR=Red]SMC 2802W[/COLOR]**_ and SMC2870W Wireless Adapter will it be ok for Kubuntu?
    
    Will i be able to use [COLOR=Red]**internet?**[/COLOR]
    
    thanks in advance for help
   
   call to all [COLOR=Red]**[SIZE=5]Ubuntu and [/SIZE]**[/COLOR][COLOR=Red]**[SIZE=5]Kubuntu [/SIZE]**[/COLOR][COLOR=Red]**[SIZE=5]developers[/SIZE]**[/COLOR]
    
    please support Wireless Card SMC 2802W and SMC2870W Wireless Adapter in this ubuntu release

---

### Post by Spyware on 2005-11-06
Wireless, wireless, wireless...all I got to say..It was impossible for me to set up my Wireless Card _**[COLOR=Red]SMC 2802W[/COLOR]**_ and SMC2870W Wireless Adapter on hoary, thought breezy would fix that but nope. No internet on ubuntu isn't gonna work for me, not being able to get upgrades, updates, packages and whatnot...sorry just not gonna work..the new ubuntu NEEDS better wireless support..

I have Wireless Card _**[COLOR=Red]SMC 2802W[/COLOR]**_ and SMC2870W Wireless Adapter will it be ok for ubuntu?
   
   Will i be able to use [COLOR=Red]**internet?**[/COLOR]
   
   thanks in advance for help
  
  call to all [COLOR=Red]**[SIZE=5]ubuntu developers[/SIZE]**[/COLOR]
   
   please support Wireless Card SMC 2802W and SMC2870W Wireless Adapter in this ubuntu release

or this is mision imposible?

---

### Post by Spyware on 2005-11-06
Wireless, wireless, wireless...all I got to say..It was impossible for me to set up my Wireless Card _**[COLOR=Red]SMC 2802W[/COLOR]**_ and SMC2870W Wireless Adapter on hoary, thought breezy would fix that but nope. No internet on ubuntu isn't gonna work for me, not being able to get upgrades, updates, packages and whatnot...sorry just not gonna work..the new ubuntu NEEDS better wireless support..
 
 I have Wireless Card _**[COLOR=Red]SMC 2802W[/COLOR]**_ and SMC2870W Wireless Adapter will it be ok for ubuntu?
    
    Will i be able to use [COLOR=Red]**internet?**[/COLOR]
    
    thanks in advance for help
   
   call to all [COLOR=Red]**[SIZE=5]ubuntu developers[/SIZE]**[/COLOR]
    
    please support Wireless Card SMC 2802W and SMC2870W Wireless Adapter in this ubuntu release
 
 or this is mision imposible?

p>S.
sorry but i am frustrated, i like ubuntu so much,but without internet its just usles os for me

---

### Post by prasys on 2005-11-06
You can always wrap windows drivers with ndiswrapper. I think its possible. It should be no problem. Read one of the guides at the wiki on how-to install drivers with ndiswrapper

---

### Post by nightfly on 2005-11-06
> 
call to all ubuntu developers

please support Wireless Card SMC 2802W and SMC2870W Wireless Adapter in this ubuntu release


You should be aware that it is the responsibility of the card manufacturer to write drivers for its own hardware.

---

### Post by mips on 2005-11-06
For the SMC2870W you simply have to load the right firmware to make it either an AP or a Bridge. Then connect with the right  cable depending on device you are connecting to seeing it has no auto MDI MDI-X or a hardware switch. So you have use either a straight or crossover ethernet cable. This has nothing to do with Linux or Ubuntu.

Your SMC 2802W could probably be made to work. It uses a Prism chipset which seems to be supported under Linux. There is even an entire site dedicated to it,   [http://prism54.org/](http://prism54.org/)  unfortunately it is in the process of moving so lots the links are broken.

The forums link on the above website works and I have found a good few threads involving the SMC 2802W card.

Might have to play around with acpi settings. I suggest reading all the post on this card and then formulating a plan.

I did a simple search in the ubuntu forums for 'SMC 2802W' and this guy got it to work under hoary  [http://ubuntuforums.org/showthread.php?t=27916](http://ubuntuforums.org/showthread.php?t=27916)

---

### Post by mlomker on 2005-11-06
> please support Wireless Card SMC 2802W and SMC2870W Wireless Adapter in this ubuntu release

It isn't up to Ubuntu to support anything--it'd be up to SMC to release drivers for their card.  You're yelling at the wrong people.  There are also very few developers on this forum--they hang out in the IRC chat channels.

Are you saying that ndiswrapper doesn't work?

---

### Post by Spyware on 2005-11-06
[quote=mlomker]It isn't up to Ubuntu to support anything--it'd be up to SMC to release drivers for their card. You're yelling at the wrong people. There are also very few developers on this forum--they hang out in the IRC chat channels.

Are you saying that ndiswrapper doesn't work?[/quote] 

i realy hope that ubuntu isn't microsoft 
and the altitutde is to human being not to corporations

what i want that my computer could use internet

so for what these forums are

just for saying that ubuntu is toward humaity, human beiings?

if i cant say that this damn thing dont work

so is it such an imposible job to make it work?

[B][COLOR=Red] can someone contact developers and ask if they going to make my card work or not?
[/COLOR][/B] 
so i can deside should i use ubuntu or windows

or maybe there is linux distro which can use my Wireless Card _**[COLOR=Red]SMC 2802W[/COLOR]**_ and SMC2870W Wireless Adapter

---

### Post by mlomker on 2005-11-06
> I can someone contact developers and ask if they going to make my card work or not?

If you believe there is a bug in a package then you can use the Bugzilla link at the top of the page to file a report.

So far you haven't described what you've tried to do.

A web search suggests that the card uses the Prism54 chipset.  Have you tried [loading the driver]("http://www.ubuntuforums.org/showthread.php?t=27916")?

I also see that you opened many threads on the same topic.  In the future please only open one thread for a problem, in the appropriate forum.

---

### Post by mips on 2005-11-06
You are just complaining that things dont work and dishing out blame left and right. You havent told anybody what you have done so far or given a clear description of the problem.

Have you actually looked at any of the advice or links given for you to follow ?

---

### Post by MightyMouse on 2005-11-06
Check ot this one by "remmelt"

[http://ubuntuforums.org/showthread.php?t=27916](http://ubuntuforums.org/showthread.php?t=27916)
Worked for me and my SMC2802W

MightyMouse

---

### Post by mips on 2005-11-07
Have you had any luck so far ?

---

