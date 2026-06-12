---
title: "Emulator for IBM AS/400"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by jazzbuntu on 2009-02-26
hi

i need to wrok at my home in my office. So, i asked how to perform a VPN( I have it on WIndows, but moved to Ubuntu) and now i really need a emulator for IBM AS/400. 

I tried TN5250 but somehow the image that apears on the screen os on the left top and small ( a quarter of the screen oe even smaller) 

How can i replace or size this image to fullfill the whole screen. 

This is one of the subjects that is missing for my final cut. 

Appreciate any help

Thanks

---

### Post by llamakc on 2009-02-26
Have you tried maximizing the emulator that you have already tried?

---

### Post by jazzbuntu on 2009-02-27
yes... i tried but it didn't work out

the screen of the application maximize but the application itself stays with the same "dimensions". 

Let's say i open the application and this application is on a window. Then, i maximize the window and the application stays like i opened it

---

### Post by swmiller6 on 2009-03-14
Start the emulator with xt5250 then press ctrl+right mouse click together choose huge as your font choice... That is just about as good as it gets unless you wanna edit some text configuration files. 
You can also look into the Ibm iSeries access package but it is much much slower imo and only available if your on a 32 bit os.

---

### Post by anewguy on 2009-03-14
Okay, it's been MANY years ago, but let me throw out a couple of things that at least used to exist in the *nix world:

termcap -> this was used to describe the characteristics of a terminal you wanted to try to emulate.  There used to be a huge "inventory" of terminals already defined.  I don't know if this still exists now or not - perhaps someone with more in-depth knowledge can answer that.

login -> this is when you specified the termcap terminal definition you wanted to use.

I believe at one time there were 2 packages - termcap and termlib - to put this functionality into Ubuntu.

In the old Unix days, this was a command-line function.  I don't remember (but again it's been MANY years!) anything like it for X windows, as it was an animal to itself.

Perhaps someone can shed some light as to if the old termcap capability is implemented in Ubuntu, and then perhaps we can find the defs for your terminal (I'm assuming it's the TN5250) and update the definitions file.

I'll try to do some additional research on my own as well.

EDIT:  I've done some more researching, and boy did it bring back memories!  While my background on mainframes was from a non-IBM standpoint (different manufacturer), seeing EBCDIC, sync, bisync and block mode terminals really brought back memories.  At any rate, I don't think there can ever be a termcap type entry for this type of terminal.  What is being emulated is a very different animal from what most people are familiar with now.  I could go into technical details, but they are not needed for the scope of what you are asking about.

Given most of these terminals were either 80 or 132 characters wide by 25 lines vertically, I'm not sure if there is any other way of getting a "larger" view than by that suggested by the previous poster on changing the font size, at least for TN5250.  I haven't looked beyond that product to see if there are any others, perhaps in sourceforge, that would work as well.

EDIT-EDIT:  Besides Tn5250, there are 2 other 5250 "emulators" on sourceforge.net your may want to try:

[http://sourceforge.net/search/?type_of_search=soft&words=5250+emulation]("http://sourceforge.net/search/?type_of_search=soft&words=5250+emulation")


Dave :)

---

