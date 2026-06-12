---
title: "Need help installing Ubuntu on old computer, dont know administrator password"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by BeeDeeGee on 2009-05-08
Ok, my wife's office gave her this old computer they were just going to throw away, so I was going to put ubuntu on it. However, it wont let me install from the cd because I dont have administrator priviledges, and there is no way to get the password. Is there anyway around this, please help.

---

### Post by raymondh on 2009-05-08
> **BeeDeeGee said:**
> Ok, my wife's office gave her this old computer they were just going to throw away, so I was going to put ubuntu on it. However, it wont let me install from the cd because I dont have administrator priviledges, and there is no way to get the password. Is there anyway around this, please help.

are you able to boot into BIOS and delete administrator's password, or at leats change it to your own?   The command to enter bios is usually seen as the computer starts up.  May also be called "set-up"

---

### Post by raydeen on 2009-05-08
Is the system asking you for a password in Windows or at the system startup when you're trying to load the LiveCD? If it's at system startup, what make and model of computer is it? On some Dell systems, the admin password could be reset by opening up the case and switching a jumper on the motherboard.

---

### Post by pro003 on 2009-05-08
you need to open the box and take a look at three pin jumpers where it says clr cmos, those pins are usually 'jumpered' on pin 1 and pin 2, and what you need to do is to shut down the computer open your box and place the jumper on pins 2 and 3 for about 1 min and then place the jumper back on pin 1 - 2. 

That should do.   

After you do that you caN USUALLY ENTER in BIOS AT BOOT by pressing DEL or F2 or F12 to manage boot options.

by the way what kind of configuration is this? If it's something like Pentium II, don't expect it'll work.

---

### Post by dvl300 on 2009-05-08
run cmd
and type in the following
net user Administrator *
hit enter
then it will ask for a password
type one in
then it will ask you to retype
the password to confirm so re
type in the password just
entered

now log out and press Ctrl
Alt and Del twice! and enter
in user name Administrator
and in password the one you
just entered and your good
to go! and install Ubuntu
from Admin!
Enjoy!
:)

---

### Post by BeeDeeGee on 2009-05-08
it;s a dell, with windows xp pentium 4

---

### Post by eriqjaffe on 2009-05-08
If it's a Windows admin password, I've used [this]("http://home.eunet.no/pnordahl/ntpasswd/") to reset admin passwords in the past.

---

### Post by BDNiner on 2009-05-08
You don't need adminstrator privilages to install ubuntu. I am guessing that you are trying to install it using wubi or whatever it is called from inside windows. You can boot the computer from the CD drive and it will run through the setup also.

---

### Post by Kareeser on 2009-05-08
You don't need to install Ubuntu from inside Windows. It's actually preferable from a speed and efficiency standpoint to format the hard drive and install Ubuntu on its own separate partition.

---

### Post by BeeDeeGee on 2009-05-08
> **dvl300 said:**
> run cmd
and type in the following
net user Administrator *
hit enter
then it will ask for a password
type one in
then it will ask you to retype
the password to confirm so re
type in the password just
entered
 
now log out and press Ctrl
Alt and Del twice! and enter
in user name Administrator
and in password the one you
just entered and your good
to go! and install Ubuntu
from Admin!
Enjoy!
:)
 
 
When i hit enter after 'net user administrator*' 
 
it says
 
The correct syntax for this command is
 
NET USER
[username [password :*] [options]] [/domain]
username {passwoord :*} /add [options] [/domain]
username [/delete] [/domain]

---

### Post by dvl300 on 2009-05-08
sorry i ment net user administrator *

---

### Post by BeeDeeGee on 2009-05-08
I have a portable disk drive hooked up through usb because there is no cd rom installed. and i cant figure out how to boot from it in the BIOS. I can't find it. It sees the external cd rom when I'm in windows though

---

### Post by dvl300 on 2009-05-08
you need to include the space

---

### Post by BeeDeeGee on 2009-05-08
> **dvl300 said:**
> sorry i ment net user administrator *
 
 
yeah i had the * in there

---

### Post by dvl300 on 2009-05-08
[IMG]http://i41.tinypic.com/ap71id.jpg[/IMG]
screenshot!

---

### Post by BeeDeeGee on 2009-05-08
ok got it, but after entering pass I get " system error 5 has occurred access denied"
 
 
the username on here was localadmin instead of administrator i found out

---

### Post by dvl300 on 2009-05-08
try creating a guest account
and log in on that then
repeat what i told you

---

### Post by BeeDeeGee on 2009-05-08
trying that now, is there a reason why the external cd rom isnt showing up in the bios, it says is an unknown device

---

