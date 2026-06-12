---
title: "Using a Virtual Machine"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by Solstice Bahai on 2011-05-17
Hi guys, I decided Not to dual boot my Acer, But I have decided to use VBOX vertual machine programme to try out a few Distros, however, I got a thingy about displaying the guest OS in 32bit Colour, for full screen display I suppose, all I currently see is a bit ogf the desktop in a minimized window. Any suggestions as how I rememdy this?:)

---

### Post by rosencrantz on 2011-05-17
Did you install the guest additions?

---

### Post by wildmanne39 on 2011-05-17
> **Solstice Bahai said:**
> Hi guys, I decided Not to dual boot my Acer, But I have decided to use VBOX vertual machine programme to try out a few Distros, however, I got a thingy about displaying the guest OS in 32bit Colour, for full screen display I suppose, all I currently see is a bit ogf the desktop in a minimized window. Any suggestions as how I rememdy this?:)

Hi, I have been running virtuailbox for 3 years, first you need to download the one from virtuialbox.org not from the repositories in ubuntu, because if you use ubuntu's you will not be able to have usb support. Second at virtualbox.org they have a complete manual for installing and setting it up, and the things you need to do for each os your are going to run in vb before you install them, everything you need is there makes sure you download the one for the correct version of ubuntu your are running.

---

### Post by ClientAlive on 2011-05-18
> **Solstice Bahai said:**
> Hi guys, I decided Not to dual boot my Acer, But I have decided to use VBOX vertual machine programme to try out a few Distros, however, I got a thingy about displaying the guest OS in 32bit Colour, for full screen display I suppose, all I currently see is a bit ogf the desktop in a minimized window. Any suggestions as how I rememdy this?:)


You said you "decided Not to dual boot" and "to try out a few Distros".

Does this mean your base o/s is Windows and you are trying to intall VBox into Windows? And then run some Linux distros in it?

This is the main page for downloads at the Virtual Box web site:  [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

HTH
;)

---

### Post by wildmanne39 on 2011-05-18
> **ClientAlive said:**
> You said you "decided Not to dual boot" and "to try out a few Distros".

Does this mean your base o/s is Windows and you are trying to intall VBox into Windows? And then run some Linux distros in it?

This is the main page for downloads at the Virtual Box web site:  [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

HTH
;)

Hi, I agree I love virtualbox.:D

---

### Post by ClientAlive on 2011-05-18
> **wildmanne39 said:**
> Hi, I agree I love virtualbox.:D


Hi wilemanne39. Yeah, the price I paid to learn that still brings tear to my eye. It was aweful. That thing can really save one's ars.  :D

---

