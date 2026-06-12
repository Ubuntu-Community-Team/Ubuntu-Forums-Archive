---
title: "Belkin Wireless G USB Network Adapter(F5D7050) installation issue"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by Sup3rkirby on 2007-04-08
Ok, I have been reading and reading and reading for the past couple hours and so far, I have not been able to figure out how to solve my problem.

I just installed Xubuntu(6.06) and have no internet access.  I only use a wireless network, so if I can't get this to work, then my computer will have no internet access, and that will suck:( 

Could someone please(with a cherry on top) give me a step-by-step set of instructions that will allow me to detect my USB Adapter, install the driver and connect to a network(or at least just get the adapter installed).

This is really frustrating for me.  I am new to Linux.  This is why I need step-by-step instructions.  I am not familiar with a lot of things in Linux and Xubuntu right now.

---

### Post by rolando on 2007-04-08
Try this

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_%28ZyDas_zd1211b_driver%29?highlight=%28WifiDocs%2FDevice%29)

:)

---

### Post by gschoper on 2007-04-08
I've been using this How-To since Breezy(5.10) to get my Belkin Wireless-G running with ndiswrapper:

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)


I have had success with it on Dapper and Edgy as well.

HTH,

gschoper

---

### Post by Sup3rkirby on 2007-04-08
Thank you both.

So far I've been running through this help page for Ubuntu with no trouble.  But right now I have a simple problem.  The 'make' command doesn't exist, and I believe this might be because I am using Xubuntu and not Ubuntu.  How can I get the 'make' command(for "sudo make both")(to install the new driver)?

My computer only has 160 Mb of RAM so I couldn't install Ubuntu.  I put Xubuntu on there so I could have an OS.  So I am running Xubuntu off the HDD right now.

---

### Post by gschoper on 2007-04-08
I believe you need to install the package build-essential. You can do this through Synaptic Package Manager or Aptitude.

gschoper

---

### Post by ffxr on 2007-04-08
Sup3rkirby, youve got make sure your installing theright driver for the chipset in that USB wireless nic,,

i have the same one, and i was fannying around for a while, before i worked out exactly what chipset it uses.. their is 3 different types of chipsets used for that card , all marketed under the same name.. the only way oof knowing for sure is checking the model number of the card..

---

### Post by gschoper on 2007-04-08
> **ffxr said:**
> Sup3rkirby, youve got make sure your installing theright driver for the chipset in that USB wireless nic,,

i have the same one, and i was fannying around for a while, before i worked out exactly what chipset it uses.. their is 3 different types of chipsets used for that card , all marketed under the same name.. the only way oof knowing for sure is checking the model number of the card..

Many ppl run into this same issue. My card is a rev 5000. This is why I suggested the ndiswrapper method as it uses the win32 drivers that came with the card.

gschoper

EDIT: if you do have a rev. 5000, you need to add the following modules to /etc/modprobe.d/blacklist:
```
blacklist ath_pci
blacklist ath_rate_sample
blacklist ath_hal
```

---

### Post by Sup3rkirby on 2007-04-09
Well, this thread has been very helpful, I still have not been sucessfully.  I have determined I have the 3000 version(lsusb) and found this article
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

but I have run through that over and over and still nothing is working...  Well, it sort of works, but not really.  The usb still isn't recognized....

I think one big problem is I can never do the 'fromdos *' step.  It tells me it does not recognize that command.  I have tried to install the 'sudo apt-get install tofrodos' but that doesn't work because it can't find the 'tofrodos' file.  I've tried loading it off the cd and everything.


I'm pretty sure that is the step that messed me up.... maybe....

also, the 'gedit' command never works either.  I have the headers and build-essential installed.

---

### Post by Sup3rkirby on 2007-04-09
Everyone has been very helpful but I am still unable to get the USB Adapter to work.  I have determined(using lsusb) that I have the 3000 version, and so I found [this]("https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29") page.

Now the problems that I think are majorly effecting my installation are
1. "sudo apt-get install tofrodos" does not recognized 'tofrodos', so it is not installed("fromdos *" will not work later)
2. 'gedit' command is not recognized

