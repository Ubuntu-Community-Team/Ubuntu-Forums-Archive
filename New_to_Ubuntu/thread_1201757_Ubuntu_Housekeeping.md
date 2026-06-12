---
title: "Ubuntu Housekeeping"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by steigerjb on 2009-07-01
I need to do some Ubuntu Housekeeping so to speak. I probably should post separate threads but oh well.

1. Update Manager - I don't know if it is just me but with Jaunty there is no arrow icon on my top panel that lights up when there's updates/upgrades to install. The update manager just pops up every so often showing updates to install. It's kinda annoying. Can I get the arrow thing back?

2. Grub - I made my own grub using the background image from jaunty's new human login screen. Problem is, the grub highlight color seems to be black so I can't tell which choice is selected. How can I make the highlight color brown or white?

3. Clean up Home Folder - See my home folder ([http://i43.tinypic.com/21amfef.png]("http://i43.tinypic.com/21amfef.png") There are extra folders these days after compiling extra compiz plugins, installing google earth,... Is there a way to maybe hide the red circled stuff. idk what the blue circled stuff is.

Thanks for helping me clean my Ubuntu house :lolflag:

---

### Post by jmszr on 2009-07-01
steigerjb,
 
!.) [http://maketecheasier.com/remove-the-annoying-update-manager-pop-up-in-ubuntu-jaunty/2009/06/18](http://maketecheasier.com/remove-the-annoying-update-manager-pop-up-in-ubuntu-jaunty/2009/06/18)   also, post #8 in this thread: [http://ubuntuforums.org/showthread.php?t=1141398](http://ubuntuforums.org/showthread.php?t=1141398)

2.) Don't know

3.) Put a (.) in front of the folders you want to be hidden.

---

### Post by LowSky on 2009-07-01
2) startup manager it in add/remove and synaptic, it has options to configure grub

---

### Post by steigerjb on 2009-07-01
> **jmszr said:**
> steigerjb,
 
3.) Put a (.) in front of the folders you want to be hidden.

google earth doesn't work now

---

### Post by steigerjb on 2009-07-01
> **LowSky said:**
> 2) startup manager it in add/remove and synaptic, it has options to configure grub

it didn't change anything

---

### Post by SaaTeeVaaGreen on 2009-07-01
3. google earth probably doesnt work now because it is looking for a folder called 'google-earth' but the folder is now called '.google-earth'. i dont know google earth very well, are you able to tell it the new folder name so it knows where to look? that should get it working again.

---

### Post by scorp123 on 2009-07-01
> **steigerjb said:**
>  3. Clean up Home Folder ... There are extra folders ....  Those folders are supposed to be there. That's where all the programs you use keep their settings. Don't mess with this unless you know what you do. And please let go of your Windows habits. "I need to cleanup folders... " is sooooo Windows-ish. It's almost a miracle you have not asked about disk defragmentation and anti-virus tools yet :lolflag:

