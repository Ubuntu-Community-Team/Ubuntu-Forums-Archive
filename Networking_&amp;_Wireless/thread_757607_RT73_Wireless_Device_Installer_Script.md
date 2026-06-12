---
title: "RT73 Wireless Device Installer Script"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by Kiefer Rodriguez on 2008-04-17
[I][B]Notice: As of Ubuntu 8.04, Most (If not all) RT73 based devices are supported out-of-the-box.
so version 2.0 will be the final release, with continued support- of course :).[/B][/I]

This script is intended to install devices using the Ralink rt73 chipset. 
If you have a different device, Head to [this thread]("http://ubuntuforums.org/showpost.php?p=3450169&postcount=1") (Thanks to wieman01).
If the script doesnt work, consider doing it yourself using [this awesome guide]("http://ubuntuforums.org/showthread.php?t=400236") by diepruis.

**Script Name:** rt73 Wireless Device Installer
**Language: **Python
**Distro:** 'Buntu Family (7.10 <)
**Script Version:** 1.1* BUILD 2*
**Script Author:** Kiefer Rodriguez
[COLOR=Blue][I]
**Announcement:** [/I][/COLOR][COLOR=Red]Version 2.0 will be released within the next few days, with a much nicer UI! :D[/COLOR]

**Changelog:**
[SIZE=1]    +0.1a:    Basic Script, no user input, System specific.
    +0.5:    User Input now accepted, System Independent.
    +0.5.5:    Log file functionality added for error checking.
    *0.5.6:    Temp file now writes correctly to blacklist.
    +1.0a:    Full functionality for self configuration at start-up (Essid, WEP, etc)
    +1.0:    Added FAQ, README and now includes a know-to-work driver.
    *1.1:    Fixed the 'iface' error where wlan0 was being specefied instead of the user specified device.
        Corrected error checking, now actually aborts on fatal error.
        Corrected a few minor bugs.    
        Corrected the '/usr/src/rt73-cvs-??????????/' syntax error.
    *1.1 BUILD 2: Fixed the 'apttitude'/'apt-get' cd-rom bug[/SIZE]
    


**Todo:**
[SIZE=1]+ Add stderr output on error after piping output to temp (so errors are viewed, but not normal output).
+ Add a GUI-Front-End (Low priority).
* Fix bug where 'install make' sometimes returns an error.
+ Add colored output
+ Add docstrings and further commenting.[/SIZE]

**Script Description:**
This is a simple Python script that will automatically install any wireless device using the RT73 chipset from RALINK.
This includes devices from the DWL-G122 device family. 

**Instructions:**
Download the tarball (below), extract the folder contained in it, open up a command line, move to the directory you extracted it in, then type:

```
sudo python install_rt73_drivers.py
```and follow the prompts.

[COLOR=Red]**Important:** You *must* have downloaded the entire archive, not just the script, it will *not* work on its own!.[/COLOR]

***Which wireless devices use the rt73 Ralink chipset?***
[I]
* Asus WL-167g     
* Sitecom WL113 v1-002             
* GW-US54HP     
* D-Link DWL-G122
* Digitus DN-7003GR (VPR 1.0) 
* Belkin F5D7050 Ver 3 
* Hawking HWUG1     
* Linksys WUSB54GR[/I]

Note: There may be others not listed here.

