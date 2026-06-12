---
title: "Madwifi Atheros Improved kismet launching script and script to revert to managed mode"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by nicedude on 2008-05-19
Hey all Atheros owners until today I had a kismet luanching script but it was not 100% so I worked on it this afternoon. I now have fixed it so it is 100% and I made a 100% working script to return your atheros card back to managed mode in a couple of seconds. So you can go back to surfing without the need to reboot or type a bunch of commands. I now will share these scripts with you guys here and I hope you enjoy my work :-)

** These scripts were designed for and tested on my AR5007 Atheros card using madwifi aircrack patched drivers with Hardy 8.04 but they should work equally well with any patched madwifi drivers and Atheros card. There are prerequisite softwares and they are listed further down this post so read that carefully and make sure you have everything you need before trying to use this. In short please follow my directions in full for success.

First some info on how to use a script in general ( To avoid the questions for those that don't know ), A script is just a text file that contains commands just the same as you would type at the command line. The only thing you need to do with my scripts to make them work for you is to right click on each file after you download them to your desktop and select properties at the very bottom -then-> click the permissions tab -then-> once in permissions click on the boxes that say executable to make the script able to run then close the window. At this point you should be able to double click on the script and when asked choose run. If that doesn't work then you either need to execute it from a command line or install nautilus scripts package from the repositories and copy the two scripts to your nautilus scripts folder, I will include the nautilus scripts install command and the location of where your nautilus scripts folder should be located after installation so all you need to do is use nautilus and cut and paste the scripts to that folder. Once the nautilus scripts software is installed and my scripts ( or any other scripts ) are copied to the nautilus scripts directory you can access and use them with a simple right click and look for the new choice "scripts". If you intend to run this from the command line you might want to take the spaces out of the script names or wrap the name in "" when you execute so it will work. 

Software needed to run my scripts - make sure these are installed before trying to use
madwifi-tools
aircrack-ng
gksu
kismet

Please note the file kismet.conf must be configured as well for use by at a minimum changing the line below
source= line must be changed -to- source=madwifi_ag,wifi0,madwifi for kismet to work with your Atheros card

Also to close the kismet client window this will launch you must use the shift+Q command inside kismet 

Command to install nautilus scripts
sudo apt-get install nautilus-script-manager

Directory where you place scripts
/home/"YourUserName"/.gnome2/nautilus-scripts

Just copy them into there to have them at your finger tips :-)

I hope this info and my scripts help everyone to have a more powerful system that is easy to use as well.

Good luck with this and if anyone needs further instruction PM me and I will try to help. And please post your results here of how it worked for you.

---

### Post by packman1234 on 2008-05-19
Worked like a champ!! I had to go back into WICD Manager and log back in--but way better than a reboot!
Thanks Nicedude for all the valuable help here.Your time is appreciated by all.

Bob

---

### Post by nicedude on 2008-05-20
Your welcome Bob, but it is kinda dis hearting that only you tried it. I am wondering if only a hand full of people actually use the pactched madwifi drivers and instead use Ndiswrapper. If so I feel sorry for them as they will never see the full power & capabilities that this wonderful chipset is capable of :-( 

Oh well I tried to inform in this matter and thats all I can do, so I did my part :-)

Glad my guide to installing the chipset driver helped you Bob and glad my script works for you as well.

To anyone that does use this script please PM me or post here so I can be aware of your results.

nicedude

---

### Post by kaane on 2008-05-25
I've been trying getting my Ubiquiti SRX 300 Expresscard(Atheros 5006 chipset) working with Kismet (using these scripts too), but it doesn't work.

It works like a charm using BackTrack2, so it must be my config/drivers. I use the madwifi drivers that comes with Ubuntu 8.04.

Here's my config in kismet.conf. The 3945 is working fine, but not the Atheros/Madwifi. I have intentionally commented out the 3945 source-line:

source=madwifi_ag,wifi0,madwifi
#source=iwl3945,wlan0,3945


Here's some of the output when running Nicedude's script:


Interface	Chipset		Driver

SIOCSIFFLAGS: Input/output error
wifi0		Atheros		madwifi-ngSIOCSIFFLAGS: Input/output error

wlan0			iwl3945 - [phy0]
ath0		Atheros		madwifi-ng VAP (parent: wifi0)
ath1		Atheros		madwifi-ng VAP (parent: wifi0) (monitor mode enabled)


