---
title: "bottom of screen has been blacked out!"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Vanderfurff on 2010-07-27
[B]hi guys, 
i'm entire knew to linux, and things have been going pretty smoothly.   however the computer that I'm learning on is a bit older, and so I  decided to reduce resource drag by setting visual effects to "none" for  simple desktop environment.  
  
Upon reboot, nearly half of the bottom of the screen is cut off!  I've  rebooted several times, but I can't get the bottom of the screen to  visually return.  from reading forums, I'm come to understand  (possibly?) that this was a result of my changing the the visual effects  setting?  The computer itself seems to be working find despite the  screen cut-off.  Even docky works.  
  
However, Appearance is not longer where it's supposed to be under  system- preferences!  I've looked for it everywhere, and it's not to be  found.  Grrr.  Arrrrgh:)  Can anyone one help me recover the lower half  of my screen?  Below is the process I believe I followed earlier.  When i  look under system -  preferences, the top of the scoll is now  "bluetooth," and appearance is naught to be found.  
  
  
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

### Post by overdrank on 2010-07-27
Please do not create multiple threads on the same issue. [Duplicate here]("http://ubuntuforums.org/showthread.php?p=9644876#post9644876").  thread closed :)

---

### Post by themusicalduck on 2010-07-27
I'm not sure why Appearance would disappear from your menus, but here is another way of opening it -

Press alt+f2 and in the box enter ```
gnome-appearance-properties
``` then hit enter. If the menu item really has disappeared then you could re-add it by right clicking on the top left menu, and clicking Edit Menus. Then Add Item and use gnome-appearance-properties as the command.

The black box is probably because of Docky. It needs effects running to work properly, so a black box will appear around it.

If you don't want to run Compiz then you could try using Metacity compositing to see if it's faster. Near the bottom of this article tells you how to enable it - [http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)

EDIT: just thought, hope this isn't obvious. When you are on the Preferences menu, have you tried scrolling up? For me there are 3 items before "Bluetooth".

---

