---
title: "gnome boot from terminal"
date: 2010-11-07
forum: New to Ubuntu
---

### Post by preston collins on 2010-11-07
so I have resently installed ubuntu 10.10 and after a few reboots i get sent to a black terminal log in page. how do i go about booting gnome from the terminal page

---

### Post by bioterror on 2010-11-07
Log in and type: "sudo service gdm start"
And then hit ctrl+alt+f7 (ctrl+alt+f1 = first TTY screen) and you should find yourself from graphical login screen.

If not, then as a backup plan you can type "startx".
Also if you get some error messages, those could help us solve your problem, becouse you should not find yourself from TTY login screen.

---

### Post by Crusty Old Fart on 2010-11-07
This can happen if you are booting using the recovery kernel selection from the grub menu.
Please post the contents of: /etc/default/grub

For now: you may be able to continue beyond the black login screen as follows:

[LIST]
[*]Log in at the black screen with your username and password at the prompts.
[*]Issue the following command:
```

sudo service gdm start

```
[/LIST]
Good luck.

---

### Post by preston collins on 2010-11-07
Tryed 'sudo service gdm start' and it said it was already running which is good the i put in ctrl alt f7 and it went through a few lines and got locked up on checking battery... 

so i restarted and tryed startx and it gave me quite afew lines the last few are 
ddxsiggiveup: closing log
giving up
xinit: no such file or dirctory (error2): unable to connect to xserver
xinit: no such process (error3): server error

---

### Post by Crusty Old Fart on 2010-11-07
The startx command has been depreciated.

The new way to start X/gdm is:
```

sudo service gdm start

```
...and the new way to stop it is:
```

sudo service gdm stop

```

Any chance that you could post what's in your /etc/default/grub file?

Here are a few commands that might help fix things that you should be able to execute from the termininal you're getting:
```

sudo update-initramfs -k all -u
sudo update-grub

```

After issuing them, reboot.

---

### Post by sikander3786 on 2010-11-07
Make sure you are connected to the internet. Bring up the tty1 by Ctrl + Alt + F1 and try,

```
sudo service gdm stop
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install --reinstall gdm
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Reboot and see if it worked.

---

### Post by preston collins on 2010-11-07
is there an easy way of copying the log i guess from  /etc/default/grub file so i dont have to write it down everytime.

and what would be the reason i would need to stop X/gdm?

---

### Post by sikander3786 on 2010-11-07
> **preston collins said:**
> is there an easy way of copying the log i guess from  /etc/default/grub file so i dont have to write it down everytime.

and what would be the reason i would need to stop X/gdm?
I don't think it is something related to Grub at all.

---

### Post by Crusty Old Fart on 2010-11-07
I didn't mean to suggest that you needed to stop X/gdm for any particular reason. I provided the commands as education in case you ever need them in the future...like you'll need them for sikander's suggestion.

I was hoping to look at the contents of the grub file to see how the default options are set.

I'm not asking for a log file. I want to see the actual contents of the file /etc/default/grub

You should be able to dump it to your screen with this command:
```

cat /etc/default/grub

```Then, you should be able to drag your mouse over the output you see on the screen, right click and select copy, and finally paste it into a reply post.

sikander's suggestion may be what you need. Hope it works.

---

### Post by preston collins on 2010-11-07
ubuntu@ubuntu:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

And i tryed
sudo update-initramfs -k all -u sudo update-grub

and not a whole lot happened



Whats the purpose of putting "cat" infront of the command

---

### Post by preston collins on 2010-11-07
_sikander 3786_ i tryed what you asked and after the command 

sudo apt-get update && sudo apt-get upgrade
i got 2 failed msg:
W: failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg) something wicked happened resolving 'extras.ubuntu.com:http' (-5 no address associated with host name)

W: failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg) something wicked happened resolvingsecurity.ubuntu.com:http (-5 no address associated with host name)

E: some files failed to download, they have been ignored or old ones used instead

then after that i continued with the rest of the codes and nothing else went wrong other than not getting into gnome

---

### Post by Crusty Old Fart on 2010-11-07
Howdy Preston:

The command: cat, as we used it, does nothing more that print the contents of the file to your screen.

You can learn more from:
```

man cat

```Thanks for posting the output you got. I didn't see anything in there that was a problem. It looks like a virgin grub file. So, evidently, you haven't made any mods to it.

The update-initramfs command just updates some of your kernel  initialization files in case there are pending changes to them, similar  for update-grub, it just updates some of your grub files if there are  any pending changes.

Sorry to read that sikander's suggestion didn't work. I was hoping it would. It dealt with updating, upgrading, and reinstalling Gnome. After that he had you fix any broken dependencies and finally, configure any unpacked but unconfigured packages. All of that is pretty safe stuff.

You can learn more about what he was telling you from:
```

man apt-get
man dpkg

```I really didn't like the looks of the errors you got. For some reason, something wicked happened that prevented your downloads.

As I said earlier, sikander's suggestions were pretty safe in that he didn't leave you any worse off than you were. That's the mark of a good helper.

Now...I'm going to recommend something that's the mark of a bad helper. If it doesn't work not only are you going to be worse off than you were before, because Gnome will be completely gone, but you may need to perform a fresh installation of Ubuntu from scratch.

So...if you aren't terribly resistant to having to start all over with a fresh installation you could try this first:

Completely remove Gnome and all of its configuration files:
```

sudo apt-get purge gdm

```Next, install Gnome from scratch:
Note: if your download problem persists you can pretty much kiss Gnome good-bye because the step above blew it off your system. So pray that the following install command is able to run without download failures.
```

sudo apt-get install gdm

```If you got this far without any errors, then sikander's last two commands wouldn't hurt:
```

sudo apt-get install -f
sudo dpkg --configure -a

```There wouldn't be any harm in cleaning things up a bit either:
```

sudo apt-get autoremove

```Reboot.

If none of this worked, then you're probably better off starting with a brand new shiny fresh installation. How about that for a cop-out?

Good Luck,

Crusty

---

### Post by preston collins on 2010-11-07
it wouldnt let me purge gdm i got a msg saying

E: invalid operation gdm

---

### Post by Crusty Old Fart on 2010-11-07
> **preston collins said:**
> it wouldnt let me purge gdm i got a msg saying

E: invalid operation gdm

A thousand apologies, Preston. I goofed up. The purge command should have been:
```

sudo apt-get purge gdm
```It should work now.

I'm going back to correct my original post.

So sorry about that,

Crusty

---

### Post by preston collins on 2010-11-07
just gave all that a shot and it had no errors but it still didnt get me onto gnome

do you think that my video card could be affecting it cause right now im useing my onboard vid to see everything and on the other screen it has a few lines of txt

---

### Post by Crusty Old Fart on 2010-11-07
> **preston collins said:**
> just gave all that a shot and it had no errors but it still didnt get me onto gnome

do you think that my video card could be affecting it cause right now im useing my onboard vid to see everything and on the other screen it has a few lines of txt

Oh man, oh man, oh man...running dual monitors injects all sorts of complications into the mix. Let's try getting things running with just one monitor for now. I'll try to help you with the dual head setup after we get things running right on a single head.

So, please...unplug the secondary monitor, reboot, and let's see how that goes.

---

### Post by preston collins on 2010-11-07
so i unplugged the cable and pulled the card out and redid the last few codes and nothing exciting happened and no errors so i guess thats good

---

### Post by Crusty Old Fart on 2010-11-07
Okay...good...so did gnome behave itself finally?

---

### Post by preston collins on 2010-11-07
nope not yet still in the terminal layout

---

### Post by Crusty Old Fart on 2010-11-07
Okay...I need some more information.

Please run the following commands and copy|paste the output into a reply post.
```

sudo lshw -short
lspci -tvv

```
The lshw command will dump some hardware information to your screen.
The lspci command will dump a tree structure of you PCI interfaces to your screen.

I need to take a look at this info before going any further.

Thanks.

---

### Post by preston collins on 2010-11-07
ubuntu@ubuntu:~$ sudo lshw -short
H/W path          Device      Class       Description
=====================================================
                              system      K7S7AG
/0                            bus         K7S7AG
/0/0                          memory      64KiB BIOS
/0/4                          processor   AMD Athlon(tm) XP 2600+
/0/4/5                        memory      128KiB L1 cache
/0/4/6                        memory      512KiB L2 cache
/0/1                          memory      2012MiB System memory
/0/100                        bridge      746 Host
/0/100/1                      bridge      SG86C202
/0/100/1/0                    display     330 [Xabre] PCI/AGP VGA Display Adapte
/0/100/2                      bridge      SiS963 [MuTIOL Media IO]
/0/100/2.1                    bus         SiS961/2 SMBus Controller
/0/100/2.5        scsi0       storage     5513 [IDE]
/0/100/2.5/0      /dev/sda    disk        300GB Maxtor 6L300R0
/0/100/2.5/0/1    /dev/sda1   volume      273GiB EXT4 volume
/0/100/2.5/0/2    /dev/sda2   volume      5893MiB Extended partition
/0/100/2.5/0/2/5  /dev/sda5   volume      5893MiB Linux swap / Solaris partition
/0/100/2.5/1      /dev/cdrom  disk        DVD-RAM GSA-H22L
/0/100/2.5/1/0    /dev/cdrom  disk        
/0/100/2.5/0.1.0  /dev/scd1   disk        DVDRAM GSA-4040B
/0/100/2.7                    multimedia  AC'97 Sound Controller
/0/100/3                      bus         USB 1.1 Controller
/0/100/3.1                    bus         USB 1.1 Controller
/0/100/3.2                    bus         USB 1.1 Controller
/0/100/3.3                    bus         USB 2.0 Controller
/0/100/4          eth0        network     SiS900 PCI Fast Ethernet
/0/100/9                      multimedia  CA0106 Soundblaster



ubuntu@ubuntu:~$ lspci -tvv
-[0000:00]-+-00.0  Silicon Integrated Systems [SiS] 746 Host
           +-01.0-[01-02]----00.0  Silicon Integrated Systems [SiS] 330 [Xabre] PCI/AGP VGA Display Adapter
           +-02.0  Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO]
           +-02.1  Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
           +-02.5  Silicon Integrated Systems [SiS] 5513 [IDE]
           +-02.7  Silicon Integrated Systems [SiS] AC'97 Sound Controller
           +-03.0  Silicon Integrated Systems [SiS] USB 1.1 Controller
           +-03.1  Silicon Integrated Systems [SiS] USB 1.1 Controller
           +-03.2  Silicon Integrated Systems [SiS] USB 1.1 Controller
           +-03.3  Silicon Integrated Systems [SiS] USB 2.0 Controller
           +-04.0  Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet
           \-09.0  Creative Labs CA0106 Soundblaster

---

### Post by Crusty Old Fart on 2010-11-07
Thanks for your quick response.

I just noticed something that I missed before. Whenever you send me a copy of your screen, it shows you as ubuntu@ubuntu. That suggests to me that you are using a live installation CD.

So now I'm a little confused:

[LIST]
[*]Does the live CD get you into Gnome?
[*]Did you install a proprietary driver for your onboard graphics adapter?
[/LIST]
Also, please post the output from the following command:
```

lsmod | grep drm

```

---

### Post by preston collins on 2010-11-07
yea im using the try it on the live cd and it gets me in.


i dont believe i have installed any other driver for my onboard graphics 


ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
dm_crypt               11385  0 
lp                      7342  0 
snd_intel8x0           25632  2 
snd_ca0106             31595  2 
snd_ac97_codec         99227  2 snd_intel8x0,snd_ca0106
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  3 snd_intel8x0,snd_ca0106,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
snd                    49006  16 snd_intel8x0,snd_ca0106,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 29886  0 
parport_pc             26058  1 
serio_raw               4022  0 
i2c_sis96x              3196  0 
soundcore                880  1 snd
parport                31492  3 lp,ppdev,parport_pc
joydev                  8735  0 
snd_page_alloc          7120  3 snd_intel8x0,snd_ca0106,snd_pcm
squashfs               25209  1 
aufs                  152358  4041 
nls_cp437               4931  1 
isofs                  30022  1 
dm_raid45              81721  0 
xor                    15136  1 dm_raid45
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
usbhid                 36882  0 
hid                    67742  1 usbhid
sis_agp                 4123  1 
floppy                 54311  0 
sis900                 17316  0 
mii                     4425  1 sis900
agpgart                32011  1 sis_agp


and grep drm isnt doing anything

---

### Post by Crusty Old Fart on 2010-11-08
Okay...I'm trying to wrap my brain around what has been happening in this thread, when there were times I thought we were dealing with your actual installation, when in truth, we were dealing with what was loaded into RAM from your live CD.


[LIST=1]
[*]I should have realized that there would have been no way for you to copy from your terminal and post it to the web when you couldn't have brought up a browser without Gnome. arrgh.
[*]So...the command: lsmod shows us the status of the modules in the Linux Kernel. But, I think what we're seeing is not the kernel in your installation, but the kernel loaded into RAM by the live CD.
[*]The most encouraging pieces of information so far have been:

[LIST=a]
[*]Gnome works from the live CD. That tells us that whatever default driver the CD is using works okay for your monitor and we don't need anything proprietary.
[*]When you installed the system, you didn't load a proprietary graphics driver. So, we don't have to be concerned with removing one.
[/LIST]

 
[*]Since the CD doesn't install anything in tryout mode, the data we got from: cat /etc/default/grub most likely came from your installation.
[*]The commands lshw and lspci probe hardware so that data is good.
[/LIST]

There's a little problem that came along with the newer distributions of Ubuntu. It's called Kernel Modesetting (KMS). It kind of raises hell with certain hardware. There's another little problem for folks who want to run multi head systems. It's called RandR. RandR cannot handle more than one graphics card. So, if you want a dual head setup, you either need a dual port graphics card, or you'll need to disable RandR. Eventually we will disable RandR in your case (more about this later). KMS and RandR are enabled by default and work with each other to minimize boot times. Part of what they do is manage the display(s). This is fine as long at the default driver being used by your graphics card is KMS compatible. In your case, I don't believe it is. So, we need to see if we can get Gnome to come to life with KMS disabled.

Earlier, you wrote that when you tried to start the X server, with the command: sudo service gdm start, the system told you it was already running. But, yet you weren't seeing anything Gnome. That didn't make sense to me until now. I think there's a possibility that since KMS didn't find a KMS-compatible driver for your graphics card, it couldn't partner with RandR to configure your monitor. So, we'll need to force the system to generate a configuration file for X. Once we've done that, it will take priority over anything KMS and RandR want to do.

So, let's give it a try. Here's how to do it, step by step:

**Step 1:** Remove the Live CD.

**Step 2:** Reboot.

**Step 3:** Log in to your black terminal screen with your username and password.

**Step 4:** In order to generate an X configuration file, we need to shut down X/gdm with the following command:
```

sudo service gdm stop

```**Step 5:** Generate an X configuration file with the following command:
```

sudo X -configure

```**Step 6:** The system will have created a file named: xorg.conf.new in Step 5. It is stored in your home directory (~). This file needs to be copied into /etc/X11 as: xorg.conf
You do this with the following command:
```

sudo cp ~/xorg.conf.new /etc/X11/xorg.conf

```**Step 7:** Check to see that it made the trip:
```

ls /etc/X11 | grep xorg
[COLOR=Red]**...your output should be one line, as follows...**[/COLOR]
xorg.conf

