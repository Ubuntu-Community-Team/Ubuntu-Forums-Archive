---
title: "HOW TO : Install Netgear WG111v3 USB wireless"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by moshos on 2008-05-21
After using ubuntu for about 2 years i'm ready to post my first solution!
__________________________________________________________________

**This is a GUI solution on how  to install Netgear USB WG111v3 USB.**


***_STEP 1_***
Go to "add and remove programs" type on the searchfield " ndiswrapper "

One program should come up! it calls samething like "graphical frontend for ndiswrapper"

Install it!


***_STEP 2_***
start whit **wine** a file called setup.exe

the installations fails! but if you go to:

/home/moises/.wine/drive_c/windows/inf/WG111v3

( Moises is my home directory )  or go to wine and push " Explore c:/ "

**There you will find the .inf file you need!**


***_STEP 3_***
Go to SYSTEM - ADMINISTRATION - and there you will find the program called

" graphical frontend for ndiswrapper "

Push the buttom " Install new driver "! Go to the .inf file located on /home/moises/.wine/drive_c/windows/inf/WG111v3

And install it!

I attach the .inf file and the rest .sys and .cat  if you are lazzy and don't want to extract the files from the CD

---

### Post by cillit on 2008-07-19
Hi, works fantastic! Thank you so much. In "Hardy" the program entry under SYSTEM - ADMINISTRATION is called "Windows Wireless Drivers" instead of "graphical frontend for ndiswrapper". Cheers!

---

### Post by gatzalf on 2008-07-29
Hey! thank you very much for this one. I figured the ndiswrapper part from somewhere on the internet but i never found a way to get the .inf file out of the .exe untill now. Thanks again

---

### Post by Tencha on 2008-08-10
Hey i dont get it where should this setup.exe be in step2
and shall i start wine config. or what?
pls help me

---

### Post by liquidfunk on 2008-08-10
Ignore the part about using wine. 

 Save the .inf and .sys files. Put them into a Folder in your Home Directory called WG111v3 or something. 

 Then open up NDISwrapper, install the .inf. Then it will work.

 The amount of times I've said this ^_^

---

### Post by Tencha on 2008-08-10
where exactly home/user/?
bcos in my home folder i dont have any order who has smthing to do with wg111

---

### Post by XTremo54 on 2008-08-15
Many thanks! That solved my problem!

---

### Post by tksee55 on 2008-08-16
> **Tencha said:**
> Hey i dont get it where should this setup.exe be in step2
and shall i start wine config. or what?
pls help me

the setup.exe is the windows driver setup files you download from the netgear download site. 

the only reason for running setup.exe on wine is to extract the inf,cat, and sys files from it. if you have the driver already installed in one of your windows pc, like me, then you can just simply copy them out from your windows pc. they're in /windows/inf/wg111v3 folder, but you have to unhide the folder in the view option first inorder to see it in explorer :)

make sure you download the latest driver from netgear site. those provided by the op is outdated! there's now a v1.3 released in may 2008.

i was having lots of trouble getting mine to work properly with the driver that came with my wg111v3 until i downloaded and used the latest driver v1.3.

---

### Post by linuxishard on 2009-01-03
why o why is there no driver that works for 8.10-AMD64
it really sucks, i want my amd64, but no wifi.. no amd64 i need wifi to work, so ill just have to wait](*,)

---

### Post by alepippirimerlo on 2009-01-14
don't work for 8.10 - Intrepid Ibex. i'm really sad

---

### Post by germ-n8 on 2009-03-05
I'm having problems getting my WG111v3 to work under 8.10, however i've had brief periods where it was working before i messed it up again...

---

### Post by Royke on 2009-03-15
Hello germ-n8,
We share exactly the same problem. But one thing is accomplished by  8.10.:The adapter gets voltage now. It just does not blink the right way (or not at all)even with the inf installed. It looks like ubuntu8.10 doesn't use this .inf because of the other installed network stuff???. Maybe there should be something disbled/removed for ubuntu to use this driver. Could someone more experiënced with this please enlighten this a bit?
It's been over one year now that i've been on-line with my ubuntustudio on my main-machine and am stuck with vista. Once i had it all figured out... untill the next system-update:D

---

### Post by Royke on 2009-03-15
Hey germ-n8,
I have the ...-thing working now!:popcorn: I just deleted autoconfig wlan(in network configuration), turned off the system, disconnected the device, started up without network, connected the wlan device and finally connected succesfully with desired network. Now i even updated system with it, restarted several times and yes: i'm typing on this forum with ubuntu!

please say it works for you too and if it ain't we'll work it out ;)

---

### Post by ministoat on 2009-03-20
just wondering royke..are you on 32 or 64bit?

---

### Post by lost123 on 2009-04-12
Hey Royke im having the same problem but ur solutions not working :( What exactly do you mean by 'deleted autoconfig wlan'...I clicked 'network configuration' then the 'wlan' tab and removed the listing of my wirelss access point. But still have the same problem. Please help this is killliiing meeee :(:(:(:(

And yehh im using ubuntu 8.10 (well 'super ubuntu' which came with all the extras that i'll end up installing anyways)...

So yehh please help??

---

### Post by lost123 on 2009-04-12
mhmmm...I think i might try this: [http://www.uluga.ubuntuforums.org/showpost.php?p=6759228&postcount=68](http://www.uluga.ubuntuforums.org/showpost.php?p=6759228&postcount=68)

---

### Post by ministoat on 2009-05-03
lost, did that work for you?

---

### Post by @ntonius on 2009-05-07
i d like to say that my wg111v3 works great on ubuntu 8.10
i have absolutely no problems

i followed [kevdog]("http://ubuntuforums.org/member.php?u=257393")'s guide which is is here -->  [http://ubuntuforums.org/showthread.php?t=574501&highlight=wg111v3](http://ubuntuforums.org/showthread.php?t=574501&highlight=wg111v3)

This guide is not for 8.10 but worked fine with me.
I followed the guide until the part were he says "PLEASE NOTE...
The reason is that from that point and AFTER the guide is for pre-gutsy releases.

---

### Post by foo144 on 2009-09-09
they are hidden files

---

### Post by @ntonius on 2009-10-16
WG111v3 works in 9.10 out of the box (no need to use ndiswrapper anymore) and has even greater performance than in 9.04.
There has been improvement and now the range in greater with stronger signal.

They have done a really great job!

---

### Post by joeyyy on 2010-12-18
Hello,

I've spent all night trying to get this to work on Ubuntu 10.10 to no avail, and then I followed your tutorial and my WG111v3 card started working immediately, without disconnecting or anything (unlike before)!

So, although it was a while ago this thread was started, this method still works if plug-n-play doesn't!

Thanks heaps!!!

---

### Post by fernando 15 on 2010-12-19
Thanks for the files am running puppy linux on a dell c500/600 nothing else worked for but this. If it wernt for this i be running windows 98 or 2000 with a lil outdated programs.

Fernando chavez

---

### Post by Chef Kiyo on 2011-01-07
I'm trying to get this to work on 10.10 with no success in sight. It tells me "Invalid Driver". Does that mean I can't do it?

---

