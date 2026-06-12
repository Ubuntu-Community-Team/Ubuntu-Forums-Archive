---
title: "Some basics"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Rael Harris on 2009-08-06
Hi everyone!
This is my first post, so I'm hoping I'll say the right things here without making too many mistakes.
Bear with me please. :P

I have installed Ubuntu 9.4 on three computers in my house in the last two days.
One on an Alu-MacBook (Using VMWare Fusion), one on the household desktop PC, and one on my fiancé's Lenovo Ideapad S10e.

First of all I was hoping I could get pointed in the right direction as far as finding drivers for these systems.
(I know I haven't given enough info for you to show me exactly where, but an idea would be gladly appreciated)

Secondly, are there drivers for the MacBooks?
ie. If I installed Ubuntu side by side with my Boot Camp Partition (Windows on Mac) would there be drivers out there that would support the Ubuntu OS? (Same question with regard to the Lenovo S10e)

I'm assuming that if there are no drivers for MacBooks, I could use the VMWare Tools Drivers Package that comes with VMWare Fusion, but there is a catch with this.
When I try to install VMWare Tools, it simply mounts a virtual CD-Rom.
Inside it sits a .tar.gz
This brings me to my third question:

How on earth do I install this??? :(

I followed the directions which explained a whole lot of complicated line commands that I needed to do but, I found I was unable to get past the first step. (Sorry, but I'm a beginner... honest)
Is there some simple thing I'm missing?

Finally, there seems to be some sort of mysterious problem on my fiancé's copy of Ubuntu.
Whenever she deletes a file (and not Shift+Del like I have seen mentioned in the forums) it does not move to trash, but it dissapears COMPLETELY. :confused:
Some people said it could be sitting in a "Trash Can" on the /root folder but, I don't know how to access it.
It seems locked. (I know I need to login as "root" but I have no idea how to.)

Phew... and that's all for now.
I hope you guys haven't chewed your arms off with my lame questions, but I'd be so happy if some of these things could clarified for me.

Thanks a million guys! Its great to be a part of the "Linux Family". :D

---

### Post by Rael Harris on 2009-08-06
Oh and one more thing...

What's is err... "Gnome" and what is it's relation to "Ubuntu"? :roll::redface:

---

### Post by LewRockwell on 2009-08-06
.

very very appropriate avatar

it might be preferable to get each machine perfected individually

.

---

### Post by Temposs on 2009-08-06
Welcome to Ubuntu :-)

Most drivers on Linux are included in the kernel(the core of Linux), so for the most part you don't have to go out and get more. Everything should just work from the start. There are some cases where grabbing some special drivers is necessary, but you haven't presented any specific cases of hardware not working, so I can't tell you if you need drivers or where to look.

Shift+Del deletes files permanently. To move a file to the trash, just use the Delete key. That will move it to the trash. Also, you can right-click and select Move to Trash. That does the same thing as the Delete key.

---

### Post by x22 on 2009-08-06
welcome to the forum

taking a few of your points

> inside it sits a .tar.gz
> how on earth do I install this???

that is source code: this is a great thing--read,
understand:-) I suggest
1. "mv foo.tar.gz /usr/src"
2. "tar -xvvzf foo.tar.gz"  #extract gzipped foo.tar.gz
3. "cd foo"
4. "more README"
and eventually
5  "make"

> ...I need to login as "root" but I have no idea
>  how...

the root account has no password; but you can make one
"passwd root" then login

> whenever she deletes a file...it disappears COMPLETELY

yes: that's *nix's way: you know what you are doing...

---

### Post by Temposs on 2009-08-06
GNOME is the desktop manager that Ubuntu uses by default. It creates the framework for the look of the menus and icons and windows and such. It's what makes a lot of Ubuntu look the way it does, and makes everything standardized across the different programs. There are several alternatives, such as KDE(comes with Kubuntu) and Xfce(comes with Xubuntu). You can try the different alternatives if you don't like GNOME.

---

### Post by Temposs on 2009-08-06
> **x22 said:**
> > whenever she deletes a file...it disappears COMPLETELY

yes: that's *nix's way: you know what you are doing...

That may be the *nix way on the command line, but in GNOME it most certainly is not. There is a very good trash system which is very much meant to be used. It's also a good idea when working with important documents to have a safeguard against deleting them entirely the first time.

With Ubuntu, we're trying to help new users transition to Linux easily, not discourage them.

---

### Post by lisati on 2009-08-06
"root" in Linux refers to a "super user" who administers the computer and hopefully knows what they are doing.

The preferred method of doing something with "root" privileges (i.e. as an administrator, not to be confused with marital relations :) ) with Ubuntu is with the "sudo" command. Have a look here for more information: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Rael Harris on 2009-08-07
> **LewRockwell said:**
> .

very very appropriate avatar

it might be preferable to get each machine perfected individually

.
Hehe.. I thought it would be appropriate in this situation. Glad you guys noticed. ;)

---

### Post by magmon on 2009-08-07
> **Rael Harris said:**
> Oh and one more thing...

What's is err... "Gnome" and what is it's relation to "Ubuntu"? :roll::redface:

Gnome is the interface that ubuntu is on, much like KDE or XFCE. It's like the vista interface, no OS behind it, just the visuals.

---

