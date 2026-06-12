---
title: "[SOLVED] AR5007 Atheros Madwifi Hardy 8.04 32BIT I386 INSTALL INSTRUCTIONS STEP BY ST"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by nicedude on 2008-05-16
Bye

---

### Post by silberj on 2008-05-16
This is an awesome step by step you compiled. I have looked and searched far and wide trying to resolve this and this is the only thing that actually worked, and works WELL! Thanks again!

---

### Post by packman1234 on 2008-05-16
[B]Wow!!
Much better but still having some problems..
It is showing my network in WICD but when i click connect, it tries but cant do it.In Preferences the WPA Supplicant Driver is WEXT and the wireless interface is ath0-which I believe is all cool. Cant connect to the internet though....
The instructions were very good and seemed to work ok-but I get a lot of unable to resolve host bob-laptop errors when I run sudo. The commands do work though. The only one that gave me the error was sudo modprobe ath_pci.
Thanks so much for getting me this far!! Any help getting me connected will be appreciated!

Bob[/B]:):):)

---

### Post by packman1234 on 2008-05-16
Now everything is very slow and WICD does not work.. And I get a box saying There was an error starting the Gnome Settings Daemon!

Bob

---

### Post by nicedude on 2008-05-16
Heres some proof that this works as I will post 2 speed test screenshots one using Wifi and one using Wired internet. My connection is 6MB DSL and the speeds I achieve here are the best it gets for me. If you look at my screen shots you can see that the first one is on my wired interface & the second is on my wireless interface ( I made arrows that point at my panel monitors showing which is in use ). The wifi in question is using 128bit WEP for this test session and this seems to have zero effect on performance since both speed tests were identical ( wireless did lose 20kb a sec out of 6500 so thats a performance loss of 1 third of 1 percent which is within statistical difference and irrelevant ). So just look at my screenshots and see for yourself that my wifi works just fine using my guide above :-) - Furthur more notice the WICD icon on my toolbar as this is what is accomplishing my wifi connection as well as my wired when I connect it. 

The problem my guide trys to resolve mainly is to just get rid of all the madwifi drivers that come with Hardy by default with the restricted driver manager since they are the wrong ones for your card. Also if you have this WIFI chipset by Atheros you are lucky not cursed as it is not "GARBAGE" far from it as its one of the best currently available for full usage of WIFI spectrum utilities, It also has one of the highest scanning speeds for use with kismet or other wireless network sniffing tools and allows setting for all modes of operation ( Just try & see if crappy Ndiswrapper allows that ). 

Kismet by the way is one of the most awesome utilities I have ever had the pleasure to use in my life as it will detect & map all wireless networks in range of your device and supports using with GPS & works with Festival to audibly speak new network information to you as it is detected, so unless you work at the CIA you won't be finding any better sneaky wifi spy utilities here on planet earth :-) - If anyone who after using this guide needs some kismet install & usage help PM me about that as well and I can help give you some advice. On a simple drive on the highway recently my kismet found and identified 700+ wireless networks driving one highway through a large city :-)

Please don't just get mad and rant about your hardware when there are working solutions and you can't seem to implement them. This will only misleads others into thinking they own junk when actually they own a Mercedes Benz and just need to be given the keys. Sorry if anyone trying this has difficulty but I see no reason for it. Your situation should be no different than mine since I am having you remove all the system components that could cause problems with your Atheros chipset. If anyone has trouble I will help you as much as I can if you just PM me with relevant info of your complications. 

Here are the screenshots for proof - first one is wired second one is wireless

---

### Post by nicedude on 2008-05-17
To anyone that uses Wicd ( Or any other network manager for that matter ) please note to use encryption and connect you must go to the advanced settings for your network connection name you create for your network router or gateway & enter the type of encryption WPA - WEP & then you must also enter your key for decryption as you won't be connecting without the key as that is how WEP & WPA protect you. Not allowing login without a key is the whole point of how this type of radio signal security works in the first place, so if without the key entered properly you can't connect then that just means it is secure :-) . Now enter your key so you can actually decrypt & use it though.

---

### Post by packman1234 on 2008-05-17
Nicedude knows what he is talking about and he is willing to help!!
I rant because of all the hours I spent working on the wireless and it is indeed frustrating. Mine is working perfectly now thanks to his advice-I spent 20 hours before his post popped up.

Thanks again for your time---Now--I installed kismet and need a few pointers in getting it up and working.(when you have the time)

Bob

---

### Post by nicedude on 2008-05-18
I was asked by someone here how to configure kismet server, So I am adding this post to give you all the commands you need to configure it and launch it with your Atheros AR5007 wifi chipset and the command to go back to normal wifi.

*** This is only info for Atheros Wireless cards using the madwifi driver!!

-= STEP 1 =-

"Editing you kismet.conf file"

you need to make some changes to your kismet configuration file named kismet.conf to allow it to work with your adapter and driver. At a minimum you will need to make the following change. There are many more things you can do in this file if you want or need to, but the following is mandatory for it to work.

This will launch a text editor and load the file for editing
sudo gedit /etc/kismet/kismet.conf

Change the source= line to the following
source=madwifi_ag,wifi0,madwifi

-= STEP 2 =-

"Getting what you need and executing the setup commands & launching kismet"

you need to configure your interface for kismet use with some commands and have the madwifi-tools package from the repositories. And you need kismet as well of course but I will assume you do, but if not get it now from the repositories.

Here is the command to install madwifi tools if you don't have them already

sudo apt-get install madwifi-tools

You will also need Aircrack as it contains a command I use to launch the server. So heres the install command for that.

sudo apt-get install aircrack-ng

And here is the sequence of commands to configure your Atheros AR5007 to correctly implement a kismet server session. While there are other variables that can be passed in these commands this will build a kismet server session in Monitor mode that will not transmit anything and only receive data. This is the mode of operation for a kismet sniffing session.

Just paste each one of these one at a time going down the list into a terminal window.

sudo wlanconfig ath0 destroy
sudo ifconfig wifi0 down
sudo airmon-ng start wifi0
sudo kismet_server --daemonize
sudo kismet_client

You should now be in a proper kismet client session and you will need to check out the key shortcuts for different commands in kismet to see what does what. Have fun with this and be responsible.

-= STEP 3 =- 

"Stopping the kismet server when done and reverting to normal"

Once you are done with kismet server session you should close the kismet client window and then enter the following command into a terminal to stop the kismet server daemon

killall -I kismet_server

This will stop all instances of the kismet server daemon

Then to restart your network interfaces like from a fresh boot you can use the following command. this will let you use your wifi for internet access again.

sudo /etc/init.d/networking restart

Hope this helps you guys get the most use out of your AR5007 :-)

---

### Post by BETELGEUSE58 on 2008-05-18
Cannot follow guide.
Step four 404 error. Not found.
Damn.

---

### Post by BETELGEUSE58 on 2008-05-18
I think maybe the 1st post step four link is meant to be
[http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz)

---

### Post by nicedude on 2008-05-18
Thanks to BETELGEUSE58 for finding the bad link. I guess I goofed that link up when writing this guide sorry it has now been ammended and will work. Please everyone who uses this guide post your results here or PM me so I can know about any other issues or just that it helped some people in general.

Good Luck with your AR5007's all

nicedude

---

### Post by Farivan on 2008-05-18
Hi Nicedude, 

Thank you so much for posting this information - I've finally got my wireless working. 

I'm an absolute new-comer to Linux, and wasn't too sure that I'd be able to do something like this - but the guide is very easy to follow. Thanks.

John

As a side note: can anybody send me details on how to install the Nvidia driver? I really don't know how to do it as I keep getting a message saying I have to close the "x-server". I have no idea what this means!

---

### Post by nicedude on 2008-05-18
Hey all AR5007 owners I have been asked by someone who used my guide for a kismet launching script. Until today I had one but it was kinda not 100% so I worked on it this afternoon. I now have fixed it so it is 100% and I made a 100% working script to return your atheros card back to managed mode in a blink of the eye so you can go back to surfing without need to reboot or type a bunch of commands. I now will share these scripts with you guys here and hope you enjoy my work :-)

First some info on how to use a script in general, A script is just a text file that contains commands just the same as you would type at the command line. The only thing you need to do with my scripts to make them work for you is to right click on each file after you download them to your desktop and select properties at the very bottom -then-> click the permissions tab -then-> once in permissions click on the boxes that say executable to make the script able to run then close the window. At this point you should be able to double click on the script and when asked choose run. If that doesn't work then you either need to execute it from a command line ( since I have spaces in my names enclose with "" ) or install nautilus scripts package from the repositories and copy the two scripts to your nautilus scripts folder, I will include the nautilus scripts install command and the location of where your nautilus scripts folder should be located after installation so all you need to do is use nautilus and cut and paste the scripts to that folder. Once the nautilus scripts software is installed and my scripts ( or any other scripts ) are copied to the nautilus scripts directory you can access and use them with a simple right click and look for the new choice "scripts". 

Software needed to run my kismet launching script - make sure these are installed before trying to use
madwifi-tools
aircrack-ng
gksu
kismet

Please note the file kismet.conf must be configured as well for use by at a minimum changing the line below
source= line must be changed -to- "source=madwifi_ag,wifi0,madwifi" without quotes for kismet to work with your Atheros card

Command to edit the kismet configuration file
sudo gedit /etc/kismet/kismet.conf

Also to close the kismet client window this will launch you must use the shift+Q command inside kismet 

------------------------------------------------------------------------------------
This section is only needed if you want to try nautilus scripts manager
It is not needed to use my scripts it just makes them even more handy

Command to install nautilus scripts
sudo apt-get install nautilus-script-manager

Directory where you place scripts
/home/"YourUserName"/.gnome2/nautilus-scripts

Just copy them into there to have them at your finger tips :-)

------------------------------------------------------------------------------------

I hope this info and my scripts help everyone to have a more powerful system that is easy to use as well.

Good luck with this and if anyone needs further instruction PM me and I will try to help. Please post your results of using my scripts here so I will know it is getting some use.

nicedude

---

### Post by Pooka2132 on 2008-05-19
Worked great for my now 32 bit install. Thanx much!

Pooka

---

### Post by tsaverette on 2008-05-20
Nicedude can you suggest a fix for Atheros 5006x (I think) or chip called 5413. Any help appreciated.

---

### Post by williamson389 on 2008-05-20
sorry, total noob question:  how can i tell if my version is 32 or 64 bit?  i think it is probably 64 because i have an amd turion 64.  if it is 64bit, am i out of luck for wireless internet?

---

### Post by nicedude on 2008-05-21
To tsaverette you should check that you actually have a AR5006 as Ubuntu wrongly ID's my AR5007 or AR242x depending on Ubuntu version not as a AR5006 so don't trust lspci entirely heres the relevant line from mine

05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

As you can see it doesn't say AR5007 and in Gutsy it said AR5006 so Ubuntu lspci has never correctly reported my chipset, I figured out what I had via my manufacturers specs which were not easy to find either by the way as most PC makers seem to prefer to keep us in the dark and just say wireless network adapter included or similar tripe but if you dig you can find out what you have for sure. If after finding out you would PM me with your chipset I will try to help you get it working.

_______________________________________________________________________

To williamson ( And anyone else with this question ) if you have a 64bit processor that just means you can use the 64bit version of Ubuntu but the 32bit version will work as well ( Check the one you downloaded as the ISO file you got will contain the version look for 64 or 32 in the ISO name ). The only difference is that 32bit wont use your CPU's advanced multicore features as well as the 64bit but you should not see any difference in operation with the 32bit and also hardware in general has better 32bit Linux driver support as more people are using 32bit and as such it has more chance of having drivers for any given piece of hardware. Furthermore there are no madwifi patched AR5007 drivers available for 64bit as I write this so if you plan to use 64bit Ubuntu you will need to use another driver solution than the one I am giving here ( although as I stated you shouldn't see any performance problems with 32bit as I can open 4 movies at once and place one on each side of my compiz 3D cube and spin it around without any stutter so I don't see any need for the 64bit ) 

The one situation I know of that 64bit would give increased performance is maybe when using multiple CPU intensive software at once or when using your PC to do sophisticated mathematical computations so unless that applies to you I would recommend using the 32bit for driver & software availability reasons.

Just if you do follow my guide please follow it to the letter to achieve success as there is no room for skipping anything. And also read what removing the restricted driver manager will require of you to use other things it might now be controlling the drivers for.

I hope this helps everyone wrap their heads around this problem and understand your options you have. If anyone needs some extra help please PM me by clicking my name and selecting "send private message" and I will try to help you out.

nicedude

---

### Post by tsaverette on 2008-05-21
Hey nicedude, My (desktop) computer is a HP Pavilion Media Center PC model m7760n .
It came with MS Vista. I bought it new about 15 months ago.
Like you said the information it reports is very generic (you said tripe - I say it louder). So I called HP tech support to ask exactly what is the wireless thingy contained in this computer. He told me I have the Intel 945G Express Chipset which in turn has integrated everything. And to go to intel.com to find out more. He even went there to see himself if he could find out more. I can't find much at intel.com that is easily intelligible to me regarding the wireless designation so maybe 945G Express is the designation I need to go with.
So, I don't know if Atheros is even part of my equation.
If you feel extraordinarily generous, then also feel free to spend any time you can spare figuring out what animal it is. Otherwise thanks so much for replying to my post/
Meanwhile I will try to find out more about this unnecessarilly exotic beast. Thanks again.

---

### Post by Jestocost on 2008-05-22
I'm in a chicken/egg situation here, since the wifi would be my only way to connect my laptop to the web. So I can't do the package updating or anything such.

Would some kind soul list the filenames of all the packages I need to manually download (hello internet coffeehouse!) for 8.04? If I understood this right, it would be all the build tools plus kernel headers?

---

### Post by nicedude on 2008-05-23
Jestocost I have modified my directions for someone asking what you asked but I don't quite understand what your situation is. Are you saying that your wifi is already working and you just want to use different drivers instead such as the madwifi ones ? They are the best drivers available but if your wifi is already working there are only a few reasons to want to change them and they are mostly advanced user reasons related to wireless hacking. If you would like advice in your situation please PM me by clicking on my name and selecting "send private message" and include all the details of your situation and I can advise you as to what attempting my guide will mean you would have to do.

---

### Post by beN..87 on 2008-05-23
using a samsung r60+ its got ATI Radeon chips in it - this should work cos ive got that wireless chip 100% - ive done it this way - all on a fresh laptop with fresh install - still no luck -- i can get ubuntu up and running - graphics are sweet as a nut, it recognises the wireless signal after i install madwifi - ive tried bothe versions - the 2537 and the 3366 anyways it still wont work even with synaptic disabling the jockey and whatnot - i get a signal - but cannot get an IP adress - it isnt the box cos that works with XP, Vista , and Linux on another Machine.

i reckon its the ATI proprietry driver - but ive tried it this way and it doesnt work either - something to do with the ATI chips proprietry driver locking stuff up? 

i even installed madwifi in shell mode after logging in alt F2 after a fresh install - before going anywhere near the ATI propreietry stuff - getting it all done then istalling the ATI stuff - getting into X - same result - i get a signal but cannot get past "retreiving IP adress"

any ideas?

---

### Post by beN..87 on 2008-05-23
> **beN..87 said:**
> using a samsung r60+ its got ATI Radeon chips in it - this should work cos ive got that wireless chip 100% - ive done it this way - all on a fresh laptop with fresh install - still no luck -- i can get ubuntu up and running - graphics are sweet as a nut, it recognises the wireless signal after i install madwifi - ive tried bothe versions - the 2537 and the 3366 anyways it still wont work even with synaptic disabling the jockey and whatnot - i get a signal - but cannot get an IP adress - it isnt the box cos that works with XP, Vista , and Linux on another Machine.

i reckon its the ATI proprietry driver - but ive tried it this way and it doesnt work either - something to do with the ATI chips proprietry driver locking stuff up? 

i even installed madwifi in shell mode after logging in alt F2 after a fresh install - before going anywhere near the ATI propreietry stuff - getting it all done then istalling the ATI stuff - getting into X - same result - i get a signal but cannot get past "retreiving IP adress"

any ideas?

Oh, and before anyone suggests it - no i cannot use envyNG to install the ATI stuff because i dont have an internet connection do i - i'm installing the driver right off of ATI's website - after installing madwifi first that is

come on ppl please please help! im absolutely stuck

---

