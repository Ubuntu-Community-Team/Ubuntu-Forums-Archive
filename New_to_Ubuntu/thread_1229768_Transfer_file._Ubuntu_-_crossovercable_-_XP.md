---
title: "Transfer file. Ubuntu - crossovercable - XP????"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by moose4204l on 2009-08-02
ok i searched and tried to follow a few peoples advice but I cant figure out how to do this. I need A STEP BY STEP INSTRUCTION on how to do this if you can please. This is my situation. I want to transfer my files  from an Ubuntu machine to a Windows XP machine USING A CROSSOVER CABLE. I have a wireless router in my house as well but I want to use the CROSSOVER CABLE

Please help. 

Thanks

--Moose

---

### Post by jacklinux on 2009-08-02
> **moose4204l said:**
> ok i searched and tried to follow a few peoples advice but I cant figure out how to do this. I need A STEP BY STEP INSTRUCTION on how to do this if you can please. This is my situation. I want to transfer my files from an Ubuntu machine to a Windows XP machine. I have a wireless router in my house as well.

Please help. 

Thanks

--Moose
You could do the following;


[LIST]
[*]Email the file(s)
[*]Use a USB flash drive
[*]Upload to a free file share host
[/LIST]
Hope these help.

---

### Post by moose4204l on 2009-08-02
That wont help -- no offense

---

### Post by jacklinux on 2009-08-02
I don't see why you need to do a Cable when there are plenty of other faster methods

---

### Post by moose4204l on 2009-08-02
I basically want to do a back up of my laptop and I dont have an external hard drive, big enough flash drive, and my wireless drops out sometimes in the middle of transfers. All I have is an crossover cable and I also want to know for learning purposes. Hope this explains it.:D

---

### Post by jacklinux on 2009-08-02
im not sure that you can do that.
Plus if your backing up ubuntu it won't work onto Windows
i'll look around for any tutorials

---

### Post by moose4204l on 2009-08-02
I can make an image of the hard drive and stuff and save as .iso and transfer it to windows. Re install ubuntu, dual boot, mess it up, etc, then transfer the .iso back over and restore it.

---

### Post by jacklinux on 2009-08-02
Could work, try it. worst you do is **** up the PC.

---

### Post by moose4204l on 2009-08-02
Thats why I need to know start to finish step-by-step instructions on how to transfer files from ubuntu to XP with a crossover cable. All other peoples forums didnt help me or started in the middle or something like that. Basically, heres ubuntu, heres XP, heres Crossover cable. What do I do?

---

### Post by jacklinux on 2009-08-02
> **moose4204l said:**
> Thats why I need to know start to finish step-by-step instructions on how to transfer files from ubuntu to XP with a crossover cable. All other peoples forums didnt help me or started in the middle or something like that. Basically, heres ubuntu, heres XP, heres Crossover cable. What do I do?
might help;

