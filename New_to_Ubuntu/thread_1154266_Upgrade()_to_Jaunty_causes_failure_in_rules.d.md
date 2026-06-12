---
title: "Upgrade(?) to Jaunty causes failure in rules.d"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-05-09
I upgraded to Jaunty 5 days ago. No errors were reported and with this one exception, everything (hardward, apps) is working well.

I tried to use the scanner portion of my Brother MFC-240c printer today. It has worked since Breezy. Sometimes needing some tweaking. So, I found the following at the forum and before you suggest checking to see if the device is supported in XSane or buying an HP device, read below.

I recall that I had to fix some number in some file, the name of the file, no doubt something to do with rules. I found the following about that:

[B]Re: MFC 240C install problem in jaunty
([http://ubuntuforums.org/showthread.php?t=1137573&highlight=mfc-240c](http://ubuntuforums.org/showthread.php?t=1137573&highlight=mfc-240c))

In jaunty the rules are now in lib\udev\rules.d[/B]

good enough, I know where the file went. Or so I thought!

Next, I found

[B]Re: How do I get my scanner to wok?  
([http://ubuntuforums.org/showthread.php?t=1137573&highlight=mfc-240c](http://ubuntuforums.org/showthread.php?t=1137573&highlight=mfc-240c))
I have a similar problem. I just installed jaunty and my scanner did not work (brother mfc 240c). It has to do with access permissions which used to be easily changed in 8.10. In 9.04 that permissions file does not exist anymore. My work around is to run "sudo xsane".
[/B]
My scanner worked with the sudo, but I cannot see the .jpeg as it's owner by root. (and I don't want to have to change file permissions, anyway, I shouldn't run XSane as root and even got a warning NOT to do that from Jaunty.

Next, I found:
**[SOLVED] XSane failed to open device intermittent MFC-240c brother**
([http://ubuntuforums.org/showthread.php?t=783599&highlight=mfc-240c](http://ubuntuforums.org/showthread.php?t=783599&highlight=mfc-240c))

and read:

[B]Changing the permissions as in the linked post will help. First of all you should find out which bus your usb scanner resides on, this is easily done with the lsusb command.

user@somelinuxbox:~$ lsusb
...
Bus 002 Device 002: ID 05d8:4002 Ultima Electronics Corp. Artec Ultima 2000 (GT6801 based)/Lifetec LT9385 Scanner...

As you can see the scanner resides on Bus 002 as the second (002) device in my case. The syntax for changing permissions of the scanner device is

user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/$BUS/$DEVICE

remember to change the $BUS and $DEVICE variables according to the lsusb output as described above. to change permissions to my scanner device i would enter:

user@somelinuxbox:~$ sudo chmod a+w /dev/bus/usb/002/002
[/B]
My lsusb shows:

mark@Lexington-19:~$ lsusb

Bus 002 Device 011: ID 04f9:01ab Brother Industries, Ltd MFC-240C


and many other devices redacted here for simplicity.

So my question is:

What do I do to get this device or application or what-ever-it-is to work? There is no file (document?) about the Brother product(s) in lib\udev\rules.d, I cannot know where, to add such a “thing”.

And how is it that the Ubuntu developers miss this with every release? I'm always having to change some “mission critical” file about the SCANNER!

---

### Post by cariboo on 2009-05-10
The Ubuntu devs have nothing to do with hardware drivers, I would suggest you check with the manufacturer to see if they have update their drivers to work with newer kernels.

---

### Post by anewguy on 2009-05-10
Actually, the rules DO have something to do with access to some scanners, digital cameras and other devices - via defaults in udev they get mounted as owned and only accessable to root.  This becomes evident with the device in question when you can't access it unless you run your app as root.  I faced this problem in 7.04, then between 7.04 and 7.10 (I think that was when) the syntax changed on the rules and was never documented in release notes - only after bug reports were filed did someone mentioned the change.  The same has happened in the change to 9.04 - the rules have changed location and the syntax has changed again.

Given your information from your scanner, this is what I would try (it worked for me to get access to my digital cameras):

via a terminal window:

cd /lib/udev/rules.d

sudo gedit 10-local-permissions.rules to open a blank file

put this line in the file:

SUBSYSTEMS=="usb" ATTRS{manufacturer}=="Brother Industries, Ltd" ATTRS{product}=="MFC-240C" MODE:="0666" SYMLINK+="Brother_MFC-240C_Scanner"


It is VERY important to keep the case, etc., as written above - you may want to just copy/paste it from here.

save the file and exit, then restart udev via:

/etc/init.d/udev --restart  (I think that's the syntax - if you want, you could just reboot).

Now with your device plugged in, check /dev and see if there is a device in there called "Brother_MFC-240C_Scanner".  If so, try using it again now.

Let us know what happens and if you still need help.

Dave :)

EDIT:  I agree on the problems of this not being mentioned everytime it changes.  You had to actually find udev in /lib before you could find the readme that explains what got moved, but that readme doesn't mention the syntax changes.  I had to look for a non-Ubuntu Linux guide to udev on the net to dig this out.

---

### Post by Mark_in_Hollywood on 2009-05-10
> **cariboo907 said:**
> The Ubuntu devs have nothing to do with hardware drivers, I would suggest you check with the manufacturer to see if they have update their drivers to work with newer kernels.

I had suggested, some year(s) ago, that the UbuntuForums.org should have hardware specific sub-forums for this very problem. Give the response that follows Cariboo907's post, it shows me several items of note:

1 - Cariboo907 doesn't know which driver works with which kernel. 

2 - This is a Ubuntu OS problem, NOT an end user problem, despite our software being "experimental".

3 - a Google search for: jaunty brother scanner, shows this thread as #1! Therefore, I'm the only person in all of Ubuntu-land that has this exact problem. Good Grief!!!

---

### Post by Mark_in_Hollywood on 2009-05-10
> **anewguy said:**
> 

via a terminal window:

cd /lib/udev/rules.d

sudo gedit 10-local-permissions.rules to open a blank file

put this line in the file:

SUBSYSTEMS=="usb" ATTRS{manufacturer}=="Brother Industries, Ltd" ATTRS{product}=="MFC-240C" MODE:="0666" SYMLINK+="Brother_MFC-240C_Scanner"


It is VERY important to keep the case, etc., as written above - you may want to just copy/paste it from here.

save the file and exit, then restart udev via:

/etc/init.d/udev --restart  (I think that's the syntax - if you want, you could just reboot).

Now with your device plugged in, check /dev and see if there is a device in there called "Brother_MFC-240C_Scanner".  If so, try using it again now.

Let us know what happens and if you still need help.

Dave :)


DAVE:

thanks for the help. I cannot find a file in /dev called:

Brother_MFC-240C_Scanner

and calling XSane from panel menu shows is still "I/O not found", however, under sudo, it comes up.

---

### Post by Mark_in_Hollywood on 2009-05-10
Now A-OK. This is what needs doing:

Brother Drivers for Linux® distributions
[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

and find:

**Scanner Driver / Scan-Key-Tool**

open that, locate the CORRECT driver (in my case it is:

**brscan 32bit 	deb 	0.2.4-0 	71 KB 	2007/09/27**

and save it to the desktop.

Next: on the same page find:

**Scanner     :    Driver Install   |  More Information   | ** 

[B]Scanner Driver Install
[http://solutions.brother.com/linux/en_us/instruction_scn1.html](http://solutions.brother.com/linux/en_us/instruction_scn1.html)[/B]

You will have to open two pages from here. One uses a dpkg install and the next page amends code in the rules.

Page 1:
[B]
Scanner driver install for USB
[http://solutions.brother.com/linux/en_us/instruction_scn1a.html](http://solutions.brother.com/linux/en_us/instruction_scn1a.html)

Step 1. Login as a superuser ( or use "sudo" option if it is required )

Step 2. Check if pre-required procedures are completed
    For Debian, Ubuntu 

Step 3. Download a driver.
    3-1. Check which driver will work with your product. (Product information is written in the driver download page)
    3-2. Download the driver
    Scanner Driver download page

Step 4. Install the driver
    4-1. Turn on your MFC/DCP and connect the USB cable.
    4-2. Open the terminal and go to the directory where the driver is.
    4-3. Install the scanner driver

        Command (for dpkg)  :  dpkg  -i  --force-all  (scanner-drivername, which you saved to your desktop)[/B]

and

page 2:

[B]Scanner Setting for normal user (I guess they mean NOT ROOT - normal? humph!)

Ubuntu 9.04
    1. Open "/lib/udev/rules.d/50-udev-default.rules" file.
    2. Edit "0664" to "0666" in "libusb device nodes" section.

    Before the edit---------------------------------

    # libusb device nodes
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   ...   , MODE="0664"


    After the edit----------------------------------

    # libusb device nodes
    SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device",   ...   , MODE="0666"


    3. Restart the OS. 
[/B]
After this, the scanner fired up. During the upgrade from Hardy Intrepid I had to go to the Brother webpages (LINUX) and d/l the scanner driver (for a 3rd or 4th time). This SHOULDN'T be needed. Developer's are you reading this?

---

### Post by anewguy on 2009-05-10
Notice the change to the udev 50- rules file - this makes all usb devices world accessable - if you don't mind this you're fine.  by creating the 10- rules file specific for the device, it would only make that device world accessable.  In 8.04, etc., our special rules came after the regular rules for a device, so we created things like 41- rules to override things in the 40- rules file.  It appears that in 9.04, such a file must come before the default rules - I found a non-Ubuntu Linux guide to udev that said to put all of our overriding rules in a file in the 10- range -> they recommended the name 10-local-permissions.rules.

I'm just glad you got it to work for you.  I really wish that these changes to udev would be noted in the release notes for Ubuntu.  I think sometimes the impression is that they are not used by very many people, so it's not worth mentioning.  I wish they would take the same attitude as one of the "big" vendors did back in the day when I was a systems programmer on large iron:  EVERY change is noted.  There can be different sections for each "group" of things changed, so that unless someone has had to work with udev in the past, they can skip it, but the information would still be there for those of us who do use the udev rules.  I realize this can mean more information than the "normal" user needs, but the whole idea of release notes are to note ANYTHING that has changed.  I'm just hoping we can get the people who create the release notes to understand this.  I suspect there are other areas with undocumented changes that are effecting others as well.

dave :)

---

