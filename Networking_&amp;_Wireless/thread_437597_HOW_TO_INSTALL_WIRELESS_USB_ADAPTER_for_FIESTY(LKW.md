---
title: "HOW TO INSTALL WIRELESS USB ADAPTER for FIESTY(LKW-G750)"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by philidox on 2007-05-08
HOW TO INSTALL WIRELESS USB ADAPTER for FIESTY(LKW-G750)

newb notes:  I never had to use the command line to install this wireless adapter, it was all GUI.   When you plug in your wireless adapter the light may or may not come on, so do not feel that your usb ports or the adapter itself is broken because the light for the adapter will come on after your installation.  Your going to need a connection to the internet to start off with because you'll need to download the drivers and software.(duh!)  You may have to unzip or extract a downloaded driver file.  

Prerequisite:  
a. You must have the extra repositories enable.  If you do not know how go to [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) and look at the section titled “How to apt-get the easy way (Synaptic)”
b.  Download the DRIVERS for your wireless adapter, or recover them from you installation cd. You'll need two things the .exe file which is probably in the utility folder(this is the file designed for windows easy installation) and the .inf file, which is probably located in the drivers section.  I use the Windows XP version.

STEP 1:
Go to System>>Administration>>Synaptic Package Manager

STEP 2
Click on the Search icon, and type in “ndiswrapper” and hit “Enter”

STEP 3
Mark the following for installation by clicking on the box on the left hand side of the package name and selecting “Mark for installation”.
ndiswrapper-common
 ndiswrapper-source
ndiswrapper-utils-1.9
Then click apply and click apply again to install.

STEP 4
Go to Application>>Add/Remove... Then type in  the search bar “Windows Wireless Drivers”.  An application called “Windows Wireless Drivers” should be there for you to install.  Install it by clicking on the box to the left side of the application name.  Click “Apply” and then click “Apply”.  You'll probably get a message about its authentication just click “Apply” to accept.

STEP 5(if you already have wine installed skip this step)
Go to Application>>Add/Remove... Then type in  the search bar “Wine”.  An application called “Wine” should be there for you to install.  Install it by clicking on the box to the left side of the application name.  Click “Apply” and then click “Apply”.  You'll probably get a message about its authentication just click “Apply” to accept.

STEP 6
Go to location of the .exe file for your wireless adapter and open it with “wine”.  
newb notes: If you have never use wine before it will not be in your list of application to open your .exe file with.  So just right click the .exe file and use the “Open with Other Application...”.  Then click on “Use a custom command”  In that search bar type “wine” and hit Enter.  When the installation wizard pops up just keep clicking next as though you were installing for Windows.  

STEP 7
Go to System>>Administration>>Windows Wireless Drivers.  Click “Install New Driver”.  Click on the rectangular box to the right of “Location” and navigate to the .inf file you got from the download or  installation cd for your wireless adapter. Double click on the .inf file and hit “Install”.  A new icon should appear under the “Currently installed Windows Drivers:”.  Do not worry about whether it say yes or no for Hardware present.  Click close.

STEP 8(sometimes this step is necessary)
Reboot your computer.  When your computer reboot.  You'll see the light on your wireless adapter should be on and you can click on your network icon to see what networks are available for you to connect to.

final notes:  I did this process on three different computers all using ubuntu, so I'm pretty confident it will work for you.  Keep in mind I used the same adapter for all three computers.  If you absolutely need your wireless adapter to work you should think about buying the one I used.  Its super cheap.  I got it for 15 bucks.  Enjoy!

---

### Post by twisted_hick on 2007-05-13
Hi I followed your instructions and can not get the ndisgtk window to say open it starts to run then it closes> Traceback (most recent call last):
  File "/usr/bin/ndisgtk", line 309, in <module>
    NdisGTK()
  File "/usr/bin/ndisgtk", line 111, in __init__
    self.setup_driver_list()
  File "/usr/bin/ndisgtk", line 140, in setup_driver_list
    self.get_driver_list()
  File "/usr/bin/ndisgtk", line 168, in get_driver_list
    driver_name = p.search(line).group()[:-1]   # strip trailing space
AttributeError: 'NoneType' object has no attribute 'group'
  heres the output from running it in terminal thanks anyone one for help with this  the usb wifi adapter is a netgear wg111t

---

### Post by philidox on 2007-05-13
> **twisted_hick said:**
> Hi I followed your instructions and can not get the ndisgtk window to say open it starts to run then it closes  heres the output from running it in terminal thanks anyone one for help with this  the usb wifi adapter is a netgear wg111t
Could you clearify just a little.  I'm do not remember typing anything about ndisgtk window but when you post your reply ensure to include what version of ubuntu your using and on which step did you get stuck on.  Step 1, step 2, etc...  Thats why I numbered them.  If your using an adapter other than the on I"m using then it may not be for you however I"m always willing to help you figure it out.  Just hit me up with that info and we'll see how to get it working.

---

### Post by lxstoian on 2007-05-14
But what if I don't have an internet connection on the pc I want to install the usb adapter?

---

### Post by philidox on 2007-05-15
We'll that is a tough one.  You can manually download them from a computer with internet and then do a local install but your going to have to get the repositories and packages to install it the way I put out.  Remember this is not the only way to get your adapter working its was just the easiest for me because it did not require ANY command line.

---

### Post by philidox on 2007-05-30
This is a copy of the pm I got from Dr.C.  I'm not blowing my own horn, just want ubuntu users to see that it works, even with another USB wireless adapter.


 A Few Words of Appreciation
I was about to give up on establishing a wifi connection out of my newly installed Ubuntu OS until I read your "how-to" article: HOW TO INSTAll WIRELESS USB ADAPTER FOR FIESTY (LKW-G750). Since I followed your instructions (but with an Encore ENUWI-G2 adapter), I have experience almost flawless wireless operation). Thank you so much for your superb instructions!

