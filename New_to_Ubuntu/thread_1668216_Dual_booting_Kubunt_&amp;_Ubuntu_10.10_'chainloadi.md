---
title: "Dual booting Kubunt &amp; Ubuntu 10.10 'chainloading'"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by heron7 on 2011-01-16
I installed Kubuntu & Ubuntu10.10 from a triple boot cd . I want to get used to using KDE while keeping the gnome separate. Initially it was Bt4 RC1'love the dragon',but for a newbie ..who up to six mounths did'nt know what reboot actually meant :( dir or registry ?..so i've come some way.

 After the installation i could only boot in Ubuntu & managed a screenshot to show what's where ,Kubuntu is on /dev/sda1  .
        &,Ubuntu  on /dev/sda 6
though two swap partitions where made only one boot in sda1 
 &    one  root with Ubuntu.
 I have found out about chainloading, but if i need to add a bootloader to one or root to the other. 
 I can't edit grub menu while at booting screen,because my keyboard keys don't match.and i tried to edit menu.lst:
  sudo gedit /boot/grub/menu.lst 

but it shows up empty,there was no paragraph to add the three lines of code to .
titel:Kubuntu
root (hd0,?)
chainloader +1
maybe it needs to be mounted first .
i appreciate any clarity

---

### Post by garvinrick4 on 2011-01-16
#It is grub2 not grub legacy:
#Open a terminal in whichever one of your 2 installs boots and;
```
sudo update-grub
```Will run os-prober and make a new grub config and put installs
in the menu entries.
#Can use either sda1 or sda6 to boot with by installing grub to sda looking
for grub files in either one you want.
#As such in Live Cd use either your sda1 install or sda6 install
```
sudo mount /dev/sda1 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
```Boot into and:
```
sudo update-grub
```
Link:
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by heron7 on 2011-01-16
Thanks so fast..  yes i have just installed grub .; but i am looking for the exact name 'place' hd0,0 ? or hd0,1  and i've been needing to ask this but when you show multiple commands under each other you use \n ?..  i.e title \n      root \n     chainloader +1 or  would it look like  : title Kubunt  root (hd0,0)  chainloader +1

---

### Post by garvinrick4 on 2011-01-16
Different ways to find here is one:
```
sudo grub-mkconfig
```
Look at whatever you want in config file:

---

### Post by heron7 on 2011-01-16
Is that my first official bug report ,or just an -option .?

---

### Post by garvinrick4 on 2011-01-16
Looks like there is a space after root -directory=
should have no space after root.
copy and paste the ones in my post:

---

### Post by garvinrick4 on 2011-01-16
You do not have both grub and grub2 installed do you?
If you do you have to purge and reinstall just grub2.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")
Both your installs grub2 in 10.10 so should not have any remnants of grub-legacy
unless dist-upgraded from 9.04 and left grub as legacy.

---

### Post by heron7 on 2011-01-16
Well spotted garvinrick4 ; 
I am somewhat confused with the sda & hd0  & now i noticed fd  too. 
i thought sda & hda where the same thing only one internal & external disk drives.

when you say 'boot into' : after the; 'sudo umount /mnt 'command . 

what do you mean?.. from command line ?.. or exit & reboot & i get to pick Kubuntu from the boot screen?..
  the; vmlinuz 2.6.35.22  & 2.6.35.24 are the kernels of the two distros right?..
& what happened to the chainloader?... or this is just another way of doing it.

---

### Post by garvinrick4 on 2011-01-16
#Boot into Hard Drive and then:
```
sudo update-grub
```It will find your other installs with a package called os-prober and put all
Operating systems into your grub menu.
#You can also run:
```
sudo grub-mkconfig
```That you can watch in terminal it find the other installs and make new config file.
#Run this to see your grub menu entries (grub menu to boot from)
```
grep menuentry /boot/grub/grub.cfg
```
#Link on grub below:
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by heron7 on 2011-01-17
garvinrick4 ; I'm starting to blush , why are all the uuid's the same ?.. and i can't type from grub boot menu my keys don't match.french keyboard ,enlish lang,& Dutch location might have something to do with that. although i'm certain there are ways to fix that too.