### Post by barlas on 2008-05-23
> -= STEP 4 =- Removing Default Stuff
 Using synaptic package manager remove all instances of the following 2 exact names by searching by name only and pasting these names in the box ( To use synaptic click on top menu bar System -> Administration -> Synaptic Package Manager )
 
 linux-restricted-modules ( VIDEO & WIFI DRIVERS THAT ARE COPYRIGHTED - just don't remove linux-generic-kernel as that is vital)
 Jockey ( the restricted driver manager ) 
 
 just search for these two names and check box to remove them then apply. 
I don't have linux-restricted-modules, but linux-restricted-modules-2.6.24.16-generic, linux-restricted-modules-commong & linux-restricted-modules-generic and selecting any of these for removal also selects linux-generic for removal, which (as you said) shouldn't be removed. 

I am using kubuntu-kde4 8.04, any ideas?

---

### Post by nicedude on 2008-05-23
To beN..87 I am not sure why it isn't working for you but I will try to help you but need some more info. For starters you say you used two versions of the madwifi drivers, did you perhaps use the 2537 and then just use the 3366 also without first removing the 2537 driver as it would definitely cause you a problem and also I am not aware that any 2537 version works for any Ubuntu AR5007EG senario since under gutsy I was using 2756 and now must use 3366 but it could be that it was the right one before 2756 came along but not sure. If you did not remove the 2537 then I would recommend you do that now. Second are you sure you followed my guide fully and completely including the modules file that you had to modify, please just do a double check for me before you respond with the following info I need.

please post the results of the following commands & PM them to me as well so that I will see them for sure the quickest I can.

Command that will list PCI devices present in the system.
lspci

Command to list wireless adapters in the system.
iwconfig

Command to see what access points are in range
iwlist ap

Your problem could just a configuration one so could you include both what network manager you are using to put your settings in place and what encryption type if any you are trying to connect with?

Please answer those and I will try to help you fix it.

---------------------------------------------------------------------------

To Barlas I guess I should have been more clear in my directions since all the things you list are not needed for the system to function the packages I didn't want you to remove are listed below as are the ones ok to remove as long as like I say in the beginning of the guide you are prepared to manage your own graphics driver if it is currently being managed by jockey. I wasn't clear about the linux-generic as I meant linux-image-2.6.24-16-generic as that is basically your kernel and without it your box will not work. I will change that so no one else gets mixed up. 

And when you put linux-restricted-modules-commong -- did you mean for the g to be on the end of that as I don't have that available and google didn't give one hit for it so I an assuming you meant linux-restricted-modules-common 

THESE ARE OK FOR SENDING BYE BYE - I HAVE NONE OF THESE INSTALLED IN UBUNTU HARDY AND I AM TYPING THIS SO I AM PRETTY SURE
linux-restricted-modules-2.6.24.16-generic 
linux-restricted-modules-common 
linux-restricted-modules-generic 
linux-generic

----------------------------------------------

THESE ARE NOT OK TO REMOVE - DO NOT REMOVE THESE - I HAVE ALL OF THESE
linux-image-2.6.24-16-generic 
linux-ubuntu-modules-2.6.24-16-generic
linux-headers-2.6.24-16 
linux-headers-2.6.24-16-generic

----------------------------------------------------------------------

Please PM me anyone who has problems so I for sure see your needing help and can respond as quickly as possible to you.

---

### Post by barlas on 2008-05-23
Thanks for the help, I got it working fine with networkmanager, didn't get need to install wicd.

And yes, that 'g' was a typo, it was linux-restricted-modules-common.

---

### Post by Jestocost on 2008-05-23
Nicedude, what I meant is: I don't have any kind of internet access so there was no way I could do the package updating required for compilation of the madwifi patch. I had to go to one of those internet public places and manually download the files for those packages to my USB pendrive. It seems to have worked, as wifi now shows up (still need to test it by hooking to a public hotspot, as I said I have no internet access of my own). For reference, the file names of the packages I downloaded and installed manually in that way: linux-kernel-headers_2.6.11.2-0ubuntu18_i386.deb, linux-libc-dev_2.6.24-16.30_i386.deb, libc6-dev_2.7-10ubuntu3_i386, libgc-dev_6.8-1.1_i386. Thanks for your help...

---

### Post by nicedude on 2008-05-23
You need to look up the make and build essential packages and see what all their dependencies etc may be and then see if you have them or not, if not you would have to download them. Might I suggest that if needed you can get debs ( kinda like a windows installer just click and install ) from the following resources that will work for your Ubuntu   

Ubuntu deb packages
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Debian packages
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

Another source
[http://www.getdeb.net/](http://www.getdeb.net/)

Also if you have a Hardy install cd you might try the following as it will add the install cd itself to your list of sources for installation so that anything contained there can be installed by your system directly form the cd. This is not done by default but I also have no idea if make or build essential packages are located on the disk. here are the commands to add it anyway as without internet I am sure you will find it helpful in future as should you the deb locations above.

First one will add it to sources second will make it be in effect
sudo apt-cdrom add
sudo aptitude update

Then try the following to see if the packages you need are there
sudo apt-get install make build-essential

If that works then all you should need is the madwifi driver package I outline in my guide and any video drivers that may be required if you have an ATI or Nvidia graphics card as outlined in step 1.

Also if you think your connected to a network with your wifi try the command below and see if you can ping google or not as that is a good indication if you are actually connected or not.

ping -c 3 [www.google.com](www.google.com)

And if you have any further troubles please post your results here of the following commands so I can see better what is going on with your card. Anyone else reading this guide and needing help please run and post these as well so I can help you the best I can.

lspci

iwconfig

iwlist ap

So just run those three and post the results as they would help me ascertain what your current situation is.

Hope this info helps both you and anyone else that has this type of situation.

nicedude

---

### Post by beN..87 on 2008-05-25
well then nicedude i've clicked that star of yours, as i am writing this in firefox on my nicely working and connected up hardy 8.04, success! thanks for the help - that guide is spot on , turns out it was wcid. - anyone else with a samsung R60 running ATI radeon chipset - this guide works

---

### Post by beN..87 on 2008-05-25
> **beN..87 said:**
> using a samsung r60+ its got ATI Radeon chips in it - this should work cos ive got that wireless chip 100% - ive done it this way - all on a fresh laptop with fresh install - still no luck -- i can get ubuntu up and running - graphics are sweet as a nut, it recognises the wireless signal after i install madwifi - ive tried bothe versions - the 2537 and the 3366 anyways it still wont work even with synaptic disabling the jockey and whatnot - i get a signal - but cannot get an IP adress - it isnt the box cos that works with XP, Vista , and Linux on another Machine.

i reckon its the ATI proprietry driver - but ive tried it this way and it doesnt work either - something to do with the ATI chips proprietry driver locking stuff up? 

i even installed madwifi in shell mode after logging in alt F2 after a fresh install - before going anywhere near the ATI propreietry stuff - getting it all done then istalling the ATI stuff - getting into X - same result - i get a signal but cannot get past "retreiving IP adress"

any ideas?

works for samsung r60 laptop with wcid network manager

---

### Post by Israphel on 2008-05-25
I followed all the steps, and it works... but... it doesn't find any network, and I'm next to the router, completely open without encryption.

lspci says

```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

and iwlist ap says

```
lo        Interface doesn't have a list of Peers/Access-Points

eth0      Interface doesn't have a list of Peers/Access-Points

wifi0     Interface doesn't have a list of Peers/Access-Points

ath0      No Peers/Access-Point in range

```

iwlist scan says

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

```

---

### Post by beN..87 on 2008-05-26
Israphel - first off your lspci has your card listed as a 242 not 5007 ---- dont worry that isnt the problem , dont get  distracted by that - mine says the same for some reason but it works. 

It looks to me that your wireless card rather than the box is the problem - but i dont know enough about this really --- my suggestion would be to install wicd network manager, uninstall and reinstall madwifi by doing :
cd madwifi3366
sudo bash
make uninstall
make clean
make
make install

apt-get install wicd   (you will have to uninstall gnome network-manager through synaptic)

then check that in wicd preferences you have listed ath0 and eth0 as your interfaces, and that your WPA supplicant driver is listed by wicd as madwifi (again in preferences of wicd)

my problem was that wicd had not isted ath0 and my preferences were set to WPA supplicant as the default instead of madwifi

anyway if youve followed nicedudes guide properly but havent installed wicd or havent checked its preferences, that would be my suggestion

also dont forget the part of the guide as thats what tells the system about ur wireless

sudo modprobe ath_pci


like i said it worked for me once i was able to go through the guide without hickups, and check all the settings in wicd were correct

good luck with your card! perhaps nicedude can be more specific about your diagnostics report

---

### Post by nicedude on 2008-05-26
Israphel - could you please post the results of iwconfig command as that might give a bit more insight. But in general I don't think yours is up and running correctly or your wide open network would be detect by the iwlist command. Also the showing up as AR242x thing is normal in Hardy Heron as it incorrectly ID's the chipset thats why everyone should verify what chipset they have via their manufacturer ( before trying this guide or any other to ensure you are installing the right stuff )if at all possible ( mine wasn't easy to find but I eventually found it, if anyone can't verify I would recommend bugging their tech support to tell you and then asking why they don't list it in the specs as they could avoid both the phone calls and the confused customers ). But I just did a reinstall of Hardy on my laptop today and used my own guide and it worked with ease so I can say that if you have the AR5007EG chipset and Hardy Heron Ubuntu ver 8.04 that it will work 100% but only if followed to the letter as there are not any steps you can really change or leave out and still have success. Also I will be updating my guide for Nvidia users today to tell you how step by step to install Nvidia drivers by hand using their installer package, so everyone might check that out as well.

HERES MY LSPCI OUTPUT FOR MY ATHEROS ITS WRONG AS WELL, BUT IT SURE WORKS :-) 
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


Hope this guide helps some people out and I know it has helped a few already who have relayed to me that other guides for this chipset did not work for them so I am glad of that. Heck this took me awhile to get working for myself and I thought I should pass the technique on. All that said please post here if you have trouble or success and if its trouble I will try to help you solve it. The only thing I can't help with is ATI installs as I don't have an ATI in any of my boxes to test with so if anyone who uses this and has ATI could post how they did it that would be appreciated as would anyone who uses this guide and then "envyng" to install graphics with success I would like to hear about that as well.

Good luck all and be sure to post what your results are,

nicedude

---

### Post by Israphel on 2008-05-27
iwconfig says:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-148 dBm  Noise level=-148 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

The laptop is Compaq F755LA, and I'm under Kubuntu 8.04, so I use Knetworkmanager by default, but I can install wicd if necessary.

The same happened when I used ndiswrapper on the 64 bit version. The driver works, but no network found.

Envyng doesn't work without the restricted modules installed, so I used the .run file of the nvidia page, and it's working.

---

### Post by _godbout_ on 2008-05-27
Thanks to nicedude!
My wifi worked, but I was not able to turn the monitor mode on. With the patch, it works perfectly!

---

### Post by SpinningAround on 2008-05-27
Does the kernel update make the AR242x work without needing to go throw this guide? Think it have something to do with the kernel but don't know when AR242x will be added as standard, anyone know?

---

### Post by nicedude on 2008-05-27
The update kernel might make it work for normal wifi ( Although I am unsure ), But the real use of this guide is to get the BEST driver installed and working i.e. the one that will let you put your card in monitor mode for use with kismet and other wifi scanners and its also patched for use with aircrack software which is what you use to get others WEP keys. So if all you want to do is just connect to a wifi that you have all the settings for and are allowed to and you don't want to learn anything about or use any wifi hacking tools then if it does fix it you would be best served that way probably as doing what I outline is not super easy but I know at least 5-8 people have used this to do it, so it does work.

So to anyone skimming this thread if you want to use AIRCRACK & KISMET with your AR5007 on top of normal networking you will need to install this driver ( using my guide or another one but definitely the driver I link to ) as it is aircrack patched and I don't think they will be using aircrack patched ones with their kernel updates :-)

---

### Post by sicotico on 2008-05-27
somebody created a package with madwifi patched , I need help because the dpkg-buidpackage -rfakeroot fails and reports:

# Copy only the driver source to the proper location
cp -s driver/*  debian/ar5007-source/usr/src/modules/ar5007
cp: no se puede efectuar `stat' sobre `driver/*': No existe el fichero ó directorio
make: *** [install] Error 1
dpkg-buildpackage: fallo: fakeroot debian/rules binary gave error exit status 2

In the dh_make, select option k.


Thaks

---

### Post by Israphel on 2008-05-27
So, if I install the new kernel, the WiFi will work? I just want to connect to my Router in my house, nothing more, in this city there aren't a lot of wifi connections to crack, welcome to argentina!

In that case, I'll just reinstall all.

---

### Post by nicedude on 2008-05-27
When you reinstall the kernel you will then have to reinstall the driver I do believe as when you use "sudo make" and "sudo Make Install" they are building themselves for that kernel so when you update I don't think it will still work. But all you would need to do is run the uninstall in the madwifi directory and then run "sudo make clean" then "sudo make" and then "sudo install" & "modprobe ath_pci" and it would be back installed for the new kernel. I am not sure the exact uninstall command but you can either find it in the README or INSTALL text files in the madwifi directory or by reading the user guides at madwifi as that is covered there as well. Hope that helps :-)

---

### Post by Israphel on 2008-05-27
Well, I'm reinstalling kubuntu from the CD XDD

So, I have to remove the restricted modules, again, and install madiwifi?

I don't want to destroy the laptop with a shotgun.

modprobe ath_hal and ath_pci, or only ath_pci?

In the /etc/modules file, have I to add the both lines?

EDIT -->I did everything again, and this time I'm using WICD instead of knetworkmanager. And again, it doesn't find any network.

And now, Wicd doesn't auto-connect to the Wired network, do you know how to do that?


EDIT 2 --> Wicd auto-connect Wired network (don't know how), but still no wireless network.

---

### Post by williamson389 on 2008-05-27
nicedude-
after a fresh install of 32bit hardy i folowed your walkthrough exactly, with no errors. Still, somehow no wireless connection is even appearing in Wicd. when looking what my wireles card is, my computer recognizes it as ar242x, but i am at present unable to find out for sure what it is from the maufacturer.  i am also unsure of how to install the ati driver, as when i run it goes to gedit and is "unable to recognize the coding".
here is my info, anything else just ask. i have connected wirelessly using windows, just not ubuntu.  my computer is an acer aspire 5100

bill@bill-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
bill@bill-laptop:~$ 

bill@bill-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

bill@bill-laptop:~$ iwlist ap
lo        Interface doesn't have a list of Peers/Access-Points

eth0      Interface doesn't have a list of Peers/Access-Points

---

### Post by Israphel on 2008-05-28
Everybody should vote here :KS

[[IMG]http://brainstorm.ubuntu.com/idea/6589/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/6589/)

---

### Post by nicedude on 2008-05-28
OK guys I have a new tip for all who are suffering from the "I can't figure out if I have an AR5007EG" dilemma. While I solved my nightmare by looking through my manufacturers different support sites ( for different countries ) until I found my info, I have found while searching for what laptop has what chipset for others that sometimes even that isn't possible. So I set about to find a way ( since lspci alone gives us bad ID info ) for everyone with Ubuntu to be able to test if they actually have an AR5007EG or not. Here is how we can do this, so anyone who is not sure of their chipset please do the following.

FIRST RUN A "lspci" COMMAND - MY OUTPUT IS BELOW

nicedude@mybox:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

AS YOU CAN SEE THE LINE THAT BEGINS WITH 05:00.0 IS MY WIFI CARD EVEN THOUGH THE ID IS NOT CORRECT

REMEMBER WHAT YOURS IS OR WRITE IT DOWN AND THEN RUN THIS COMMAND TO GET THE TRUE VENDOR PCI ID FOR DEVICES

lspci -n

HERES MY OUTPUT FROM THAT COMMAND

nicedude@mybox:~$ lspci -n
00:00.0 0500: 10de:0547 (rev a2)
00:01.0 0601: 10de:0548 (rev a2)
00:01.1 0c05: 10de:0542 (rev a2)
00:01.2 0500: 10de:0541 (rev a2)
00:01.3 0b40: 10de:0543 (rev a2)
00:02.0 0c03: 10de:055e (rev a2)
00:02.1 0c03: 10de:055f (rev a2)
00:04.0 0c03: 10de:055e (rev a2)
00:04.1 0c03: 10de:055f (rev a2)
00:06.0 0101: 10de:0560 (rev a1)
00:07.0 0403: 10de:055c (rev a1)
00:08.0 0604: 10de:0561 (rev a2)
00:09.0 0101: 10de:0550 (rev a2)
00:0a.0 0200: 10de:054c (rev a2)
00:0b.0 0604: 10de:0562 (rev a2)
00:0c.0 0604: 10de:0563 (rev a2)
00:0d.0 0604: 10de:0563 (rev a2)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:04.0 0c00: 1180:0832 (rev 05)
01:04.1 0805: 1180:0822 (rev 22)
01:04.2 0880: 1180:0843 (rev 12)
01:04.3 0880: 1180:0592 (rev 12)
01:04.4 0880: 1180:0852 (rev ff)
02:00.0 0300: 10de:0428 (rev a1)
05:00.0 0200: 168c:001c (rev 01)

AS YOU CAN SEE THE 05:00.0 IS PCI VENDOR ID 168c:001c - AN AR5007EG WILL HAVE THAT ID STRING

If your output from these commands gives you anything but 168c:001c then you don't have an AR5007EG but instead another wifi chipset ( could well be Atheros brand but not a AR5007EG ). If your results do show a different value then Google that value and see what you find. When I Googled the 168c:001c ID for my AR5007EG I did find however that it could also be a AR5006EG but this is as close as I can get to the truth without telling you to take your laptop apart & remove the interference shielding and visually verify the FCC ID and look it up ( And I would not and do not recommend that for anyone who isn't a PC technician with laptop repair experience )

So to Williamson389 or any others who can't verify through tech support or manufacturers literature your exact wifi please do the above and post back if that gave that value because if it does not then you don't have an AR5007EG and my guide won't work for you.

---

### Post by beN..87 on 2008-05-28
for ATI Radeon Graphics Chipset: 


get the ATI proprietry drivers from here 

[https://a248.e.akamai.net/f/674/9206...x86.x86_64.run](https://a248.e.akamai.net/f/674/9206...x86.x86_64.run)

put the file on a USB drive  or similar

insert hardy 8.04 i386 (NOT the 64 bit) ALTERANATE CD (must be alternate CD)
F6       (opens boot paramater line to input)
noapic   (add this to prevent I/O Bug) 
<press enter>  (Starts install process)
Install to ones liking.
Reboot into system without cd in drive. 
Press alt F2 and login.
Insert Install CD
sudo bash
apt-cdrom add (adds the CD to the lsit of resources)
apt-get install build-essential (installs build environment)
remove CD
mkdir /mnt/usb  (mount point for external media)
insert your USB flash drive or other media
mount /dev/sdb1 /mnt/usb   (your point may be /dev/sda1 or /dev/sdb2 or similar)
cp -R /mnt/usb /usb
umount /dev/sdb1 /mnt/usb
remove flash drive
mv /usb /ati-driver
cd /ati-driver
sh ati-driver-installer-x86.x86_64.run
--- just accept all defaults for the install - literally its yes yes yes yes
after install is complete---
reboot

your Ubuntu should now boot into a full graphical gnome system

now for your wireless card - follow nicedudes guide TO THE LETTER   ( also install wicd network manager is reccomended)

this worked for me on ATI Chipset /Aetheros wireless (Samsung r60plus)

---

### Post by beN..87 on 2008-05-28
> **nicedude said:**
>  The only thing I can't help with is ATI installs as I don't have an ATI in any of my boxes to test with so if anyone who uses this and has ATI could post how they did it that would be appreciated as would anyone who uses this guide and then "envyng" to install graphics with success I would like to hear about that as well.

Good luck all and be sure to post what your results are,

nicedude

for ATI Radeon Graphics Chipset:


get the ATI proprietry drivers from here

[https://a248.e.akamai.net/f/674/9206...x86.x86_64.run](https://a248.e.akamai.net/f/674/9206...x86.x86_64.run)

put the file on a USB drive or similar

insert hardy 8.04 i386 (NOT the 64 bit) ALTERANATE CD (must be alternate CD)
F6 (opens boot paramater line to input)
noapic (add this to prevent I/O Bug)
<press enter> (Starts install process)
Install to ones liking.
Reboot into system without cd in drive.
Press alt F2 and login.
Insert Install CD
sudo bash
apt-cdrom add (adds the CD to the lsit of resources)
apt-get install build-essential (installs build environment)
remove CD
mkdir /mnt/usb (mount point for external media)
insert your USB flash drive or other media
mount /dev/sdb1 /mnt/usb (your point may be /dev/sda1 or /dev/sdb2 or similar)
cp -R /mnt/usb /usb
umount /dev/sdb1 /mnt/usb
remove flash drive
mv /usb /ati-driver
cd /ati-driver
sh ati-driver-installer-x86.x86_64.run
--- just accept all defaults for the install - literally its yes yes yes yes
after install is complete---
reboot

your Ubuntu should now boot into a full graphical gnome system

now for your wireless card - follow nicedudes guide TO THE LETTER ( also install wicd network manager is reccomended)

this worked for me on ATI Chipset /Aetheros wireless (Samsung r60plus)

---

### Post by ElEdTech on 2008-05-28
I can confirm with my Acer Aspire 5570z that the steps listed in this forum worked. I changed them around a little bit (I have neither ATI or Nvidia to worry about) but for the new link from MadWifi posted on the first page was different from the one I used from this page...

[http://ubuntufor5570z.blogspot.com/2008/04/update-new-wireless-instructions.html](http://ubuntufor5570z.blogspot.com/2008/04/update-new-wireless-instructions.html)

Last night, after my wifi stopped working due to the updates, I uninstalled and reinstalled following the exact steps from the blogspot page. 

Everything worked but my Suspend and Hibernate were still broken.

Today I uninstalled the Madwifi patch and reinstalled it using the driver listed on page 1 of this posting.

[http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

I also added ath_pci and ath_hal to my modules listing. 

Now my wifi is working AND my hibernate and suspend are working like a charm.
Before when I tried to Suspend or Hibernate I had a black screen full of white text! Now it works!

Thank you!

---

### Post by williamson389 on 2008-05-28
after running lspci -n, i am positive i have an ar5007.now that i know that,how did the guide not work?

---

### Post by Israphel on 2008-05-28
Everything OK here, working with WPA2 Encryption, a 63 characters long passkey (100% ASCII), and 100% of signal in all the house :)

Anyway, everybody should vote in the link I've posted, we need more support or an improvement of MadWifi and Wicd (more than they already are).

Nivida geforce 7000M working great, integrated webcam working great. Last Step: The internal Mic :(

---

### Post by clockworkmcd on 2008-05-28
this seems like overkill to me. check out the thread [http://ubuntuforums.org/showthread.php?t=810723](http://ubuntuforums.org/showthread.php?t=810723) before you do all this. worked for me on multiple installs. i've narrowed down exactly what needs to be done to make it work. i don't believe that you need to do all this other stuff but i could be wrong.

---

### Post by nicedude on 2008-05-29
Clockwork your way might work for you but it didn't work for my box and as such I made this. Also the driver you link to is not the newest one, the newest is 3366 so you might want to look at changing that. As I state in my little guide this is not the only way its "my way" and since I think the restricted driver manager is flaky at best I just throw it in the digital trash and prefer instead to manage my own stuff myself and not rely on that silly "JOCKEY" software to try and do it for me. As I speak I have the very best AR5007EG driver and the very best Nvidia Beta driver installed and working and JOCKEY can't do that but I can, so I choose to do things myself as if I wanted easy I would be using Microsoft in the first place. I have 2 requirements for my boxes first that it works with the best drivers available for key components second that it be DRM free and that I can control and configure it myself. So due to those two philosophies this is where it led me, Both to Ubuntu and to use my install methods. Your welcome to anyone I have helped to get control of your Ubuntu box and may you in time learn ( as I am )  through your own trials by fire so to speak :-) 

Now if I can only get my Aircrack 1.0 beta 2 source to compile and work with an injection capable driver for my Edimax 7318USG and all coexist and play nice with my madwifi 3366 aircrack patched AR5007 then I will be happy but for right now it has given me a headache :-(

If anyone is using 3366 madwifi aircrack patched driver and has had success building and installing the Aircrack 1.0 beta2 source ( I can get it to build and install just not to work with madwifi ) then please PM me or post here. I am not talking about the one in the repositories to any that may think thats the answer as that is old and doesn't support newest injection and fragmentation attacks.

EDIT : I got aircrack-ng 1.0 beta2 working so now just need a Edimax 7318USG injection & frag enabled driver so I am 50% of the way to solving my own problems :-)

Oh well time to take a few aspirin and start again so good luck to all others as well.

---

### Post by cooldudeak on 2008-05-29
Hey nicedude. I want to try your instructions but the problem is that I had followed some other guide ([http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html")) (I am on 32-bit) and downloaded and compiled some other madwifi packages (my network showed up but I was not able to connect...:( )
So now I want to know how should I remove them. I don't think I will be able to follow the guide before removing them..



Please guide...

---

### Post by beN..87 on 2008-05-29
> **cooldudeak said:**
> Hey nicedude. I want to try your instructions but the problem is that I had followed some other guide ([http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html]("http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html")) (I am on 32-bit) and downloaded and compiled some other madwifi packages (my network showed up but I was not able to connect...:( )
So now I want to know how should I remove them. I don't think I will be able to follow the guide before removing them..



Please guide...

first off disbale the restricted modules as listed in nicedudes guide


to uninstall previously installed madwifi packages cd into the directory of the one you installed, do the following:

sudo bash
cd madwifi-blabla
make uninstall

then get the 3366 version of mad wifi listed in the guide and,  in a different dirtectory and unpack it and install it

sudo bash
tar -xvzf madwifi3366
cd madwifi3366
make
make install

then youll need to use synaptic to get rid of
network manager
network manager-gnome

then install wicd network manager

apt-get install wicd

check the preference of wicd that  the WPA supplicant is listed as madwifi
also check that ath0 and eth0 are listed in mad wifi ( i had to manually list ath0)

then just check your WEP pass key is correct and whether it is 1/2 or hex is correct

--- also just make sure you follow nicedudes guide properly all should work

hope this helps, ben

---

### Post by Thorzilla on 2008-05-29
Hi,
This process worked like a charm on my Toshiba and wireless was working fine until yesterday, when I installed 26 new updates and restarted my computer.
Now, I'm back to square one, and I'm not sure what has changed.
Will I have to repeat this process or do something else because madwifi is already installed?


Laptop Specs:
Toshiba A221
AMD Turion 64 Duo Core
160GB HDD, ATI Radeon Graphics
Atheros AR5700EG Wireless card

Ubuntu Hardy 8.04 dual booted with Vista


Thanks in advance
TZ

---

### Post by beN..87 on 2008-05-29
Thorzilla - from you comment  about the updates -you obvously know its that which has done it , but which one?

well - i got a list of updates also and noticed that it had on the list linux-restricted modules ---- so i pressed reject --- my advice would be go back and check that restricted modules are still turned off - cos those are what stops the madwifi patch from working.

if you are gonna reinstall madwifi - there is a newer patch -the 3366 as listed by nicedude - it works alot better

to unintall and reinstall madwifi - the instructions are on the comment just before yours

---

### Post by williamson389 on 2008-05-29
sorry but can anyone help me out. i have no clue what to do, and i cant use my laptop.

---

### Post by Thorzilla on 2008-05-29
Reinstallation worked! A-thank-u

---

### Post by beN..87 on 2008-05-29
> **williamson389 said:**
> sorry but can anyone help me out. i have no clue what to do, and i cant use my laptop.


you'll have to be abit more specific than that my friend

---

### Post by beN..87 on 2008-05-30
> **nicedude said:**
> 


*** FOR ATI CARDS

DRIVER PACKAGE
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_64.run)

ATI WIKI FOR INFO ON ITS USE
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-4-x86.x86_64.run)

Once you have the driver or if its not managed by the restricted manager then you are ok for step 2




ati drivers no longer available at that link - get them at ATI website

 [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

---

### Post by cooldudeak on 2008-05-31
Hey people, I am stuck on step 5.
I have the "make" and "build-essential" packages installed.
What I think is that when I removed those restricted-modules thing, my kernel got updated to '17' (see below) and I have my "make" and "build-essential" for version '16'. I am stuckkkkkkkk....:confused:

Please help

```
akshay@akshay-laptop:~$ cd ~/madwifi-nr-r3366+ar5007
akshay@akshay-laptop:~/madwifi-nr-r3366+ar5007$ sudo make
cd: 1: can't cd to /lib/modules/2.6.24-17-generic/build
Makefile.inc:66: *** /lib/modules/2.6.24-17-generic/build is missing, please set KERNELPATH.  Stop.
akshay@akshay-laptop:~/madwifi-nr-r3366+ar5007$
```

---

### Post by cooldudeak on 2008-05-31
All right. I got through that step somehow, now I have finished the whole process including installing wicd. But I think I am back to square One, I can see the network but cannot connect to it..........
Damn it!

Please help guys...I am stuck on it for more than a week now....
Plzzzzzzzzz guide.......:(

---

### Post by cooldudeak on 2008-05-31
Allright people...
it is some diffrent problem..
I can sometimes connect to the internet, it lasts for about 2-3 minutes and it dies again...
then i ususally issue the following command:

sudo dhclient ath0

it reconnects again after 2 -3 minutes and this is what happens...

help please...

---

### Post by azdavef on 2008-06-02
Worked for me on a new Toshiba A205.  Did have to tell WICD what to use (ath0) and change to madwifi.  After that it worked like a charm.  I am a Linux noob, but not a boob.  WICD is miles ahead of the Network Manager..

---

### Post by bluester on 2008-06-03
> **beN..87 said:**
> Israphel - first off your lspci has your card listed as a 242 not 5007 ---- dont worry that isnt the problem , dont get  distracted by that - mine says the same for some reason but it works. 

It looks to me that your wireless card rather than the box is the problem - but i dont know enough about this really --- my suggestion would be to install wicd network manager, uninstall and reinstall madwifi by doing :
cd madwifi3366
sudo bash
make uninstall
make clean
make
make install

apt-get install wicd   (you will have to uninstall gnome network-manager through synaptic)

then check that in wicd preferences you have listed ath0 and eth0 as your interfaces, and that your WPA supplicant driver is listed by wicd as madwifi (again in preferences of wicd)

my problem was that wicd had not isted ath0 and my preferences were set to WPA supplicant as the default instead of madwifi

anyway if youve followed nicedudes guide properly but havent installed wicd or havent checked its preferences, that would be my suggestion

also dont forget the part of the guide as thats what tells the system about ur wireless

sudo modprobe ath_pci


like i said it worked for me once i was able to go through the guide without hickups, and check all the settings in wicd were correct

good luck with your card! perhaps nicedude can be more specific about your diagnostics report

beN..87 and nicedude;

I too was experiencing the same issue as Israphel.
I too was receiving the same response from iwconfig, iwlist, etc.
I have a Toshiba A205-S5825 laptop - Intel graphics and Aetheros wireless.
I read ben..87 post above which stated his error as:
"my problem was that wicd had not isted ath0 and my preferences were set to WPA supplicant as the default instead of madwifi"
Coincidentally, this was my problem as well... I made the appropriate changes and viola; wireless is working very well!

MANY THANKS TO ALL!
Linux rocks, Windows stops!:guitar:

---

### Post by henkeb on 2008-06-04
Really good guide dude. I have a strange problem though, I've managed to get my atheros card working with the ng-r2756 driver. However, after a while beeing logged on to my system, it starts to lag and sometimes eventually freeze. If i try to remove the ath_pci module I get an errror message saying segmentation fault, but if I restart I can remove the module and everything is fine (except I don't have wireless...again) Any ideas anyone??
Thankful for any help I can get, been trying to solve this for several days straight now.

---

### Post by beN..87 on 2008-06-04
> **henkeb said:**
> Really good guide dude. I have a strange problem though, I've managed to get my atheros card working with the ng-r2756 driver. However, after a while beeing logged on to my system, it starts to lag and sometimes eventually freeze. If i try to remove the ath_pci module I get an errror message saying segmentation fault, but if I restart I can remove the module and everything is fine (except I don't have wireless...again) Any ideas anyone??
Thankful for any help I can get, been trying to solve this for several days straight now.

madwif2756 has some issues on the Aetheros 5007 - get the 3366 as instructed

---

### Post by henkeb on 2008-06-04
Ah ok thanks for the tip man, I'll try that and switching to wicd also to see if it makes any difference. I just love this forum, it's a good thing there are so many helpful people out there. I'm not at all religious, but god bless open source =)

---

### Post by kingair on 2008-06-04
To the original poster. Thank You!!!!!

---

### Post by bluester on 2008-06-04
In reference to my reply, #63 I believe...
When I reboot the computer, I must start wicd, choose Hidden Network, type in my ESSID (which is not broadcasted), once the ESSID is shown in the available networks, I can then connect using the saved settings and password.
The "Automatically connect to this network" box is checked...

Any ideas as to why it does not auto-start?:confused:

---

### Post by henkeb on 2008-06-04
beN..87, thanks a billion, now it finally works (I think) no crashes yet. I've tried the 3366 driver before but my computer wouldn't detect the card using that driver. This time it worked somehow, I added the ath_hal line to /etc/modules and installed wicd instead of network-manager and now it works as a charm. Thanks a lot for the help.

---

### Post by Coffeeman51 on 2008-06-04
Oh, I love the fix because it works...or rather it did work...

Until the latest kernal update that I downloaded this morning...which promptly reverted to no nvidia and no wifi...btw I also have a Aspire 5520. So my question is, Do I have to redo the whole fix or what?

---

### Post by bluester on 2008-06-05
> **Coffeeman51 said:**
> Oh, I love the fix because it works...or rather it did work...

Until the latest kernal update that I downloaded this morning...which promptly reverted to no nvidia and no wifi...btw I also have a Aspire 5520. So my question is, Do I have to redo the whole fix or what?

I had the same issue; I uninstalled and reinstalled the madwifi by doing :

cd /directory/madwifi3366
sudo si
make uninstall
make clean
make
make install

Check wicd for proper setting (if already installed) and you should be alright. :popcorn:

---

### Post by Coffeeman51 on 2008-06-05
worked like a charm...thanks (I'm back on my laptop) and I did have to do a re-install of the nvidia driver...but with a nice printout it was easy...

---

### Post by beN..87 on 2008-06-06
> **bluester said:**
> In reference to my reply, #63 I believe...
When I reboot the computer, I must start wicd, choose Hidden Network, type in my ESSID (which is not broadcasted), once the ESSID is shown in the available networks, I can then connect using the saved settings and password.
The "Automatically connect to this network" box is checked...

Any ideas as to why it does not auto-start?:confused:


no mine doesn't auto connect either - i just have to press the buton on wicd when i start up - can't figure out why as ive set it to connect on start up .... maybe the madwifi patch will sort that in the next release, for now tho, i'm happy!

---

### Post by bluester on 2008-06-06
> **beN..87 said:**
> no mine doesn't auto connect either - i just have to press the buton on wicd when i start up - can't figure out why as ive set it to connect on start up .... maybe the madwifi patch will sort that in the next release, for now tho, i'm happy!

I found a possible solution here: [http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends#TheStationclientSide](http://madwifi.org/wiki/UserDocs/WPA_PSK_on_Both_Ends#TheStationclientSide)

However, when I try to build wpa_supplicant on the station it errors during the build. I have "make" and "build-essential" installed on my system.

I try again later tonight and report back.

Btw, there is a gui build with the supplicant as well. 
I will try that also. 
Cheers. :guitar:

---

### Post by calcfreak83 on 2008-06-06
> **Israphel said:**
> Everything OK here, working with WPA2 Encryption, a 63 characters long passkey (100% ASCII), and 100% of signal in all the house :)

I have a Compaq f700, and have run into the exact same problem. Did you do anything special to get the card to work?

---

### Post by idgara on 2008-06-07
Thanks Nicedude

Worked well for me on a Toshy Satellite Pro A200.

I couldn't make it connect with wicd no matter what I did. Wicd could see the wireless network, seemed to connect but would never get an IP.

I tried setting up a script to do it all from the command line, but the same thing happened - could connect, but never got an IP. I did setup the wpa_supplicant correctly I believe.
 
However all was not lost as it connects fine using network-manager - so swmbo will be pleased :D

---

### Post by Kulgan on 2008-06-07
Popping in to give a big THANK YOU!

Everything worked perfectly, including WPA encyption. At first the network applet didn't list the wireless networks, so I considered going with wicd, but all it needed was a little refresh with iwlist. 

Thank you!

---

### Post by azdavef on 2008-06-07
This is really a great how to and my son's new laptop if working really well.  I have two minor issues:
WICD doesn't auto connect to the identified network.  The Sessions entry we have is /opt/wicd/tray.py
Update Manager keeps asking to install restricted drivers after we decline to install them.
Are there any fixes?  These are really just quibbles.....:)

---

### Post by Trebawa on 2008-06-07
I did all this and... it works!  However, when I rebooted my computer, I had to reinstall the driver- until I did, ```
sudo modprobe ath_pci
``` returned ```
FATAL: Module ath_pci not found.
``` After reinstalling it everything works fine, though.  I wish I didn't have to do that every time.  Apart from that, though, it's great with WICD.

---

### Post by lazydesi on 2008-06-08
i reinstalled madwifi-2756 and installed 3366 my wireless is not showing up

---

### Post by braveerudite on 2008-06-08
Here is the answer to all your prayers.  Finally!!! a super simple method that will works 100% with Ubuntu 8.04 “Hardy Heron” 64bit and Atheros AR2425 (AR5007EG) chipset. No more the need ndiswrapper or even Wi-Fi Radar and WICD to get secure (WPA2,WEP) connection working.  You can just keep the default Ubuntu wired and wireless network manager because now it just works with no problem. 

Make sure you go to System ->Administration ->Hardware Drivers and disable Atheros (HAL) & Atheros support and reboot before you follow the steps on the guide.  At the end of the guide you'll see that it will ask you to re-enable them again and reboot.

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

Thank the guy that posted the guide last night by clicking on his Gold star with a blue ribbon on the right.

---

### Post by beN..87 on 2008-06-08
> **lazydesi said:**
> i reinstalled madwifi-2756 and installed 3366 my wireless is not showing up

you need to UNINSTALL the 2756 patch before installing the 3366 patch INSTEAD

sudo bash
cd madwifi2756
make uninstall
tar -xvzf madwifi3366
cd madwifi3366
make uninstall
make clean
make
make install

make sure you have the restirced modules off,
install wicd and check it's preferences are set properly -- all the instructions for this are on previous posts there for you to read

---

### Post by bluester on 2008-06-08
> **azdavef said:**
> This is really a great how to and my son's new laptop if working really well.  I have two minor issues:
WICD doesn't auto connect to the identified network.  The Sessions entry we have is /opt/wicd/tray.py
Update Manager keeps asking to install restricted drivers after we decline to install them.
Are there any fixes?  These are really just quibbles.....:)

Update Manager is trying to update the restricted drivers you still have installed. Try this:

"sudo apt-get remove linux-restricted-modules linux-modules-generic Jockey"

I too have been searching for a solution to enable reconnect.
It is not a big deal.... I rather reconnect after logon, or before, rather than launch wicd, select hidden network, type in my essid, and once it is displayed, click on connect. My settings are saved as I am not required to retype in my password (this was done during my initial setup in the preferences option).
Anyway, if you find something, do not hesitate to post! Inquiring minds need to know :popcorn:

---

### Post by beN..87 on 2008-06-22
nicedude! nightmare!! all was working fine and dandy last time i did this --- somehow i got it to work with no white screen of death after disabling linux-restricted-modules --- but i've just reinstalled my ubuntu after having some prolems -- fresh install

now when i follow you method disabling the restricted modules - i reboot and get white screen of death upon login

my thinking is that ATI proprietry drivers needs the restricted modules, that the whole point of it right??

anyway im using the same method as i did last  time when it worked - yet now it wont - im 100% im doing everything right

anyways can anyone help out with diagnostics / or has anyone found out what restricted modules can 100% be removed or which ones are needed for ATI ?

im really puzzled - same method - differing resluts 

any ideas appreciated!

---

### Post by ddg on 2008-06-23
Hi,

I got an error message when trying to move the file from desktop to home folder.
Here is the output:
 mv -f ~/Desktop/madwifi-nr-r3366+ar5007 ~/madwifi-nr-r3366+ar5007mv: cannot stat `/home/raras/Desktop/madwifi-nr-r3366+ar5007': No such file or directory

Actually I managed to get my wireless working by copying manually the madwife driver from desktop to home folder.
After that I follow the instruction you gave. 
After finishing wireless driver installation i could see the wicd manager and I got the wireless working but after installing the nvidia driver the wireless device was gone. I could not see anymore from the network.

Please give some more tips.
Regards,
ddg

---

### Post by ddg on 2008-06-23
Hi Nicedude,

I spent few hours yesterday following your steps.
I have Acer 4520 with atheros 5007 and nvidia GE 7000M.
First I installed the wireless driver and I got the wicd manager and I can see the wireless device in the network (System > Administr
ation > Network). But after installing nvidia driver I lost the wireless device, the wicd manager still there.

Please give more some tips.
regards,
ddg

[QUOTE=nicedude;4969968]IF YOU FOLLOW MY MADWIFI WAY YOU WILL HAVE TO REMOVE MULTIPLE THINGS FROM YOUR UBUNTU INSTALL WHILE THIS IS SAFE TO DO ITS NOT A SIMPLE CLICK CLICK FIX - EVERY COMMAND I GIVE IS WRAPPED IN QUOTES DON'T INCLUDE THE QUOTES JUST WHATS INSIDE THEM - I REMOVE THE RESTRICTED DRIVER MANAGER & LINUX RESTRICTED MODULES SO IF YOU USE NVIDIA OR ATI GRAPHICS ADAPTER YOU WILL NEED TO REINSTALL DRIVERS FOR THEM YOURSELF AS THE RESTRICTED MANAGER HANDLES THAT BY DEFAULT - READ THIS FULLY BEFORE EVEN STARTING SO YOU CAN UNDERSTAND WHAT IS REQUIRED - YOU MOST DEFINITELY WILL NEED ADMIN PRIVILEGES TO USE THIS GUIDE - PLEASE READ UP ABOUT INSTALLING YOUR OWN GRAPHICS DRIVERS AS IT WILL BE REQUIRED IF YOU HAVE A NVIDIA OR ATI CARD, ENVYNG MIGHT WORK TO INSTALL THE GRAPHICS DRIVER FOR YOU BUT IF NOT YOU WILL HAVE TO USE THE DRIVER PACKAGE DIRECT FROM NVIDIA OR ATI.

---

### Post by beN..87 on 2008-06-24
> **beN..87 said:**
> nicedude! nightmare!! all was working fine and dandy last time i did this --- somehow i got it to work with no white screen of death after disabling linux-restricted-modules --- but i've just reinstalled my ubuntu after having some prolems -- fresh install

now when i follow you method disabling the restricted modules - i reboot and get white screen of death upon login

my thinking is that ATI proprietry drivers needs the restricted modules, that the whole point of it right??

anyway im using the same method as i did last  time when it worked - yet now it wont - im 100% im doing everything right

anyways can anyone help out with diagnostics / or has anyone found out what restricted modules can 100% be removed or which ones are needed for ATI ?

im really puzzled - same method - differing resluts 

any ideas appreciated!

turns out going into synaptic and straight up removing all the linux resticted-modules packages disables your proprietry drivers --- but it also disables your graphics drivers -- just go to Restricted Driver Manager and disable your wireless ones only - and your graphics ones should be just fine.... with no white screen of death

all the same, with a little tweak here and there , great guide!

---

### Post by videoordvd on 2008-06-26
Hello there,

Thanks so much for your excellent howto on getting the madwifi drivers to work in hardy. Unfortunately my wireless card is still not working even after following all of your steps.

I have included the output of my wireless status commands below. I know the atheros card is quite powerful as I had it set up perfectly in gutsy, but I'm now quite frustrated as the update to hardy seems to have clobbered everything. Any help would be most appreciated.

Thanks again!

lspci:
```
[me@host:~]$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

iwconfig:
[me@host:~]$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:"myessid"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:5418  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

iwlist ap:
[me@host:~]$ iwlist ap
```
lo        Interface doesn't have a list of Peers/Access-Points

eth0      Interface doesn't have a list of Peers/Access-Points

wifi0     Interface doesn't have a list of Peers/Access-Points

ath0      No Peers/Access-Point in range
```

---

### Post by beN..87 on 2008-06-26
> **videoordvd said:**
> Hello there,

Thanks so much for your excellent howto on getting the madwifi drivers to work in hardy. Unfortunately my wireless card is still not working even after following all of your steps.

I have included the output of my wireless status commands below. I know the atheros card is quite powerful as I had it set up perfectly in gutsy, but I'm now quite frustrated as the update to hardy seems to have clobbered everything. Any help would be most appreciated.

Thanks again!

lspci:
```
[me@host:~]$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

iwconfig:
[me@host:~]$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:"myessid"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:5418  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

iwlist ap:
[me@host:~]$ iwlist ap
```
lo        Interface doesn't have a list of Peers/Access-Points

eth0      Interface doesn't have a list of Peers/Access-Points

wifi0     Interface doesn't have a list of Peers/Access-Points

ath0      No Peers/Access-Point in range
```

if yu have upgraded o hardy and that is what has caused problems, my advice would be;

using synaptic remove

network manager
network manager gnome

then 

sudo bash
cd madwifi (any installations or patches including 3366)
make uninstall
rm -r madwifi

then uninstall wicd network manager

reboot

get the 3366 patch
get latest stable wicd network manager

install wicd network manager first

change preferences of wicd to list WPA supplicant as madwifi
make sure ath0 and eth0 are listed as interfaces

then

sudo bash
tar -xvzf madwifi 3366
cd madwifi 3366
make
make install
modprobe ath_pci

gedit /etc/modules

add those lines
ath_hal
ath_pci

reboot

open wicd mananger and click refresh - make sure your wireless router is ok

---

### Post by videoordvd on 2008-06-26
Thanks for your help Ben. Sadly I still can't see my opened wireless network :cry:. Looks like I'll have to backup my home directory and try this howto on a fresh install.

EDIT: Followed this guide on a fresh install and it worked like a charm - thanks again!

---

### Post by scher2jb on 2008-06-27
so im satified with the nvidia drivers that i have, do i have to do the first step to make this work or can i skip right to the madwifi steps?

---

### Post by beN..87 on 2008-06-27
> **scher2jb said:**
> so im satified with the nvidia drivers that i have, do i have to do the first step to make this work or can i skip right to the madwifi steps?

just go to your restricted driver manager (has a padlock sign thing under administration)

you only need to disable the Aetheros wireless restricted drivers, no need to disable all of them under synaptic by removing linux-restricted modules, that also disables your graphics cauding problems. As long as you dsable your wirelees restricted modules before the madwifi install you should be good to go.

---

### Post by noway2 on 2008-06-30
Nicedude, 

Thank you for taking the time to make this post. You definately get a :KS  I found it to be of extreme value while attempting to configure a new system with an AR5007 wireless card and an Nvidia GeForce 7000M graphics card.  

I struggled for a couple of days trying to get both of these items working and no matter what I tried I could get either the video OR the wireless, but not both.

After following your instructions, to the letter, it worked flawlessly.

Prior to using these instructions, I had tried several different approaches including Envy, NDISwrapper, getting the latest drivers from Nvidia, etc.

---

### Post by scher2jb on 2008-07-01
well to the poster above i think i have the same problem that you had.  i followed the steps to a T, and got my wireless card to work.  Unfortunately now the system does not recognize my graphics card which is a gforce 7000m with 610m chip set.  if anyone wants to make sure what im saying is true the computer i have is a compaq f767nr. im sure its a 7000m, the other part im not sure of.  i have installed both driver 173.08 to no success, then tried 169.12 also no success.  then i tried 173.14.05 which i found online hoping it was the most up to date.  all to no avail.  each install says it is successful, then i reboot and does not work.  "piece broke, engine dont go"  let met know if anyone can help.  just so you know the default jockey program worked great for the nvidia card, so if that would be the easiest fix to go back to i could live with that. thnks

p.s.  id like someone to clarify one line for me;
step 4 of the graphics card portion that is to be done after the madwifi portion.  quote "now just add the following to the bottom of all things displayed in this file- nvidia"  does that mean add that multiple times after each individual entry, or just add once at the bottom of all the entries?

---

### Post by dmlxyz on 2008-07-02
NICEDUDE,

I have an Acer 5315-2153 laptop. I am running Ubuntu Ultimate 1.8 which is the 8.04 Hardy for those wondering. Your methods for AR5007 installation worked for me without a hitch. My network manager works fine. Thanks for the help. I had tried numerous methods with no results. You are one of the reasons I like Linux so much.

keep up the good work,
dmlxyz

---

### Post by unlocalhost on 2008-07-03
Thanks nicedude

I have a sony vgnnr220e/s

i ran into a small hangup and that is for some reason build-essential was not a part of my install.  I found my solution for adding this off the ubuntu CD on another thread, and after sucessfully getting my laptop on wifi noticed you have set instructions posted later on in this thread.  So shame on me for not reading on, but I am happily running my laptop with ubuntu now.  

:guitar:  you rock

---

### Post by laxrick on 2008-07-06
Someone please help! I've read this entire thread and still can't get my internet working through wifi. I've had my wifi working before, but it won't seem to pick up my router, and I won't know until later today if it is still picking up ANY wifi. I do know that my router, Netgear WGR614v9t, works fine because I have a Wii and a PocketPC hooked up to it perfectly.

IWLIST SCAN says:

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results


LPSDI:
> 01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)



Nothing seems to be detected... everything that could be a simple fix I have more than likely tried, like checking Wicd to see if madwifi is the driver and that I'm set to ath0, and things like that. I also have ath_pci and ath_hal loading from "modules" as stated in the guide. Jockey and linux-restricted-modules have both been removed.

Any ideas? I'm fresh out...

---

### Post by scher2jb on 2008-07-07
so the mad wifi worked, and i have connected through the wifi.  but since i uninstalled the restricted drivers for my graphics card, that no longer works.  ive followed the install for my nvidia card more than once and with different recomemded drivers, but to no avail.  my computer is a compaq f767nr with a nvidia geforce 7000m card.  would someone tell me the correct drivers to use, and confirm that the install given above is correct.  i believe it is.  im just tired of tinkering and rebooting.  i guess i better get used to it if im going to stick with linux.

---

### Post by beN..87 on 2008-07-08
> **scher2jb said:**
> so the mad wifi worked, and i have connected through the wifi.  but since i uninstalled the restricted drivers for my graphics card, that no longer works.  ive followed the install for my nvidia card more than once and with different recomemded drivers, but to no avail.  my computer is a compaq f767nr with a nvidia geforce 7000m card.  would someone tell me the correct drivers to use, and confirm that the install given above is correct.  i believe it is.  im just tired of tinkering and rebooting.  i guess i better get used to it if im going to stick with linux.


there is a solution - i also found removing all the restricted modules in synaptic was a bit too harsh on all the OTHER restricted modules such as graphics 

instead of removing JOckey and linux-restricted-modules in Synaptic - simply go to your restricted driver manager (Jockey) in administration and untick the boxes for your restricted wireless drivers - leave the graphics one alone , reboot then carry on installing madwifi and wicd

---

### Post by scher2jb on 2008-07-08
thanks ben, ill give it a try.

---

### Post by jerryfleming on 2008-07-10
short version: wireless network scanned, but connection failed (not because of WEP key)

I am on a Gentoo box. Since my hardware is exactly the same as discussed here, I follow the instructions. Everything went smooth until I came to hhclient part. I got "No DHCPOFFERS received."

Please help me.

(see attachments for detailed logs)

---

### Post by Hawkeye004 on 2008-07-12
I followed the instructions, and they worked well, but I have discovered a slight hitch. I have an ATI Radeon X1200 graphics card and and Atheros AR5007 in my laptop. When I remove the restricted modules (and jockey, although I think that has less to do with it) and follow the wireless setup my screen is blank after the reboot and login. I reonfigured my XServer to get the screen back, but at the cost of the hardware's graphics acceleration. Thank you in advance for any ideas.

---

### Post by beN..87 on 2008-07-12
> **Hawkeye004 said:**
> I followed the instructions, and they worked well, but I have discovered a slight hitch. I have an ATI Radeon X1200 graphics card and and Atheros AR5007 in my laptop. When I remove the restricted modules (and jockey, although I think that has less to do with it) and follow the wireless setup my screen is blank after the reboot and login. I reonfigured my XServer to get the screen back, but at the cost of the hardware's graphics acceleration. Thank you in advance for any ideas.

i had the same problem - instead of removing linux-restricted-modules and Jockey ect from Synaptic -- instead use Jockey (restricted driver manager found at administration menu) to remove restricted driver support for your wireless

for anyone else experiencing graphics drivers problems just take note that just straight up removing all restricted driver support will hack away your restricted graphics also - better to use jockey for what it is intended

---

### Post by kirsch92 on 2008-07-13
nicedude,

this worked like a charm under Mint 5.0 Elyssa as well.
I just disable HAL and Atheros driver by unchecking the boxes in the restricted driver manager rather than removing the whole thing.
You rock!
Every other madwifi solution I tried failed.

---

### Post by seshakri on 2008-07-13
Thanks a lot for your post. This helped me immesely. Just followed your steps and it worked. Thanks a lot.

---

### Post by tiltus on 2008-07-13
thnakyou very much for your help! This was my first insight into linux, and without this guide i may have turned away!

---

### Post by gibbyn on 2008-07-13
Thank you for the detailed notes on how to set up the Atheros AR5007 under Hardy 8.04.  I had several days of work trying other methods until I found this.  

One problem I ran across in the note.  The following command needs to have a character changed.  The  (in the "from" file name) "ng" was needed in place of the original "nr".  It seems the file I downloaded had a file contained inside that didn't match the file name of the tar file.  I used this command:
sudo mv -f ~/Desktop/madwifi-ng-r3366+ar5007 ~/madwifi-nr-r3366+ar5007

Also I ran into confusion earlier since my HP Pavilion dv9815nr reports the chipset of the wireless with a "AR242x" from the lspci command.  The AR242x is the Ar5007, apparently, but I had little clue of this, at first. 

Things that I tried that didn't work for me: 1. 64bit Ubunto and my wireless chipset (a known problem now). 2. ldiswrapper - I assume the problem gets back to the fact that I didn't know the AR242x is the AR5007 (so perhaps I used the wrong driver).

I'm happy now and so I'll try the video driver install too.

---

### Post by jeremyswalker on 2008-07-14
You obviously know what you are talking about, and your tutorial is very thorough. However, why are you disabling the restricted drivers then reinstalling them? I have the Atheros AR5007 in my laptop, and all I needed to do was compile the driver and load it. It simply replaces the driver that the restricted driver manager already loads. Perhaps I am missing something, but this worked fine for me. I didn't edit the modules file either. Just by compiling and loading or restarting, I have working wireless. Perhaps this is just a fluke, I don't know. Anyway, I am glad that there are folks like you to help Linux users getting there systems to perform properly.

---

### Post by pjcvdpol on 2008-07-15
Bloody hell.... this guide actually works! thank you! Kudos to you and if I can ever do anything... I grow rosehips in the netherlands and I am a photographer, see if this is of any use to you.... ([www.rozenbottels.nl](www.rozenbottels.nl) / [www.petervandepol.com](www.petervandepol.com) )

---

### Post by markcoatsworth on 2008-07-17
WOW!! I'm using the new Acer Aspire One mini-laptop (just hit stores last week) so there's no info online with wifi instructions for Ubuntu. Your guide worked perfectly. Thanks again!!

---

### Post by cypheroptic on 2008-07-30
If someone could help with this issue, I would GREATLY appreciate it. First off I have Ubuntu 8.04.1 32bit installed and working with an atheros wifi, internal to laptop.

In normal aspects it scans APs, connects, etc, everything is normal. I have the madwifi compiled and installed with the usual HAL process disabled. I have read that I need be using a patched madwifi driver/setup but everytime I try to download it, all it has is a README file that says go to such site and use this driver instead, which is not the patched version I would guess. I think this is part of the issue. 

My final outcome I looking for is to have this setup and have kismet working properly. I have also installed the associated packages for kismet, madwifi-tool, etc.

While trying to launch kismet with the scripts from niceguy, I get the following error: FATAL:  Could not connect to localhost:2501.

lspci:
```
14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Cyberia"  Nickname:""
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1C:10:BB:D3:61   
          Bit Rate:24 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-35 dBm  Noise level=-96 dBm
          Rx invalid nwid:1686  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

If you need any other posts, conf info or what not let me know...

Thanks in advance

---

### Post by ethos101 on 2008-07-30
I had the same problem.  I think I remember what I did to fix it.  I went into my madwifi folder and ran "sudo make uninstall" then rebooted and did the make, make install, modprobe ath_pci commands once again.

I think what causes this is running the make install too many times creating too many wireless extensions or something confusing the setup.

Correct me if I'm wrong, but I think thats all i did.  Let me know if that helps.

---

### Post by cypheroptic on 2008-07-31
@ ethos101: That would hold true for me too I believe. I had the wifi setup and running after first install, then ran some other installs and when I rebooted wifi was down. I just simply re-ran the wifi install again, I did not uninstall, reinstall in a proper manner. I'll try your fix when I get home later and let you know the results.

Thanks.

---

### Post by cypheroptic on 2008-07-31
@ ethos101: I tried your recommendation. 

> I went into my madwifi folder and ran "sudo make uninstall" then rebooted and did the make, make install, modprobe ath_pci commands once again.


This did not remedy the issue. I'm still getting the error...

```

FATAL:  Could not connect to localhost:2501.

```

I thought it maybe a port issue, so a disabled the ufw for a few moments and tried again, this also did not resolve the issue. Any other thoughts or ideas?

---

### Post by ethos101 on 2008-07-31
Possibly reboot the machine before you install, after uninstalling?

I remember when I ran the airmon-ng start wifi0 I had multiple VAP's running when there should only be 2, wifi0 and ath0...  That's what clued me in.

---

### Post by tehbillick on 2008-07-31
Thanks so much for the helpful guide.  It nearly worked flawlessly, with 2 exceptions...

First, I had to add the ath_ entries to /etc/modules and reboot as I got a fatal error when trying to modprobe ath_pci.  I should have copied and saved the failure, but hey, at least I could SEE ath0 after the reboot.

Second, I don't seem to be able to use Wicd.  I installed it as per the instructions, and it seemed to function until the reboot.  Then I couldn't open it.  It is still there in the Applications->Internet menu, it just never opens when I pick it.  This was a major problem because once Wicd wiped out my default network manager, I lost my wired connection too.  I also don't seem to have dhcp capability, so I had to manually define my network settings via the command line.  

My experience is completely with Solaris, and the apt get commands are a little foreign from pkgadd that I'm used to.  I have to admit, though, that Solaris is not friendly to my laptop hardware, which is why I'm moving to Ubuntu....


Thanks again!

---

### Post by cypheroptic on 2008-08-01
@ ethos101: I uninstalled, rebooted, reinstalled, rebooted still get the same error as previously stated.

> 
I remember when I ran the airmon-ng start wifi0 I had multiple VAP's running when there should only be 2, wifi0 and ath0... That's what clued me in.

How do I check for this. I'm using the scripts posted by niceguy for starting and stopping everything.

Thanks

---

### Post by ethos101 on 2008-08-01
I type: sudo airmon-ng start wifi0
And would get wifi0, ath0 and ath1 or even more...

I'm pretty sure all I did was uninstall it to start from scratch...
Maybe this: sudo airmon-ng stop ath0
or before that stop ath1 if you need to.  Stop them all untill you just have wifi0. then just run it once.  I may have had to do that.

Post the feed you get once you type "sudo madwifi-ng start wifi0"
and, iwconfig
and ifconfig

I'm no expert but I'm starting to get some experience.  I've finally been able to crack a few WEP keys after lots of reading.  WITH PERMISSION of course (mine and my girlfriends AP's).  Now I need a new project.

---

### Post by cypheroptic on 2008-08-02
I justed wanted to drop a line and say thanks to everyone for their help. I read through the guides and found were my issues were and was able to get everything installed and running without issue or error.

My resolution was to simply RTFM. I was a bit more patient and read through everything one by one, went through it all and found the errors I made. The info, scripts and guides are great and work as written, providing you read and follow them correctly.

Thanks

---

### Post by nicedude on 2008-08-11
As for right now don't use this guide - i have been absent the forums for like 2 months and the drivers listed are no longer correct for the latest kernel - i will be looking this guide over to see any changes i need to make. I am planning to upload a newwer pre patched driver to rapidshare and post a link for everyone that needs it. So give me 1 or 2 days to get all that done ( i am going to try to get it done by monday night but dont want to promise ) and i will update this guide accordingly

sorry to be absent so long but i am back to help any who need it

sorry again to all who needed help and couldnt get it

---

### Post by rfincher on 2008-08-11
[FONT="Arial"][/FONT]
Hi,
The following somewhat lengthy comments are about my efforts to get my Compaq C731TU laptop communicating wirelessly with my D-Link DI-624 router. I'm completely new to Linux OS's, my first experience being the installation of Ubuntu 8.04 from a magazine DVD about 3 weeks ago. I've learned that just about everybody has trouble getting their Atheros AR5007 chipset talking with their routers - there are many hundreds of posts on the official Ubuntu threads as well as others - some have had quick success but most have had to perform many tweaks before they got a working system.
My laptop has a single-processor Celeron 540 with 2GB RAM, an 80 GB drive, Windows Vista Home Basic pre-installed, and it cost about AUD550 a few months ago. It now has the Grub boot menu on start-up, allowing either Vista or Ubuntu 8.04 to be selected.

So here is what happened.

1. I installed U804 with the 2.6.24-16 generic kernel from the DVD (July 2008 copy of APC magazine).
2. Successfully activated wireless (WLAN) using madwifi-ng-r2756+AR5007, and successfully connected to internet wirelessly.
3. The "Hardware Drivers" screen confirmed Atheros HAL and Support for Atheros 802.11 wireless LAN card were enabled and in use.
4. The "Network Settings" screen showed the WLAN connected as ath0. Network name was di624, password type was WEP key (hexadecimal).
5. About 240 MB of Ubuntu upgrades were downloaded via WLAN and installed. With the new 2.6.24-19 generic kernel now installed, the WLAN stopped operating, but was restored by re-applying the above madwifi patch.
6. After about a week U804 became unstable and froze intermittently. So I purchased another U804 dual 32 /64 bit DVD with the Linux Magazine Special 01/2008 and did a fresh install of U804 from this new DVD.I also tried to install the Windows Vista driver for the AR5007, using NDISWRAPPER.
7. The Windows driver was oem12.inf, but it failed to install under ndiswrapper - error message "Invalid Driver". 
8. Successfully removed the invalid driver and ndiswrapper from the U804 drive, and re-installed the madwifi-ng-r2756+ar5007 patch above.
9. This time the patch was unsuccessful, and the Atheros WLAN was not set up. The "Network Settings" screen showed no sign of ath0, just the wired ethernet connection eth0.
10. However, the AR5007 was still working perfectly under Vista.
11. To cut this long story short, I tried a different and newer patch from the madwifi site. First I disabled the Atheros drivers via the "Hardware Drivers" screen. Then went to the madwifi hal 0.10.5.6 site and downloaded the latest patch using Terminal code as follows:

sudo apt-get update && sudo apt-get install build-essential
wget [http://madwifi-hal-0.10.5.6-r3835-20080810.tar.gz](http://madwifi-hal-0.10.5.6-r3835-20080810.tar.gz)
tar xvf madwifi-hal-0.10.5.6-r3835-20080810.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo make
sudo make install
sudo modprobe ath_pci
sudo reboot

12. Then re-enabled the 2 Atheros drivers via the "Hardware Drivers" screen, and rebooted again.
13. Could now see ath0 Wireless Connection in Network settings screen, but internet connection not yet working.
14. Under System>Administration>Network>Hosts, changed alias of 127.0.0.1 from "hosts" to "di624" (the essid code for my router).
15. Ran iwconfig to discover "Rx invalid nwid:1" in one of the lines - assumed there was a network id error.
16. No internet yet, but now I could access the D-Link router Wizard via the Mozilla browser and [http://192.168.0.1](http://192.168.0.1). So I re-ran the Wizard, changing nothing, and rebooted the laptop.
17. The error in iwconfig had now gone - RX invalid nwid:0.
18. With much relief, the internet connection fired up, and is working well. What's more, it fires up again after a machine reboot.
19. The "Suspend" shutdown option works too, but not  "Hibernate" - it seems there is insufficient swap space at 384 MB on the HDD.
20. I made sure the WLAN on/off push-button on the laptop was ON at all times. Unfortunately the button's light stays orange instead of blue when the WLAN is on.

This tale doesn't tell of the frustration in reaching a solution. But I hope you'll be encouraged to persevere when things don't go right. I learned a lot about the Ubuntu system, the community, and the philosophy of free and open software as I worked my way through all this. I'm now looking forward to making Ubuntu my preferred OS. (Now if someone could just tell me how to get Quicken running under Ubuntu.....)
Good luck and thanks for all the many caring people whose posts have helped me so much.
Rob

---

### Post by ethos101 on 2008-08-12
I'm not sure what the purpose of step 14 is...  I never renamed the loopback alias, it should be "localhost."

Anyways, I'm using the madwifi-ng-r3366+ar5007 version and it's running flawlessly.  I tried updating to madwifi-hal-0.10.5.6-r3772-20080716 but it was intermittent at best so I went back to the 3366 version.

Like you I had somehow undid my wifi setup after updating the kernel but all i did was re-install the 3366 drivers and it worked great again.

Try the 3366 version here: [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz]("http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz")

Don't forget to add these two lines to /etc/modules:
ath_hal
ath_pci

Hope this helps. :D

---

### Post by tc3157050 on 2008-08-12
Does anyone has problem of downloading the driver using 
[http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz) ??
I got the tar file with only a "README" inside as
________________________________________________________________________
You most likely downloaded this tarball since you are looking for a version of MadWifi which supports the AR5007 chipset family, which is for example used in the EeePC.

However, since you've downloaded this tarball, you've followed outdated
instructions. The code that this tarball once contained is now obsolete.
Please follow these instructions to enable your AR5007-based WLAN device:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

If you have any questions about it, please contact our regular support
channels:
[http://madwifi.org/wiki/Support](http://madwifi.org/wiki/Support)

Thanks.
________________________________________________________________________

Is there a alternative version that i can use?

---

### Post by nicedude on 2008-08-12
PLEASE SEE POST #1 AS MY GUIDE HAS BEEN UPDATED AND THERE IS A WEB LINK TO THE NEWEST DRIVER PUT TOGETHER BY ME TODAY. IT IS AIRCRACK PATCHED AND INJECTION TESTED SO USE THAT, AS THE OLD DRIVER MIGHT NOT WORK RIGHT AFTER RECENT KERNEL UPDATES. 

Do not do what the guy a few posts up did and change your hosts file settings to the name of your router. That is not needed ever and while I couldn't say for sure what any negetive side affects are, I would guess that for starters it would not work anywhere but with that router so this is not what 98% of people would want to be doing.

PLEASE JUST USE MY OR SOMEONE ELSE'S GUIDE AND NO MATTER WHICH GUIDE YOU USE - READ IT AND FOLLOW IT. THE NEW DRIVER AT POST #1 OF THIS THREAD WORKS 100% WITH KERNEL 2.6.24-20 INCLUDING MONITOR MODE & PACKET INJECTION 


goodluck to all with your AR5007

nicedude

---

### Post by nicedude on 2008-08-12
Wow I have been absent these forums for over 1 1/2 months and I just read back through some of everyones comments and I am overjoyed that so many people found my guide helped them out. I am glad to have helped some of you stick with Linux and tough it out through the learning process instead of giving up and returning to the dark side of the force :-) . The Emperor must not be very pleased :-)

AWESOME 


glad to be of service to a nice community,
nicedude

---

### Post by rfincher on 2008-08-12
Heh Nicedude,
Thanks for the update - it came about 48 hours too late for me I'm afraid. Like another guy, I found the r2756 tarball was only 500 odd bytes, not a few MB as it was the first time I downloaded it, so I used the r3835 snapshot from madwifi. This seemed to get me over the problem of not being able to see ath0 on the Network Settings screen. As for changing the alias of the 127.0.0.1 address from localhost to di624 - that was a move of desperation which I now discover had no observable effect here, but could well have stuffed up my chances of connection away from home base - as you observed. I've since changed the alias back to localhost and everything still works. BTW I had no intention in my earlier post of suggesting your install instructions were in some way no good. Although they didn't work for me, I think that was because my r2756 download was not what it should have been, and I got nowhere. Maybe it was just inappropriate for me to have posted at all - I sure didn't mean to offend or confuse.
Rob

---

### Post by nicedude on 2008-08-12
To everyone 

I screwed up last night and posted a link to a driver that didn't work right, I thought I removed the modules and reloaded new ones before testing but I guess sleep deprivation took its toll. The POST #1 driver has been changed again just now and works for sure now, its the one I have been using for several weeks. Injection tested and working.

To rfincher 

I in no way was offended by your post nor was I trying to be rude to you. I just wanted to let everyone know that your steps are not the way to do this so that no one would try using them as such. I would strongly suggest you rename your localhost to its original name and figure out whats wrong another way, since I believe all you will be able to connect to is that one router. I also don't know what other negative effects this renaming could have on your system ( either security wise or function wise ) as I have never seen anyone have to do this in either Windows or Linux. I am super happy you are learning and figuring stuff out but I just want you to have a safe and fully functional system. 

Yes the drivers from my guide were old and I just hadn't been around these forums for awhile to update them, but I finally did when I saw people were still using it, My bad for not paying attention.

The main and only bonus for someone to use my driver I have now posted at post #1 is to allow packet injection on your adapter, which the regular Madwifi drivers won't allow. If you don't care about packet injection ( used for hacking wifi with aircrack-ng ) then the standard Madwifi drivers from their site will serve you just fine. I just know allot of users here would like to learn about wifi hacking and drivers that support injection is the biggest stumbling block I know of ( outside of technique of course ) for newcomers who might be interested in learning Wifi computer security or to test their own home/business security on their own.

To test if packet injection is working for you, you can run the following.
sudo aircrack-ng -9 ath0

Hope this helps you understand I was just wanting to warn people to not rename their localhost.

Good luck with your Ubuntu adventure

nicedude

---

### Post by rfincher on 2008-08-13
To nicedude,
Many thanks for your helpful reply, and excellent instructions guide. I do not understand the concept of packet injection, so I guess I'll skip that for a while. I did test to see if it worked, but it didn't!! From what I can see, there are many forums and posts where the old madwifi drivers are still listed as the way to go to get AR5007 working, and to date their hosts have not taken steps to update their threads. Not so here :) My Ubuntu adventure begins in earnest tomorrow as I'll be using my laptop to make a presentation to a computer self-help group that I help to run, and it'll be all about Ubuntu apps.
Thanks again
Rob

---

### Post by Malachai33 on 2008-08-13
I try to follow this guide to the letter, have even printed it out so I can read it while in linux since my wireless isnt working yet.  I run into a problem early on in the tutorial, where it says to add the package "build-essential".  There is no such critter as "build-essential" found.  I just downloaded u804 last night, so thought it should be there.  Since I do not have build-essential, I am assuming that is why I run into problems when I run the sudo make in step 5.  Any advice on what I may be missing here?  I would love to be able to get rid of Vista and run Ubuntu full time, but, until I can get my wireless working, this is only a dream.

Malachai

---

### Post by nicedude on 2008-08-13
I am guessing you looked in add/remove programs and didn't find them, thats ok because they are not there :-)  Most software can only be found via the synaptic package manager under SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER


but for now here are two commands to install what you need 

sudo apt-get install build-essential

sudo apt-get install make


Open a terminal window ( Applications -> Accessories -> Terminal ) and then paste each of those, one at a time and press enter and it will install them.

hope this helps and just ask if you need more help, when/if you do need more help please tell me as much as you can about your computers model and hardware as it helps me to do so, Thanks

nicedude

---

### Post by ethos101 on 2008-08-14
> **nicedude said:**
> ...
To test if packet injection is working for you, you can run the following.
sudo aircrack-ng -9 ath0
...

Do you mean:
sudo aireplay-ng -9 ath0
??
:D

Confirmed packet injection is working on KERNEL 2.6.24-19...

Will check WPA when I get home.

Thanks again.

---

### Post by nicedude on 2008-08-14
Yes aireplay-ng not aircrack-ng I type faster than I think sometimes :-)

---

### Post by karachuonyo on 2008-08-14
I have a Phillips pci card Atheros AR 5413 (02:00.0 0200: 168c:001b (rev 01)) and this one works OOTB with the restricted drivers, using the network manager. The only problem I'm seeing is that the power and activity lights on the card do not come on at all. Not critical but anyone knows how to get my cool lights :guitar: again.

---

### Post by Malachai33 on 2008-08-14
> **nicedude said:**
> I am guessing you looked in add/remove programs and didn't find them, thats ok because they are not there :-)  Most software can only be found via the synaptic package manager under SYSTEM -> ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER


but for now here are two commands to install what you need 

sudo apt-get install build-essential

sudo apt-get install make


Open a terminal window ( Applications -> Accessories -> Terminal ) and then paste each of those, one at a time and press enter and it will install them.

hope this helps and just ask if you need more help, when/if you do need more help please tell me as much as you can about your computers model and hardware as it helps me to do so, Thanks

nicedude

I am running a Sony Vaio VGN-NR220E.  I found another site online that said it was possible to put Ubuntu on this machine, so thought I would give it a shot.  

When I went to install build-essential, I was in synaptic, not sure why it didnt come up, but I will try to run the command you gave me to get it in there.

thanks for all your help nicedude! :D

Malachai

EDIT:  I tried running the sudo apt-get install build-essential and got the message "E:  Couldn't find package build-essential".  Not sure why everyone else seems to be able to get this, but this is twice now that I have installed from wubi and received the same result.

As far as machine specs, I pretty much have the same thing as the other site I found, which is located 
[http://aqeeliz.com/2008/06/02/linux-on-sony-vaio-vgn-nr220e/](http://aqeeliz.com/2008/06/02/linux-on-sony-vaio-vgn-nr220e/) there.  One or two things are different, but, like his my video and audio work with no issues or changes necessary.

---

### Post by nicedude on 2008-08-14
I have no idea about using a WUBI install as that is a way to use Ubuntu from within Windows. There are negetives to using WUBI compared to setting up a proper dualboot machine ( assuming you have to have windows XP or Vista etc ) mainly such as speed ( you are running Ubuntu on top of Windows which greatly affects performance as I understand it, I don't know first hand as I wouldn't recommend and haven't used WUBI ). I guess I can support the idea of Wubi if it helps more people try Ubuntu but on the other hand I kinda think that if it harms Ubuntu's performance it might give people a wrong impression about what they would get with a full Ubuntu install and they could easily just use a live CD to try Ubuntu ( although using a live CD also reduces performance ). Also you should try checking your repository sources and make sure you have them all checked, except the CD one and the proposed one. As it might be a sources problem but I would think make and build essential should be available by default. I would like to know what you find out when you figure this one out ( just for my own knowledge/curiosity about WUBI ).

So if you like Ubuntu I would suggest using a gparted live CD or a Ubuntu live CD to resize your windows partition down to size ( say between 15GB-to-30GB ) and  then install Ubuntu to your hard disk ( 2GB SWAP partition + 15GB-to-30GB EXT3 partition for Ubuntu ) then do the rest the space on your disk as  a NTFS data partition and use the rest of your disks space on this, which will then let you store stuff on the data partition and access it from both Windows & Ubuntu so you can have your music, videos & documents available no matter which you boot to. Thats my way and it works great so its what I recommend :-)

If you ever want to setup a dualboot system then there are many guides on how to do this and if you get stuck I am more than glad to help as I have done this setup at least 10 times so I am pretty familiar with all the aspects of what is needed & what can go wrong ( as well as how to fix problems that occur ).

Hope this helps and let me know if you figure out why make & build essential are not available in WUBI.

---

### Post by Malachai33 on 2008-08-14
I tried the LiveCD once, but just burned another one as the first time it kept giving me an error of the cd already being in use...going to try it again...I had ubuntu installed on an old machine and loved it.

Here goes nothing! :D

Malachai

---

### Post by gaurang on 2008-08-14
hey nicedude ... your guide is :guitar: .... with its help, i was able to use madwifi for my atheros 5007 ...
err .. i have one question ... just like this guide .. can you write a little more about "how to use aircrack ?" ... 
i had followed one guide ...  [http://ph.ubuntuforums.com/showthread.php?t=528276](http://ph.ubuntuforums.com/showthread.php?t=528276) .. but its for some other wifi card ... so if you can make it for atheros .. it will be great help ..

again .. you guide was really helpful ...

thankx ....

---

### Post by ethos101 on 2008-08-14
> **gaurang said:**
> .. can you write a little more about "how to use aircrack ?" ... 

I learned everything I know about aircrack from the official tutorials here:
[http://www.aircrack-ng.org/doku.php?id=tutorial](http://www.aircrack-ng.org/doku.php?id=tutorial)

They are very detailed.

To get monitor mode I do this:
sudo wlanconfig ath0 destroy
sudo ifconfig wifi0 down
sudo airmon-ng start wifi0



nicedude, I'm working over WPA as I type.  So success as far as that goes.  :D

Someone said something about wifi lights not coming on.  Mine don't flash either (Acer Aspire 5720Z).  I considered it a bit distracting anyways.  BUT if anyone figures out how to get the lights on please do inform us, I think I'd rather have the light.

---

### Post by nicedude on 2008-08-14
Good to hear WPA is working for you, so it should work for others too. As far as the LED thing, I believe this is like Laptop special keys ( like Email & Web ) and the manufacturers don't release code to control these ( or maybe just the specs of how to, so others could fix it in linux ). So unless you find a guide for your exact laptop where some evil genius has found out how to do so then I think your sunk on that one ( I found one for my laptop's special keys but it looked like way to much work to get a couple extra buttons when I could instead use hotkey combo's & scripts ). So I will just have to live with no LED's or special keys, but no big deal.

AS FAR AS YOUR COMMANDS

To get monitor mode I do this:
sudo wlanconfig ath0 destroy
sudo ifconfig wifi0 down
sudo airmon-ng start wifi0

I do the same things with scripts in my nautilus scripts folder, so I can go from monitor to managed or fake my mac all in a few seconds. You can also launch your card in monitor with wlanconfig but either way it is the same.

---

### Post by gaurang on 2008-08-14
> 
I learned everything I know about aircrack from the official tutorials here:
[http://www.aircrack-ng.org/doku.php?id=tutorial](http://www.aircrack-ng.org/doku.php?id=tutorial)

They are very detailed...

thanks for the tip ... i don;t know why i was just wonder everywhere without going to "original" source ... i read it .. and it helped me to understand on important thing for which i was struggling since this morning .. its that .. " you can't do cracking unless there is already someone using it !!! " .. its because to crack wpa , it is needed to do 4 way handshake but before that we must "listen" communication between AP and another user, which is NOT possible in case of only one user like me :( ... man.. i am the only person who uses wifi .. all others a on LAN .. damn ... hey but i will keep trying :)

anyways ... ethos101 .. friend .. you helped me lot .. thanks a lottttttt ...

---

### Post by ethos101 on 2008-08-14
Cracking a wep without a client already connected is possible.  Far more complicated but possible.  I've done it but it's so much easier with a client.  :D

nicedude, I've never written a script for linux but I've thought about that.  Guess it's time to learn.  :D

---

### Post by gaurang on 2008-08-15
> Cracking a wep without a client already connected is possible. Far more complicated but possible.:confused: must be typo .. u mean to say WPA .. right ??

anyways .. ethos101 .. can you tell me how can i add dictionary in aircrack ?? because , i just followed their tutorial and at end to crack password we need to execute this ...

aircrack-ng -w password.lst -b 00:14:6C:7E:40:80 psk*.cap

now when i do so , it says .. "no such a file" .. but i see there is one file "password.lst.gz" in "examples" folder !!! :roll: ... is there any other way to execute this line ?? also , how can i add other dictionary , err i mean ,exactly in which folder i have to copy those txt files ?? 
i am soooooo eager to see this thing working and now i am stuck at the end :( ... i am sure that upto that line i did all correctly because , i was able to de-authenticate connected client ( i know this because, my desktop's winamp stopped playing shoutcast !!)

do you guys have any other suggestions ?? 

please help me out ...

---

### Post by nicedude on 2008-08-15
gaurang - he was correct in stating that cracking WEP without a client is possible, more than possible actually quite easy really depending on how the AP is set up, the only thing to stop you form cracking a WEP without a client connected is if the router has mac address filtering enabled and there are no clients connected. In that case you would need to wait till you can see a valid client connect, just so you can spoof their mac address so the router will talk to you :-)

As for WPA the aircrack command you listed is correct but you didn't unzip their password file and so the names don't match password.lst vs password.lst.gz which is a compressed file, so unzip the file and then you should have a file named password.lst which will let it work. Also the password file that comes with aircrack probably isn't that good since it no doubt will be small. There are much better password files out there, I have several including my super password file that is like 3GB so be sure to go find yourself a better one. I would suggest heading to the pirate bay and searching for the word "password" and you will find an "xploitz" password list which is authored by one of the moderators of the remote exploit forums which is a place to go learn about this stuff. Also you might want to google "rainbow tables" ( like a password list but works against non words as well ) and see if you can't find some for WPA although I think they will be harder to find and they are very big ( mine for 1000 most common essid's is 33GB in size so takes a minute to download :-) )

Also did you capture a WPA handshake with airodump when you did your deauth as that is what you need to do in order to have the info that aircrack will try to crack. 

hope this helps you figure this out, and act responsibly with the knowledge.

nicedude

---

### Post by stevenpusser on 2008-08-16
Nice work... have found an alternate method of creating drivers for the 5007EG, though, and you can share the built module .debs with others that use the same kernel.

If you want just a working driver, you need to install module-asistant as well as the other packages needed to compile the regular driver.

Go to packages.debian.org and pull the latest madwifi-source .deb out of unstable.  Install it (it just puts a source tarball in /usr/src)

Now we use module-assistant (m-a) to build and install the package:

sudo m-a prepare
sudo m-a update
sudo m-a a-i madwifi-source

When all is done, you should have installed madwifi-modules show up in Synaptic, and there will also be .debs you can share in /usr/src.  You should uninstall ndiswrapper to avoid any driver conflicts.

You can also create your own madwifi-source .deb containing your own patched driver, then install and build it the same way.  This is a little more complicated; it involves "backporting."
Here's a guide in the Mepis wiki that should also apply, but Mepis uses an actual root user, so just apply sudo as necessary.

[http://www.mepis.org/docs/en/index.php/Mepis_Package_Building_Guide](http://www.mepis.org/docs/en/index.php/Mepis_Package_Building_Guide)

You don't need to worry about the gpg stuff...you would want to pull the madwifi-source source packages (.dsc, .diff or .diff.gz, and orig.tar.gz) from Debian unstable or maybe packages.ubuntu.com  (intrepid?) Use the .dsc to extract and patch the source.  Now examine the source.  Take your patched source folder and place it in the folder over the older source. You would want to add a section to the /debian/changeog file, renaming the version of this package. Then you can build a .deb of the new madwifi-source with

sudo debuild binary

then this deb can be installed, then driver modules built with m-a.


If you need an updated madwifi-tools, they can be backported also, or mine here will probably work:  [http://www.mepislovers.org/forums/showthread.php?t=16794&highlight=madwifi-tools](http://www.mepislovers.org/forums/showthread.php?t=16794&highlight=madwifi-tools)

---

### Post by gaurang on 2008-08-16
hey nicedude and ethos101 ... 

see these screenshots ... i guess , i am rolling now .. with aircrack for WPA  .. man , don't think that i am doing this with other's network , this is 100% mine .. so don't think wrong about my intentions dude ...:) ...

but still i have one question, like you can see in screenshot file **wac_4** ... i got about 40K of packets and with lots of ACKs .. but i haven't got any ARP .. is it normal for WPA ?? .. actually i took "little" help from another post in this forum , which was actually for some intel card , but hey commands will be common right ? so i just tried them ...

and another problem is , i guess , i need super huge dictionary .. because normally any WPA must have atlest 8 char. right ?? and unfortunately i wasn't able to break my password which was 8 char. long .. so i need a dictionary which has words => 8 letters ... like you said , i will try to find on piratebay ...

ya , i have heard before this exploit people ,they provide some kind of software .. "back track" , which contains handy tools for this like , kismet, wireshark or aircrack ... and lots of others ... i have downloaded it .. i guess i will try with it too ..

at the end , i would like to make a request you to see my screenshots and suggest anything / anywhere if i am wrong ...

err.. one more thing ... do u know how to install aircrack-ptw ?? i mean , how and where i can use it ?? it has been said that , i need to capture less number of packets if i use aircrack-ptw inplace of -ng ....

thanks ....

---

### Post by rfincher on 2008-08-17
to nicedude - re posts #121,126,127
Started this computer today, and the darned wlan was not working. complete inability to go on-line. WLAN was working last time the machine was in use, and I've done nothing to upset things. Ran all the previous checks like iwconfig, ifconfig etc and all seemed OK. Checked the wlan under vista - no problems. Then I decided to reinstall the madwifi patch tried before (post# 121) - still with no luck. Next I started to go through your install instructions, but I got cold feet when it came to the part about installing new graphics drivers. Can you help me with a method which will get me going again, but which doesn't require me to get new graphics drivers, nor remove the default stuff like linux-restricted-modules and jockey? I was really starting to enjoy U804, and this latest setback has really discouraged me. Any help or directions would be very much appreciated.
Rob

---

### Post by nicedude on 2008-08-17
To rfincher - no I will not rewrite my guide for you ( I dont have the time and using Jockey is not my preferred method, I don't even have it on any of my systems ). But you are more than welcome to learn how to control jockey's behavior instead ( I have been told this is possible but I don't know firsthand ). I personally dislike jockey ( props to whoever makes it if it helps windows based newcomers use Linux but ill manage my own stuff thanks just the same ) as it is really silly to me, Linux is not Windows and so since all jockey does is manage 2 categories of hardware ( ATI & NVIDIA video & Wifi ) I would rather choose to learn what I am doing and take care of my own system . To any who read my guide it will only work if you follow it to the letter, if you skip steps it won't work, its as simple as that. Except last step for WICD which is optional in case network manager doesn't work right for you, at the time it didn't work right for me but now it does so at this time I use it as well although most of the time I just use the command line to setup my wifi anyway or scripts I wrote (the same things WICD or network manager does can be done at the command line instead). 

As for Video drivers, if you don't want to use the latest driver packages direct from Nvidia or ATI then you can use the "envy-ng" program to download and manage them for you automatically, it does this without Jockey so now were down to Jockey just managing Wifi ( so needed less than ever with envy-ng installed ). Now once you install the madwifi driver you once again have no need at all for "Jockey" and you will have wifi, the only negative is when the kernel updates you will have to install the madwifi driver again so that it works for that kernel ( it takes me like 2 minutes to do so ) & envy-ng will update the video driver with the kernel it says ( I dont know how well it works anymore since when the kernel updates I just see if there is a newer Nvidia driver and update it myself, Nvidia has Linux driver packages available and updates them quite regularly ). Updating the Video driver by hand takes like 2 minutes as well and since they update the kernel only every few weeks it is not too much trouble to spend 4-5 minutes to redo my drivers every few weeks.

Also you might want to really be sure what chipset your wifi has before you start this as Wifi adapter makers hide this info like its top secret and they do change chipsets even in the same adapter model # with different version numbers, so google is your friend to find this out for your equipment. Also keep in mind that Madwifi drivers don't work for USB based Atheros adapters at all, so if you have a USB based adapter then you will have to use Ndiswrapper and you wont get monitor  mode nor packet injection with that solution. The list of Adapters that work with aircrack-ng with packet injection is pretty long but the list that doesn't work is much longer. Primarily that is what this guide is trying to give people with this chipset ( A way to have monitor mode & packet injection with the AR5007 adapter in easy to follow steps ). At least 20 people have sent me a PM to say that this guide worked for them when other methods were either inferior ( Ndiswrapper ) or didn't work so I am confidant it works and by using it you will learn about how to handle your own system without having to use Jockey. 

*** Some people have claimed you can just uncheck the Atheros devices in jockey and it will then work with a new driver you install, I can't test this as I don't have "jockey" on any of my 5 Ubuntu/Xubuntu PC's as it is in the list of things I uninstall as soon as I do a system install so I don't know if that is correct or not.

Heres a link to aircrack's "does my card work with injection" page
[http://www.aircrack-ng.org/doku.php?id=compatible_cards](http://www.aircrack-ng.org/doku.php?id=compatible_cards)

There anyone can find out if their card is supported by aircrack-ng or not.

---

### Post by nicedude on 2008-08-17
to gaurang - I see one thing you have wrong, and allot you have right :-). When cracking WPA you don't need 40,000 packets you just need the encrypted handshake that takes place when a client ( as in one that has the correct key ) connects to the router and they do a little encrypted handshake to authenticate. Now normally that would require waiting for someone to connect to the AP ( router, but from now on referred to as AP in this message ) and capturing the data, but thank god for deauthing since if there is already a valid client connected to the AP you want to attack then when you deauth them then you can capture the handshake when it re-authenticates with the AP. Now you can run aircrack-ng against the captured handshake ( you can also check out a program called cowpatty as it is for doing this as well, but you will have to install it from source ). Remember also not to specify the --ivs flag on your airodump-ng capture session for the handshake as you don't need or want it for WPA. To test this technique try starting off by either adding your password to the password file or choosing one that is already in there, so you can be sure it should find it if everything else is correct.

Heres a link to a good page that explains WPA & WEP attacks and how to carry them out. It has pretty simple descriptions of the steps to take.

[http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks#WPA_Flavours](http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks#WPA_Flavours)

Also you don't have to use Backtrack in order to gain allot of knowledge from their forums. The same tools used in Backtrack can be installed in Ubuntu its just that they are not all available from the repositories and you must compile and install allot of them by hand if you want to use them. In fact I even compile and install aircrack-ng & kismet from newer versions than are in the repositories as there are newer versions available from the authors of both those softwares. For example the newest version of aircrack has 2 new attack types "caffe latte" & "cfrag" which are attacks that target a client instead of an AP so if you want to have those in your arsenal you need to compile from source :-)

Hope the link and insight helps, let me know when you crack your WPA on your router :-)

---

### Post by nicedude on 2008-08-17
to rfincher again - I looked at your laptop model and it uses a built in Intel graphics chipset, I don't believe this is even managed by Jockey ( to check you can look at System -> Administration -> Restricted Drivers or hardware - i am not sure 100% and I don't have it to look at ) but there you will see a list of things Jockey says it can manage and some may be checked, if they are then jockey is trying to manage that devices driver. I read your post #121 and think I see problems, for one you say you used a driver to install form source then go on to say this,

The "Hardware Drivers" screen confirmed Atheros HAL and Support for Atheros 802.11 wireless LAN card were enabled and in use

Well if you compile the driver from source and install by hand then these shouldn't be checked ( This is why I just remove Jockey so there is no confusion ). If those are checked and you installed from source then I have no idea which is in control or if this will work at all. Its sort of a one or the other situation. Also note the driver I use now ( and is linked to post #1 of this thread is newer than the one you mentioned and the one you mentioned no longer works properly with the updated kernels ). I now am using Madwifi 3745 - AircrackPatched - with HAL 10.5.6 which works 100% here for me and for some others that report success as well. It works with WEP & WPA connections as well as being prepatched for aircrack suites packet injection.

And also to save you some time if you were unsure, as I was. You do aparently have a AR5007 wifi chipset so the driver I list in post #1 is the best one I know of at this time for this equipment. 

Goodluck

---

### Post by gaurang on 2008-08-18
> **nicedude said:**
> to gaurang - I see one thing you have wrong, and allot you have right :-). When cracking WPA you don't need 40,000 packets you just need the encrypted handshake that takes place when a client ( as in one that has the correct key ) connects to the router and they do a little encrypted handshake to authenticate. Now normally that would require waiting for someone to connect to the AP ( router, but from now on referred to as AP in this message ) and capturing the data, but thank god for deauthing since if there is already a valid client connected to the AP you want to attack then when you deauth them then you can capture the handshake when it re-authenticates with the AP. Now you can run aircrack-ng against the captured handshake ( you can also check out a program called cowpatty as it is for doing this as well, but you will have to install it from source ). Remember also not to specify the --ivs flag on your airodump-ng capture session for the handshake as you don't need or want it for WPA. To test this technique try starting off by either adding your password to the password file or choosing one that is already in there, so you can be sure it should find it if everything else is correct.

Heres a link to a good page that explains WPA & WEP attacks and how to carry them out. It has pretty simple descriptions of the steps to take.

[http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks#WPA_Flavours](http://docs.lucidinteractive.ca/index.php/Cracking_WEP_and_WPA_Wireless_Networks#WPA_Flavours)

Also you don't have to use Backtrack in order to gain allot of knowledge from their forums. The same tools used in Backtrack can be installed in Ubuntu its just that they are not all available from the repositories and you must compile and install allot of them by hand if you want to use them. In fact I even compile and install aircrack-ng & kismet from newer versions than are in the repositories as there are newer versions available from the authors of both those softwares. For example the newest version of aircrack has 2 new attack types "caffe latte" & "cfrag" which are attacks that target a client instead of an AP so if you want to have those in your arsenal you need to compile from source :-)

Hope the link and insight helps, let me know when you crack your WPA on your router :-)
hey nicedude ... i was able to crack the WPA passcode of my wifi ( actually i just added that passphrase in my dictionary to check that i m going in right direction !! ) ... but i 4got to copy that screenshot in to my windows partition and now i don't know how to open that linux partition while running windows .. so i will post attach that screenshot later on ... and you were right , it need to have only good handshake .. nothing else ...

actually, i want to ask u ... how can i detect hidden SSID ?? i tried to google it , and i found one software , airsnort ... but i find hard time for installing ( it says i need to upgrade gtk >2 and some other things too ) .. so is there any other software for same use ??? 

i must say , you are a great help to guys ,man you answer so finely !! ...

thanks again ...

---

### Post by sil3nt on 2008-08-18
Thanks for this tutorial, I fixed the wireless on my Acer Aspire One netbook ;)

[http://ubuntuforums.org/showthread.php?p=5611800#post5611800](http://ubuntuforums.org/showthread.php?p=5611800#post5611800)

---

### Post by nicedude on 2008-08-18
Thanks for the flattery ( whoever said flattery gets you nowhere was a complete fool :-) ) 

The best detector for finding hidden AP's is Kismet hands down it is just the best there is. Now to install Kismet is easy but after installing you need to configure one main thing for sure before it will work. Kismet has a config file and it needs a setting for what driver you are using to be set before it will work. Also once it is installed and you configure the config file you must launch kismet_server first then kismet_client , the first one is the server which sits in the background and the client lets you read the data from what the server sees in an easy to use GUI window.

COMMAND TO INSTALL KISMET
sudo apt-get install kismet

COMMAND TO OPEN KISMET CONFIG FILE TO EDIT IT
sudo gedit /usr/local/etc/kismet.conf

HERE IS WHAT MIN LOOKS LIKE - dont pay any attention to my version number as yours will be different as I installed from source. Although I don't think you should for starters since it doesn't add any more functions and the one in the repositories works just fine. Please just not where I put # and then comments follow that, there are 2 places you must change and I have comments there as to what to change it to.

# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2007.09.R1 # yours will say something different here

# Name of server (Purely for organizational purposes)
servername=scanner

# User to setid to (should be your normal user)
suiduser=nicedude # put your username that you use here

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifi_ag,wifi0,madwifi #copy this line and change the one in your file to this, wihtout my ocmments of course


After you change these things close the file and select save changes, then in a terminal ( wifi must be in monitor mode first ) you type the following 2 commands to launch Kismet, after the first one to start the server leave that terminal window open or it would kill the server ( you can just minimize it to get it out of the way )

sudo kismet_server

THEN

sudo kismet_client

Once in kismet you have to use key commands to maneuver around etc so press "h" I think for help as to what they are.

PS another cool thing in kismet is if you install "festival" which is a speach program and in the repositories and then set it in the kismet conf file that you use festival for speech, then it will speak network ESSID's when they are detected which is pretty cool if you are driving somewhere and you can just listen as it calls out the network name and type of encryption. Just thought you might wanna try that too so you can make your friends jealous :-)

Hope this helps you sniff out those sneaky hidden networks, by the way there is no way for them to hide from this if there is a client connected :-)

---

### Post by rfincher on 2008-08-18
to nicedude - thanks very much for your lengthy replies. I certainly didn't want you to re-write your guide - for me or anyone else. However your comments have been extremely helpful, and I'm now trying to understand their full implications. Thanks very much. 

Firstly, I am quite sure my wifi chipset is the AR5007 - the label on the device actually says so, as does the Windows Device Manager.  So does one of the linux commands in Terminal. And it is definitely not USB based.

So putting aside the question of whether I'll use aircrack to go into deeper hacking just yet, am I right in thinking that if my laptop uses an Intel graphics chipset, no harm can be done if I remove the Default Stuff in Step 4 of your guide. Furthermore, couldn't I simply forget about Step 1? (BTW my System>Administration drop-down doesn't have a "Restricted Driver Manager" listed). Also, there'd be no need for using envy-ng?

Re-installing the madwifi driver after any kernel updates doesn't seem too hard, and I've already done it once before!
Since the earlier madwifi driver revisions r2756 and r3366 are no longer available from madwifi, and I don't have copies on my drive, it seems that installing the r3745 revision as per your guide is the way to go. 

I don't know how Jockey works, but there is definitely something odd going on, which you may have put your finger on in post #149.
A search under Synaptic PM shows 3 jockey packages - jockey-common, jockey-gtk and jockey-kde. All are listed as "Latest Version". Does removal of the jockey packages remove "Hardware Drivers" from the System>Admin drop-down or does it just remove the operator's ability to enable/disable the Atheros drivers listed there? Or something else?

Finally do you have a view on why the Atheros WLAN was working one day, and not the next? I swear I touched or altered nothing other than the shutdown button in software!!

Thanks again
Rob

---

### Post by nicedude on 2008-08-18
to rfincher - Ok great you have a internal AR5007, this is exactly what this guide is written for.

Ok as far as not needing envy-ng No you probably don't. To see for sure look at what drivers show up as being controlled by the hardware manager that you describe as having Atheros in it. That by the way is Jockey, as to why there are 3 Jockeys those are jockey the program and 2 different GUI frontends for it one GTK & one for KDE. You don't need any of them though as I would bet that all they are trying ( miserably I might add ) to control is your Atheros AR5007 adapter. Why doesn't it just work now, I have no idea but it won't start working all on its own I can tell you that. If I am right and Jockey only lists your Atheros adapter then just nuke all 3 of those jockey entries and follow my guide minus the Video drivers ( which you won't need and I believe I explain in my guide that the graphics driver section is just for Nvidia & ATI users )

So unless there are more things listed in the place you mentioned where you can enable & disable your Atheros adapter then you are good to go. If there are more things listed there then post back and I will advise what to do, but I don't think there are. The main reason I like to ditch Jockey altogether is that then there is ZERO chance of it screwing with your wifi at a later date, some say you can just uncheck Atheros and use my driver the way I describe to, but I prefer to rip Jockey out since if something is not there it can obviously not cause any problems. It also doesn't really do squat for you at the junction that you are managing your own Wifi driver by hand. So just verify that Atheros is the only thing and go for it. I will be around later tonite to help if needed. Remember too that step 7 is optional and you shouldn't need WICD if you can use the built in Network-manager so try it first once you have the driver installed.

If you have problems connecting to your router remember to do it in baby steps like follows -> first connect and test with NO WEP or WPA -> then try WEP -> then try WPA . If you follow that progression and at some point it won't connect that will let me know what to do as saying "it won't connect" is very poor in comparison.

Goodluck and I will check in on you later this evening, but I think it will be just to read how your wifi works now.

---

### Post by rfincher on 2008-08-19
hello again nicedude - you'll be getting tired of me soon, I reckon!! Well, I tried to get my card going, but failed. First I followed Step2 successfully.
Step 3 took me to the FileFactory site, but the driver listed there differed from the one you named in Step 3. It was "AR5007EG-Madwifi3745-AircrackPatched-HAL10.5.6.tar.gz". So I downloaded it anyway since its description more or less matched what I thought it should be. 

Step 4 was successful - I removed the linux-restricted -modules and the Jockey applications.

I was then able to extract the downloaded driver file and get into its directory. The "sudo make" command in Terminal produced an error-free compile (I think that's the term?), and the "sudo make install" command produced an error-free install. I followed the next instructions and felt that Step 5 was successful.

Step 6 successfully installed WICD.

Next I rebooted. The "Hardware Drivers" entry had gone from the System>Admin menu, and WICD was there on the Applications>Internet menu. However, starting WICD produced the message "No Wireless Networks Found". And of course opening Firefox did not connect to the Internet (more on that soon). Under "System>Admin>Network" it wasn't possible to eliminate the security, the minm option being WEP (hex).

The most telling info was from iwconfig, as follows:

rob@compaqC731-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:3  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rob@compaqC731-laptop:~$ 
Note there is No Access Point, the link quality is zero, and the signal level is -96 dBm - same as the noise level. In short the Atheros card is not working, even though it appears to be recognised. 
It's all pretty frustrating, eh? What am I doing wrong? Is there any other info I can get via Terminal which would help you? and BTW how do I get a nice box around the Terminal screen printout above?
Again sorry to bother you nicedude, hope you can help.
Thanks Rob

---

### Post by timpaton on 2008-08-19
I'm on an Acer Aspire 4315, running Linuxmint 5 Elyssa.

I have an AR5007, and have followed these instructions, but I can't find a wireless interface!

lspci gives me:
```
 $ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

That 04:00.0 line is the same mis-identification as many have. It's a 5007.

So, I have the hardware. But iwconfig gives me:
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

... and that's it. Not ath0, no wifi0 or anything.

I've done the modprobe ath_pci thing, I'm using Wicd, but it's no use if I don't have an interface!

This laptop came with Feisty pre-installed, and wireless worked then. I've installed several *buntu OSs with several Madwifi drivers, and some have worked, some have worked intermittently... but at the moment, I can't win a trick.

Any clues?

---

### Post by rfincher on 2008-08-19
to nicedude- update on post #155,
After more poking around in "Network Settings", I changed the Host Name from compaqC731-laptop to di624, and the alias of 127.0.0.1 to di624. This was similar to what I did in post #121, and got canned for. The Network Settings screen then flashed a warning, so I reset both these fields to their original names, and rebooted the machine. Then ran iwconfig in Terminal, and the response showed the  wireless card ath0 to be working. The Access Point was now 00:1c:f0:66:43:18, link quality = 71/70, Tx power = 16 dBm, and signal level = -25 dBm - well above noise level of -96 dBm. So somehow, changing then changing back the network settings caused ath0 to be energised.
But WICD still cannot find any wireless networks. Pinging the router's address at 192.168.0.1 produced a very varied response - average 1.72 ms, min 1.01 ms, max 3.2 ms.
However, attempts to ping my server or Ubuntu.com were unsuccessful. So I'm tantalisingly close to getting on-line, but not quite there yet. I'm now going to bed (it's 12.20 am in Melbourne) and I hope you'll have some comments/ideas when I get up in the morning. BTW how do I officially record "thanks" to you on this thread?
Cheers
Rob

---

### Post by gaurang on 2008-08-19
hey nicedude ...

man i got stuck again .. like you said , i found that xploit ppl's dictionary .. which is about 3.5Gb after extraction !!! ... and like they have given instruction in it , i combined all things in to one single txt file , which was damn huge 3.5 Gb !! ... but now when i try to use it for aircrack , i get error like this you can see in screenshot .. 
err.. you can see just above that i used another small dictionary and i can crack that wpa .. but when i use that bigfile .. i get error ..both are in same place though .. it says file is empty :confused: but i checked that file with one software that was given in that same package (which is designed to view files >1Gb ) .. and i can see there are words ..and anyways .. it shows it is of size 3.5Gb in properties .. so naturally its not empty. .. then why i get this message ?? 

any suggestion guess ?? 

Note... i think to crack any wpa .. you must have to be lucky, because no matter how big is your dictionary , i feel its almost impossible to crack wpa if that word isn't in dictionary ...](*,) .. right ??

---

### Post by nicedude on 2008-08-19
I don't know why you get that error but my bet would be that there is a sort problem with the file ( as in Aircrack wants the file in a certain structured format and it is different from that ) I haven't even used Xploitz files yet as I had already found many other password lists and combined & sorted them giving myself a 1.5 GB file which is pretty complete as far as I was concerned when guessing a password that is a word or 2 words ( I found double word lists ). As far as you can't crack it if its not a word, that is not true as there is another way to crack a WPA key without using a password list. It is to use a rainbow table to crack the password in use ( i say password but in this case that applies to whatever they are using not just words ). Rainbow tables just make the time it takes VS bruteforce guessing much quicker as they are all the hashes for given ESSID & WPA. So when working with a rainbow table it must have been compiled for only certain ESSID's ( one or more ). Now the bad news they are huge, I have a set for the top 1000 ESSID's and it is 33GB in size, I got them from "church of wifi" but I am not sure that they still have torrents for them and there is a company that sells rainbow tables like these for allot of money. You can make a custom rainbow table for say a single ESSID but it can take a long time to create even for one ESSID. The 1000 top ESSID rainbow tables I have were compiled using special computers that are designed for cryptography and I believe they used 15 of them together to compile them and it still took a week ( each of the special computers generate many times the keys per sec compared to a top shelf home PC ) So to do the same list like I have on a standard home PC would probably take a few years :-(  

You can also check out COWPATTY as a secondary to aircrack for actually cracking the WPA once captured. And google "church of wifi" and "wpa rainbow tables" and see what you can find. You may still be able to find a torrent for the rainbow tables I have but as I said they are 33GB so it will still take awhile to obtain them even if you find a source ( unless you want to pay some serious cash to buy them :-( ).

HERE IS A LINK TO COWPATTY SOURCE
[http://wirelessdefence.org/Contents/coWPAttyMain.htm](http://wirelessdefence.org/Contents/coWPAttyMain.htm)

Hope this helps and let me know how this all turns out.

---

### Post by rfincher on 2008-08-20
G'day nicedude - the saga continues! Started the machine up again this morning, and damn it - no sign of WLAN activity. 

iwconfig showed
> rob@compaqC731-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"di624"  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

rob@compaqC731-laptop:~$

Then ifconfig gave
> rob@compaqC731-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1f:3a:10:53:32  
          inet6 addr: fe80::21f:3aff:fe10:5332/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:1f:3a:10:53:32  
          inet addr:169.254.3.10  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:1b:38:c6:30:af  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fec6:30af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:899619 (878.5 KB)  TX bytes:98530 (96.2 KB)
          Interrupt:22 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93016 (90.8 KB)  TX bytes:93016 (90.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-3A-10-53-32-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80394 errors:0 dropped:0 overruns:0 frame:5064
          TX packets:122197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:10641759 (10.1 MB)  TX bytes:5926552 (5.6 MB)
          Interrupt:22 

rob@compaqC731-laptop:~$

If the Atheros card was working perfectly on Windoze (dual boot) you'd begin to suspect the card was faulty! Next thing I did - probably shouldn't have - was to re-do your instructions from Step 5 on. Still got the same iwconfig/ifconfig response, and of course no connection to the router/internet.

Any ideas?
Rob

PS The smilies in the iwconfig quote are in fact colons (:). Not sure why.

---

### Post by nicedude on 2008-08-20
To anyone that is using WICD and having troubles but followed the guide here is a tip that might be your problem. Although this is only possibly your problem if you see ath0 in your iwconfig output, if you see no ath0 in iwconfig output then the driver is not loaded. rfincher for one does have ath0 though in his outputs and this might solve his problem.


Try opening WICD and make sure you select the interface of ath0 and not the interface wifi0 as that is not the correct interface. It has been brought to my attention by someone who used my guide that this was a problem for them and by just setting to ath0 all was resolved.

nicedude

EDIT
PS You never have to change your hosts name setting ever. If anyone has ath0 showing up in their iwconfig and still can't connect to a wireless router then please contact me via PM ( so that I get the note faster ) and I will jump in and help one on one to get it resolved. Please send me in the PM the output of the following commands so I know what I am dealing with and I will answer you with things to try as soon as possible, then you can post here once we get it worked out how we did it etc for others to see. But PM'ing me will get you a much quicker response most of the time ( sometimes minutes VS hours ).

Commands to send me the output of in your private message so I can see whats going on with your adapter.

iwconfig

sudo iwlist ath0 scan

lshw -C Network

---

### Post by timpaton on 2008-08-21
> **timpaton said:**
> I'm on an Acer Aspire 4315, running Linuxmint 5 Elyssa.

I have an AR5007, and have followed these instructions, but I can't find a wireless interface!

After some PM discussion with Nicedude, we wondered whether the problem might be that Mint uses a different generation of kernel than the main Ubuntu. So, as an experiment, I installed Ubuntu... and found that it has the same generation of kernel (installed -16, and it updated to -19 using the update tool).

None the less, I followed the page 1 instructions again, up to the modprobe ath_pci stage. Again, iwconfig didn't list any wireless devices!

So, I did a modprobe -r ath_pci (to uninstall the module), and went googling for a different driver.

I found this one here:
[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)
... and downloaded the most recent. That is, the latest version of the latest madwifi driver. Completely standard and regular stuff.

So, I unpacked it, cd into the directory, make, sudo make install, modprobe ath_pci. iwconfig... again, nothing. Hmmm.

Reboot... and there in the network config thing in the system tray (sorry, still using Windows terminology), I have wireless networking ability!

Now, Nicedude said something about Ubuntu being on kernel -20. That's strange, because I'm fully up to date on this install, and it's only -19. So, Nicedude, I'm not sure where you got your kernel from. Maybe the driver you provide works with -20, and the main Madwifi driver only works with -19. Guessing.

I'll now try and see if the main Madwifi release will work with my LinuxMint installation (which also uses kernel -19). For the minor differences, I think I prefer the Mint... as long as I can make it work.

tim

---

### Post by nicedude on 2008-08-21
You need to change your sources or something so that you can get the 2.6.24-20 kernel from the repositories. Although to me it is in the regular main repository. I will attach a screen shot so you can see.


Did you maybe install Ubuntu 7.10 Gutsy Gibbon as my guide is for 8.04 Hardy Heron ? That could be the difference. And the driver you mentioned trying is probably the same one I used except I patched it for injection with the aircrack suite for hacking purposes.

---

### Post by gaurang on 2008-08-22
> **nicedude said:**
> You need to change your sources or something so that you can get the 2.6.24-20 kernel from the repositories. Although to me it is in the regular main repository. I will attach a screen shot so you can see.


Did you maybe install Ubuntu 7.10 Gutsy Gibbon as my guide is for 8.04 Hardy Heron ? That could be the difference. And the driver you mentioned trying is probably the same one I used except I patched it for injection with the aircrack suite for hacking purposes.


hey nicedude i have -19 kernel ... but as you know i m running smooth ... :) ... i think timpaton must be missing something in those "step by step guide" .. 

err.. i don't know the solution though , just raised my hand for -19 :) ...

---

### Post by nicedude on 2008-08-22
Thanks for that info Gurang I didn't remember if this was the same driver I was using when I used -19 but thought it was just didn't want to say before for sure ( in case I might be wrong, I don't always remember such things as if something breaks due to a update I just fix it and forget it ) but I am on -20 and it works for me with that as well.

Timpaton can you confirm for me that you are using 32bit Hardy 8.04 so I know whats up with your situation.

---

### Post by nicedude on 2008-08-22
Ok timpaton I did some googling this morning and found out the following about your laptops wifi, I think you don't have an AR5007 like me but instead have a Atheros AR5BXB63 AR5006 which is another adapter that even gives the same lspci ID code as the AR5007 ( sudo lspci -v and look at the subsystem ID and google that as it might get you exact info about what it truly is ). Pretty much to figure out what you have sometimes you have to google it and not just trust lspci. So I would say you need to look up and see what driver version & installation technique is best for the AR5006 and also verify I am right that you have a AR5006 below is a link to someone with a 4315 with one but there are different versions of Acer laptops as in I have a 5520 but if I look on the bottom I see it is a 5520-5716 so you might want to use that extra version number in your googling to confirm what you have for sure as I could only say I am probably right but cant be 100% so you will just have to verify what yours is for sure ( I also saw some people say they had a AR5BXB63 sticker on bottom of their laptop so you might check for that as well ). 

Here is a link to someone with 4315 saying he has ar5006

[http://forum.notebookreview.com/showthread.php?t=256052](http://forum.notebookreview.com/showthread.php?t=256052)

Heres a link to a guy saying his ubuntu and AR5006 are working with this driver -> madwifi-ng-r2756+ar5007

[http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html](http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html)

Link to madwifi ticket about AR5007 which has several people discussing AR5006 just search in the thread

[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)


Hope that all helps you figure out your adapter for sure :-)

---

### Post by stevenpusser on 2008-08-23
I'm pretty sure these are all one and the same chipset--Atheros is just making things harder for us.

I just installed Linux Mint, and upgraded the kernel to 2.6.24-19.36.
Followed your excellent guide about uninstalling jockey and restricted drivers. Installed some of the  backported deb packaging tools (debhelper) from the Mepislovers forums, Installed the madwifi-source .deb from Debian Lenny (packages.debian.org) and built a madwifi-modules .deb for the Mint kernel using module-assistant. Also installed the Mepis backported madwifi-tools 0.9.4 as it's a dependency...

Added ath_pci to /etc/modules, rebooted, and hey-presto! network-mangler auto-connected--cool.

You would have to rebuild and install the module any time there is a change in the kernel with

sudo m-a a-i madwifi-source

This creates and installs the module .deb.  You will find it afterwards in /usr/src.

As a proof of concept, here are the debs needed.  Of course, remember the warnings about taking .debs from strangers...if you don't feel safe, try these in a test install.

You don't need the madwifi-source unless you want to create your own sharable .debs for your particular kernel.

It's also possible to use patched source to create the madwifi-source .deb, then use that to create modules compatible with aircrack.

File: [http://files.filefront.com/madwifi+debs+toolszip/;11579585;/fileinfo.html](http://files.filefront.com/madwifi+debs+toolszip/;11579585;/fileinfo.html)



> **nicedude said:**
> Ok timpaton I did some googling this morning and found out the following about your laptops wifi, I think you don't have an AR5007 like me but instead have a Atheros AR5BXB63 AR5006 which is another adapter that even gives the same lspci ID code as the AR5007 ( sudo lspci -v and look at the subsystem ID and google that as it might get you exact info about what it truly is ). Pretty much to figure out what you have sometimes you have to google it and not just trust lspci. So I would say you need to look up and see what driver version & installation technique is best for the AR5006 and also verify I am right that you have a AR5006 below is a link to someone with a 4315 with one but there are different versions of Acer laptops as in I have a 5520 but if I look on the bottom I see it is a 5520-5716 so you might want to use that extra version number in your googling to confirm what you have for sure as I could only say I am probably right but cant be 100% so you will just have to verify what yours is for sure ( I also saw some people say they had a AR5BXB63 sticker on bottom of their laptop so you might check for that as well ). 

Here is a link to someone with 4315 saying he has ar5006

[http://forum.notebookreview.com/showthread.php?t=256052](http://forum.notebookreview.com/showthread.php?t=256052)

Heres a link to a guy saying his ubuntu and AR5006 are working with this driver -> madwifi-ng-r2756+ar5007

[http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html](http://brunoabinader.blogspot.com/2008/05/atheros-ar5bxb63-on-ubuntu-hardy-heron.html)

Link to madwifi ticket about AR5007 which has several people discussing AR5006 just search in the thread

[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)


Hope that all helps you figure out your adapter for sure :-)

---

### Post by nicedude on 2008-08-23
There are actually a AR5006 & AR5007 separate chipsets, now how close they are to being the same thing I have no idea. I would assume they are very close to the same thing and also since Madwifi driver source works with allot of adapters I would imagine that all Atheros adapters are somewhat similar. But there could be differences and its best if you are kind of new to all this, to just make sure which adapter chipset you have for sure & then find someone who has got it working and tells how ( especially if you have allot of trouble in getting it to work ). I actually took my RF shield off and looked at the actual chipset because I was curious enough, but I don't recommend anyone do this unless you have worked on laptops before and know a little bit about PC technician work ( so you don't break your PC ). 

In general though most people that I have helped via PM who had problems turned out to not have followed my guide exactly, or had a configuration problem once the driver was installed. So if you install my driver following my guide and can't connect but iwconfig lists "ath0" as being there, then there is a good chance that you could have a configuration problem. First would be having wifi0 selected in your network-manager or WICD options when you should select ath0 for your Atheros wifi. Second would be that you have WEP or WPA enabled on your router you are trying to connect to and have some setting misconfigured ( like your key :-) ). So the best way is to turn off encryption & mac filtering when first testing your routers wifi. If it connects OK that way, then go on to enable WEP or WPA and if it then doesn't work you know you need to check the encryption settings otherwise you would think the driver didn't install. If you get stuck in one of these situations just PM me and I will try and help you figure it out and get it going.

Thanks steven for mentioning the build a deb module idea, another guy mentioned that a while back and I thought about it. But in general the driver is so easy to make/makeinstall this. I kinda also figured if while using my guide someone has to make and install the driver from source then they learn the make lesson and when they want to try some program from source they already have done it before and therefore it doesn't seem too difficult. Thanks though for mentioning the idea though.

EDIT
And yes they do make it extremly hard to find the real specs etc for your wifi adapter ( its like its top secret or something ). You don't buy a PC that says the Graphics card is 3D 256MB without seeing what chipset they use and they give that info freely but wifi specs never just tell what chipset is being used. Oh well at least I can usually google up the answer from somewhere :-)

---

### Post by gaurang on 2008-08-23
hey nicedude ...

i am still at that problem we had discussed in pm ... :( .... do you see any other way ??? you know , i have found that site ,which provides that 33Gigs of rainbow tables ... and but i m still on 15Gigs (err only 50% downloaded .. still says 15 hrs remaining :( .. dsl sucks .. i want FIOS man ... :) ) ... anyways .. i have downloaded couple of other things tooo ... so i need your help with gettting cowpatty working dude .. 

i m sooooo excited to try it out ... so ... help meeeeeeee .... 

tc ..

ow .. one more thing ... what if user has restricted access to router via , MAC addresses ?? i mean , like you know , we can setup our router that we can setup so that , it allows only those MACs to connect it which are already in its list... in that case  .. what's gonna happen even if we have PSK ?? i m gonna try it , but i m sure it will not work .. right ???

---

### Post by nicedude on 2008-08-23
Gurang I sent you a PM with some things to try as to the top part. And as to what effect someone using MAC address filtering would make as to how hard it is to try and crack. Here is the differences as I see it for wep & wpa because they are different.

For WEP you would have to sniff the network and find an already associated client and then use a utility like macchanger to change your wifi mac to the MAC of the client you detected earlier. So you could not hack this type of setup without there being a valid client detected prior to being able to attack ( or at least previously sniffing and recording valid clients MAC's for you to use ) . But once valid clients are detected this can usually still be hacked via the spoofing of your MAC and then hacking it the same way you would ( FakeAuth then AirReplay injection to get a bunch of packets ).

For WPA it shouldn't really affect an attack since all you need is a handshake capture, which you will later attack with a dictionary or Rainbow attack. To get the handshake captured you will need a client computer connected once again, and then you would start the capture with say airodump-ng and then deauth the client computer and when it reconnects you will have your handshake capture. So I don't think you would even have to use macchanger to change your wifi's MAC address to do this even with the router having MAC address filtering on. If I am wrong though then just spoofing the MAC of the valid client would still make MAC address filtering useless. Check out the software "macchanger" in the repositories as it can make your wifi MAC any MAC you want.

I saw this list of 6 worst ways to secure your wifi on which #1 was MAC  address filtering so have a look at it because it explains some things that are common misconceptions about wifi security.
[http://blogs.zdnet.com/Ou/index.php?p=43](http://blogs.zdnet.com/Ou/index.php?p=43)

hope that helps you figure it out.

---

### Post by gaurang on 2008-08-23
> **nicedude said:**
> Gurang I sent you a PM with some things to try as to the top part. And as to what effect someone using MAC address filtering would make as to how hard it is to try and crack. Here is the differences as I see it for wep & wpa because they are different.

For WEP you would have to sniff the network and find an already associated client and then use a utility like macchanger to change your wifi mac to the MAC of the client you detected earlier. So you could not hack this type of setup without there being a valid client detected prior to being able to attack ( or at least previously sniffing and recording valid clients MAC's for you to use ) . But once valid clients are detected this can usually still be hacked via the spoofing of your MAC and then hacking it the same way you would ( FakeAuth then AirReplay injection to get a bunch of packets ).

For WPA it shouldn't really affect an attack since all you need is a handshake capture, which you will later attack with a dictionary or Rainbow attack. To get the handshake captured you will need a client computer connected once again, and then you would start the capture with say airodump-ng and then deauth the client computer and when it reconnects you will have your handshake capture. So I don't think you would even have to use macchanger to change your wifi's MAC address to do this even with the router having MAC address filtering on. If I am wrong though then just spoofing the MAC of the valid client would still make MAC address filtering useless. Check out the software "macchanger" in the repositories as it can make your wifi MAC any MAC you want.

I saw this list of 6 worst ways to secure your wifi on which #1 was MAC  address filtering so have a look at it because it explains some things that are common misconceptions about wifi security.
[http://blogs.zdnet.com/Ou/index.php?p=43](http://blogs.zdnet.com/Ou/index.php?p=43)

hope that helps you figure it out.


damn .... that was dumb question i guess ... :) ..  .... anyways ... it was interesting to read that thing :p ... that blog told me that i was one of that dumb users ( .. actually for first two :P ) who think that can make them "safe" 

you know , i feel like , linux's synaptic manger is a home of devil ... it has all bad things in it ... :P .... 

thanks

---

### Post by stevenpusser on 2008-08-23
> **nicedude said:**
> .....

Thanks steven for mentioning the build a deb module idea, another guy mentioned that a while back and I thought about it. But in general the driver is so easy to make/makeinstall this. I kinda also figured if while using my guide someone has to make and install the driver from source then they learn the make lesson and when they want to try some program from source they already have done it before and therefore it doesn't seem too difficult. Thanks though for mentioning the idea though.



Agreed that learning to compile is valuable!  But if possible, I try to build proper .deb packages, so things show up in the APT package managing system, and can be added and removed easily...
And there are a lot more drivers-source in upstream debian that can be upgraded in this fashion,(module-assistant) such as alsa-modules and ndiswrapper (of course, remembering that newer is not always better)

Once you have set up a package building system, it's wonderful how easy it is to "backport" packages and create proper .debs than it is to try and build them from the raw source.  One command automatically pulls in and installs all the build dependencies (if available, if not, you have to make those), then "debuild" gets everything going and out pops your installable, sharable .debs.  When installed, these will automatically pull in all the "run-dependencies" when you run

sudo apt-get f install

---

### Post by David Mulligan on 2008-08-24
I've gotten the madwifi drivers installed and it is working under Ubuntu 8.04.  However I have an N network but the best speed I can get is 54Mb, often much less.  The same card and network report 300Mb from windows.  Any ideas?  The router and card seem to require AES encryption to get above 54Mb.  I think I have that enabled on my ubuntu config.

Thanks,
David

---

### Post by TpyKv on 2008-08-24
You are the man, thank you!  

:guitar:

---

### Post by nicedude on 2008-08-24
David
I don't know what the problem would be unless the windows driver is different and supports the 300MB while the Madwifi doesn't which could be the case. But in general 54MB should be fine for anything you do, I mean do you have faster than 54MB internet connection ( I would tend to think you have 3,6,10 or 20 MB internet like the rest of us ). So unless you are trying to send and receive allot of data on a local network this shouldn't matter, as in your internet connection is probably just running at 10MB/sec anyway. A good test to see how much using wifi slows you down, try doing a speedtest with wired Ethernet cable connected to your router & then test it again while connected to the router via Wifi and see if there is any difference. Basically I think the whole 300MB/sec thing takes having the same brand router and adapter to work and probably wants its own driver ( ie the windows one that they wrote for it ) 

To do a speedtest here is a place to do it.
[http://www.speedtest.net/](http://www.speedtest.net/)

So if it is just as fast as your wired Internet then I wouldn't worry about it as 54MB should suffice & be faster than your actual internet connection is :-)

---

### Post by David Mulligan on 2008-08-24
Nicedude,

It is not just about the internet connection.  However I often connect at 18Mb which is slower than my internet connection.  I have 10Mb+boost which gives me 15-20 bursting and 18Mb wireless is half duplex which is really only 9Mb when the wind is at my back.  However it is rarely the internet connection I care about.  I would like to be able to stream video across my network which includes the ability to pause and skip which require bandwidth and low latency.

Thanks,
David

> **nicedude said:**
> David
I don't know what the problem would be unless the windows driver is different and supports the 300MB while the Madwifi doesn't which could be the case. But in general 54MB should be fine for anything you do, I mean do you have faster than 54MB internet connection ( I would tend to think you have 3,6,10 or 20 MB internet like the rest of us ). So unless you are trying to send and receive allot of data on a local network this shouldn't matter, as in your internet connection is probably just running at 10MB/sec anyway. A good test to see how much using wifi slows you down, try doing a speedtest with wired Ethernet cable connected to your router & then test it again while connected to the router via Wifi and see if there is any difference. Basically I think the whole 300MB/sec thing takes having the same brand router and adapter to work and probably wants its own driver ( ie the windows one that they wrote for it ) 

To do a speedtest here is a place to do it.
[http://www.speedtest.net/](http://www.speedtest.net/)

So if it is just as fast as your wired Internet then I wouldn't worry about it as 54MB should suffice & be faster than your actual internet connection is :-)

---

### Post by David Mulligan on 2008-08-24
It seems that that madwifi is limited to 54Mb.  I have to wait for the ath9k driver to be able to go faster.

---

### Post by Resolent on 2008-08-26
This guide is extremely well written with plenty of attention to detail. Even if you have a problem, niceguy will be there to answer all of your questions through private messages. 

Thank you niceguy.

---

### Post by nicedude on 2008-08-26
You are most welcome my friend :-)

---

### Post by jhoe on 2008-09-01
Has anyone had the problem of Wicd not seeing wireless networks?

Wireless and wired was working fine...then I rebooted.  All I remember doing is deleting the AR5007EG-Madwifi-AircrackPatched-HAL10.5.6 directory, I'm guessing that nicedude's instructions require leaving that directory behind?  I tried to go back and reinstall it, but only wired works.

iwconfig yields:
```

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have wext as the WPA supplicant.  ath0 is the wireless and eth0 is ethernet, which is working fine.

And how do you say thanks in the forums?  I don't see a 'thank this person' button anywhere?!

---

### Post by nicedude on 2008-09-01
To jhoe

If WICD is a problem for you then you can always reinstall network-manager the default Ubuntu network management utility, it used to mess up for me but now works so I use it once again.

The directory with the driver in it will not do anything bad if you delete it, but that said each time the systems kernel is updated you will have to go into that directory and run make and make install again to reinstall the driver for the new kernel version. If you have had your kernel updated lately and my solution was working then that may be your problem.

And to thank someone you can look in the bottom right hand corner of one of their posts and click on the small gold star which will show you chose to thank them.

Please PM me if you want some one on one help and I will help you figure out your troubles. Also I believe you can choose madwifi instead of wext, but maybe someone else knows this better.

---

### Post by jhoe on 2008-09-01
Well, I copied the directory back over and did make, install, etc again, it still didn't work.  Shutdown it down and went to bed, booted it back up this morning and now it works again!

Thanks for all the info!

---

### Post by nicedude on 2008-09-01
Sorry jhoe I left out that after redoing make and make install you would need to type modprobe ath_pci to actually load the driver or reboot.

Glad to see you got it fixed though

---

### Post by thomas228 on 2008-09-03
> **nicedude said:**
> EDIT

well they choose to give me an infraction here for smartmouthing a noob, thats their right to do so by all means. It is also my right to no longer care to waste my time helping so this guide is closed as I have better uses for my time. Sorry if this offends anyone as I am very sorry to step on anyones toes as they are sensitive here.

Very sorry to see you close this guide.  This angers me a great deal as I looked forward to using Ubunu. Back to windows.  I will be removing myself from the forum thanks to the policies that forced nicedude to close such a helpful guide.  I'm afraid that I will be only one of many who will give up on Ubuntu because of such poor thoughtfullness.  Infractions have their place but I think this has been excesive and therefor I don't need to be a party to it.  Good luck Ubuntu.  You'll probably need it as you have caused a great harm to the Linux community by your actions. Wished I knew how to PM Nicedude so I could get the Guide he spent so much time developing.

---

### Post by laxrick on 2008-09-03
Can someone repost this guide if they have it saved? This was THE definitive guide for the ATheros chipset to work on hardy...

---

### Post by gaurang on 2008-09-03
> **nicedude said:**
> EDIT

well they choose to give me an infraction here for smartmouthing a noob, thats their right to do so by all means. It is also my right to no longer care to waste my time helping so this guide is closed as I have better uses for my time. Sorry if this offends anyone as I am very sorry to step on anyones toes as they are sensitive here.


oh .. its really surprising and little upsetting .... this guide nd nicedude were great help to people like me .... 

i just don't understand what was wrong with them ???

---

### Post by starscalling on 2008-09-04
> **nicedude said:**
> EDIT

well they choose to give me an infraction here for smartmouthing a noob, thats their right to do so by all means. It is also my right to no longer care to waste my time helping so this guide is closed as I have better uses for my time. Sorry if this offends anyone as I am very sorry to step on anyones toes as they are sensitive here.

that should be 'shutdown -r now' instead of reboot, as sometimes there are sync issues on a pure reboot command ;) otherwise quite nice, great guide!

---

### Post by ruggrat on 2008-09-04
If you are having trouble with a 32-bit system, there is another thread that lists the steps for getting Madwifi up.

[http://http://ubuntuforums.org/showthread.php?t=865971&highlight=madwifi]("http://ubuntuforums.org/showthread.php?t=865971&highlight=madwifi")

It is post #4 in that thread.

Hopefully that helps, it worked for me.  I thought there was a guide up for 64-bit instructions as well, but I'm having trouble finding it.  

Hope this helps.

edit: I found the thread that is supposed to work for Madwifi on 64-bit.  I haven't tried it, but it may be worth a shot.

[http://ubuntuforums.org/showthread.php?t=816780]("http://ubuntuforums.org/showthread.php?t=816780")

---

### Post by TpyKv on 2008-09-04
damnit I knew I should have saved a copy of this - what a joke - need wireless now and it's going to be a pain to sort, again...

---

### Post by Ethras on 2008-09-05
ahh... man this is a bummer... I just spent hours looking for some kind of guide to get my Atheros working.... I have no hardline to update anything with ubuntu and wifi is my only option, I dual-boot and download everything through windows and move it over to ubuntu and on top of that I am a super noob! please, please repost this guide, it seems to be the only one on the internet of any value... or post it on a different forum and link to it from here... somthing...

---

### Post by thomas228 on 2008-09-06
I don't have the expertise needed to support this guide as I am a UBUNTU newbie.
I was able to install wifi in a Toshiba A55 and Toshiba A205 using the nicedude guide (post #1) I saved.  Works great


Thanks again for such a great guide nicedude.

---

### Post by T3h_Dohtem on 2008-09-07
Pretty ignorant way to retaliate for being reprimanded for ignorant behavior.

---

### Post by TpyKv on 2008-09-08
> **T3h_Dohtem said:**
> Pretty ignorant way to retaliate for being reprimanded for ignorant behavior.

seconded, at first i thought it was a bit harsh but then quickly realised nicedude was in the wrong, everyone was a newbie once and they need all the help they can get, not ignorance.

Nice one thomas228!

---

### Post by Orbital_sFear on 2008-09-11
I run 64bit Hardy but here is exactly what I did to make mine work.

1. wget http: / /snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
2. tar -zxvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
3. cd madwifi-hal-0.10.5.6-r3835-20080801
4. sudo make
5. sudo make install
6. System -> Administration -> Hardware Drivers -> Uncheck both hal and Atheros support
7. sudo vi /etc/modprobe.d/blacklist -> blacklist ndiswrapper (This is because I was using ndis, but it was a gimpy solution)
8. Reboot =(, so windows-y... ick
9. sudo modprobe ath_pci
10. Surf surf surf

Since most people don't want to type sudo modprobe... on boot, this is how you load the module automatically.  !!!NOTE!!! please do all the previous steps before you auto load a new module.  If ath_pci crashes your computer when you load it, you don't want ath_pci to automatically load on boot!

1. cd /etc
2. sudo vi modules
3. add: ath_pci

Here is what my complete /etc/modules file looks like:
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
#ndiswrapper
ath_pci

Now my card boots right up and works great!

-Orbital_sFear

---

### Post by nicedude on 2008-09-16
I only got so mad because I had been up 2 days strait and instead of going to sleep I was trying to help some guy mount a disk and he wouldn't listen to the things I was telling him to try and it made me upset and I said he wasn't capable of learning and I still stand by that statement. Instead of PM'ing me he ran to an admin like he would his mommy and they obliged him like mommies do, instead of spending 2 minutes to speak to me about it and I would have apologized to the little crybaby noob. Well if they can't be personal with me and instead act like traffic cops handing out tickets well then I won't waste my time here helping. And I pulled my guide since without me being here on a regular basis to answer peoples problems when they try to use it I pulled it rather than have someone mess up their system while trying to use it. To all that were appreciative of my help you are welcome and to all that wanna talk smack about what I choose to do I could care less. Why don't you just write your own guide or copy mine and then help everyone yourself, be my guest.

nicedude

---

### Post by alephone on 2008-09-24
oh bullocks, I'm sitting here with a brand spankin' new laptop, now with no way of getting it online.  That wasn't very *nice* of nicedude. :cry:

---

### Post by ethos101 on 2008-09-26
I learned what I know from Nicedude.  Sad to see him go.

Here's what I did:

1) Get a copy of the latest snapshot from here and extract it in a safe place:
[http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/]("http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/")

2) In System>Administration>HardwareDrivers, uncheck both and reboot.

Note:  You're going to need build-essential installed.
sudo apt-get install build-essential

3) Go to the directory where you extracted the latest snapshot and type these:
sudo make
sudo make install
sudo modprobe ath_pci

4) Add it to module for startup:
sudo gedit /etc/modules
Add the line 'ath_pci' to the bottom of the list and save it.

5) Reboot.

I had to replace the wifi manager with WICD to get connected to unencrypted networks, before it was saying they were encrypted when they weren't.

As far as patching for monitor mode... I'll get back to you on that one.  This should at least get you on-line.
:edit: I tested packet injection and it's working without a patch.  I'm guessing the patch is no longer needed for injection.  I'm not sure though.  Maybe someone with more knowledge than me can explain the details.

Note: Whenever there is a headers update you'll need to do step 3 again and reboot, so now you know why I say to keep the extracted snapshot in a safe place.

---

### Post by rfincher on 2008-09-30
I've just re-visited this thread after a 5-week holiday break, and was astounded to read about the "demise" of Nicedude. He certainly helped me get my Compaq C731tu laptop communicating wirelessly with the internet. Sorry also to see him go. My laptop is one of those sub-A$600 machines being flogged by all the big resellers like Hardly Normal and OfficeWorks, and has a single-core Celeron 540 processor running at 1.86 MHz.It has Vista Home Basic and Ubuntu 8.04 dual OS, and works well under both. I took it away on hoidays, having followed Nicedude's step-by-step instructions to get the Atheros AR5007 chip communicating. At home, I couldn't get it to go, with WICD reporting "No wireless networks found". In Queensland, I tried again - having made absolutely no changes to the machine - and was staggered to make wireless connection with the wifi hotspot at the place where we stayed. Reliable, repeatable, solid internet connections over the 5 week period - no problems. Back home, same result on day 1, but alas the gremlins struck when I fired up the machine the next day - no WICD connections and no communications. After a few days of this, I was just about ready to repeat Nicedude's instructions from scratch, when today everything is working again. 
Incidentally, the Atheros AR5007 works every time under Vista. So what gives?  Anybody else having such problems?
Rob

---

### Post by lorenzocricca76 on 2008-10-13
hello All ,

in the fisrt message of this discussion, there are the 
instructions to install nvidia card driver , after installing
AR5007 MADWIFI driver. where is the guide to install 
AR5007?

---

### Post by pippo68 on 2008-10-15
> **nicedude said:**
> Bye

Sorry all but where the guide??? :confused:

---

### Post by pippo68 on 2008-10-16
> **pippo68 said:**
> Sorry all but where the guide??? :confused:

I solved alone ](*,)](*,)](*,)](*,)](*,)


1) the file Madwifi-ng-r2756+ar5007 is outdate as you can read in the file Readme inside 

2) so just link [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192) and download the update file

3) then read  [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) exactly and the joke is done!


P.S. first disable HAL and at the end if the command iwconfig not lis ath0 just only reboot the system.


---------------
ubuntu 8.04.1
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by xroox on 2008-10-31
Hi, stopped at STEP 2.

sudo wlanconfig ath0 destroy

results in:

wlanconfig: ioctl: No such device


Where do I go from here?

---

### Post by codyhendrix2 on 2008-11-07
where is this "atheros tutorial" all i see in post #1 is "bye" and a sticky to an "install nvidia AFTER atheros" guide. am i missing something???

i am another unfortunate linux noob with an atheros 5007 chipset that no linux distros currently support natively. i've gotten it working in the past twice but haven't been able to as of late. i've been through dozens of "tutorials" that are either ridden with typos and expired links or require some unlisted prerequisite conditions i am not meeting. any help would be greatly appreciated.
](*,)](*,)](*,)](*,)](*,)

---

### Post by codyhendrix2 on 2008-11-07
sorry just read the entire thread. turns out NICEDUDE had a tantrum and pulled his guide of the forum. bummer. i guess i'll just keep hunting.

---

### Post by pippo68 on 2008-11-16
> **xroox said:**
> Hi, stopped at STEP 2.

sudo wlanconfig ath0 destroy

results in:

wlanconfig: ioctl: No such device


Where do I go from here?

sorry... only a question 
why have you type wlanconfig ? I did not find this command in the page at step 3. Read that first.
I'm an newbaby with linux. I had only follow these steps and work for me now with ubuntu 8.10. 
Tell me about your doubts Bye ):P

---

### Post by ntlam on 2008-12-22
> **nicedude said:**
> The update kernel might make it work for normal wifi ( Although I am unsure ), But the real use of this guide is to get the BEST driver installed and working i.e. the one that will let you put your card in monitor mode for use with kismet and other wifi scanners and its also patched for use with aircrack software which is what you use to get others WEP keys. So if all you want to do is just connect to a wifi that you have all the settings for and are allowed to and you don't want to learn anything about or use any wifi hacking tools then if it does fix it you would be best served that way probably as doing what I outline is not super easy but I know at least 5-8 people have used this to do it, so it does work.

So to anyone skimming this thread if you want to use AIRCRACK & KISMET with your AR5007 on top of normal networking you will need to install this driver ( using my guide or another one but definitely the driver I link to ) as it is aircrack patched and I don't think they will be using aircrack patched ones with their kernel updates :-)

Where did you link the driver? I am kinda lost. But I want to try aircrack.

---

### Post by C3POXTC on 2009-02-25
With [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192) wifi ist working, but kismet ist not. Any tips to get kismet work?

---

### Post by Ctx on 2009-04-07
Hey, I can't see where is the step by step guide about AR5007. The only I can see in the main post is an nvidia installation guide :(

---

### Post by Ctx on 2009-04-08
I don't need that guide now, I already have my Atheros injecting packages :D

---

### Post by gaurang on 2009-06-07
ubuntu Junty has option to use MadWIFI ... now no need to follow this guide ...

bt in past this guide had helped me a lot in learning ...:D

---

### Post by ethos101 on 2009-06-10
I had problems getting Jaunty's madwifi option to work and still had to use the madwifi snapshot method.  Some may have the same issues but it's good to know they're giving us options. :D

> **gaurang said:**
> ubuntu Junty has option to use MadWIFI ... now no need to follow this guide ...

bt in past this guide had helped me a lot in learning ...:D

---

### Post by logaloga on 2009-07-02
Thanks alot nicedude. Your guide very useful for me!

---

### Post by henry199 on 2009-07-18
I have a problem with ubuntu wireless network i got a acer aspire one and i had windows 7 on it and now i put ubuntu 9.04 on it and when i do this install for the nvidia driver it says cant install when  i hit the ctrl alt f1 and put all the sudo stuff in there on the end when i put in the sudo sh nvidia-linux........  it says cant install what can i do will i ever have working wireless network on this laptop?

thanks

henry

---

### Post by muis198 on 2010-07-12
[http://web.archive.org/web/20080614212529/http://ubuntuforums.org/showthread.php?t=795984](http://web.archive.org/web/20080614212529/http://ubuntuforums.org/showthread.php?t=795984)
 
Here is the first post of NiceDude before it was edited. God bless google :P

---