[SIZE=1]source: [http://rt2x00.serialmonkey.com/wiki/index.php/Hardware#rt73](http://rt2x00.serialmonkey.com/wiki/index.php/Hardware#rt73)[/SIZE]


**Help:**
See the FAQ & README.

The Script (Will not work on its own, If you want to use it see the 'Important' note above):
```
#!usr/bin/python                        

# Version :     1.1 BUILD 2 [See Changelog.]
# Author:     Kiefer Rodriguez.
#        Thanks to diepruis for a great guide on the serialmonkey driver installation!
# Contact:     E-mail= [kiefer[dot]rodriguez[at]gmail[dot]com], 
#        IRC= kiefer08 (usually in ##linux on irc.freenode.net)
# Script:     'Ralink rt73: Driver Installer - by Kiefer Rodriguez.' -- Installs and configures any device that uses the rt73 chipset.


print "Ralink rt73: Driver Installer - by Kiefer Rodriguez."
# Import 'os' so we can run os.system(<command>) later, very important module.
try:
    import os
except ImportError:
    print "Error: ImportError: Couldnt import the python module 'os'. Aborting Script."
    raise SystemExit
# Initiate the log file for troubleshooting.
log = file("rt73-logfile", 'w')
log.write("Log File Initiated.\n")
log.close()
log = file("rt73-logfile", 'r')

# Get some Info from the user for future use.
try:
    ESSID = str(raw_input("Please enter your intended AP name (e.g. 'OfficeWireless' or 'Our_Internet') : "))
    WEP_KEY = str(raw_input("Please enter the WEP key for " + ESSID + " (or type 'off' if there isnt one, ASCII keys need to be prefixed with 's:' without the quotes and without any spaces.) : "))
    pm = str(raw_input("Please enter your package manager (e.g. 'apt-get' or 'aptitude') : "))
    answer1 = str(raw_input("Do you currently have an active internet connection? [y/n] : "))
    iface = str(raw_input("Enter the interface name for the device to activate (Most likely 'wlan0') : "))
except:
    print "Error: BadInput: Aborting Script."    # Better now then later. :\
    raise SystemExit

print "*    Copying rt73 module .tar to /usr/src.."
os.system("sudo cp rt73-cvs-daily.tar.gz /usr/src")
print "*    Unpacking rt73 module in /usr/src.."
os.system("sudo tar -xvzf /usr/src/rt73-cvs-daily.tar.gz > rt73-logfile")

if answer1 == 'n':        
    __0xFFFFa__ = raw_input("Please insert your [Edu/U/Ku]buntu CD, wait 10 seconds then press enter.")
    print "%    Gathering required header files from CD, this may take a while.."
    os.system("sudo apt-cdrom add")
    print "*    Added CD-Rom to sources list, now updating list.."
    os.system("sudo aptitude update")
    print "*    Installing headers.."
    os.system("sudo aptitude install build-essential linux-headers-`uname -r`")
                
else:
    print "*    Installing headers.."
    os.system("sudo " + pm + " install build-essential linux-headers-`uname -r`")
print "*    Compiling rt73 module [1/2].."
try:
    os.system("cd /usr/src/rt73-cvs-2008??????/Module") # Sometimes [2/2] Doesnt 'cd' for some reason.
except:
    os.system("cd /usr/src/rt73-cvs-2008*/Module")
print "*    Compiling rt73 module [2/2].."
os.system("cd /usr/src/rt73-cvs-????*/Module && sudo make > /tmp/rt73-logfile")
warning = str(raw_input("*    Did you just recieve a 'WARNING' message regarding file size? [y/n] : "))
if warning == 'y':
    print "*    Fixing the size issue [known 'bug'].."
    os.system("sudo strip -S rt73.ko > rt73-logfile")
print "*    Installing module.."
os.system("sudo make install > rt73-logfile")
print "*    Bringing down wireless device.."
os.system("sudo ifconfig  " + iface + "  down")
print "*    Removing obsolete modules.."
os.system("sudo modprobe -r rt73usb > rt73-logfile")
# os.system("sudo modprobe -r rt2570 > rt73-logfile") Seems to cause freezing sometimes. Uncomment at your own risk.
os.system("sudo modprobe -r rt2500usb > rt73-logfile")
os.system("sudo modprobe -r rt2x00lib > rt73-logfile")

print "*    Making a backup of /etc/modprobe.d/blacklist to your Home dir. just in-case.."
os.system("sudo cp /etc/modprobe.d/blacklist ~/BACKUP-OF-BLACKLIST")
os.system("sudo cp /etc/modprobe.d/blacklist ~/rt73-blacklist.temp")
print "*    Opening /etc/modprobe.d/blacklist.."
modprobe = file("rt73-blacklist.temp", 'a')
print "*    Writing to /etc/modprobe.d/blacklist.."
modprobe.write("#ADDED BY DWL SCRIPT:\nblacklist rt2570\nblacklist rt73usb\nblacklist rt2500usb\nblacklist rt2x00lib\n#END.")
os.system("sudo mv rt73-blacklist.temp /etc/modprobe.d/blacklist") # Experimental - May be replaced in next version.
print "*    Closing blacklist.."
modprobe.close()
print "*    Deleting temp file[s].."
os.system("sudo rm -rf rt73-blacklist.temp")
print "*    Making sure rt73 installed correctly.."
os.system("sudo modprobe -v rt73 > rt73-logfile")
print "*    Bringing up device.."
os.system("sudo ifconfig " + iface + " up")
print "*    Configuring new device.."
os.system("sudo iwconfig " + iface + " essid " + ESSID)
os.system("sudo iwconfig " + iface + " key " + WEP_KEY)
print "*    Running dhclient.."
os.system("sudo dhclient " + iface + " > rt73-logfile")
print"*        Script complete, You should now be able to connect, if not - Read the FAQ."

# This script is licensed under the GNU public license, You are free to edit, modify and distribute this script as you wish, as long as the original authors name ('Kiefer Rodriguez') remains. =)
```

---

### Post by spartan777 on 2008-04-27
this is what I get when i run it. i tell the script that I have NO active connection, but it still tries to connect to a bunch of servers anyways. btw, i haven't upgraded to 8.04 yet.


[IMG]http://farm4.static.flickr.com/3247/2445488236_1b594ea167_b_d.jpg[/IMG]

---

### Post by Kiefer Rodriguez on 2008-04-27
> **spartan777 said:**
> this is what I get when i run it. i tell the script that I have NO active connection, but it still tries to connect to a bunch of servers anyways. btw, i haven't upgraded to 8.04 yet.


spartan777,
Firstly, thanks for alerting me to this bug,
But I'm afraid you are not the first to encounter this little bug;
Someone had a similar problem (well not 'similar', the exact same :p) and informed me,
I made some changes and such is how version 1.1 BUILD 2 was born (with emphasis on 'Build 2').

I am under the impression (from myself) that doing one/both of the following will fix your issue;

> Double check you have 'version 1.1 BUILD 2' of the script, and not an earlier version.
> Double check you are inserting your 'buntu CD-Rom and waiting 10 seconds when asked to.
> If neither of the above yield results, then open the script in your text editor of choice and make the following changes via means of 'Find and Replace':
```
Find 'os.system("sudo " + pm + " update")' and Replace with:
'os.system("sudo aptitude update")'
Find 'os.system("sudo " + pm + " install build-essential linux-headers-`uname -r`") and Replace with:
'os.system("sudo aptitude install build-essential linux-headers-`uname -r`")'
```If even after the above you are unsuccessful, I suggest using the guide linked to in my original post.

Thanks,
Kiefer

Note: In future could you please post the output of the CLI as a text, not an image.

---

### Post by spartan777 on 2008-04-27
i threw the new 8.04 in, and to my utter horror, my wireless worked. it just worked. i've been trying to get my wireless to work for the last 1.5 years.

thanks for the help Kiefer, but it looks like i won't need you're script anymore. btw, i was indeed using rev 2 of your script when I posted my first post. also, I tried the 3 things you suggested to troubleshoot, and nothing helped. in the 'find/replace' step, i couldn't find the first phrase anywhere.

```
os.system("sudo " + pm + " update")
```

---

### Post by Kiefer Rodriguez on 2008-04-28
> **spartan777 said:**
> i threw the new 8.04 in, and to my utter horror, my wireless worked. it just worked. i've been trying to get my wireless to work for the last 1.5 years.

thanks for the help Kiefer, but it looks like i won't need you're script anymore. btw, i was indeed using rev 2 of your script when I posted my first post. also, I tried the 3 things you suggested to troubleshoot, and nothing helped. in the 'find/replace' step, i couldn't find the first phrase anywhere.

```
os.system("sudo " + pm + " update")
```

Hrmm, Well enjoy your wireless, but im still a tad confused about the bug, the code in question that was being ran when the bug was encountered was:

```
os.system("sudo apt-cdrom add")
os.system("sudo aptitude update")
os.system("sudo aptitude install build-essential linux-headers-`uname -r`")
```Which to put it simply runs the argument supplied to the method os.system() under the CLI, which when run manually works perfectly (meaning it doesnt try to use the internet).

Oh well, the solution provided when the bug originally rose fixed it, but in your case it seemed to not matter, anyhow - Thanks for letting me know :)

