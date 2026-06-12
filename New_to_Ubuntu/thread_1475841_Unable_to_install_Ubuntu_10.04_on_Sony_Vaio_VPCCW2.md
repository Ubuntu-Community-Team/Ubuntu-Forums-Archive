---
title: "Unable to install Ubuntu 10.04 on Sony Vaio VPCCW26FG"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Yap Siauw Soen Gie on 2010-05-07
Hi all,

I am totally blind about linux

As the title I am unable to install the latest realease of ubuntu 10.04 both the 32 bit neither the 64 bit. The Sony Vaio it self come with 64 bit windows 7 preinstalled.
When I booted the linux cd installer show me a page with 3 kind of icon at the bottom side and then followed by a blank screen.
Nothing happen until i forced the machine to shutdown by pressing power button momentarily.

I've ever install 32 bit ubuntu 9.10 at the same machine without serious problem except still unable to configure a dial up dsl connection of bridge mode of my speedstream 4200

Anybody have the same experience about it?
and How should I solve this problem?

TIA

Yap

---

### Post by benny.kallstrom on 2010-05-07
Hi!

Have you tried to press the left or right arrow on the keyboard when at the icons, that should bring on the language menu.

---

### Post by madjr on 2010-05-07
have you tried installing it using wubi ?

pop the cd when you're in windows, a menu should come up

it's a quick way to test your system and see if anything is wrong

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

for now its quick

---

### Post by Yap Siauw Soen Gie on 2010-05-07
thanks for the fast reply folks :)

@ Benny: umm... not yet.. i'll give it a try it as soon as possible

@ madjr: also not yet tried to install using the wubi... so far i thought this wubi only works for side by side installation inside windows... i'll take a look for the possibility to using it.

again thank you :)

---

### Post by Yap Siauw Soen Gie on 2010-05-07
Tried both above suggestion with no success...

Hit the arrow button tricks works to bring out language selection screen...
Running wubi from inside windows operating system give me several same error message....
"There is no disk in the drive. Please insert a disk into drive \device\hardisk2\DR2"
after hit retry button several times wubi option shown... and i click at demo and installation option.
after reboot still need to press keyboard arrow key to bring out the language option screen.

Tried below options...

1. Try Ubuntu without installing
2. Install Ubuntu

and then the same thing happened a blank screen appear and stuck over there...

press esc then enter then followed by ctrl + alt + del button will eject the cd
press the enter after that will reboot the computer.

Any other suggestion to solve this problem will be a lot appreciated

---

### Post by madjr on 2010-05-08
> **Yap Siauw Soen Gie said:**
> Tried both above suggestion with no success...

Hit the arrow button tricks works to bring out language selection screen...
Running wubi from inside windows operating system give me several same error message....
"There is no disk in the drive. Please insert a disk into drive \device\hardisk2\DR2"
after hit retry button several times wubi option shown... and i click at demo and installation option.
after reboot still need to press keyboard arrow key to bring out the language option screen.

Tried below options...

1. Try Ubuntu without installing
2. Install Ubuntu

and then the same thing happened a blank screen appear and stuck over there...

press esc then enter then followed by ctrl + alt + del button will eject the cd
press the enter after that will reboot the computer.

Any other suggestion to solve this problem will be a lot appreciated

seems the problem is your Cd-rom, could be getting defective

some cd-roms will work perfectly playing music and do some other small tasks without problems, but installing an OS is different

well we have 2 options then:

a) install ubuntu using usb memory stick with unetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

or

B) install inside windows without the cd with wubi
[http://wubi-installer.org/](http://wubi-installer.org/)


more install info:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Yap Siauw Soen Gie on 2010-05-08
I am not sure if the cdrom is the problem mad...

Because the cdrom works well when I use Ubuntu 9.10 cd to install

Thanks for guessing the possibility tho

---

### Post by goldshirt9 on 2010-05-08
run as live cd.
then install from the desktop.

i had to do this on my laptop as its the only option i could get to work.
no idea why but it worked :confused:

---

### Post by Yap Siauw Soen Gie on 2010-05-08
That mean you had choosen "Try Ubuntu without installing" option gold?
My notebook will just give a blank screen after clicking that option instead.

Any help from the expert here?

---

### Post by AlexDudko on 2010-05-08
Have you tried to use any boot options? It can be that your CDROM isn't detected correctly. You should try the **noprobe** option.

---

### Post by Yap Siauw Soen Gie on 2010-05-08
ahh...
not yet... hope this will give me a chance to try this lucid lynx :)
Will try it soon...
thank you Alex

---

