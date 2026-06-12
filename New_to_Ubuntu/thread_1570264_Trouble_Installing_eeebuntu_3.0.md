---
title: "Trouble Installing eeebuntu 3.0"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by essartee4 on 2010-09-07
I currently have eeebuntu 2.0 On my Asus Eee PC 1000H so at work today i decided to download the 3.0 version and upon booting it from the USB drive i get a weird display error.

Any ideas?

Ill post a photo in a sec....

---

### Post by jtarin on 2010-09-07
The only idea I have without more information is you've been drinking too much.....hence weird displays.I used to have a GF that gave weird displays after upgrades!And downgrades as a matter of fact. :)

---

### Post by essartee4 on 2010-09-07
Here are some shitty iphone pics of my problemo...

[IMG]http://i46.photobucket.com/albums/f138/drel83/photo2-1.jpg[/IMG]
[IMG]http://i46.photobucket.com/albums/f138/drel83/photo-1.jpg[/IMG]
[IMG]http://i46.photobucket.com/albums/f138/drel83/photo3-1.jpg[/IMG]

---

### Post by jtarin on 2010-09-07
In your terminal issue the command ```
lsmod |grep i9
``` and post the results.

---

### Post by essartee4 on 2010-09-08
> **jtarin said:**
> In your terminal issue the command ```
lsmod |grep i9
``` and post the results.


dsm@dsm-laptop:~$ lsmod |grep i9
i915                   30208  2 
drm                    78248  3 i915
dsm@dsm-laptop:~$

---

### Post by jtarin on 2010-09-08
Try pressing F2 when it starts to boot or try an alternate kernel if you have one listed in Grub.

---

### Post by essartee4 on 2010-09-08
Not sure what an alternate kernel and grub is as im brand new to ubuntu however ill give the F2 a try.

---

### Post by essartee4 on 2010-09-08
No luck with the F2:-x

---

### Post by essartee4 on 2010-09-08
I dont know whats going on but something is not right with my OS

If i go to System>Admin>update manager and attempt an update in my 2.0 version i get a message

"dpkg: dependency problems prevent configuration of libc6-dev
 libc6-dev depends on libc6 (= 2.9-4ubuntu6.2); however:
  Package libc6 is not installed
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured" 

now if i click "start upgrade" anyway in will go to "installing the updates", then throw an error "this script detected the following installed services which must be stopped before the ipgrade : gdm"

Ahhhhhhhhhh

---

### Post by jtarin on 2010-09-08
libc6  is in the repositories.....use Synaptic to take a look. I have "libc6" and " libc6-dev" installed.
You need those. Good catch on the GDM thing.

---

### Post by essartee4 on 2010-09-09
[B]Ok this is really starting to **** me off im about to go to windows....

So last night i downloaded a new [/B]**[B]eeebuntu 3.0**** torrent from a different site.**

Next i downloaded unetbootin-linux-471 to created a bootable usb with the new .iso

I open unetbootin-linux-471 and get an error...
"7z not found. This is required for either install  mode. Install the p7zip-full package or your distributions equivalent"

 N**ext i run **[/B][B](sudo apt-get install mtools) "which is needed for the USB drive install mode of UNetbootin     "

Error messsage pops up
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to configure

Lastly i run: sudo apt-get install p7zip-full
Error message pops up
[/B][B] E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to configure





[IMG]http://i46.photobucket.com/albums/f138/drel83/photo-6.jpg[/IMG]
[/B]

---

### Post by jtarin on 2010-09-09
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by essartee4 on 2010-09-09
Ran Universal-USB-Installer-1.7.9.4

and got this, nothing seems to work.

