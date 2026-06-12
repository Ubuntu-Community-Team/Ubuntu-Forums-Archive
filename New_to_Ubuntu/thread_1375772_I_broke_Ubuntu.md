---
title: "I broke Ubuntu"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by jermza on 2010-01-08
I'm back in Windows now because I can't boot up Ubuntu (9.10).

In short, I've been learning Ubuntu over the last few days, after creating a partitioned boot up drive.

I've been having endless hassles with Ubuntu.

1.  My sound doesn't work properly.  I don't know what card I have, but my PC is a few years old (new one coming soon).  All I know is that everything works perfectly under Windows.  If everything "just works" under Ubuntu, then my logic dictates that my sound should "just work".  But it doesn't.  It's far too loud to the point of potentially blowing my speakers.  My volume control does nothing other than mute the excessively loud sound.  Every time I lower the PCM sound via Terminal, it forgets the settings on reboot.

2.  My graphics card is an old ATI Raedon 9600.  Nothing is working.  A friend of mine, who knows Linux well, has spent hours with no luck.  So my display is lousy.

3.  He then asked me to attempt the Kubuntu desktop, to see if it'd make a difference.  I installed it and my sound worked perfectly.  But I don't like Kubuntu because it's far too heavy and intense.  Before trying to see if my graphics card was working properly, I attempted to uninstall Kubuntu by copying and pasting a command I found [here]("http://www.psychocats.net/ubuntu/kde").

Now when I try boot up Ubuntu, it goes to a black command prompt screen that looks like Terminal.  I have no idea what to do further.

I'm considering reverting to Windows.  Is it all supposed to be this time consuming and impossible?

If anyone can help, thanks.  If not, back to Windows (or Snow Leopard).

---

### Post by MooPi on 2010-01-08
Sometimes the learning curve is steep and it sounds as if your hardware may be making it tougher. If you were an experienced user of Linux and Ubuntu this might have taken an afternoon or less. But because you are new to the system it might take longer and will be troublesome. I can only comment that when and if you get things running so they are acceptable, it should be enjoyable to use Ubuntu. I've had equipment that has given me fits and it is tough to see past the problems at times. I hope it all works out for you. There is nothing lost if you start from scratch again, so I suggest if you feel up for it start anew. Maybe take a breather from linux right now so your frustration doesn't get the best of you.

---

### Post by jermza on 2010-01-08
> **MooPi said:**
> Sometimes the learning curve is steep and it sounds as if your hardware may be making it tougher. If you were an experienced user of Linux and Ubuntu this might have taken an afternoon or less. But because you are new to the system it might take longer and will be troublesome. I can only comment that when and if you get things running so they are acceptable, it should be enjoyable to use Ubuntu. I've had equipment that has given me fits and it is tough to see past the problems at times. I hope it all works out for you. There is nothing lost if you start from scratch again, so I suggest if you feel up for it start anew. Maybe take a breather from linux right now so your frustration doesn't get the best of you.

I'm happy to start afresh.  How do I that, without ruining my current Windows installation.  Do I simply put the CD that I made back into the drive?  What about the current Ubuntu installation?

---

### Post by audiomick on 2010-01-08
I also think a fresh install might not be a bad idea.

If you boot into the live cd and do
```
lspci
```
in the terminal, it should show you what the computer is recognizing as your sound card.

+1 MooPi on the learning curve, your hardware and enjoying Ubuntu. Not much help I know, but I would like to encourage you to keep at it.

---

### Post by JayKay3000 on 2010-01-08
use win 7, it's just works.

You could pick up some stand alone speakers. Then you would be able to change the sound. I've always notice the sound to be quieter in ubuntu than in xp. 

Blank the pc and re-install. Make sure you have the right gfx drivers. Under the software centre there are gfx drivers which you will need to enable, there is another way to do this but on my win 7 laptop atm so I forgot.

With the sound i'm not sure off the top of my head.

Good luck with your ubuntu, else snow leapord which is a perfectly good os too. Or ubuntu, snow leapord and windows :P

---

