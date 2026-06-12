---
title: "Problem with a flash based browser game."
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Digital X on 2010-01-08
I recently had a dual boot installation with Windows XP and Ubuntu 9.10. The game "Battleon" works fine on windows with flash player 10 as the game only needs flash player 8 to run. I have flash player 9 installed on Ubuntu. the game loads the login screen, but when it goes to load the game itself, it just says "Loading" and will not continue. How would I go about resolving this issue? and there are other things i need to install? Kind of new to Ubuntu so i dont know about what packages or whatever are needed to fully work flash games.

---

### Post by Desert Sailor on 2010-01-08
The brains of the forum will be along any minute and tell you all about how to install the latest flash player...  But the real answer is there is a problem with some web-sites and the Linux flash player version.  My bet is that no matter what you do, this won't get resolved until April when 10.4 is released.

One other possible solution is to back up to Ubuntu 9.4, the Flash player worked in that version on these websites as far as I know.

---

### Post by Digital X on 2010-01-08
OK, Well the funny thing is, I had the game working perfectly before when I had Ubuntu a while ago. I don't know why it suddenly decided to mess up now.

---

### Post by Desert Sailor on 2010-01-08
Yes, I understand.  My flash was working in 9.4 but is broken in 9.10  I have decided to live with it and hope that it is patched along the way.  I will be more careful next time before I jump on a new release.  I am thinking that 10.4 is a LTS and I may install that and then just stay there for a while (couple of years) rather than doing a clean install every 6 months.   I dunno, there are pros and cons either way.  

Don't get me wrong, I am very much committed to Ubuntu and love that I am free of the Redmond Virus ver-7, but this is one little irritation which has been bugging me also.

---

### Post by J V on 2010-01-08
"The brains" have arrived :)

First try to install the ubuntu-restricted-extras package.

Now open a terminal (Accessories) and type in:
uname -m

This will show you your architecture.

Tell me what architecture you have (If you are running 64 bit you will need to manually install 64 bit flash, which is easy)

---

### Post by Desert Sailor on 2010-01-08
Yey...  the brains are here.  J.V. will you just move into my house and be my 24/7 Linux Advisor..??  

My install is the 32 bit Ubuntu 9.10 version on a AMD 64 processor. My flash works on all the U-tube videos and most everything, BUT, there is one website which uses a flash-based chatting routine.  It just will not work for me, but the rare times I wanna go there, I just boot my Virus machine with the Windows XP.  I believe the problem the web-site's software vs. Linux, although it worked for me when I was running 9.4.  I have been through the install advice over the past few months several times, but it just doesn't work.

Help Digital X and I will follow along....

---

### Post by J V on 2010-01-08
Not familiar with architectures, but methinks a 64 bit app can run on a 64 bit machine with a 32 bit OS?

These lines will uninstall 32bit flash (apt-get) download (wget) unpack (tar) and remove the temporary package (rm) for 64 bit flash```
sudo apt-get remove flashplugin-nonfree
wget "http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz"
tar -xzf "libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz" --directory "~/.mozilla/plugins"
rm -f "libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz"
```Paste the lot into a terminal, restart firefox and you're set :)

(Only do this if you are on 64bit, otherwise it will screw it up)

Note: The 64 alpha is more stable on 64 bit than the 32 bit release... Much more stable... Just because its more stable you shouldn't forget its still alpha, don't expect too much, I still get lockups from a memory leak on a certain websites flash player... *cough* gamespot *cough*

It should at least help though :)

Edit: wow, checked it out, the mem leak was fixed with the 64 bit version... nice :D

---

### Post by Digital X on 2010-01-08
When you say type "uname -m" do i literally type that? or is uname the username I'm using for Ubuntu? I typed "uname -m" and it said i686 and that was it, I have no idea if this is 32 or 64 bit..

---

### Post by J V on 2010-01-08
Nope, thats 32 bit, you installed ubuntu-restricted-extras, and thats enough for you, try it out :)

---

### Post by Digital X on 2010-01-08
Hmm, last time i tried installing restricted extras, it says something about super cow, and it couldn't initialise (sp?) the installment. I'll try loading it again, and see what happens. Flash game is incredibly laggy and takes ages to load the page, let alone the game. That's if it DOES get past loading..

---

### Post by Sef on 2010-01-08
> When you say type "uname -m" do i literally type that? or is uname the username I'm using for Ubuntu? I typed "uname -m" and it said i686 and that was it, I have no idea if this is 32 or 64 bit..

That is 32-bit.   This is 64-bit: x86_64

---

### Post by Digital X on 2010-01-08
Ok thank you. So the quote full of code that was on page 1, I should of pasted that in the terminal or not?

---

### Post by J V on 2010-01-08
Nooo, no, don't paste that, it will screw up your flash...

if you did, open your ~/.mozzilla/plugins and delete the flashplayer.so file

then install flashplugin-nonfree...

---