[/home/dsm/Universal-USB-Installer-1.7.9.4.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/dsm/Universal-USB-Installer-1.7.9.4.exe or
          /home/dsm/Universal-USB-Installer-1.7.9.4.exe.zip, and cannot find /home/dsm/Universal-USB-Installer-1.7.9.4.exe.ZIP, period.


[IMG]http://i46.photobucket.com/albums/f138/drel83/photo-8.jpg[/IMG]

---

### Post by jtarin on 2010-09-09
It might have helped to see that command line output.

---

### Post by essartee4 on 2010-09-09
Nothing seems to work i get an error no matter what i do so im just going to mount the .iso on my work windows pc, sick of messing with Linux.

---

### Post by essartee4 on 2010-09-09
> **jtarin said:**
> It might have helped to see that command line output.
[/home/dsm/Universal-USB-Installer-1.7.9.5.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/dsm/Universal-USB-Installer-1.7.9.5.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/dsm/Universal-USB-Installer-1.7.9.5.exe or
          /home/dsm/Universal-USB-Installer-1.7.9.5.exe.zip, and cannot find /home/dsm/Universal-USB-Installer-1.7.9.5.exe.ZIP, period.

---

### Post by jtarin on 2010-09-09
I saw that almost identical message the other day onsite. The guy had a bad burn. ;)

---

### Post by essartee4 on 2010-09-09
Yet another interesting find, when i go to Applications>add remove it will says 

"checking installed and available applications"

Then i get this fun message

**"Failed to check for installed and available applications**
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

---

### Post by essartee4 on 2010-09-09
> **jtarin said:**
> I saw that almost identical message the other day onsite. The guy had a bad burn. ;)
Bad burn meaning bad copy of the Ubuntu?

---

### Post by jtarin on 2010-09-09
> **essartee4 said:**
> Bad burn meaning bad copy of the Ubuntu?yea, only his was a .rar.

---

### Post by jtarin on 2010-09-09
> **essartee4 said:**
> Yet another interesting find, when i go to Applications>add remove it will says 

"checking installed and available applications"

Then i get this fun message

**"Failed to check for installed and available applications**
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."
You would be wiser to use Aptitude,Synaptic or apt in that order of effectiveness to install or remove software. Much easier to take care of problems with the first two.

---

### Post by essartee4 on 2010-09-09
Well considering i have been using ubutu for a total of about 2 hrs i have no idea what that means. I finally found where the Terminal is hah.

Otherwise ill just do a fresh install with the new .iso i downloaded last night. Just need to use my work windows pc to create a  bootable usb as it seems impossible to do anything on my eeebuntu

I tried to post all my issues in this thread with the code and nothing has been resolved. Any assistance?

---

### Post by essartee4 on 2010-09-09
If i go to Synaptic Package Manager i get error...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

wtf does this mean


I was trying to see if i have the p7zip installed which unetbootin is requiring.

---

### Post by jtarin on 2010-09-09
It gave you the instructions of what to do. In a terminal issue the command```
sudo dpkg --configure -a
```

---

### Post by jtarin on 2010-09-09
> **essartee4 said:**
> 
I was trying to see if i have the p7zip installed which unetbootin is requiring.
Hve you tried [Pendrive Linux]("http://www.pendrivelinux.com/") and use their tool?

---

### Post by essartee4 on 2010-09-09
> **jtarin said:**
> It gave you the instructions of what to do. In a terminal issue the command```
sudo dpkg --configure -a
```
Ya, i did,

dsm@dsm-laptop:~$ sudo dpkg --configure -a
[sudo] password for dsm: 
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.9-4ubuntu6.2); however:
  Package libc6 is not installed.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
dsm@dsm-laptop:~$

---

### Post by essartee4 on 2010-09-09
> **jtarin said:**
> Hve you tried [Pendrive Linux]("http://www.pendrivelinux.com/") and use their tool?
isnt that a .exe file? Can ubuntu open that?

---

### Post by jtarin on 2010-09-09
> **essartee4 said:**
> Ya, i did,

dsm@dsm-laptop:~$ sudo dpkg --configure -a
[sudo] password for dsm: 
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.9-4ubuntu6.2); however:
  Package libc6 is not installed.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
dsm@dsm-laptop:~$Again it tells you what to do...libc6-dev depends on libc6 (= 2.9-4ubuntu6.2); however:
  Package libc6 is not installed. Install the package it ask for, then try again. You have to resolve problems as they come up. it's not always like this. In the Windows world most of these error messages are hidden from you.

---

### Post by jtarin on 2010-09-09
> **essartee4 said:**
> isnt that a .exe file? Can ubuntu open that?

No this is something you will have to do on a Window smachine.

---

### Post by essartee4 on 2010-09-10
I just went with 10.04

at first i loaded the netbook version and could not stand the desktop layout

now i am on the desktop version and everything is running beautiful on my netbook :]

---

### Post by jtarin on 2010-09-10
Excellent! Good for you. :)

---

### Post by essartee4 on 2010-09-11
One last question, as this being my only computer as of now i do need to run microsoft word, so i downloaded a lite netbook windows 7 .iso off thepiratebay, can i dual boot this on my netbook with ubuntu? If so how do i make a bootable usb for windows.

---