Why do I get input/output error on wifi0?

---

### Post by nicedude on 2008-05-27
Ok to guy above you said the iwl3945 worked well I see that as being an Intel wifi adapter so I have no idea if it is an Atheros one or not ( or do you have 2 wifi adapters I am not understanding fully as I read it again ), I see you say that lspci reports a Ar5006 which is an Atheros but this is not always 100% correct by a long shot ( In fact I am going to guess you are using Ubuntu Gutsy since that is what my AR5007 reports as in Gutsy and in Hardy it reports as a AR242x instead of AR5007 ). You need to do some Googling and/or call your laptops manufacturer and get them to tell you the exact wifi chipset used in your PC. As this looks like a driver problem, could you please post the driver you used to enable this chipset as well as the version? Also run a iwconfig command and post and I will try to figure out what you have going on to make this not work for you. 

I made this for use with an AR5007 under Hardy Heron 8.04 using the aircrack patched madwifi driver package available from madwifi.org under support ticket #1679 currently it is driver version 3366. so please just research what wifi chipset you have for sure and the driver used along with the iwconfig output ( Any one who has problems with their wifi no matter what type should do that and also you should post a lspci command readout as well but this gentleman has already told me what lspci says his is so not needed in this case )  

PS tell me your Ubuntu version as well and I will try to help you out :-)

nicedude

---

### Post by kaane on 2008-05-27
I'm sorry if I've not been clear. I have a builtin Intel 3945ABG AND an Ubiquiti 300SRX expresscard. On Ubiquiti's homepage, not lspci, it says that this expresscard has Atheros 5006 chipset. I want these two cards to work separately; the 3945 connected to my wireless gateway and the Atheros-card for Kismet.

I definetely use Hardy 8.04! System->About Ubuntu says: "This version (Hardy Heron) was released in April 2008 so its version number is 8.04."

I also use the original "Hardy" Madwifi drivers. I've not done anything with these drivers! Maybe I should reconsider this and compile my own Madwifi drivers?


The wifi part of lspci looks like this:
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
0d:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"removed"  Nickname:""
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:18:39:53:71:EC   
          Bit Rate:36 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-55 dBm  Noise level=-94 dBm
          Rx invalid nwid:1619  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



I hope this straighten things out. :)

/Lars

---

### Post by nicedude on 2008-05-28
Ok kaane 2 points that may affect your situation. I posted this here for anyone else with these dilemmas as well so they might figure out their situation.

First I am still not sure if you are using 32 Bit or 64 Bit Hardy as madwifi drivers will not work with 64 Bit Linux anything and there are no 64 Bit Linux native drivers anywhere on the Internet nor source for them. If you don't know what version you have installed then you can run the following to find out.

uname -m

If it returns i386 or i686 then its 32 Bit but if it returns x86_64 then you have installed 64 Bit Ubuntu and will either have to reinstall 32 Bit Hardy or use Ndiswrapper in conjunction with a Windows driver for your card ( If you do that however you will not be able to use kismet or aircrack as the windows factory drivers will not support MONITOR or MASTER modes ).

Second - If you do have 32 Bit installed and the Hardy wifi drivers work to enable your Atheros card they still will not enable you to use Aircrack as it requires a aircrack patched madwifi driver not the Ubuntu one. I have not tried the Ubuntu default driver at all as I decided on day one to get the best driver available and it was not it. You can find out about as well as obtain precompiled prepatched drivers at madwifi support ticket #1679, the correct 32 Bit patched driver for Hardy is also linked to my AR5007 guide and you can click that to get the best driver available anywhere that is publicly accessible. So no need to compile anything just to install it. You will also have to remove some stuff ( like laid out in my guide ) or blacklist stuff ( not my method of choice so I am no help with that ) since Ubuntu's default drivers will conflict with the proper one when you try to install and use it. I just prefer to rip the restricted driver manager out and all the modules it uses then provide my own drivers thereby giving me total control of my own machines drivers.

So in short if you want access to all modes then use 32 Bit Hardy ( You won't see any difference anyway ) and use the driver my guide links to, But if someone thinks they need 64 Bit version then you have to use Ndiswrapper solution which is the poorest way in my view but might give you basic connectivity with your router but no sneaky stuff :-(

My guide for installing an AR5007EG wifi chipset in 32 Bit Ubuntu Hardy 8.04
[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

nicedude

---