~Kiefer

---

### Post by dfour on 2008-04-28
I noticed in another thread:
> 
Re: Desktop Hardware Incompatibility List.

Linksys Ralink WUSB54GR USB Wireless Card
Rt73 Based
Quite tempermental, work for an hour, then stop. Requires you to unplug the card, then plug it back it for it to carry on working.

Gutsy Gibbon.

I'm using an Edimax 7318USG (RT73) and getting this problem on Hardy 8.04.  It worked great for the first few hours, but now all of a sudden it is spotty and not working well at all.  I was hoping it would fix itself, but it looks like i'll be trying this script tonight.

---

### Post by Kiefer Rodriguez on 2008-04-28
> **dfour said:**
> I noticed in another thread:

I'm using an Edimax 7318USG (RT73) and getting this problem on Hardy 8.04.  It worked great for the first few hours, but now all of a sudden it is spotty and not working well at all.  I was hoping it would fix itself, but it looks like i'll be trying this script tonight.

Well the script hasnt been tested on Hardy (As its supposed to work out-of-the-box), but the only difference the script will make is that it installs the serialmonkey driver, which could fix the issue your facing, let me know.

~Kiefer

---

### Post by Ezetreal on 2008-04-30
First, thanks for the script, very nice of you to think of all us newbies.

