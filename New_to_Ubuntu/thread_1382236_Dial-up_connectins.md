---
title: "Dial-up connectins"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by K-Bar on 2010-01-15
[SIZE=2]After installing Ubuntu 9.10 on my computer I was distressed to learn that my ISP does not support Linux and Linux does not support dial up connections.[/SIZE]
 
[SIZE=2]After consulting the help screens I found that the first thing I had to do was run scanModem, which I did. I gathered from that that the next step was to install wvdial, which I did, however when I tried to configure it I got an error message saying my modem was not detected and needs to be configured.[/SIZE]
 
[SIZE=2]I can't seem to find any instructions on how to do this.[/SIZE]

---

### Post by alwayshere on 2010-01-15
You will need "gnome ppp" if you dont have it alredy put this command in terminal to install it

 sudo apt-get install gnome ppp
----------------------------------------------------------------------


                ** Here is a link to a how to **

 [http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html]("http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html")
---------------------------------------------------------------------
    ** The above link should sort you out or try my how to below **
---------------------------------------------------------------------

If you are using a full hardware external modem(IS THE BEST OPTION !!)
go to "gnome ppp" 

put your dailup number in phone number area
put your dailup user name and password in

now set up modem if you have a serial conection use "/dev/ttyso from drop box
or if your using a usb conection change /dev/ttyso to /dev/ttyUSB0 (note manualy change it point click and edit it)
set dail type to tones

tick all boxs in options tab

once all done click save tick box at top left

now when you turn on your pc it will dail up straight away

if your using a pci modem it will be an uphill battle best to get full hardware external modem
as i did .they're cheap as chips

im using a dynalink v1456vqe serial conection ) a bit old school v90

i set up a dlink dfm-562e serial conection ) on my mates macbook which is a v92

no serial port no worries just get a serial to usb adapter cord and use the /dev/ttyUSB0 as i said above

---

### Post by K-Bar on 2010-01-15
[SIZE=2]I have seen that link before Alwayshere (I did search a couple of other threads before starting this one). The problem is that I dont have a networking option on my System/Admistration menu. Is there something I have to do to put it there?
[/SIZE]

---

### Post by alwayshere on 2010-01-15
Thats why I left that bit out and just put "go to your gnomeppp"
have a bit of a look about for it or one of  the below commands in terminal should launch it .


gnomeppp


gksudo gnomeppp


sudo gnomeppp

note you might have to put a space between the e and ppp . eg :gnome ppp

---

### Post by alwayshere on 2010-01-15
try lookling under :"Applications then internet " gnomeppp  might be there

---

### Post by alwayshere on 2010-01-15
ahhh haaa this is the command to launch it 

gnome-ppp 

hey sorry to muk ya about but as i didnt hav it installed as i dont have dailup thesedays i couldnt test it but now i have installed it and gnome-ppp  does launch it.

I should have asked you at the start Are you using a external hardware modem ??

---

### Post by JimInLakeland on 2010-01-15
I have not even thought about dialup in years.

---

### Post by K-Bar on 2010-01-15
> **alwayshere said:**
>  I should have asked you at the start Are you using a external hardware modem ?? It is an internal modem, 56k pci data fax modem that came with a Dell Insprion 537.
 
I did find that program but I can't seem to execute it. I tried running it from the directory it is in and I get an error message that it couldn't find it.

---

### Post by alwayshere on 2010-01-15
You will need an external hardware modem  they are cheap as chips .I still have my old one you can have it if ya want just pay for the postage. but you should get one local for cheaper id say. 

---------------------------------------------------
in the terminal put below to install gnome ppp 

sudo apt-get install gnome ppp 
---------------------------------------------------

and in terminal put below to launch gnome ppp

gnome-ppp 
--------------------------------------------------

---

### Post by lkraemer on 2010-01-15
KBar,
Linux does support dialup, but you might need to install wvdial.

Once you run the scanmodem script, you will need to get back with
Marvin and the folks at [www.linmodems.org](www.linmodems.org) to locate exactly what
Winmodem you have in the computer.  Then you will need to install
the correct driver package (some require purchase) to make the
modem functional.  At that point wvdial should detect the modem.
But, You need to configure wvdial first, then you also most likely
need to setup pppconfig for pap or chap connections.  When you
have wvdial working, then you can try Gnome-PPP.  Otherwise you
will probably never get it functional, unless you're mighty lucky.

[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)
Posting #4 will assist you.

It's best to just purchase a used Serial US Robotics Hardware Modem
from ebay, as these work fine with Linux.  wvdial and Dialup works
fine with them.

lk

---

### Post by K-Bar on 2010-01-15
I did run scanModem and I did install wvdial. I tried to send an e-mail to [EMAIL="discuss@linmodems.org"]discuss@linmodems.org[/EMAIL] but it didn't go through.  I think I am going to have to try that again

---

### Post by alwayshere on 2010-01-15
good luck youll need it

---

### Post by Bartender on 2010-01-16
K-Bar, if you're the kind of person who likes to face impossible odds, more power to you.  Good luck with the winmodem.

If you want to get online with Ubuntu, buy a serial hardware external modem, then buy a Sabrent SBT-USC1M so you can plug into USB.

Case solved.

---

### Post by lkraemer on 2010-01-16
K-Bar,
The reason your email was rejected is the folks at [www.linmodems.org](www.linmodems.org)
only accept emails in PLAIN ASCII TEXT.  NO OTHER FORMAT, PERIOD!!!!!

So, just go into your email and set it for PLAIN ASCII with no encoding.
It took me a while to find that out also......the hard way.....

Good Luck with the Win-Modem.......You're going to need it.

Oh, if you get a used External, Serial, US Robotics Hardware Modem,
and go through the guide, you should be online within about 30 minutes.
Just remember that you will open a Terminal Window, start wvdial, and then
leave that window open for the duration of your connect session.  Once you
have finished you can use CNTL-C to terminate your session, then close
the Terminal Window.  And when all is working fine, just setup
Gnome-PPP.  Then you will be all set.


lk

---

### Post by K-Bar on 2010-01-16
Thanks Ikraemer, I didn't realise my e-mail program defaulted to html text.
 
My Windows partition can use the modem; it can't be that difficult to get Linux to do it.

---

### Post by K-Bar on 2010-01-17
It seems it was a sequence error on my part.  I knew I was going to need hsfmodem but I thought I had to configure wvdial first.  That was backwards.  Once I installed hsfmodem wvdialconfig worked

---