```
**Step 8:** Reboot and pray that the system was able to configure a good xorg.conf file that we don't have to edit.

If we are really, really lucky, Gnome will come alive. If not, it may be something simple that won't be too hard to fix.

So, that's my best thinking so far, Preston. If I'm right about the cause of this problem, a fresh install wouldn't have fixed it.

Please, let me know how it goes.

Thanks,

Crusty

---

### Post by preston collins on 2010-11-08
i just finished with a fresh install do you still want me to go though with all that because most likely it wont take me back to that screen for a few more restarts

---

### Post by Crusty Old Fart on 2010-11-08
Wo!

What's that??? Are you successfully getting into Gnome for your first few boots and then it gives up and throws virtual terminal tty1 screens at you forever after?

Or did the virtual terminals just start showing up when you tried to go for your dual head setup?

---

### Post by preston collins on 2010-11-08
yea i get to boot up a hand full of times after the install then it gives up on me but i have a feeling that it was the vid card that was messing with things.

im gona keep everything that you have said at hand just incase it happens again

---

### Post by Crusty Old Fart on 2010-11-08
Just in case you get the urge to start without me, here's my tutorial on how to extend a desktop across dual monitors. I'm sure you'll notice some similarities in my earlier post.

[How to: Extend desktop across dual monitors]("http://ubuntuforums.org/showthread.php?t=1611704")

Good Luck,

Crusty

---

### Post by preston collins on 2010-11-08
i didnt want the dual head, i had to install the new vid card cause the onboard wasnt working properly, but i do think that the new card was affecting it some how

---

### Post by Crusty Old Fart on 2010-11-08
Oh...okay...well, that may keep things a little simpler. By the way, if you start experiencing problems with the onboard adapter and decide to snap in the daughter board. I think you'll have a much easier time with Ubuntu booting correctly if you don't connect an additional monitor to it. Just move your monitor's data cable from the onboard port to the daughter board's port. You may need to run: update-initramfs -u if you do that since the kernel may load a different driver module for the new card. At this point, we just don't know.

Like I wrote earlier, dual head systems are not easy to deal with now. The cats at Xorg kind of abandoned the old way of doing things and went to RandR before RandR was really ready for a wide range of multi-headed setups. To add insult to injury this happened damned near coincidentally with the implementation of KMS in Ubuntu. The whole ball of snakes has really been a headache for a LOT of Linux geeks. People are surprised to find that the new versions of Ubuntu have no xorg.conf file. It has to be generated by the user if it's needed. This whole bit has been a huge step backward for Ubuntu's solution for the multi-head geeks out here.

Anyway Preston, good luck with the mess. It's bedtime for this old fart.

G'nite,

Crusty

---

### Post by preston collins on 2010-11-10
hey so all was going good then after i put in my nividia geforce 9400gt 1G pci video card and istalled the recomended driver for it and rebooted it i was sent back to the black sign in screen any ideas?

---

### Post by Crusty Old Fart on 2010-11-10
Well, Preston:

At least now we know what the cause of the problem is.

I'm beginning to wonder if there's a problem with the system running two graphics adapters: one being your onboard adapter and the other being the daughter board. If its trying to do that, it may be what's choking Gnome, especially considering that your onboard adapter may take priority as the primary adapter.

If you can **disable the onboard adapter in your BIOS settings**, then your daughter board should become the primary (and obviously ONLY) adapter that the system sees, and with any luck, you'll have Gnome come up with a big smile.

I think that's worth a try.

Hope it works.

---

### Post by preston collins on 2010-11-10
i have attempted that many times in the bios i have the pci as my main video card or well so it looks like but i have had it like that since i got the card a yr ago.

even then it still doesnt show the initial boot up screen ive been trying to look around to see if anyone else has had the same problem but so far i have come up with nothing, im given a choice between using AGP or PCI and i have it set for pci

---

### Post by Crusty Old Fart on 2010-11-10
No...that's not what I'm talking about.
[INDENT]**AGP**: stands for Accelerated Graphics Processor. Typically, there is a special AGP slot on the mother board for those kinds of cards. I think you'd know it if you were plugging your Nvidia card into it. Usually, there's only one AGP slot on a motherboard, whereas there can be several PCI slots.

**PCI**: is most likely the interface that your Nvidia card uses.
[/INDENT]Bottom line here: the BIOS setting that you've set to: PCI probably doesn't have anything to do with the onboard graphics adapter.

I'm hoping that you'll find **another** setting in your BIOS that will allow you to disable the onboard graphics adapter, similar to how many BIOS's allow you to disable the integrated sound card.

Am I making any sense here?

---

### Post by Crusty Old Fart on 2010-11-10
I'm also back to wondering again if the driver for your Nvidia card is not KMS compatible.

What happens if you add the kernel option:
```

nomodeset

```
to the end of the kernel that you select for grub to use for booting?

---

### Post by preston collins on 2010-11-10
yea that all makes sence i havent seen anything that looks like it can turn off the onboard graphics but i'll take another look and with the 
Code
nomodeset
[FONT=monospace]how do i type that into the terminal 

[/FONT]

---

### Post by Crusty Old Fart on 2010-11-10
Well, we won't be using the terminal to add the **nomodeset** kernel option until we determine if it helps.

We can find out what it will do for us by using it one time.

Here are the steps:

[LIST=1]
[*]Reboot the machine.
[*]Using your up/down arrow buttons, select the kernel you use to boot into Ubuntu if it isn't already highlighted. Press the letter e on your keyboard. That will take you to a new screen where you can edit the kernel boot options.
[*]Find the line that ends with: **quiet splash**
[*]At the end of that line type in **nomodeset**
[*]Make sure you leave at least one space between the words: **quiet splash nomodeset**
[*]Press the key combination: **Ctrl+X** to resume booting.
[/LIST]
And see what happens. It won't hurt anything if it doesn't work. And the added boot option doesn't get remembered.

Also, we should probably get on the telephone. I live in the United States.

---

### Post by preston collins on 2010-11-10
yea i live in canada dont worry about it my brother inlaw is a geek he should know what to do about the onboard settings which i just looked and there was nothing about shuting off the onboard graphics from the bios.

I'll giev that a shot

---

### Post by preston collins on 2010-11-10
so tryed to add the boot option nothen happened

and right now i booted up in the recovery mode but i still dont know how to disable the onboard graphics

---

### Post by Crusty Old Fart on 2010-11-10
The setting to disable the onboard graphics doesn't exist in all BIOS's. So, evidently it isn't in yours. Thanks for looking for it.

I think it's finally time to ask you to follow the procedure I explained in:
[Post number 24 of this thread.]("http://ubuntuforums.org/showpost.php?p=10087668&postcount=24")

And...I have another question: Are you using the **nouveau** driver for your Nvidia card?

---

### Post by preston collins on 2010-11-10
the driver that is requesting me to install is "NVIDIA accelerated graphics driver (version curren) [Recommended]"  or NVIDIA accelerated graphics driver (version 173)

i installed the first one but have just removed it

---

### Post by Crusty Old Fart on 2010-11-10
Okay...neither one of those drivers is KMS compatible. KMS is enabled by default for the -intel, -ati, and -nouveau drivers.  It is not available for any other drivers at this time.

So, you can't run KMS even if you wanted to with the hardware you have. And, since there is no xorg.conf file that is created upon installation anymore, the x server won't be able to configure your display.

As soon as you finish experimenting with different drivers, I think we NEED  to generate an xorg.conf file. Until we do that, I doubt you'll ever see Gnome from that graphics card.

Please let me know what happens after you follow the procedure I gave you in post #24.

If you don't want to do that, maybe we can play a different game :cool:

---

### Post by preston collins on 2010-11-11
i have the card plugged into my computer but i have uninstalled the driver so i dont get that tty1 screen any more whats that screen actual name. should i install that driver and then attempt the process that you suggested 

thanks for the help so far its making it easier to learn

---

### Post by Crusty Old Fart on 2010-11-11
Howdy Preston:

The tty1 screen is often referred to as a "virtual shell" as opposed to the shell that you get when you open a terminal window.

In general, a "shell" refers to any command interpreter that serves as a textual interface between the user and the kernel.

The terminal window in Linux is often referred to just as a "shell", a "bash shell", or a "CLI".

Years ago, the bash shell was just the Bourne shell. It was created by Mr. Bourne. Therefore the name: Bourne shell, which was often abbreviated as: bsh.

As time passed, the Bourne shell experienced a significant upgrade. The new version was renamed as the "bash" shell. Bash is an acronym for: **B**ourne **A**gain **SH**ell. Cute, eh? It's true, I'm not making this up.

CLI is an acronym that stands for: **C**ommand **L**ine **I**nterface.

All this is probably way more information than you wanted, but it may help you understand what you're reading a little better when you find these terms used on web pages that you visit in your search for answers to other Linux questions.
[br] [/br]
[br] [/br]
_With regard to the next step in this project:_ My recommendation is that you go ahead and install the driver that the system recommends. Then, follow steps 1 through 8 in [Post #24]("http://ubuntuforums.org/showpost.php?p=10087668&postcount=24")

After you do that, one of two things is going to happen:
[LIST=1]
[*] Gnome will come up and everything will work so well that we'll want to throw a party and invite everybody over to your house to show them what you did.
[br] [/br]
[br] [/br]
[*] Gnome still won't come up. However, you will have had the system generate an xorg.conf file that you'll be able to post here, like you posted the contents of /etc/default/grub several days ago, and then we can modify it to make it work.
[/LIST]
So, after installing the recommended driver and following the procedure in post #24, regardless of whether Gnome comes up or not, we'll be a helluva lot better off than we are right now because we'll have a configuration file for X that we can fix.

Good Luck!

---

### Post by preston collins on 2010-11-14
alright so i went through the steps and i couldnt quite understand the last step

ls /etc/X11 | grep xorg 
i didnt know how to instert it as a code so i got it to do something after trying to get the code to work.

after restarting it didnt take me to the virtual shell but it gnome didnt fully load

now what do i need to type to veiw xorg.conf soi can post it online

As well i cant get into the recovery kernal or into the page that enables me to choose between original ubuntu or recovery

---

### Post by Crusty Old Fart on 2010-11-14
> 
now what do i need to type to veiw xorg.conf soi can post it online

Boot using your live CD and get into tryout mode.

Open a terminal and issue the following command:
```

cat /etc/X11/xorg.conf

```
Drag your mouse over all of the output, right click and select copy to grab the highlighted output, and post it into a reply message on this thread.

---

### Post by preston collins on 2010-11-14
ubuntu@ubuntu:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory

---

### Post by Crusty Old Fart on 2010-11-14
Uh oh...somehow the ~/xorg.conf.new file didn't get copied to /etc/X11/xorg.conf

Hopefully, the file xorg.conf.new got generated and is in your home (~) directory.

Perhaps we can check for it.

For the next command, where I have used the word: [COLOR=Blue]**username**[/COLOR], you'll need to substitute the username you chose for yourself when you did your last install. I'm not sure this next command will work from the Live CD but it won't hurt anything if it fails. So let's give it a shot:
```

cat /home/**[COLOR=Blue]username[/COLOR]**/xorg.conf.new 

```

Please post the output that you get from doing that.

Thanks

---

### Post by preston collins on 2010-11-14
ubuntu@ubuntu:~$ cat /home/prestoncollins/xorg.conf.new
cat: /home/prestoncollins/xorg.conf.new: No such file or directory

---

### Post by Crusty Old Fart on 2010-11-14
I was afraid of that. In order to help you from this point, I need to shut down my computer and boot from a Live CD so that I don't tell you to try anymore commands that don't work.

This could take a while, and I don't want to do it if you're not going to be awake for the next hour or so.

Do you have time for this?

---

### Post by preston collins on 2010-11-14
im gona be up for the next 4 hours plenty of time if ur willing

---

### Post by Crusty Old Fart on 2010-11-14
Okay Buddy...Let's do it. I'll post back as soon as I'm running off a live CD.

I'm back, running off a live CD...Hang on while I check a few things out.

---

### Post by Crusty Old Fart on 2010-11-14
Okay...this is pretty easy. We need to get the hard drive where you installed Ubuntu mounted.

We'll do this from the menus in Gnome.


[LIST=1]
[*]At the upper left corner of your screen, click on: **Places**
[*]Find the hard drive that has your Ubuntu installation on it in the list and click on it.
[*]The drive should show up on your desktop.
[/LIST]
Let me know if you got through these steps ok.

---

### Post by preston collins on 2010-11-14
good so far

---

### Post by Crusty Old Fart on 2010-11-14
Enter the following command and post the output:
```

cat /etc/mtab

```

---

### Post by preston collins on 2010-11-14
ubuntu@ubuntu:~$ cat /etc/mtab
aufs / aufs rw 0 0
none /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
/dev/sda1 /media/cf92f996-4b2c-435f-9681-283f352c0ade ext4 rw,nosuid,nodev,uhelper=udisks 0 0

---

### Post by Crusty Old Fart on 2010-11-14
You're doing great, Preston!

Now, enter the following command and post the output:
```

ls -al /media/c*/etc/X11

```

---

### Post by preston collins on 2010-11-14
ubuntu@ubuntu:~$ ls -al /media/c*/etc/X11
total 96
drwxr-xr-x  10 root root  4096 2010-11-14 23:47 .
drwxr-xr-x 136 root root 12288 2010-11-15 01:24 ..
drwxr-xr-x   2 root root  4096 2010-10-07 16:14 app-defaults
drwxr-xr-x   2 root root  4096 2010-10-07 16:14 cursors
-rw-r--r--   1 root root    14 2010-10-07 16:15 default-display-manager
drwxr-xr-x   6 root root  4096 2010-10-07 16:10 fonts
-rw-r--r--   1 root root 17394 2010-05-28 01:59 rgb.txt
lrwxrwxrwx   1 root root    13 2010-11-08 04:32 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2010-10-07 16:14 xinit
drwxr-xr-x   2 root root  4096 2010-04-15 12:12 xkb
-rw-r--r--   1 root root  3859 2010-11-15 01:11 xorg.conf
-rw-r--r--   1 root root   269 2010-11-11 02:41 xorg.conf.failsafe
-rwxr-xr-x   1 root root   709 2010-08-09 10:20 Xreset
drwxr-xr-x   2 root root  4096 2010-10-07 16:01 Xreset.d
drwxr-xr-x   2 root root  4096 2010-10-07 16:01 Xresources
-rwxr-xr-x   1 root root  3730 2010-08-09 10:30 Xsession
drwxr-xr-x   2 root root  4096 2010-11-08 05:34 Xsession.d
-rw-r--r--   1 root root   265 2010-05-28 01:59 Xsession.options
-rw-------   1 root root   601 2010-10-07 16:01 Xwrapper.config

---

### Post by Crusty Old Fart on 2010-11-14
Excellent!

Now, enter the following command and post the output.
```

cat /media/c*/etc/X11/xorg.conf

```

---

### Post by preston collins on 2010-11-14
ubuntu@ubuntu:~$ cat /media/c*/etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
    Load  "dri"
    Load  "record"
    Load  "dri2"
    Load  "dbe"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoKey"               # <i>
        #Option     "FlatPanel"              # [<bool>]
        #Option     "FPDither"               # [<bool>]
        #Option     "CrtcNumber"             # <i>
        #Option     "FPScale"                # [<bool>]
        #Option     "FPTweak"                # <i>
        #Option     "DualHead"               # [<bool>]
    Identifier  "Card0"
    Driver      "nv"
    BusID       "PCI:3:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "fbdev"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by Crusty Old Fart on 2010-11-14
Perfect.

I need a couple of minutes to study that. I'll edit this post when I'm done.

Okay...the system is trying to run two monitors. Probably because it is seeing two graphics cards, your integrated (on-board card), and your Nvidia card. Fortunately, it is using your Nvidia card as the primary graphics adapter. It is using the "nv" driver for that card, which I am assuming is the driver that you installed. The integrated card is being driven by the "fbdev" driver, which I believe is the default frame buffer driver.

So, here's what we're going to do. I am going to copy your xorg.conf file and edit it to set it up for a single monitor. When I finish editing it, I'm going to upload it as an attachment and then I'm going to tell you how to install it.

[COLOR=Red]**Before**[/COLOR] we do any of that, we are going to save a copy of the xorg.conf to a new file named xorg.conf_original right now so that if I goof up, we'll always be able to restore the original version that's on the system now.

I'll give you the commands we need in my next post.

---

### Post by preston collins on 2010-11-14
if it screws up i dont have anything on the hard drive that i need so dont worry about it too much and i have time to do a fresh install

---

### Post by Crusty Old Fart on 2010-11-14
First, we need to get you into the X11 directory.
Enter the following command:
```

cd  /media/c*/etc/X11

```
Now we need to copy xorg.conf to xorg.conf_original
But, you'll need to use **sudo** to issue the command with root level permissions.
Enter the following command:
```

sudo cp xorg.conf xorg.conf_original

```
Next, I need to take a look at what you did by seeing what's in X11.
So, please post the output from the following command:
```

ls -al

```

Let's see how that goes.

---

### Post by preston collins on 2010-11-14
ubuntu@ubuntu:/media/cf92f996-4b2c-435f-9681-283f352c0ade/etc/X11$ ls -al
total 100
drwxr-xr-x  10 root root  4096 2010-11-15 09:49 .
drwxr-xr-x 136 root root 12288 2010-11-15 01:24 ..
drwxr-xr-x   2 root root  4096 2010-10-07 16:14 app-defaults
drwxr-xr-x   2 root root  4096 2010-10-07 16:14 cursors
-rw-r--r--   1 root root    14 2010-10-07 16:15 default-display-manager
drwxr-xr-x   6 root root  4096 2010-10-07 16:10 fonts
-rw-r--r--   1 root root 17394 2010-05-28 01:59 rgb.txt
lrwxrwxrwx   1 root root    13 2010-11-08 04:32 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2010-10-07 16:14 xinit
drwxr-xr-x   2 root root  4096 2010-04-15 12:12 xkb
-rw-r--r--   1 root root  3859 2010-11-15 01:11 xorg.conf
-rw-r--r--   1 root root   269 2010-11-11 02:41 xorg.conf.failsafe
-rw-r--r--   1 root root  3859 2010-11-15 09:49 xorg.conf_original
-rwxr-xr-x   1 root root   709 2010-08-09 10:20 Xreset
drwxr-xr-x   2 root root  4096 2010-10-07 16:01 Xreset.d
drwxr-xr-x   2 root root  4096 2010-10-07 16:01 Xresources
-rwxr-xr-x   1 root root  3730 2010-08-09 10:30 Xsession
drwxr-xr-x   2 root root  4096 2010-11-08 05:34 Xsession.d
-rw-r--r--   1 root root   265 2010-05-28 01:59 Xsession.options
-rw-------   1 root root   601 2010-10-07 16:01 Xwrapper.config

---

### Post by Crusty Old Fart on 2010-11-14
You're getting really good at this.

I'll have a new version of xorg.conf uploaded in about five or ten minutes.

---

### Post by Crusty Old Fart on 2010-11-15
Okay...the file is uploaded.

Can you download it to your Live desktop?

---

### Post by preston collins on 2010-11-15
saved to desktop

---

### Post by Crusty Old Fart on 2010-11-15
Good.

Now we need to go back to the terminal and enter some more commands

First, we need to get to your desktop with the following command:
```

cd ~/Desktop

```

Please post the output of the following command:
```

ls -al

