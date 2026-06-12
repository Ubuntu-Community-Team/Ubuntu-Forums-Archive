---
title: "(EE) SAVAGE(0): and low graphics mode error"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by ufireup on 2009-02-05
When asking for login my screen goes black and then the following appears:

Ubuntu is running in low-graphics mode
You may need to update your configuration to solve this.

(EE) SAVAGE(0): Unknown EDID version 2
(EE) SAVAGE(0): No valid modes found
(EE) Screens found, but none have a usable configuration.

I'm using an old CRT monitor if that would affect it.
I have tried the xfix and anything else I do just makes my screen go black.

Please help me understand this! 

IF MORE INFO IS NEEDED~ LET ME KNOW!! Thank you!

---

### Post by kerry_s on 2009-02-05
with savage driver on my t20 i have to put:

in the driver section:
```
Option "BusType" "PCI"
```

and specify the screen size and depth:

```
Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 16 
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes "1024x768"
	EndSubSection
EndSection

```

---

### Post by ufireup on 2009-02-05
I understand what you mean about the screen section. But what do you mean exactly when you say driver section? is that in the xorg file also?

---

### Post by ufireup on 2009-02-05
Alright, I entered this all into the xorg config file.. 
Nothing changed. I'm trying to save my log file to post but it's on a separate computer. 

Any more advice from here?

---

### Post by kerry_s on 2009-02-05
boot into the failsafe mode and run> X -configure
that will give you a /root/xorg.conf.new it should have all the options for the savage driver in it.
to replace your current 1 with it do:
cat /root/xorg.conf.new > /etc/X11/xorg.conf

for the log, the (EE) ones are the important 1's, don't need the rest.

---

### Post by ufireup on 2009-02-05
ok i will try to type in theEE from log

and about the xconfig did you mean xfix? and when i do this it generates a corg file automatically. is this the new one i'm looking for? if so i'll use this with what you described to do. it flashes up and goes away very quickly.

---

### Post by ufireup on 2009-02-05
Also, I have provided all the (EE) in the first post that are shown still in the log. I do not think I exactly did the whole switch to config.new correctly

---

### Post by ufireup on 2009-02-05
I believe I changed to the new xorg.config made by xfix. Still nothing.

When it asks for my login the screen flashes blank 3 times then goes to the gray box with the 
"Ubuntu is running in low-graphics mode
You may need to update your configuration to solve this.

(EE) SAVAGE(0): Unknown EDID version 2
(EE) SAVAGE(0): No valid modes found
(EE) Screens found, but none have a usable configuration.
"
I and I believe you as well know this has to be something with the savage card. i saw that a lot of people have reported it in the ubuntu bug thing as well. Let me know if you have another idea! :D

---

### Post by kerry_s on 2009-02-05
> **ufireup said:**
> ok i will try to type in theEE from log

and about the xconfig did you mean xfix? and when i do this it generates a corg file automatically. is this the new one i'm looking for? if so i'll use this with what you described to do. it flashes up and goes away very quickly.

no > X -configure < is different, it's xorg that scans the hardware and makes the xorg.conf from the results.

once you get the xorg.conf.new look at the options, see if there's 1 for the edid thing, i think you want to disable the check.

i would look at mine, but i don't have that laptop right now, my niece is using it.

---

### Post by ufireup on 2009-02-05
Alright I did X-configure the right way this time. 
I followed [http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html) 
It pulls up FATAL ERROR : No Screens Found 
Now on my xorg.conf there is a part under device section that says
#Option     "IgnoreEDID"    #[<bool>]

Thanks for all your help! IF you have any more suggestions I'd reaaally appreciate it.

---

### Post by ufireup on 2009-02-05
NOTE: I don't know if this would help.. but I am able to run Ubuntu 6.06.1 LTS from Live CD. Does that make any sense? Can I use info from that xorg.conf file?

---

### Post by kerry_s on 2009-02-05
> **ufireup said:**
> NOTE: I don't know if this would help.. but I am able to run Ubuntu 6.06.1 LTS from Live CD. Does that make any sense? Can I use info from that xorg.conf file?

yes you can, copy the xorg.conf from the live section straight to the hard drive.

hmm, what version is the installed 1?
have you tried using the vesa drivers? it should be able to get you into X.

---

### Post by ufireup on 2009-02-06
I have installed 8.1 intrepid...

---

### Post by ufireup on 2009-02-06
How do I 'use' the vesa drivers? Just replace the names with that?

---

### Post by ufireup on 2009-02-06
**SOLVED********** AS far as I know it's working. I just replaced the driver with vesa in the xorg file after copying the xorg.conf from the live cd xorg..!

-------------------------------------------------------------------------
When you go to the text terminal, log into it, and then type the following:

Code:

sudo nano /etc/X11/xorg.conf

(that first X is a capital X)

This opens up a text editor. In the Section Device part, just under the line that begins "Identifier", type:

Code:

     Driver          "vesa"

Use tabs so that the new part lines up with the old part.

Save your changes by pressing Control-O and pressing Enter, and then quit by pressing Control-X. Reboot:

Code:

sudo reboot

---

### Post by kerry_s on 2009-02-06
:lolflag:

i thought you knew about the vesa driver, it's kind of a catch all driver when the standard 1 fails, you could have used that at anytime. it has it's limit though, like no 3d(i think), resolutions(not like it matters, unless you have a weird screen size), etc...

if your happy, i'm happy. :D

---

### Post by ufireup on 2009-02-06
Hey, I can actually see and use Ubuntu lol I'm happy for now.. HaHa. Sorry, I had run across the vesa word, but didn't know exactly what it was. I am pretty new to Ubuntu and linux. Hopefully I will learn a lot more about it! :D  

Thanks for all your help!

However .. yeah no 3d so that kinda sucks.. 

I thought this computer was trash and then I was like, hey I should try Ubuntu.. and thanks lol because this is way better than nothing. I'm sure in the future I'll get annoyed and get to the point where I want to change things in order to get 3d and all..but for now this is fine!

---

