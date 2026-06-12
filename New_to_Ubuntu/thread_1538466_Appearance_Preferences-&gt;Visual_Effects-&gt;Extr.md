---
title: "Appearance Preferences-&gt;Visual Effects-&gt;Extra"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by angiesworld on 2010-07-25
[FONT=Verdana][SIZE=2]Within my Windows 7 I have installed Virtualbox which I have installed Ubuntu 10.04
Example: ([http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)) 

With 3D Acceleration enabled on my Virtualbox and Compiz installed I want to run 3D effects. 

in Ubuntu I go to system->Appearance Preferences->Visual Effects and select "Extra". The system begins to "search for drivers" and returns an error "Desktop effects could not be enabled":(

My Host Machine:
Windows 7x64
4.00 GB RAM
2.40GHz AMD 8750 Triple-Core Processor
NVIDIA GeForce 8600GT 

What am I omitting that is causing this error??


Help! :D

~angie [/SIZE][/FONT]

---

### Post by nerdtron on 2010-07-25
You should install Virtualbox Guest Additions for your Linux Guest. This link will help:
[http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)

---

### Post by beew on 2010-07-25
Ubuntu doesn't work well with Nvidia graphic cards, it is always a headache to find and install the right drivers. I am currently trying get Ubuntu to work on a Sam Sung laptop with a Nvidia card. Plug in a live usb and all visual effects stop.

I could be wrong, I haven't been using virtual machines because my computers don't have enough ram, but I think even virtual machines need to have the drivers for the graphic cards in order to run visuals.

---

### Post by realzippy on 2010-07-25
"*Ubuntu doesn't work well with Nvidia graphic card, it is always a headache to find and install the right drivers*"

ehm,well,this is -sorry- nonsense.No better 3d performance in linux than
with nvidia cards.But,back to topic,in a virtual machine the graphics card is also *virtual*.You cannot install nvidia drivers for a virtual chip...you have to install -as formerly suggested by *nerdtron*-the *guest additions*,which should give you (poor) 3D acceleration.

@angiesworld:

BTW,why not make a *real* installation (Dualboot with your existing windows)?
Your machine should run pretty fine,your nvidia card would run perfectly (and all that fancy compiz stuff...)

---

### Post by angiesworld on 2010-07-25
RE:
You should install Virtualbox Guest Additions for your Linux Guest. This link will help:
[http://www.dedoimedo.com/computers/v...st-addons.html]("http://www.dedoimedo.com/computers/virtualbox-guest-addons.html")
 		                   		  		  		 		 			 				__________________
				[COLOR=Blue][The Philippine Team]("http://ubuntuforums.org/forumdisplay.php?f=303")[/COLOR]
The best Ubuntu derivative: [COLOR=Lime][Linux Mint]("http://www.linuxmint.com/")[COLOR=Black]
Relax. Head to the [Community Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11").[/COLOR][/COLOR]


thank you! :) 
I have been trying to change directory as is on the URL you provided... cd /media/cdrom and I keep getting, "No such file or directory"
first time it's ever done that....hmmmm
I have the iso mounted........hmmmm.

---

### Post by realzippy on 2010-07-25
maybe it is cdrom0.You can type **cd /media/** and then **ls**
to list devices..

---

### Post by philinux on 2010-07-25
> **beew said:**
> Ubuntu doesn't work well with Nvidia graphic cards, it is always a headache to find and install the right drivers. 

I afraid it's ATI cards that are currently a headache for some. Particularly older cards. NVidia is well supported.

---

### Post by angiesworld on 2010-07-25
YAH:D
Finally got it to find drivers in the Appearance.
What I had to do is after installing guest additions, go into synaptic packet manager (in system) and ubuntu software center (in applications) and delete all traces of NVIDIA. 

I believe that is where I had my conflict.....but, whooohooo it works now :)

Thank you! Thank you! Thank you! for such a quick response and detailed info.

Many Blessings......angie

---

### Post by angiesworld on 2010-07-25
> **realzippy said:**
> "

@angiesworld:

BTW,why not make a *real* installation (Dualboot with your existing windows)?
Your machine should run pretty fine,your nvidia card would run perfectly (and all that fancy compiz stuff...)

The dualboot would sound great accept for the fact that I am running dual monitors and I wish to have access to everything (Windows 7 + my Linux distro) at the same time :popcorn:

I like everything at my fingertips.........LOL

---

### Post by angiesworld on 2010-07-25
> **philinux said:**
> I afraid it's ATI cards that are currently a headache for some. Particularly older cards. NVidia is well supported.

Like [realzippy]("http://ubuntuforums.org/member.php?u=216523") stated in a virtual environment the video card is also virtual (which I discovered the hard way.......ha ha:o

My discovered solution was after installing Guest Additions I then located any and all NVIDIA files that were installed on Ubuntu (within Virtualbox) and UNINSTALLED them......

Pretty much what Guest Additions is trying to say is..."I'm in charge here, I've got the drivers you need.....get NVIDIA outta'here" LOL:KS

---

### Post by realzippy on 2010-07-26
> **angiesworld said:**
> The dualboot would sound great accept for the fact that I am running dual monitors and I wish to have access to everything (Windows 7 + my Linux distro) at the same time :popcorn:

I like everything at my fingertips.........LOL


So what about Windows7 in virtualbox in Ubuntu?  :D
Might be superior in security...

---

### Post by angiesworld on 2010-07-26
> **realzippy said:**
> So what about Windows7 in virtualbox in Ubuntu?  :D
Might be superior in security...

Well, ya know...there's a thought.....guess I'll have to grow into that idea.....really liking Ubuntu/Linux......guess when I feel as comfortable in Linux as I am in Windows...I'll probably just do that :)

---

### Post by Vanderfurff on 2010-07-27
[B]hi guys, 
i'm entire knew to linux, and things have been going pretty smoothly.  however the computer that I'm learning on is a bit older, and so I decided to reduce resource drag by setting visual effects to "none" for simple desktop environment.  


Upon reboot, nearly half of the bottom of the screen is cut off!  I've rebooted several times, but I can't get the bottom of the screen to visually return.  from reading forums, I'm come to understand (possibly?) that this was a result of my changing the the visual effects setting?  The computer itself seems to be working find despite the screen cut-off.  Even docky works.  


However, Appearance is not longer where it's supposed to be under system- preferences!  I've looked for it everywhere, and it's not to be found.  Grrr.  Arrrrgh:)  Can anyone one help me recover the lower half of my screen?  Below is the process I believe I followed earlier.  When i look under system -  preferences, the top of the scoll is now "bluetooth," and appearance is naught to be found.  


THANKYOUTHANKYOUTHANKYOU!!!!!![/B] 

**Configuring visual effects**

                                                                   	Press System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects to change basic options relating to visual effects. 	
                                
[LIST]
[*]                          	Select *None* to provide a simple desktop      	environment without any effects.     	
[*]                          	Select *Normal* to provide a good balance between      	attractiveness and performance.     	
[*]                          	Select *Extra* to provide an aesthetically pleasing      	set of graphics.     	
[/LIST]
               
                	When you select an option, it may take several seconds for the change to be  	applied. During this time, your screen may flicker briefly. 	
                	Once the settings have been applied, a dialog box will appear asking you to  	either keep the new settings or to revert to your previous settings. If you  	find that the new settings work correctly, then click  	**Keep Settings**. Otherwise click  	**Use Previous Settings**. If you do not select anything  	for 20 seconds the system will return to your previous settings.

---

