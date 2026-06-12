---
title: "what is tty1 &amp; why do you get stuck in it"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by wildman424 on 2010-12-16
I have a problem I'm stuck I upgrade from the 10.04 LTS to 10.10 and after the reboot tty1 launches and I'm locked out of my desktop there's no GUI 

[LIST]
[*]what is tty1
[*]why do you get stuck in it
[*]how do you get rid of it
[/LIST]

:?  :?

---

### Post by owiknowi on 2010-12-16
for what tty means and its use see:
[http://en.wikipedia.org/wiki/Tty_%28Unix%29](http://en.wikipedia.org/wiki/Tty_%28Unix%29)

---

### Post by Hippytaff on 2010-12-16
To exit tty1 press CTRL+ALT+F7
 
Edit -> I should have read the post thoroughly.
 
What graphics card to you have?
 
And welcome :-)

---

### Post by karthick87 on 2010-12-16
Welcome to ubuntuforums :)

What you get when you type the following in your cpnsole,
```
sudo service gdm start
```

---

### Post by nothingspecial on 2010-12-16
Sounds like a graphics card problem maybe.

Get a wired internet connection

Log in

type

```
sudo apt-get update && sudo apt-get upgrade
```

Then type

```
jockey-text
```

and see if there are any drivers you need.

---

### Post by Hippytaff on 2010-12-16
> jockey-text
That's a new one for the notes :-)

---

### Post by gamblor01 on 2010-12-16
You definitely do not want to get rid of tty1.  Usually there are many running and you can press CTRL, ALT, and a function key to switch between them.  To access tty1 you would press CTRL+ALT+F1, for tty2 it's CTRL+ALT+F2, and so on.  tty7 or tty8 should probably be the default one where your X server is running.

If you're running gnome then the file /etc/init.d/gdm is supposed to linked to different runlevels which causes gnome to start, though it appears to have been converted to an upstart job and I'm not too familiar with those.

Try launching gdm manually as suggested to see if gnome starts at all.  If not, it's probably an issue with your X config (/etc/X11/xorg.conf) and you might be able to run this command to fix the issue:

```
sudo dpkg-reconfigure xserver-xorg
```


If gnome does start up then your X settings are fine but something got removed from a link somewhere.  Does the file /etc/X11/default-display-manager contain /usr/sbin/gdm?  For example, on my system:

```
$ grep "gdm" /etc/X11/default-display-manager 
/usr/sbin/gdm
```

---

### Post by wildman424 on 2010-12-16
> **karthick87 said:**
> Welcome to ubuntuforums :)

What you get when you type the following in your cpnsole,
```
sudo service gdm start
```
I get 
```

start: job is already running: gdm

```

---

### Post by nothingspecial on 2010-12-16
oops, bit more detail......

```
sudo jockey-text -l
```

To search for available drivers.

If anything shows up

```
sudo jockey-text -e driver
```

To enable it.

Change driver for the name of the driver (the first bit (before the dash))

---

### Post by wildman424 on 2010-12-16
> **gamblor01 said:**
> 

```
$ grep "gdm" /etc/X11/default-display-manager 
/usr/sbin/gdm
```

i get file or directory doesn't exist

---

### Post by Hippytaff on 2010-12-16
try 
```

cat /etc/X11/default-display-manager

```
 
Did you install the minimal or server version of Ubuntu?

---

### Post by wildman424 on 2010-12-16
> **nothingspecial said:**
> oops, bit more detail......

```
sudo jockey-text -l
```To search for available drivers.

If anything shows up

```
sudo jockey-text -e driver
```To enable it.

Change driver for the name of the driver (the first bit (before the dash))
it shows nvidia_96 - nvidia_96 (proprietary, Enabled, Not in use)
when use the -e paranmeter ```
I get unknown driver: nvidia_96
```
and a long strand of directorys followed by ```
could not open display
```

---

### Post by wildman424 on 2010-12-16
> **Hippytaff said:**
> try 
```

cat /etc/X11/default-display-manager

```Did you install the minimal or server version of Ubuntu?
I had standard 10.04 LTS but had an option available last night for an upgrade to 10.10 when I checked for updates so I said ok and clicked the upgrade button something now I'm wishing I hadden done I was content with the way I had it

