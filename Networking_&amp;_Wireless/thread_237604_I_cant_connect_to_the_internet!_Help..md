---
title: "I cant connect to the internet! Help."
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by Seldoms on 2006-08-16
I am a COMPLETE linux newbie.
My DSL modem is directly connected to the pc. No Wireless Router.

I have no idea where to go what to configure. Please help. I also have a couple non related questions.

My screen resoloution in Ubuntu is messed up. There is a black line running down the right end of the screen. When I hold my mouse over the applications tab, the description gets cut off.

Also, the startup and shutdown speed is a lot slower with the live cd, correct?

And finally, I would like it if someone had some links to understand the basics of Linux/Ubuntu.

I was good with Windows. I understood the paths c:\program files\ blah.
I want to know whats different and whats the same with Ubuntu/Linux. Thanks!

---

### Post by brk3 on 2006-08-16
To be honest Im not really sure about the internet, if your DSL is working normally and plugged in while linux is booting up it should work.. Hopefully someone else can give you some things to try.

In the mean time, the resolution thing just sounds like your monitor needs to be centered, you just need to fiddle around with the centering buttons on your monitor! If you have a nvidia card, installing the driver will position the screen the same as on windows. (see thread on automatix which will install this automatically, plus a load of other cool stuff!)

Also, the speed when using the live cd is definatly significantly slower, as everything is being read from the disc drive rather than memory. The live cd is really best for just testing if everything works ok on your system before installing. (they come in handy in lots of other times too though)

And finally, just type in 'linux basics', 'windows to linux for beginners' or something similar into google(once you get your internet sorted!) and the guides are endless. You'l find you'l adjust to the basics quickly though, then you'l never go back :) To get you started, you mentioned paths on windows, just remember that paths on linux are seperated with a '/' instead of a '\'.

good luck

---

### Post by Seldoms on 2006-08-16
Thanks, I get the error Problem Loading Page whenever I use firefox in ubuntu.

---

### Post by bensexson on 2006-08-16
Does your DSL provider use PPPoE?  Does the modem do the PPPoE authentication for you?

---

### Post by Seldoms on 2006-08-16
I think so bensexson. Im 75 percent sure and I'll check again now.

---

### Post by Seldoms on 2006-08-16
Yes, I am using PPPoE.

---

### Post by bensexson on 2006-08-16
Is the mode doing PPPoE authentication for you? If not look here for a HOWTO for setting it up.  If not post the output of sudo ifconfig -a, route -n, and netstat.

---

### Post by Seldoms on 2006-08-16
Ok, I am a complete linux newbie so I dont really understand. Would I try and connect with the PPPoE or the eth0?
I am not dial up though, I am DSL.

---

### Post by Seldoms on 2006-08-16
Someone please help me.

---

