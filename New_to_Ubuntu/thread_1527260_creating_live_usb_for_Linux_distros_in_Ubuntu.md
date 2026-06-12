---
title: "creating live usb for Linux distros in Ubuntu"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by beew on 2010-07-09
Hi,

I am wondering if there is an easy way to create live usbs from isos for other  Linux distros such as Debian and Fedora in Ubuntu. The Ubuntu startup disk creator only works for Ubuntu isos.

I know about Unetbootin, but it doesn't have an option to add persistence to the live usbs that it creates.

I have looked at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)  But almost all of it is about creating live Linux  usbs in windows!It seems incredible that there are so many neat and convenient tools created by Linux developers  for windows users but none for Linux users! Why doesn't Linux have something like the universal Usb installer?[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/):confused:
It just doesn't make sense that if a beginning Ubuntu user such as myself wants to make a live usb for Fedora or Knopix with persistence (so unetbootin wouldn't work) , the easiest way would be to get a hold of a windows machine and do it there!

As a side note, I notice a peculiar behaviour of Ubuntu's startup disk creator (10.04). If the iso is located at the download folder then the option for adding persistence to the usb is greyed out, but it works ok if the iso is located in other places (say the Desktop). Does anyone else experience that?

Cheers

---

### Post by audiomick on 2010-07-09
Hallo.
I have only made one USB installler, and it was the "classic situation" that you have read about, i.e. making an  Ubuntu installer from a windows machine,  however I think you will find useful information here
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

hope that helps.

---

### Post by C.S.Cameron on 2010-07-09
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Ubuntu, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

This should also work using a casper-rw file copied from a persistent usb-creator install.

I have not tried this on other Linux distros.

---

### Post by bodhi.zazen on 2010-07-09
+1 unetbootin, IMO that is the easiest method.

---

### Post by C.S.Cameron on 2010-07-09
Another thought, most modern computers see a flash drive as just another hard drive.
You should be able to do a Full install of most distro's to USB just like to hard disk.
I would suggest disabling the internal HDD before attempting this just to be safe.

---

### Post by beew on 2010-07-26
> **bodhi.zazen said:**
> +1 unetbootin, IMO that is the easiest method.

 Easiest? Only if you want a live usb without persistence. The easiest way to create a live Fedora usb with persistence, for example, is when you already have Fedora installed or, gapse, do it with Windows using Fedora's live usb creator. 

That is what I don't get, developers for different Linux distros create clean and easy to use programs to create live usbs for their own distros, but ONLY for Windows users! If you have other distros installed and you would have to go through a lot of conf file editing and command line hell which in the end may not even work! I gather it would be the same story if you try to make a Ubuntu live usb with persistence in  Fedora.

---

### Post by beew on 2010-07-26
C.S.Cameron,

Thanks for the detail instruction. I haven't had a chance to try it until last night so I sort of left the thread dangling.

I am trying to create a live USB with persistence for Fedora in Ubuntu and the only tool available is unetbootin. 

Your method as described only works for Ubuntu live.  The line you need to edit read like this in the Fedora live USB

"kernel /ubnkern
append initrd=/ubninit root=UUID=4729-5519 rootfstype=auto ro liveimg quiet  rhgb rd_NO_LUKS rd_NO_MD"

I am not sure what would be the appropriate way to edit it, or if editing this line would work.

I have a dual boot system so I can do this easily if I go to the Windows partition and create the USB using Fedora's live USB creator there, but I would like to do this in a Linux environment and see if that works.

