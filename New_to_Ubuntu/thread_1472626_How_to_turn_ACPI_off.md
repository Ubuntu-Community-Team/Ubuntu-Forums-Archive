---
title: "How to turn ACPI off"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by frillybob on 2010-05-04
HI to install Ubuntu I need to acpi=off. Here are my system specs before I go any further:

[http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_L505D-S5983.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_L505D-S5983.pdf)

So I read other stuff on how to turn it off but it says to do f6 and whenever I press that it just boots normally! I want to dual boot windows 7 and ubuntu. THERE IS NOTHING WRONG with my live cd I've tried it on another pc and also tried a bootable flash drive with the same thing. I do see the start up of the purple thing then it goes into that. But unlike the pc i booted the live cd in that worked it didn't start loading it just gave me [a bunch of errors inside of these] HELP

---

### Post by arochester on 2010-05-04
Have a look at "BootOptions" - [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It could initially be a case of clicking F6 on startup.

---

### Post by frillybob on 2010-05-04
NO!!!!!!!! I can't even get to that!

---

### Post by anewguy on 2010-05-04
EDIT:  FORGET ME INITIAL REPLY HERE - I WAS WRONG.

I see now I mis-read your initial post, and so my reply here was wrong.  I have edited to remove that text, and am adding a new post so it gets bumped back up.

Sorry!

Dave ;)

BTW - please avoid things like > NO!!!!!!!!, as even though we know you are frustrated (we've all been there), it is usually taken as a rude reply.  You should say something like "You'll have to excuse me for being frustrated - I really want this to work.  When I try to do that I am unable to get to the options menu and instead the PC just boots.  Thank you in advance.".  You have to remember everyone is just volunteering their time here, and while there are *many* experts here, some of us like myself have gotten help for our problems and are just trying to help others as best we can as we try to grow also.  Thanks!

---

### Post by anewguy on 2010-05-04
I think I mis-read your initial post - are you saying that when you attempt to boot the LiveCD you never get to the screen where it asks for you to select the language and either try Ubuntu or install Ubuntu?  After re-reading, I think that's what you are saying.  So, a couple of questions:

- do you get the purple screen?

- does that screen have the work Ubuntu on it and do the dots alternate red/white?

- can you catch any of the error messages?  What do they say?


If indeed you can't even get the LiveCD to boot, you may want to try downloading the alternate CD (text based) and try installing from that.

Sorry for mis-reading your initial post!

Dave ;)

---

### Post by frillybob on 2010-05-04
Ok, after a lot of stress becuase I thought I lost win 7 I have dual boot somewhat set up! So to run Ubuntu I must go to the command line and say "acpi=off" then it will run. If I want to run windows 7 I must insert my recovery point disk. (not iso image of win 7) strange huh and srry for getting mad I wasn't mad @ you but at my self!!

---

### Post by spydeyrch on 2010-05-04
@frillybob

Why did you start another thread dealing with almost the same issue? You could have continued with your [original thread]("http://ubuntuforums.org/showthread.php?t=1471425") and asked the same question, as several of us were trying to help you. This can cause confusion. Please try to keep things in one thread if they are dealing with the same issue, thank you.

That being said, have you taken a look at your original thread? I posted a suggestion there that may help but may not as it wasn't about your AHCI.

Also, are you sure that you need to disable ACPI in order to boot from the CD/USB? What lead you to come to that conclusion?

I can understand your frustration as I have been there too but with a little patience and determination, eventually the issue will get solved. :D

-Spydey :KS

P.S. Have you tried using WUBI first? Just a thought/idea.

---

### Post by spydeyrch on 2010-05-04
> **frillybob said:**
> Ok, after a lot of stress becuase I thought I lost win 7 I have dual boot somewhat set up! So to run Ubuntu I must go to the command line and say "acpi=off" then it will run. If I want to run windows 7 I must insert my recovery point disk. (not iso image of win 7) strange huh and srry for getting mad I wasn't mad @ you but at my self!!

Awesome! I am glad to hear that you got it working. That is strange that you have to use your recovery disk to get back into windows. Up until now the only OS that you have installed is Win7, right? And you were running ubuntu form the live cd/uusb, right?

-Spydey:confused:

---

### Post by frillybob on 2010-05-04
Well I started a new thread becuase no one was anwering it! I waited  several hours and knew that starting a new thread would be faster.  Sorry. I'm going to restore back to defults without ubuntu... then do it  all over again with the other boot option you mentioned sydney..... oh man this is CRAZY! I'll reply back soon with the results.


P.S. If I don't respond dont' expect 1 back for a month becuase I'll probably have it sent back into toshiba! TTYL

---

### Post by spydeyrch on 2010-05-04
> **frillybob said:**
> Well I started a new thread becuase no one was anwering it! I waited  several hours and knew that starting a new thread would be faster.  Sorry. I'm going to restore back to defults without ubuntu... then do it  all over again with the other boot option you mentioned sydney..... oh man this is CRAZY! I'll reply back soon with the results.


P.S. If I don't respond dont' expect 1 back for a month becuase I'll probably have it sent back into toshiba! TTYL

Not a problem. :D Try to keep us informed about what is going on, things you have tried, things that worked, and things that didn't.

I find it very very unusual that the live cd/usb won't boot up for you the right way unless you tun off your apci, that is strange. I have to have mine turned on or else it won't work. So there is definitely something wrong.

-Spydey :KS

---

### Post by frillybob on 2010-05-04
Well luckily the installation didn't erase my recovery partiton! It crashed windows 7 and Ubuntu was installed and it says it was installed but when I load up every time I get the same [random stuff goes in here] crap problem again! Unlike with the live cd I don't get the options to start Ubuntu without making changes to my pc or not! It just automaticliy does that. So that won't start. I tried in the command line acpi=off but that didn't work. So now I'm reformating again for the THIRD TIME TODAY and I'll try it again after I get some help!
 
 
So when I boot I see start ubuntu with a bunch of technical stuff
the same thing with recovery mode
memery diagnostics
antoher type of memory diagnostics
start win 7 crazy random stuff
start win 7 crazy random stuff again
start windows vista WHAT I HAVE NEVER HAD THAT ON my machine!
 
 
So all the windows options get me to the revovery thing execpt the second win 7 option which gives me an error message then gives me an OS to boot from. All I see is win 7 and when entered I get the error again. GOSH!!!! HELP ME!!!

---

### Post by frillybob on 2010-05-05
Reply please

---

