---
title: "Lenovo g780 no wifi an ethernet port not working on ubuntu 13.04"
date: 2013-10-14
forum: Networking &amp; Wireless
---

### Post by vzkratos on 2013-10-14
hi this will be my first thread so i'll try to explain myself the best i can.

Details:
lenovo g780 with  dualboot ubuntu 13.04 and windows 8
ubuntu has been installed on uefi mode by the way
problems:
The wifi is on i can see my router connection,but when i click on it, it asks me for my password i put in and then it tries to connect but it fails and it just keeps asking me over and over,
the password is the right one.
The other issue is the ethernet port wont recognize the data from the ethernet wire.[i managed to get around that with an ethernet to a usb adapter though and that way i get internet working]
On the windows side i get everything working normal,wifi is good ethernet works ok.

In the past i had  on this same computer ubuntu 11.10 12.04 and 12.10 not at the same time though and i still had issues with the wifi,when i was on 12.10 i managed to get wifi working it was super slow i read a post from some guy who had the same computer and he had this codes for the terminal on 12.10

[FONT=arial]sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma

[/FONT][FONT=arial]sudo modprobe wl

now the connection would turn off or reset it, and then when it would come back it would be really good super fast, but "there was something really strange for some reason it will hog all the data on the house,therefore any other wifi enable device would suffer from a really slow connection to the wifi until i wiil turn off the wifi or ran the first command above to stop the wifi"

i honestly don't understand why it would make all other  device's connections slow but that's what it did, i could not use the wifi because of that, i will **** everybody on the house because i will make their speed go  super slow.
i in fact don't understand most things on linux [ubuntu] or know how to do them but if there is anything that i should do  please include the commands that i gotta follow thanks in advance.

p.s. 
this is unrelated to networking  but there is another issue that i have on 13.04,whenever i start ubuntu after grub the screen goes black i figure out by luck that by holding fn key an arrows i can restore the screen but it's really annoying if anyone know how i can fix that issue it would be great,but my main concern right now is the networking.[/FONT]

---

### Post by wildmanne39 on 2013-10-14
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by vzkratos on 2013-10-14
thanks for helping 
here we go
ok so i try to upload the 2 the 1 that is the tar file and the script. it did not allow me to upload the script file the same way i did with the tar now i have a question i'm confused am i supposed to run this commands while connected to an internet connection or without it i got lost on that part, but anyways what i did is i'm hooked to the internet through ethernet to a usb adapter i got internet and ran the commands.
please let me know what else you need.


thank you again.

---

### Post by wildmanne39 on 2013-10-14
Please do:
```
sudo apt-get purge --remove bcmwl-kernel-source
```
Then:
```
sudo modprobe -rv wl
sudo modprobe brcmsmac
```
Thanks

---

### Post by chili555 on 2013-10-14
@vzkratos --

I read your PM. My good friend Wild Man has the solution for you. He is as good or better here as anyone and I suggest you follow his solution.

---

### Post by vzkratos on 2013-10-14
thank you good sir  for your support i will try it.

---

### Post by vzkratos on 2013-10-14
thanks i will chili godbless you both.
so thank you

---

### Post by vzkratos on 2013-10-14
wildman it didn't work i don't know what happend.
first command went fine the bcmwl thing got removed
2 command said    FATAL: Module wl not found.
3 command said     nothing just went through
i'm gonna restart the laptop maybe that updates and fixes the problem.

---

### Post by wildmanne39 on 2013-10-14
It should be working, go to network manager and make sure wireless is enabled and see if you can see your network.
Thanks

---

### Post by vzkratos on 2013-10-14
Yes I actually Can see my network, I have tried to connect to my wireless and it just didn't connect.  I haven't go to network manager yet but I'll go and make sure that says wireless enable.
I'm gonna restart the computer when I get back. 
About that message that said fatal module not found,was that Ok or was that a problem. 

P.s. 
This was an upgrade from 12.10 to 13.04 wonder if I should do a fresh start and just install 13.04 from the usb stick not run the automatic updates and then once is set and running run your commands.

---

### Post by Hadaka on 2013-10-14
Hi, from the netinfo file the Wildman had you 
do, I am seeing some confusion..
you have..
ETH0
ETH1
ETH2
WLAN0
Since you have your ethernet (wired) cobbeled together with a usb
that needs to be disconnected (removed)
then do ..
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
BOOT
*replace the ethernet cable~ [computer]~~~~~[modem/router]  NO usb
then BOOT again.
the wired side should be working.
Your wired side-Eternet uses the ALX driver --that is supported by 13.04
Your wireless uses the brcmsmac..
*If your wired connection comes to life after the above then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
ignore any errors..then do..
```
sudo modprobe -v brcmsmac 
```
**IF the 2 above dont work..then i would suggest re-loading 13.04
Don't be concerned if on a reload the wireless is not working and dont use
the usb connection...just load the os.
post back the results and Wildman or someone else will guide you through.
also IF you do reload 13.04 please do NOT load b43,wl,or anything else, inludeing
the suggested "proprietary" driver...ignore that
thanks.

