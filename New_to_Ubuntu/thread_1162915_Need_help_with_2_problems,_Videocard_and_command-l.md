---
title: "Need help with 2 problems, Videocard and command-line installation"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by HugoB on 2009-05-18
Hi

I am very new to Ubuntu Linux and would appreciate some help on 2 problems. 

From what I know (I have an Ubuntu installation CD 8.4 (2008, April) release), this release of Ubuntu had problems with the GeForce 6600 series video cards, giving buggy displays (experienced it myself before).

In the past I fixed this problem by going into Recovery Mode and applying some commands. After the commands were applied, Ubuntu worked well afterwards.

I was trying to setup Ubuntu on a new hard drive and this is what I encountered:

_My first problem is now:_
If I try to boot from the disc to either install / test Ubuntu, the screen (Samsung 720N) goes into a little screensaver block reporting the following:

Not Optimum Mode, Recommended Mode: 1280 x 1024 60Hz

This happens before I can even get into the next GUI screen, so that I can setup Ubuntu properly.

_The second problem is suppose to be a fix on the first problem:_
A possible way to fix the first problem is to somehow do a command-line installation using the Ubuntu disc and then make the GUI interface active somehow afterwards. The problem is that I dont know where to look for commands to perform these tasks. 

"Safe graphics mode" is not working either. It starts up the Ubuntu GUI setup screen and freezes after about 10 seconds during the loading of the setup screen.
 
Hopefully I would be getting the new release of Ubuntu at the end of the week, but do not know if it has any bug fixes for the GeForce video card problems it had for the 8.4 release as well as the screen going into "screensaver mode".

If a forum based on this one has already been posted before, can someone please give me a reference to such a forum? or maybe help me with this one?

Thank you in advance

---

### Post by gettinoriginal on 2009-05-18
Hope this might help, I will continue to look for more help.  
[http://www.linuxquestions.org/questions/ubuntu-63/6600-problems-with-nvidia-geforce-521743/](http://www.linuxquestions.org/questions/ubuntu-63/6600-problems-with-nvidia-geforce-521743/)

---

### Post by HugoB on 2009-05-18
Hi there,

Thank you for the reply :), but I already went through that forum earlier today. It was found that one of the links (that helped the person to solve his problem) at the bottom post was broken and therefor does not help me.

The first thing I wanted to do, was to use a text-based installation approach to solving the problem, but I don't think the Ubuntu Desktop CD has any text-based installation included with it. By now I can tell there is an alternate CD image that could be downloaded from Ubuntu's site that includes a text-based installation for pc's with less resources, but I would need the GUI (GNOME interface) part as well.

After that I wanted to install the GNOME interface on top of the text-based installation (this part I was not sure of), but I don't think that would be possible.

The reason why I wanted to do so, was because both "NORMAL" and "SAFE GRAPHICS MODE" options failed, when I was trying to choose them during boot-time with this machine (AMD Sempron).

_Symptoms observed:_
NORMAL : PC's screen turned into a screen-saver like mode before reaching Ubuntu's setup screen, displaying the following message in a block hovering on the screen:
"NOT OPTIMUM MODE, RECOMMENDED MODE: 1280 x 1024, 60Hz"

SAFE GRAPHICS MODE : Continued to the setup screen, but it just hanged (I was not sure if the computer was loading, no progress lights showed any indication of a machine being alive)

I honestly don't know what to do, but I will keep looking through forums.

Thank you for trying to help :)

---

### Post by Cheesemill on 2009-05-18
You can use the alternate CD to do a command line install.
You then just need to type in
```
sudo aptitude update && sudo aptitude -y install ubuntu-desktop
```
and you will end up with a full Ubuntu install.

Cheesemill

---

### Post by HugoB on 2009-05-18
Hi

Thanks for helping out there. First I need to download an image of the Ubuntu Alternate installation, before the command could really be tested.

I will let you know through this forum if it worked.:)