```

---

### Post by preston collins on 2010-11-15
ubuntu@ubuntu:~/Desktop$ ls -al
total 20
drwxr-xr-x  2 ubuntu ubuntu  100 2010-11-15 10:08 .
drwxr-xr-x 23 ubuntu ubuntu  640 2010-11-15 09:49 ..
-rwxr-xr-x  1 ubuntu ubuntu  203 2010-11-15 02:12 examples.desktop
-rwxr-xr-x  1 ubuntu ubuntu 8534 2010-11-15 01:26 ubiquity-gtkui.desktop
-rw-r--r--  1 ubuntu ubuntu 2100 2010-11-15 10:08 xorg.txt

---

### Post by Crusty Old Fart on 2010-11-15
Okay good.

Now let's get back into X11 with the following command:
```

cd  /media/c*/etc/X11
```Next, we'll bring in a copy of the xorg.txt file and rename it to xorg.conf with the following command:
```

sudo cp ~/Desktop/xorg.txt xorg.conf

```Finally, we'll check to see that everything made the trip okay.
Please post the output from the following command:
```

cat xorg.conf

```...and we'll see how all that went.

---

### Post by preston collins on 2010-11-15
ubuntu@ubuntu:/media/cf92f996-4b2c-435f-9681-283f352c0ade/etc/X11$ cat xorg.confSection "ServerLayout"
Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
EndSection

Section "Module"
Load "glx"
Load "dri"
Load "record"
Load "dri2"
Load "dbe"
Load "extmod"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
EndSection

Section "Device"
### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
### <percent>: "<f>%"
### [arg]: arg optional
#Option "SWcursor" # [<bool>]
#Option "HWcursor" # [<bool>]
#Option "NoAccel" # [<bool>]
#Option "ShadowFB" # [<bool>]
#Option "UseFBDev" # [<bool>]
#Option "Rotate" # [<str>]
#Option "VideoKey" # <i>
#Option "FlatPanel" # [<bool>]
#Option "FPDither" # [<bool>]
#Option "CrtcNumber" # <i>
#Option "FPScale" # [<bool>]
#Option "FPTweak" # <i>
#Option "DualHead" # [<bool>]
Identifier "Card0"
Driver "nv"
BusID "PCI:3:0:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Viewport 0 0
Depth 1
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

---

### Post by Crusty Old Fart on 2010-11-15
Okay good deal.

Now it's time for the smoke test.

Remove your live CD, reboot, and please, oh please please please tell me that Gnome came up and we can throw a big fat party.

---

### Post by preston collins on 2010-11-15
so a little bit after i posted the ubuntu@ubuntu:/media/cf92f996-4b2c-435f-9681-283f352c0ade/etc/X11$ cat xorg.confSection "ServerLayout"

my computer froze up so i had to force a restart, then i restarted it without the cd in and nothing has changed since we first started tonight


I guess its a small question to all of this but should i have both video outputs be plugged in the vga and dvi

---

### Post by Crusty Old Fart on 2010-11-15
No...one or the other...NOT both.

Did you have both of them plugged in?

...and...

Did you have a monitor connected to your on-board card as well as another connected to your Nvidia card?

---

### Post by preston collins on 2010-11-15
right now i have it plugged into the onboard = VGA but i do remember unplugging the cable that is going to the card = DVI but i dont remember when that was.

When i had the both of them plugged in they were both plugged into the monitor

---

### Post by Crusty Old Fart on 2010-11-15
Preston, look at me, this is important.

At some point you need to set your system up with a particular configuration and leave it that way until we get it running.

I can't help you if things keep changing that I don't know about.

Through all this, I had assumed that you had one monitor, plugged into the VGA port of your Nvidia graphics card when you did your last installation and that you left it that way throughout everything we did tonight.

But now, you tell me that assumption is wrong. Furthermore, I'm completely unsure of how your system was configured when you had the system automatically generate the xorg.conf.new file.

I could probably, maybe, figure it out if I study the xorg.conf files that you posted tonight.

There are other things that you wrote at the beginning of the night that confuse me. They are:
> 
ls /etc/X11 | grep xorg 
i didnt know how to instert it as a code so i got it to do something after trying to get the code to work.
I have no idea what you did or what you got the system to do, or whether it was good or bad. It's not a good idea to experiment with issuing commands to the shell if you have no idea what they will do.
> 
after restarting it didnt take me to the virtual shell but it gnome didnt fully load
That doesn't sound very good.
> 
As well i cant get into the recovery kernal or into the page that enables me to choose between original ubuntu or recovery
That sounds even worse. It indicates that there's a pretty serious problem with the boot loader.

So, you did really well tonight, and you must have followed the instructions very well in Post #24, because you did get the system to generate an xorg.conf.new file and you were successful in copying it into /etc/X11.

But, something had happened that had the boot loader messed up as well as your monitor configuration.

So, here's what I think we should do next:

Agree on a configuration of graphics adapters, monitors, and connections. Then we leave it that way, and reinstall the operating system from scratch. Then we deal with whatever little problems it serves up. We can do that. And...we'll have the best chance of getting things running.

However, if the system hardware is constantly changing, while we're trying to configure the code to run it, then there's little hope that we'll ever get it running unless Jesus was a geek and decides to perform a miracle for us.

Okay?...I'm willing to help you, but if you make it impossible for me, then we're justing wasting time for nothing.

So how about we agree on a hardware configuration. I suggest the following.

[LIST]
[*]Get the monitor that you want to use and plug it into the DVI port of your Nvidia card.
[*]Don't connect any other cables to your Nvidia card.
[*]Don't connect anything to your on-board video card.
[/LIST]
If you'd rather have a different setup, then let me know what you want it to be so that I'll know what we're dealing with. But I'll warn you now, if you start changing hardware around again without letting me know, then I'm going blow out of this sandbox because I don't have time to spend the rest of my life in it for nothing.

Understand?

---

### Post by preston collins on 2010-11-15
Yea im srry about that i havent ever had the monitor plugged into the  Nvidias vga only the dvi, i had the monitor plugged into the onboards  vga. I am pretty sure i had only the onboards vga plugged into the  monitor before our chats tonight i unplugged the dvi which would of been  after creating the xorg.conf.new file

When i tryed the step in Post #24 ls /etc/X11 | grep xorg i didnt know  if it was suppose to be in 2 parts or one so i tryed separating it and  it said LS wasnt installed so i installed it they tryed  ls /etc/X11  again and it didnt give me the usual comand lines instead there was  nothing so i tryed typing grep xorg and nothing happened so i restarted  it. I also tryed it as a whole but i ddint know how to type the big old  bar that is separating the code nothing happened there.

When the restart had stopped loading it came up to a purple screen with a  3 inch black bar on the right side of the screen not sure what happened  there. that screen came up at the same time the virtual shell would  have.

There have been a couple times where i could get into it i figured it  was how i had the boot up sequence set up but i dont know how that would  affect it other than it not being able to start from the hard drive  which i did change it to so i could try to boot it up after we altered  the xorg file.

Yes i do agree with that configuration the main goal is to only be using the Nvidias DVI port

Maby someday in the future when i totally understand whats going on then  i might have a dual but there is no real reason for me to have that for  a while now

i guess one question u might be able to answer is when i do the fresh  install will the dvi on the nvidia actually work for the video instead  of the onboard especially with out having the driver for it not  installed

I really do appreciate everything that you are doing for me i really  dont like making things hard for myself or other ppl especially if they  are helping me out.

---

### Post by jocko on 2010-11-15
I've been reading this thread, and think I can help.

First, it looks like your xorg.conf is set up for using the "nv" driver. That is a very poor driver which has been abandoned by nvidia. You are better off using the "nouveau" driver (open source, installed and used by default on ubuntu) or the "nvidia" driver (proprietary).

From what I have read so far I have jumped to the following conclusions:
1. Everything works fine on a clean install (even with the nvidia card plugged in and in use)?
In that case, the nouveau driver works for you. Please correct me if I'm wrong. It's important to know which card works at which stage and with which driver installed...
2. Once you install the nvidia driver (prompted by the hardware driver manager) you end up with a system that can't start gnome.
This usually means there is some misconfiguration that prevents X from starting.
3. When you uninstall nvidia, you still can't get X started. This is probably because your /etc/X11/xorg.conf tries to use the nv driver...
4. I'm not sure which video card's vga and dvi you talk about, but of course you should only try to use ONE of them. You can't use both cards, so plug the nvidia card to the monitor by whatever connection it has, and unplug any connection between the onboard card and the monitor. Dual display can only be accomplished by connecting ONE graphics card to two monitors, so there is absolutely no point in trying to connect both graphics cards. If the nvidia card only have one output you'll never be able to use dual screen.


To use nouveau, simply delete your xorg.conf (or rename if you want to have a backup).
This command will do it for you (from a virtual terminal on your actual install, if you do it from a live cd you'll have to mount the partition and adjust the paths in the command accordingly):
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Reboot and see if it works.

If it still just boots to a virtual terminal, we need to see the reason why and not just try random things that may or may not help.
The first place to look when there is a problem with X is in the file /var/log/Xorg.0.log (from your actual installed system, not from a live cd). Post it's entire contents here, but be sure to paste it between [noparse]```
 and 
```[/noparse] to get a nice scrollable code box.

---

### Post by preston collins on 2010-11-15
all is true except  #3 i have been able to uninstall the driver and it did restart but i had to go into recovery mode, i cant get back there beacuse i have no idea how i got the kernals to show up in the first place

The nividia card has a s-video, vga and a dvi port and then my on board is a vga but i dont want to use the onboard anymore i had issues with it awhile ago not working properly with windows XP

the only thing is how do i get the nvidia to work when i do the fresh install will it actually start up my monitor or will my computer try to force the onboard to work

AS well i have no idea whats going on when its booting up because my bios doesnt give me the option to change the setting so i can use the nvidia card instead of the onboard video

---

### Post by jocko on 2010-11-15
> **preston collins said:**
> the only thing is how do i get the nvidia to work when i do the fresh install will it actually start up my monitor or will my computer try to force the onboard to work
If you boot from a live cd with only the nvidia card connected, does it work?
In that case, the nouveau driver works fine, and it should still work after a clean install.

But try my suggestion to rename the xorg.conf first. It is not needed and if it's misconfigured (which I'm convinced it is as it's set to use nv) it can cause a lot of problems...

---

### Post by preston collins on 2010-11-15
i haven't try it without having the onboard plugged in it kinda annoys me when i cant see the boot up sequence but i will give it a shot

---

### Post by Crusty Old Fart on 2010-11-15
> 
If you boot from a live cd with only the nvidia card connected, does it work?
In that case, the nouveau driver works fine, and it should still work after a clean install.
That's a damned good idea, jocko. Thanks for coming in here to help us out. I would LOVE it if the nouveau driver works with Preston's card.

It would also be nice to know which port, DVI or VGA, on the Nvidia card, is connected when Preston boots from the Live CD.

Preston: If you want to disable your xorg.conf file, as jocko has suggested, the commands you need to use when you're running from the Live CD are:
```

cd /media/c*/etc/X11
sudo mv xorg.conf xorg.conf.bak

```Just enter them one at a time in a terminal window.

Thanks again, jocko, for coming in here. Evidently my prayers were answered. I was wondering how this thread got so far along without an expert showing up to help us out. I could only imagine everybody kicking back and laughing at the Preston and Crusty show. It's been a pretty frustrating time for both of us, though I have to give Preston credit for having more patience with it than I have at times.

---

### Post by preston collins on 2010-11-15
Jocko 

so i tryed to start up the computer with just the dvi on the nvidia card  plugged in and it only got so far as the purple ubuntu 10.10 screen and  then i plugged the vga from the onboard before i restarted it and it  had loaded to the try it page 

crusty old fart 

i tryed the 2 codes 
> sudo mv xorg.conf xorg.conf.bak

but the second one said 
> 
buntu@ubuntu:/media/cf92f996-4b2c-435f-9681-283f352c0ade/etc/X11$ mv xorg.conf xorg.conf.bak
mv: cannot move `xorg.conf' to `xorg.conf.bak': Permission denied

dont know what to do from there

---

### Post by jocko on 2010-11-15
> **Crusty Old Fart said:**
> Thanks again, jocko, for coming in here. Evidently my prayers were answered. I was wondering how this thread got so far along without an expert showing up to help us out.
Well, unfortunately I just made a quick visit here and have to move on (getting ready to go to work)... I rarely respond to prayers, but apparently I did this time.
I may check in later to see what's happened, but hopefully someone else will stop by to help Preston out...

Preston: You forgot to use** sudo** in the command.
It should be:
```
**sudo** mv xorg.conf xorg.conf.bak
```

---

### Post by Crusty Old Fart on 2010-11-15
It looks like you forgot to type sudo before mv.

Try it again using sudo.

---

### Post by preston collins on 2010-11-15
so i gave that a shot then restarted it and it does boot up but it only goes as far as the main ubuntu 10.10 start up page then when i plug the onboard vga into the monitor i get the screen with the try it or install it
```
cd /media/c*/etc/X11
 sudo mv xorg.conf xorg.conf.bak
```

---

### Post by Crusty Old Fart on 2010-11-15
What that seems to indicate, at least from what jocko was telling us, is that the default nouveau driver won't work with the DVI connection on your Nvidia card.

Will the Live CD take you all the way in if your monitor is connected to the VGA port on the Nvidia card instead of the DVI port? It would be nice to know that.

By the way, this will not work:
```

cd /media/c*/etc/X11 sudo mv xorg.conf xorg.conf.bak

```Those two commands need to be entered one at a time as follows:
```

**~~~ enter this one ~~~**
cd /media/c*/etc/X11

**~~~ then this one ~~~**
sudo mv xorg.conf xorg.conf.bak

```

---

### Post by preston collins on 2010-11-15
i'll try the vga on the nvidia card

 i did put them in separately i didnt get any errors just tryed to move it again and it said no such file or directory

---

### Post by robsoles on 2010-11-15
> **preston collins said:**
> so i gave that a shot then restarted it and it does boot up but it only goes as far as the main ubuntu 10.10 start up page then when i plug the onboard vga into the monitor i get the screen with the try it or install it
```
cd /media/c*/etc/X11
 sudo mv xorg.conf xorg.conf.bak
```


This makes it sound like Preston is still booting from the LiveCD again after applying the /etc/X11/xorg.conf move command, where Jocko's instructions seem to rely on rebooting after ejecting the LiveCD to see what the installed OS does without an existing xorg.conf file - often default settings are visible and usable to set preferred stuff...

The instructions given seem to rely on the user mounting their file system under /media (or actually it entirely looks like used GUI to mount example file system '/media/c*/.....') before executing them as well.

---

### Post by preston collins on 2010-11-15
It did the same thing with the vga on the nvidia card as it did dvi

if you want to take a break and we can pick this up another time it totally up to you but i think i have another hour left in me

---

### Post by Crusty Old Fart on 2010-11-15
Preston:
Here are some answers to one of your earlier posts:
> 
When i tryed the step in Post #24 ls /etc/X11 | grep xorg i didnt know   if it was suppose to be in 2 parts or one so i tryed separating it and   it said LS wasnt installed so i installed it they tryed  ls /etc/X11   again and it didnt give me the usual comand lines instead there was   nothing so i tryed typing grep xorg and nothing happened so i restarted   it. I also tryed it as a whole but i ddint know how to type the big old   bar that is separating the code nothing happened there.
Firstly, you were playing a dangerous game by doing this. If you send a command in a terminal window, it cannot be taken back. There is NO undo. So, if you send strange commands, there's no telling what could happen.

Secondly, the big old bar is called a **pipe**. It's probably Shift+\ (the uppercase character on your [s][COLOR=Black]backspace[/COLOR][/s](sorry) backslash key), which should be above the Enter key on your keyboard.
This command:
```

ls /etc/X11 | grep xorg

```is a single command. I will NEVER put two commands on one line in a code box that I send to you.

> 
i guess one question u might be able to answer is when i do the fresh   install will the dvi on the nvidia actually work for the video instead   of the onboard especially with out having the driver for it not   installed
I don't know. But, I'm wondering, if during the installation process, a good driver for it would be automatically recommended. That would be nice.

Let's finish testing the default nouveau driver that the Live CD loads, we already know it won't work for the DVI port, maybe it will work for the VGA port.

I'd like to ask a big favor: Could you PLEASE begin your sentences with capital letters and end them with periods. When you run everything together, with absolutely no punctuation, your writing is VERY difficult to interpret at times.

---

### Post by robsoles on 2010-11-15
Have you installed to a HDD/partition yet Preston?

I ask because those 'sudo mv' commands before are for booting off the LiveCD, mounting your file-system (as in installed on your HDD) and then moving the config file and then restarting from the HDD with the LiveCD removed.

---

### Post by preston collins on 2010-11-15
It did the same thing with the vga on the nvidia card as it did dvi.

