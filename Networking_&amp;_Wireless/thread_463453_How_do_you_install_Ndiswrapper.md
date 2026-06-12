---
title: "How do you install Ndiswrapper?"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by Maniac Matt on 2007-06-03
How do you install Ndiswrapper? I have done it before..but of course I do not remember how, And it was on Kubuntu. I am now using Ubuntu, just to try it, but if anyone knows how to install Ndiswrapper, any imput is wanted.

It is not in Synaptic Package manager Or Adept package manager. I used the Desktop Cd to install Ubuntu, and it says it has ndiswrapper on the live Cd. so that confuses me.

I tried the installation directons that came with it, but with no avail. 

so any help would be appreciated. 


The other time i got ndiswrapper to run, i used the Kubuntu 7.04 Alternate Cd... could that have made the difference?

thanks.. matt

---

### Post by patsfan on 2007-06-03
go into add/remove programs it is in there to install with ease

---

### Post by Maniac Matt on 2007-06-03
That doesnt work, when i click it, Synaptic tells me that i need an internet connection to install it.

---

### Post by snowdude on 2007-06-03
You can download ndiswrapper from [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) and transfer it to that computer via thumbdrive and then just compile it.

---

### Post by Maniac Matt on 2007-06-03
I did that, but being a linux noob, i don't know how to compile it.

---

### Post by snowdude on 2007-06-03
ok well open up your terminal and navigate to the folder where your ndiswrapper is for example, in terminal type, "cd ~/Desktop/ndiswrapper-1.45".

Now that you are in that folder type "make".

If you get and error its probably because gcc/c header files isn't installed which is the c compiler. To install gcc type the command "sudo apt-get install build-essential". After that finishes installing then run make again. This time you shouldn't recieve any errors.

Then type "sudo make install".

Now ndiswrapper is installed. :-) Which you can verify by just simply typing in "ndiswrapper".

---

### Post by Maniac Matt on 2007-06-03
i guess i can give that a shot. Thank you.

---

### Post by jglen490 on 2007-06-03
Before you get into compiling, and all the "stuff" that goes with that, look on your install CD.  Open it up with nautilus, or whatever file manager you have  and poke around the folders to find the ndiswrapper and utilities files.  These should be installable directly from the CD.

---

### Post by Maniac Matt on 2007-06-03
well.. with a little bit of messing around i now have a nice Gnome-Kde thing going... I finaly was able to get ndiswrapper of off a Kubuntu 7.04 alternate Cd.

Woot Woot. Thank you.

---