### Post by dvl300 on 2009-05-08
go here
[http://www.instant-registry-fixes.org/fix-system-error-5-has-occurred-problem/](http://www.instant-registry-fixes.org/fix-system-error-5-has-occurred-problem/)

---

### Post by dvl300 on 2009-05-08
check the connection?
and what are using to connect it?
usb, firewire? etc!

---

### Post by BeeDeeGee on 2009-05-08
usb

---

### Post by dvl300 on 2009-05-08
also try this
1. At a command prompt, type "control userpasswords2" and press Enter to open the Windows 2000-style User Accounts
    application.
2. On the Users tab, clear the Users Must Enter A User Name And Password To Use This Computer check box and then
    click OK.
3. In the Automatically Log On dialog box that appears, type the user name and password for the account you want to be
    logged on each time you start your computer.

---

### Post by dvl300 on 2009-05-08
if all else fails use this
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

---

### Post by BeeDeeGee on 2009-05-08
I am not aprt of the admin gorup so I cant access the user password manager. If I could just figure out how to boot from this damn cd drive. this thing is locked up pretty good

---

### Post by dvl300 on 2009-05-08
restart your pc then hit either F8 or F11
and hit enter on the drive that has your
ubuntu disc in
Or in bios change the boot order so the
disc drive that has your disc in boots
first when you turn on your PC

---

### Post by BeeDeeGee on 2009-05-08
boot menu is as follows
 
1. Normal
2. hard disk drive c
3. system setup
4.ide drive diagnostic
5. bootto utility partition

---

### Post by dvl300 on 2009-05-08
does this then
in bios change the boot order so the
disc drive that has your disc in boots
first when you turn on your PC

---

### Post by BeeDeeGee on 2009-05-08
:(that's the problem, it's not an option to boot from the usb drive that the external is connected through.

---

### Post by dvl300 on 2009-05-08
have you check your bios and done the following
in bios change the boot order so the
disc drive that has your disc in boots
first when you turn on your PC

---

### Post by BeeDeeGee on 2009-05-08
in the bios I went to boot order it only had three options
 
Hard drive C
intergrated NIC
and floppy drive which isnt installed
 
 
those are the only 3 I can change to boot orderfor

---

### Post by Niniel on 2009-05-08
You may have more options under "Hard Drive C".
On my box, there's an arrow and I can select which hd to boot from. If I have an external hd connected, it shows up there as well. Or have you tried that already?

---

### Post by BeeDeeGee on 2009-05-08
yeah, there is nothing there
 
will moving thejumpers work you think, that was mentioned way earlier

---

### Post by ushills on 2009-05-08
google for the machine and find out how to reset the bios.  You may have issues with the usb cd due to bios driver issues, could you try creating a bootable usb flash drive, note this may also not work. Or remove hd put in other machine and install there.

---

### Post by Niniel on 2009-05-08
Speaking of BIOS - check the manufacturer's website for a possible update to that. 
Btw, who made your computer?

---

### Post by BeeDeeGee on 2009-05-08
dell, its pretty old, my wifes office was throwing it out. It used to be hooked up to a network i guess, i've tried everthing and nothing works. it sucks. is there really no way to jsut format the hard drive without the admin pass

---

### Post by ushills on 2009-05-08
if all else fails you can install ubuntu over a network at boot time.  google install ubuntu network pxe and you will find quite a few guides.  you need to have a working ubuntu system that you can use as the server but this will work without a cd-rom or usb.

---

### Post by BeeDeeGee on 2009-05-08
cool i will try that, I have ubuntu on my laptop, how would I go about this.

---

### Post by albinootje on 2009-05-08
> **BeeDeeGee said:**
> is there really no way to jsut format the hard drive without the admin pass

Take out the hard disk, put it in another machine, install Ubuntu, and then place the hard disk back in the Dell machine.
I've done this successfully many times through the years, also with laptop disks.

---

### Post by dvl300 on 2009-05-08
check if usb legacy support is on in your bios?

---

### Post by BeeDeeGee on 2009-05-08
> **dvl300 said:**
> check if usb legacy support is on in your bios?
 
 
yeah , theres is usb emulation optin

---

### Post by dvl300 on 2009-05-08
enable that then restart and go back into the bios
and change the boot order so the
disc drive that has your disc in boots
first when you turn on your PC

---

### Post by BeeDeeGee on 2009-05-08
tried but it isnt recognizing the external cd rom. so it isnt an option in the boot order. but when I'm in windows i can see it, i dont get it

---

### Post by dvl300 on 2009-05-08
how many desktop pc's do you have apart from the one your trying to install to?

---

### Post by BeeDeeGee on 2009-05-08
jsut this one i'm trying to get into.

---

### Post by dvl300 on 2009-05-08
do you have a 1gb pendrive by any chance?

---

### Post by BeeDeeGee on 2009-05-08
i have a 4 gig as a matter of fact

---

### Post by dvl300 on 2009-05-08
well install the live cd to your pendrive

---

### Post by BeeDeeGee on 2009-05-08
yeah i've tried this before too, it doesnt recognize the pen drive either. guess i'm just have to forget about it, thanks alot for all the help

---

### Post by dvl300 on 2009-05-08
wait go here
[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/]("http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/")

---

### Post by dvl300 on 2009-05-08
sorry forgot use wubi
[http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by ACupOfCoffee on 2009-05-08
Has nobody thhought that the computer doesn't support booting to USB devices?
I am 100% certain that that is your issue. Most USB optical drives are nothing more than regular desktop drives and an adapter inside a fancy case. If you're comfortable taking things apart see if this is the case with yours. If so, you'll be able to boot to it once it's connected via ATA.

---

### Post by huggies15 on 2009-05-08
I dont know if uve seen this, but it might just work for u...

[http://internetbusinessdaily.net/how-to-hack-a-window-xp-admins-password/](http://internetbusinessdaily.net/how-to-hack-a-window-xp-admins-password/)

it looks pretty simple, but ive never been in this situation before so dont know if it actually works...
if all else fails u might want to install on the hdd in a different machine and move it over.

cheers

---

### Post by albinootje on 2009-05-08
> **dvl300 said:**
> sorry forgot use wubi
[http://wubi-installer.org/]("http://wubi-installer.org/")

Sounds like a great idea, but for Wubi you need admin rights to install it : [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by albinootje on 2009-05-08
> **BeeDeeGee said:**
> yeah i've tried this before too, it doesnt recognize the pen drive either.

How did you prepare the usb stick ? I had the most success with unetbootin for preparing bootable usb sticks : [http://unetbootin.sf.net](http://unetbootin.sf.net)

Did you test the bootable usb stick on another machine first, to make sure it worked ? Just wondering.

---

### Post by 73ckn797 on 2009-05-08
I have been able, sometimes, to bypass the password in XP. When the login comes up press ctrl+alt+del twice and see if it allows you to type admin or administrator.

The best other solution is to remove the drive and connect to another machine as mentioned before and either format or install Ubuntu using that machine. Then go buy a CD drive or buy one then boot from the Ubuntu LiveCD.

---

### Post by -kg- on 2009-05-08
Or something that I haven't seen mentioned yet.  Why don't you just buy an internal DVD/CD-R/RW drive and install it?  They're cheap, and then you shouldn't have all these issues booting to an external drive that obviously isn't supported as a boot device.

---

### Post by 73ckn797 on 2009-05-08
> **-kg- said:**
> Or something that I haven't seen mentioned yet.  Why don't you just buy an internal DVD/CD-R/RW drive and install it?  They're cheap, and then you shouldn't have all these issues booting to an external drive that obviously isn't supported as a boot device.


See post above yours.:P

---

### Post by albinootje on 2009-05-08
> **-kg- said:**
> Or something that I haven't seen mentioned yet.  Why don't you just buy an internal DVD/CD-R/RW drive and install it?  They're cheap

Yes, but I think it's cheaper and possibly more social and fun to ask a friend or relative with another computer to do the installation on that other computer and then take the hard disk back home. :)

---

### Post by pro003 on 2009-05-09
> **BeeDeeGee said:**
> Ok, my wife's office gave her this old computer they were just going to throw away, so I was going to put ubuntu on it. However, it wont let me install from the cd because I dont have administrator priviledges, and there is no way to get the password. Is there anyway around this, please help.

Ok. You do not need to install ubuntu from windows, you should boot from CD-ROM i.e. installation CD which you have obtained and as far as for win passwords the easiest way for you is to find something called passware key enterprise v8.xx - boot from that and you'll wipe all users and admins passwords... and just to say it: do it completely on your own risk.

Still I'm not quite sure what are you trying to do though...?

---

### Post by albinootje on 2009-05-09
> **pro003 said:**
> You do not need to install ubuntu from windows, you should boot from CD-ROM i.e. installation CD which you have obtained and as far as for win passwords the easiest way for you is to find something called passware key enterprise v8.xx - boot from that 

The OP had problems booting from a cdrom-drive already.

---

### Post by 73ckn797 on 2009-05-09
> **pro003 said:**
> Ok. You do not need to install ubuntu from windows, you should boot from CD-ROM i.e. installation CD which you have obtained and as far as for win passwords the easiest way for you is to find something called passware key enterprise v8.xx - boot from that and you'll wipe all users and admins passwords... and just to say it: do it completely on your own risk.

Still I'm not quite sure what are you trying to do though...?

Have you not read though all of the posts?

---

### Post by pro003 on 2009-05-09
> **73ckn797 said:**
> Have you not read though all of the posts?

yes, I've read it. The guy needs to install ubuntu but he can't boot either from CD-ROM neither from USB/External drive. So, remind me, what are we talking about here?

---

### Post by pro003 on 2009-05-09
and yes, this quite looks like a topic for windows xp forums...

I'm out.

---

### Post by 73ckn797 on 2009-05-09
> **pro003 said:**
> yes, I've read it. The guy needs to install ubuntu but he can't boot either from CD-ROM neither from USB/External drive. So, remind me, what are we talking about here?


How they can install Ubuntu when they have an old computer with no CD drive or USB support.

---