> 
Secondly, the big old bar is called a **pipe**. Its probably Shift+\ (uppercase character on your backspace key, which should be above the Enter key on your keyboard.
This command:
 	Code:
 	ls /etc/X11 | grep xorg 


Yes i see that now, it makes more sence. I figured you wouldnt have more than one code on one line from your past posts that always had one code per line but im very new to ubuntu so i gave it a shot.

I was going to say should i try the codes again on post#24 but i realized i cant get back to the virtual shell without using the live cd via ubuntu terminal.

If you want to take a break and we can pick this up another time it totally up to you but i think i have another hour left in me.

---

### Post by preston collins on 2010-11-15
robsoles

I havent partition the HDD i used the whole disk, it was confusing so i went with the easy route and used the whole disk when i installed ubuntu. Every thing that has been ask of me to do is way over my head i really have no idea what is actually going on im trying to pick up on it as much as i can and when things are explained it does help but im still at  a loss for most things that have gone on

---

### Post by Crusty Old Fart on 2010-11-15
To Preston:
> 
It did the same thing with the vga on the nvidia card as it did dvi.


Okay. If that was happening when booting from the Live CD, then we know the default nouveau driver won't work on your card. Regardless of what port is being used. Bummer!

> 
If you want to take a break and we can pick this up another time it  totally up to you but i think i have another hour left in me. 	

Yup, my friend, it's probably not a bad idea to call it a night. I'm pretty shagged out. Plus, I really think that it would help me to study what jocko told us, and some of what you wrote right before jocko showed up. You had written a reply to things that were confusing me that I haven't taken the time to internalize. I also think it would help me to go back and review a lot of what we've done, so that I can put together a coherent plan regarding what we should try next.

Sleep well,

Crusty

---

### Post by Crusty Old Fart on 2010-11-15
To robsoles:

> 
This makes it sound like Preston is still booting from the LiveCD again  after applying the /etc/X11/xorg.conf move command, where Jocko's  instructions seem to rely on rebooting after ejecting the LiveCD to see  what the installed OS does without an existing xorg.conf file - often  default settings are visible and usable to set preferred stuff...
Well, we already knew that Preston's installed OS couldn't get Gnome to come up without an xorg.file. That's why I had him generate one with the instructions in Post #24, which we didn't get around to doing until Post #45 or so. The part of jocko's instructions that seemed especially important to me was to determine whether or not the nouveau driver on the Live CD would work. If it did, then we'd be in much better shape, and we hadn't tested that at the time he recommended it. But, admittedly, I need to go back and study jocko's instructions again when I'm not so tired.

> 
The instructions given seem to rely on the user mounting their file  system under /media (or actually it entirely looks like used GUI to  mount example file system '/media/c*/.....') before executing them as  well.
I'm a little confused by what you wrote. However, we used the Live CD in tryout mode to access the HDD that contained the installed OS because it wouldn't boot far enough on its own. It was the only way I knew of to have Preston get to the system-generated xorg.conf. And, yes, I did have him mount the HDD containing the installed OS from the Live CD GUI. And yes, I instructed him to manipulate the xorg.conf files by accessing them the same way. So, I reckon I stand guilty as charged on all those counts. However, after we finished mucking around with xorg.conf, we _did_ smoke test it by trying to boot from the installed OS (Ref.: Posts #47 through 72).

It wouldn't surprise me in the least if I haven't interpreted your comments correctly. I'm tired. I'll read them again after I get some sleep. Mostly, I wanted you to know that we're not ignoring the help you're offering, by at least giving you the courtesy of a reply.

Thank you, and good night,

Crusty

---

### Post by Crusty Old Fart on 2010-11-15
To jocko:
> 
Dual display can only be accomplished by connecting ONE graphics card to  two monitors, so there is absolutely no point in trying to connect both  graphics cards. If the nvidia card only have one output you'll never be  able to use dual screen.
I ignored this when I first read it because we aren't trying to set up a dual head system for Preston.

However, I thought you might like to know that while what you wrote is true for systems running RandR, it is not entirely true for every configuration. RandR is easily disabled by the presence of a good xorg.conf file in /etc/X11.

I am running the following setup:

[LIST]
[*]Dual HP w2207h monitors
[*]Dual ATI Radeon 9250 graphics adapters. Each monitor is driven by its own separate adapter card.
[*]Ubuntu's default "radeon" driver running both graphics adapters.
[*]Xinerama extension enabled in xorg.conf to extend my desktop across both monitors.
[*]Ubuntu Lucid Lynx 10.04.1
[*]If you'd like to know how I did it, you can read the following tutorial:
[How to: Extend desktop across dual monitors]("http://ubuntuforums.org/showthread.php?t=1611704")
[/LIST]

---

### Post by robsoles on 2010-11-15
Sorry I didn't read the whole thread before, it looked like you were asking Preston to change something on a mounted file-system from a LiveCD and try rebooting.It further looked like Preston was leaving the LiveCD in the tray for the reboot. As far as I could tell booting off the LiveCD at that point makes the previous step(s) pointless.

Had I read the whole thread I'd have known either to keep my fingers to myself or to make it much clearer that fiddling with files on the HDD is pointless if you don't boot from it. I hope rest serves you guys well, it's about my bedtime now too :)

---

### Post by Crusty Old Fart on 2010-11-15
This post goes to Preston, jocko, robsoles, and any major-geek out there who is an expert at installing Nvidia drivers.

I think I may have finally figured out what the whole problem is.

In very short terms: we've never had a working driver for Preston's Nvidia card.

Here's more detail:

We've never had a successful boot into Gnome from Preston's Nvidia card because none of the drivers we've tried: "nouveau", "nv", and _possibly_ "nvidia" have worked. But, honestly, I'm not really sure that we ever had the nvidia driver installed correctly _and_ actually running. In fact, I have enough doubt about it to believe that it should be the first driver we try to install. Preston's current installation has received so many body blows that I don't believe it serves us well as a test platform anymore. So, at this point, I think we need to connect a monitor to the DVI port of Preston's Nvidia card, and do a fresh installation. Unless the "nvidia" driver gets automatically loaded and configured to drive Preston's card during the installation process, I expect that we still won't boot to Gnome and will be served a virtual terminal. If we get that far, I think we should try to install the "nvidia" driver manually using a series of "apt-get" commands followed with a "dpkg --configure -a", an "update-initramfs -u" as well as an "update-grub" for good measure, and finally reboot. If we still can't get into Gnome, I think we'll need to generate a new xorg.conf file and make any modifications to it that we need.

Before I instruct Preston on how to do all that, I'd like some input regarding the following so that I can gain a more solid foundation regarding how to do what I believe needs to be done and can develop a coherent plan that has a high potential for success.

[LIST]
[*]Which packages do we need to install for the "nvidia" driver using "apt-get"?
[*]Will RandR work when kernel mode-setting (KMS) won't support the driver? Presently, KMS support is limited to the intel, ati, and the nouveau driver, which has never worked for us. I'm assuming RandR will still work without KMS support for the driver. But, I'd like to know for sure from someone who knows.
[*]I've found a Linux driver for Preston's Nvidia card on Nvidia's website. It's a very new version dated four days ago: 11-11-10. I'd like a cursory explanation of how to install it if we need it. I don't need newbie level detail. So, for the sake of brevity, assume that I am a master-geek.
[*]Are there any special commands or other procedures that we'll need to get a proprietary driver running, like modules we may need to add to the kernel with modprobe or such?
[*]Anything else you can think of that we need to know and haven't thought to ask? Like maybe the name of a recognized expert on installing Nvidia drivers who is a member of Ubuntu Forums and wouldn't mind us picking his brains?
[*]Lastly, if you think I'm totally off base about any of this, I'd like to know where I've lost the path. This is not a solicitation for uninformed criticism. I won't be overjoyed to read snark from people who haven't read most of this thread. Trust me, I'll know if they haven't.
[/LIST]
Thanks for any help you can give us.

Crusty

_Hardware info:_
Preston's Nvidia card is a Geforce 9400gt 1G pci video card
Preston's computer is a 32 bit system
More detail regarding hardware is in Posts #21 and #23

---

### Post by jocko on 2010-11-15
> **Crusty Old Fart said:**
> To jocko:
I ignored this when I first read it because we aren't trying to set up a dual head system for Preston.

However, I thought you might like to know that while what you wrote is true for systems running RandR, it is not entirely true for every configuration. RandR is easily disabled by the presence of a good xorg.conf file in /etc/X11._..._
I realized that after I wrote the post, and it may even work on Preston's system, as long as he stays with the open source drivers (nouveau and whatever driver his onboard card uses) and does not try to install nvidia's proprietary driver. The proprietary driver will definitely break the output from the onboard card...

---

### Post by robsoles on 2010-11-15
I read as much of the thread as I could stand last night. It is weird that Crusty Old Fart instructed Preston to mount a file-system using places as if a boot from the LiveCD worked to get to the GUI/desktop and then next boot from LiveCD fails according to what I make out in Preston's most recent posts.

I probably didn't read it properly, I am going to keep my fingers to myself unless directly challenged for more input or I become a lot more sure of anything than I am right now.

---

### Post by jocko on 2010-11-15
Preston: I'm still a bit unsure about a few things...

If you boot with a live cd with only the nvidia card connected to a monitor, exactly what happens? Which "purple ubuntu 10.10 screen" are you talking about? The boot splash? Does it just stay with the boot splash indefinitely? Does it drop to a shell (and give any error messages)? Does the screen just go black? Or do you actually see the wallpaper of the desktop, but not getting any panels or desktop icons?

What happens if you boot a live cd with only the onboard card connected to a monitor (but the nvidia card still in the pci slot)?
If that works, what happens if you boot a live cd with both cards connected to a monitor?
Does it boot all the way to gnome but just never getting any output from the nvidia card?

---

### Post by preston collins on 2010-11-15
robsoles

> **Re: gnome boot from terminal**             
                                                                I read as much  of the thread as I could stand last night. It is weird that Crusty Old  Fart instructed Preston to mount a file-system using places as if a boot  from the LiveCD worked to get to the GUI/desktop and then next boot  from LiveCD fails according to what I make out in Preston's most recent  posts.

I probably didn't read it properly, I am going to keep my fingers to  myself unless directly challenged for more input or I become a lot more  sure of anything than I am right now.
The live Cd works properly when i only use the onboard vga. if im not using the cd to boot from and when i only have the nvidias either vga or dvi plugged in a screen comes up as if it was about to show the purple ubuntu 10.10 splash screen but there is only the purple screen and no txt on it.

without booting from the cd and After installing the nvidias driver that was asked of me from ubuntu then thats when gnome doesnt boot up i get sent to the virtual shell, but with the attempts from crusty im not being sent to the tty1 screen anymore i get sent to the purple splash screen with out any "ubuntu 10.10" on it and its as if the screen inst centred cause i get at 3 inch black bar on the right side of my screen.

---

### Post by preston collins on 2010-11-15
jocko

**Re: gnome boot from terminal**             
                                                                Preston: I'm still a bit unsure about a few things...

>  If you boot with a live cd with only the nvidia card connected to a  monitor, exactly what happens? Which "purple ubuntu 10.10 screen" are  you talking about? The boot splash? Does it just stay with the boot  splash indefinitely? Does it drop to a shell (and give any error  messages)? Does the screen just go black? Or do you actually see the  wallpaper of the desktop, but not getting any panels or desktop icons?

When i boot from the cd and have the nvidias either dvi or vga plugged in i get the boot splash page which then it stops loading. when it stops loading i change it over to the onboards vga and i get the try it screen then when i click the try it and switch back over to the nvidias dvi the splash screen is gone and it gives me a black screen with abit of txt but its not the tty1 screen its like its showing what its has gone though when loading the cd

> But

What happens if you boot a live cd with only the onboard card connected  to a monitor (but the nvidia card still in the pci slot)?
If that works, what happens if you boot a live cd with both cards connected to a monitor?
Does it boot all the way to gnome but just never getting any output from the nvidia card?


gnome ubuntu will boot up with the card in the pci slot and haveing the onboards vga and the cards dvi plugged in but as soon as i install the driver for the card then it sends me to the tty1 virtual shell screen.
the only way i can see the ubuntus destop is with the onboards vga.

hope that made sence

---

### Post by jocko on 2010-11-15
> **preston collins said:**
> gnome ubuntu will boot up with the card in the pci slot and haveing the onboards vga and the cards dvi plugged in but as soon as i install the driver for the card then it sends me to the tty1 virtual shell screen.
the only way i can see the ubuntus destop is with the onboards vga.

hope that made sence
I see... But is there any display at all from the nvidia card when you see the desktop from the onboard card?

---

### Post by preston collins on 2010-11-15
> I see... But is there any display at all from the nvidia card when you see the desktop from the onboard card?

nothing of use to me its a black screen with some txt i think the last line is something like checking battery status or something like that

---

### Post by Crusty Old Fart on 2010-11-15
Howdy all:

I'm in the process of making a list of all the things that I think we know about this problem. Shortly after I started, I realized that I was about to fall into the dangerous trap of making an assumption that could have added to the confusion instead of reducing it.

In order to make the list as accurate as I can from the start, I need Preston to answer the following three questions:

[LIST=1]
[*]Have you always used the same computer to make all of your posts to this thread?
[*]Have you ever made a post to this thread using an operating system other than Ubuntu?
[*]Do you have more than one computer that you can use to post to this thread?
[/LIST]
These may seem like silly questions. But, at least for me, knowing the answers to them will help a lot.

---

### Post by preston collins on 2010-11-15
> **Crusty Old Fart said:**
> Howdy all:

I'm in the process of making a list of all the things that I think we know about this problem. Shortly after I started, I realized that I was about to fall into the dangerous trap of making an assumption that could have added to the confusion instead of reducing it.

In order to make the list as accurate as I can from the start, I need Preston to answer the following three questions:

[LIST=1]
[*]Have you always used the same computer to make all of your posts to this thread?
[*]Have you ever made a post to this thread using an operating system other than Ubuntu?
[*]Do you have more than one computer that you can use to post to this thread?
[/LIST]
These may seem like silly questions. But, at least for me, knowing the answers to them will help a lot.

1. yes i have always used this computer to post my threads
2. i have always used ubuntu while posting threads
3. i have another hard drive with xp on it but i would have to use this computer

---

### Post by Crusty Old Fart on 2010-11-15
> **robsoles said:**
> I read as much of the thread as I could stand last night. It is weird that Crusty Old Fart instructed Preston to mount a file-system using places as if a boot from the LiveCD worked to get to the GUI/desktop and then next boot from LiveCD fails according to what I make out in Preston's most recent posts.

I probably didn't read it properly, I am going to keep my fingers to myself unless directly challenged for more input or I become a lot more sure of anything than I am right now.

I'm sorry, robsoles, but when I read that I couldn't suppress my laughter. All I can say is welcome to the club. I can't think of anything I've ever experienced in my entire life that has been more confusing than this thread. For a ton of reasons, some of which have certainly been my fault.

It sure has been one helluva bean maker though, eh?

---

### Post by Crusty Old Fart on 2010-11-15
> **preston collins said:**
> 1. yes i have always used this computer to post my threads
2. i have always used ubuntu while posting threads
3. i have another hard drive with xp on it but i would have to use this computer
Thank you SOOOOOO much!

---

### Post by Crusty Old Fart on 2010-11-15
[SIZE=3][COLOR=Green][B]~~~ Preston's List ~~~
[/B][/COLOR][/SIZE]
Rather than having to continually re-read this thread to figure out what we've learned. I thought it would be a good idea to put some of it in one post that we can revisit to check our sanity.
Please feel free to suggest any additions or corrections to this list.  The more accurate we can make it, the better it will serve all of us.

Most recently updated on 11-18-10.
[LIST]
[*]**Preston's operating system:** Ubuntu Maverick Meerkat 10.10
[/LIST]

[LIST]
[*]**Preston's posting situation and the dynamic nature of his hardware configuration:**
[/LIST]
[INDENT]
[LIST=1]
[*]Preston makes all of his posts from the same computer using Ubuntu. This is important for the following reasons:
[/LIST]
[INDENT]
[LIST=a]
[*]All of Preston's posts have been made when he has either been  running Ubuntu in tryout mode from the Live CD, or from his installed  OS.
[*]We have never been able to run Gnome from Preston's Nvidia card,  either from his installed OS, or his Live CD. So, every one of Preston's  posts have been made when his monitor was connected to his integrated  (on-board) graphics card.
[*]Anytime we have instructed Preston to test something that involves  having his monitor connected to his Nvidia card, in order for him to report back  to us, he has had to shut down his computer, connect the monitor to the  integrated card, and reboot in order to post. Additionally, depending on the state of his installed OS at the time, he may have resorted to booting from the Live CD and running it in tryout mode. This has added a lot of  confusion and frustration to the thread, because _Preston's situation  does not allow him to keep his hardware configuration static_. We're  trying to configure his system to run the Nvidia card. But he can't tell  us what's happening unless he changes his configuration to run from the  integrated card. If he's posting to us, and we tell him to do  something, like issue commands to poll the system for certain parameter  values or log files, we need to understand that his monitor is connected  to his on-board card at that time and the data he posts may reflect _that_ hardware configuration and _not_ the one that has  his Nvidia card driving his monitor.
[/LIST]
[/INDENT][/INDENT]
[LIST]
[*]**Driver test results:**
[/LIST]
[INDENT][INDENT][LEFT]_Nouveau driver_: Failed to drive Nvidia board on either the VGA port or the DVI port when booting from Maverick Meerkat Live CD. Testing performed without anything connected to the integrated (on-board) graphics adapter. (Ref.: various posts - [#82]("http://ubuntuforums.org/showpost.php?p=10117705&postcount=82") through [#95]("http://ubuntuforums.org/showpost.php?p=10117867&postcount=95"))
[/LEFT]
[/INDENT][/INDENT]
[LIST]
[*]**Preston's hardware:**
[/LIST]
[INDENT][INDENT]  _More detail regarding hardware in this thread_:[INDENT][Short hardware list (output from lshw -short) - link to Post #21]("http://ubuntuforums.org/showpost.php?p=10087312&postcount=21")
[PCI tree (output from (lspci -tvv) - link to Post #21]("http://ubuntuforums.org/showpost.php?p=10087312&postcount=21")
[/INDENT]_BIOS_: AMIBIOS SIMPLE SETUP UTILITY - VERSION 1.21.12 Copyright (c) 2000[INDENT][Picture of top level BIOS menu - link to Post #176]("http://ubuntuforums.org/showpost.php?p=10126371&postcount=176")
[Possible (version?) BIOS manual - link to Post #199]("http://ubuntuforums.org/showpost.php?p=10129900&postcount=199")
[Possible (version?) BIOS manual - link to ECS]("http://www.ecs.com.tw/ECSWebSite/Downloads/Downloads_Driver_Detail.aspx?MenuID=61&LanID=0&detailid=261")
[/INDENT]_Computer_: 32 bit system

_Motherboard_: ECS K7S7AG[INDENT][Possible (version?) Motherboard specification - link to ECS]("http://www.ecs.com.tw/ECSWebSite/Downloads/Downloads_Driver_Detail.aspx?MenuID=61&LanID=0&detailid=261")[/INDENT]_Nvidia card_: Geforce 9400gt 1G pci video card[INDENT][Nvidia Binary Driver Howto at help.ubuntu.com/community]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")
[/INDENT]_Onboard Video_: Xabre 200 AGP8X 256-bit GPU[/INDENT][/INDENT]

---

### Post by preston collins on 2010-11-15
looks good so far

---

### Post by Crusty Old Fart on 2010-11-15
I owe you an apology, Preston.

I became really frustrated recently at you changing your hardware connections around while I was trying to modify the code for your system for a particular configuration that involved having your Nvidia card driving your monitor.

At the time, I didn't fully realize that your situation **would not allow** your connection configuration to remain static and still be able to post to this thread.

Fortunately, for me, you are a very good natured soul, and took my frustration in stride.

So, I apologize for coming at you like the Crusty Old Fart that I am.

Sorry,

Crusty

---

### Post by preston collins on 2010-11-15
no worries i would be getting abit frustrated myself, im willing to learn and having someone help me get this card working makes it easier for me

i appreciate it thanks

---

### Post by cheezewiz25 on 2010-11-15
I've been interested in this thread for awhile as well.  I too have an Nvidia card and recently upgraded to 10.10.  However, upon the final reboot, I get error messages on a few things and then the TTY1 login screen.  I've tried some of the suggestions such as #24 to no avail.  I have not tried a live cd yet and that will be my next step after I wait for the download.
I'm getting a terminal type login not graphical

---

### Post by preston collins on 2010-11-15
if you haveing the same problem as i am its the driver that ubuntu is asking you to install that is messing everything up

---

### Post by preston collins on 2010-11-16
So this is exciting just thought i would try to boot up my computer of off the OS and the nvidia driver isnt conflicting with anything but i still cant use the dvi on the nvidia card. The onboard vga is the only port which actually turns my monitor on so the nvidia card isnt working just quite yet

---

### Post by Crusty Old Fart on 2010-11-16
> **preston collins said:**
> So this is exciting just thought i would try to boot up my computer of off the OS and the nvidia driver isnt conflicting with anything but i still cant use the dvi on the nvidia card. The onboard vga is the only port which actually turns my monitor on so the nvidia card isnt working just quite yet
Preston just gave us irrefutable proof that Jesus is a geek.

---

### Post by Crusty Old Fart on 2010-11-16
Preston:

While you're still running from your OS, do this:

[LIST]
[*]At the upper left corner of your desktop, click on: **Applications**
[*]Click on: **Ubuntu Software Center** from the pull down menu.
[*]In the upper right corner of the Ubuntu Software Center window, type nvidia to the right of the magnifying glass.
[*]Look for the following driver in the list: **NVidia binary X.Org driver ('version 185' driver)**
[*]Tell me if there is a green circle with a check mark in it on its icon.
[/LIST]

---

### Post by preston collins on 2010-11-16
> **Crusty Old Fart said:**
> Preston:

While you're still running from your OS, do this:

[LIST]
[*]At the upper left corner of your desktop, click on: **Applications**
[*]Click on: **Ubuntu Software Center** from the pull down menu.
[*]In the upper right corner of the Ubuntu Software Center window, type nvidia to the right of the magnifying glass.
[*]Look for the following driver in the list: **NVidia binary X.Org driver ('version 185' driver)**
[*]Tell me if there is a green circle with a check mark in it on its icon.
[/LIST]



No the version 185 dosnt have a nice green circle in it.

The only one that has a green circle in it is additional drivers (jockey-gtk).

---

### Post by Crusty Old Fart on 2010-11-16
I thought so.

It never installed.

Install it and allow it to install any other packages it may tell you it requires.

After they've been installed, do the following:

[LIST]
[*]Shutdown your computer.
[*]Disconnect your monitor from your on-board card.
[*]Connect your monitor to the DVI port on your Nvidia card.
[*]Reboot and tell me what happens.
[/LIST]

---

### Post by preston collins on 2010-11-16
So i installed it it said it was installed it didnt ask me to do anything so i restarted my computer and had only the dvi plugged in but nothing happened i plugged the onboards vga back in and my desktop was up and running but the screen ratio is abit out of size. so i went to adjust it and i got a window saying "it appears that your graphincs driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?" 

So i said yes,

 then another window saying you do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server. 

so i said ok,

 then a NVIDIA X Server Settings application started up but it didnt give me much to change the settings

---

### Post by Crusty Old Fart on 2010-11-16
> **preston collins said:**
> So i installed it it said it was installed it didnt ask me to do anything so i restarted my computer and had only the dvi plugged in but nothing happened i plugged the onboards vga back in and my desktop was up and running but the screen ratio is abit out of size. so i went to adjust it and i got a window saying "it appears that your graphincs driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?" 

So i said yes,

 then another window saying you do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server. 

so i said ok,

 then a NVIDIA X Server Settings application started up but it didnt give me much to change the settings
Well...I'm not surprised to read that the system ultimately didn't let you get away with what you were trying to do to it.

It looks like you were trying to use the Nvidia driver configuration tools to configure the driver being used by your onboard card which was probably the frame buffer driver (fbdev).

One nice thing is that this is new stuff that we haven't seen before, and that means we've made some progress.

So, I have three questions:

[LIST=1]
[*]Have you been hot-swapping your monitor between your graphics adapters, meaning moving your monitor's data cable from one adapter to the other while your operating system was up and running?
[*]When you boot with your monitor connected to the DVI port on your Nvidia card, are you at least able to get to a tty1 terminal.
[*]Is your Grub boot menu still not showing up, you know? the menu that lets you select which kernel you want to boot from, like the normal kernel or the recovery kernel.
[/LIST]
Hope to read from you soon, we're getting closer to fixing this.

---

### Post by jocko on 2010-11-16
> **preston collins said:**
> then another window saying you do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server. 

so i said ok,

 then a NVIDIA X Server Settings application started up but it didnt give me much to change the settings
Did you run nvidia-xconfig and reboot?
The command to get a completely new /etc/X11/xorg.conf is:
```
sudo nvidia-xconfig --force-generate
```Then reboot to see if it works.

And to get back to your current state if things get worse:
```
sudo rm /etc/X11/xorg.conf
```

---

### Post by Crusty Old Fart on 2010-11-16
jocko:

Will that work if his monitor is not connected to his Nvidia card and he's running from his on-board card when he issues that command?

I've been thinking it would be safer to see if we could get him into a recovery kernel after booting with the monitor connected to the Nvidia DVI port.

What say you?

---

### Post by robsoles on 2010-11-16
Hey Crusty Old Fart,

If Preston can plug a monitor into every output he hopes to have available 'at the end of the day' for the next couple of rounds (particularly should he run the nvidia-xconfig tool as shown by Jocko) it will be better.

It should be less than harmless to have both monitors plugged in on the reboot from running the tool.

EDIT: If X starts on both monitors it is easy enough to set them to 'mirror' and unplug the one we don't want later.

---

### Post by jocko on 2010-11-16
> **Crusty Old Fart said:**
> jocko:

Will that work if his monitor is not connected to his Nvidia card and he's running from his on-board card when he issues that command?

I've been thinking it would be safer to see if we could get him into a recovery kernel after booting with the monitor connected to the Nvidia DVI port.

What say you?
As you have now got him to install the nvidia driver, why not try to use it and see if it works? Of course he should have a monitor connected to his nvidia card when he reboots (any port is fine)...

As it is now his computer is in a state where the installed nvidia driver have replaced some of the open source components needed for his onboard graphics card with nvidia's proprietary files, probably messing up his ability to set resolution and use any 2d/3d acceleration that his onboard gpu supports...

And if xorg fails to start with the nvidia driver installed and **in use** (which it will only be after running the nvidia-xconfig command), it would be really helpful to see a copy of Preston's /var/log/Xorg.0.log (taken directly after a failed attempt to start xorg)... It usually contains some very helpful information which will tell us exactly why it fails, which is the only way to know how fix it...

---

### Post by Crusty Old Fart on 2010-11-16
> **robsoles said:**
> Hey Crusty Old Fart,

If Preston can plug a monitor into every output he hopes to have available 'at the end of the day' for the next couple of rounds (particularly should he run the nvidia-xconfig tool as shown by Jocko) it will be better.

It should be less than harmless to have both monitors plugged in on the reboot from running the tool.
Alrighty then...

I think I'll pass the baton to you and jocko for a while and watch the fireworks from the hilltop.

Good luck guys...Jesus is with us now...don't cuss too much.

---

### Post by robsoles on 2010-11-16
Hey Preston,

Please execute Jocko's instructions and reboot with the monitor plugged into the DVI port or with a monitor on the DVI port on NVidia card and another monitor on the VGA port on inbuilt video - should be cool to have both but certainly skip it [COLOR=Blue]if it[/COLOR] doesn't seem cool.

---

### Post by Crusty Old Fart on 2010-11-16
> 
As you have now got him to install the nvidia driver, why not try to use  it and see if it works? Of course he should have a monitor connected to  his nvidia card when he reboots (any port is fine)...

As it is now his computer is in a state where the installed nvidia  driver have replaced some of the open source components needed for his  onboard graphics card with nvidia's proprietary files, probably messing  up his ability to set resolution and use any 2d/3d acceleration that his  onboard gpu supports...

And if xorg fails to start with the nvidia driver installed and **in use**  (which it will only be after running the nvidia-xconfig command), it  would be really helpful to see a copy of Preston's /var/log/Xorg.0.log  (taken directly after a failed attempt to start xorg)... It usually  contains some very helpful information which will tell us exactly why it  fails, which is the only way to fix it...

Noted. Thank you.

---

### Post by jocko on 2010-11-16
> **Crusty Old Fart said:**
> Jesus is with us now...
I know you mean well, but could you please keep your religion out of it? As an atheist I find it to be quite offensive...

---

### Post by robsoles on 2010-11-16
@jocko: If atheism is working out for you then that little bit of Crusty's larger post was nothing, certainly meaningless to me.

If you turn the page (10 posts per page) in a support thread without posting something really helpful a cool thing to do is to bring the most helpful thing in a previous post forward to the new page.

> **jocko said:**
> Did you run nvidia-xconfig and reboot?
The command to get a completely new /etc/X11/xorg.conf is:
```
sudo nvidia-xconfig --force-generate
```Then reboot to see if it works.

And to get back to [s]your current[/s] [COLOR=Blue]the default[COLOR=Black] state[/COLOR][/COLOR] if things get worse:
```
sudo rm /etc/X11/xorg.conf
```
> **robsoles said:**
> [COLOR=Blue]Hey Preston,

Please execute Jocko's instructions and reboot with the monitor plugged  into the DVI port or with a monitor on the DVI port on NVidia card and  another monitor on the VGA port on inbuilt video - should be cool to  have both but certainly skip it [/COLOR] [COLOR=Blue]if it doesn't seem cool.[/COLOR]

---

### Post by Crusty Old Fart on 2010-11-16
> **jocko said:**
> I know you mean well, but could you please keep your religion out of it? As an atheist I find it to be quite offensive...
Well then...You'd probably really like my favorite T-shirt.

It has two words silk screened on it:

Lion Chow

---

### Post by Crusty Old Fart on 2010-11-16
To cheezewiz25:
> **cheezewiz25 said:**
> I've been interested in this thread for awhile as well.  I too have an Nvidia card and recently upgraded to 10.10.  However, upon the final reboot, I get error messages on a few things and then the TTY1 login screen.  I've tried some of the suggestions such as #24 to no avail.  I have not tried a live cd yet and that will be my next step after I wait for the download.
I'm getting a terminal type login not graphical
Stay tuned. I think we're getting very close to cracking this nut -- at least for Preston.

Check out the link in the post directly below. Finding it was a real Jesus moment for me.

---

### Post by Crusty Old Fart on 2010-11-16
Ohhh...Baby, Baby, Baby!!!

Looky what I found:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Hot Damn!

---

### Post by indyeah on 2010-11-16
i had the exact same problem like preston using my nvidia fx 5500 graphics card.i took the easy way out,i removed the graphics card plugged my monitor in my native vga slot and reinstalled 10.10 and hurray its working like a charm :)

---

### Post by jocko on 2010-11-16
Preston: Did you try [my suggestion]("http://ubuntuforums.org/showpost.php?p=10122073&postcount=124")?

---

### Post by preston collins on 2010-11-16
> **jocko said:**
> Preston: Did you try [my suggestion]("http://ubuntuforums.org/showpost.php?p=10122073&postcount=124")?


I did and im back to where i started, i tryed to put in the second code but its not allowing me to do that from the live cd.

No worries just put in the second code on the tty1 screen and im back on the gnome screen

---

### Post by preston collins on 2010-11-16
> **Crusty Old Fart said:**
> Well...I'm not surprised to read that the system ultimately didn't let you get away with what you were trying to do to it.

It looks like you were trying to use the Nvidia driver configuration tools to configure the driver being used by your onboard card which was probably the frame buffer driver (fbdev).

One nice thing is that this is new stuff that we haven't seen before, and that means we've made some progress.

So, I have three questions:

[LIST=1]
[*]Have you been hot-swapping your monitor between your graphics adapters, meaning moving your monitor's data cable from one adapter to the other while your operating system was up and running?
[*]When you boot with your monitor connected to the DVI port on your Nvidia card, are you at least able to get to a tty1 terminal.
[*]Is your Grub boot menu still not showing up, you know? the menu that let's you select which kernel you want to boot from, like the normal kernel or the recovery kernel.
[/LIST]
Hope to read from you soon, we're getting closer to fixing this.


1. Yes i have been i know its not good but i have been doing it.
2. No i have never seen the tty1 screen when i have had the dvi plugged in.
3. No my grub is still not showing up.


yea i hope this gets worked out, i guess its been kinda interesting so far deff a learning experiance

---

### Post by Crusty Old Fart on 2010-11-16
Okay, so grub is kind of toasted.

I think Jocko's suggestion was intended to be done while you were running your OS, not your CD. But I know your display/resolution got a little fried after we installed the new driver.

What do you think about doing a fresh install from scratch tonight, and then getting the driver loaded, configured, and hopefully running? Three to five hours depending on how it goes.

---

### Post by preston collins on 2010-11-16
> **Crusty Old Fart said:**
> Okay, so grub is kind of toasted.

What do you think about doing a fresh install from scratch tonight, and then getting the driver loaded, configured, and hopefully running? Three to five hours depending on how it goes.

yea sounds good should i get goen with the fresh install

---

### Post by Crusty Old Fart on 2010-11-16
Yes, but first, let's agree on a hardware configuration before you install.

I suggest the following:

[LIST]
[*]Monitor connected to the VGA port only on the Nvidia card (we may have a better chance of getting this going and then trying the DVI after we can boot into Gnome from your VGA port.)
[*]Nothing connected to your on-board card.
[/LIST]
What do you think about that?

---

### Post by preston collins on 2010-11-16
Yup sounds great

---

### Post by Crusty Old Fart on 2010-11-16
Okay...Listen up...

After you get the OS installed:

[LIST]
[*]The Nvidia driver won't be loaded. So the card still won't boot into Gnome.
[*]Hopefully we'll get Grub back.
[*]If we don't get taken to a tty1 virtual shell, we may be able to use the recovery kernel from grub to drop into a root shell.
[*]What we're hoping for is that you'll be able to get the system to serve up a tty1 shell after the install and then, I'll give you the commands you need to install and configure the driver.
[*]If we get this far, the next reboot should bring up [s]Grub.[/s](sorry) Gnome!
[/LIST]
Go for it!

---

### Post by preston collins on 2010-11-16
[LIST]
[*]> Monitor connected to the VGA port only on the Nvidia card (we  may have a better chance of getting this going and then trying the DVI  after we can boot into Gnome from your VGA port.)
[/LIST]
do you want me to have the nvidias vga plugged in when i do the reinstall cause i wont be able to see anything thats going on.


[LIST]
[*]> Nothing connected to your on-board card.
[/LIST]


> **Crusty Old Fart said:**
> Okay...Listen up...

After you get the OS installed:

[LIST]
[*]The Nvidia driver won't be loaded. So the card still won't boot into Gnome.
[*]Hopefully we'll get Grub back.
[*]If we don't get taken to a tty1 virtual shell, we may be able to use the recovery kernel from grub to drop into a root shell.
[*]What we're hoping for is that you'll be able to get the system to serve up a tty1 shell after the install and then, I'll give you the commands you need to install and configure the driver.
[*]If we get this far, the next reboot should bring up [s]Grub.[/s](sorry) Gnome!
[/LIST]
Go for it!

The first point makes sence and hopfully the second point works.

will the virtual shell pop up before grub gets a chance to load

gnome doesnt load after i have installed the diver for the nvidias card so once i install the driver then i get sent to the tty1 screen. 

Is there any other way of getten grub to work cause i can get back to the tty1 screen when i type 

```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```

---

### Post by Crusty Old Fart on 2010-11-16
Sorry I took so long to get back to you. I've been on the phone helping my cousin with a hard drive crash.

From everything that you wrote in your last post, it looks like we should make some big changes in the whole plan. But before we do that, maybe we can get your Nvidia driver working and worry about Grub later.

Did you learn about the following command from the Jesus link I found?
> 
Is there any other way of getten grub to work cause i can get back to the tty1 screen when i type 
```

     sudo apt-get --purge remove xserver-xorg-video-nouveau 

```


---

### Post by preston collins on 2010-11-16
> **Crusty Old Fart said:**
> Sorry I took so long to get back to you. I've been on the phone helping my cousin with a hard drive crash.

From everything that you wrote in your last post, it looks like we should make some big changes in the whole plan. But before we do that, maybe we can get your Nvidia driver working and worry about Grub later.

Did you learn about the following command from the Jesus link I found?


Yea i took a peek at the site, looks like its setting me up to install the driver that is messing everything up

---

### Post by Crusty Old Fart on 2010-11-16
You know, we've punched your OS in the gut so many times over the last week or so that we really should just do a fresh install without trying to figure out why we're having so many problems with everything else we're trying to do, we'll have a much better chance of success getting the good driver going and we'll get Grub back as well.

So...

How about agreeing in the following hardware configuration for the installation process:

[LIST]
[*]**Nothing** connected to your Nvidia card.
[*]Monitor connected to your on-board card.
[/LIST]
Okay?

---

### Post by preston collins on 2010-11-16
sounds good

---

### Post by Crusty Old Fart on 2010-11-16
Okay...go for it.

Then after the installation is finished, Reboot and come back to this thread while your computer is running the newly installed OS, [B]NOT while your running the Live CD.


[/B]

---

### Post by preston collins on 2010-11-16
So fresh install ad grub works im happy so far

---

### Post by Crusty Old Fart on 2010-11-17
Alrighty then...Here we go...

Now we're going to try to get your Nvidia card working.

Write down as many of the following steps on a piece of paper as you think you need to, **especially the commands.** 

Perform the following steps:

[LIST]
[*]Shutdown (not restart) your computer.
[*]Disconnect your monitor from the on-board card. We don't want **anything** connected to the on-board card now.
[*]Connect your monitor to the VGA port on the Nvidia card only. Don't plug anything into its DVI port.
[*]Reboot.
[*]Hopefully, you'll see Grub come up. It will want to boot from the default kernel. Just let it do it.
[*]Next, you should be taken to a tty1 virtual shell. Go ahead and log in and then issue the following commands (write these down carefully, exactly as they appear in the code boxes):
[/LIST]
[INDENT][INDENT]The following command removes the nouveau driver that doesn't work for your card:
```

sudo apt-get --purge remove xserver-xorg-video-nouveau

```This next command installs the Nvidia driver that we need:
```

sudo apt-get install nvidia-glx-185

```And this command command configures X to use the new driver:
```

sudo nvidia-xconfig --force-generate

```Finally, reboot using the following command:
```

sudo reboot now

```[/INDENT][/INDENT]Hopefully, this will have done it and your Nvidia card will boot into gnome.

Please let me know how it went.

---

### Post by preston collins on 2010-11-17
ok so i plugged in my monitor into the nvidias vga after i shut it off then rebooted it and all i got was the ubuntu 10.10 splash screen and that was it.

Do you want me to install the crappy driver then do the restart casue that will most definatly send me to the tty1 screen but i probably wont be able to see it with the nvidias vga

---

### Post by Crusty Old Fart on 2010-11-17
No...don't uninstall or install anything yet.

Tell me how you got here, as in how you're running right now:

[LIST]
[*]Are you using the Live CD with your monitor connected to your on-board card?
[*]Or are you using the new OS with your monitor connected to your on-board card?
[/LIST]

---

### Post by preston collins on 2010-11-17
i havent done any of the codes, i am currently running the os off of my onboard

---

### Post by Crusty Old Fart on 2010-11-17
Good...have you written down all four of the commands?

Because what I'm going to tell you next is going to shut down gnome.

---

### Post by preston collins on 2010-11-17
yup got them

---

### Post by Crusty Old Fart on 2010-11-17
Write these commands down because you won't be able to see them as soon as you drop into the virtual shell.

Get into a tty1 virtual shell by pressing the key combination: [COLOR=Blue]**Ctrl+Alt+F1**[/COLOR]

Log in at the prompts.

Shut down gnome with the following command:
```

sudo service gdm stop

```Now...enter the **first three **commands that you wrote down earlier in the right order.

This time we'll shutdown the machine instead of rebooting it.
So, the fourth command should be:
```

sudo shutdown -P now

```After the machine has shut down, connect your monitor to the VGA port on the Nvidia card, and boot your machine.

Whatever you do, don't experiment with anything. Don't try to install, or uninstall anything.

If you don't get the Nvidia card to boot to Gnome this time, there's another process we'll use to get there.

Any questions?

---

### Post by preston collins on 2010-11-17
> **Crusty Old Fart said:**
> Write these commands down because you won't be able to see them as soon as you drop into the virtual shell.

Get into a tty1 virtual shell by pressing the key combination: [COLOR=Blue]**Ctrl+Alt+F1**[/COLOR]

Log in at the prompts.

Shut down gnome with the following command:
```

sudo service gdm stop

```Now...enter the **first three **commands that you wrote down earlier in the right order.

This time we'll shutdown the machine instead of rebooting it.
So, the fourth command should be:
```

sudo shutdown -P now

```After the machine has shut down, connect you monitor to the VGA port on the Nvidia card, and boot your machine.

Whatever you do, don't experiment with anything, Don't try to install, or uninstall anything.

If you don't get the Nvidia card to boot to Gnome this time, there's another process we'll use to get there.

Any questions?

sounds good im on it

---

### Post by Crusty Old Fart on 2010-11-17
Sorry that took so long...I had some trouble getting it posted.

---

### Post by preston collins on 2010-11-17
so ctrl + alt + F1 didnt take me to the tty1 shell

all i got was a black screen and a blinking underscore in the top left corner

---

### Post by Crusty Old Fart on 2010-11-17
That's weird.

How did you get back to this thread?

---

### Post by preston collins on 2010-11-17
restarted my computer but i have just found if i typed 
ctrl + alt + F7 it brings me back neet eh

---

### Post by Crusty Old Fart on 2010-11-17
> **preston collins said:**
> restarted my computer but i have just found if i typed 
ctrl + alt + F7 it brings me back neet eh
Yup...that's because gnome runs on tty7.
Try Ctrl+Alt+F1 again but don't put in any commands. Just come back here (Ctrl+Alt+F7) and tell me if the shell showed a log in prompt.

---

### Post by preston collins on 2010-11-17
Just tryed it and nothen still blank i even tryed it without logging into gnome

---

### Post by Crusty Old Fart on 2010-11-17
There are six virtual shells available, tty1 through tty6.
See if tty2 (Ctrl+Alt+F2) gives you a login prompt. Then come back here and tell me.

Don't worry, were not going to try all six of them. If tty2 doesn't work, we'll try something other than virtual shells.

---

### Post by robsoles on 2010-11-17
If you have access to gnome then why don't you use Applications->Accessories->Terminal ?

Have I followed correctly that you are now using VGA output of the NVidia and you got Gnome?
[COLOR=Blue]
tty1 etc may be on output of onboard video card if you are looking at VGA out of NVidia right now - gnome is probably mirrored on both and tty does't mirror as far as I know.[/COLOR]

---

### Post by preston collins on 2010-11-17
yup same thing except it froze up so i just tryed both f1 and f2 and nothen happened

---

### Post by preston collins on 2010-11-17
> **robsoles said:**
> If you have access to gnome then why don't you use Applications->Accessories->Terminal ?

Have I followed correctly that you are now using VGA output of the NVidia and you got Gnome?

I would like to say that was true but the card doesnt wana give im running the onboards vga

---

### Post by Crusty Old Fart on 2010-11-17
> **robsoles said:**
> If you have access to gnome then why don't you use Applications->Accessories->Terminal ?

Have I followed correctly that you are now using VGA output of the NVidia and you got Gnome?
No...we're not running the Nvidia card and we don't have the Nividia driver loaded yet.

---

### Post by Crusty Old Fart on 2010-11-17
Preston:

Open a terminal window.
Please post the output from the following command:
```

ps -ef | grep tty

```
You can copy it from the code box and just paste it to the command prompt in your terminal window.

---

### Post by preston collins on 2010-11-17
> **Crusty Old Fart said:**
> Preston:

Open a terminal window.
Please post the output from the following command:
```

ps -ef | grep tty

```You can copy it from the code box and just paste it to the command prompt in your terminal window.


preston@preston-K7S7AG:~$ ps -ef | grep tty
root       754     1  0 23:43 tty4     00:00:00 /sbin/getty -8 38400 tty4
root       762     1  0 23:43 tty5     00:00:00 /sbin/getty -8 38400 tty5
root       774     1  0 23:43 tty2     00:00:00 /sbin/getty -8 38400 tty2
root       776     1  0 23:43 tty3     00:00:00 /sbin/getty -8 38400 tty3
root       780     1  0 23:43 tty6     00:00:00 /sbin/getty -8 38400 tty6
root       989   980  4 23:43 tty7     00:00:14 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-nagwEZ/database -nolisten tcp vt7
root      1024     1  0 23:43 tty1     00:00:00 /sbin/getty -8 38400 tty1
preston   1619  1599  0 23:48 pts/0    00:00:00 grep --color=auto tty

---

### Post by robsoles on 2010-11-17
Preston, please restart your computer, go into BIOS while it is starting, grab your best camera (please tell me you have one, your phone?) and take the clearest picture of the top level of your BIOS menus that you can and then boot up any which way gets you a workable browser and post the picture - please - any one of us should be able to get info off that picture to find a copy of the manual on line.

I'm sorry if I missed the post where reading the manual was mentioned, I think it's worth double checking to see if the BIOS does actually offer something to disable the onboard video or if really lucky perhaps there is a way to have it run both favoring the NVidia.

---

### Post by Crusty Old Fart on 2010-11-17
Well, I don't see anything wrong there.

I didn't want to do it this way, because it might throw some weird crap at you, but let's try putting these commands into the terminal window:

The following command removes the nouveau driver that doesn't work for your card:
     ```

     sudo apt-get --purge remove xserver-xorg-video-nouveau 

```
This next command installs the Nvidia driver that we need:
     ```

     sudo apt-get install nvidia-glx-185 

```
And this command command configures X to use the new driver:
     ```

     sudo nvidia-xconfig --force-generate 

```
Then shutdown, connect your monitor to the Nvidia VGA port, boot and tell me what happened.

---

### Post by Crusty Old Fart on 2010-11-17
> **robsoles said:**
> Preston, please restart your computer, go into BIOS while it is starting, grab your best camera (please tell me you have one, your phone?) and take the clearest picture of the top level of your BIOS menus that you can and then boot up any which way gets you a workable browser and post the picture - please - any one of us should be able to get info off that picture to find a copy of the manual on line.

I'm sorry if I missed the post where reading the manual was mentioned, I think it's worth double checking to see if the BIOS does actually offer something to disable the onboard video or if really lucky perhaps there is a way to have it run both favoring the NVidia.
[s]Did you miss the part of this thread where we already jumped through those hoops (sans camera)?
Posts #32 through #40[/s] (Sorry...your intention to "double check" didn't sink in on my initial reading of the quote above. We've never been to the BIOS manual.)

---

### Post by preston collins on 2010-11-17
> **robsoles said:**
> Preston, please restart your computer, go into BIOS while it is starting, grab your best camera (please tell me you have one, your phone?) and take the clearest picture of the top level of your BIOS menus that you can and then boot up any which way gets you a workable browser and post the picture - please - any one of us should be able to get info off that picture to find a copy of the manual on line.

I'm sorry if I missed the post where reading the manual was mentioned, I think it's worth double checking to see if the BIOS does actually offer something to disable the onboard video or if really lucky perhaps there is a way to have it run both favoring the NVidia.


hope this helps

---

### Post by robsoles on 2010-11-17
> **Crusty Old Fart said:**
> [s]Did you miss the part of this thread where we already jumped through those hoops (sans camera)?
Posts #32 through #40[/s] (sorry...your intention to "double check" didn't sink in on my initial read of the quote above.

I feel a bit like I did when my first wife's mother offered to punch me in the nose if I went and got the dictionary and we check this word her other daughter and I were disagreeing about at the time.

I read #32 to #40 very carefully a couple of days ago, again yesterday and now I read them again today. No change to my request, I just want enough of the BIOS's ID string to find the manual, I'll happily read it for a mention of onboard VGA, always worth at least a quick check of the manual!

---

### Post by jocko on 2010-11-17
> **robsoles said:**
> Preston, please restart your computer, go into BIOS while it is starting, grab your best camera (please tell me you have one, your phone?) and take the clearest picture of the top level of your BIOS menus that you can and then boot up any which way gets you a workable browser and post the picture - please - any one of us should be able to get info off that picture to find a copy of the manual on line.

I'm sorry if I missed the post where reading the manual was mentioned, I think it's worth double checking to see if the BIOS does actually offer something to disable the onboard video or if really lucky perhaps there is a way to have it run both favoring the NVidia.
I'm guessing[ this is it ]("http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=315&CategoryID=1&MenuID=50&LanID=0")(from the lshw output in post #21).
According to that manual, the only relevant setting is "primary graphics adapter" where the choices are "agp" or "pci", where "agp" will only use the onboard (my interpretation), and pci will use both cards. But no setting to disable the onboard as far as I can see...

---

### Post by Crusty Old Fart on 2010-11-17
> **robsoles said:**
> I feel a bit like I did when my first wife's mother offered to punch me in the nose if I went and got the dictionary and we check this word her other daughter and I were disagreeing about at the time.

I read #32 to #40 very carefully a couple of days ago, again yesterday and now I read them again today. No change to my request, I just want enough of the BIOS's ID string to find the manual, I'll happily read it for a mention of onboard VGA, always worth at least a quick check of the manual!
Right!...I agree....I read what you posted too fast...Sorry.

---

### Post by Crusty Old Fart on 2010-11-17
> **jocko said:**
> I'm guessing[ this is it ]("http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=315&CategoryID=1&MenuID=50&LanID=0")(from the lshw output in post #21).
According to that manual, the only relevant setting is "primary graphics adapter" where the choices are "agp" or "pci", where "agp" will only use the onboard (my interpretation), and pci will use both cards. But no setting to disable the onboard as far as I can see...
Well...now we know for sure. Thanks for checking that out, jocko.

Preston: Any luck with the instructions in Post #174?

---

### Post by preston collins on 2010-11-17
Nope no luck im in recovery mode it sent me to tty1 and i tryed ctrl alt f7 and got nothen

I got ahold of ECS and they said to reset the bios manually with the card in the pci slot and that would make the pci card the first choice, i tryed it and nothen happened

---

### Post by Crusty Old Fart on 2010-11-17
> **preston collins said:**
> Nope no luck im in recovery mode it sent me to tty1 and i tryed ctrl alt f7 and got nothen

I got ahold of ECS and they said to reset the bios manually with the card in the pci slot and that would make the pci card the first choice, i tryed it and nothen happened
Yup...in Post #60 the xorg.conf that we got showed card0 being driven by "nv" and card1 being driven by "fbdev". I assumed by the driver assignment that card0 was the Nvidia card. Plus, the nv driver was assigned to the device on      BusID       "PCI:3:0:0". Whereas the fbdev driver was assigned to the device on      BusID       "PCI:1:0:0"

---

### Post by jocko on 2010-11-17
Preston: I think I may have the beginning of an idea.
It may be worth a try to see what happens if you prevent the driver for the onboard card from loading.

If your system is in a state where you can boot with both cards connected to monitors (but getting output only from the onboard), try this:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```At the end of the file, add these lines:
```
blacklist sis_agp
blacklist agpgart
blacklist sis
blacklist sisfb
```This should prevent loading of any drivers needed by your onboard card.
Reboot and see if you get any output from your nvidia card (but keep the onboard card connected).
If things would get worse than where you are now, boot from a live cd (if you can't get a gui, tty or recovery mode boot to work), mount your ubuntu partition and revert the changes you just made to the blacklist.conf file...

---

### Post by Crusty Old Fart on 2010-11-17
Preston:

Crtl+Alt+F7 doesn't work from recovery mode because gnome isn't loaded by recovery mode.

But, it's nice to know that you can enter recovery mode.

The only thing I can think of tonight that we haven't done is to try to configure X from recovery mode (assuming that the nouveau remove command and the nvidia install commands worked, which they should have.)

Typically, X doesn't like to be reconfigured while it's running gnome. That's why I wanted to get to a tty virtual shell and shut down gnome before configuring X.

So...How about connecting your monitor to your nvidia card, getting into recovery mode, log in...
and then issue the following command:
```

sudo nvidia-xconfig --force-generate

```...and then:
```

sudo reboot now

```

---

### Post by Crusty Old Fart on 2010-11-17
Too many of us stirring the pot right now. Poor Preston.

I'll bail for now and let jocko take over.

Good luck.

---

### Post by jocko on 2010-11-17
> **Crusty Old Fart said:**
> Too many of us stirring the pot right now. Poor Preston.

I'll bail for now and let jocko take over.

Good luck.
Well, I off for work soon, so I can't do much more now...

---

### Post by Crusty Old Fart on 2010-11-17
Jocko:

We did a fresh install tonight and got Grub back. Then we tried to get the Nvidia card running as shown in the following quote. Do you see anything in this procedure that could be giving us a problem?

Thanks in advance for taking a look at it.

> **Crusty Old Fart said:**
> Alrighty then...Here we go...

Now we're going to try to get your Nvidia card working.

Write down as many of the following steps on a piece of paper as you think you need to, **especially the commands.** 

Perform the following steps:

[LIST]
[*]Shutdown (not restart) your computer.
[*]Disconnect your monitor from the on-board card. We don't want **anything** connected to the on-board card now.
[*]Connect your monitor to the VGA port on the Nvidia card only. Don't plug anything into its DVI port.
[*]Reboot.
[*]Hopefully, you'll see Grub come up. It will want to boot from the default kernel. Just let it do it.
[*]Next, you should be taken to a tty1 virtual shell. Go ahead and log in and then issue the following commands (write these down carefully, exactly as they appear in the code boxes):
[/LIST]
[INDENT][INDENT]The following command removes the nouveau driver that doesn't work for your card:
```

sudo apt-get --purge remove xserver-xorg-video-nouveau

```This next command installs the Nvidia driver that we need:
```

sudo apt-get install nvidia-glx-185

```And this command command configures X to use the new driver:
```

sudo nvidia-xconfig --force-generate

```Finally, reboot using the following command:
```

sudo reboot now

```[/INDENT][/INDENT]Hopefully, this will have done it and your Nvidia card will boot into gnome.

Please let me know how it went.

---

### Post by jocko on 2010-11-17
> **Crusty Old Fart said:**
> Jocko:

We did a fresh install tonight and got Grub back. Then we tried to get the Nvidia card running as shown in the following quote. Do you see anything in this procedure that could be giving us a problem?

Thanks in advance for taking a look at it.
Nothing really wrong there, but I don't think it's very helpful either...
I think the first thing to do before you install the proprietary driver is to get the card working properly with the nouveau driver. If it's not working with nouveau, I don't think there is any chance to get it to work with the nvidia driver.

My guess at the moment is that the agpgart driver (loaded because of the detection of the onboard agp card) interfers with the pci card. I've found a few posts that seem to describe similar problems, where an agpgart driver mistakenly tries to load a pci or pcie card (which will probably never work)...

---

### Post by preston collins on 2010-11-17
> **jocko said:**
> Preston: I think I may have the beginning of an idea.
It may be worth a try to see what happens if you prevent the driver for the onboard card from loading.

If your system is in a state where you can boot with both cards connected to monitors (but getting output only from the onboard), try this:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```At the end of the file, add these lines:
```
blacklist sis_agp
blacklist agpgart
blacklist sis
blacklist sisfb
```This should prevent loading of any drivers needed by your onboard card.
Reboot and see if you get any output from your nvidia card (but keep the onboard card connected).
If things would get worse than where you are now, boot from a live cd (if you can't get a gui, tty or recovery mode boot to work), mount your ubuntu partition and revert the changes you just made to the blacklist.conf file...

So i gave it a shot and not a whole lot happend tryed booting up in both recovery mode and without both having the cards dvi pluggen in and nothing happened

---

### Post by Crusty Old Fart on 2010-11-17
> **jocko said:**
> Nothing really wrong there, but I don't think it's very helpful either...
I think the first thing to do before you install the proprietary driver is to get the card working properly with the nouveau driver. If it's not working with nouveau, I don't think there is any chance to get it to work with the nvidia driver.
Well...it didn't work on either VGA or DVI ports on the Nvidia card when we booted from the Live CD. But, beyond that, we didn't muck around with any configuration for it.

> 
My guess at the moment is that the agpgart driver (loaded because of the detection of the onboard agp card) interfers with the pci card. I've found a few posts that seem to describe similar problems, where an agpgart driver mistakenly tries to load a pci or pcie card (which will probably never work)...Hope you're right. Nothing else seems to be working for us.

Have a good day at work,

Crusty

---

### Post by preston collins on 2010-11-17
im game for anything i just want this stupid card to work

well im off to be pick this up tomorrow 

thanks for everything so far

---

### Post by Crusty Old Fart on 2010-11-17
Preston:

Did you try what I put in the quoted post below?

> **Crusty Old Fart said:**
> Preston:

Crtl+Alt+F7 doesn't work from recovery mode because gnome isn't loaded by recovery mode.

But, it's nice to know that you can enter recovery mode.

The only thing I can think of tonight that we haven't done is to try to configure X from recovery mode (assuming that the nouveau remove command and the nvidia install commands worked, which they should have.)

Typically, X doesn't like to be reconfigured while it's running gnome. That's why I wanted to get to a tty virtual shell and shut down gnome before configuring X.

So...How about connecting your monitor to your nvidia card, getting into recovery mode, log in...
and then issue the following command:
```

sudo nvidia-xconfig --force-generate

```...and then:
```

sudo reboot now

```

I'll be busy for a while helping my cousin recover from a nasty hard drive crash. So, I may not be around for a few days. I'm fairly sure that jocko and robsoles will check in. They both seem pretty committed to helping you out. Good luck. Hopefully, by the time I get back to taking a look at this thread, they will have been able to get your Nvidia card to play nice for you.

---

### Post by CurryNoodles on 2010-11-17
I'm having the same problems too, wonder these solution applied on my ubuntu 6.10 as well...

---

### Post by robsoles on 2010-11-17
> **CurryNoodles said:**
> I'm having the same problems too, wonder these solution applied on my ubuntu 6.10 as well...

1) Please start your own thread.
2) Please consider moving forward to at least Ubuntu 10.04 LTS if not Ubuntu 10.10 before starting a thread about device support.

> **preston collins said:**
> im game for anything i just want this stupid card to work

well im off to be pick this up tomorrow 

thanks for everything so far

My request to see your BIOS 'home screen' wasn't as useful as I was hoping, sorry I put you to the trouble but jolly good on you for posting it.

Maybe there is a jumper on the motherboard to kill onboard video - **please post the model identification for your motherboard**, I'll find it's manual and risk disappointment of reading it and finding we still can't disable your onboard video. (Please forgive me if the Motherboard ID has been posted to this thread even once!)


Can you get (do you have) a second monitor? I've heard of such crazy hardware configurations that I would really like to know what you see in System->Preferences->Monitors when you boot from the LiveCD with a monitor connected to VGA or DVI output of NVidia, and another monitor connected to onboard VGA (of course leaving NVidia card plugged into motherboard :))

I would also like to know what you see in System->Preferences->Monitors when you boot from an installed instance of Ubuntu which has had the NVidia driver version 185 installed but same circumstance of connectivity -

If we can't disable the onboard video then the machine will always 'boot' using it and we can only hope to get your NVidia going as mirrored (and it will only switch on after the OS is 9/10ths booted) and that problem may as well be attacked with a monitor plugged in to both video cards at the same time.

I am at work for another four or so hours but I can pop in at regular intervals while I am here. I go fairly late into the night once I get home.

---

### Post by preston collins on 2010-11-17
> **Crusty Old Fart said:**
> Preston:

Did you try what I put in the quoted post below?



I'll be busy for a while helping my cousin recover from a nasty hard drive crash. So, I may not be around for a few days. I'm fairly sure that jocko and robsoles will check in. They both seem pretty committed to helping you out. Good luck. Hopefully, by the time I get back to taking a look at this thread, they will have been able to get your Nvidia card to play nice for you.


Just tryed it but nothing happened no fireworks yet

---

### Post by preston collins on 2010-11-17
> **robsoles said:**
> 1) Please start your own thread.
2) Please consider moving forward to at least Ubuntu 10.04 LTS if not Ubuntu 10.10 before starting a thread about device support.



My request to see your BIOS 'home screen' wasn't as useful as I was hoping, sorry I put you to the trouble but jolly good on you for posting it.

Maybe there is a jumper on the motherboard to kill onboard video - **please post the model identification for your motherboard**, I'll find it's manual and risk disappointment of reading it and finding we still can't disable your onboard video. (Please forgive me if the Motherboard ID has been posted to this thread even once!)


Can you get (do you have) a second monitor? I've heard of such crazy hardware configurations that I would really like to know what you see in System->Preferences->Monitors when you boot from the LiveCD with a monitor connected to VGA or DVI output of NVidia, and another monitor connected to onboard VGA (of course leaving NVidia card plugged into motherboard :))

I would also like to know what you see in System->Preferences->Monitors when you boot from an installed instance of Ubuntu which has had the NVidia driver version 185 installed but same circumstance of connectivity -

If we can't disable the onboard video then the machine will always 'boot' using it and we can only hope to get your NVidia going as mirrored (and it will only switch on after the OS is 9/10ths booted) and that problem may as well be attacked with a monitor plugged in to both video cards at the same time.

I am at work for another four or so hours but I can pop in at regular intervals while I am here. I go fairly late into the night once I get home.


Model id: K7S7AG

Im in recovery mode but the 185 is installed and when i click on the monitors i get a window saying

" It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead " 

And if i click yea i get another window saying

" You do not appear to be using the NVIDIA X driver. Please edit your x configuration file (just run 'nvidia-xconfig' as root). and restart the X server. "

---

### Post by robsoles on 2010-11-17
> **preston collins said:**
> Model id: K7S7AG

Im in recovery mode but the 185 is installed and when i click on the monitors i get a window saying

" It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead " 

And if i click yea i get another window saying

" You do not appear to be using the NVIDIA X driver. Please edit your x configuration file (just run 'nvidia-xconfig' as root). and restart the X server. "

Sorry, should have specified: Don't click 'yes' or 'ok', click 'no' and go through to the monitors dialog, not the nvidia tool!

---

### Post by preston collins on 2010-11-17
> **robsoles said:**
> Sorry, should have specified: Don't click 'yes' or 'ok', click 'no' and go through to the monitors dialog, not the nvidia tool!
[IMG]file:///home/preston/Desktop/Screenshot.png[/IMG]
I attached a screen shot hope that helps

---

### Post by robsoles on 2010-11-17
> **preston collins said:**
> [IMG]file:///home/preston/Desktop/Screenshot.png[/IMG]
I attached a screen shot hope that helps

Screenshot helps me know it has nothing we can attack in it.

> **preston collins said:**
> Model id: K7S7AG

...

I spotted 0 options to directly disable the onboard video in the manual :(

Please tell me whether or not you have a second monitor to play with :)


May I know your current BIOS setting for the items in the attached picture please:


[http://www.ecs.com.tw/ECSWebSite/Downloads/Downloads_Driver_Detail.aspx?MenuID=61&LanID=0&detailid=261](http://www.ecs.com.tw/ECSWebSite/Downloads/Downloads_Driver_Detail.aspx?MenuID=61&LanID=0&detailid=261) has the manual I found and used, just in case anyone can point out that I've got the wrong one or missed something useful in it.

---

### Post by preston collins on 2010-11-17
> **robsoles said:**
> Screenshot helps me know it has nothing we can attack in it.



I spotted 0 options to directly disable the onboard video in the manual :(

Please tell me whether or not you have a second monitor to play with :)


May I know your current BIOS setting for the items in the attached picture please:


[http://www.ecs.com.tw/ECSWebSite/Downloads/Downloads_Driver_Detail.aspx?MenuID=61&LanID=0&detailid=261](http://www.ecs.com.tw/ECSWebSite/Downloads/Downloads_Driver_Detail.aspx?MenuID=61&LanID=0&detailid=261) has the manual I found and used, just in case anyone can point out that I've got the wrong one or missed something useful in it.

its as you posted for the bios mine is he same settings and i do have a tv that i have a dvi input plus the monitor that i am on right now

---

### Post by robsoles on 2010-11-17
> **preston collins said:**
> its as you posted for the bios mine is he same settings and i do have a tv that i have a dvi input plus the monitor that i am on right now

About BIOS: Forgive me if it's in the thread already but have you tried booting this PC with the other option chosen for "Primary Graphics Adapter"? - if not please try it with the PC set up as 'even cooler' from next paragraph, revert the setting in BIOS if it doesn't make a 'good difference' (Insist I post clearer instructions if that came out horribly muddled!)

Cool. Even cooler if you can position the PC so that you can have the TV hooked into the NVidia output while keeping the onboard video VGA hooked into the monitor you've been using.



Whenever you hooked your monitor into the NVidia card and saw a purple background and nothing else happening (or whatever it displayed, the monitor didn't go into power-down/power-saving mode) it was -><- this close to working to some capacity or other.

I vote we pursue that and see if we can get to twinview or xinerama while having an individual monitor on each card - can't take the outputs from both cards to the one monitor because on startup the monitor will favor the DVI input if both VGA and DVI cables have signals present and the NVidia can't see the boot process so DVI isn't worth looking at ***yet...***


EDIT: Please boot from HDD with the 'even cooler' config, I expect your onboard VGA to remain 'primary' for you to be able to use - Please tell me (a) if I am wrong or (b) what is displayed on the TV once you log into Gnome.

I'm semi-aware of what state your system is in if you haven't done anything you haven't mentioned doing, please let me know if you've done anything else to the system on the HDD etc etc.

It is of some interest to see the same physical configuration's behaviour booted from the LiveCD - if the picture on the TV is a purple background off LiveCD and pitch black (or similar) from your HDD I will probably ask if you can stand reinstalling.

---

### Post by Crusty Old Fart on 2010-11-17
I'm not meaning to interrupt what you guys are doing. I really don't want to muddy things up by getting in the way.

I just wanted to let you know that I've updated Post #111 with a lot of links to posts having information and links to resources external to this thread.

In order to make it easy to access, my signature has temporarily been changed to provide a link to Post #111 as well as the date of the most recent update. I'll leave it that way until thread comes to a close.

Carry on, lads!

Good Luck and Good Night.

---

### Post by robsoles on 2010-11-17
> **Crusty Old Fart said:**
> I'm not meaning to interrupt what you guys are doing. I really don't want to muddy things up by getting in the way.

I just wanted to let you know that I've updated Post #111 with a lot of links to posts having information and links to resources external to this thread.

In order to make it easy to access, my signature has temporarily been changed to provide a link to Post #111 as well as the date of the most recent update. I'll leave it that way until thread comes to a close.

Carry on, lads!

Good Luck and Good Night.

Thanks Crusty, speak up if even slightly provoked - don't worry about interrupting :)

---

### Post by Crusty Old Fart on 2010-11-18
> **robsoles said:**
> Thanks Crusty, speak up if even slightly provoked - don't worry about interrupting :)
Thanks Rob -- I can feeeeeel the luv!...Can you?...Luvya back, Bro...Can you feel it now?...I can. -- and no, I'm not gay...I just "ain't ~ quite ~ right"...The toys in _my_ attic play with each other without me -- but, I bet you've already figured that out.

Anyhow, I gotta blow...good luck with the mess.

---

### Post by robsoles on 2010-11-18
I am about to take off for work, I will check in directly I get there in 50 minutes - how is what going Preston?

---

### Post by preston collins on 2010-11-18
so i guess this is exciting but right now im in recovery mode and i and i have the monitor running off of the dvi and its working the only thing is i had to remove the nvidia driver. As well i cant get into gnome

I also have the onboards vga plugged into the same monitor and its almost like the settings are backwards from before.

when we started i could only use the onboard vga to see everything but now im using the dvi to see everything, but i have to use the vga to get everything started because i cant see grub with the dvi.

---

### Post by robsoles on 2010-11-18
(Good morning :))

That gives me the impression that you are not keeping the monitor attached via the onboard video card and you are not keeping the TV attached to the NVidia but instead you are either switching between the pair or have both going to the same monitor.

It'd be fair enough to be switching between the pair although not as useful as having a monitor per video card at this point.

It'd really rub my fur the wrong way entirely to be sure that you have both video card outputs hooked up to the same monitor.


I was rather hoping that without changing anything from the last known circumstance you were in you would hook up the TV to the output on the NVidia card and try the stuff in my first post on this page.


Please hook monitor into onboard video card
Connect TV into NVidia card
Boot from the LiveCD
Choose 'try ubuntu'

What do you see on the TV once the desktop has loaded (please!)

---

### Post by preston collins on 2010-11-18
we are watching a movie right now its going to be atleast another hour till its finished i'll get back to you when its over

---

### Post by preston collins on 2010-11-18
hey yea so im running the recovery on the tv connented to the dvi and the monitor to the vga

---

### Post by robsoles on 2010-11-18
Recovery? Do you mean having booted from the HDD? So, if I followed correctly from before you are looking at a blank monitor and the TV is displaying a TTY terminal?



Please boot into 'try ubuntu' from LiveCD (without unplugging anything) and tell me if following is correct:

Monitor displays boot process, splash, option of install or try, then desktop
TV displays nothing during boot process, nothing during splash, ??????? during option of install or try, then purple background [COLOR="Blue"](when desktop displays on Monitor)[/COLOR] ???

---

### Post by preston collins on 2010-11-18
> Recovery? Do you mean having booted from the HDD? So, if I followed  correctly from before you are looking at a blank monitor and the TV is  displaying a TTY terminal?

The tv does display the tty1 screen and the monitor displays a few lines of txt  
EX: 
[     0.501922] ACPI: PCI Interrrupt Link [LNKG] enabled at IRQ 5
[     0.501969] ohci_hcd 0000:00:03.2: PCI INT C -> Link[LNKG] -> HSI 5 (level,oq) -> IRQ 5

there is some stuff about usb, PS/2 controllers and mouses and keyboards

but the lines of txt is just sitting there.

and i will be back with the info about the live cd

---

### Post by robsoles on 2010-11-18
Cool - please don't try to change anything about the installed OS while you are booted from the LiveCD :) (ie., don't reinstall or delete current install yet - with a bit of luck we walk from where it is to where we want it without reinstalling but I am not holding my breath!)

---

### Post by preston collins on 2010-11-18
Alright so i booted with the cd and the splash screen came up on the tv so dvi and i got the try it page on the monitor - vga, clicked try it and the tv is now showing a black screen with 5 lines of txt the last line saying checking battery state ...    [ OK  ]

An the monitor has the try it version of ubuntu running

---

### Post by robsoles on 2010-11-18
Very cool - anything at all displaying on the TV while a GUI is also available is good.

I am working with a copy of 10.04 and I think you are in 10.10 so forgive me and look for the nearest equivalent if you can't find what I tell you to look for - lemme know too though :)


'System->Administration->Hardware Drivers' - What does it list, if anything, in that window please? (may take time to load the list!)

'System->Preferences->Monitors' - Does it look much different from the screenshot you posted previously? If so, may I see it again please?


Take no action, please don't issue a command or select anything in the GUI that actually tries to change any settings just yet :)

---

### Post by preston collins on 2010-11-18
> **robsoles said:**
> Very cool - anything at all displaying on the TV while a GUI is also available is good.

I am working with a copy of 10.04 and I think you are in 10.10 so forgive me and look for the nearest equivalent if you can't find what I tell you to look for - lemme know too though :)


'System->Administration->Hardware Drivers' - What does it list, if anything, in that window please? (may take time to load the list!)

'System->Preferences->Monitors' - Does it look much different from the screenshot you posted previously? If so, may I see it again please?


Take no action, please don't issue a command or select anything in the GUI that actually tries to change any settings just yet :)

the hardware drivers is labled as additional drivers
the screen shot is what i got for both

---

### Post by robsoles on 2010-11-18
OK, so a very well written /etc/X11/xorg.conf file should be able to land Gnome squarely on the DVI output of the NVidia card, once we load the correct driver - I'm thinking it is more likely the recommended one than anything else, we may have to block certain drivers as suggested by Jocko though!

I need to dig up examples of xorg.conf files that deal with multiple graphics adapters to proceed with any degree of certainty - I can get them from the xorg mailing list but it's going to take me a bit of time, hopefully not much.


With the machine hooked up like that, each video card with it's own monitor/TV, have a fiddle and play based on ideas/instructions given in this thread previously (but keep both monitors plugged in to a card's output each and turned on/ready all along) - note any encouraging results and how you got them, post anything that seems relevant as you go.

I'm going to post to the xorg mailing list asking for people running multiple heads on mixed graphics adapters (plenty exist according to stuff going across the list) to please send me example xorg.conf files which enable non-matched video cards and any tips they'd care to drop on me - if I pose the request well I should drown in examples within a few hours :)

---

### Post by Crusty Old Fart on 2010-11-18
Rob:

Just curious --

I've been following along here and am wondering if your plan, in general terms, goes something like this:

[LIST=1]
[*]Install the Nvidia driver (from what I've been able to determine, the recommended one is the 185, but I could be wrong about that detail).
[*]Generate, modify or create from scratch an xorg.conf that will run gnome on both monitors.
[*]If you're successful in step 2, then try to modify xorg.conf and do whatever driver un-installing and/or jocko's blacklisting you need to in order to run only one monitor being driven by the Nvidia card?
[/LIST]
This might save you some frustration:

[LIST]
[*]Somewhere back in one of your posts, you mentioned using Xinerama or Twinview. If you enable Xinerama in xorg.conf, and decide you want to make changes to xorg.conf later, you will need to **disable** Xinerama in order to have your changes take effect. Before enabling Xinerama again, you may need to restart gdm or reboot so that your changes get applied in X, then re-enable Xinerama and either restart gdm or reboot again. I don't know enough about Twinview to comment on its behavior here.
[/LIST]
However, if you're ultimately wanting to get to a single head setup, running off the Nvidia card, you shouldn't have to play with either Xinerama or Twinview. They are just desktop extenders. I don't think they'll do much to help you get gnome running on both monitors, It may be that Xinerama or Twinview just get in your way and add unnecessary complications.

From where you are right now, you might want to consider the following before installing the Nvidia driver:

[LIST=1]
[*]Shutdown gdm.
[*]Have the system automatically generate an xorg.conf.new file and examine it to see if it is using the nouveau driver.
[*]If the the system grabs the nouveau driver, the generated xorg.conf.new may be all you need, or at least may give you a configuration that might not require much modification.
[/LIST]
Quite a while back we had the system make us an xorg.conf.new, but we weren't running dual heads at the time, even though the xorg.conf.new that was created made it look like we were. Also, the system chose to use the "nv" driver for the Nvidia card, which jocko didn't think was worth much.

Good luck.

---

### Post by Crusty Old Fart on 2010-11-18
> **jocko said:**
> ...

I think the first thing to do before you install the proprietary driver is to get the card working properly with the nouveau driver. If it's not working with nouveau, I don't think there is any chance to get it to work with the nvidia driver.

My guess at the moment is that the agpgart driver (loaded because of the detection of the onboard agp card) interfers with the pci card. I've found a few posts that seem to describe similar problems, where an agpgart driver mistakenly tries to load a pci or pcie card (which will probably never work)...
Who knows? But if jocko is right, maybe xorg.conf should be modified to work with the nouveau driver before trying the Nvidia driver.

I'll crawl back under my rock now.

---

### Post by robsoles on 2010-11-19
> **Crusty Old Fart said:**
> Who knows? But if jocko is right, maybe xorg.conf should be modified to work with the nouveau driver before installing the Nvidia driver.

I'll crawl back under my rock now.

Thanks for crawling out, please don't crawl too far back in :)

I shouldn't have mentioned xinerama, it's just a partner option to mirror/twinview but it isn't necessary for Preston's desires.

Here's where I'm operating from:

1) Preston just wants to use the NVidia graphics card to drive one monitor.
2) Onboard video, Xabre 200 AGP8X 256-bit GPU, cannot be disabled at BIOS level.
3) Geforce 9400gt 1G (PCI)  video card displays anything at all under most circumstances (just not going into standy, prefer text but purple background with nothing happening is still ''anything'').

So I am believing:

1) We can't configure the system to show us POST, for example we are unlikely to access BIOS, on the NVidia's output.
2) We should be able to get the Kernel to boot on the NVidia and show us the boot process there, I think this is happening off his installed OS at the mo but it doesn't make it to gnome (ooh, logs!)
3) Once/If we've got twinview (duplicated per monitor) we should be able to figure out how to have x shut down the onboard VGA output and stop using any processing power to drive it.
4) Twinview may not be possible and we may even need to figure out how to disable onboard VGA in Kernel boot config before any drivers for video load (ouch!).

