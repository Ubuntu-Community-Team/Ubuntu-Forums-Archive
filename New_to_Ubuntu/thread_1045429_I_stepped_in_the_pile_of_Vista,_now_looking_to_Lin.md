---
title: "I stepped in the pile of Vista, now looking to Linux...?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by foocaKes on 2009-01-20
I'm just a basic college student, unfortunate enough to fall for Vista. I bought this HP laptop this previous summer, which is a really good for the price. Except now its hardware is being strangled by Vista. I use this for pretty much only these things: Music (Winamp), messenger (Trillian [AIM, MSN]), internet (Mozilla), movies (VLC or WMP), picture storage, uTorrent (Movies, music, and TV shows), Word Processor (Microsoft Office), and Steam (Team Fortress 2, Counter-Strike).

Now, I know there are alternatives: I can keep music and get XMMS or Amarok, Ubuntu has a messenger with AIM and MSN or just Pidgin, Ubuntu also has Mozilla preset, VLC works on Linux, something like KTorrent, and Word Processors in Ubuntu (Or online). Apparently there is no Linux version for Steam, but I think I play games infrequently enough to not miss them on the laptop.

I guess my question is: Is it worth switching over to Ubuntu, or any other Linux? Saving all of my files and getting rid of Windows? I also don't know if perhaps my hardware won't be compatible or work with Linux (I'm no programmer, computer engineer, or protocol genius).

If you think it is, what would your suggestions be for distributions? I'm pretty sure Ubuntu is probably the best bet for me as a **COMPLETE** beginner; what would the difference be in KDE, Gnome, kubuntu, xubuntu, etc?

---

### Post by taurus on 2009-01-20
If you want to know how well Ubuntu would run on your laptop, why not just list the spec of your laptop.

Meanwhile, Gnome, KDE, XFce3, Fluxbox, OpenBox, etc. are just window managers or desktop environments.  Check them all out before you decide which one you like best.  For instance, you can install Kubuntu or Xubuntu after you have installed Ubuntu on your laptop.  No need to reinstall anything.

```
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
```

---

### Post by foocaKes on 2009-01-20
Eh, I guess I should stress this more: I don't know that much about computers. How do I get a list of all of my hardware? Also, I know I could do the research on the specifics and differences in KDE, Gnome, and whatever; however, I, again, don't know what any of it means. That's why I wanted to ask for a simplified response and or a recommendation.

---

### Post by taurus on 2009-01-20
Go to HP's site and look up the model of your laptop.

---

### Post by rzrgenesys187 on 2009-01-20
As said before Gnome and KDE are desktop environments which means they are just interfaces in front of the terminal pretty much.  They allow you to have everything you are used to when running a computer so you don't have to use a command prompt (although with a terminal window open you can still use the terminal).

Ubuntu by default installs with the Gnome environment which is considered easier for most users.  Kubuntu (note the K) uses the KDE environment and it has been said that Kubuntu is not the best KDE distro out there so I would go with something else if you want KDE (OpenSuse, Fedora, and Mandriva seem popular).  From an Ubuntu install you can install kubuntu or xubuntu (XFCE interface) with the commands listed above.

If you just want to see what Ubuntu is like I suggest downloading the cd off of the website and burning it.  You can boot into the cd and run the operating system off the disk which makes no changes to your hard drive to see if you like it.

I hope that helps some, feel free to ask for clarification on anything I said.

---

### Post by dasunst3r on 2009-01-20
I think your computer's more likely choking on all the stupid little pieces of software that came with your computer.  Try removing those.  Better yet, consider backing up your data and reinstalling the operating system.

Start off by downloading a LiveCD to try on your laptop.  If you can **easily** do your everyday tasks (IM, word processor, web surfing, etc.), then Ubuntu is right for you.  Furthermore, unless you have another computer for gaming, I suggest you dual-boot on your laptop.

---

### Post by foocaKes on 2009-01-20
I bought it through Best Buy, which no longer lists it and HP does not have it on their site.

---

### Post by taurus on 2009-01-20
What is the model of it?

---

### Post by floatingpoint on 2009-01-20
start menu > run (or maybe search for 'run', the programme should show up > type dxdiag and hit 'run' or 'okay' or press return.

That should list your hardware. I think.

---

### Post by foocaKes on 2009-01-20
Is Wubi as good as doing that? I don't really know how to dual boot.

---

### Post by foocaKes on 2009-01-20
HP Pavilion dv6000.

---

### Post by mangurt on 2009-01-20
I'm sure people are going to get the specs of your laptop and say hey or nah on it.  My suggestion would to download one the live cd and see what your computer will do.  Gnome or KDE really does not matter, it's pretty much how you want things to look.  You can test basically all your hardware before you even install the operating system.

---

### Post by foocaKes on 2009-01-20
Yeah... I know where 'Run' is on XP, but I can't find it on this.

---

### Post by foocaKes on 2009-01-20
Well, like I asked just a minute ago: Is Wubi the same as putting it on a CD and using it? And, isn't doing the CD thing just the same as installing it? If I do like it when I use it, and pick Gnome, how do I switch to KDE if I like that... Or something?

---

### Post by Therion on 2009-01-20
Just had an HP dv6000 in my hands the other day.  I could run a LiveCD on it just fine, although the wireless card needed some help to connect.  

If it's a standard '6000 it comes with 512MB of RAM which is enough, but not ideal in my opinion.  Graphics are, most likely, the Intel integrated GMA 950 chipset.

In short, it'll run most any version of Ubuntu you care to throw at it though, most likely, you're looking at doing some tweaking to get everything working correctly.  If you were my client, I'd also suggest adding more RAM.

Download a LiveCD and take it for a spin.  You can use the LiveCD and get a feel for Ubuntu without making any permanent changes to your current configuration.  When you're done playing with Ubuntu, shut down, remove the disk and reboot.  You'll be right back in Vista.

---

### Post by taurus on 2009-01-20
> **foocaKes said:**
> I bought it through Best Buy, which no longer lists it and HP does not have it on their site.

Did a search and this came up?

[http://h10025.www1.hp.com/ewfrf/wc/manualCategory?cc=us&dlc=en&product=1842155&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/manualCategory?cc=us&dlc=en&product=1842155&lc=en&jumpid=reg_R1002_USEN)

---

### Post by hyperdude111 on 2009-01-20
Dual bootiung is easy and with gparted safe, i never bother with backups now. Wubi is always good if you want to try it then you can make an informed final decision, but a wubi install crashes easily.

---

### Post by foocaKes on 2009-01-20
A friend of mine told me about CPU-Z. I know it doesn't list everything, but:

AMD Turion 64 X2 Mobile TL-60
Quanta 30D0 Motherboard NVIDIA Chipset nForce 520
DirectX 10
PhoenixBIOS 4.0 Release 6.1
HP Pavilion dv6700 Notebook PC
Conexant High Definition SmartAudio speakers (Default)
2048 MBytes DDR2 Dual Channel memory
NVIDIA GeForce 8400M GS 1023 MB memory

---

### Post by foocaKes on 2009-01-20
Haha, when I searched, it just showed batteries.

---

### Post by floatingpoint on 2009-01-20
> **foocaKes said:**
> Yeah... I know where 'Run' is on XP, but I can't find it on this.

Like I said, do a search for 'Run' in that wee bar on the start menu, and it'll appear.

---

### Post by foocaKes on 2009-01-20
If you dual boot, or burn Ubuntu to a CD and run it, does that mean *no* Windows is running and you choose Ubuntu **or** Windows when you turn on the computer?

---

### Post by floatingpoint on 2009-01-20
Dual boot is when you have two operating systems installed, e.g. Ubuntu and Windows, and you pick the one you want to use when you turn the computer on.

---

### Post by Grogger on 2009-01-20
You asked about WUBI.  I believe this installs Ubuntu from a windows base.  The regular installer runs from an Ubuntu or Debian base.  If you're going to install, it's probably better to run it from the regular way.  

Like others have mentioned burning ubuntu to CD and starting the computer with the disk in the drive will allow you to run the operating system from the CD.  All the data goes into your RAM and allows you to test it without touching your windows install on the hard drive.  That's the "Live CD" part.  You can install from the desktop icon later if you like Ubuntu.  Aysiu's tutorials below also explain how to download and burn a CD from an ISO file.  

Helpful information on whether Ubuntu could be right for you from Aysiu:
[http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)

I've found Aysiu's Ubuntu Tutorials incredibly clear and helpful for explaining how to install and set up Ubuntu to my liking.  It seems pretty clear for beginners.  
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

I hope this helps.

---

### Post by egalvan on 2009-01-20
> **foocaKes said:**
> If you dual boot, or burn Ubuntu to a CD and run it, does that mean** *no* Windows is running and you choose Ubuntu [B]or** Windows when you turn on the computer[/B]?

to stress the point, 

one or the other runs, not both.

but one OS can (optionally) see the other's files.

---

### Post by Captain_tux on 2009-01-20
> **foocaKes said:**
> HP Pavilion dv6000.

> **foocaKes said:**
> A friend of mine told me about CPU-Z. I know it doesn't list everything, but:

AMD Turion 64 X2 Mobile TL-60
Quanta 30D0 Motherboard NVIDIA Chipset nForce 520
DirectX 10
PhoenixBIOS 4.0 Release 6.1
HP Pavilion dv6700 Notebook PC
Conexant High Definition SmartAudio speakers (Default)
2048 MBytes DDR2 Dual Channel memory
NVIDIA GeForce 8400M GS 1023 MB memory

I dual-boot Ubuntu 8.04 (Hardy Heron) with Vista on an HP dv6500 (similar to your 6700). After a few tweaks here and there, I've gotten it to the point where I want it... but for the requirements you've posted, you should be fine with little or no tweaking.

---

### Post by Paddy Landau on 2009-01-20
> **hyperdude111 said:**
> Wubi is always good if you want to try it then you can make an informed final decision...

WUBI is a superb choice for the experimenter. You install it on Windows as you would any other program. To get rid of it, you simply uninstall it.

WUBI will answer your questions.

> **hyperdude111 said:**
>  ... but a wubi install crashes easily.
WUBI may crash more easily than a native install of Ubuntu, but -- in my experience -- it crashes less often than Vista ;).

If you try WUBI and it works for you, and you can do everything you want, then (if your hard disk is large enough) uninstall it and do a native install.

(Back up your data first, though! As reliable as the process is -- and I've found it more reliable than Windows -- there's always that chance.)

---

### Post by donkyhotay on 2009-01-20
You can do anything with linux that you can do with windows, except use overpriced proprietary commercial software. Definitely use wubi first as it's the safest way to try it out without affecting your system.

---

### Post by linezfanatix on 2009-01-20
I am also a new comer to Ubuntu and i used wubi to install ubuntu without partioning my single drive. It works amazingly well. Just make sure you do a defrag before running wubi. I used jkdefrag on Vista in safe mmode to accomplish that. Good luck. :-)

---

### Post by Joe computer on 2009-01-20
To get to the Run command in Vista:

Click the "windows" button (bottom left hand corner)

In the white space with the cursor (it should say "Start Search"), type run

Press enter

Boom!  There's your run prompt!

:D

---

### Post by Captain_tux on 2009-01-20
Also, not sure if anyone's mentioned it yet, but I think you can get some good use from this tutorial:

[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by wolfen69 on 2009-01-20
> **Joe computer said:**
> To get to the Run command in Vista:

Click the "windows" button (bottom left hand corner)

In the white space with the cursor (it should say "Start Search"), type run

Press enter

Boom!  There's your run prompt!

:D

an easier way: Windows key + R

---

