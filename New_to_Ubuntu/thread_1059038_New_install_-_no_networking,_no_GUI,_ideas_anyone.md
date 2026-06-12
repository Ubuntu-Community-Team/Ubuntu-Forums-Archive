---
title: "New install - no networking, no GUI, ideas anyone?"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by bernie888 on 2009-02-03
Hi there

New to Linux. Used Unix about 15 yrs ago but been on the no hassle Windows platform since then :o)
Now having to go back to basic command line and figure out how to do even the simplest thing in Linux as none of it is done automatically. Shame, but I guess learning another O/S is always a good thing.
Anyway, installed Ubuntu 8.04 Server version and can't really do much at all on it. No networking is working. I have a wireless card in the PC (oh no, I hear people say). Yep, apparantly wireless networking is a difficult thing to get working in Linux. Not sure why. Ok, so thats the first problem. Second one is I have no GUI available. Yes, I know, its Linux and its basically just command line but when researching how to install wireless nic drivers, most of the articles point at using tools available IN THE GUI!
So, kind of a catch 22 situation. 
By the way, when I try and install GNOME or any of the GUIs with the apt-get install command they all fail saying the file cannot be found.
I new there had to be a reason Linux was still free :)

---

### Post by matt79 on 2009-02-03
Well try installing a edubuntu desktop or somthing; You will need your disk though.

---

### Post by bernie888 on 2009-02-03
any ideas how to do this? Do I have to figure out how to mount a CD first?
thanks

---

### Post by handydan918 on 2009-02-03
If you wanted a gui, why in the world did you install the server version? You can install any server software you want on the gui version of Ubu...

---

### Post by bernie888 on 2009-02-03
its not that I wanted a GUI particularly (although yes, it would be easier) but right now I can't get any sort of networking running, no internet, nothing, so without a GUI which apparantly has some network tools that actually go out and do some auto detection to find your wireless card, how is one supposed to connect to the internet from the command line?

---

### Post by halitech on 2009-02-03
2 things, what is the type of wireless card?

post the output of ```
lspci
``` and we can get a better idea of what steps you may need to get the wireless going

for the gui, I *think* if you put your cd back in and do
```
sudo apt-get install ubuntu-desktop
``` it *should* get it from the cd if available. if not we'll have to get the wireless working first unless you want to get the ubuntu desktop or alt install cds and reinstall.

Do you actually want the server install or will this be used as a desktop?

---

### Post by bernie888 on 2009-02-03
thanks halitech. I'll check out the nic info when I get home this evening.
As for the gui command, I did try that last night with the cd in and got the same error i get when trying to install anything - E Could not find package or something similar. Apologise for not quoting the exact message but I'm not at my home machine currently. Perhaps I need to mount the CD first before I can install a GUI from it? Not sure.

---

### Post by bernie888 on 2009-02-03
lspci shows....

Network Controller: Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller (rev 02)

Apologies if I mis-typed anything but seeing as I have no internet connection currently on the Linux machine I cant take screenshots or copy text to files :)

---

### Post by sandyd on 2009-02-03
see this for your hard config....

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

---

### Post by halitech on 2009-02-03
> **bernie888 said:**
> lspci shows....

Network Controller: Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN Controller (rev 02)

Apologies if I mis-typed anything but seeing as I have no internet connection currently on the Linux machine I cant take screenshots or copy text to files :)

probably needing the b43 driver as pointed out by carlee. hopefully it will work for you

---

### Post by bernie888 on 2009-02-04
Carlee, thanks for the link but how is that going to work considering I have no GUI. 

It says to "open the Hardware Drivers program (go to the System menu)".

I assume I can't do this from the command line can I?
 

> **carlee said:**
> see this for your hard config....

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

---

### Post by bernie888 on 2009-02-04
ok, so i managed to do one thing - mount a CD Rom using sudo /mount/media/cdrom. And I can list the ubuntu install files from there. Now how do I go about installing a GUI off of the CD?
I tried the standard command: sudo apt-get install ubuntu-desktop but it still fails with E: Couldnt find pacakage ubuntu-desktop.
I tried to search the CD Rom but I cant even find that file. Of course the search command i'm using may not be correct or perhaps the linux files are compressed or encrypted so that i can't see the names?
Is there some parameter I need to use to tell linux that I'm trying to install a package from a CD Rom?

---

### Post by garuhhh on 2009-02-04
hmmm..seems you're in a bad luck man :D

i would suggest working out the gui first (i also have no idea how to install network card in CLI), so why not install first a desktop version and then from there install the softwares that your system needs for it to become server.

also, 
```
sudo apt-get install ubuntu-desktop
```
will not work, since that needs to connect to internet for the files, that's why it says couldn't find package.

after having the GUI, then you can resolve the networking issue.

by the way, after installing a new desktop version of ubuntu, and after the networking issue has been resolved, update the software package list by
```
sudo apt-get update
```

-or-

if you managed to make your network working even before the gui, do this in the terminal
> sudo apt-get update
sudo apt-get install ubuntu-desktop