If we can't disable the onboard video under any circumstances then I think it is better controlled either into twinview (or perhaps into displaying TTYx if possible) rather than trying to just not load a driver and ignoring it (I'm watching for if I have this idea backwards though, speak up!) - then it can be left unplugged in favour of the NVidia's output.

I'm hoping it is possible to get Preston's stuff configured the way he wants - it shouldn't require luck to get a neato setup out of it but I am a little worried :-k - I've got NVidia cards and I've got Extended desktop on two monitors but I've only read of multiple video cards, with the odd non-matching pair, in the xorg mailing list 8-[

**Preston:** Please reboot off your HDD and log into tty1 I am expecting to find on your TV at the moment.
```
tail /var/log/xorg.0.log
```Pretty picture please :) (assuming you can't post it in this condition)
```
tail /var/log/messages
```Pretty picture please.

I might be after a couple more logs after seeing those, might ask you to show me a bigger picture of either of those logs - don't worry, but sorry I am sending through more restarts.

@anybody: If you can see my mistake, delusion or other failing then please don't fear embarrassing or offending me, you'll be helping!

---

### Post by Crusty Old Fart on 2010-11-19
Howdy Rob:

Thanks for taking the time to write all that up. It helps a lot to know where your head is taking the thread rather than trying to guess at it based on where it's been.
> 2) Onboard video, Xabre 200 AGP8X 256-bit GPUThanks for that. It's been added to Post #111.