I've used all of my asking credit & if i could come over at Canonical & make tea for everyone for a whole week i would. 

well ,it sure feels closer now then last week . I don't want to format,remove the whole partition just for the sake of not giving in.. i still refuse to, remove Kubuntu :(

at the boot menu i have two vmlinuz and a recovery mode for each & memtest.. the only diff is the last digits 2.6.35.22 & 2.6.35.24 ;yet all the uuid's are the same;unless that means same drive.which they are on.
all is 'hd0,msdos6' ,that's where Ubuntu is at.& insmod ext2?... i thought it were ext4 :(
oh,i see that my external drive is plugged in now too with fedora 14 on it; if that effected the out put ?..no i don't think so ,it's not mounted.

---

### Post by heron7 on 2011-01-17
I lost both of them now. I get grub boot menu to edit command line :( stage 1.5
up to not so long ago i thought that all the lines of text on black screen were'nt for my eyes to see.. let alone edit :( why does a bit of white light on a black screen seems such a dodgy place to be in?.. it don't scare me anymore but i still need to know exactly what to punch in.
i must have read five different ways of mending my predicament +1 to simply delete the Kubuntu & try it again with editing the 8'th step of the installation sequence..just read this one other method.
i must have changed the grub config ,the good thing is fedora boots from the external disk 
i had to backup the boot menu.lst first.
i miss my Ubuntu now too.

---

### Post by heron7 on 2011-01-17
i lost everything ,even fedora does'nt boot up anymore i was gonna format the whole disk empty & clean install before the month is even out,not usual. 
cd rom does'nt boot or load either ....
greed to have a third Linux distro ,i guess .without being able to handle 1 
mia culpa ;mia culpa.. :(

---

### Post by heron7 on 2011-01-17
I have rebooted after the last fase i showed up here 'previous post' ,exited because as shown on screenshot with the command grep menuentry  and when i turned the pc on later nothing booted ,not even fedora14 on external drive. 
I found out that m keyboard switches to qwerty while in grub boot menu C-line. & that's as far as it'll go.
I was gonna remove the whole mess i made with the grep command by formatting 'wipe clean' the whole drv from fedora14,but that didnt boot either.
I know only one way to get a clear drive and it's one hell of a long way around but for an 'idiot;always newbie' i am left with the only option of trying a windows cd which i think will clear out grub2 and then reinstall ubuntu over that,sounds crazy :yes :( i have tried a live cd ,it does'nt boot or mnt i don't know what it's supposed to do ,this affair has gone from negligible not available Kubuntu to nothing available . 
If anyone can help please. the alternative is'nt pretty .
p.s. sorry garvinrick4 4 messing up you'r advice & my machine
mia culpa !

---

### Post by heron7 on 2011-01-17
I think i know what happened. grep brought over the grub that fedora uses. i had it  plugged in when i ran that grep command .
I am gonna cheat otherwise now ,instead of windows i can switch the drives 'eurika' :( 
so much for chainloading

---

### Post by garvinrick4 on 2011-01-17
I just believe you have grub-legacy and grub2 installed in internal drive somehow and the Fedora drive comes with grub-legacy. 
CD should always work if CD is choosen first in order of boot. Must get it working so can run this:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")
download above to DESKTOP. Only takes a minute.
Now run below in a terminal and will put a text file on your desktop, copy and paste it to
this thread and after pasted highlight whole thing and hit the # sign in upper right of message box to put in nice little box to read, is long.
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```## Just a matter of purging your grub and reinstalling them in right place.
Not a major thing. Instructions below but post results so we can read:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")
###By the way as you see grub-legacy and grub2 work together like water and oil.
       They do not play together well at all. Good thing it is easily fixable.

---