and to add a cdrom to your repositories,
> sudo apt-cdrom add
though i don't know if that will help you install a gui even before you have settled you internet connection.

hope that helps..

---

### Post by theozzlives on 2009-02-04
search the internet for wlanbroadcom.tar.gz and```
sudo apt-get install ndiswrapper
``` for starters

---

### Post by garuhhh on 2009-02-04
by the way, i got this from another page of the forum
> If you wanted a GUI then you want the Ubuntu Desktop CD or the Ubuntu Alternate CD because the Ubuntu Server CD is for a non-GUI system.

Servers aren't meant to have GUIs because they are a serious waste of CPU clock cycles. Perform a desktop install and NOT A SERVER INSTALL.
so, if you have no internet connection, the thing i could recommend is get a Desktop CD or Alternate CD, and install that first before tinkering with your internet connection. ;)

---

### Post by ratmandall on 2009-02-04
> **bernie888 said:**
> 
I new there had to be a reason Linux was still free :)

[http://www.gnu.org/philosophy/shouldbefree.html](http://www.gnu.org/philosophy/shouldbefree.html)

---

### Post by bernie888 on 2009-02-04
Ok, quick update. 
I can now at least copy files from my Vista partition to my Ubuntu linux partition. I installed Ext2 IFS for Windows. Its great - now I can at least download files from the internet and copy to linux for later installation.

Now, next task! Anyone know where I can get a GUI from in tar format or something similar so I can copy to linux and then install it finally? Doesnt appear to be on the install cd i have.
And how would I install it - do I need to add to a repository or package or something? Yep, I know I'm mixing terminology but coming from a 'click to run setup' person this is not easy! :)

---

### Post by garuhhh on 2009-02-04
i don't know of any tar which will give you gui.
what ubuntu will give you are a list of files which it needs to install ubuntu-desktop.

anywhere in your home directory, do this
```
sudo apt-get -qq --print-uris install ubuntu-desktop | cut -d\' -f 2 > list.txt
```
take the list.txt to your windows and download all the packages one by one. (they will be a lot) they will be *.deb files which you will install in your linux using dpkg
```
sudo dpkg -i *package_name*
```

---

### Post by Zill on 2009-02-04
bernie888:  I may well be missing the point here but it seems to me that you are simply wanting a standard install of Ubuntu with a GUI and all the other bells and whistles.  All versions do happily run server software but the specific server edition does *not* include a GUI by default, although a GUI *can* be added later.

However, for simplicity, I suggest you download the standard desktop edition ISO from the following site:

[http://www.ubuntulinux.org/getubuntu/download]("http://www.ubuntulinux.org/getubuntu/download")

If you then reboot using this CD this will take you into the Ubuntu Live CD GUI.  This has an install icon on the desktop which will then install Ubuntu (complete with Gnome GUI) to your HDD, either as the sole OS, or alongside an existing Windows installation.

Set up your networking using an ethernet cable to your router, then setup the wireless networking later.  If you hit any problems just shout and there will be plenty of help available on these forums. :-)

---

### Post by bernie888 on 2009-02-04
Hi Zill

Actually its not the gui thats most important. Howvever it appears its easier to get networking installed if you have a gui! That was my reasoning.
Connecting an ethernet cable directly is not an option. The wireless router is in a cupboard in the hall so unless i sit in the cupboard thats not going to happen :)  Never needed a wired connection for years but I guess at some point if this just doesnt work in linux, i may need to do something different.
Anyway, I've copied some wireless drivers onto my linuix partition and trying to install this NDISWRAPPER but getting errors....
-bash:ndiswrapper:command not found
Then I try to install it and back to the usual install error....
E:COuldnt find package ndiswrapper-common

So does the Server version not even come with ndiswrapper driver commands?
Any idea where I can get this command from?

Who'd have thought connecting to a network would be such a challenge!

---

### Post by Zill on 2009-02-04
bernie888:  I still feel that you would find things easier if you installed the standard desktop edition, rather than the server edition.

I can't comment on the ndiswrapper installation as I don't use wireless - I much prefer to use a simple ethernet cable. ;-)  You have said that it is difficult for you to use ethernet but can you not just run a cable, even temporarily, to link the router to your PC?

---

### Post by bernie888 on 2009-02-04
Zill, thanks for the suggestion. You know, maybe I will just give up on Ubuntu Server and install the Desktop Version instead. Seems that most people are recommending that. Guess Server edition just doesnt work very easily.
So, if I do just install the desktop version, is it going to be any easier to get wireless networking working or will i have exactly the same issues with ndiswrapper not being installed, etc etc. I dont really want to blow everything away to find I have exactly the same issue again.
Yes, its not impossible to hook up ethernet cable directly. I'll need to go and buy a long patch cable somewhere - not sure if i can get to a computer shop that sells these for a couple days. Or sit in the closet in the hall :)

---

### Post by Zill on 2009-02-04
> **bernie888 said:**
> ...So, if I do just install the desktop version, is it going to be any easier to get wireless networking working or will i have exactly the same issues with ndiswrapper not being installed, etc etc. I dont really want to blow everything away to find I have exactly the same issue again... :)