(just kidding of course, please don't take me wrong, OK?  :)   )

---

### Post by ibuclaw on 2009-07-01
> **steigerjb said:**
> google earth doesn't work now
Rename those files from '.google earth' back to their original name.

What you should do instead is create a new file named:
```
.hidden
```
inside your home directory, and put in all the names of files/folders you want hidden in that file

ie:
```

freewins
google-earth
rubik
stackswitch
googleearth
Software.ini

```

For each directory you want files to be hidden, you'll have to create a new **.hidden** file.

Regards
Iain

---

### Post by ibuclaw on 2009-07-01
> **steigerjb said:**
> 2. Grub - I made my own grub using the background image from jaunty's new human login screen. Problem is, the grub highlight color seems to be black so I can't tell which choice is selected. How can I make the highlight color brown or white?

Can you paste your /boot/grub/menu.lst file either here or in a [pastebin]("http://paste.ubuntu.com")?

```
gedit /boot/grub/menu.lst
```

Regards
Iain

---

### Post by steigerjb on 2009-07-01
> **tinivole said:**
> Can you paste your /boot/grub/menu.lst file either here or in a [pastebin]("http://paste.ubuntu.com")?

```
gedit /boot/grub/menu.lst
```

Regards
Iain

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color white/black white/brown

#A splash image for the menu
splashimage=/boot/grub/splashimages/background.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=83283067-1542-4b2f-bb45-79ab3da0e1c1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=83283067-1542-4b2f-bb45-79ab3da0e1c1

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04 Jaunty Jackalope
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-13-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista Home Premium
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


```

---

### Post by ibuclaw on 2009-07-01
Attached should be the result from your colour combination.

What type of background are you using?

---

### Post by steigerjb on 2009-07-01
> **tinivole said:**
> Attached should be the result from your colour combination.

What type of background are you using?

I have a xmp image as my background image

---

### Post by ibuclaw on 2009-07-02
Ah, that changes everything.

Try this new one I just made up.


Regards
Iain

---

### Post by steigerjb on 2009-07-02
> **tinivole said:**
> Ah, that changes everything.

Try this new one I just made up.


Regards
Iain

umm, it's all whitey.

---

### Post by sadaruwan12 on 2009-07-02
> **steigerjb said:**
> I
1. Update Manager - I don't know if it is just me but with Jaunty there is no arrow icon on my top panel that lights up when there's updates/upgrades to install. The update manager just pops up every so often showing updates to install. It's kinda annoying. Can I get the arrow thing back?

2. Grub - I made my own grub using the background image from jaunty's new human login screen. Problem is, the grub highlight color seems to be black so I can't tell which choice is selected. How can I make the highlight color brown or white?

3. Clean up Home Folder - See my home folder ([http://i43.tinypic.com/21amfef.png]("http://i43.tinypic.com/21amfef.png") There are extra folders these days after compiling extra compiz plugins, installing google earth,... Is there a way to maybe hide the red circled stuff. idk what the blue circled stuff is.

1. Go to System -> Administration -> Software Sources and click on update tab and see which option have been selected just select the last option to get your arrow notification back.

2. Just stop beating around the bush and just use startup-manager with this you can edit the grub screen with out getting in to trouble and do lots more with too.
Open the terminal and enter,

```
sudo apt-get install startup-manager
```

3. Don't clean it 'cos those folders needs to be there thats the reason why your Google earth is not working just put every thing back to the way they where and your earth will start working

---

### Post by steigerjb on 2009-07-02
> **sadaruwan12 said:**
> 1. Go to System -> Administration -> Software Sources and click on update tab and see which option have been selected just select the last option to get your arrow notification back.

2. Just stop beating around the bush and just use startup-manager with this you can edit the grub screen with out getting in to trouble and do lots more with too.
Open the terminal and enter,

```
sudo apt-get install startup-manager
```

3. Don't clean it 'cos those folders needs to be there thats the reason why your Google earth is not working just put every thing back to the way they where and your earth will start working

where is software sources?

i am using startup manager

---

### Post by ibuclaw on 2009-07-02
> **steigerjb said:**
> umm, it's all whitey.

Oh really? Whoops ...

Don't know what happened there.

Patched!


You'll probably say that it is a "bit greyie" now ... but that is near enough as dark as it can get without you not being able to distinguish between the two.

I've also attached the alpha version of the jaunty login png too, so you can tweak it (just open it in GIMP, add a layer to the bottom, and put it in a darkish colour, save it as a png, then run
```
convert -resize 640x480 -colors 14 bootsplash.png bootsplash.xpm
gzip bootsplash.xpm
```
Then copy/move it to it's designated place).

I've also attached a picture of what it should look like too.

Regards
Iain

---

### Post by sadaruwan12 on 2009-07-02
The path is there follow and see friend and use Gnome look you can find lot's off goodies there.

---

### Post by steigerjb on 2009-07-02
> **tinivole said:**
> Oh really? Whoops ...

Don't know what happened there.

Patched!


You'll probably say that it is a "bit greyie" now ... but that is near enough as dark as it can get without you not being able to distinguish between the two.

I've also attached the alpha version of the jaunty login png too, so you can tweak it (just open it in GIMP, add a layer to the bottom, and put it in a darkish colour, save it as a png, then run
```
convert -resize 640x480 -colors 14 bootsplash.png bootsplash.xpm
gzip bootsplash.xpm
```
Then copy/move it to it's designated place).

I've also attached a picture of what it should look like too.

Regards
Iain

I'll try it out.

yeah, idk how to do layers in gimp. Besides, my gimp doesn't work. It is missing a box. (see attachment) There's supposed to be three correct?

don't laugh at my desktop, I like leaving it as default

---

### Post by ibuclaw on 2009-07-03
> **steigerjb said:**
> I'll try it out.

yeah, idk how to do layers in gimp. Besides, my gimp doesn't work. It is missing a box. (see attachment) There's supposed to be three correct?

don't laugh at my desktop, I like leaving it as default

Close  GIMP.

Open Nautilus, go to your Home directory, then Press "**Ctrl+H**".
You should see a directory named:
```
.gimp-2.6
```
Delete it.

Then start GIMP again.

Regards
Iain

---

### Post by steigerjb on 2009-07-03
> **tinivole said:**
> Oh really? Whoops ...

Don't know what happened there.

Patched!


You'll probably say that it is a "bit greyie" now ... but that is near enough as dark as it can get without you not being able to distinguish between the two.

I've also attached the alpha version of the jaunty login png too, so you can tweak it (just open it in GIMP, add a layer to the bottom, and put it in a darkish colour, save it as a png, then run
```
convert -resize 640x480 -colors 14 bootsplash.png bootsplash.xpm
gzip bootsplash.xpm
```
Then copy/move it to it's designated place).

I've also attached a picture of what it should look like too.

Regards
Iain

Alright, that pic works fine.

> **tinivole said:**
> Close  GIMP.

Open Nautilus, go to your Home directory, then Press "**Ctrl+H**".
You should see a directory named:
```
.gimp-2.6
```
Delete it.

Then start GIMP again.

Regards
Iain

There we go again! You rock, gimp back to normal! :lolflag:

:-k Now if you really **wanna** help me. Help me get wireless working: [http://ubuntuforums.org/showthread.php?t=1184929]("http://ubuntuforums.org/showthread.php?t=1184929") I can't get it to save my life. :frown:

If you can help with that, you are GOD ):P

---

