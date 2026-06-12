---
title: "Ubunbtu 10.04 Grrrr"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by cliff0108 on 2010-05-21
This is ridiculous.
I have replaced my old Breezy Badger with 10.04 in a dual boot system.
Now my sound is scratchy with my feedback and the mic will NOT work.
I have researched the issue on the forums - read various guides and 'how-to's' and am getting nowhere !
I have posted my issues twice and have received no responses whatever.
I am very disappointed because Ubuntu is quite unusable for me in it's present state.

---

### Post by -humanaut- on 2010-05-21
Did you upgrade from Breezy Badger - Lucid Lynx or do a Clean install. I can tell you right now if you upgraded thats what causing all the problems.

---

### Post by cliff0108 on 2010-05-21
Fresh install.
Sound was perfect in Breezy and in XP
Also webcam won't work for Skype but I can live without that.

---

### Post by -humanaut- on 2010-05-21
Click the sound icon go to sound preferences and make sure the hardware is correct and make sure the microphone input volume is amplified.

---

### Post by cliff0108 on 2010-05-21
Microphone volume indicator shows UNamplified.
How do I amplify ?

---

### Post by -humanaut- on 2010-05-21
You should just be able to slide it.

---

### Post by cliff0108 on 2010-05-21
Under Sound Preferences there is a dialogue box and when I go to "input" it shows Input Volume Unamplified 100%. There doesn't seem to be a slider or control that changes unamplified to amplified unless I am missing something..

---

### Post by cetoka on 2010-05-21
> Also webcam won't work for Skype but I can live without that. 	

in order to have a more easy life, ive created  a file in /usr/local/bin called skype that superseeds the binary in  /usr/bin/ which is in charge of running skype...

type
 	Code:
 	$ sudo gedit /usr/local/bin/skype 
and paste the following 2 line
 	Code:
 	#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype 
then make it executable
 	Code:
 	$ sudo chmod a+x /usr/local/bin/skype 
no more crazy command typing :grin: just run with the  shortcut, or alt-f2 and type skype
 		                   		  		  		  		  		  	  This post made my skype video to work

---

### Post by cliff0108 on 2010-05-22
Thanks cetoka
Unfortunately while this turns my webcam on the 'screen' show consists only of coloured bands.
I suspect it's because of the webcam brand a NexxTech
If you know if a brand that WILL work I will get it.
Also my mic function will not work :o(

Thanks for your suggestion.
Should I leave  or delete the new edits ?

Cliff

---

### Post by izark47 on 2010-05-22
Sounds to me like a driver issue,  Click on System, top left.  then click on administration>Hardware Drivers, and verify that you have the latest drivers for your sound card.

---

### Post by cliff0108 on 2010-05-22
Good thought !
Will give it a try when I get back and report if that worked
Thanks.
C

---

### Post by cliff0108 on 2010-05-23
I did this and the only update related to my NVIDA graphics card - niothing related to the Fund Fusion CS46 sound card - so I assume that's up to date.
Output seems better now - just the damn mic ! :o)

---

### Post by Copperline on 2010-05-23
Hi - this is probably not going to work but you could try it just in case!

[http://embraceubuntu.com/2005/12/05/fixing-the-errant-microphone/](http://embraceubuntu.com/2005/12/05/fixing-the-errant-microphone/)

(alsamixer is in the repos)

---