---

### Post by wildman424 on 2010-12-16
I just made a new install disk for 10.04 I'm going to boot off it to rescue my personal files maybe I can get more access to the distro I have installed and shed some light on this mystery

---

### Post by nothingspecial on 2010-12-16
Did you try rebooting?

```

sudo reboot
```

---

### Post by wildman424 on 2010-12-16
rebooted still stuck in tty1

---

### Post by wildman424 on 2010-12-16
can I rescue it from an installation disc?

---

### Post by amsterdamharu on 2010-12-16
Hold on, don't re install just yet. I think this is a known problem.

First stop gdm (gnome login thing)
```
sudo service gdm stop
```Then please see the output of:
```
lsmod | grep nou
```If it has a loaded nouveau driver then you can unload it during boot, that should fix your problem (it shows something with nouveau).

Now edit the grub in default
```
sudo nano /etc/default/grub
```There is a line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```Change it to
```
GRUB_CMDLINE_LINUX_DEFAULT="nouveau.modeset=0 rdblacklist=nouveau blacklist=vga16fb nouveau.noaccel=1"
```Press control + o -> enter -> control + x

Run one more command
```
sudo update-grub
```Now press control + alt + delete to restart and see if that fixes anything for you.

---

### Post by amsterdamharu on 2010-12-16
After some digging around I found another solution, the previous post solved it for me but this can work as well:
Remove nvidia drivers -> install nouveau -> reboot and let Ubuntu detect your videocard when you're running the desktop -> install the new drivers -> reboot.

Note that you can press tab to autocomplete your command and double tab to show suggestions:
if you type apt-g(tab) it will complete to apt-get you type apt-get purge nvidia-c(tab) it completes to apt-get purge nvidia-common

Remove nvidia
```
sudo apt-get purge nvidia-common
```Install nouveau and remove the xorg.conf
```
sudo apt-get install xserver-xorg-video-nouveau
sudo rm /etc/X11/xorg.conf
```Make sure you undo the changes you made in /etc/default/grub
```
sudo nano /etc/default/grub
```Restore the line GRUB_CMDLINE... to[FONT=monospace]
[/FONT]```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```Reboot

---

### Post by wildman424 on 2010-12-16
ok I started the first solution got to nano I have **/ect/default/grub** at the top of the screen in the title bar does that mean I successfully open the file ? I don't see any commands except the commands at the bottom for nano

---

### Post by Hippytaff on 2010-12-16
If the file is empty it means you just created a file called grub. You can do CTRL+X to exit without saving it. I think the file your looking for is grub.cfg (I can't check...not at my ubuntu box)

---

### Post by wildman424 on 2010-12-16
I started the second fix got to nano its a blank screen looks like the file is blank
what should I do now

---

### Post by wildman424 on 2010-12-16
> **Hippytaff said:**
> If the file is empty it means you just created a file called grub. You can do CTRL+X to exit without saving it. I think the file your looking for is grub.cfg (I can't check...not at my ubuntu box)
it looks blank as well this can't be good 
:(

grubs the boot loader right

---

### Post by wildman424 on 2010-12-16
ok I been looking through the directories I found grub its there but when I bring it up with nano I don't see any contents ???

---

### Post by Hippytaff on 2010-12-16
do
```

cat grub

```
any output?

---

### Post by wildman424 on 2010-12-16
> **Hippytaff said:**
> do
```

cat grub

```any output?
you mean run ```
 cat grub
``` from a cmd line
yes is this the output your looking for
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE=""

```
followed by a list of notes with # starting each line

---

### Post by Hippytaff on 2010-12-16
so ```
nano grub
``` should open this file for you to edit.
 
I notice the file is a bit sparce. Can't post mine as a comparison, not at home. Will do after work.

---

### Post by Elfy on 2010-12-16
Could be that /ect/default/grub is your issue 

try spelling it correctly :)

/etc/default/grub

---

