---
title: "Intel536ep Modem, Working, Wiki, Whoops - Newbie Win"
date: 2005-05-27
forum: Networking &amp; Wireless
---

### Post by Zerksis on 2005-05-27
This post describes a "Windows User" view of installing an Intel analog modem in Ubuntu! - that eventually worked.  Details of the install are given below.

It is assumed that you have to download and check the required files in Windows.  Many readers will probably have to - if Ubuntu worked your modem then you would not be here reading this!
   
Having my install fail twice, and not finding a solution in the forums, forced some reading and more examination of error messages.

Helpful material can be found in;-

a) "*Compiling drivers for newbies*"  at  
[http://linmodems.technion.ac.il/compiling.html](http://linmodems.technion.ac.il/compiling.html)

b) the *readme.txt* found in the "*intel-536ep-4.69.1.tgz*" file.

If your existing Windows setup is unable to manipulate the .tgz" file, then visit  [www.7-zip.org](www.7-zip.org)  and get 7zip. 
Run 7zFM, which will enable you to test, or extract from, .tgz files within Windows.
  
Both a) & b), above, refer to sub folders of; 
*/lib/modules/(kernel-version)/*

It became clear, {from a), b) and the error messages}, that a **clean install** of Ubuntu does *not* create a necessary "misc" folder which is required for both the Intel 536 and 537 modems.  Information on adding this folder is given later. *(Section 3)*     

It will be assumed that you have a copy of the Ubuntu - Wikipage;-

"[color=Sienna]IntelFiveThreeSixEPModemHowto[/color]" available. 

Get it at;-

 "[http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto](http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto)"

The first goal, is to be able to run the Wiki pg5. command
"*modprobe Intel536*" without it ending in "[color=Red]FATAL:...[/color]" 

The 536 Modem "Howto" consists of 4 sections;-

***[size=+1]1.)  Install required Ubuntu packages[/size]***

This worked every time.

Just pop the Ubuntu 5.04 disk into the CD and follow the "Howto" instructions.

The terminal [color=Green]**input (i/p)**[/color] and output (o/p) looks like;-

```

mdm3@zerk1:~$ [color=Green]**sudo apt-get install build-essential linux-headers-386**[/color]
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  g++ g++-3.3 gcc gcc-3.3 libstdc++5-3.3-dev linux-headers-2.6.10-5 linux-headers-2.6.10-5-386
Suggested packages:
  gcc-3.3-doc manpages-dev autoconf automake libtool flex bison gcc-doc libstdc++5-3.3-doc
  stl-manual
The following NEW packages will be installed:
  build-essential g++ g++-3.3 gcc gcc-3.3 libstdc++5-3.3-dev linux-headers-2.6.10-5
  linux-headers-2.6.10-5-386 linux-headers-386
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9581kB of archives.
After unpacking 79.1MB of additional disk space will be used.
Do you want to continue [Y/n]? [color=Green]**Y**[/color]
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter


Preconfiguring packages ...
Selecting previously deselected package gcc-3.3.
(Reading database ... 58010 files and directories currently installed.)
Unpacking gcc-3.3 (from .../gcc-3.3_3.3.5-8ubuntu2_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_3.3.5-1_i386.deb) ...
Selecting previously deselected package libstdc++5-3.3-dev.
Unpacking libstdc++5-3.3-dev (from .../libstdc++5-3.3-dev_3.3.5-8ubuntu2_i386.deb) ...
Selecting previously deselected package g++-3.3.
Unpacking g++-3.3 (from .../g++-3.3_3.3.5-8ubuntu2_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_3.3.5-1_i386.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_10.1ubuntu1_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.10-5.
Unpacking linux-headers-2.6.10-5 (from .../linux-headers-2.6.10-5_2.6.10-34_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.10-5-386.
Unpacking linux-headers-2.6.10-5-386 (from .../linux-headers-2.6.10-5-386_2.6.10-34_i386.deb) ...
Selecting previously deselected package linux-headers-386.
Unpacking linux-headers-386 (from .../linux-headers-386_2.6.10-7_i386.deb) ...
Setting up gcc-3.3 (3.3.5-8ubuntu2) ...
Setting up gcc (3.3.5-1) ...

Setting up linux-headers-2.6.10-5 (2.6.10-34) ...

Setting up linux-headers-2.6.10-5-386 (2.6.10-34) ...
Setting up linux-headers-386 (2.6.10-7) ...
Setting up libstdc++5-3.3-dev (3.3.5-8ubuntu2) ...
Setting up g++-3.3 (3.3.5-8ubuntu2) ...
Setting up g++ (3.3.5-1) ...

Setting up build-essential (10.1ubuntu1) ...

```
Remove CD & Reboot, (restart the computer) I did.

***[size=+1]2.) Download required files.[/size]***

... but saving Win -> Linux can have problems. 

Downloading driver and patch files whilst in Windows - and then trying to place them in the "Howto" recommended Linux folder/s means that you might encounter Linux "permissions and owners".

It is probably easier to cuddle the scrap yard Rottweiler than get a Windows file to reside in some Linux folders!  

The Wiki "patch page" text reads, "*Make sure you know where you've saved this file; for the purposes of this document it will be assumed that it is in your home directory.*"
As a Windows user you will look for a "home" directory, possibly using the File Browser - 
[color=Sienna]*[Menu] Applications -> System Tools -> File Browser*[/color]
and you will find it!  
Don't bother trying to save the file in 'home' - you will just get the msg. 
"[color=Red]Error while copying to '/home'[/color]"  
You have to know that in Linux your *'home'* directory is actually 
[color=Sienna]***/home/<username>***[/color] where <username> is your username you logged on with.  NOT your actual *'home'* directory. 

