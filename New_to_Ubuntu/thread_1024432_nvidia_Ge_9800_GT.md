---
title: "nvidia Ge 9800 GT"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by v1p3r69 on 2008-12-29
i am using 

ubuntu 8.10 
Biostar P4M900-M7 FE Motherboard
Intel Pentium Dual Core E2200 2.20GHz OEM Processor 
zero therm CPU cooler 
160gb HD
sony dvd/cd rewritable
(2) Kingston 1024MB PC5400 DDR2 Memory
nvidia Ge9800 GT grahpics card 
riviera 5.1 channel surround sound card 
450w p/s 

( i hope this is enoff info on my system )

i have install ubuntu 4x's now and same result - the grahpics are running in " low " grahpics mode on boot up, 

i have spend hourds lookin and tryin the suggestion on the forums and still i am unable to use the card.... 

i have tryed to install the driver 173 and 177 / reboot and same error i get " low " mode... i am confused on the problem, i have tryed many things such as 

ie... 

```
http://ubuntuforums.org/archive/index.php/t-965180.html
```

i tryed all the diff. combos, and still no-go

i am not sure wat i am doing wrong or how to get this card to work in my ubuntu box. 

i am lost on wat to do and where to look next on the issue 


thanks 

v1p3r

---

### Post by gettinoriginal on 2008-12-29
Here is a great tutorial on sound/video, it will show you how to get the repositories for free and non free drivers and codes:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by v1p3r69 on 2008-12-29
its strange - bc i had it all going lastnight was workin great,,,

then i installed the ubuntu beryl and messed around with that was workin wonderful i was very impressed with my ubuntu was everthing i wanted it to be - then it crashed / i reboot and got the error for the 1st time... 

then i started to mess around with the error lookin online for other ppl with same problem.. found lost of issues and tryed all the commnets and suggestion ( and trust me im not sayin it not user error ) but something got to work or something im doing wrong. 

not sure where or wat to do now - i am lookin at your link/post now thanks... 

if there ne one who like to lend a hand for a min - i own a few IRC servers where and can troubleshoot one on one not toight it 2am here - but maybe tomarrow night if ne one has time 

thanks 

v1p3r 

sorry just very fustrated - ready to thu the box out the window lol

---

### Post by adobrakic on 2008-12-29
This happened to me once before, but for me I couldn't log on at all with the low memory graphics error. All I did was go on my Windows (i had dual-boot), and a day later went back onto linux and it was working fine.

But then again, I don't have a nvidia or anything, so your case could be different. 
:D

---

### Post by gettinoriginal on 2008-12-29
Alright, lets start with the first time you had a problem, everything was good, then you were adjusting settings in compiz, everything working, crash. 
Now lets try to reset your system:
Boot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

Now lets set compiz back to default:
In terminal:
```
gconftool-2 --recursive-unset -a /apps/compiz
```

Is it working yet ??

---

### Post by v1p3r69 on 2008-12-29
thanks for your post 

i have tryed wat u wanted me to do - i am able to change the resolution now 
its a start 

but the x server still will not start 

this is wat i get 