---

### Post by Bearly Able on 2009-05-18
I used the alternative CD to install Xubuntu on an old computer with very little RAM.  It installs the full version, GUI and all, so I imagine the Ubuntu alternative CD is the same and will include the GNOME desktop.

---

### Post by anewguy on 2009-05-18
And....probably a dumb question, but when everything looks hosed up, have you tried holding down ctrl&at and pressing F1 to see if you get a terminal login?

Do you remember if in the past you used Envy (for the new releases it is Envyng) to install the driver?  If you can get to a terminal login, then you could install envy via sudo apt-get install envyng-cor envyng-gtk

To run it after it is installed I believe the syntax is sudo envyng -t


Dave :)

---

### Post by HugoB on 2009-05-18
Hi anewguy

I still need to get Ubuntu to work properly, by downloading the Alternate Ubuntu image file. 

From my understanding (as a complete beginner in Linux) the CTRL, ALT + F1 trick would be useless if you can't get a copy of Linux running on a machine (which is my current situation).

Will probably be giving attention to it for tomorrow, but I will try and keep everyone informed who started reading at the beginning of the forum.

Thanks for everyone's support. Really appreciate it. :)

---

### Post by anewguy on 2009-05-18
> **HugoB said:**
> Hi anewguy

I still need to get Ubuntu to work properly, by downloading the Alternate Ubuntu image file. 

From my understanding (as a complete beginner in Linux) the CTRL, ALT + F1 trick would be useless if you can't get a copy of Linux running on a machine (which is my current situation).

Will probably be giving attention to it for tomorrow, but I will try and keep everyone informed who started reading at the beginning of the forum.

Thanks for everyone's support. Really appreciate it. :)

Oooopppppssss - I didn't read your post correctly!  Sorry!  I was also thinking - I know you can boot Linux with things like vga=774, etc., in the bootlin line - I wonder if you can do this somehow (or if it would even apply) when you are trying to install?  It's been a while, but I remember seeing that option (might be a different number after vga=) for people having trouble booting the livecd - I think you can press esc and edit the bootlin line for the test without installing and the install lines both (if you get to that screen).

As already mentioned, the alternate CD will have you go via a command line and old line graphics windows, but it does still install the GUI - by default Ubuntu it would be Gnome - and will try to boot that after the install.

Dave :)

---

### Post by HugoB on 2009-05-19
Hi everyone.

I would like to share my latest experiences about Ubuntu with you! :)

I downloaded the alternate boot cd (the latest release) of Ubuntu earlier this morning. The image was burned to a disc and really wanted to get it to work again.

Booting with the disc the first time, it was found that the Ubuntu boot menu looked slightly different from the standard desktop Ubuntu installation cd (which was version 8.4). From all the forums that was posted this far, it is important to remember that I first used Ubuntu 8.4 Desktop Install CD, and now I downloaded the Ubuntu 9.4 Alternate Image to attempt installing it again.

Back to the boot menu of Ubuntu 9.4 Alternate Install. The install option was chosen on the boot screen. The install went very well (just followed the on-screen instructions) and thought that it would only install the command-based system, but instead Ubuntu installed the GNOME interface on top of the command-based system by itself (big relief).

As part of being new in learning Ubuntu, it was my responsibility to mess things up. After the first install, a very professional log-in screen appeared and I was very excited to get going. I logged in. At this stage I knew that my video card would be giving problems if I didn't handle things correctly. I saw a little icon appearing saying that the video drivers had to get an update.

I dubble-clicked the icon and clicked the activate button. A menu appeared stating that it was preparing to update. The update process was taking too long, and decided to look for manual install driver on the internet from Nvidias website. Before I did, I tried closing the update window and it didn't close. Having this problem I restarted the machine instead and couldn't access the GUI interface again. I was left with a command-based system that I struggled handling myself.

The next problem I received was:
The X server is now disabled. Restart GDM when it is configured correctly.