Now, I seem to have a problem. After using your script (running Hardy, fresh install), my wireless card completely disappeared. I used it in the first place because my connection while using the wireless was slow and eventually just stopped working after a few minutes.

the rt73-logfile is empty, however I will attach my lspci, lsmod and ifconfig files from before I used the script, as well as the failed installation process copied from the terminal.

Any help would be greatly appreciated.

Thanks

---

### Post by Kiefer Rodriguez on 2008-04-30
> **Ezetreal said:**
> First, thanks for the script, very nice of you to think of all us newbies.

Now, I seem to have a problem. After using your script (running Hardy, fresh install), my wireless card completely disappeared. I used it in the first place because my connection while using the wireless was slow and eventually just stopped working after a few minutes.

the rt73-logfile is empty, however I will attach my lspci, lsmod and ifconfig files from before I used the script, as well as the failed installation process copied from the terminal.

Any help would be greatly appreciated.

Thanks

Ezetreal,
Thanks for letting me know, The script has never been tested on Hardy (as noted in the main post) but this problem should be easily fixed- the first thing I need you to do is check '/usr/src/' for a folder named 'rt73-cvs-<a bunch of numbers>' if you cant see it there, then i need you to copy the contents of the tarball contained within the folder 'install rt73' folder (that you extracted when you download the script) it should be named 'rt73-cvs-daily.tar.gz', extract its contents to /usr/src/ then run the script again.
If that fails to work then your best option is to use the guide linked to in my main post ('if the script doesnt work consider doing it yourself..').

Thanks, and best of luck; :)

Kiefer

---

### Post by Ezetreal on 2008-04-30
Thanks for the quick reply.

in /usr/src i could only find the still archived rt73-cvs-daily.tar.gz so I copied the contents of it from the folder it was actually extracted to which was on my desktop in the install_rt73 folder to /usr/src and ran the Install_rt73_drivers.py (from the folder on my desktop). This time around, the compiling of rt73 (1/2) and (2/2) went fine. The problem came right after that when it said installing module then "no rules for building 'install´". No interface was found and i was back where i started.

Actually the first time i used the script i could see the interface in iwconfig (it was wlan0) but now there is no wireless interface.

If there is nothing else you can help me with, is it at least possible to undo everything your script did so that i can rebuild it manually as you suggested ?

Thanks for your help.

---

### Post by chrisdudeperson on 2008-04-30
i've done the install and it worked

but i cant seem to find any networks?


thanks
chris

---

### Post by Kiefer Rodriguez on 2008-04-30
> **Ezetreal said:**
> Thanks for the quick reply.

in /usr/src i could only find the still archived rt73-cvs-daily.tar.gz so I copied the contents of it from the folder it was actually extracted to which was on my desktop in the install_rt73 folder to /usr/src and ran the Install_rt73_drivers.py (from the folder on my desktop). This time around, the compiling of rt73 (1/2) and (2/2) went fine. The problem came right after that when it said installing module then "no rules for building 'install´". No interface was found and i was back where i started.

Actually the first time i used the script i could see the interface in iwconfig (it was wlan0) but now there is no wireless interface.

If there is nothing else you can help me with, is it at least possible to undo everything your script did so that i can rebuild it manually as you suggested ?

Thanks for your help.

If you wish to rebuild it manually, theres no need to undo any operations the script did, just start at step 1 in the guide and there shouldnt be any issues, as for the 'no rule to make install' error, I got that a few times during beta testing - it seemed to happen randomly, I could never determine a cause for it other than 'make' didnt fully execute, but theres no need to worry, I would suggest just using the guide, to save yourself time :p
Sorry the script didnt work for you, Im going to have to look into why 'make' is acting up. Best of luck-

Kiefer

---

### Post by Kiefer Rodriguez on 2008-04-30
> **chrisdudeperson said:**
> i've done the install and it worked

but i cant seem to find any networks?


thanks
chris

