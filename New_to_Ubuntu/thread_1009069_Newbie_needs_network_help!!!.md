---
title: "Newbie needs network help!!!"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by lewbram on 2008-12-12
Hey guys
I am a total newbie not long had 'intrepid' working and I am trying to linkup my laptop (XP) to share files and an internet connection.

i.s.p. is virgin cable

I have a wired router 

two network ports....one that the internet goes into. 

the ways I think it works is:-

cable from unused network port into router, then from router to lap top? 

or should it be virgin modem to router then router to desktop and laptop?

From there I have no idea how to configure it all!

any advice or tutorials anybody knows of would be a great help

Thanks

---

### Post by ibizatunes on 2008-12-12
The sharing of file with XP you will need to install samba, 
Your router should provide the internet connection to your xp and linux boxes should get the IP address from there

---

### Post by ianhaycox on 2008-12-12
Sounds like you need to change the IP address of your second router.

Not familiar with the Virgin cable setup but does the PC work connected directly to the virgin box ? If yes, then you should cable from the virgin box to your router then two cables from the new router to each pc.

Before you hook up the virgin to router connection connect your pc to the new router, power on and browse to [http://192.168.1.1](http://192.168.1.1)  Hopefully there should be a config page to change the address of the new router. Change it to something like 192.168.2.1 and save.  For ease, power everything down, connect virgin to new router, restart everything and you should be good to go.

If not, then post more details about your hardware.

---

### Post by lewbram on 2008-12-12
Thanks guys I have an exam now, will give it a go and get back to you tonight.

Thanks again

---

### Post by lewbram on 2008-12-12
Hey I have tried this but nothing happens when i browse
 [http://192.168.1.1](http://192.168.1.1) 

The current situation is 

desktop (ubuntu)
laptop (XP)

internet going into router, from router toboth desktop and laptop

can anybody help?

Thanks

---

### Post by Kellemora on 2008-12-12
Hi Lew

The IP to get into your router might be different than what was given to try.  It was just a common one used on many brands.

Ok, from your Virgin Cable the wire that comes into the house should be connected to your Modem.

Without using the Router, connect one of your PC's to the Modem to see if your Account is activated.  If not, you will have to call your cable company to have then turn you on as a subscriber.

Once you KNOW the internet is active and working, THEN place the Router between the Modem and your computer.  Most Routers are already defaulted to the proper settings and pass set-up through to your Network configuration when started.

Once you have one computer going, just plugging in the second computer to your router should get that one going also.  Internet Networking comes set up already in Ubuntu.

If all else fails, place your LIVE CD with Ubuntu on it in your CD player and reboot the computer and run it from the LIVE CD, it should Automatically connect to the internet.

You can go into your System/Administration/Network and write down the numbers you see listed under DNS.

Then remove the CD and reboot.
Go back to System/Administration/Network and check what it shows there, if different you will have to change it to what is correct.  It shouldn't be different though!

If it is come back and someone will ask for you to paste a couple of printouts.

TTUL
Gary

---

### Post by lewbram on 2008-12-13
Hey  Thanks for your advice, 

I have tried this and have the internet working on ubuntu fine, but it will not pick up the xp. Is there something that I should be doing to allow access from xp?

The router is second hand by the way....not sure if that makes a difference?! 
Thanks lew

---

### Post by ianhaycox on 2008-12-13
Good news about the Ubuntu box.

As a starting point for the XP box are there any lights illuminated on the router and the XP network card to indicate connectivity ? Just to check the cabling is OK.

BTW What make and model is your router ?

---

### Post by clive littlewood on 2008-12-13
Hi

An easy route for Samba shares is to create a "shares" folder in your documents files.

Right click on this new folder and click on share options.

It will say that shares are not activated and offer to install samba for you.

Accept and samba will be installed.

Put a file into the shares folder and open up networks in XP.

Your Ubuntu box should now be visible in XP.

You will be asked for your username and password before being given access to Ubuntu.

Hope this helps     :p

Clive

---

### Post by theozzlives on 2008-12-13
I'm gonna go out on a limb here and say it sounds like a bad cable. Do you have a cable tester? If not try switching cables and see what happens.

---

### Post by lewbram on 2008-12-13
hello!

I am at work at the moment so am trying to remember the make of the router. think it is netgear, quite old. 
The lights are on for the each of the cables placed, i have checked the cables cause i thought that may be a problem (don't even know where they came from!) but the internet works through both of them. 

Have read a little about samba and would like to use it.

I really appreciate all the help I receive from you guys.

---