> 
1) We can't configure the system to show us POST, for example we are unlikely to access BIOS, on the NVidia's output.Really? Are you saying that if Preston doesn't have anything connected to the integrated card, and the monitor is connected to the Nvidia card, the BIOS cannot be accessed? I seem to recall that when Preston was running Windows XP, the Nvidia card ran fine, all by itself. At least, I think it did. It's hard to remember if he was running one or two monitors with XP. I never thought to ask him if he had no access to his BIOS before XP's boot process began.

So much of where the focus is now involves the desire to disable the integrated card somehow. If we REALLY need to do that, it makes me wonder how XP did it. And if XP didn't disable the integrated card somehow, maybe Ubuntu doesn't need to either.

Just thinking...

I wonder if anything could be learned by having Preston boot up XP with the dual head setup you guys have now, and taking a look at the display properties in XP.

---

### Post by robsoles on 2010-11-19
> **Crusty Old Fart said:**
> ...

So much of where the focus is now involves the desire to disable the integrated card somehow. If we REALLY need to do that, it makes me wonder how XP did it. And if XP didn't disable the integrated card somehow, maybe Ubuntu doesn't need to either.

Just thinking...

I wonder if anything could be learned by having Preston boot up XP with the dual head setup you guys have now, and taking a look at the display properties in XP.