### Post by MooPi on 2010-01-08
Yes you will need the Ubuntu CD. When you decide to try again just boot from the CD and follow the instructions. When it comes time to tell the software how to partition your drive , just use the exiting Ubuntu partition to proceed.  The new install will write over the old. Once again good luck !

---

### Post by Methuselah on 2010-01-08
You sound very frustrated.
Windows might be better for you and your hardware and the current point in time.
But a new Ubuntu is due in April so you can come back and give it a try then.

It's not that Ubuntu is tough to use but might have installation quirks for certain hardware.
So typically, if it doesn't detect all your hardware and use it optimally right away you'll have to spend some time configuring.
If that is too much for you to take on right now you can try on a different machine or try a future Ubuntu version.

---

### Post by nothingspecial on 2010-01-08
> **jermza said:**
>  I attempted to uninstall Kubuntu by copying and pasting a command I found [here]("http://www.psychocats.net/ubuntu/kde").

Now when I try boot up Ubuntu, it goes to a black command prompt screen that looks like Terminal.  I have no idea what to do further.


It sounds like you removed kubuntu but didn`t reinstall ubuntu.

```
sudo apt-get install ubuntu-desktop
```

If your hardware is not playing nice, and you are a begginer one of 3 things will happen. You will quickly become quite proficient with the linux terminal at the expense of your time; you will remove linux and revert to something you know; or you will chuck the stupid thing out of the window.

Do you want to spend the time learning and getting things working or do you just want to use your computer for computing?

I also break ubuntu, regularly, on purpose, because I get bored if everything works.

---

### Post by Mahngiel on 2010-01-08
The biggest draw back for Linux converts is the lack of adaptability for plug & play, "just working", and a feeling of helplessness.  I went through this myself just 3 months ago.  I would go back and forth with Windows, but would ultimately come back to Ubuntu.  Perhaps it was because Windows no longer offered me anything of major pertinence that I couldn't get elsewhere; most key: document editing and music playing.  I enjoy creating and developing - from images to application coding; which was the biggest lure for me since most everything is free and open source.  Which means I didn't have to download fake torrents and worry about viruses, keys not working, or cracks.

My computer is a 5 year old HP laptop, which marginal RAM (512) and a **once** state-of-the-art 64M nVidia GeForce 5200 graphics car.  Ubuntu's gnome is far lighter than kubuntu or any other KDE for that matter, and I average about 40% of my ram when running most of my programs, and though I COULD use the desktop effects programs, I chose not to, which saves my graphics card from burning up.  *nix systems are typically best suited for aged computers since they are not resource heavy, so I have a hard time understanding why your graphics card could not get up and loaded.

So, to answer your questions the best I can:
>  My sound doesn't work properly
See: [[link]("http://ubuntuforums.org/showthread.php?t=205449")]

> My graphics card is an old ATI Raedon 9600
See: [[link]("http://ubuntuforums.org/showthread.php?t=22496&highlight=radeon+9100")]
> Now when I try boot up Ubuntu, it goes to a black command prompt screen that looks like Terminal. I have no idea what to do further.
Chances are, your friend disabled the daemon that supported your card's 2D capabilities and now you don't have GUI. Follow the link above about your gfx card, install it via the command terminal, and you should be back up.

---

### Post by Darce on 2010-01-08
Try
```
startx
```

at the command propmt.

As for a new install, I'd simply use gparted on the live CD to delete the Ubuntu partition ( AFTER you've backed up all you windows stuff !! )

Isn't there some sort of repair feature on the live CD ?

---

### Post by nothingspecial on 2010-01-08
> **jermza said:**
> I'm happy to start afresh.  How do I that, without ruining my current Windows installation.  Do I simply put the CD that I made back into the drive?  What about the current Ubuntu installation?

When you install, it will ask you how you want the disk partitioned. Choose manual (advanced)

You will probably see 3 partitions (unless you have more) select the one that currently has ubuntu on it, click change (or modify or whatever it says). Select use as ext4 journalling file system choose a mount point of /
 Check the format partition box.
[COLOR="Red"]
DO NOT GO ANYWHERE NEAR THE WINDOWS ONE

MAKE SURE YOU GET IT RIGHT OR YOU WILL TOAST WINDOWS ASWELL

BACK UP EVERYTHING YOU DO NOT WANT TO LOOSE BEFORE YOU DO IT[/COLOR]

---

### Post by bodhi.zazen on 2010-01-08
Although it is a bit of an off topic suggestion ....

If you are having problems with hardware, sometimes it is easier to learn on Virtualization.

You could install VirtualBox in Windows and learn the basics of Ubuntu in Virtualbox.

If and when you obtain additional (new or used) hardware, you can try installing Ubuntu again (you can often get used Linux compatible video cards very inexpensive).

Also sometimes other distros have better hardware support. You could try Fedora or aas you seem to want a light install Puppy Linux.

---

### Post by MooPi on 2010-01-08
> **bodhi.zazen said:**
> Although it is a bit of an off topic suggestion ....

If you are having problems with hardware, sometimes it is easier to learn on Virtualization.

You could install VirtualBox in Windows and learn the basics of Ubuntu in Virtualbox.

If and when you obtain additional (new or used) hardware, you can try installing Ubuntu again (you can often get used Linux compatible video cards very inexpensive).

Also sometimes other distros have better hardware support. You could try Fedora or aas you seem to want a light install Puppy Linux.

Sucking up to the Admin +1  good advice

---

### Post by moody_mark on 2010-01-08
Personally I would advise the same as the post a few previous and re-install the ubuntu desktop. I broke my desktop just the other day and i couldnt even get a network connection. If you have a black screen and no network connection try the following;

1. CTRL+ALT+F1 - logs you into a command line
2. Login with your usual user / password
3. Check your network connectivity

```
ifconfig
```

You should see something like this

```
eth0      Link encap:Ethernet  HWaddr 00:21:70:e6:2e:dc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f6ae0000-f6b00000 