[http://www.microsoft.com/windowsxp/using/setup/getstarted/bott_fstw.mspx](http://www.microsoft.com/windowsxp/using/setup/getstarted/bott_fstw.mspx)

---

### Post by LewRockwell on 2009-08-02
I did a quick and dirty search for "crossover linux windows" and came up with a bunch...

one of which would be this:

[http://www.techspot.com/vb/topic18935.html](http://www.techspot.com/vb/topic18935.html)



I will also note that I use Clonezilla and one of these([http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)) and any old hard drive I've got laying around to achieve what you're trying to accomplish

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

.

---

### Post by irv on 2009-08-02
Don't beat your head against the wall, Just go out and buy a 1TB USB Drive, that's what I did. You can find them for $99 if you look. Just think of all the files you can backup then. I backup three computer on mine.

---

### Post by moose4204l on 2009-08-02
yeah thats what i want to do eventually but i am poor...i also want to know for learnign purposes because I want to be a Tech guy..right now I am studying for CompTia A+

---

### Post by theboomboomcars on 2009-08-02
Do you have SAMBA set up?  

SAMBA allows your linux computer to talk to yor Windows computer through the network.

---

### Post by moose4204l on 2009-08-02
no i dont...i dont really want to unless thats the only way..i just want to transfer files via crossover from ubuntu to xp

---

### Post by niteshifter on 2009-08-02
Hi,

Step-by-step isn't likely to be forthcoming (as you can see) because it's an arduous process, requiring downloads and modifications to networking on both ends. That and there's several different ways of doing this for both ends. None of them what one could call simple.

And in the end you're going to be disappointed. Windows probably is not going to like some filenames your Linux system provides. More trouble will come when you get around to making an .iso - there are limits to ISO9600 for path/file naming, length of path, depth - and these limits vary as to what extensions to ISO9660 are provided / used.

Then there's the problem with Ubuntu's file permissions: rolling the files over to Windows will change them.

In short - as a backup means this - just transfer files - isn't going to work.

Do you have a working CD/DVD burner? If so check out using System Rescue CD [here]("http://www.sysresccd.org/Main_Page") as a means of backing up your Ubuntu system. It can be installed on a USB thumb drive, which frees up the CD/DVD drive or if you have enough RAM can be booted from a CD and told to run totally in RAM, freeing the CD/DVD drive. You can backup direct (via partimage) to CD/DVD.

Or check out remastersys [here]("http://www.remastersys.klikit-linux.com/ubuntu.html"). That may work out well for you, depends upon how much data you have in Ubuntu.

---

### Post by egalvan on 2009-08-02
A CROSS-OVER cable is simply a poor-man's ETHERNET SWITCH.
A standard UTP wired for directly connecting two computer ethernet ports.

They were widely used back in the day when simple hubs cost $100 per port, and switches could hit $1000 per port.

They connect two ETHERNET ports to each other, and allow them to communicate at full speed, duplex.
Most network techs keep a couple in their tool boxes.
They are very useful for fast connects, and to isolate NIC/Switch/router problems.



Using one is NO DIFFERENT than using a network-connected PC.
The machines will be totally unaware that this is not simply a (very small) network.

And NO IT WILL NOT MESS UP YOUR MACHINE.
At most a mis-wired will not work at all.

But YES WINDOWS DOES NOT PLAY NICE WITH ALL LINUX FILE NAMES.
*nix allows some characters that are verboten under MS-Windows.
Be aware of this.

Here are two simple how-to's that I found here...
the url point to the original thread, if you want to peruse the whole thing...
And they are not in any order.

FIRST ONE
> [http://ubuntuforums.org/showthread.php?t=1188222](http://ubuntuforums.org/showthread.php?t=1188222)

 Re: access windows from ubuntu

Go to Places > Connect to Server

  Service type - Windows share
  Server - IP of Windows machine
  Share - c$
  User name - Administrator

Click 'Connect',
enter the Administrator password and you're good to go.

SECOND ONE
> [http://ubuntuforums.org/showthread.php?t=1217556](http://ubuntuforums.org/showthread.php?t=1217556)

excelent from ugm6hr

Re: Share Files XP -> Ubuntu

In simple terms (assuming on same network):

1. Share the folder with your files from Windows.
    From XP File Manager, Right-click folder, select "Properties"
    Select radio button for sharing.
    Type <xpshare> in share name (something with no spaces, all lower case)

2. Find out IP address of XP computer.
     From XP, Click the networking icon in System Tray (bottom right) and select Support tab.
     Read and record IP address 
(e.g. 192.168.0.2 in example bel
ow)

3. Access share from Ubuntu
     From Ubuntu, open Nautilus (File browser)
     Change nautlus view to allow text entry of location
       (To the left of the file location, there is a button that looks like a page of text.
        It says, "Toggle between button and text location" - click it.)
     Enter location as smb://192.168.0.2/xpshare
     You should now have read access to the directory you have shared



Yeah, 1000th post!
:popcorn:

---

### Post by mpm on 2009-08-02
Any idea what IPv4 settings one would use when connecting the crossover cable?

---

### Post by cwsnyder on 2009-08-02
IPv4 or IPv6 does not matter, as long as they match.

Another alternative, which I use more than the method outlined, is to get one of the (under $20USD) USB-to-hard disk cables, remove the drive from the old computer, plug it into the USB-to-hard disk cable and the USB end into the computer.  Either use the power adapter which comes with the cable or an extra drive power cable from the new computer for the 'old' drive power.  Now reboot and check your BIOS settings to see if the 'old' drive is recognized connected to your 'new' computer.  The 'old' drive should show up on the desktop of Linux machines, or in 'My Computer'/Windows Explorer on Windows machines.

Drag and drop your files from the 'old' machine to a folder on the 'new' machine.

Done.

---