### Post by wildman424 on 2010-12-16
oops guess spelling it correctly would help I make the same mistake with Windows all the time :oops:
ok I got it open with nano here is the contents
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian'
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```

---

### Post by wildman424 on 2010-12-16
ok since we figured out what was up with grub I ran the fix in post #19 rebooted and it still booted into tty1

---

### Post by wildman424 on 2010-12-16
ran the fix in post #18 rebooted and it still booted into tty1

I'm going to change the line in grub back to what it was before I ran that last fix attempt

---

### Post by wildman424 on 2010-12-16
I'm still stuck in tty1 I have no desktop no way to copy my files off of it I have no access other that tty1 
I been messing with this thing all day and still haven't got any thing fixed now I'm irritated

---

### Post by nothingspecial on 2010-12-16
Ok, if you have a external drive, plug it in

Then type```
 sudo fdisk -l
```

Work out which /dev/sd?? is your external drive, probably /dev/sdb1

```
sudo mkdir /mnt/drive
```

```
sudo mnt -t ??? /dev/sd?? /mnt/drive
```

Change the question marks after -t to what ever the filesystem of the external drive is (ntfs, ext3, ext4 - note for fat drives use vfat)

eg

```
sudo mnt -t vfat /dev/sd?? /mnt/drive
```

or

```
sudo mnt -t ext3 /dev/sd?? /mnt/drive
```

Change the question marks after sd to the letter and number you found out from fdisk -l

Now you copy your stuff across

```
cp -rv ~/Music /mnt/drive
```
```

cp -rv ~/Pictures /mnt/drive
```

etc etc

If you don`t understand post back

---

### Post by Elfy on 2010-12-16
> **wildman424 said:**
> ran the fix in post #18 rebooted and it still booted into tty1

I'm going to change the line in grub back to what it was before I ran that last fix attempt

Did you try post #19 - that will remove nvidia and use nouveau.

> **wildman424 said:**
> I'm still stuck in tty1 I have no desktop no way to copy my files off of it I have no access other that tty1 its a worthless piece of junk that might as well be a paper weight 
THIS IS BULLSH**T  :mad::mad::mad::mad::mad::mad::mad::mad:

I been messing with this thing all day and still haven't got any thing fixed now I'm irritated

This is not likely to get people to help.

---

### Post by wildman424 on 2010-12-16
I apologize for my temper this morning its been one of those day,I appreciate every ones help thank you all I'm going to tr a few more things if it don't work Ill just reformat and start over

---

### Post by amsterdamharu on 2010-12-16
Hi wildman, sorry I wasn't here to help you out earlier. I went to bed and now I soon have to go to work. I know how frustrated it is to get stuck and more frustrating to find and try solutions that don't work for you. I have had my fair share of it and know the feeling. 

If you're going to try out removing nvidia drivers and use nouveau than I have a tip for you using the Linux terminal.  Use the tab, for example I want to type nano /etc/default/grub  I type "nan(press tab)" 
It will complete to "nano" 
continue typing "nano /et(press tab)" 
It will complete to nano /etc/ .. 
If there are more than one option available then try pressing tab twice it will give you a list of available options.
nano /etc/d(tab twice) will give you a list of options  If this solution doesn't work then try to boot off a live CD to copy your files. Live CD is the installation cd when you choose the "try ubuntu" option in the startup menu.

---

### Post by gamblor01 on 2010-12-19
Just FYI, another way to copy stuff off of the disk easily is the scp ***mand.  It's syntax is essentially the same of the cp ***mand, but it does the copy over an SSH connection.  So if you have another system with some spare space you can install an SSH server on your Ubuntu system like so:

```

sudo apt-get install openssh-server

```

Then go to your other system and you can do something like:

```

scp -r [COLOR=Red]wildman[/COLOR]@[COLOR=Red]192.168.0.6[/COLOR]:~/Music .

```


You'll need to replace the stuff in red with values appropriate for your network (i.e. your username in Ubuntu as well as the correct IP address for your system).  In any case, the above ***mand basically says to copy the ~/Music directory over recursively to the current working directory.

If you have a gigabit connection between the two systems then this should go rather quickly (I get around 27-28 megabytes per second copying large files...yes megabytes and not megabits!).

---