I am about to try that page one last time, step-by-step and see if I am successful.  I have just reinstalled Xubuntu so I am using a fresh start(just in case I screwed anything up)(it is ok because i had just installed it yesterday and didn't have anything saved yet).

If anyone knows why those steps might have messed up, or anything, I'd be glad to know.  I will post back on my status as soon as I retry that page(which is right now).

[EDIT]
Sorry.  My last post wasn't there when this page loaded.  It showed up in the 'quick post box'(which is where i typed it last night) and i hit the button to enable the box, then the message disappeared.  I figured it was lost so I typed another one(slightly different, but essentially the same).  So now there are two of the same message, sorry....

---

### Post by Sup3rkirby on 2007-04-09
ok.  the 'tofrodos' package can not be found.  How can I install this?  I loaded the CD and i couldn't find it on there.  Is there a download or something?  I am very sure I need this to install my adapter.

Also, the 'gedit' command will be accepted, but it will first ask for the admin pass, then once that is entered, it does nothing.  It just goes to the next line in the terminal.  So I am unable to edit some needed files("/etc/modprobe.d/blacklist" and "/etc/network/interfaces").  Xubuntu will not let me change those files.  Is there some way I can change the permission(temporarily) or anything so I can added the required lines.


Those are my only two problems.  If anyone can help me get those working, I should more than likely be able to install my adapter and get internet access on my new Xubuntu powered pc.

---

### Post by Sup3rkirby on 2007-04-09
Ok, if i use
```
sudo vi -b /etc/network/interfaces
```
then i can edit the file in the terminal.  But I still don't exactly know what I am doing.  How to I save the file in the terminal?  Right now anything I hit is just added to the file.  is there some hotkey or keyboard shortcut or command I enter to let it know I'm done editing the file and then save it?

---

### Post by Sup3rkirby on 2007-04-09
I am finally(it took lots of work) in the last little part of this whole ordeal.

My computer will recognize the USB Adapter, but I am not connected to the internet.  I must configure my Adapter.
```
# rt73 wireless network device using DHCP
iface rausb0 inet dhcp
pre-up ifconfig rausb0 up
wireless-essid MY_ESSID
# wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                  # This line for ASCII (string) keys
auto rausb0
```
I use the code as instructed, and replace 'MY_ESSID' with the name of my network and then use the 'wireless-key'(hex) line and add my network password.
```
$ iwconfig
```
returns the following
```
rausb0    RT73 WLAN  ESSID:""  
          Mode:Managed  Frequency=1 MHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-28 dBm  Noise level:-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```*(the number are not exactly those)

I am pretty sure I have not messed anything up, but I never connect to my network.  I would really appreciate some help.  It has taken me forever to find a decent Linux Distro(Xubuntu) but if I can't get this to work then Xubuntu is uselss to me and I will have to find another(which will take forever).


P.S.
 does anyone know what to type if you have no password for your network?

---

### Post by gschoper on 2007-04-09
I have had little success getting Belkin adapter's to work in Ubuntu without using ndiswrapper. Have you tried the link I suggested in my fist post in this thread? It took me less than 5 minutes to get connected to the net using that how-to and I have used it multiple times over the past 18 months or so on three different releases of Ubuntu..

gschoper

---

### Post by ffxr on 2007-04-09
i have the same revision as that card... its fairly painless installing the driver, & i think your better going with the native linux drivers if you can find them, rather than ndiswrapper, but thats an argument for another day ; )

& you didnt need to worry about that fromdos thing.. anywayy...

can you post the contents of the rt73sta.dat file that you copied to /etc/Wireless/rt73 (i think)

does the ESSID in that file match your own ESSID.. i dont think thats documented in that how to,,,,

---

### Post by ffxr on 2007-04-09
essentially what you have (had) to do is:

```
sudo apt-get install build-essential
wget http://www.ralink.com.tw/data/RT73_Linux_STA_Drv1.0.3.6.tar.gz 
tar xvzf RT73_Linux_STA_Drv1.0.3.6.tar.gz  
cd RT73_Linux_STA_Drv1.0.3.6/Module
gedit rtmp_def.h 
```
add the line:  ```
{USB_DEVICE(0x050d,0x705a)}, /* Belkin F5D7050 ver 3000 */      \
```
```
make
make install
sudo mkdir /etc/Wireless 
sudo mkdir /etc/Wireless/RT73STA
sudo cp rt73.bin /etc/Wireless/RT73STA 

```

```
gedit rt73sta.dat
```

add your ESSID in the relevant line .. then

```
sudo cp rt73sta.dat /etc/Wireless/RT73STA
sudo modprobe rt73
```


then just configure your network in the gnome-network-manager gui(or whatever its called) 