Also, I am using Ubutu10.04. If I want to create a Ubuntu live USB with persistence using Ubuntu there is really no need to use unetbootin and then go through the trouble of editing configuration files. Use the built in start up disk creator in system > administration. I only wish they have something more universal so they can do this with other distros as well. The Linux community actually have already invented a powerful and easy to use universal USB installer for mainly Ubuntu but a few other Linux distros as w
ell,--no Fedora though,-- but alas, it is only available in Windows, of course!  [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by beew on 2010-07-26
audiomick

Thanks for the links. But they apparently only work for creating Ubuntu live USBs. As I said, in Ubuntu10.04 the cleanest and easiest way to create a live Ubuntu USB with persistence is to simply use the start up disk utility (you may find the persistence box greyed out if you start the utility and it finds the iso in the default "Downloads" directory, you can rectify this by simply moving your iso to another directory say Downloads/Ubuntu_live and make it looks for the iso, this is probably a minor bug)Now you may need to use the method described in these links if you try to make a usb for earlier versions of Ubuntu in your 10.04 box, though I doubt it, but I haven't tested with earlier versions.

---

### Post by snowpine on 2010-07-26
beew, you can create a Fedora Live USB from any Linux using the terminal command "dd":

[http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo#Command_Line_Method_-_Linux_only](http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo#Command_Line_Method_-_Linux_only)

If you really prefer a GUI for whatever reason, the [source for liveusb-creator]("https://fedorahosted.org/releases/l/i/liveusb-creator/liveusb-creator-3.9.2.tar.bz2") is freely avaiable; I see no reason why it should not work in Ubuntu.

---

### Post by beew on 2010-07-26
snowpine

Thanks for the link. I will try creating the Fedora usb creator in ubuntu  from source and see if it works.

In the mean time, I will try a bit of  reverse engineering. I will create a Fedora USB with persistence using the windows tool and then check the syslinux file and change whatever need changes in the one I created using unetbootin and see if it works. Not very elegant in that I would need to use windows to this Linux job but it seems like a sound idea.

---

### Post by snowpine on 2010-07-26
You could also buy a 2nd USB stick, or a blank CD--the low cost and easy availability of both methods are probably the reason why the Fedora team isn't wasting their time writing a GUI liveusb-creator for Ubuntu.

---

### Post by beew on 2010-07-26
I am in the process of learning and experimenting so the goal is not just to get a Fedora live usb, but to see how I can create it in a Linux environment (in a nwebie friendly way because I am sure there are ways to do it with commands but all the tutorial I read seems complicated. :)) . If I just want the end product I can easily create it using the windows tool (with persistence) or Unetbootin (without persistence) . A live USB without persistence is like a live CD except much better in terms of speed and storage. So, no, I won't pay for a live CD. (Though it seems that with Open_Suse you need to actually burn the live CD, boot into it in order to create a live USB, but I am not using that right now) :)

---

### Post by snowpine on 2010-07-26
1. Use Unetbootin or dd to create a non-persistent Fedora on Thumb Drive #1
2. Boot Fedora using Drive #1
3. Create a persistent live USB on Thumb Drive #2. 

But that is cool you are trying to learn; trying something unconventional is how progress happens! :)

ps "dd" works with OpenSUSE too.

---

### Post by C.S.Cameron on 2010-07-26
> If I want to create a Ubuntu live USB with persistence using Ubuntu there is really no need to use unetbootin and then go through the trouble of editing configuration files. Use the built in start up disk creator in system > administration

Yes that method is much easier but persistence is limited to 4GB.

I have also been trying to figure out how to add persistence to a Fedora grub2 install, (made using MultiBootUSB).
No luck so far, even cheating a bit using an overlay file created using Fedora's Windows USB LiveUSB creator.

---

