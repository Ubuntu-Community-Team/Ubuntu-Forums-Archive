---
title: "Password fails on Lexmark x2600 install"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by cloyd on 2009-11-17
Hi.  I'm new, but I really like what I've seen of Ubuntu.  I'm runnning UNR 9.10, and having problems installing the lexmark x2600 printer driver (lexmark-inkjet-08-driver-1.0-1.i386.deb.sh) .  It seems to work, up to the point where I must key in my password. I remember setting up 2 passwords during my install. One I give as when administrator privileges are required, and one for my "key ring" which I've only used for getting email.  Neither of these passwords work on the install. 

I've looked quite a bit on the forum and even tried a program called liblexz600cor0.deb. This resulted in an error: Dependency is not satisfiable: libstdc++5.  I've seen several solutions . . . some people seem to get the printer running, but thus far, I have not been able to use what I've seen suggested.

I really like Ubuntu . . . no crashes, faster booting (I'm using it instead of Vista home basic on a Gateway 2 gig memory netbook-- a nightmare  --too much os).  I want to keep on using this, but rebooting to go into Vista  in order to print is a royal pain.  

Is there any help?
Thanks in advance.

---

### Post by cariboo on 2009-11-17
When do you need to type in your password? Usually when installing anything you need to use the password you set up during the installation.

---

### Post by cloyd on 2009-11-17
Thanks.  I click on the file, and get window to open.  It asks if I accept the license agreement. I accept. I see an image of a printer in the window, and then, it asks for a password.  Neither of the two I set up in my install work. 

You know, I like this well enough to keep going back to windows when I must print.  But it would be so much better if I could get the printer to work. I might even get my wife to switch on her computer.

Thanks again.

---

### Post by cloyd on 2009-11-18
I'd really like to get my printer working.  I like UNR enough to put up with having to reboot in Windows to print, but it is a pain, though.not as much of a pain as Vista constantly freezing up on this netbook.  

I know some people do get the lexmark x2600 to work. I currently can't justify buying a new HP printer.  I'm hoping someone out there can tell me how to get it running. Is there anyone who can help?  Again, I can start the install on the driver from lexmark, but the install comes to a point where it asks for a password.  It will not accept the administrator password nor my key ring password. Is there another level of security that I forgot about during the install?  Is ti a bug? 

 Or, will the thing just not work?

---

### Post by cloyd on 2009-11-20
It appears that no one really has much to say on this thread.  My best option may be to buy a new HP when it is possible.  May not be such a bad idea, since 2 black ink print cartridges cost more than the printer cost new.

---

### Post by ktsteel on 2009-11-22
HI, I am having the same problem, so now  I can see it's not that I can't remember a password. That was driving me nuts. I read one post that said the Lexmark debian set up was not a driver just  a set up procedure. I am going to attempt a Z600 driver, stay tuned

---

### Post by aggie_surfer on 2009-12-19
Did anyone resolve this issue?

I have run into the same thing.  When using the print driver installer from Lexmark after updating to 9.10, I get into the password loop as described above.  I see nothing on the Lexmark site addressing the problem nor  do I see anything on this forum.  Did I miss something?
Thanks!

---

### Post by cloyd on 2009-12-21
> **aggie_surfer said:**
> Did anyone resolve this issue?

I have run into the same thing.  When using the print driver installer from Lexmark after updating to 9.10, I get into the password loop as described above.  I see nothing on the Lexmark site addressing the problem nor  do I see anything on this forum.  Did I miss something?
Thanks!
   

Aggie_Surfer, I still haven't solved the problem. I'm dual booting, and when I _must_ print, I reboot in Windows.  But Ubuntu is cool enough I'm willing to do that. I do wish someone would help with this, but it seems that my best bet is to buy a new computer, maybe an HP, though I do have someone who might help me find a Ubuntu or Linux compatible printer.  I don't know what you paid for your Lexmark, but mine was less than two print cartridges, and the cartridges don't last that long even on quick print.  Will do this most likely sometimes after April 15th, if you know what I mean.

---

### Post by aggie_surfer on 2009-12-21
Thanks for the reply, Cloyd.  This install worked so fine in release 9.04.  So I was really disappointed to run into this problem with release 9.10.  I'll keep looking for a solution and will post back if I find something that works. Please do the same if you come across something.   I paid less than $50 for the X2600.  It meets my needs but the ink cartridges are too expensive!  I love Ubuntu -installed on a netbook, ASUS 900A.  No windows on this system.

---

### Post by cloyd on 2009-12-22
You just gave me some important information: you said the Lexmark installer worked on 9.04.  If I understand you right, it might solve half of my problem.  I have another laptop, (not a netbook) running 9.04 that stays at home (it also is a dual boot machine, so I can print in Windows).  I have a Lexmark x5495 on that machine, and it doesn't work with any of the drivers supplied on the Ubuntu distribution.  Perhaps I take the x2600 home from the office, and take the x5495 to the office . . . . I could print in Ubuntu at home, anyway.

---

### Post by aggie_surfer on 2009-12-27
Cloyd - I was able to get the Lexmark printer  install to work on rel 9.10.  I resolved the password loop by manually assigning a password to usr root.  No password was indicated as it was for my user ID (my being the administrator).  After assigning the same password to root, all worked fine!

---

### Post by cloyd on 2009-12-28
Thanks, aggie_surfer.  I'm on vacation right now . . . till about Jan 4th.  When I get back to the office, I'll see if I can do this.  I'm going to have to read up a little on my "Linux for Idiots" and "The Official Ubuntu Book to do it, but your help is GREATLY appreciated. (I think I am indeed turning into a bit of a geek . . . I brought The Official Ubuntu Book with me on vacation. I almost bought some other Ubuntu & Linux books at a book store, but they were 2 to 7 years old . . . thought  perhaps what I already had might be better.)

---

### Post by cloyd on 2010-01-04
Thanks again, Aggie-surfer.  Got to the office this morning (through snow and ice) and followed your instructions (except I used a different password for root than my usual administrative password . . . thought that indiscriminate signing in as root may open me up to doing all kinds of things I really don't mean or want to do).  It worked like a charm.  Getting closer to being Windowless on this computer.  My next big challenge is to see if I can get my 9.04 machine at home to print . . . thus far, can't find any kind of driver. 

Your solution makes life easier.

Cloyd

---

### Post by JosephGarrison on 2010-01-24
I googled adding the usr root pasword, and great news! I was able to add a password and install the printer. Thanks to everyone who worked this problem out. You all saved me a bundle.

---

### Post by cloyd on 2010-01-24
JosephGarrison, 
Sorry I didn't check my email earlier.  There is lots of help online. Still, I'd suggest _The Official Ubuntu Book_ by Benjamin Mako Hill.(fourth edition -though surly fifth should come out soon . . . this one focuses on 9.04) . Aggie_surfer told  me to set the root password here on the forum.  I went to the book to learn how.  Hope you are enjoying Ubuntu as much as I am.

---

### Post by ThisGirlsLife on 2010-04-28
So I have been using Ubuntu now for 2 years, and I'm still learning the whole terminal thing. It took me forever to find a way to get passed the admin root passwrd, but I did it. 

FIRST you can go to the Lexmark website and download, make sure you download the .deb file which is debian, [http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2600&actp=PRODUCT&id=DR860&segment=DOWNLOAD&userlocale=EN_US+&locale=en](http://support.lexmark.com/index?page=content&productCode=LEXMARK_X2600&actp=PRODUCT&id=DR860&segment=DOWNLOAD&userlocale=EN_US+&locale=en) or [http://support.lexmark.com/index?page=answers&detectedProductFacet=CMS-CATEGORY_REF.LEXMARK.PRODUCTS.ALLINONE.LEXMARK_X2600&searchid=1272505199477&userlocale=EN_US%20&locale=en&segment=DOWNLOAD&question=x2600&productCode=LEXMARK_X2600#2](http://support.lexmark.com/index?page=answers&detectedProductFacet=CMS-CATEGORY_REF.LEXMARK.PRODUCTS.ALLINONE.LEXMARK_X2600&searchid=1272505199477&userlocale=EN_US%20&locale=en&segment=DOWNLOAD&question=x2600&productCode=LEXMARK_X2600#2) then after download extract it to your desktop.

SECOND go to terminal and put      sudo passwrd root     after that it will ask you for a password, give them whatever, after that close terminal and double click the icon for the driver and follow through, make sure your cable isn't connect till you are told so, works like a charm!!!

---