It has to be possible to send the video card into low power mode, how is another thing and when we find it I think where/how it is will embarrass us but we will learn :)

It will probably prove invaluable, Preston please boot up in a copy of XP configured to use the NVidia output as primary and tell us a few things:

1) What is the monitor connected to the onboard VGA output displaying.
2) Details from Device Manager regarding both cards, whether Xabre is disabled etc.
3) Details from "Display Properties" 'Settings' tab and if Xabre is listed anywhere, especially in dialog that opens when 'Advanced' is clicked on settings tab.


Flipside, in Linux:

Booting from the HDD, as in my previous post, try

```
sudo apt-get install nvidia-glx-185
sudo nvidia-xconfig --force
startx
```and then get me the tails of those logs, as in that previous post, unless a GUI happens to open on the TV :)

---

### Post by jocko on 2010-11-19
> **Crusty Old Fart said:**
> Who knows? But if jocko is right, maybe xorg.conf should be modified to work with the nouveau driver before trying the Nvidia driver.

I'll crawl back under my rock now.
The problem is that there are two graphics cards, and that it seems like Preston can't get Xorg to display anything useful on the nvidia card. Installing the nvidia driver in such a situation will not help, and may just make things more complicated by introducing a driver which will definitely conflict with the driver for the onboard card.
Unfortunately Preston still haven't posted any log files (esp. /var/log/Xorg.0.log) that would hopefully show us *why* things doesn't work...