### Post by beew on 2010-07-26
Apparently the Fedora liveusb creator works in other Linux distros as well but you have to compile it yourself [ https://fedorahosted.org/liveusb-creator/]("https://fedorahosted.org/liveusb-creator/") (Thanks also to snowpine for the links earlier, one of which is the tarred package for the usb creator.

I tried to install it but failed.

I untarred the package in usr/local/src, , there is no "how to"  information in the readme file. I then cd into the untarred directory  (folder), type ./confugre. It says there is no file with that name, I  then typed "make" and it seemed ok, I then  typed sudo checkinstall, it printed out something which looked like  the name of the packages to be installed, asked for a description as there  is no documentation in the directory, it then printed out the error  message  **[B]"No rule to make target "install". Stop"**[/B] and said "bye".

I probably did something stupid. Please help.

---

### Post by beew on 2010-07-26
> **C.S.Cameron said:**
> Yes that method is much easier but persistence is limited to 4GB.


 Actually all my usb drives are either 2 or 4 gs so I wouldn't worry about the 4g limitation. :)  I did manage to do a full installation (not a live usb with persistence) on my one and only 8 g Kingston thumb drive though. It has some advantages over a live usb with persistence because you can do full system updates, install graphic drivers etc. But it is kind of slow comparing to the live usb because it is not running out of ram anymore. 

I think Fedora limits the persistence overlay to 2 g no matter how big your usb drive is because it uses a method whereby a memory cell cannot be reused even if you have deleted its content as a way to protect the usb medium--I could be wrong though.

---

### Post by wojox on 2010-07-26
Try this

```
su -c 'yum install liveusb-creator'
```


you shouldn't have to compile it.

---

### Post by beew on 2010-07-26
> **wojox said:**
> Try this

```
su -c 'yum install liveusb-creator'
```
you shouldn't have to compile it.

Hi,

This didn't work. "yum" is a Fedora command, no? Also in Ubuntu you can't become root by typing su- as you wouldn't know the root password. I tried sudo -c but was told the command doesn't exist. It didn't work with just sudo either.

Oh, I have cd into the folder where the package was untarred into when I ran these commands.

---

### Post by beew on 2010-07-27
Ok, it seems that I am getting a bit closer after reading this thread. 
[URL="http://ubuntuforums.org/showthread.php?t=1415394"]
http://ubuntuforums.org/showthread.php?t=1415394[/URL]

I followed the instruction cd-ing into the directory which is the untarred package and run sudo ./liveusb-creator, but then I got an Import Error. Here is part of the output


> File "./liveusb-creator", line 89, in <module>
    main()
  File "./liveusb-creator", line 82, in main
    from liveusb.gui import LiveUSBApp
  File "/home/beta/liveusb-creator-3.9.2/liveusb/__init__.py", line 45, in <module>
    from liveusb.linux_dialog import Ui_Dialog as LiveUSBInterface
  File "/home/beta/liveusb-creator-3.9.2/liveusb/linux_dialog.py", line 10, in <module>
    from PyQt4 import QtCore, QtGui
ImportError: No module named PyQt4




---

### Post by beew on 2010-07-27
OK, installed PyQt4 from repo and run sudo ./liveusb-creator again and got a runtime error:

> File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 382, in add_signal_receiver
    self._require_main_loop()
RuntimeError: To make asynchronous calls, receive signals or export objects, D-Bus connections must be attached to a main loop by passing mainloop=... to the constructor or calling dbus.set_default_main_loop(...)

What does this mean???

---

### Post by wojox on 2010-07-27
You have Fedora installed correct?

You need to follow my instructions while running Fedora.

---

### Post by beew on 2010-07-27
No, I have Ubuntu 10.04 installed. I want to create a Fedora live usb with persistence in a ubuntu environment. Thanks.

---

### Post by snowpine on 2010-07-27
Burn a Fedora Live CD (or Live USB). Then, you will be running a Fedora environment, and Wojox's instructions should work fine.

---

### Post by beew on 2010-07-27
I know. But it bothers me that the liveusb-creator doesn't seem to work in Ubuntu while it should! Why all the goodies only for Windows users??

I actually do have a Fedora13 live usb which I made using the liveusb-creator in windows so I can boot into it and create another one in the Fedora environment as you said. (or I could have made the first one using Unetbootin cause I don't need persistence in the first one)

Btw, Wojox may know the answer to this. It seems that the Fedora live usb is incredibly slow. Even slower than running a full Ubuntu installation (not a live usb with a persistence overlay, but a full installation) in my 8G usb thumb drive. The Ubuntu live usb is lightning fast though as it runs out of the RAM, is it different with Fedora?

---

### Post by beew on 2010-07-27
Let me clarify. My purpose is not to just make a Fedora live usb with persistence because I already have one and can make more if I want to. I want to explore to see if there are simple, newbie friendly ways to do that in a purely Ubuntu environment  using tools available in Ubuntu ( I know I can always do it with dd and tons of command lines like I found in some tutorials but it doesn't seem to be very newbie friendly) I think this is a Linux job and I should be able to do it in Linux, it doesn't make sense if the most clean and painless way would be to do it in Windows or do it in a round about way by using two USBs  just to get into the Fedora environment.

The Fedora liveusb-creator is supposed to work in all Linux distros according to their wiki, this would be the right way to do it. Unfortunately I keep running into errors when trying to do that and their wiki contains absolutely no instruction, strangely there are instructions for windows users though while they don't really need the instructions because once you download the exe file everything is intuitively obvious!

---

### Post by beew on 2010-07-28
Hahahaha!!!! It finally works thanks to this link [http://coffeecode.net/archives/223-Using-Fedoras-liveusb-creator-on-Ubuntu-Lucid-Lynx.html](http://coffeecode.net/archives/223-Using-Fedoras-liveusb-creator-on-Ubuntu-Lucid-Lynx.html)

Here is the procedure. Download the Fedora iso from their site, download the liveusb-creator [https://fedorahosted.org/releases/l/i/liveusb-creator/liveusb-creator-3.9.2.tar.bz2](https://fedorahosted.org/releases/l/i/liveusb-creator/liveusb-creator-3.9.2.tar.bz2)

Download and install the packages PyQt4, Qt4-dbus and python-parted from Sypnatic, untar the tar.bz2 file into somewhere, say your home directory. Then edit the file " liveusb/gui.py" as instructed in my first link.

Now plug in a blank USB drive in FAT32 format, cd into the directory created from extracting the tar.bz2 file, say, /home/liveusb-creator-3.9.2. Then type in the terminal
>  sudo ./liveusb-creator After providing your password a nice GUI will appear and from then on everything is easy. You need to choose the iso source, the name of the target usb (something like dev/sdb1, but be careful, or you will wipe out your hard drive!) and you can choose the size of the persistence overlay. Then click create and wait. 

This is actually very easy if they would give you some instructions instead of just dump a tar ball at you and assuming that you know what do with it. Evidently I don't know and neither do the good people who are trying to help. Is it so difficult to write a few lines of explanations? The thing I find most frustrating and user unfriendly about Linux is not the command lines and the tweaking that are required sometimes, but the unwillingness or inability of developers to provide understandable documentations. How often do you down load a utility which is supposed to do something you want but there is absolutely no explanation  of how to use it? You shouldn't have to scourge the internet to look for a straight forward "how to" if the help file really does it job!  But the most incomprehensible thing is these same people would go through great length to explain what is completely obvious to windows users. There are tons of tutorial for windows users to use the Fedora liveusb creator on the web even though it is completely obvious once you download the exe file. The liveusb wiki page has instructions for windows users, but for Linux users who have other distros than Fedora they just dump a buggy tar ball at you and that's it. Hello?? Is there something wrong with that picture? No wonder they say Windows is more user friendly!

End of rant.

---

### Post by beew on 2010-07-28
Follow up. It turns out that you can install the liveusb-creator instead of just running it from the directory.

Type in the terminal

> sudo python setup.py install

The liveusb-creator would be installed and a launcher will be created under Applications > System tools.

In order to be able to launch it by clicking the icon you have to edit the launcher. Go to System > Preference > Main Menu, find the entry for the liveusb creator, click properties and then edit. Replace the command with gksudo full path of the live usb creator. For example "gksudo /home/username/liveusb-creator-3.9.2/liveusb-creator" without quotations.

---

### Post by tophatandy on 2010-07-28
Congrats on getting it to work and thank you for sharing how you did it!

---

### Post by dmgExP on 2010-07-30
Easy way to create a multi-boot usb pendrive on linux.  It can handle most (if not all) linux iso images and even a complete linux installation or three using GRUB:

Instructions:

**Download:**
Grub4dos:  _[download grub4dos]("http://download.gna.org/grub4dos/grub4dos-0.4.4.zip")_
Puppy Linux: Not essential, but always useful to have on a flashdrive:  _[Download latest Puppy]("ftp://ibiblio.org/pub/linux/distributions/puppylinux/")_
GParted Live:  Another useful tool. _[Download latest Gparted ZIP file]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/")_

Download any other linux iso's

**Step 1:**
use gparted or the Ubuntu disk utility to format flashdrive to fat32

**Step 2:**
***Do not mount flashdrive!***
Open a terminal and type command:
[FONT="Verdana"][SIZE="2"]*sudo syslinux /dev/sdb999*[/SIZE][/FONT] [SIZE="1"](use device id of your flashdrive)[/SIZE]

**Step 3:**
Mount flashdrive.
Extract **[FONT="Arial"]grub.exe[/FONT]** from grub4dos-0.4.4.zip, copy g**[FONT="Arial"]rub.exe[/FONT]** to flashdrive.
Copy all linux.iso images to flashdrive.
To add Puppy Linux you will need to copy **[FONT="Arial"]initrd.gz, lupu500.sfs[/FONT]** and **[FONT="Arial"]vmlinuz[/FONT]** from the the Puppy iso to the flashdrive.  (it is not necessary to copy the complete Puppy iso).
To add GParted Live you will need to copy the folder **/live/** from the downloaded zip file or iso image to /GPARTED/ on the flashdrive.

**Step 4:**
create file [FONT="Arial"]**syslinux.cfg**[/FONT] on flashdrive with just this one line of text:
[FONT="Courier New"][INDENT]**default grub.exe**[/INDENT][/FONT]
create file [FONT="Arial"]**menu.lst**[/FONT] on flashdrive with one entry for each iso image as in this example:[INDENT][FONT="Courier New"][B]timeout 15
color black/cyan yellow/cyan
default 0

title Puppy Linux
find --set-root /vmlinuz
kernel /vmlinuz BOOT_IMAGE=linux acpi=on 
initrd /initrd.gz

title Ubuntu (All versions)
find --set-root /ubuntu-10.04.iso
map /ubuntu-10.04.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent [/FONT][/B] [SIZE="1"](the kernel line ends here)[/SIZE]
[FONT="Courier New"][B]initrd /casper/initrd.lz

title Acronis TrueImage 2011
find --set-root /Acronis-2011.iso
map /Acronis-2011.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title GParted Live
find --set-root /GPARTED/vmlinuz
fakebios
kernel /GPARTED/vmlinuz live-media-path=/GPARTED boot=live config  noswap noprompt  toram=filesystem.squashfs ip=frommedia  nosplash [SIZE="1"](the kernel line ends here)[/SIZE]
initrd /GPARTED/initrd.img

title Memtest86+
find --set-root /memtest86+.bin
kernel /memtest86+.bin
[/INDENT][/B][/FONT]More entries can be found at pendrivelinux.com

You can now boot the drive!

_NB it is important that iso images on the pendrive are not fragmented.  You may need to reformat the drive after deleting images before you can add new ones._

---

### Post by snowpine on 2010-07-30
Glad you got it working beew and thanks for the tutorial! :)

---

### Post by beew on 2010-07-30
One small wrinkle that I have since worked out.

Say you format your usb drives with gparted. For some reasons persistence wouldn't work if you allow gparted to assign a label to the USB which contains numbers and/or "-"  (for Fedora 13, but it seemed that it works for 12, I can't remember clearly if it did. :)) It all worked if you manually assign a simple label with just alphabets, say, "volume". Probably it can't be too long either.

As someone has pointed out before all these automated programs are just graphic front ends to some variations of the dd command (but it is fun to work with gui and I like beautiful graphic designs, I am not like many Linux purists :)) A way for newbie such as myself to peek under the hood and see how the command lines work would be to do the following.

Instead of invoking the liveusb-creator by clicking the icon, open a terminal, cd into the directory where the live usb creator is created and type 
> 
sudo ./liveusb-creator --verbose It will bring out the Gui and when you run it you will see the command lines in the terminal.

---

### Post by vodanh016 on 2010-07-30
thanks pro but it so hard to practice!

---

### Post by tariqsheikh on 2011-07-05
> **beew said:**
> The liveusb wiki page has instructions for windows users, but for Linux users who have other distros than Fedora they just dump a buggy tar ball at you and that's it. Hello?? Is there something wrong with that picture? No wonder they say Windows is more user friendly!

End of rant.

Exactly! Couldn't agree more with you. Thanks for the tutorial!

---