### Post by montini on 2009-08-07
> **Rael Harris said:**
> Hehe.. I thought it would be appropriate in this situation. Glad you guys noticed. ;)

This was the first thing I had noticed too :D

---

### Post by Rael Harris on 2009-08-07
Hey Tempos, thanks for your help so far. You said that most of the drivers are built into the Ubuntu Kernel so I'll just try and list the specs of my computers here to see if there is anything else that's needed:

MacBook:

Processor Name:    2.4 GHz Intel Core 2 Duo
Graphics Card:       NVIDIA GeForce 9400M
Memory:                2 GB 1067 MHz DDR3

Lenovo Ideapad S10e:

Processor:   Intel ATOM Processor N270 Single Core ( 1.60GHz 533MHz 512KB )
Display:      Intel Graphics Media Accelerator 950
**Memory:    1 GB** PC2-5300 DDR2 SDRAM 667MHz
Monitor:      10.1 " WSVGA Glossy TFT with integrated camera 1024x576
Track Pad:   Industry Standard Multi-touch 2 button touchpad
Wireless:     Broadcom 11b/g Wi-Fi wireless
Bluetooth:   Bluetooth Version 2.1 + EDR

Desktop PC:

Display:       NVIDIA GForce 8500 GT
Processor:   2.00 GHz Intel Dual Core

That's all the most important stuff I think... Everything else seems to work fine. :)

---

### Post by Rael Harris on 2009-08-07
Now as far as that .tar.gz is concerned, X22 had this to say about it:

> that is source code: this is a great thing--read,
> understand:smile: I suggest
> 1. "mv foo.tar.gz /usr/src"
> 2. "tar -xvvzf foo.tar.gz"  #extract gzipped foo.tar.gz
> 3. "cd foo"
> 4. "more README"
> and eventually
> 5  "make"

What does this mean? :P

---

### Post by Rael Harris on 2009-08-07
Thanks very much for the info on "sudo" Lisati. Very helpful stuff. :)

---

### Post by Rael Harris on 2009-08-07
> **Temposs said:**
> That may be the *nix way on the command line, but in GNOME it most certainly is not. There is a very good trash system which is very much meant to be used. It's also a good idea when working with important documents to have a safeguard against deleting them entirely the first time.

With Ubuntu, we're trying to help new users transition to Linux easily, not discourage them.

I'm still a really confused about the trash can. Who's Nix? :redface:
I tried the following last night while trying to fix her computer:

I tried normal delete and the files disappeared. They never went to Trash and I was unable to find them again. I tried Shift+Del and a warning came up asking me if I would like to permanently delete the file. I even tried opening the Trash folder and dragging a file from my desktop onto it. It was like dropping the file into an abyss... it just disappeared and it was impossible get it back. I tried right-click "Move to Trash"... still no luck.

What could I be doing wrong, or what setting could be causing this?

Thanks guys. :)

---

### Post by super kim on 2009-08-07
> **Rael Harris said:**
> I'm still a really confused about the trash can. Who's Nix

i think the *nix is a bit of jargon you dont need to know.
[http://en.wikipedia.org/wiki/Unix-like](http://en.wikipedia.org/wiki/Unix-like)
that link will explain if you care though.

> **Rael Harris said:**
> I tried normal delete and the files disappeared. They never went to Trash and I was unable to find them again.
where were these files before they were deleted?

---

### Post by 3rdalbum on 2009-08-07
X22 gave you some commands to put into the terminal (Applications > Accessories > Terminal), but didn't explain this.

Why don't you try following the VMware instructions, and if you get stuck at a particular point just give us a yell with what you're trying to do and the error message?

As far as your system specifications, they aren't exhaustive, but what you've posted there generally either has drivers built-in, or Ubuntu can get drivers for them from the Internet (System > Administration > Hardware Drivers)

DO NOT install normal hardware drivers in VMware or any virtualisation program. The guest operating system cannot see the real hardware; it interacts with some emulated hardware. That's what the VMWare guest additions are for (partly).

---

### Post by dark_harmonics on 2009-08-07
I have gotten 3 or 4 models of Macs to work with ubuntu. Try these how-tos [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

Some very helpful stuff in there. 

To answer some of your questions:
-You should never login as root to a Mac or Linux system, use sudo or gksudo to get root privilages for operations.
-Gnome is a suite of programs that make up the user interface.
-Most hardware will "Just work" and doesnt need additional drivers.


*edit* If you are running linux in a virtual machine then the tar.gz you have probably contains software that supports the virtual hardware. The how-to above were for natively running ubuntu. To extract a tar.gz you may need to have the build-essential package installed. Here's how i would go about trying to install it:

sudo apt-get install build-essential
*copy the file to my desktop*
cd ~\Desktop
tar -xvf filename.tar.gz
cd folderitcreated
more README
*Compile it according to the readme*
usually commands are like:
./configure
make 
sudo make install

---

### Post by Rael Harris on 2009-08-09
> **super kim said:**
> i think the *nix is a bit of jargon you dont need to know.
[http://en.wikipedia.org/wiki/Unix-like](http://en.wikipedia.org/wiki/Unix-like)
that link will explain if you care though.


where were these files before they were deleted?
They were sitting on the Linux Desktop, but last night after a reboot it mysteriously started working again. I have no idea what I did. :P

---