---

### Post by vzkratos on 2013-10-14
allright thanks for the support hadaka.
1 like i said i was confused on wether i should do the tar file that wiseman told me to do in the beginning with the wired ethernet to usb hooked up to the computer or not.Now with your response  i see that it had to be run without the wired set up.
2 i understand that i gotta run your first command no wires,reboot with just ethernet cable plug in into the ethernet port only,and that if the connection for wired works run the second command to make it stick,and then follow up with the 3 command and ignore any errors mentioned during the process.

3 when you say reload the system you mean do a fresh start from cd/usb live and start fresh from scratch right?
also you mention that if i don't see the wifi working not to worry about it and just install and load the os correct?
now once i installed the fresh os and load it for the first time is it ok to use the wired ethernet to usb adapter to load updates or maybe just to surf the web?


p.s.
funny thing now that i reloaded the os i don't see my network anymore.
from this point on i'm gonna follow your guide hadaka.

---

### Post by wildmanne39 on 2013-10-14
This message is okay About that message that said > fatal module not found,was that Ok or was hat a problem. it just means the purge command unloaded the driver when you ran it. I do not see a reason to install 13.04 fresh unless you are having other issues or we run into some other issue we can not resolve with your wireless.

---

### Post by wildmanne39 on 2013-10-14
I see something I missed earlier the brcmsmac driver is dependent on bcma and you have that blacklisted, please do:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Then remove:
```
blacklist bcma
```
save and close gedit then reboot.
Thanks

---

### Post by vzkratos on 2013-10-14
thank you wild man for your quick support ,dedication and patience to my ignorant and sometimes rude ways to ask as being impatient all in all thank you.


Now the good news thanks to the observation of unhooking the ethenet to usb adapter  while running the commands and just simply not having any wires attached the ethernet port works just fine and is fast enough.

the 1 command that did the trick was 

sudo rm /etc/udev/rules.d/70-persistent-net.rules

---

### Post by vzkratos on 2013-10-14
now i'm gonna run the 2 command from hadaka post #11 and see if the wifi works wish me luck guys

---

### Post by vzkratos on 2013-10-14
after second command ran this is what i got in terminal

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



no wifi yet gonna run 3 command now.

---

### Post by wildmanne39 on 2013-10-14
Those commands in Hadaka's post for wireless do not need an internet connection to work I do not believe, I believe the issue is that I missed the bcma driver being blacklisted.
Thanks

---

### Post by vzkratos on 2013-10-14
thanks wild man i just rebooted the system,and after the third command from hadaka i still can't get  wifi to work yet now i'm gonna run your commands on post #14 see what happens i got my fingers crossed lol.

---

### Post by wildmanne39 on 2013-10-14
I am sorry I just woke up from a nap when I got on here, the brcmsmac driver also needs removed from the blacklist file.
Thanks

---

### Post by vzkratos on 2013-10-14
i don't see bcma only i see it as  bcm43xx i'm not sure if that's the one you want me to blacklist.This is the whole thing that says on the document after i run you command please let me know which one i gotta fix or delete and then click save.

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by Hadaka on 2013-10-14
Wild Man is correct you need to get rid of..
blacklist bcma

either delete that line or put a "#" at the begining of that line
like this ->  #blacklist bcma 
(I saw it,even made a note of it and forgot to mention it..sorry)

---

### Post by wildmanne39 on 2013-10-14
Run the script again and lets see what it tells us, purging the wl driver may have unblacklisted those drivers.

---

### Post by vzkratos on 2013-10-14
ok this time i did not get a tar file i got this instead
sorry for the wait i got confused for a while

---

### Post by wildmanne39 on 2013-10-14
Looks like there may be a bug in the driver but I am to tired tonight to work on it maybe hadaka will be able to help tonight if not I will begin again tomorrow.

---

### Post by wildmanne39 on 2013-10-14
I would set your channel to 1 or 11 and set your encryption to wpa2 AES in the router.

---

### Post by Hadaka on 2013-10-14
Hi, thanks Wild Man
give this a try see if it helps..
please do..
```
sudo modprobe -rf brcmsmac
sudo modprobe -v brcmsmac
```
thanks.

---

### Post by vzkratos on 2013-10-14
> **Wild Man said:**
> I would set your channel to 1 or 11 and set your encryption to wpa2 AES in the router.

i'm not sure exactly how to do that and if i do that wouldn't that change my connections with my other computers and wifi enable devices on the house. just wondering thanks if you are tired i understand we will leave it for tomorrow thanks for such quick responses.

---

### Post by vzkratos on 2013-10-14
should i run this while hooked to the ethernet or should i unplug the wire of the ethernet.?
well i'm gonna run with the connection for now see what happens....

> **Hadaka said:**
> Hi, thanks Wild Man
give this a try see if it helps..
please do..
```
sudo modprobe -rf brcmsmac
sudo modprobe -v brcmsmac
```
thanks.

---