Chris,
The obvious question - Are you sure there are networks in the area to find?
Can you post the output of the following commands?
```
iwconfig
sudo iwlist wlan0 scan
ifconfig -a
```

Thanks, Kiefer

---

### Post by Ezetreal on 2008-05-01
I will attempt to do it manually then.

Thanks again for the script and the help !

PS: Excellent Avatar ! You wouldn't happen to have Donatello ? :)


Attempted the manual installation, i get an:  

 SIOCSIFFLAGS: Invalid argument

when typing sudo ifconfig wlan0 up

I hope this helps with your debugging. It seems to happen randomly to some people and others not, so it might be the problem your script is encountering.

---

### Post by Colorado on 2008-05-04
I bought the "Hama Wireless LAN USB 2.0 Stick 54 Mbps" overseas and it seems to also use this driver.  I intend to test your script tonight and see for sure.

Many Thanks!


Colorado

---

### Post by jcortes on 2008-05-12
Are the drivers included in this fix patched and work with Aircrack suite?

---

### Post by Kiefer Rodriguez on 2008-05-12
> **jcortes said:**
> Are the drivers included in this fix patched and work with Aircrack suite?


Cortes,
Im not sure regarding support for the Aircrack Suite (A suite which I highly doubt your going to use for a security audit..) but please check the SerialMonkey website regarding the RT73-Chipset driver.
It should be noted the driver included with the tarball was a daily release < Feb2008.
Feel free to post any problems you encounter here. thanks-

Kiefer.

---

### Post by jcortes on 2008-05-12
I actually do security audits for company's in a complex. I explain to them the possible threats that wireless could cause to there company and if they agree I show them a demonstration. So don't be so quick to judge I'm not just another teenager trying to get his friends Myspace account password. 

Anyways...

I was unable to get it to work for me I chose Rausb0 to be my device interface during the installation but still no luck after a reboot. No errors either during the installation.

Also if I slip the patched drivers in place of the drivers you have included would that work or have you altered the C code of the driver itself.

---

### Post by Kiefer Rodriguez on 2008-05-13
> **jcortes said:**
> I actually do security audits for company's in a complex. I explain to them the possible threats that wireless could cause to there company and if they agree I show them a demonstration. So don't be so quick to judge I'm not just another teenager trying to get his friends Myspace account password. 

Anyways...

I was unable to get it to work for me I chose Rausb0 to be my device interface during the installation but still no luck after a reboot. No errors either during the installation.

Also if I slip the patched drivers in place of the drivers you have included would that work or have you altered the C code of the driver itself.

JCortes,
Do accept my apologies, you must understand in all the years I've spent assisting others, very few people wish to use the Aircrack Suite for security audits, like you said, most of them are teenagers wanting their friends MySpace password.
As for your problem, try running the script again, but instead of 'rausb0' specify 'wlan0' (or 'wlan1' if you already have 'wlan0' etc) and let me know how it goes :).
As for replacing the driver, I dont suggest it - the script looks for certain files and directories in relation to the driver thats included.

Kiefer

---

### Post by jcortes on 2008-05-14
I see, thanks for the replay I will post back when I get a chance to try this. 

No hard feelings either I can not express to you how frustrating it is to be asked 100x a day if I can hack an email account or Myspace account when all I'm trying to do is express the security flaws in WEP. I do understand where you are coming from.

---

### Post by Kiefer Rodriguez on 2008-05-20
[jcortes]("http://ubuntuforums.org/member.php?u=577230"),
Today I took the time to test the aircrack-ng suite I managed to pick up enough IV packets to crack my own 128 WEP key (Which usually uses WPA), But I've read elsewhere that the RT73 chipset doesnt support the Aircrack-ng suite, So my advice is to give it a try- It may or may not work,
I wish you the best of luck with your work-

Kiefer.

---

### Post by popo06 on 2008-06-06
Please I am a new member here, I can't download your script named "Install_rt73_drivers_script_(v1.1_BUILD2).tar.gz" from ubuntu server, can you please send me it on my email adress if you have got enough time?
[email]fredericviera(at)hotmail.com[/email]
Thank you very much, and congratulation for your work!
Frédéric

---

### Post by bmwman on 2008-06-10
Hello, I've been having problems with my Belkin USB adapter for a while. It does "work" out of the box with Ubuntu Hardy 8.04 but it connects at only 1mbps and sometimes the whole system freezes. I tried using ndiswrapper to load the windows driver and blacklist the alternative but it was still showing as loaded so dunno what else to do. I would definetly try this script when I get home tonight. My concern is that it has listed Belkin F5D7050 Ver3 and mine is actually Ver.2. Is is still gonna work or I need to make some changes?  