Stupid bl**dy Windows user, you should know this! - *uh! er. well, well Win has it's share of silly naming conventions too.*

If you do manage to save the files to '/home' then you should be aware that if you try to apply the patch with;-

[font=Courier New]patch -l -p1 < ~/intel536.diff[/font]

this command won't work.  Because the ~ is a Filename Metacharacter and if used with no name (rather than ~name) means home directory of current user.
Which results in the Error Msg. "[color=Red]No such file or directory[/color]" 

So the file is not where Linux is looking for it! get it ?
Check it out later, with terminal commands  dir ~/ then dir /

[i]Ah! back to 'home' directory is actually /home/<username>  
Well, we Windows users knew all that - - ... did'nt we ?[/i]

To be fair to the Wiki page author it does state,
home = /home/<username> in the "Download driver source" section.

However, a new user is likely to interpret instructions *exactly* as written, or if one downloads and continues at some other time or is interrupted then the last item read will be the section, 
"To save the patch,..."

I used the following steps;-

**2a)** While in Windows, download modem driver "*intel-536ep-4.69.1.tgz*" by following the Wikipage link.

**2b)** While in Windows, download driver "*patch*" by following the Wiki instructions and save as;

"*intel536.diff*"

When creating the .diff file do not use Word, instead use Notepad and "Save as type: *All Files*", with the complete name (including the 4 letter "*diff*" extension) typed in the "*File Name:*" box.

Also, ensure that the last line of the .diff file is a blank, if the last "}" does not have a CR after it - then the o/p of the patch command will contain the error message;- 

"[color=Red]patch unexpectedly ends in middle of line[/color]".

Eliminating any error msgs. is helpful when things go wrong.

**2c)** Save (still in Windows) both the files,
"*intel-536ep-4.69.1.tgz*" and "*intel536.diff*"
to a floppy disk or any form of USB storage.  Both files total less than 500kB so they easily fit on one floppy.

**2d)** Start Ubuntu 5.04, open 2 File Browser windows;-
[color=Sienna]*[Menu] Applications -> System Tools -> File Browser*[/color]
Both windows will open in */home/<username>* 
In one window click on the "Computer" icon, select your storage device (USBn: <name> or Floppy disk) and browse to the 
"*intel-536ep-4.69.1.tgz*" and "*intel536.diff*" files.

Just "drag" each file into the other window  */home/<username>*

**Note:** the file icons should not be coloured red or display a lock symbol.  Permissions on both should be 755 -rwxr-xr-x and the file Owner should be <username>.  Right click a file, select "Properties and click on the "Permissions" tab to view.
 
Do not use root or sudo to copy the files as this changes the owners or permissions and may result in problems later in the install process.

Both files are now in the Wiki preferred location.    


***[size=+1]3.) Compiling the driver.[/size]*** 

At this point, before running any Intel files, create the missing "misc" directory. Open a Terminal;
[color=Sienna]*[Menu] Applications -> System Tools -> Terminal*[/color]

