---
title: "New Dell Linux laptop coming"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by Calais225 on 2010-11-14
Dell Canada had a good deal, with discounts, on a laptop pre-installed with Ubuntu 8?? so I bought one.  It's a Celeron, one gig of ram-expandable to 4 gigs, webcam, wireless and DVD burner installed so there should not be many problems getting it up and running.

However, I would like to upgrade it to the latest Maverick Meerkat version.

Any suggestions on:

1.  What I should do during the first few weeks while confirming that all is well in the system?

2.  Anything to make my possible upgrade a bit smoother?

I have just returned my dual boot desktop to Windows only but that did take a bit of work.  I have used Karmic Koala for a while but the new computer will be fully Linux and pretty much open source software.  

I have my other machine for heavy duty photo editing so this will be a general purpose machine, mail, surfing, travel, and sharing photos processed on the other machine.

I am very much a beginner with Linux and deliberately chose this laptop so that I could continue to learn.  You will probably hear from me when I mess it up.

Nice to have a new computer and a clean install.  What should I add, what should I avoid, should I increase the ram to 2 gigs?

Suggestions wanted.

Thanks,

Bill

---

### Post by tom.swartz07 on 2010-11-14
> **Calais225 said:**
> Dell Canada had a good deal, with discounts, on a laptop pre-installed with Ubuntu 8?? so I bought one.  It's a Celeron, one gig of ram-expandable to 4 gigs, webcam, wireless and DVD burner installed so there should not be many problems getting it up and running.

However, I would like to upgrade it to the latest Maverick Meerkat version.

Any suggestions on:

1.  What I should do during the first few weeks while confirming that all is well in the system?

2.  Anything to make my possible upgrade a bit smoother?

I have just returned my dual boot desktop to Windows only but that did take a bit of work.  I have used Karmic Koala for a while but the new computer will be fully Linux and pretty much open source software.  

I have my other machine for heavy duty photo editing so this will be a general purpose machine, mail, surfing, travel, and sharing photos processed on the other machine.

I am very much a beginner with Linux and deliberately chose this laptop so that I could continue to learn.  You will probably hear from me when I mess it up.

Nice to have a new computer and a clean install.  What should I add, what should I avoid, should I increase the ram to 2 gigs?

Suggestions wanted.

Thanks,

Bill

Hey Bill

When your new computer arrives, it should be fine right out of the box- no need to configure anything.
HOWEVER- and this is imperative- you must update using the update manager. 8.04 (I think is the version Dell used) is no longer being supported and will be woefully out of date. 

Simply open the usual update manager program and click the button to upgrade to the most recent version of Ubuntu and youll be all set.

---

### Post by Rex Bouwense on 2010-11-14
Hey guys.  I believe that Hardy Heron (Ubuntu 8.04) is a Long Term Support version and that means that it is supported for three years.  I used Hardy on one of my machines until the new LTS version (10.04) came out.  By all means update but will not have to immediately upgrade.

---

### Post by waynefoutz on 2010-11-14
> **Rex Bouwense said:**
> Hey guys.  I believe that Hardy Heron (Ubuntu 8.04) is a Long Term Support version and that means that it is supported for three years.  I used Hardy on one of my machines until the new LTS version (10.04) came out.  By all means update but will not have to immediately upgrade.

That support ends at the end of April, which isn't very far down the road at all. You're right, it's not an immediate rush, but the clock is ticking. 


As for upgrading with update manager, going from 8.04 to 10.04 is extremely time consuming and messy. The upgraded install will not boot as fast or perform as well as a fresh install off of a 10.04 disk. I tried it a few weeks ago on a laptop, primarily out of boredom and curiosity to see how it would go. The whole process took about 4 hours, and that was on a really fast Road Runner cable modem connection. When it was finally finished it took forever to boot and a lot of the applications weren't functioning at all. It's far quicker and easier to do a fresh install, and you'll get better results.

---

### Post by Calais225 on 2010-11-15
How to best do a fresh install?  Should I download the iso for the new version and install that way?  
Then would I remove the old version?  How do I do that?

I want to keep this machine as clean as possible even though I am a bit of a software junkie---on my PC.

This will be my travel computer, e-mail, word processing and sharing of photos so a one gig of ram celeron machine should do fine.

Thanks for help re above.

Bill

---

### Post by Rex Bouwense on 2010-11-15
Bill, I would do a clean install.  Just download the version you want.  Lucid (10.04) is the LTS and the newest 18 month version is Maverick (10.10).  Be careful which one you download (32 bit or 64 bit) based on your computer.  Be sure and do a md5sum to check the download hash.  If you got a good download, burn the ISO to a CD.  You will then be able to boot from the CD which you can use to try Ubuntu without changing your computer.  This will give you an idea if the new version will work out of the box.  Since you already have Ubuntu on it, that will probably be the case.  You have the choice of installing your new version on the whole drive or installing it side by side with the OS that you already have on the computer.  This choice will be given you as part of the installation process.  Enjoy.

---

### Post by mastablasta on 2010-11-15
> **Calais225 said:**
> How to best do a fresh install? Should I download the iso for the new version and install that way? 
 
If you have an empty (at least 1GB big) USB hanging arround you might want to create live USB and first try it out. otherwise download the CD image (10.04 for LTS and 3 years support or 10.10 for 18 months support) burn it to a CD and again try it first before you do any install. that way you can see what works out of the box and what not. and if something doesn't work then you can search for solution ahead of install.
 
