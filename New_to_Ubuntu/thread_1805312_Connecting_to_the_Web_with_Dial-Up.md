---
title: "Connecting to the Web with Dial-Up"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by MottMan on 2011-07-15
I have two questions to ask although the first is by the far the most important. How can I connect to the internet with a dial-up connection with Ubuntu? I've tried several apps that either didn't work on install (libraries missing) or didn't do what was required (gnome-network-admin would've worked if they hadn't taken away the connections tab!). 

So I'm asking for anyone to explain to me (preferably as descriptive as possible) how can I connect to the internet using a dial-up connection. 

My second question, which is much smaller, is how do I see all executables? In Windows you use the start menu of course but I see no way of doing it in Ubuntu (11.04 by the way). I'm not running Unity due to my computer being old so the launcher and app search features are disabled. 

Thanks for reading. My main question is the dial-up problem. Hopefully someone can help. Thanks in advance.

---

### Post by sammiev on 2011-07-15
Read [this]("http://ubuntuforums.org/showthread.php?t=1589966&page=3"), post number 22. Worked great for me. GL :)

---

### Post by MottMan on 2011-07-15
I don't have access to broadband however. I can transfer apps from one of my computers (that is connected to dial-up) onto another if necessary. Is there any solution for that scenario?

---

### Post by varunendra on 2011-07-16
> **MottMan said:**
> How can I connect to the internet with a dial-up connection with Ubuntu?
Install **wvdial** from within the installation cd, if it is not already installed (you can check by entering wvdial command in the terminal). To install it:

[LIST=1]
[*]Insert your ubuntu installation cd and browse to **pool/main/w** directory in the CD.
[*]There you should see two folders: 1) **wvdial,** and 2) **wvstreams**. Your target is to install the wvdial package located in the wvdial directory. But in order to successfully install, it will need those packages in wvstreams directory to be installed first. Hence the next step-
[*]Install (by double-clicking) all three packages in the wvstreams directory first. You may need to install them in some particular sequence that you can easily figure out by yourself.
[*]After installing the above three packages, install the wvdial package in the last from the wvdial directory.
[/LIST]
While installing the final (wvdial) package, you may encounter an "Unhandable Error Due to Apt" error. Just ignore it, or hit "Reinstall" button to be extra sure :).

If you like a GUI instead of commandline to setup your connection in wvdial, you can install **gnome-ppp** package from synaptic which is nothing but a GUI frontend to wvdial.


> **MottMan said:**
> 
My second question, which is much smaller, is how do I see all executables?
I'm not sure about this since I haven't installed natty myself, but if you are using classic gnome desktop, then these should be under "Applications" and "System" menus. Not all the installed apps appear in these menus as many of them are commandline apps - if you didn't already know it.

---

### Post by lkraemer on 2011-07-16
Are you trying to use a WinModem, External Hardware - Serial Modem,
or USB Modem?