### Post by Solstice Bahai on 2011-05-18
> **wildmanne39 said:**
> Hi, I agree I love virtualbox.:D
Well, yes I WAS going to dual boot between Win7 and Natty, but I decided to use VB instead to try out a few Distros, openSUSE,Pardus, etc and yes I installed the appropriate guest additions, but do not know how to follow the instructions in the read me.  some thing /extract /D=C:\ SOMETHING ELSE.... :(

---

### Post by Solstice Bahai on 2011-05-18
> **Solstice Bahai said:**
> Well, yes I WAS going to dual boot between Win7 and Natty, but I decided to use VB instead to try out a few Distros, openSUSE,Pardus, etc and yes I installed the appropriate guest additions, but do not know how to follow the instructions in the read me.  some thing /extract /D=C:\ SOMETHING ELSE.... :(
Now I have ANOTHER problem....:( I could not sort out this issue, so I decided to INSTALL Natty on my Acer  via Wubi, so I could finally have a dual boot of Win7( for blue-ray playback) and Natty for everything else! Ok so far, but I was attempting to re-size  the launcher via Compiz, and well truth be told "decided" to try out a few other option in Compiz and well.....I lost the lot, all I got now is a nice desktop background, no launcher, no bar at the top, and NO CLUE as to undo MySTUPIDITY:(:(

---

### Post by ClientAlive on 2011-05-18
> **Solstice Bahai said:**
> Well, yes I WAS going to dual boot between Win7 and Natty, but I decided to use VB instead to try out a few Distros, openSUSE,Pardus, etc and yes I installed the appropriate guest additions, but do not know how to follow the instructions in the read me.  some thing /extract /D=C:\ SOMETHING ELSE.... :(


You still haven't confirmed whether you are trying to run Virtual Box in Windows or something else. I'll assume you want to run it in Windows but it prob doesn't matter too much as long as you have the correct download.

While the readme file may have useful information in it for someone I think what wildemanne39 was referring to was this:

[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

Here is something else you may find interesting once everything is working correctly:

[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

Hope it helps my friend.

Thanks

---

### Post by noidian on 2011-05-18
If your doubt is just full screen for Vbox: It should be part of the menu under Machine I believe.

---

### Post by Solstice Bahai on 2011-05-18
I was running VB in Windows Windows was the host OS

---

### Post by ClientAlive on 2011-05-18
> **Solstice Bahai said:**
> Now I have ANOTHER problem....:( I could not sort out this issue, so I decided to INSTALL Natty on my Acer  via Wubi, so I could finally have a dual boot of Win7( for blue-ray playback) and Natty for everything else! Ok so far, but I was attempting to re-size  the launcher via Compiz, and well truth be told "decided" to try out a few other option in Compiz and well.....I lost the lot, all I got now is a nice desktop background, no launcher, no bar at the top, and NO CLUE as to undo MySTUPIDITY:(:(


That sounds like something similar I had happen to me a while back. I don't recall off the top of my head how we fixed it but I'll try to hunt down that thread and post the link here.

Hang on man.

Oh, also, they say that if a person is doing a dual boot with Windows and Linux where you actually install both - that it's better to install Linux first and then Window. They say doing it the other way round can lead to problems and possibly data loss. This is not what you talked about doing when you said you used wubi but I thought I'd mention it to you in case the information becomes useful to you some time in the future.

Hang on, I'll look for that post.

---

### Post by CharlesA on 2011-05-18
Usually they install Windows first then Linux, so you don't have to mess with Grub.

---

### Post by Solstice Bahai on 2011-05-18
> **ClientAlive said:**
> That sounds like something similar I had happen to me a while back. I don't recall off the top of my head how we fixed it but I'll try to hunt down that thread and post the link here.

Hang on man.

Oh, also, they say that if a person is doing a dual boot with Windows and Linux where you actually install both - that it's better to install Linux first and then Window. They say doing it the other way round can lead to problems and possibly data loss. This is not what you talked about doing when you said you used wubi but I thought I'd mention it to you in case the information becomes useful to you some time in the future.

Hang on, I'll look for that post.
Thanks, will bear that in mind for the future.:)

---

### Post by ClientAlive on 2011-05-18
> **Solstice Bahai said:**
> Thanks, will bear that in mind for the future.:)

What operating system are you talking about having the problem with? You are talking about having the problem with Ubuntu??

---

### Post by Solstice Bahai on 2011-05-18
/home/solstice-bahai/Desktop/Screenshot.png> **Solstice Bahai said:**
> Thanks, will bear that in mind for the future.:)
>  this is all I am left with I'm not sure I put this pic in right

---

### Post by Solstice Bahai on 2011-05-18
> **ClientAlive said:**
> What operating system are you talking about having the problem with? You are talking about having the problem with Ubuntu??
Yes!! apart from a nice Natty Narwhal desktop every thing else has disappeared off the screen:( I mean desktop background

---

### Post by wildmanne39 on 2011-05-18
> **Solstice Bahai said:**
> Now I have ANOTHER problem....:( I could not sort out this issue, so I decided to INSTALL Natty on my Acer  via Wubi, so I could finally have a dual boot of Win7( for blue-ray playback) and Natty for everything else! Ok so far, but I was attempting to re-size  the launcher via Compiz, and well truth be told "decided" to try out a few other option in Compiz and well.....I lost the lot, all I got now is a nice desktop background, no launcher, no bar at the top, and NO CLUE as to undo MySTUPIDITY:(:(
Hi , you need to work on one problem at a time, first we have to fix unity.
Hi, just open a terminal by hitting alt+f2 or ctrl +alt+t and type unity --reset  and let it run for about three minutes, do not worry about the errors it will list, then hit ctrl+alt+del to restart the computer and everything should be fine.):P Then we can continue with the vb issue.):P

---

### Post by Solstice Bahai on 2011-05-18
> **CharlesA said:**
> Usually they install Windows first then Linux, so you don't have to mess with Grub.
Any idea how I can get Compiz BACK on screen so I can UNDO all that I have done, and get back to a nice clean Natty Narwhal 11.04 with side launcher, Dash screen and EVERY THING back to normal?????? :(

---

### Post by ClientAlive on 2011-05-18
> **CharlesA said:**
> Usually they install Windows first then Linux, so you don't have to mess with Grub.


Oh. Sorry, guess I got that turned around somehow. Thanks.

> **Solstice Bahai said:**
> Yes!! apart from a nice Natty Narwhal desktop every thing else has disappeared off the screen:( I mean desktop background

It sounds like something that happened to me back when I was running 11.04. I had made a couple changes in Compiz through ccsm and it resulted in my losing my entire widow system. Everything dissappeared. I wasn't able to use the gui at all.

I just got done re-reading that old post and it turns out what I did was re-install the operating system. That was way back when, when I didn't know a darn thing about Linux and doing that was the only thing I did know to do. Now, if I had to do it over again, I would do it differently.

Why don't you try this:

Open a terminal window in Ubuntu by pressing ctrl+alt+F1

You will be asked to enter your user name and then (after you press enter) to enter your password. Do those to get logged in. Once you are logged in in the terminal window just type "ccsm" and press enter. If ccsm launches . . .

Crap, if you don't have a gui I don't think that will work either.


_Guys_ He's running Ubuntu 11.04. I'm almost certain that what is going on is something happened to the unity plugin when he made the changes in compiz. That's what happened to me. He needs a way to fix or reinstall the unity plugin and have it be enabled and I don't think he'll be able to do it any other way than through the command line. I'm going to look on the internet to see what I can find but if someone knows how he can look into that and get that done please help.

I'll be back.

Sorry.

---

### Post by wildmanne39 on 2011-05-18
> **bkerensa said:**
> I run Virtual Box from a Ubuntu Repo Install and USB support works just fine.

Hi,the last I heard that still was not possible with out downloading from virtalbox, so learned something new. Thank you. I just started having key board problems, so it is very hard to type now.

---

### Post by ClientAlive on 2011-05-18
> **wildmanne39 said:**
> Hi , you need to work on one problem at a time, first we have to fix unity.
Hi, just open a terminal by hitting alt+f2 or ctrl +alt+t and type unity --reset  and let it run for about three minutes, do not worry about the errors it will list, then hit ctrl+alt+del to restart the computer and everything should be fine. Then we can continue with the vb issue.


Thank you. Wish I would have know that 6 wks ago when it happened to me.

:(

---

### Post by ClientAlive on 2011-05-18
> **Solstice Bahai said:**
> Any idea how I can get Compiz BACK on screen so I can UNDO all that I have done, and get back to a nice clean Natty Narwhal 11.04 with side launcher, Dash screen and EVERY THING back to normal?????? :(


Do what wildemanne39 says in post #18. That should work.

---

### Post by wildmanne39 on 2011-05-18
Hi, in post 18 I gave you the commands and instructions to fix unity.:)

---

### Post by wildmanne39 on 2011-05-18
> **ClientAlive said:**
> Do what wildemanne39 says in post #18. That should work.

Hi, it happened to me to, and that is how I found out about it. There is another way to but more complicated. Now we can have the cube in unity but that is complicated too, I helped a lot of people with these problems, and I started telling people not to try compiz with unity and I got told not to do that, that it works great with unity, but the real issue is that the new people trying it ended in broken unity.

---

### Post by Solstice Bahai on 2011-05-18
Hi wildmanne, I tried, but terminal asks for login, I give username, and it ask for password, I type my password that I set when I installed Ubuntu, but all I get  is " invalid password:(

---

### Post by wildmanne39 on 2011-05-18
> **Solstice Bahai said:**
> Hi wildmanne, I tried, but terminal asks for login, I give username, and it ask for password, I type my password that I set when I installed Ubuntu, but all I get  is " invalid password:(
Hi,it should not, if you did it the way I mentioned,from with in ubuntu, it sound like you restarted? Make sure your caps locks are not on. also if you look in my signature under this text you will see reset unity and compiz, you can click on it for more info.

---

### Post by ClientAlive on 2011-05-18
> **wildmanne39 said:**
> Hi, it happened to me to, and that is how I found out about it. There is another way to but more complicated. Now we can have the cube in unity but that is complicated too, I helped a lot of people with these problems, and I started telling people not to try compiz with unity and I got told not to do that, that it works great with unity, but the real issue is that the new people trying it ended in broken unity.


I'm running 10.04 now. Love it. Wish I hadn't been so stubborn there in the beginning. Could have avoinded a lot of headaches. Maybe I'll go back to it sometime once they really get it dialed in though. Not sure.

wildmanne39 check your pm

---

### Post by Solstice Bahai on 2011-05-18
Also, rebooted  laptop ( ctrl+alt+del) and went into ubuntu version of safe mode, and now I got "classic" desktop because Ubuntu  in low graphic mode "says" I can't run Unity!!!  This is a Corei3 Acer Aspire!! of course it can run Unity, I want my Unity back!! Sorry if I sound like a spoiled kid, Im not Im just hacked off that I could be so stupid

---

### Post by Solstice Bahai on 2011-05-18
I booted into terminal like you said, but it asked for login, I assume that means username and authentication password????

---

### Post by ClientAlive on 2011-05-18
> **Solstice Bahai said:**
> Also, rebooted  laptop ( ctrl+alt+del) and went into ubuntu version of safe mode, and now I got "classic" desktop because Ubuntu  in low graphic mode "says" I can't run Unity!!!  This is a Corei3 Acer Aspire!! of course it can run Unity, I want my Unity back!! Sorry if I sound like a spoiled kid, Im not Im just hacked off that I could be so stupid


No worries man. There's two of us right here in this thread that have had it happen to us. Stuff happens. You just deal w/ it and learn. Not that I like it but I've learned a lot from the "problems" I've had to deal with. It'll get worked out if you stick with it and try to slow down a little.

:D:D

---

### Post by wildmanne39 on 2011-05-18
> **Solstice Bahai said:**
> I booted into terminal like you said, but it asked for login, I assume that means username and authentication password????
Hi, was it the graphical log in screen?

---

### Post by wildmanne39 on 2011-05-18
> **ClientAlive said:**
> No worries man. There's two of us right here in this thread that have had it happen to us. Stuff happens. You just deal w/ it and learn. Not that I like it but I've learned a lot from the "problems" I've had to deal with. It'll get worked out if you stick with it and try to slow down a little.

:D:D
Hi, do you see what I was talking about in my signature, click on it and check it out.

---

### Post by Solstice Bahai on 2011-05-18
> **wildmanne39 said:**
> Hi, do you see what I was talking about in my signature, click on it and check it out.
just looking there now

---

### Post by ClientAlive on 2011-05-18
> **wildmanne39 said:**
> Hi, do you see what I was talking about in my signature, click on it and check it out.

Oh wow . . .

Yup!

I'm off to bed fellers. Catch you on the flip side!

:D

---

### Post by wildmanne39 on 2011-05-18
> **Solstice Bahai said:**
> just looking there now

ok, let me know if you have the graphical log in screen or the terminal screen.

---

### Post by Solstice Bahai on 2011-05-18
> **Solstice Bahai said:**
> just looking there now
I have bookmarked all the links, will try Terminal, as you outlined again

---

### Post by Solstice Bahai on 2011-05-18
> **ClientAlive said:**
> Oh wow . . .

Yup!

I'm off to bed fellers. Catch you on the flip side!

:D
Sleep tight!

---

### Post by Solstice Bahai on 2011-05-18
> **wildmanne39 said:**
> ok, let me know if you have the graphical log in screen or the terminal screen.
ok I tried in the terminal screen under Acessories

---

### Post by Solstice Bahai on 2011-05-18
> **Solstice Bahai said:**
> ok I tried in the terminal screen under Acessories
But I'm thinking you meant Terminal as you had originally mentioned???

---

### Post by wildmanne39 on 2011-05-18
> **Solstice Bahai said:**
> But I'm thinking you meant Terminal as you had originally mentioned???

Hi, you can do it that way if you can get the terminal use it,then follow the instructions.

---

### Post by zxy6532720 on 2011-05-18
Ah well[Kids Dress](http://www.amykidsshop.com/)

---

### Post by wildmanne39 on 2011-05-18
> **zxy6532720 said:**
> Ah well[Kids Dress](http://www.amykidsshop.com/)

Hi, what is this for?

---

### Post by Solstice Bahai on 2011-05-18
> **wildmanne39 said:**
> Hi, you can do it that way if you can get the terminal use it,then follow the instructions.
Ok, it 8.20AM here in London,UK. I have booted back into Win7 and I have bookmarked ALL the links in your message, as I have a meeting to attend (1PM) I have decided to go drastic, I have un-installed Ubuntu (as I had installed it anyway under Wubi) and am now in the process of re-installing it (under Wubi) and I can promise you this, I WONT BE GOING ANYWHERE NEAR COMPIZ again!! At least untill I know more than I do now. :)

---

### Post by wildmanne39 on 2011-05-18
> **Solstice Bahai said:**
> Ok, it 8.20AM here in London,UK. I have booted back into Win7 and I have bookmarked ALL the links in your message, as I have a meeting to attend (1PM) I have decided to go drastic, I have un-installed Ubuntu (as I had installed it anyway under Wubi) and am now in the process of re-installing it (under Wubi) and I can promise you this, I WONT BE GOING ANYWHERE NEAR COMPIZ again!! At least untill I know more than I do now. :)
Hi, ok good luck.:)

---