Appreciatively,

Chard Crosby
Newport, Oregon
USA

---

### Post by jalirious on 2007-06-11
Alright Matey, trying to get my crappy talktalk wireless usb dongle (SNU5630NS, apparently a rebranded Phillips device) to work on feisty. When I open the setup.exe with wine it looks ok, until ~the end when I get the error

Unhandled Exception

Error Number 0x80040707
Description : D ll function call crashed: Install. EnumerateDevice

Setup will now terminate.

[OK]


Any thoughts? Thanks in advance, Ben.

---

### Post by philidox on 2007-06-13
Sorry man not a clue

---

### Post by philidox on 2007-06-28
Ok i found a way for the installation of your wireless card to install good every single time.  I'll make a youtube video showing step by step instructions.  When I do i'll post the url.

---

### Post by t4thfavor on 2007-06-28
He could use a windows box to get the .sys file from the disk. 

Pop the cd into a windows disk, and run the exe let it install the device. Look at the device properties then find out where the driver is by doing a search (or if the exe just extracts the sys to a tmp folder its even easier) then use your usb key (assuming you have no network) to transfer the relavent files. 

Note: most driver cd's have the bare inf and sys files somewhere on them mine was in a folder called Manual (I guess meaning manual install and not product manual).

Just a few thoughts.

---

### Post by philidox on 2007-07-03
Ok guys I have been drowning myself in ubuntu since my quest to upset the Microsoft universe has began and I am now ready to handle what you guys can throw at me with a few exceptions of course.  I have been installing wireless adapters left and right thru gui and command line.  The only adapter I have not work with yet is internal which I will buy today and have fun with on arrival.  But as far as usb and pcmcia(card slots) card gimme what you got.  Cannot guarantee anything but I feel pretty confident I can hook you up.  By the way I got a skype in number just for you ubuntu lovers.  If you do not know what skype is your missing out they just started a sick offer that blows vonage outta the water.  I purchase a local U.S number to make/receive all the calls to U.S and Canada for an entire year for only 29.99.  Here is my number if you get one on one help over phone: 5806094614

---

### Post by Racheado on 2007-07-10
> **philidox said:**
> This is a copy of the pm I got from Dr.C.  I'm not blowing my own horn, just want ubuntu users to see that it works, even with another USB wireless adapter.


 A Few Words of Appreciation
I was about to give up on establishing a wifi connection out of my newly installed Ubuntu OS until I read your "how-to" article: HOW TO INSTAll WIRELESS USB ADAPTER FOR FIESTY (LKW-G750). Since I followed your instructions (but with an Encore ENUWI-G2 adapter), I have experience almost flawless wireless operation). Thank you so much for your superb instructions!

Appreciatively,

Chard Crosby
Newport, Oregon
USA

Hi philidox, can you help me to contact Chard Crosby? I have the same Encore Adapter but this instructions did not work in my Ubuntu Feisty =( I would like ask him for help...  Thanks a lot

ps sorry by my poor english writting, I can do it better in spanish =)

---

### Post by Soviets on 2007-11-22
hello,
I follow your guide right up to step 7 and stop because the lkw-g750 rev B drivers on Linkskey download page is not a available (if you could please provide the rev B driver it might slove my problem) do i try to use rev 1.10 and it said i had a invalid driver for all four windows version and internet didnt work but when i tried the vista driver it said (Hardware present=yes) but internet does not work , i try to reinstall all driver but it did not work, i do not no what the problem is please help, i use ubuntu 7.10

---

### Post by dynamethod on 2007-11-22
id just like to say from experience of about an hour ago, NEWBIES BE VERY VERY VERY CAREFUL AND BACKUP BEFORE TRYING TO MESS WITH THIS, i tried installing my usb wireless adapter about an hour ago, and for that i ended up with a kernel pannick, and now am currently in the process of reinstalling my OS after formatting the drive, search my profile for my posts about this if you want

---