^dont know if that helps at all (maybe i have muddied the waters?), but ive installed that driver so many times now, ive pretty much got the procedure mprinted in my mind.

---

### Post by ffxr on 2007-04-09
oh your using xubuntu not gnome, sorry; exchange gedit with mousepad above..

the network manager gui is in .. apllications -> settings -> network...

your almost there, i am sure.. dont lose faith.. youll know exactly what you have to do if you run into a similar issue again.. its ust a matter of picking up a few more basics..

---

### Post by Sup3rkirby on 2007-04-09
> **gschoper said:**
> I've been using this How-To since Breezy(5.10) to get my Belkin Wireless-G running with ndiswrapper:

[http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux](http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux)


I have had success with it on Dapper and Edgy as well.

HTH,

gschoper
I spent hour and hour trying the long method from the Ubuntu WIFIDocs page.  Then I tried your method, gschoper.

[SIZE="7"]THANK YOU![/SIZE]
I feel like an idiot for not trying that first.  It worked with no problem at all.  10 minutes to get it tops.  Now everything is working. Topic Solved!

---

### Post by gschoper on 2007-04-09
> **Sup3rkirby said:**
> I spent hour and hour trying the long method from the Ubuntu WIFIDocs page.  Then I tried your method, gschoper.

[SIZE="7"]THANK YOU![/SIZE]
I feel like an idiot for not trying that first.  It worked with no problem at all.  10 minutes to get it tops.  Now everything is working. Topic Solved!

Glad I could help. Best of luck...

gschoper

---

### Post by babysteps on 2007-04-14
> **gschoper said:**
> I have had little success getting Belkin adapter's to work in Ubuntu without using ndiswrapper. Have you tried the link I suggested in my fist post in this thread? It took me less than 5 minutes to get connected to the net using that how-to and I have used it multiple times over the past 18 months or so on three different releases of Ubuntu..

gschoper

Hello!  as my name implies I'm taking very little steps towards configuring Ubuntu 5.10 on my Compaq Armada E500.  I have taken the plunge with Ubuntu by installing it on both of my laptops.  The other one, the Acer TravelMate 611 TXCi miraculously got online rather soon, but the compaq is waiting on being able to get online using a Belkin Wireless G USB (F5D7050).  I've so far been able to determine that it's a version 2000 (thanks to this thread!) and was waiting for that CD with the drivers to do the installation with the Ndiswrapper.  I'm embarrassed to say that even though I was able to download from their site the driver using another laptop and copied over to the Compaq, I did not know how to do the command line when the driver is not on a CD. 
Anyhow, now that I got the CD, I want to the site you have linked, and it's down!!  I'm so bummed.  I don't know what to do.  Would you happen to have a set of instructions that you can post here?  

Much appreciated!

Babysteps

---

### Post by gschoper on 2007-04-14
> **babysteps said:**
> Hello!  as my name implies I'm taking very little steps towards configuring Ubuntu 5.10 on my Compaq Armada E500.  I have taken the plunge with Ubuntu by installing it on both of my laptops.  The other one, the Acer TravelMate 611 TXCi miraculously got online rather soon, but the compaq is waiting on being able to get online using a Belkin Wireless G USB (F5D7050).  I've so far been able to determine that it's a version 2000 (thanks to this thread!) and was waiting for that CD with the drivers to do the installation with the Ndiswrapper.  I'm embarrassed to say that even though I was able to download from their site the driver using another laptop and copied over to the Compaq, I did not know how to do the command line when the driver is not on a CD. 
Anyhow, now that I got the CD, I want to the site you have linked, and it's down!!  I'm so bummed.  I don't know what to do.  Would you happen to have a set of instructions that you can post here?  

Much appreciated!

Babysteps

Found it in the forums:

[http://ubuntuforums.org/showthread.php?p=501001](http://ubuntuforums.org/showthread.php?p=501001)

gschoper

---

### Post by babysteps on 2007-04-15
> **gschoper said:**
> Found it in the forums:

[http://ubuntuforums.org/showthread.php?p=501001](http://ubuntuforums.org/showthread.php?p=501001)

gschoper

Thanks so much for finding that for me!  I was able to get to where the driver was installed, and hardware present, but then I think something I did prior to this is beyond my ability to troubleshoot..so just  to re-install and try it from scratch. Wish me luck!

---

### Post by babysteps on 2007-04-15
> **gschoper said:**
> Found it in the forums:

[http://ubuntuforums.org/showthread.php?p=501001](http://ubuntuforums.org/showthread.php?p=501001)

gschoper

gschoper,

This HOW TO was really a God send!  I have gotten the laptop to see the Belkin Wireless G USB F5D7050(version 200) now...but I'm not able to get online, yet.  I think I goofed when I left out the line: 

sudo ndiswrapper -hotplug


So, now I have two questions:
1) I typed the "sudo ndiswrapper -hotplug" after I've already typed :wq.  Is this bad?  Did it make up for when left it out the first round?

2) My laptop has USB 1.0 I believe.  Somewhere along the line I read that USB 2.0 would be faster for the wireless adapter.  If this is true, will getting an upgrade for the usb port help any?  And will I have to reconfigure everything?  

3)(OK, I have 3 questions) Is there a way to "undo" something I may have done in the Terminal and start over short of re-installing Ubuntu?

Thank you for your help!

Babysteps

---

### Post by stmorgan on 2007-04-23
I've lost my Belkin Install disk. How can I get the files I need to use the ndiswrapper method? I can download the drivers from the Belkin website, but it gives me an .EXE file, when I need the .INF and possibly others as indicated in gschoper's link.

---

### Post by dannyboy79 on 2007-04-23
you have a few options. install the software on a friends computer, copy all the files that the .exe leaves behind and use them with ndiswrapper

install a virtual machine using qemu or virtual box, install windows, then install the .exe. again, take all the files and put them on a usb stick or somewhere you'll have access to so you can them with ndiswrapper.

see if the drivers are anywhere on the internet. like [www.driverguide.com](www.driverguide.com), it's free to register and they have tons of drivers. i have used their website for more than 1 old piece of hardware. (i know your hardware isn't old, I merely pointing out that they have a ton  of drivers.)'

good luck!!

---

### Post by babysteps on 2007-04-23
> **stmorgan said:**
> I've lost my Belkin Install disk. How can I get the files I need to use the ndiswrapper method? I can download the drivers from the Belkin website, but it gives me an .EXE file, when I need the .INF and possibly others as indicated in gschoper's link.

Firstly, the .EXE file that you download from the manufacturer's website  is to be extracted, after which you will see the .inf file, amongst other files.  