Have a look at Posting #3 here:
[http://ubuntuforums.org/showthread.php?p=10197883#post10197883](http://ubuntuforums.org/showthread.php?p=10197883#post10197883)

You should be up and running in less than 30 minutes.

lk

---

### Post by grahammechanical on 2011-07-16
I used to use a dial-up serial modem. To connect I used a utility called pppconfig. I did not need to download it. I just typed sudo pppconfig in a terminal and a text based utility loaded. I then put in my ISP details. If it does not work then try altering the settings.

There is a GUI version of this in the software centre. Here is a link to the home page.

[http://www.gnome-ppp.org/](http://www.gnome-ppp.org/)

Regards.

---

### Post by ieee488 on 2011-07-16
Back when I was on dial-up, I used **scanmodem** to tell me if my dial-up modem is supported in Linux.
[http://techplusnj.com/linux/linux_dialup.html](http://techplusnj.com/linux/linux_dialup.html)

If your dial-up modem isn't recognized by **scanmodem**, you have a long road ahead of you.

---

### Post by MottMan on 2011-07-16
Thanks guys. I'll give them a try and see what happens. My modem drivers are actually "acting up" (to say the least) and am taking my computer back to some local computer techs. 

After that is sorted out I'll try the suggested methods and update on my progress.

Thanks :)

---

### Post by ieee488 on 2011-07-16
Huh???

What "modem drivers"?  For Windows?
It isn't brain surgery. You should be able to do it yourself.

---

### Post by MottMan on 2011-07-16
The computer techs put the wrong drivers on my computer that won't uninstall and when I do they install themselves back on. My driver disc attempts to download the correct one's but then the wrong drivers install over-top of them. 

It's a strange problem that is difficult to explain. My ISP suggested that I just take it back. 

In short, yes, I should be able to do it myself, but other problems are preventing me from doing much.

---

### Post by lkraemer on 2011-07-16
MottMan,
WOAH HOSS!!!!  What are you talking about?  Didn't you install Ubuntu?
If you are trying to use ndiswrapper, to load some Windows Drivers, 
instead of trying to follow a proven guide, you need to be telling us what
you have done.  It's hard to see what you are doing from my place!

We need the following:
1.  A listing of your HISTORY of commands.  Get it by Opening a Terminal
    and doing:
    ```

     pwd
     history > myhist.txt
    
```
    
2.  A listing of lsmod by doing:
    ```

    pwd
    lsmod >> myhist.txt
    
```
   
3.  A listing of:
    ```

    pwd
    ndiswrapper -l >> myhist.txt
    
```
    Then attaching the file with the results

Then well assist you in getting it working.

lk

---

### Post by MottMan on 2011-07-16
This problem is on Windows. I have done nothing other than try different dial-up apps on Ubuntu.

---

### Post by lkraemer on 2011-07-17
MottMan,
If I read your posting correctly, your first question was:
> 
How can I connect to the internet with a dial-up connection with Ubuntu?

How did Windows get worked into the posting?  Windows questions are best
answered by Gates & Company or your local Wonder$ GURU........

Your Second Question was:
> 
My second question, which is much smaller, is how do I see all executables?

which also states nothing about Windows..........

I do believe your first Ubuntu question was properly answered.

As to the second question........Ubuntu executables are called Binaries
or BIN files, just as the Other OS's Executables.....So Open a Terminal
or Console and do:
```

cd /
pwd
sudo updatedb
locate *.bin
cd /usr/bin
pwd
ls -alt
cd /
pwd
cd /usr/local/bin
pwd
ls -alt
exit

```
Will show you the bin files.

My suggestion is to forget Windows, Boot the Ubuntu LiveCD, do a FRESH Install of Ubuntu, assuming
the LiveCD worked properly, and proceed with learning something that will be GREAT!  Once you have
a bit of time under your belt you'll never go back. 

I'd also suggest finding a different Windows GURU........until you have done what is stated above.
 
lk

---

### Post by ieee488 on 2011-07-17
> **MottMan said:**
> This problem is on Windows. I have done nothing other than try different dial-up apps on Ubuntu.

It sounds like you don't even have dial-up working in Windows.

Getting dial-up working in Windows is not a big deal. Install the driver for the dial-up modem, and that is it.

If you are not able to connect to your ISP in Windows, then you had better be able to do that first, before trying to do it in Ubuntu. This is my suggestion which is contrary to what is advised above. Getting your dial-up working in Windows will help you understand what authentication and username/password your ISP requires which is also necessary for Ubuntu.

Find someone to help you with Windows.

---

### Post by lkraemer on 2011-07-17
MottMan,
Desktop or Laptop?  Is the Modem a PCI Card (WinModem) or ISA, or PCMCIA,
or USB, or EXTERNAL USB or EXTERNAL Serial Hardware Modem?

What Version of Wonder$?

Can you Find the Control Panel Wonder$ Application?
Can you Locate Device Manager Wonder$ Application?

Locate the Modem in SYSTEM, HARDWARE, DEVICE MANAGER and Expand the Modem.
LEFT CLICK on the Modem to Highlight the Modem, then REMOVE the DRIVERS.
Then close all Open Windows, Shutdown.  Remove the PCI WinModem.
Power up and go back to Device Manager.

Look for Modem or Drivers you were talking about.  Most likely nothing will be located
unless you got something really strange going on.  Now Power Down again.  Plug the PCI WinModem
in a different PCI Slot.  Power up and go to Device Manager.  Look for Modem.  See if the
Drivers were installed and if they are correct.  You can Update the Drivers, either by Web,
or from the associated CDR that came with the WinModem.  The Web is probably best choosing
the Manufacture's website, or you can download from Manuf. and save in Downloads subdirectory,
and BROWSE to that Subdirectory.

Look for any YELLOW QUESTION MARKS in Device Manager.  Everything needs
to be good, meaning all have Drivers.  Any RED or YELLOW SYMBOLS means problems need to be resolved.

Exit and Test your Modem.  All you need is your ISP Phone Number, your
ISP [email]Login@copper.net[/email] and your ISP Supplied PASSWORD.  Set up your 
Internet Options from Control Panel and dial the Number.  If I remember correctly there is
a Wizard to assist your setup.  Run it and it creates what you need, but I haven't used Wonder$ since
Ubuntu 7.04 came out......ZIT ZOT.....Slick as SNOT!   What is the problem?

Then Proceed to Linux, but if it is a WnModem you're in for a rough ride.  Start at [www.linmodems.org](www.linmodems.org)
with their scanmodem script.  Send Marvin and the fine folks there your script results in PLAIN TEXT ONLY
as they DO NOT ACCEPT any other format.  So set your EMAIL Accordingly......for PLAIN TEXT.


lk

---

### Post by MottMan on 2011-07-17
Thanks guys. I had no problems with setting up dial-up on Windows until my local computer tech (for some reason) installed improper drivers that will not remain uninstalled. 

I have contacted my ISP and they went through all the possibilities and have concluded that the best thing to do is to take it back to the tech. Calling them they gave me several options on how I could fix it, all of which failed, and have offered to fix it for free. 

It's difficult to explain my problem beyond that but I won't have my computer back for a few days. When I get it back I'll try the different solutions here to connect to dial-up with Ubuntu.

---

### Post by sammiev on 2011-07-17
> **MottMan said:**
> Thanks guys. I had no problems with setting up dial-up on Windows until my local computer tech (for some reason) installed improper drivers that will not remain uninstalled. 

I have contacted my ISP and they went through all the possibilities and have concluded that the best thing to do is to take it back to the tech. Calling them they gave me several options on how I could fix it, all of which failed, and have offered to fix it for free. 

It's difficult to explain my problem beyond that but I won't have my computer back for a few days. When I get it back I'll try the different solutions here to connect to dial-up with Ubuntu.

Windows and Linux use totally different drivers and one has no effect on the other. GL :)

---

### Post by MottMan on 2011-07-19
I got my problem fixed. My modem had somehow died on me. A new one was installed and Windows has got dial-up working now.

I was going down the wvdial route for Ubuntu but stumble when I get to this:


scott@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
scott@ubuntu:~$ wvdial --chat
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.


Is it just my Linux drivers it can't find? This would make sense since I haven't installed any. I used scanmodem and it found my modem. How I do find the drivers?

---

### Post by lkraemer on 2011-07-19
Now you are back to:
[http://ubuntuforums.org/showthread.php?p=10197883](http://ubuntuforums.org/showthread.php?p=10197883)
Posting #3.

What drivers did Marvin suggest from your submission?

lk

---

### Post by MottMan on 2011-07-20
hcfpcimodem-7.80.02.05full_k2.6.38_8_generic_ubuntu_i386.deb.zip

This wasn't available so I tried the generic package: [http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-1.21full/hcfpcimodem_1.21full_i386.deb.zip](http://www.linuxant.com/drivers/hcf/full/archive/hcfpcimodem-1.21full/hcfpcimodem_1.21full_i386.deb.zip)

Wvdial still wasn't working so I then tried to run the hcfpcimodem and got an error: 
dev/hcfpcidiag0: No such file or directory
hcfpcidiag: Modem Expert open failed.


I am, again, at a loss...

---

### Post by pottzie on 2011-07-20
Just want to comment that I use dial-up when I'm at work (and the boss isn't looking....)

 wvdial works for me, but I have to use a serial modem. I think MottMan says he has one. I have an old but trusty US Robotics modem that I got for ten bucks from a local computer shop.

---

### Post by lkraemer on 2011-07-21
MottMan,
If Marvin and the folks at [www.linmodems](www.linmodems) suggested that you use:
hcfpcimodem-7.80.02.05full_k2.6.38_8_generic_ubuntu_i386.deb.zip
I'd stick with what they recommend.

OK you have downloaded the hcfp.......i386.deb.zip and have it in
your Downloads subdirectory.  Create a subdirectory named ModemDriver, then double
left click on the .deb.zip file and extract it to ModemDriver.
Now you will have the .deb file.  You can then copy this file to where
it needs to reside, in case you want to properly remove it, with these
commands:
```

sudo updatedb
locate *.deb

```
Look for all the *.deb files.........assume /var/cache/archives  But in Debian 6.0
mine is /var/cache/apt/archives ................since you never have told us what
Distro or version you are using.......................
```

cd ~/Downloads/ModemDriver
sudo cp *.deb /var/cache/archives

```
Then to install the deb use:
```

dpkg -i hcfp*.deb

```

Then run the wvdial configure program again.
```

sudo wvdialconf /etc/wvdial.conf

```
and wvdial should locate and configure your modem.

Now you are back to:
[http://ubuntuforums.org/showthread.php?p=10197883](http://ubuntuforums.org/showthread.php?p=10197883)
Posting #3.   Now.......this....for some reason seems very familiar...
Where have we seen it before......???

lk

---

### Post by Je Et on 2011-10-30
What you should do has been suggested earlier. You should download and run _**scanmodem**_. All the information you need to compile and install your modem, if it finds your modem is compatible with Ubuntu, will be found in a folder called **'modem'**.

---