eth1      Link encap:Ethernet  HWaddr 00:23:4e:7e:e1:5c  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4eff:fe7e:e15c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:205026 errors:11 dropped:0 overruns:0 frame:200523
          TX packets:227542 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:155528517 (155.5 MB)  TX bytes:78948667 (78.9 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11215 (11.2 KB)  TX bytes:11215 (11.2 KB)
```

If you dont see any ip address then type

```
sudo dhclient
```

Then check again.

4. Reinstall the ubuntu desktop

```
sudo apt-get install ubuntu-desktop
```

Hope this helps :)

---

### Post by jermza on 2010-01-10
> **nothingspecial said:**
> When you install, it will ask you how you want the disk partitioned. Choose manual (advanced)

You will probably see 3 partitions (unless you have more) select the one that currently has ubuntu on it, click change (or modify or whatever it says). Select use as ext4 journalling file system choose a mount point of /
 Check the format partition box.
[COLOR=Red]
DO NOT GO ANYWHERE NEAR THE WINDOWS ONE

MAKE SURE YOU GET IT RIGHT OR YOU WILL TOAST WINDOWS ASWELL

BACK UP EVERYTHING YOU DO NOT WANT TO LOOSE BEFORE YOU DO IT[/COLOR]

Thanks.  I followed these steps, and I'm back in Ubuntu now.  I see that it left some stuff from my installation.

As I'm typing this, my updates are installing.

After that, I want to get my graphics card working, and my sound.

Any help with how to get my ATI Readon 9600 working?  (It's an old card, yes.)

---

### Post by jermza on 2010-01-10
I've installed my updates, and it's now prompting me about grub-pc or something.

It says 

CONFIGURING GRUB-PC
WHAT WOULD YOU LIKE TO DO ABOUT GRUB?
- keep the local version currently installed

What do I do from here?  What do I click on?

---

### Post by starcannon on 2010-01-10
- keep the local version currently installed

Do that.

---

### Post by jermza on 2010-01-10
I clicked on the one that says something like "keep package maintained" or something.

Did I do something wrong?

---

### Post by jermza on 2010-01-10
Well, I hope not.  SO far, everything seems fine.

---

