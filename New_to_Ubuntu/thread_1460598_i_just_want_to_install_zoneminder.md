---
title: "i just want to install zoneminder"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by iamsolost on 2010-04-23
ok, so i came home, and noticed, that my dad has put ubuntu on my computer. why. i did a little bit of research and now, i need my freakin webcam, to do surveillance outside my house again, zoneminder, motion and whatever else there is will not install. every single error in the book is here. error dependancy this, or that, libgcc1? it says its installed, i cant seem to find a dummies version of how to install zoneminder, im really interested in this and its frustrating....ive used ubuntu before and i love all these apps and stuff but come on, i need some real help in getting this freakin zoneminder to work. i will copy and paste whatever is needed in the order its needed to install whatever is needed. hence my name, i am so lost. please, before i throw this computer from my second story window.

---

### Post by nhasian on 2010-04-23
you didnt mention what version of ubuntu you are using.  I am using the latest Ubuntu 10.04 Lucid Lynx Release Candidate (official release date should be on the 29th).  when i went to Applications-> Ubuntu Software Center, I found zoneminder there with a one click install.

---

### Post by mikodo on 2010-04-23
It is in Karmic Synaptic as well. System > Administration > Synaptic Package Manager and type in the seach box on top,  zoneminder

---

### Post by iamsolost on 2010-04-24
i am using ubuntu 9 point something, im not sure how to look for it on here to be really sure, im positive its a 9 point something. ok, well heres the latest....zoneminder installed whatever it needed...i think, but i cannot view it or run the program. i went to applications>add and remove programs, and i did a search for it, nothing came up. i found a "self help copy and paste thing on some website that was like a step by step, but i ran into errors, but so far, the file is on my computer but will not run.

---

### Post by iamsolost on 2010-04-24
Mikodo.....i went there, and it has a green box like if its installed on my computer? i can see the files when i do a search for it and it comes up but this is where im stumped...

---

### Post by nhasian on 2010-04-25
open up a terminal from applications-> accessories-> terminal

enter this command

```
lsb_release -a
```

that tells you what version of ubuntu you have.

also 

```
uname -a
```

will tell you if its 32bit or 64bit

---

### Post by no2498 on 2010-04-26
lets see if your webcam is recognized
open a terminal type,  gstreamer-properties click enter
click video try v4l1 and v4l2

try the cam in cheese

you may need to install cheese but look in graphics,or/and sound & video first

sudo apt get install cheese

---

### Post by no2498 on 2010-04-26
only 1 webcam program at a time can run zoneminder, motion
if any thing is running cheese will give an error
same as zoneminder, motion

---

### Post by iamsolost on 2010-04-28
ok i finally found my camera by installing cheese....this is a huge step thanks a bunch....now...what is this : dependancy not satisfiable...libgcc1   ? ? ? ? when i try to run skype it says this, and wont complete....


this is the version it gave me .....Linux kenny-ubuntu 2.6.24-27-generic #1 SMP Fri Mar 12 01:10:31 UTC 2010 i686 GNU/Linux     when i checked to see what version i have....hope this helps to see where im at....hold on, the version of skype that im trying to download....the icon on my screen says I386....but it shows i have i686......am i trying to do the wrong version?

---

### Post by iamsolost on 2010-04-28
alright guys, im sorry, i am trying to download zoneminder. and skype, im confusing everyone with the errors associated with them. zoneminder is not running but the files are on my computer, i get the libgcc1 error when i tried to download skype....sorry for the confusion

---

### Post by sh2515 on 2010-05-02
i have updated to 10.04 and zoneminder doesn't recolonise the webcam and I can't run the zmu -d /dev/video0 -q -v command anymore.  But all this worked on 9.10, any ideas on how to get around it?

---

### Post by no2498 on 2010-05-02
sh2515

go back and do as i told him to do


do not try to use get skype working yet
get zoneminder working first

---

### Post by sh2515 on 2010-05-03
I have installed cheese and the webcam works with cheese. But zoneminder still doesn't want to see my webcam any more.

P.S. I am not trying to get skype to work or any other software, I only want to use the webcam for zoneminder.

---

### Post by sh2515 on 2010-05-03
I also have done the gstreamer-properties and it works fine. I am thinking that ubuntu is not allowing the webcam to marry upwith ZM.

---

### Post by madjr on 2010-05-03
@iamsolost

install gnome-do (is like quicksilver)

you can find any program that you installed and almost anything else you can do with your computer


[http://www.omgubuntu.co.uk/2010/05/danny-piccirillos-rockin-post-install.html](http://www.omgubuntu.co.uk/2010/05/danny-piccirillos-rockin-post-install.html)
[http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html)

also available in
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)


as for zoneminder, anyone tried asking in their site or contacting them?

---

### Post by Ubunthree on 2010-05-04
Hello,

I will add my question to this thread, since I would have pretty much the same subject line anyway...

I have apparently installed ZoneMinder via Synaptic, but have no idea how to run it. There is no entry for it in the panel menu, and entering "zoneminder" in a terminal just returns "command not found."

"man zoneminder" returns information about container modules and so forth which would undoubtedly be helpful so someone with more knowledge than I have.

My cam works fine with Cheese.

Thanks!

---

### Post by sh2515 on 2010-05-04
hi 
open a web browser and type in the address
127.0.1.1/zm
that should open it
or 
127.0.0.1/zm

as you should have already got apache2 started and running when you installed the package. if not have a look for a tutorial that will guide you through installing and setting up zoneminder as they all include-from the ones I have seen - apache2 web server

---

### Post by no2498 on 2010-05-04
looks like they need to do the same thing for zoneminder
as they need to do for skype

this is not it but looks like it
preload v4l so vyl2 so ( the program you like to use )

---

### Post by Ubunthree on 2010-05-06
Ah well... This is one of those cases where my motivation for getting the thing running (idle curiosity) will not survive the amount of effort required to educate myself enough to understand what I'm doing. I've managed to get Firefox showing a page with some config options across the top, but I think I'd best stop blindly copy/pasting terminal commands before something breaks.

Thanks, though.

---

### Post by no2498 on 2010-05-07
try this
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so   ( your program name here )
no ()

---

### Post by mike1234567b on 2010-05-21
I think I will just add to this thread, because it is my exact problem.  Zoneminder is installed - so the software center says, but it does not show up as a program, and when I typed in the 127.0.0.1/zm it came back 404.

I am totally new to Ubuntu, I want to use this computer just as a camera monitor / recorder.  Any help would be greatly appreciated.

I updated everything btw, so running 10.4 I think, and all the updated software.

---

### Post by mvip on 2010-05-23
Here is a step-by-step installation guide on how to install ZoneMinder 1.24.2 on Ubuntu 10.04:
[http://viktorpetersson.com/2010/05/23/how-to-install-zoneminder-1-24-2-on-ubuntu-10-04-lts-server/](http://viktorpetersson.com/2010/05/23/how-to-install-zoneminder-1-24-2-on-ubuntu-10-04-lts-server/)

---