But that might be the least of your problem...I'm still without WIFI on my compaq laptop because even though I've gotten the great set of instruction from this forum, (thanks to everyone's help) , and have gotten as close as actually associating with the router (with all the addresses, key, channels...showing properly!) I couldn't get online.  

The Belkin Wireless G USB apparently has 4 versions, each with different types of chipset, which may require different kinds of drivers.  I don't know which one you have, and maybe you have already checked and gotten the right one.  Mine is version 2000 (on the USB stick it says K7SF57050A), which doesn't seem to be supported by Linux's native driver, so I'm stuck using the Ndiswrapper method, even though I have not been able to get any closer  to where I am in the last week.

Anyhow, good luck to you.

---

### Post by babysteps on 2007-04-25
> **babysteps said:**
> 
"...........The Belkin Wireless G USB apparently has 4 versions, each with different types of chipset, which may require different kinds of drivers.  I don't know which one you have, and maybe you have already checked and gotten the right one.  Mine is version 2000 (on the USB stick it says K7SF57050A), which doesn't seem to be supported by Linux's native driver, so I'm stuck using the Ndiswrapper method, even though I have not been able to get any closer  to where I am in the last week.

Anyhow, good luck to you.

AS I'm finding out more and more that this Belkin wireless G USB stick is full of controversies.  Now, with lsusb command I find out the ID, which is 050d:7050, which some site say is a RT73, some others say its' GW3887 (! a Prism chipset). ON top of which, I couldn't get my unit to match to the picutre the UK Belkin site as far as the part number is concerned.  I did find out, that maybe, just maybe, this unit is a version 1 , not 2. 

Amidst all this, I am finding the lack of basic understanding of Linux and of Ubuntu combined with the many half-solutions and half-explanations on line make an earnest heart for this seemingly great system soon admit defeat, despite trying hard.  I wish there didn't have to be so many distributions and versions, each with slightly different key words.  There's just so many holes in my understanding of Linux in general, that even when I'm able t find instructions online that seemed to fit my situation, I still get tripped up on the simplest thing, (like how to copy a file from one location  to another, )

---

### Post by davidcourney2002 on 2007-10-21
> **gschoper said:**
> Many ppl run into this same issue. My card is a rev 5000. This is why I suggested the ndiswrapper method as it uses the win32 drivers that came with the card.

gschoper

EDIT: if you do have a rev. 5000, you need to add the following modules to /etc/modprobe.d/blacklist:
```
blacklist ath_pci
blacklist ath_rate_sample
blacklist ath_hal
```

-----------------------
Belkin Wireless G Card and Ubuntu 6.06
I have a really old Thinkpad that I want to use as a print server

I have a Belkin Wirless G 7100 5100 and I didn't / could find the right .inf file for NDISWRAPPER. I am running ubuntu 6.06 and i just did the following:
I went to /etc/modprobe.d/
"sudo vim blacklist"
added "blacklist bcm43xx" to the bottom of the file
I didn't blacklist auth_pci or auth_hal
restarted the computer and configured the network
I dont know why or how it worked but it did so give it a try

---

### Post by dmspin on 2007-12-01
I had been working on getting the Belkin F5D7050 to connect to my wireless network until late into last night and for most of this evening.  I even went and purchased an UBUNTU BIBLE book that was about 3 inches thick, hoping that it had help, but nothing I tried from that reference worked at all.  The book had me trying all sorts of ndiswrapper stuff.  I felt like I was banging my head against a brick wall over and over.

Finally, I found this thread and **ffxr**'s instructions for the RT73 Linux driver modifications.  I found a website with the RT73_Linux_STA_Drv1.0.3.6.tar.gz file and then followed **ffxr**'s instructions.  After struggling a little with the syntax used at the command line and cheating with a little bit of drag and drop, I had the two modified files (rtmp_def.h and rt73sta.dat) and the original rt73.bin file located in the */etc/Wireless/RT73STA *directory that **ffxr**'s iinstructions have you create with the *sudo mkdir *commands.  Once that was done I just went to the top of the screen, clicked on the Networking icon, clicked the radio button for my SSID and the thing adapater was finally recognized and connected like magic.   [SIZE="5"]A GREAT BIG THANKS [/SIZE]to **ffxr** for making my life much easier today.

---

### Post by 5hort5 on 2008-02-08
Ok, took me some finding out cause I new to this game but I did the following:



Belkin USB Wireless G Adapter

Version 5000 (or as listed on the box 5000uk )

Edubuntu and Ubuntu v 7.10



Went to the Menu "System" on the top of the screen, selected "Administration" and from the menu "Synaptic Package Manager"



In Synaptic do a search for "ndis"



A few things come up but select for install (if not already installed) these three things:



ndisgtk

ndiswrapper-common

ndiswrapper-utils-1.9 (or whatever the current version is)



Install the above and then close Synaptic



Now put your drivers CD in, the one that came in the belkin box
 and also (if you haven't already) plug in your belkin USB wireless adapter.


Goto the "Syetem" menu on the top again, then "Administration" then select the newly installed "Windows wireless drivers" from the menu.



This opens up in a new window



Click on “install new driver” and then browse to you CD drive, (click the little button next to root a few times to get to the top of the directory tree) then go to the "media" directory and then onto "cdrom0".



This bit may change depending on your version belkin adapter but for the 5000 I had to browse to "installationfiles/winxp2k".  In this directory is an inf file called "BLKWGU.inf", install this.  (Note: Other versions may have different files names but there will be a  .inf somewhere, try it.  Also I installed the windows 64 bit driver on my 64 bit ubuntu system and it worked fine).



If you don't have any security on your wireless network (shame on you) it should just work but if you do then click on the "Configure network" button on the Wireless network drivers window you have open.  In here highlight wireless connection by clicking on it and click "Properties".  Uncheck "enable roaming mode" then:



Select the name of your network from the "Network name" drop down

Select your security type WPA or WEP

Then enter the passwords as requested (which can be found on your router)



Click ok, click close and that should be it (hopefully).

:popcorn:

---

### Post by Lourie2 on 2008-03-09
I am trying to connect to the internet after having performed all the steps posted by 5hort5 above.  The driver is installed and I have a wireless network to connect to.  When trying to configure the network manually, through the properties of the wireless connection, after typing in the password to the network and clicking OK, it opens a box with "Changing interface cofiguration" and a bar moving from left to right and back and forth for a while, then stops.  Still I am unable to browse the web.  Whereto now?  Please help. (Ubuntu 7.10 with Ver.5000UK):confused:

---