during install you will erase the whole disk and previous system as a result. and everyhting will be fresh and clean. you might need to install wireless driver later on. depends on which computer you go.
 
>  
I want to keep this machine as clean as possible even though I am a bit of a software junkie---on my PC.

 
aside from any drivers you might need you should also install ubuntu restricted extras so you can see the movies.
this one is for 10.10 but they have a similar one for 10.40 - 10 things to do after installing Ubuntu 10.10 Maverick Meerkat:
[http://www.omgubuntu.co.uk/2010/10/10-things-to-do-after-installing-ubuntu-10-10-maverick-meerkat/](http://www.omgubuntu.co.uk/2010/10/10-things-to-do-after-installing-ubuntu-10-10-maverick-meerkat/)
 
>  
This will be my travel computer, e-mail, word processing and sharing of photos so a one gig of ram celeron machine should do fine.

 
yes it will be fine with 1GB ram, though you might want to add 1 GB more to make it more snappy. depends on how much of ram is taken by graphcis card.
 
I have 2 computers. one has celeron (new one, dual core, i think model is E3300) with 1.3 GB ram and is working very fast. it's just "snappy" and this part of it i like very very much. i have/had other issues with this one...
 
the other one i have is 1.2 Ghz old Athlon with only 224MB ram (256-32GB for graphics card) and it works a bit slower but still fast enough for surfing, documents, emai, some pictures, movies.... except flash is slow of course.
 
EDIT: Also i use the 10.04 version because it's LTS and i don't have to deal with upgrades and setting up the system every time i upgrade.

---

### Post by Quackers on 2010-11-15
Download and burn the iso and then select "try Ubuntu" to make sure all the hardware works first. That would be my suggestion.
If all is well then you can do a fresh install. Upgrading across 4 or 5 versions may be somewhat problematical, and definitely slower.

---

### Post by Rex Bouwense on 2010-11-15
Mastablasta, I just checked out the manual in your signature.  +1.  I wish I had found that when I started.

---

### Post by TNT1 on 2010-11-15
> **Calais225 said:**
> 

Nice to have a new computer and a clean install.  What should I add, what should I avoid, should I increase the ram to 2 gigs?




Ask a silly question... RAM is like beer.... More is always better...

Oh, and what was the price of the machine? Sounds like a good little box, similar spec to my one thinkpad.

---

### Post by TNT1 on 2010-11-15
> **Quackers said:**
> . Upgrading across 4 or 5 versions may be somewhat problematical, and definitely slower.

I disagree, go from 8.04 to 9.04 with the alternate upgrade cd, and from there to 10.04/10.10 with alternate upgrade cd. he wants to learn, so let him, also, with a new machine, he has no data to backup. He can always do a fresh install from the 10.04/10.10 alternate cd if it all goes pear-shaped...

---

### Post by Quackers on 2010-11-15
> **TNT1 said:**
> I disagree, go from 8.04 to 9.04 with the alternate upgrade cd, and from there to 10.04/10.10 with alternate upgrade cd. he wants to learn, so let him, also, with a new machine, he has no data to backup. He can always do a fresh install from the 10.04/10.10 alternate cd if it all goes pear-shaped...

Aren't you comparing apples with oranges?

---

### Post by TNT1 on 2010-11-15
> **Quackers said:**
> Aren't you comparing apples with oranges?

Probably.

---

### Post by Calais225 on 2010-11-15
My new laptop is a Dell Vostro 1410 and there were discount coupons which brought the price down to just under $250 Canadian funds.  Could not resist.  Bigger than a netbook but a 14 inch screen is easier on my old eyes and the full size keyboard, cd burner, webcam and wireless n card plus a 6 cell battery made it a killer deal.
Time limited until they sold 500 units so I was lucky.

It should be okay hardware wise since it already has Linux on it so my plan might be to install Meerkat which should keep me messing around as it develops.

I managed to convert my dual boot XP/Karmic desktop back to XP only during which time I learned quite a bit----the hard way.

The nice thing about winter coming up is that I will have lots of time to experiment--being retired helps too.

Thanks for all the suggestions so far.  

More thoughts welcomed.

Cheers,

W.

---

### Post by MrPage on 2010-11-15
can you provide a link to the computer on Dell?
I can't find it...

---

### Post by Calais225 on 2010-11-15
This WAS the deal, sold out a couple of days ago.

[http://www.redflagdeals.com/deals/main.php/alldeals/comments/rfd_10th_anniv_exclusive_dell_285_vostro_14_laptop_199_ultrasharp_u2211h_ip/](http://www.redflagdeals.com/deals/main.php/alldeals/comments/rfd_10th_anniv_exclusive_dell_285_vostro_14_laptop_199_ultrasharp_u2211h_ip/)

there was a second coupon listed in the comments section of the above to allow a double dip.

Here is a desktop deal with even better specs...

[http://www.redflagdeals.com/deals/main.php/alldeals/comments/redflagdealscom_exclusive_dell_vostro_230_desktop_pc_w_intel_e5400_27ghz_3g/](http://www.redflagdeals.com/deals/main.php/alldeals/comments/redflagdealscom_exclusive_dell_vostro_230_desktop_pc_w_intel_e5400_27ghz_3g/)

---

