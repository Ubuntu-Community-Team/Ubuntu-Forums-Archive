---
title: "How do i install grapic driver and get bigger than 800x600 resulution?"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-15
when I go to "System> Preferences> Displays" it says "Display unknown" I do not get to a higher resolution than 800 x 600, and when I press the "Search for Displays " button either nothing happens? what should I do?
 I have Ubuntu 10.10 on a laptop Advent 1015 Nordic
 is the first time I try linux and I do not understand how I find out what video driver is called and how do I get hold of the driver: S

 help please!

---

### Post by Grenage on 2011-02-15
Under *Administration/Additional drivers*, are any available?

Do you know what graphics card you have?  If not, from a command line:

```
lspci | grep -i vga
```

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-15
> **Grenage said:**
> Under *Administration/Additional drivers*, are any available?

Do you know what graphics card you have?  If not, from a command line:

```
lspci | grep -i vga
```

yeah i forgot to say i tried that to and none are available

i just wrote that comand i get this

>  01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
 
what do i do now?

---

### Post by Grenage on 2011-02-15
Your computer is a laptop, I assume?

While I have no personal hand-on experience with SiS cards, I'm assuming that the kernel drivers are sufficient.  You can create a custom xorg.conf, and I have a rough guide [here]("http://www.grenage.com/xorg.html").

If you get stuck, post back.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-15
ok i followed the guide and i am at this part now:
>   The syntax is *"cvt [horizontal resolution] [vertical resolution] [refresh rate]"*:what is this? when i tryped that in console i get this message back:
> usage: cvt [-v|--verbose] [-r|--reduced] X Y [refresh]

 -v|--verbose : Warn about CVT standard adherance.
 -r|--reduced : Create a mode with reduced blanking (default: normal blanking).
            X : Desired horizontal resolution (multiple of 8, required).
            Y : Desired vertical resolution (required).
      refresh : Desired refresh rate (default: 60.0Hz).dont understand what i do here now....... and yes i am on laptop : p


btw how are i making this file you are talking about, i have no idea what i am doing i am total new to linux remember heh

---

### Post by SpiderSkull on 2011-02-15
Ubuntu doesn't have good support for the SIS family cards
to activate higer resolutions do this:


hit: ctrl+alt+F1
login with username and password
execute the following commands

```

sudo -s (give pass all commands are now executed as root)
service gdm stop
Xorg -configure

mv /root/xorg.conf.new /etc/X11/xorg.conf

service gdm start

```

tell us if it is working.

---

### Post by Grenage on 2011-02-15
Ok, forget about the guide for now. ;)

Do you have, or can you find, a user manual for the laptop?  What we're after is the technical specifications, such as horizontal/vertical frequencies, and native resolution.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-15
> **SpiderSkull said:**
> Ubuntu doesn't have good support for the SIS family cards
to activate higer resolutions do this:


hit: ctrl+alt+F1
login with username and password
execute the following commands

```

sudo -s (give pass all commands are now executed as root)
service gdm stop
Xorg -configure

mv /root/xorg.conf.new /etc/X11/xorg.conf

service gdm start

```tell us if it is working.

i just copied that whole thing went to ctrl +alt+F1 and tried to paste inside, dident work to paste, tried to get out somehow, dont remember what i pressed right now but my computer restarted..
so should i write all that things down and type in by myself? and how do i get out of that thing without restarting?

---

### Post by SpiderSkull on 2011-02-15
lol, starting gdm service again will bring you back
but yes you should type all this maybe write it down first.
you can't just open a terminal en paste it there because the desktop service should be down to accept a new configuration file.

try again :P

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-15
it looked like that first 3 commands worked but when i typed the 4th
mv /root/xorg.conf.new /etc/X11/xorg.conf
it said cant find file or filecataloge or something................
is it even possible for me to fix this or do i have to use 800x600 forever?

---

### Post by SpiderSkull on 2011-02-15
if you execute Xorg -configure after it is done it should say where he placed your file. then change the line acording to file.
mv "your location" to /etc/X11/xorg.conf

---

### Post by krustybaguette on 2011-02-15
I am running into the same video problem with Ubuntu 9.04 on Toshiba Portege 7140CT. 500 Mhz Pentium III with max RAM of 320. I have located a driver for the machine but cannot figure out what to do with it. Based on an earlier entry in this thread my video is:

kenny@Portege7140CT:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: Trident Microsystems Cyber 9540 (rev 52)

I also have pages from the Portege's online manual which give further detail about the video hardware. I can probably locate the file again and paste that information into a subsequent posting.

The driver I found is in BladeXF86_SVGA.gz Filename is "XF86_SVGA"

I searched file system for an xorg.conf file and only result is a compressed file/folder "xorg.conf.5.gz" which contains a read only file "xorg.conf.5" As I understand it there should be an "xorg.conf" file at /etc/xorg.conf.

Is it possible that the above named file "SF86_SVGA" is merely a text file that needs to be cut and pasted into a new file and named /etc/xorg.conf?

When I open System/Preference/Display my options are limited to 800x600. I assume this is based on some generic driver that gets you up and running. Yesterday's experimenting ended up crashing as rebooting sent me into a flashing screen that showed "login:" but did not respond to keyboard entries.

---

### Post by realzippy on 2011-02-15
@krustybaguette

..since OP has a SIS graphics card,I suggest to open an own thread,or things get complicated here...

---

### Post by realzippy on 2011-02-15
@ OP:

..have a look here,same graphics,no luck.
but you should try what I suggested in post #11
[http://ubuntuforums.org/showthread.php?t=1685866&page=2](http://ubuntuforums.org/showthread.php?t=1685866&page=2)

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-15
[(A) realzippy]("http://ubuntuforums.org/member.php?u=216523") : i dont understand german sorry:...........t

situation is diffrent now since i created the topic, one guy from other forum norwegian show me this link:
[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)
seem to be the right drivers, no?
but My problem is i when i do like it says on that site to write the command its wrong and, i have try like 50 diffrent typos for the direction where the install files are, but nothing works and i get an error message thats like this:
> cp: can not retrieve information about "sis671_drv.so" with the state: No such file or directory
my system language is norwegian so i translated that "error message" in google translator...........Btw
Help anyone.. i feel that i am close........

---

### Post by realzippy on 2011-02-15
*but My problem is i when i do like it says on that site to write the command its wrong and, i have try like 50 diffrent typos ......*

Can you specify?Where exactly you get stuck?
Btw,the guide from that link you posted,is:

1.For lucid.Since Xorg server has changed,the driver might not work..

2,Gives unnecessary instructions,suggests to become root and goes on with "sudo" commands,can be simplified.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-15
> **realzippy said:**
> *but My problem is i when i do like it says on that site to write the command its wrong and, i have try like 50 diffrent typos ......*

Can you specify?Where exactly you get stuck?
Btw,the guide from that link you posted,is:

1.For lucid.Since Xorg server has changed,the driver might not work..

2,Gives unnecessary instructions,suggests to become root and goes on with "sudo" commands,can be simplified.
are you saying that driver is not for ubuntu? but it says "[COLOR=Blue][B][SIZE=3]THIS WORKS on ubuntu 10.04" ?

so why shouldent it work for ubuntu 10.04+++ ??? i am really ******* confuzed about this....
[/SIZE][/B][/COLOR]

---

### Post by realzippy on 2011-02-15
If you read on [that thread]("http://ubuntuforums.org/showthread.php?t=958967&page=38"),you will find the sources to compile the driver,anyway,this might be too hard since we are in beginners section..
I do not know if this works although,since the Xorg server has changed to 1.9 meanwhile.


Edit:
*Grenage* already asked,but we need to know:

*Do you have, or can you find, a user manual for the laptop? What we're after is the technical specifications, such as horizontal/vertical frequencies, and native resolution.*

---

### Post by realzippy on 2011-02-15
*(A) realzippy : i dont understand german sorry:...........t*

..there is not much to understand,only important things are the bash commands.Anyway,this guide from the german ubuntu forum [URL="http://ajoliveira.com/ajoliveira/uk/software/xorg.php"]points to
a guy[/URL] who has a driver,also for 10.10.

Can translate the instructions for you,but need to know the Hsync/Vrefresh
values for your laptop,the native resolution and if you run
32 or 64 bit.



.

---

### Post by gyyug78fg87ogguiioioioioi on 2011-02-15
a

---