Thanks.

---

### Post by spartan777 on 2008-06-22
bmwman;

I've been using the rt73usb support out of the box for the last few weeks, and it shows that my connection is only 1Mb/s too. my connection just crawls. would using the latest version of this script install a newer version of the rt73sub driver than the one built into the kernel?

sometimes my connection fails too, but i think its a hardware issue with my wusb54gr since the same thing happens in windows, except in windows, it can be fixed by doing the "Repair Connection," which basically stops the device, the initializes it over, and everything is working again. there isn't anything like this in the nm gui to do this. does anyone know of the command to do this?

EDIT**

i checked the daily tar from serialmonkey, and their latest rt73usb driver is from june, and is several kb larger. could you update the script to support the newer driver, or could we just drop the new driver into the folder with the script and it work fine?

---

### Post by Rick Churchill on 2008-06-22
> **Kiefer Rodriguez said:**
> [jcortes]("http://ubuntuforums.org/member.php?u=577230"),
Today I took the time to test the aircrack-ng suite I managed to pick up enough IV packets to crack my own 128 WEP key (Which usually uses WPA), But I've read elsewhere that the RT73 chipset doesnt support the Aircrack-ng suite, So my advice is to give it a try- It may or may not work,
I wish you the best of luck with your work-

Kiefer.
I have had nothing but problems with my Linksys WUSB54GC with Ubuntu but know for a fact that if you use Backtrack3 on a USB stick that the driver is perfect.

---

### Post by Kiefer Rodriguez on 2008-07-06
> **spartan777 said:**
> bmwman;

I've been using the rt73usb support out of the box for the last few weeks, and it shows that my connection is only 1Mb/s too. my connection just crawls. would using the latest version of this script install a newer version of the rt73sub driver than the one built into the kernel?

sometimes my connection fails too, but i think its a hardware issue with my wusb54gr since the same thing happens in windows, except in windows, it can be fixed by doing the "Repair Connection," which basically stops the device, the initializes it over, and everything is working again. there isn't anything like this in the nm gui to do this. does anyone know of the command to do this?

EDIT**

i checked the daily tar from serialmonkey, and their latest rt73usb driver is from june, and is several kb larger. could you update the script to support the newer driver, or could we just drop the new driver into the folder with the script and it work fine?

spartan777,
I greatly appologise for the long delay in my reply, I was hospitilized dues to a car accident recently and am only just beggining to recover.
As for using a new driver from the serialmonkey website, my advice is this, download the new driver, rename it to the one currently included with the script, open the script in a text editor and read through to make sure I havnt referenced the filename explicitly (I dont think I have, but I cant check right now, as I dont have my laptop) If I have, just change it to refer to the new driver files.
Best of luck,

Kiefer

---

### Post by robokiller on 2008-07-23
> **bmwman said:**
> Hello, I've been having problems with my Belkin USB adapter for a while. It does "work" out of the box with Ubuntu Hardy 8.04 but it connects at only 1mbps and sometimes the whole system freezes. I tried using ndiswrapper to load the windows driver and blacklist the alternative but it was still showing as loaded so dunno what else to do. I would definetly try this script when I get home tonight. My concern is that it has listed Belkin F5D7050 Ver3 and mine is actually Ver.2. Is is still gonna work or I need to make some changes?  

Thanks.

Hey bmwman and anyone else with this problem.

I am not sure if it is the same problem or not but it is worth a try anyway.
I used to have a problem where while there was lots of network activity (even just searching medium - large sized websites) would make my computer really slow and almost unresponsive at times. just like really choppy and laggy and sometimes experience lower than usual speeds.

I fixed this by manually setting my adapter to 11Mb/s rather than 54Mb/s. i know what your thinking.. "how is that supposed to INCREASE speeds?" and im not quite sure myself. :P

after i changed it i had my full interent bandwidth and no lag what so ever.

to change this is fairly simple, here are the steps:

step 1 - set it to fixed bitrate mode instead of auto.
```
sudo iwconfig wlan0 rate fixed
```

step 2 - set the bitrate to 11mb/s

```
sudo iwconfig wlan0 rate 11M
```

step 3 - restart the device

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```

now check to see if it worked by doing the 'iwconfig' command and it should read "Bit Rate=11Mb/s" under wlan0

Now reconnect to the network using the network manager and see if your problem goes away.

Hope it helped you.

---