So my advice is:
1. Uninstall the nvidia driver.
2. Make sure the nouveau driver is still installed (it should be unless you've uninstalled it).
3. Delete/rename /etc/X11/xorg.conf. It is not needed to get the nouveau driver working.
4. Reboot with both graphics cards connected to separate displays.
This should bring up gnome on the onboard card, but the nvidia card will probably not work.

5. Open up gnome-display-properties (System-->Settings-->Displays).
How many screens are detected?
If only one screen is detected I think there should be some helpful information in some of the log files.
Open up a terminal and run this:
```
dmesg > dmesg.txt
cat /var/log/Xorg.0.log > Xorg.0.log.txt
```
This should make two new text files in your home directory. Either add them as attachments to a post or paste their contents between code brackets ([noparse]```
 and 
```[/noparse]).

6. Turn off the computer, unplug the display cable from the onboard card and reboot.
I guess you'll just get to the boot splash, but you haven't really explained to us exactly what happens next (or I've missed it). Does the boot splash just stay on forever? Does it just flicker off and show you a black screen? With text? With a cursor? Can you switch to a tty? Does it just turn off the monitor completely? Anything else worth mentioning?

7. We need the log files from **this boot**, because it is very likely that they will tell us exactly what happened. If you can get to a tty, run this:
```
dmesg > dmesg2.txt
cat /var/log/Xorg.0.log2.text
```
Otherwise boot from a live cd (otherwise the logs will be overwritten) and browse to the /var/log/ folder of your installed system and copy the two files (dmesg and Xorg.0.log) from there.

---

### Post by Crusty Old Fart on 2010-11-19
> **robsoles said:**
> 
Flipside, in Linux:

Booting from the HDD, as in my previous post, try

```
sudo apt-get install nvidia-glx-185
sudo nvidia-xconfig --force
[s]startx[/s] [B][COLOR=Red]<--That's been depreciated.
Use the following instead:
[/COLOR][/B][COLOR=Red][COLOR=Black]sudo service gdm start
[/COLOR][/COLOR]
```and then get me the tails of those logs, as in that previous post, unless a GUI happens to open on the TV :)
Rob: Check changes in code box above. But more importantly, take a look at jocko's post above. I agree with him that this isn't the time to be installing the 185 again. This isn't the first time he's told us to look at the logs. If we don't do it soon, we might just continue pissing into the wind, Even worse: jocko might get frustrated with us for not taking his advice and give up on the idea of trying to inject any more of his wisdom into this thread.

---

### Post by robsoles on 2010-11-19
Thanks Jocko, forgive me I want to make sure Preston follows your instructions.


1) To uninstall NVidia drivers if you think any are installed
```
sudo apt-get purge nvidia*
```2) To install Nouveau driver if you think it isn't
```
sudo apt-get install xserver-xorg-video-nouveau
```3) Removing xorg.conf - probably engraved in you now but anyway
```
sudo rm /etc/X11/xorg.conf
```4) Keep the TV on your DVI output of NVidia and your monitor on the onboard VGA port.

5) It might be "System->Preferences->Monitors" in 10.10, tell me if you can find something else without a proprietary driver installed.
[COLOR=Blue]```
dmesg > ~/dmesg-both.txt
cat /var/log/Xorg.0.log >> ~/xorg-log-both.txt
```[/COLOR] 
6) Oooh yes please - unplug onboard VGA and on your way to completing Jocko's instructions please try to access BIOS using any output of the NVidia (if you set primary device to AGP in BIOS before and didn't switch it back you may need to while plugged into the onboard VGA to make this a fair test - thanks Crusty.)

7) We should have asked you to show us the logs the first time it booted to tty1 on DVI output, sorry. We need you to post the files that are created and if I can get you to use my copy of the commands:
```
dmesg > ~/dmesg-log.txt
cat /var/log/Xorg.0.log >> ~/xorg-log.txt
```[COLOR=Blue]If you haven't issued a 'cd' command since logging in you should be in the same directory the files have been written to, when you boot from the LiveCD this is [COLOR=Red][s]/media/<insert-silly-string-here>/home/<your-user-name> under the file system you've mounted from places before[/s] /home/ubuntu[/COLOR]. I could read files in an unencrypted home directory booted off the 10.10 LiveCD so hopefully you didn't encrypt(?).[/COLOR]

[COLOR=Blue]If the LiveCD session won't let you read them then ```
sudo chmod 777 *.txt
``` will turn all text files readable by everyone, you can attach them and then issue same command with 700 instead of 777 to make them readable only to your 'logged in' self.[/COLOR]

---

### Post by preston collins on 2010-11-20
> **Crusty Old Fart said:**
> Howdy Rob:

Thanks for taking the time to write all that up. It helps a lot to know where your head is taking the thread rather than trying to guess at it based on where it's been.
Thanks for that. It's been added to Post #111.

Really? Are you saying that if Preston doesn't have anything connected to the integrated card, and the monitor is connected to the Nvidia card, the BIOS cannot be accessed? I seem to recall that when Preston was running Windows XP, the Nvidia card ran fine, all by itself. At least, I think it did. It's hard to remember if he was running one or two monitors with XP. I never thought to ask him if he had no access to his BIOS before XP's boot process began.

So much of where the focus is now involves the desire to disable the integrated card somehow. If we REALLY need to do that, it makes me wonder how XP did it. And if XP didn't disable the integrated card somehow, maybe Ubuntu doesn't need to either.

Just thinking...

I wonder if anything could be learned by having Preston boot up XP with the dual head setup you guys have now, and taking a look at the display properties in XP.

Hey srry ive been away for a bit the weekend here is crazy for work.

when i was running xp i couldnt see the bios boot up when i had the tv hooked up to the nvidia dvi port, i could only see it when i had the tv connected to the onboard vga

---

### Post by robsoles on 2010-11-20
> **preston collins said:**
> Hey srry ive been away for a bit the weekend here is crazy for work.

when i was running xp i couldnt see the bios boot up when i had the tv hooked up to the nvidia dvi port, i could only see it when i had the tv connected to the onboard vga

We all have things that may get in the way of being able to respond too quickly, don't worry about it.

I thought so, regarding boot-up etc under Windows.

So, how does what go when you follow the seven steps posted by Jocko and embellished by me?

---

### Post by Crusty Old Fart on 2010-11-21
> **robsoles said:**
> We all have things that may get in the way of being able to respond too quickly...

I believe those "things" are called: lives. 8)

---

