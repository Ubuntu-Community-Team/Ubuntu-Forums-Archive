---
title: "nothing on screen"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by topman48 on 2009-12-29
I have a Elonex Webbook but when I start it up I get the Ubuntu logo scrolling on screen but then I get a blank screen, I have tried another monitor plugged in and their is a desktop on the screen, can anyone please help??

---

### Post by stlsaint on 2009-12-29
what distro are you running? a webbook as in netbook? you should try UNR if you havent! [UNR]("http://www.ubuntu.com/GetUbuntu/download-netbook")

---

### Post by topman48 on 2009-12-30
Sorry don't mean to be ignorant but what's "distro" please??

---

### Post by halitech on 2009-12-30
Distro - short for Distrobution

He's asking what version of Linux you are running. ie. Ubuntu 9.10

---

### Post by Geoff918 on 2009-12-30
Maybe your system is set to output to an external display. If there "is" a desktop being displayed on the external monitor, you may wish to use that. Go to the System menu and then select Preferences and then Display.

It may be self-explanatory from there. Let us know.

---

### Post by topman48 on 2010-01-01
Thanks for suggestions and enlightenment on "distro" but on the top of the keyboard there is a function control to switch to external monitor and the colour of the screen changes although still blank, anyway I will try and go into settings when I attach my monitor and get back to you and let you know if it works Cheers Topman48 :) sorry I forget to say which o/s was, it's Ubuntu, which actually comes on with a scrolling line when booting up but then goes blank as I said, topman48

---

### Post by Max_Mackie on 2010-01-01
Have you logged into Ubuntu before? Or is this a boot from a clean install?

---

### Post by topman48 on 2010-01-03
No, I bought the webbook second hand but since have not been able to get it working properly unless connected to an external monitor
:(

---

### Post by halitech on 2010-01-03
I'm going to take a stab in the dark here and suggest holding the Fn key (lower left of the keyboard) and then try pressing F2 through F10 one at a time slowly and see if the laptop screen comes back. Don't hit Fn + F1 as that will turn the wireless off.

---

### Post by anewguy on 2010-01-03
While up and running on the external monitor, please do the following:

in a terminal window (applications/accessories/terminal) type:

lspci | grep VGA <press enter>


Please post the output of that back here.

Dave :)

---

### Post by topman48 on 2010-01-15
Sorry for the delay in replying but I have been hectic with weather bad. I did what you said and the information about the graphics comes on :( Cheers TC

---

### Post by anewguy on 2010-01-23
Yes - and I need you to post back here the complete line returned so we can see what chipset the video is using to see if we can find a driver.

Dave :)

---

### Post by anewguy on 2010-01-24
EDIT:  removed - I posted info here meant for another thread.

Dave

---