Change directory to */lib/modules/(kernel-version)/* and create the "*misc*" directory.  
Can be done with the following [color=Green]i/p[/color];- 

```

mdm3@zerk1:~$ [color=Green]**cd /lib/modules/$(uname -r)/**[/color]
mdm3@zerk1:/lib/modules/2.6.10-5-386$ [color=Green]**sudo mkdir -v misc**[/color]
Password:
mkdir: created directory `misc'

```
So, now you know that your kernel version is  2.6.10-5-386 or whatever is displayed - in case anyone should ask.

*misc* Note: Owner and Group = root. Permissions 755 drwxr-xr-x

**3a)** Uncompress the download file. "*intel-536ep-4.69.1.tgz*"

Still in the Terminal change to the */home/<username>* directory with *cd ~/*  and then type;  *tar xzvf intel-536ep-4.69.1.tgz* 

Note the addition of a 'v' in the 4 letter group after 'tar' 
This v initiates a verbose mode (somewhat like this post! :-) ) that gives extra information, in this case - file names as they are extracted. 

This worked OK every time. Terminal [color=Green]i/p[/color]-o/p will look like;-

```

mdm3@zerk1:/lib/modules/2.6.10-5-386$ [color=Green]**cd ~/**[/color]
mdm3@zerk1:~$ [color=Green]**tar xzvf intel-536ep-4.69.1.tgz**[/color]
intel-536EP-2.56.76.1/
intel-536EP-2.56.76.1/config_check
intel-536EP-2.56.76.1/coredrv/
intel-536EP-2.56.76.1/coredrv/536core.lib
intel-536EP-2.56.76.1/coredrv/clmmain.c
intel-536EP-2.56.76.1/coredrv/coredrv.c
intel-536EP-2.56.76.1/coredrv/hamcore.h
intel-536EP-2.56.76.1/coredrv/hamdefs.h
intel-536EP-2.56.76.1/coredrv/locks.c
intel-536EP-2.56.76.1/coredrv/lock_lin.h
intel-536EP-2.56.76.1/coredrv/Makefile
intel-536EP-2.56.76.1/coredrv/rts.c
intel-536EP-2.56.76.1/coredrv/rts.h
intel-536EP-2.56.76.1/coredrv/softcore.h
intel-536EP-2.56.76.1/coredrv/softserial.c
intel-536EP-2.56.76.1/coredrv/softserial.h
intel-536EP-2.56.76.1/coredrv/softserial_io.c
intel-536EP-2.56.76.1/coredrv/softserial_ioctl.c
intel-536EP-2.56.76.1/coredrv/sys_ver.h
intel-536EP-2.56.76.1/coredrv/task.c
intel-536EP-2.56.76.1/coredrv/tasker.h
intel-536EP-2.56.76.1/coredrv/uart.c
intel-536EP-2.56.76.1/coredrv/uart.h
intel-536EP-2.56.76.1/coredrv/wwh_dflt.c
intel-536EP-2.56.76.1/coredrv/wwh_dflt.h
intel-536EP-2.56.76.1/hamregistry
intel-536EP-2.56.76.1/Intel536_boot
intel-536EP-2.56.76.1/Intel536_inst
intel-536EP-2.56.76.1/license.txt
intel-536EP-2.56.76.1/makefile
intel-536EP-2.56.76.1/readme.txt
mdm3@zerk1:~$

```
Reboot

**3b)** Change to the intel directory
[color=Sienna]*[Menu] Applications -> System Tools -> Terminal*[/color]

```

mdm3@zerk1:~$ [color=Green]**cd ~/intel-536EP-2.56.76.1**[/color]
mdm3@zerk1:~/intel-536EP-2.56.76.1$ 

```
**3c)** Apply the '*intel536.diff*' patch

Sure that the lastline is a blank ?  [see 2b)]

Follow the Wiki and type  patch -l -p1 < ~/intel536.diff
Note that the character after the first "-" is a lower case L and the character after the “p” is a One.

Terminal [color=Green]i/p[/color]-o/p looks like;-

```

mdm3@zerk1:~/intel-536EP-2.56.76.1$ [color=Green]**patch -l -p1 < ~/intel536.diff**[/color]
(Stripping trailing CRs from patch.)
patching file coredrv/softserial.h
(Stripping trailing CRs from patch.)
patching file coredrv/softserial_io.c
mdm3@zerk1:~/intel-536EP-2.56.76.1$

```
**3d)** Run compile commands.  *make clean* and *make 536*

```

mdm3@zerk1:~/intel-536EP-2.56.76.1$ [color=Green]**make clean**[/color]
cd coredrv; make clean
make[1]: Entering directory `/home/mdm3/intel-536EP-2.56.76.1/coredrv'
rm -f *.ko *.o *~ core
make[1]: Leaving directory `/home/mdm3/intel-536EP-2.56.76.1/coredrv'
rm -f *.o *.ko
mdm3@zerk1:~/intel-536EP-2.56.76.1$

```

```

mdm3@zerk1:~/intel-536EP-2.56.76.1$ [color=Green]**make 536**[/color]
   Module precompile check
   Current running kernel is: 2.6.10-5-386
   /lib/modules...   autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No such file or directory
   autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No such file or directory
   version.h matches running kernel
uname -r|grep "2.6" && \
cd coredrv && make 536core_26 && \
cp Intel536.ko .. && cd .. && \
strip --strip-debug Intel536.ko && \
exit; \
ls Intel536.ko >/dev/null 2>&1 ||  uname -r | grep "2.6" && echo "Failed to build driver" && exit; \
if [  ]; then \
cd coredrv; make TARGET=TARGET_SELAH KERNEL_SOURCE_PATH= "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
else \
cd coredrv; make TARGET=TARGET_SELAH KERNEL_INCLUDES=/lib/modules/`uname -r`/build/include \
       "PSTN_DEF=-DTARGET_SELAH -DTARGET_LINUX -DLINUX" 536core; \
        fi ; \
cp Intel536.o .. ; \
if [ -a /boot/vmlinuz.version.h ]; then \
        cp /boot/vmlinuz.version.h /lib/modules/`uname -r`/build/include/linux/version.h;\
        fi
2.6.10-5-386
make[1]: Entering directory `/home/mdm3/intel-536EP-2.56.76.1/coredrv'
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/mdm3/intel-536EP-2.56.76.1/coredrv modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/coredrv.o
/home/mdm3/intel-536EP-2.56.76.1/coredrv/coredrv.c:754: warning: initialization from incompatible pointer type
/home/mdm3/intel-536EP-2.56.76.1/coredrv/coredrv.c:755: warning: initialization from incompatible pointer type
/home/mdm3/intel-536EP-2.56.76.1/coredrv/coredrv.c: In function `dspdrv_CommRamISR':
/home/mdm3/intel-536EP-2.56.76.1/coredrv/coredrv.c:877: warning: function declaration isn't a prototype
include/linux/module.h: At top level:
/home/mdm3/intel-536EP-2.56.76.1/coredrv/coredrv.c:286: warning: `power_callback' defined but not used
  CC [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/clmmain.o
  CC [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/rts.o
  CC [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/task.o
  CC [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/uart.o
  CC [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/wwh_dflt.o
  CC [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/locks.o
  CC [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/softserial_io.o
  CC [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/softserial_ioctl.o
  CC [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/softserial.o
  LD [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/Intel536.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/mdm3/intel-536EP-2.56.76.1/coredrv/.536core.lib.cmd for /home/mdm3/intel-536EP-2.56.76.1/coredrv/536core.lib
  CC      /home/mdm3/intel-536EP-2.56.76.1/coredrv/Intel536.mod.o
  LD [M]  /home/mdm3/intel-536EP-2.56.76.1/coredrv/Intel536.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: Leaving directory `/home/mdm3/intel-536EP-2.56.76.1/coredrv'
mdm3@zerk1:~/intel-536EP-2.56.76.1$ 

```
**3e)** Follow the Wiki instructions to check for the Intel536.ko driver file.
```

mdm3@zerk1:~/intel-536EP-2.56.76.1$ [color=Green]**ls -l Intel536.ko**[/color]
-rw-r--r--  1 mdm3 mdm3 1090804 2005-05-25 16:04 Intel536.ko
mdm3@zerk1:~/intel-536EP-2.56.76.1$

```
If the line -rw-r... is there, then so far so good!

Now copy the Intel536.ko file to the created "misc" directory.

```

mdm3@zerk1:~/intel-536EP-2.56.76.1$ [color=Green]**sudo cp -v Intel536.ko /lib/modules/$(uname -r)/misc**[/color]
Password:
`Intel536.ko' -> `/lib/modules/2.6.10-5-386/misc/Intel536.ko'

```
***[size=+1]4.) Install driver[/size]*** 

Make the system aware of the Intel module.

```

mdm3@zerk1:~/intel-536EP-2.56.76.1$ [color=Green]**sudo depmod -a**[/color]

```
Now load the driver

```

mdm3@zerk1:~/intel-536EP-2.56.76.1$ [color=Green]**sudo modprobe Intel536**[/color]
mdm3@zerk1:~/intel-536EP-2.56.76.1$

```
if just a system prompt (as above) and no "[color=Red]FATAL:...[/color]" msg. you are doing well!

Reboot.

**4a)** Load driver at boot-up.

Open terminal and backup file;-
[color=Sienna]*[Menu] Applications -> System Tools -> Terminal*[/color]

```

mdm3@zerk1:~$ [color=Green]**sudo cp -v /etc/modules /etc/modules.backup**[/color]
Password:
`/etc/modules' -> `/etc/modules.backup'
mdm3@zerk1:~$

```
Modify the “modules” file  

```

mdm3@zerk1:~$ [color=Green]**sudo echo Intel536 >> /etc/modules**[/color]
bash: /etc/modules: Permission denied
mdm3@zerk1:~$ [color=Green]**exit**[/color]

```
Whoops – maybe it's that nasty Rottweiler guard dog again!

Exit the Terminal and open a Root Terminal
[color=Sienna]*[Menu] Applications -> System Tools -> Root Terminal*[/color]

Enter your user password.
Type the command again but without "sudo"

```

root@zerk1:/home/mdm3 # [color=Green]**echo Intel536 >> /etc/modules**[/color]
root@zerk1:/home/mdm3 # [color=Green]**exit**[/color]

```
This adds the text "*Intel536*" to the file "modules", make sure you typed this correctly.

Exit the root terminal.

The Wiki does say check the /etc/modules file *before* you reboot.
If you want to; open a terminal;-
[color=Sienna]*[Menu] Applications -> System Tools -> Terminal*[/color]

Type in:  [font=Courier New][color=Green]**sudo gedit /etc/modules**[/color][/font]

when the file is displayed, check that the last line is 
*Intel536* 
if not correct it; and save it!

Reboot


***[size=+1]5) Testing Time![/size]***

Being a Windows user I used the Ubuntu *Modem Monitor*

1.) Right click on the top toolbar, (or the bottom toolbar if you prefer the modem icon *à la* Windows) & left click "*+ Add toPanel...*"

2.) Scroll down to a red telephone icon, double click it.
The icon will now appear on the top toolbar.  

3.) Right click on the toolbar/panel icon, & left click "Properties" in the drop down menu.  Enter your user password.

4.) Check the "This device is configured" box, - now fill in
*Phone number* (ISP dial-in No.)
*Dial prefix* can be left blank
Your ISP dial-in *Username*
Your ISP dial-in *Password*

5.) On the *Modem* tab, in *Modem port:* type [color=Green]**/dev/536ep0**[/color]  
(don't even think about Autodetect!) and that last character above is a zero.
Under "*Volume*" select Medium, from the drop down menu, if you want to listen to the modem dialing out.

6.) Under the *Options* tab make sure that the "*Set modem as default route to internet*" is ticked.