### Post by Hadaka on 2013-10-14
Hi, the other wifi devices should be fine..all they care about
is the correct SSID and password. They will adjust to a new channel and
differnt encryption. Wild Man is correct, even if you get your wireless working
linux..ubuntu is not fond of TKIP. Sooner or later you need to learn how to make
adjustments to settings in your router..soooo...you decide.
what type of router do you have..linksys,netgear???
thanks

---

### Post by vzkratos on 2013-10-14
hadaka thanks for  breaking down  what that means i assume is like a radio channel frecuency,some work better than others for tuning signals or something, i htought i was be messing with n.g or whatever speeds are out there for wifi,i'll give the name and model of my router i gotta check it on the mean time,something weird happend so i ran your commands the last ones you gave me rebooted the system no wifi yet i plug in the ethernet wire a few seconds later boom  my network shows up i click on connecte it connected i unplug the ethernet wire and i had signal for about 15 seconds after that the signal went away try to do the same thing but my network dissapear completly i just thought i'll let you know that weird fact.

---

### Post by vzkratos on 2013-10-15
what does that mean [COLOR=#000000].ubuntu is not fond of TKIP
again  i connected the ethernet the wifi show up unplug the data cable and wifi seems to have been stable and decently fast but that was after like 5 to 10 minutes though.

as for my router  is from at&t  they sent it to me 
at&t router details:
model number3801
pace      pace americas at&t u verse this router is the one that you can use to connect a tv box from att to get signal or channels 
now that i been with  the wifi for about 5 minutes ish the connection drooped and no more signal conclusion the wifi is not strong,stable,and constant sorry for the wait[/COLOR]

---

### Post by vzkratos on 2013-10-15
if the information above  about the at&t router is not enough  i think i can call att or go to their website and figure out more details about the router like the maker i think

---

### Post by Hadaka on 2013-10-15
Hi, some computers,depending on the bios settings,dont
allow wifi and ethernet to run at the same time. Sounds like
yours may be configured that way. TKIP is a signal/encryption
type..google it...google...ubuntu tkip router. If you are going to
be "messing about" with linux, its kinda important to extend and
gain a knowledge base on terms,commands,and general knowledge.
Not a day goes by i dont learn something new..thus far you are doing
GREAT !! The current TKIP setting "may" be what is slowing your connection
after some time. we shall see. More tomorrow..take a break !

---

### Post by vzkratos on 2013-10-15
thanks hadaka,you right we should leave it for tomorrow is getting late thanks for the help but the tkip you are talking about is some weird stuff for instance i get to be able to get to the wifi  only while hooked to ethernet,2 i take off the ethernet and a few 5 minutes later boof it goes away,3 before when i had this same computer but on 12.10 i ran a few commands that you and chili555  provided a guy with and next thing you know my computer was slowing down all other wifi devices in the house.

on a different area but related i have this laptop version but the one previous model is lenovo g770 and i have absolutley no problems with wifi or the ethenet port ridiculous i think.
but anyhow you managed to get the data port working that's a hell of a start we'll continue tomorrow just let me know what time works better for you so we can run most things right away thanks again good night.

---

### Post by varunendra on 2013-10-15
> **vzkratos said:**
> what does that mean .ubuntu is not fond of TKIP

From [http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access#Encryption_protocol](http://en.wikipedia.org/wiki/Wi-Fi_Protected_Access#Encryption_protocol) -
> **CCMP **
An AES-based encryption mechanism that is **stronger than TKIP**. Used by WPA2. Among informal names are "AES" and "AES-CCMP". According to the 802.11n specification, this encryption protocol must be used to achieve the fast 802.11n high bitrate schemes, though not all implementations enforce this.[24] **Otherwise, the data rate will not exceed 54 MBit/s**.

A detailed post I just made discussing something similar - [http://ubuntuforums.org/showthread.php?t=2180178&p=12817442#post12817442](http://ubuntuforums.org/showthread.php?t=2180178&p=12817442#post12817442)

As of now, make sure you have done what Wild Man suggested earlier. That is - change the encryption type to pure WPA2-PSK (AES) and it may further help getting better connection if you change the channel from 9 to 1 or 11. Both these changes are to be made in the router.

You may not need to do anything else other than above, but delete the existing connection and create a new one after making the changes in the router, just to be extra sure.

---

### Post by vzkratos on 2013-10-16
Thanks for explaining what that does and means i'll give a shot And see what happens
Thanks s again

---

### Post by vzkratos on 2013-11-06
i found the fix for ubuntu 13.04 for the wifi issue and the black screen after the grub screen on this thread.

[http://ubuntuforums.org/showthread.php?t=2183173&highlight=lenovo+g780](http://ubuntuforums.org/showthread.php?t=2183173&highlight=lenovo+g780)

i want to thank everyone who helped  me on this journey WILDMAN   for all his patience and time to help me with this,  HADAKA well you too between you and wildman helped me get the the ethernet port working ,   VARUNENDRA thanks for posting how to do log files or whatever they are thanks again and also thanks to MECHEVAR21 for taking care of the wifi and black screen all in all thank you all for helping i don't know what else to say but thank you again all of you.

---