### Post by Yap Siauw Soen Gie on 2010-05-08
tried to open the bios there are no such noprobe option...
the only existing options are to enable/disable external boot device and enable/disable network boot
they are both disable by default... I changed it to enable
but the same thing happen... blank screen appear after i click on "try ubuntu without installing"
even  there is no display I guess I already inside ubunu system
The clue is when i press ctrl+alt+del followed by enter the system will eject the cd and will reboot if i then press enter again...

phew.... what a tough installation :(

---

### Post by madjr on 2010-05-08
> **Yap Siauw Soen Gie said:**
> tried to open the bios there are no such noprobe option...
the only existing options are to enable/disable external boot device and enable/disable network boot
they are both disable by default... I changed it to enable
but the same thing happen... blank screen appear after i click on "try ubuntu without installing"
even  there is no display I guess I already inside ubunu system
The clue is when i press ctrl+alt+del followed by enter the system will eject the cd and will reboot if i then press enter again...

phew.... what a tough installation :(


i have 3 other computers/laptops at my home from different manufacturers all of them has gone pretty smooth

am not sure why you haven't tried either unetbootin or downloading wubi, both options dont need a cd rom

ubuntu using usb memory stick with unetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

or

install inside windows without the cd with wubi
[http://wubi-installer.org/](http://wubi-installer.org/) (download this)

---

### Post by davidryderuk on 2010-05-08
Hi,
I don't have this computer myself, but I think these two links should get you started:

[http://ubuntuforums.org/showpost.php?p=8748678&postcount=16](http://ubuntuforums.org/showpost.php?p=8748678&postcount=16)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/571383](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/571383)

The second link seems to suggest that you can boot the live cd by using the "nomodeset" boot option:

1. Wait for the boot menu to appear.

2. After navigating the language menu press the F6 key.

3. Press escape to get rid of the menu that appears.

4. Use the keyboard to add "nomodeset" to the end of the boot parameters.

5. Press return once or twice to commence booting.

If in doubt there seem to be plenty of threads around from people suffering the same problem (just search for "sony vaio cw ubuntu" on google).

---

### Post by Yap Siauw Soen Gie on 2010-05-09
@ madjr: wubi already tried and fail, whether the Unetbootin downloaded but not yet implemented... still looking for a logic reason to do it.

@ david : the best guidance so far david... thank you very very very much :)
I've made a big progress after implementing your suggestions; the installation successful.
Unfortunately it again goes to blank screen at boot time... happened to both boot options the generic and the safe mode one.

Is there another tricks to make the boot success?

Again thanks a lot to all

---

### Post by davidryderuk on 2010-05-09
Glad to hear it worked. In order to boot the installation you have to use the "nomodeset" boot option again. This involves slightly different instructions than before:

1. At the grub menu select the generic kernel and press e.

2. Using the arrow keys navigate to the line that ends with "quiet".

3. Add the nomodeset option to the end of this line.

4. Use the "ctrl x" key combination to boot.

In order to make this change permanent you need to make some changes to grub once your machine boots (otherwise you'll have to manually add the same boot option every time):

1. Open the terminal (Applications > Accessories > Terminal).

2. Edit the grub configuration file.

```
sudo gedit /etc/default/grub
```

3. Find the following line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and change it to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

4. Save and close the file, and then update grub.

```
sudo update-grub
```

5. This should allow your machine to use the new boot option automatically.

I just wanted to make it clear the problem you have with booting is related to your graphics card not setting the resolution properly. The "nomodeset" boot parameter just tells linux to use a slightly older method of setting the resolution. This is why you need to use the same boot option on the live cd and in the installation.

You should know that the proprietary nvidia drivers (which are optional) are also quite buggy with this graphics card, although you can find people who have worked around the problem.

[http://ubuntuforums.org/showpost.php?p=8748678&postcount=16](http://ubuntuforums.org/showpost.php?p=8748678&postcount=16)

---

### Post by goldshirt9 on 2010-05-09
sorry to state the obvious, but have you tried to download again and burn at a lower speed.
if you have , ignore me but i had a similar  problem with dodgy disks and i found it crashed my system when trying to boot into the disc.

---

### Post by Yap Siauw Soen Gie on 2010-05-09
Works flawlessly great thanks to david :)
Also thanks to goldshirt9 for remind me about another possibility.
Also to all who have tried hard to give hand... a great site to get help :)
Case closed.

---

### Post by dharmendra verma on 2010-09-02
ya great work davidryder, i became a fan of urs .thanx  u really  solved my problem that i was having in installation ubuntu  ultimate *64 in my sony  vaio vpccw15fg.... thanx

---

### Post by dharmendra verma on 2010-09-02
visit this link to solve your problems- related to sony vaio 64 bit 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9795785#post9795785](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9795785#post9795785)

---