Click on OK

Check that the modem phone line is connected  - right click on the telephone icon, click *Activate*, enter PW,  

If you hear it dial, wait at least 30sec, then click on the Firefox icon in the top tool bar and browse.  Most ISP's will work with the default settings.

*WHAT!* you want flashing modem activity lights & an indication of download bytes too!

*OK* - do 1.) and 2.) above but double click on the "Network Monitor" *instead* of the Modem Monitor.

When connected to your ISP, right click the Network Monitor icon in the toolbar and click "*Properties*".
 In the “*General*” tab use the scroll bar in the *Connection, Name:* section to select *ppp0*, this will link the modem connection to the *Network Monitor*. You can also see a received/sent packet count.

During modem *send/receive* activity the Network Monitor will now flash.

Clicking the *Support* tab shows Internet Address information.

When you *Deactivate* the modem the Network Monitor icon will display a red disc with a white bar, indicating that you cannot access the ppp0 controlled network.

*And!*
You want to know, how to display the modem connection speed?  

*dunnow!*

Z

---

### Post by David Kaisemann on 2005-05-27
This is a helpful. Additional reading after Ubuntu Starter Guide.

---

### Post by Zerksis on 2005-06-08
[COLOR=DarkOrange]***Addendum:***[/COLOR]

Note: The official Ubuntu Wiki "How To" at;- 

