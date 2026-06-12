---
title: "Ubuntu 10.10 CD does not boot -- blank screen-"
date: 2010-10-23
forum: New to Ubuntu
---

### Post by anneg on 2010-10-23
I have downloaded ubuntu 10.10 ISO

burned it to two different CDs with two different burners on a computer that I have used before to burn disks ok.

Neither disk boot up on my dell latitude e4310.

If I look at the CD from vista or windows 7 the program starts and ask about install.
I see a bunch of folders and applications. 

I have ubuntu 10.04 installed with wubi, and that works ok. I can boot from hard disk into ubuntu. 

What could be the problem?

---

### Post by terdon on 2010-10-27
Hi, have you checked the boot device priority in your BIOS? Have a look at [http://www.hiren.info/pages/bios-boot-cdrom]("http://www.hiren.info/pages/bios-boot-cdrom")

---

### Post by anneg on 2010-10-27
I have booted from live CDs before. I hit F12 before the computer starts and it gives me an option to boot from cd/dvd. So that's what I do. 

I don't think I need to change the bios to make the dvd be first option in bootup.

---

### Post by terdon on 2010-10-27
Oh. So despite having chosen to boot from cd, the cd is ignored? That is strange... 

I would try changing the boot priority in the bios just in case though.

 Otherwise, I can only think that there is a problem with (both!) your cds. Not very likely,I know.

---

### Post by Terl on 2010-10-27
> **anneg said:**
> I have booted from live CDs before. I hit F12 before the computer starts and it gives me an option to boot from cd/dvd. So that's what I do. 

I don't think I need to change the bios to make the dvd be first option in bootup.

What do they do?  Does the pc bypass the cd even though you hit the F12 (I have a Dell too) and select cd?  Or does it try to boot and hang?

To rule things out:  Did you check the md5sum after download?  Will it boot in another computer?  If it will not boot anything I would try to redownload and burn again.

---

### Post by anneg on 2010-10-29
I used the DVDinfopro to confirm that the two 10.10 ISO discs I burned at max speed are identical to a new download of 10.10 ISO -- Can a disc burned at max speed be a problem even if it is identical? 

I get to a first purple screen with like a battery = a little man. Than the screen goes blank
but then I see nothing more. I just hear disk noises. 

I changed the bios to boot from CD in priority. the same thing happens, it just hangs.

I downloaded 10.04 and burned to disk at speed 1. 
I used F12 to boot from CD. 
The disk took for ever to boot up but it moved fairly quickly to a purple screen with Ubuntu and moving dots and eventually I got to a menu so I could  run Ubuntu from the 10.04 CD. 

Is there a way to catch errors from the failed bootup with the 10.10 CD so I can provide more info to the Ubuntu community about this?

---

### Post by ssing on 2010-10-29
I am also having the same issue. Tried installing on Latitude E6510. Get a black screen when booting from the CD. I download couple of times and burned on 4 CD but the result was same.

---

### Post by Omnomnom on 2010-10-29
Just out of interest, did you set your boot priority to all the disk drives above the hard drive?

---

### Post by anneg on 2010-10-29
Yes, I put CD/DVD then Hard Disk then USB 

My computer is a recent laptop.

---

### Post by Omnomnom on 2010-10-29
Oh, that's quite odd then. When you say laptop, do you mean laptop, or a netbook?

---

### Post by anneg on 2010-10-29
It is a laptop, latitude E4310

[http://www.dell.com/us/en/enterprise/notebooks/latitude-e4310/pd.aspx?refid=latitude-e4310&cs=555&s=biz](http://www.dell.com/us/en/enterprise/notebooks/latitude-e4310/pd.aspx?refid=latitude-e4310&cs=555&s=biz)
[URL="http://www.dell.com/us/business/p/latitude-e4310/fs?refid=latitude-e4310&ST=latitude%20e4310&dgc=ST&cid=57659&lid=1474319&acd=58857,8,0,105313396,771763475,1288402345,,25688701,5750901897"]
[/URL]

---

### Post by texasboy2084 on 2010-10-30
I am having this same problem I press 10 to go to boot menu and select boot from cd/dvd and i get to the battery (i guess that what it is) with the little man and just get a black screen.

---

### Post by jjaakkol on 2010-11-01
A bit same kind of issue:

1. CD burned with InfraRecorder (Actions- Burn Image -OK to popup)
2. CD inserted in CD drive and PC rebooted (Fujitsu Siemens Esprimo Mobile V6515)
3. Ubuntu text and white/red dots (looks like Ubuntu is loading)
4. Then just background picture on display and mouse pointer, nothing else.

I do not get any Welcome window where I could select language as mentioned here:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by elkinsj210 on 2010-11-01
Similar problem, the live cd will load to a purple screen with two low res, white icons at the bottom of the screen and then it will go to a black screen with the blinking cursor at the top left of the screen and then it turns completely black.  I have found that by changing the top two boot parameters that Ubuntu will load but that I am missing key features such as power management.  I attempted to go back to 10.04 but the same thing occurred.  I am wondering if the new linux kernal is to blame.

---

### Post by jjaakkol on 2010-11-02
I tried Ubuntu CD at work: laptop is IBM T41 and CD is OK. :)

This same CD does not work in my home laptop Fujitsu Siemens Esprimo Mobile V6515. I waited yesterday about half an hour but I only got purple background and mouse pointer...

---

### Post by 4Orbs on 2010-11-02
When you reach the purple screen, hit the space bar on your keyboard. Maybe it will open a menu with the option to boot in "Compatibility Mode". Try that and see if it will take you to the live cd desktop. I don't know if the Ubuntu cd includes that option, but the Mint cd does, and I'd guess Ubuntu also has it.

---

### Post by jjaakkol on 2010-11-02
Did not help. In fact any key did not helped. No windows popped up.

During boot I can see some "load text" if I press F1. 

It complains about "user id not found" (something like that can't remember exactly)

And also complains about some favourite_list....(could not found....)

Too bad that can not remember more detailed...I will check it again later... :)

---

### Post by jjaakkol on 2010-11-02
Ok, I got some extra now.

During boot from CD when this display shows up press F1

[]("http://pricklytech.files.wordpress.com/2010/07/ubuntu-boot-01.png")[IMG]http://pricklytech.files.wordpress.com/2010/07/ubuntu-boot-01.png[/IMG]

There is some kind of boot setup menu?? Language is there, 
keymap at least have not tried all yet. :)