_First approach:_
Looking up useful forums on Ubuntu's website, some suggested to modify a file located at /etc/X11/xorg.conf. Some had success, I didn't. 

This was attempted by running the following command:
sudo gedit /etc/X11/xorg.conf

It said that the file could not be found. mmm.

_Second approach:_
Other people even suggested to run the command: sudo dpkg-reconfigure xserver-xorg

Change the video mode to vesa, I was not sure if the mode was set to vesa, because I only had two options to chose from: yes / no. Anyway trying both options, no success.

_Third approach:_
I tried that command suggested (2 times) earlier on the forum:

sudo aptitude update && sudo aptitude -y install ubuntu-desktop

I was left with some processes running (the command did work), but it was not fixing the GUI problem.

Now to do the right thing.

I was left with only one option (back to the drawing board). Ubuntu had to be reinstalled in order to get access to that GUI interface once again (only had one attempt). If something went wrong the first time using the GUI interface and installing the video drivers not correctly the first time, I had to do a reinstall once again of Ubuntu, because I'm not sure how to handle it correctly.

After the second installation, I tried to auto-update the video driver again, but operation for update timed out reporting the following message:

"Sorry, the Jockey backened crashed. Please file a bug at ubuntu-bug jockey-common. Trying to recover by restarting backened."

I was slowly starting to run ouf of luck, but didn't give up, because it was strongly believed that Ubuntu has got a lot of potential. Reading some more forums on the internet, a very cool program called EnvyNG was discovered. This program manages your graphics card (for Ubuntu and other distributions) by itself, by keeping the video drivers up-to-date. 

Making some changes in the video card settings, it asked me to restart the Operating System. I was very sceptical about this, but thought to myself "Lets do it". Restarting Ubuntu, the GNOME interface appeared the second time and everything seems to be working well now. 

It is hard for me to really make a clear distinction on the different installs, because both versions serve more or less the same purpose, that is to get Ubuntu installed on your system. Except that I got everything to work well with the latest version of Ubuntu, not version 8.4.

---

### Post by anewguy on 2009-05-19
I mentioned envyng in one of my replies, so I'm glad that part worked for you.

Do you have any problems left yet or is everything going ok?  Remember we are here to help.

Dave :)

---

### Post by HugoB on 2009-05-19
Hi anewguy,

Thanks a lot. :) The problem is now solved. How do I mark the forum as being solved (because I am still new here)?

Forums have always helped me to solve problems. Sometimes it does not help me to solve problems, but I always learn something new just by reading what other people have to say. 

You were all of great help and thank you very much for your support. :)

---

### Post by anewguy on 2009-05-19
They removed the actual link to mark solved, but here is what most of use are doing:

go to your first post that started the thread

click edit

click advanced

add [SOLVED] to the front of the title

save

It doesn't usually change what's in the index, but at least when someone goes to the thread they know it's solved.

Later!

Dave :)

---

### Post by D4VOBRO on 2009-05-19
Hello all...
W00t first post!

Sorry to do this but i am completely new to linux and don't know ho these forums work but anyway... how do you get the command line up at boot. i have to remove fglrx
thanks in advance

---

### Post by anewguy on 2009-05-19
Either boot in recovery mode, or at the time that the gui appears do the following:

hold down ctrl-alt and press F1

login using your normal user name and password

do what ever you need to do to remove fglrx - this may involve editing xorg.conf, and if so, do it this way:

cd /etc/X11

sudo cp xorg.conf xorg.conf_save

sudo gedit xorg.conf

make your changes and exit

type exit to close the terminal window

either reboot, or just restart X via ctrl-alt-backspace.

Dave :)

---

### Post by HugoB on 2009-05-20
Hi anewguy

Thank you. I will try that :)

Hello D4VOBRO. I am also very new to Ubuntu myself, but reading the post of anewguy, try that first.

Let us know if your problem was solved.

Good luck :)

---