[http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto](http://www.ubuntulinux.org/wiki/IntelFiveThreeSixEPModemHowto)

has now been modified from *misc* to *kernel/drivers/char* see last page of latest "How To".  

This means that following the Wiki should now work fine, without having to add extra code to create the *misc* directory.  

However, I notice that the PCTel HSP modems also load a file *ptserial* to */lib/modules/$(uname -r)/misc* - so several devices seem to expect a *misc* folder.

Z

---

### Post by voidlogic on 2005-06-11
thanks for the info guys :) I'm having a bit of my own modem issue- any ideas?

[http://www.ubuntuforums.org/showthread.php?p=202288#post202288](http://www.ubuntuforums.org/showthread.php?p=202288#post202288)

 ](*,)  ](*,)  ](*,)

---

### Post by Zerksis on 2005-06-12
I had a similar problem with a serial modem.

I used the fix described in Bug 8890 at bugzilla.

Open the file /etc/ppp/peers/ppp0 with

[FONT=Courier New][COLOR=DarkGreen]$ sudo gedit /etc/ppp/peers/ppp0[/COLOR][/FONT]

and add the following line at the end 

[FONT=Courier New][COLOR=DarkGreen]115200[/COLOR][/FONT]

just the number - nothing else.

This will set the speed of the serial interface.