You can also choose install Ubuntu etc. 

I tried "Try Ubuntu without installing" but boot was halted. It is halted in this line:

saned disabled; edit /etc/default/saned

Previous line is : Pulse audio configured... (some extra text)

Could someone explain what are these?

First line when boot start is:
(process 365): GLid warning get pwduid_r() failed due to unknown user id (0)

There are also complains before halt point:

No value set for /app/netbook-launcher/favorites/favorite_list
No value set for key /app/netbook-launcher/favorites/favorite_list

---

### Post by jjaakkol on 2010-11-03
I tried yesterday "install ubuntu" it did not work either. Same symptoms like "try ubuntu without installation"

---

### Post by Clever_Username on 2010-11-03
Personally, I've never had much luck with the cd. I've never had a problem when I install from usb though. Just a thought.

---

### Post by jjaakkol on 2010-11-03
> **jjaakkol said:**
> I tried yesterday "install ubuntu" it did not work either. Same symptoms like "try ubuntu without installation"

This I have to try today:

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

:)

---

### Post by hiddensphinx on 2010-11-03
same problem here on older computer

1. Upgraded 10.04 to 10.10 :popcorn:
2. linux kernel 2.6.35-22 gives blank screen with blinker on top left :(
3. linux kernel 2.6.32-25 loads fine :P

---

### Post by jjaakkol on 2010-11-03
> **jjaakkol said:**
> This I have to try today:

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

:)

Ok, status update :)

1. USB installation "failed" same way as CD install, only background graphic and mouse pointer
2. Tried with different resolution 1024x768, no hope (my display is 1280x800)
3. Tried previous version 10.04 also from USB, same result than 10.10 but now I got grey box in the middle of screen. Welcome window maybe? There was no text inside grey box.

---

### Post by jjaakkol on 2010-11-06
Finally I got my Ubuntu working. :grin:

UBUNTU installed  with "Alternative downloads" from CD
[http://www.ubuntulinux.org/desktop/g...ative-download]("http://www.ubuntulinux.org/desktop/get-ubuntu/alternative-download")
  
After that I did not have any desktop installed, only prompt. (install of "applications" failed or something like that, I just continued to install rest)

 From prompt I installed desktop with "sudo apt-get install ubuntu-desktop" but desktop was still not working. 
But from Grub2 I could choose Recovery mode for Ubuntu

So solution was:

1. picked up NVIDIA graphic card driver matching to laptop hardware from NVIDIA site to USB stick
2. Started ubuntu with recovery mode

In recovery mode you need to give command to be able to install driver:
3. telinit 3 (it will ask your username and psw what you gave in installation)
4. mkdir /media/usb
5. mount -t /dev/sdb1 /media/usb (you can check your usb stick "dev name" with sudo fdisk -l)
6. cd /media/usb/linux (I had driver in linux directory)
7. sudo ./NVIDIA-Linux-x86-260.19.12.run
Installation should start. I just followed instructions.
8. sudo reboot- f
9. Start Ubuntu in normal mode.

Desktop is OK now! So my problem was in the end that graphic driver in  Ubuntu installation "package" was not compatible with my hardware.

---

### Post by Tasty Bacon Vortex on 2010-11-06
I had problems loading from the CD and USB. The CD nor the USB would boot even after adjusting the BIOS but while trying the CD again with only a blank screen visible, I stuck in the USB and Ubuntu 10.10 Netbook loaded off the USB.

---

### Post by m4tic on 2010-11-06
For the blank screen problem, press enter multiple times till the processor light starts working. i got through that stage but the darn thing gives an error on all my computers. i've downloaded the .iso 4 times and wasted 9cds nothing works

---

### Post by Mka on 2010-12-09
I am having the same problem right now. Using Dell Latitude E5500. When booting/installing the alternate dvd, I get the purple screen (splash) with progress indicating dots, they took more than 10 minutes without noticeable progress, I had to intervene and do a forced shutdown.

---

### Post by Mka on 2010-12-09
More info into this. I have run the command 'md5sum -c md5sum.txt' inside the /media/cdrom directory (with dvd mounted) and I got the errors and warnings as attached.

Looks like casper/filesystem.squashfs file cannot be read at all.

---

### Post by greybeard62 on 2010-12-10
OK,  I have installed 10.10 on two laptops, lenovo X61 and a Toshiba.  Tonight I got a new Lenovo Ideapad U160, i5-470um.  Changed setup to boot from CD, put in the SAME cd which booted and loaded (although slow as dirt) in the other two and nada, nuttin.  Get the same symptoms mentioned, little battery thing, then a long time bumping the CD, then blank - nothing.  Then I tried the 10.04 CD which also booted on many laptops, same thing - nothing.  So, perhaps something is amiss with the new machines???  I also noted the HD had option for pwd and reset that to blank.  Hit all the keys many times, nothing else happens.  I refuse to be stuck with Win 7 mess.  Anybody got any ideas yet?  Since I'm holding two CD's which booted in other machines it ain't the CD guys and I'm running out of thoughts here.

---

### Post by hiddensphinx on 2010-12-13
I have decided to go back to 9.10...that seems to work best on my older machine running ATI X850 graphics card :(

no more load problems!

---

### Post by robert shearer on 2010-12-13
When the purple screen first appears press enter then enter again to set language.

Then press F6 and scroll down and select 'nomodeset' (enter selects,
Esc returns you to the main menu.

Now you will see a line of white text near the bottom of the screen with a blinking cursor.
use the backspace key to erase **back to and including** "quiet splash"
Then hit enter to boot.

note..nomodeset should allow you to get a gui even if you have an odd graphics hardware problem.

removing quiet splash will produce a line by line display of the boot process instead of the usual 'counting dots' splash screen.

if the boot hangs at any point note the line of text onscreen when this happens and post. Include any other error messages. Check the links below first as any errors may be covered there already.

Good luck.:)


[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

### Post by acovrig on 2011-04-09
I am trying to install to a toshiba w/an ati card; I downloaded desktop and alternate isos from the torrent on the site, burned them,burn is ok (I ran the 'check disk for defects' on another computer).  Desktop: get the battery-person, press Ctrl Alt and get the menu, press English, choose anything but Memtest and i get the underscore top-left, then nothing.  Alternate skipps the battery-man screen, but same results, not even cmd-line install works.  If I boot into 8.04 (yes, its old, but I couldn't update for a long time) and try to update from the cd (sudo /media/cdrom/updatesomething.sh)I get python errors.  I maynot support USBboot cuz it ignors it and boots hdd-and yes I picked USB at boot.  I may try something from a pendrivelinux.com, burn someting to cd, then pick usb to force usb boot.  I can boot from CD though cuz I booted GParted just fine.  I am thinking about installing 9.01

---