I guess you may still need to install ndiswrapper but you will then have a nice friendly GUI to help install software.  Just look for the Synaptic package manager in the desktop menus.  Then make sure you have your Ubuntu CD as a "source", as well as the usual Ubuntu repositories.

Alternatively, if you are using an ethernet connection, you can first install the required wireless packages directly from the internet repositories.

---

### Post by bernie888 on 2009-02-04
Zill, ok, going to do it tonight! Will put on Ubuntu 8.10 Desktop 64 Bit version insead of this Server Version and see if some things are a bit easier at least :)

---

### Post by Zill on 2009-02-04
bernie888:  Checking the info given earlier (in [this thread]("http://ubuntuforums.org/showthread.php?t=197102")), it looks like you *may* not need to install ndiswrapper to get wireless working.

> This process is vastly simplified in Hardy. The easiest way to do it is to open the Hardware Drivers program (go to the System menu in the top left corner of the screen, and click Administration, and then Hardware Drivers) and check the Broadcom B43 wireless driver box, and reboot.

Hopefully, this should get your wireless running quickly but if the B43 driver does not prove suitable for your purposes then you can install ndiswrapper later if desired.  Good luck. :-)

---

### Post by handydan918 on 2009-02-04
> **theozzlives said:**
> search the internet for wlanbroadcom.tar.gz and```
sudo apt-get install ndiswrapper
``` for starters

ndiswrapper is not needed for the OP's card. I have that exact card in my lappy, and b43 handles it nicely.

---

### Post by bernie888 on 2009-02-04
Hi Zill

Well, we're halfway there!
Did a re-install and used Ubuntu desktop 8.10 this time, so now I have the GUI up!
Now onto the main problem of connecting to the network.
Sadly its not as easy as the quote below as when I go to Hardware Drivers there is only 1 listed and its a Video driver.
I'll have to read back on some of the other ideas next.
But at least I can move around the system more easily now.
thanks


> **Zill said:**
> bernie888:  Checking the info given earlier (in [this thread]("http://ubuntuforums.org/showthread.php?t=197102")), it looks like you *may* not need to install ndiswrapper to get wireless working.



Hopefully, this should get your wireless running quickly but if the B43 driver does not prove suitable for your purposes then you can install ndiswrapper later if desired.  Good luck. :-)

---

### Post by Zill on 2009-02-05
bernie888:  Congratulations on your new installation. :-)

I suggest you now try connecting the PC and router with an ethernet cable as discussed earlier.  You may need to tinker with the networking settings slightly (eg gateway IP should be the router local IP address etc) but basically the default settings should connect you to the internet.

Once you are connected and can browse the web etc, leave the PC for a few minutes and then a new icon advising of new updates should appear in the top right panel of the desktop.  Click on this icon to start the update manager, entering your user password when requested.

When all the updates have been installed (it could take a while!), reboot.  Note that rebooting is not *normally* necessary after updating software in Linux except after kernel or xorg updates, but in this case it *may* help the system detect your wireless card.

Check the hardware manager again and see if the Broadcom card is now listed, enabling it if necessary.  If it can be enabled let's see how you get on when the ethernet cable is disconnected...

---

### Post by bernie888 on 2009-02-06
ok, spent another evening trying to connect Ubuntu to the network/internet and no joy yet. Been through a bunch of the solutions involving both broadcom and ndiswrapper installations. 
Currently when i type sudo iwconfig it does show the correct ESSID and Encryption Key etc for wlan0, but Access Point says 'Not-Associated' and there are 0 transmissions or receptions.
If I type sudo ifup wlan0, it says wmaster0: unknown hardware address type 801, SIOCSIFFLAGS: No such file or directory. Then a bunch of send_apcket: Network is down.
Any ideas what to try next?
thank you.

---

### Post by bernie888 on 2009-02-06
SUCCESS - we are on the wireless network!!

Holy smokes, that was a battle and a half :P
Still a couple of teething probs such as ubuntu hanging when i shutdown with an error about /etc/modprobe line entry and another on a b43 driver but forgetting that for a moment as its fairly minor - I'M ON THE INTERNET wirelessly now!

Can't say what the exact solution was as I tried so many things but one of the key issues was with the firmware I believe. Things improved in leaps and bounds after I followed the broadcom firmware installation instructions below - and thanks to everyone who helped. I did end up linking the PC to the wired connection to allow me to download these other drivers more easily (and yet, the wired connection was only a matter of plug and play!)

[http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation](http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation)

Bedtime now and for once I'm not annoyed and frustrated, lol!

---

### Post by Zill on 2009-02-06
> **bernie888 said:**
> SUCCESS - we are on the wireless network!!...
Great news :-)

Welcome to the wonderful world of GNU/Linux.  I shook off the Microsoft chains years ago and continue to enjoy learning about Linux, which just gets better and better!  Yes, you do hit problems occasionally but they can always be solved - there is lots of information and help available with free software, not least from the Ubuntu forums.

Stick with it and have fun!

---

### Post by garuhhh on 2009-02-06
congratulations! :D enjoy..

---