Hope this works for you too

Z

---

### Post by tariqf on 2005-09-07
Hi I have followed the wiki for the 536ep and am trying to use vgetty but it does not appear to work. I have the Intel536 module loaded ok as its listed with lsmod. I have aslo edited /etv/mgetty/voice.conf and mgetty.conf to use 536ep0 as the modem device. Please please can anyone help? I've spent the best part of today trying to get this to work with this to work. My vgetty log is:

09/07 18:26:01 dem  vgetty: experimental test release 0.9.32 / 24Dec01
09/07 18:26:01 dem  mgetty: experimental test release 1.1.31-Jul24
09/07 18:26:01 dem  WARNING: parent process not init(pid=1), but pid=5748 (bash)
09/07 18:26:01 dem  reading generic configuration from config file /etc/mgetty/voice.conf
09/07 18:26:01 dem  reading program vgetty configuration from config file /etc/mgetty/voice.conf
09/07 18:26:01 dem  reading port modem configuration from config file /etc/mgetty/voice.conf
09/07 18:26:01 dem  check for lockfiles
09/07 18:26:01 dem  locking the line
09/07 18:26:01 dem  tio_get_rs232_lines: TIOCMGET failed: Invalid argument
09/07 18:26:01 dem  WARNING: DSR is off - modem turned off or bad cable?
09/07 18:26:01 dem  lowering DTR to reset Modem
09/07 18:26:01 dem  TIOCMBIC failed: Invalid argument
09/07 18:26:01 dem  WARNING: obsolete setserial spd_hi/spd_vhi used, 38400 is not real port speed
09/07 18:26:02 dem  send: \d
09/07 18:26:03 dem  do_chat: can't write to modem!: Bad address
09/07 18:26:03 dem  waiting for ``OK''
09/07 18:26:23 dem  timeout in chat script, waiting for `OK'
09/07 18:26:23 dem  init chat timed out, trying force-init-chat
09/07 18:26:23 dem  send: \d
09/07 18:26:23 dem  do_chat: can't write to modem!: Bad address
09/07 18:26:23 dem  waiting for ``OK''
09/07 18:26:24 ##### failed dev=modem, pid=6392, got signal 2, exiting

---

### Post by ntu on 2005-10-11
Hi Zerksis,

I want to thank you very much for your very informative first post on this thread.

I am new to Linux and was looking round for a distro that would give me good info on how to get online with my 536ep internal modem (or even any internal modem). I found the Wiki Howto and your (Whoops) post. Your post was the clincher.

I am new to Linux and have just got online with Ubuntu! First time online with Linux in my own machine. No email as yet - still have to sort that out.

I particularly like the way you give 'printout' of what to expect after commands have been entered, so that readers can check whether they 'are on the right track'

Once again, many thanks, and best wishes,

---

