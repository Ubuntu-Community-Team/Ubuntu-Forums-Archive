---
title: "Screen resolution"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by littlboz on 2010-04-04
hello, I am a complete beginner and I need help adjusting my screen to      1280 x 1024 (I think). I am using Karmic Koala 9.10

My screen is a "lg flatron W1943TB-pf 1280"

If I go into system>preferences>display the resolution can only be as high as 800 x 600.

I read earlier posts on this but they were over my head.

Happy Easter if that's your holiday, if not I hope you have a wonderful day.

---

### Post by littlboz on 2010-04-04
is it okay if I.......bump.

---

### Post by littlboz on 2010-04-04
hmm I should probably post this in desktop environment

---

### Post by littlboz on 2010-04-04
hello, I am a  complete beginner and I need help adjusting my screen to      1280 x  1024 (I think). I am using Karmic Koala 9.10

My screen is a "lg flatron W1943TB-pf 1280"

If I go into system>preferences>display the resolution can only be  as high as 800 x 600.

I read earlier posts on this but they were over my head.

Happy Easter if that's your holiday, if not I hope you have a wonderful  day.

---

### Post by littlboz on 2010-04-04
hello, I am a  complete beginner and I need help adjusting my screen to      1280 x  1024 (I think). I am using Karmic Koala 9.10

My screen is a "lg flatron W1943TB-pf 1280"

If I go into system>preferences>display the resolution can only be  as high as 800 x 600.

I read earlier posts on this but they were over my head.

Happy Easter if that's your holiday, if not I hope you have a wonderful  day.

---

### Post by Cam42 on 2010-04-04
Do you turn your monitor on before you boot your computer? If I don't, I get the same issue. Reboot, but keep your monitor on.

---

### Post by littlboz on 2010-04-04
> **Cam42 said:**
> Do you turn your monitor on before you boot your computer? If I don't, I get the same issue. Reboot, but keep your monitor on.


nope that didn't work. I tried doing this however,

"xrandr -s 1366x768"

but i just got

"size 1366x768 not found in available modes.

---

### Post by littlboz on 2010-04-04
[IMG]http://ubuntuforums.org/images/rank_2.png[/IMG]
 			  			  			 				 
				Join Date: Apr 2010
 				 				 	  					Beans: 35 				
 			   				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				 				**Screen resolution** 			
 			 			 		   		 		 		hello, I am a  complete beginner and I need help adjusting my screen to      1280 x  1024 (I think). I am using Karmic Koala 9.10

My screen is a "lg flatron W1943TB-pf 1280"

If I go into system>preferences>display the resolution can only be  as high as 800 x 600.

I read earlier posts on this but they were over my head.

Happy Easter if that's your holiday, if not I hope you have a wonderful  day.

---

### Post by littlboz on 2010-04-04
oh, just a bit more information

I am dual booting with windows and my ubuntu version is 64 bit Karmic Koala 9.10.
I partitioned ubuntu as the following:

Swap as 2GB
root as 15GB 
home as 30GB (I think)

---

### Post by tom.swartz07 on 2010-04-04
> **littlboz said:**
> [IMG]http://ubuntuforums.org/images/rank_2.png[/IMG]
 			  			  			 				 
				Join Date: Apr 2010
 				 				 	  					Beans: 35 				
 			   				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				 				**Screen resolution** 			
 			 			 		   		 		 		hello, I am a  complete beginner and I need help adjusting my screen to      1280 x  1024 (I think). I am using Karmic Koala 9.10

My screen is a "lg flatron W1943TB-pf 1280"

If I go into system>preferences>display the resolution can only be  as high as 800 x 600.

I read earlier posts on this but they were over my head.

Happy Easter if that's your holiday, if not I hope you have a wonderful  day.

Hiya!

Thanks for the Easter wishes! 

Could you please check and see if you have the correct Video Card driver installed? On the top panel, Select System>Administration>Hardware Drivers. Allow this application to scan your system for hardware and possible drivers for it. 

HOPEFULLY, you will have a video card driver listed there. Activate it and you should be all set. 

Is this display an official 'PC Monitor' or is it a TV with a VGA input? I have seen that some computers have problems recognizing the inputs on televisions....

---

### Post by Elo! on 2010-04-04
If you open up the terminal and enter xrandr, you'll see your possible screen resolutions (this is a more complete list than you would normally see). If 1280 x 1024 is listed there (or is under the maximum it gives you), then you can change it manually by entering: xrandr --output LVDS --mode 1024x768

---

### Post by overdrank on 2010-04-04
Hi and welcome, please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by tsp_2177 on 2010-04-04
i was gonna ask if you had installed the latest drivers for your video card but i think everyone has that covered :popcorn:

---

### Post by littlboz on 2010-04-04
My deepest apologies about multiple threads, I thought that was rather cruel as well.

okay, so I first did xrandr
and it states my screen is "minimum 320 x 240, current 800 x 600, maximum 800 x 600"
it also states below this line "default connected 800x600+0+0 0mm x 0mm

okay. for hardware drivers it states the following:
NVIDIA accelerated graphics driver (version 173)
NVIDIA accelerated graphics driver (version 185) [Recommended]
NVIDIA accelerated graphics driver (version 96)

I am going to activate the recommended version and I'll let you guys know how it goes.

---

### Post by littlboz on 2010-04-04
okay restarted and then click on system

got this message with a nice blue question mark next to it,
"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphic driver vendor's tool instead?"

states yes and then no...

alright, not going to take initiative to say yes because no is automatically highlighted, quite discouraging.


Edit: lol alright, so I clicked yes .NVIDIA X server setting opens up and I can access it from the systems tab which is lovely. Within it I can change my resolution just fine.

thanks everyone

---

### Post by tom.swartz07 on 2010-04-04
> **littlboz said:**
> okay restarted and then click on system

got this message with a nice blue question mark next to it,
"It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphic driver vendor's tool instead?"

states yes and then no...

alright, not going to take initiative to say yes because no is automatically highlighted, quite discouraging.

That should fix it! Let us know how it works

---

### Post by littlboz on 2010-04-04
hey tom check my edit above your post.

once again thanks everyone I am super satisfied, you all are amazing and wonderful peeps!!!

---

### Post by rulitawyn on 2010-04-22
glad to see that someone else is having success in this problem mine is the same as his only when i follow the same instructions i dont resolve my issue. with the correct driver installed and after rebooting i go to change my resolution using the nvidia software the highest rez i can get is still 640x480 please tell me i missed something here i have read this and several other threads many times and tried more stuff than i can remember. typed about a hundred lines of stuff i dont understand into terminals because it worked for people with similar problems but no luck. I'm not looking to get some huge graphical breakthrough that lets me play intense games i just want to be able to open a few cheap games from the software center and not have to worrie about not being able to get to see enough of the window to even get to the options menu or exit button.

---

### Post by realzippy on 2010-04-22
[http://ubuntuforums.org/showpost.php?p=9158917&postcount=4](http://ubuntuforums.org/showpost.php?p=9158917&postcount=4)

---