```
viper@server-1:~$ gconftool-2 --recursive-unset -a /apps/compiz
viper@server-1:~$ sudo -s
[sudo] password for viper: 
root@server-1:~# nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

root@server-1:~# 

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

---

### Post by v1p3r69 on 2008-12-29
then when i reboot i get same error running on low graphic mode :( 

ne suggestions ?

---

### Post by v1p3r69 on 2008-12-30
ok - i did a little trouble shooting lastnight... still could not get ubunutu 8.10 to work with my system - not sure why is a very strange matter. my graphics are very bad at this point ( lines down the screen - fuzz ect.... it was workin fine then after a bit of use it craped out )  

so a good friend told me to install 8.04 i was like what the hell why not ne thing is worth a shot at this point " i just want to be able to use my ubuntu " 

so i installed the 8.04 and i got the same error :( 

then took out the graphic card and sound card " going to use just teh on board system " and reinstall 8.04 and got the same error - low graphic mode.... but the screen is much better now no fuz or lines down the screen.... 

i would love to use this card with the system and with ubuntu 8.10 just not sure if i can or wat to do or try next 

thanks 

VIPER

---

### Post by gettinoriginal on 2008-12-30
Put your cards back in, then do the following:
Reboot > during grub splash, hit escape > Recovery mode > Enter (let finish)
Repair Broken Packages > Enter (if it asks about updates hit N) (let finish)
Try to fix X server > Enter (Let finish)
Resume normal Boot > Enter

Then if it is not working, to back up your xorg files in case you need it:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Then:
```
sudo gedit  /etc/X11/xorg.conf
```
And edit it to look like mine, but with your configuration:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by v1p3r69 on 2008-12-30
ok  - ill reinstall 8.10 and put computer back together and give it a shot... im at work now ill do it then i get home 

ok - i am sorry for the dumb questions - i have been playin with linux for about a yr now and ubuntu for about 1 mth... but alittle unsure wat u want me to do with ===> " And edit it to look like mine, but with your configuration " 

how do i get my config..... or wat you mean i know where to edit it... just unsure wat to put in there 


thanks

---

### Post by gettinoriginal on 2008-12-30
this is what you get:

```
viper@server-1:~$ gconftool-2 --recursive-unset -a /apps/compiz
viper@server-1:~$ sudo -s
[sudo] password for viper: 
root@server-1:~# nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "***_Configured Video Device" must have a Driver line_***.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

root@server-1:~#

Section "Device"
Identifier "***_Device0_***"
Driver "nvidia"
VendorName "NVIDIA Corporation"
EndSection
```

This is what I get::
```
Section "Device"
	Identifier	"***_Configured Video Device_***"
	Driver	"nvidia"
```
So with the command 
```
gksudo gedit /etc/X11/xorg.conf
```
Change Identifier to "Configured Video Device"

---

### Post by quadcam on 2008-12-30
I'm having this exact same issue... except I have a GeForce 6100 card
I opened my xorg.conf file and mine says :

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

i tried to install the Nvidia driver 177 over and over and then when xserver starts I get a black screen with a single yellow line across the top. I have to restart xserver repair and then it sends me into low res mode but at least I have full screen where as before i would have what looks like widescreen format. it's making me crazy because even my screensavers are jittery and laggy

heres a link to my previous post on this subject, maybe someone can find a solution. 
[http://ubuntuforums.org/showthread.php?t=1025411&highlight=video+card](http://ubuntuforums.org/showthread.php?t=1025411&highlight=video+card)

---

### Post by gettinoriginal on 2008-12-30
quadcam, how did you install driver 177??  Have you tried:
System > Admin > Hardware Driver ....and let your system search for the correct driver???  You have no driver in your xorg file.  Do not do anything just yet, but let me know about the above questions.  :P

---

### Post by v1p3r69 on 2008-12-31
ok - i have tryed it - my .conf file is just like your with my settings i have install the 177 driver in and out of recovery mode " root " and still nogo 

i have takin in all the suggestion that ppl have givin me and look at many post on line - i have tryed everthing other ppl have done and they say it works - well i cant get the nvidia ge 9800 GT card to work with ubuntu 

i have read it is supported and iv read it not supported im not sure ... then i got to lookin 

when i went in to the bios my pic was the same - and it never hot me that it might me a hardware iussue 

bc to my knowing when u enter the bios ur not usin the card 

so i remove the card and the sound card again and this time i reinstalled ubuntu 

and it worked - so im not sure if my conclusion are correct but this is my finding 

1 the nVidia Ge 9800 GT is not supported 

2 its a bad or damaged card 

i am not givin up i would love to see this system work on ubuntu and have all the fuctions of the nvidia card 

im kinda stuck dont know wat to do lol

---

### Post by gettinoriginal on 2008-12-31
Probably a bad card, as nvidia usually runs out of the box .  Try finding another one.  Good Luck :P

---

### Post by v1p3r69 on 2008-12-31
thank you for your help - i just ordered another one - should be here in a few dayz .... :) cant wait

---

