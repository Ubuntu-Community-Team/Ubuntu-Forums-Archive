---
title: "Help the n00b!!"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by brianfantastic on 2009-02-12
Hey there guys and girls. First of all id like to say im an ABSOLOUTE beginner. I downloaded and installed ubuntu because ive head great things about it.

Id consider myself an intermediate pc user, but since switching to ubuntu i feel like a 3 year old who needs to circumnavigate the globe using only his wits.

My problem.

I need to install graphics card drivers. My card is an ATI radeon HD 4670 sapphire. I go to ATI's website and download the linux driver. Low and behold it appears on my desktop as a .run file. I click it and nothing happens. Now this is where i draw the blank. I know im an utter noob. I want to know how to make the file run and install the drivers. I feel like such an idiot because i cant make it do *anything...* If you need any more info in order to help me just let me know.

Guys, any and all help will be appreciated, i really have fallen in love with ubuntu and id love to keep it, but if i cant even get my head around installing a simple set of drivers then i think im going to have to go back to *shudders* windows. 

Please help!

---

### Post by kdreimiller on 2009-02-12
follow the installation instructions on ATI's website.  their install instructions work just fine.

---

### Post by kanikilu on 2009-02-12
See if either of these guides answer your question:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

OR

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by DGortze380 on 2009-02-12
> **brianfantastic said:**
> Hey there guys and girls. First of all id like to say im an ABSOLOUTE beginner. I downloaded and installed ubuntu because ive head great things about it.

Id consider myself an intermediate pc user, but since switching to ubuntu i feel like a 3 year old who needs to circumnavigate the globe using only his wits.

My problem.

I need to install graphics card drivers. My card is an ATI radeon HD 4670 sapphire. I go to ATI's website and download the linux driver. Low and behold it appears on my desktop as a .run file. I click it and nothing happens. Now this is where i draw the blank. I know im an utter noob. I want to know how to make the file run and install the drivers. I feel like such an idiot because i cant make it do *anything...* If you need any more info in order to help me just let me know.

Guys, any and all help will be appreciated, i really have fallen in love with ubuntu and id love to keep it, but if i cant even get my head around installing a simple set of drivers then i think im going to have to go back to *shudders* windows. 

Please help!

Follow any ATI instructions you can find for that card.. but my guess you'll need to right click and hit 'Run in Terminal'

---

### Post by perlluver on 2009-02-12
Will the restricted drivers not work for you?  System>Administration>Hardware Drivers.

---

### Post by brianfantastic on 2009-02-12
Ok guys, firstly thanks for the quick response's.

Let me try and expand on the problem im having. Ive got the install instructions from ATI sitting in a PDF file on my desktop open and read. But the actual installation its self isnt the problem. Because i cant get to that stage. The problem is when i click the file "ati-driver-installer-9-1-x86.x86_64.run" I get this exact message "Could'nt display "/home/shayn/desktop/ati-driver-installer-9-1-x86.x86_64.run  - there is no application installed for this filetype"

---

### Post by kdreimiller on 2009-02-12
unless your install instructions were different from mine (i have a radeon 3100, but i think all install directions are the same), you do the install from the terminal, no clicking on the downloaded file.

go to the terminal and try this:
 sh ./ati-driver-installer-8.573-x86.x86_64 

that should start the automatic installation and bring up a gui to follow thru

**edit** which version of the driver are you trying to install.  ive mistakenly assumed you meant the latest 9.1.  but realized i made a bad assumption when i could find you graphics card listed

**edit2** duh, yeah, you are trying the 9.1 so that sh ./ati command  should work

---

### Post by brianfantastic on 2009-02-12
did what you said and i got the following

"shayn@shayn-ubuntu-desktop:~$ sh ./ati-driver-installer-8.573-x86.x86_64
sh: Can't open ./ati-driver-installer-8.573-x86.x86_64
shayn@shayn-ubuntu-desktop:~$ 
"

any ideas?

edit: im installing th hd4800 series driver. which is the right 1 for the card.

---

### Post by kdreimiller on 2009-02-12
im not sure.  i dont remember if i had to switch to the directory the driver was in to run that command.  try that.  

if that doesnt work, download the file and try again?  maybe it got corrupted somehow?  im a bit of a newbie myself, but i didnt have problems installing 9.1.  i had some hiccups with it after i installed it but i got everything back in order finally.

---

### Post by Therion on 2009-02-12
Maybe you need to be "root"?  

Try this (Cut and Paste):

```
sudo sh ./ati-driver-installer-8.573-x86.x86_64
```

Can't remember if this requires root-privs or not...

---

### Post by brianfantastic on 2009-02-12
> **perlluver said:**
> Will the restricted drivers not work for you?  System>Administration>Hardware Drivers.
I dont know what that means? What do i do once im in hardware drivers?

The "hardware Drivers" window opens but its empty and says "no proprietary drivers are in use on this system"


**_-therion,_** i pasted what you told me to into terminal and got this

"shayn@shayn-ubuntu-desktop:~$ sudo sh ./ati-driver-installer-8.573-x86.x86_64
[sudo] password for shayn: 
sh: Can't open ./ati-driver-installer-8.573-x86.x86_64
shayn@shayn-ubuntu-desktop:~$ "

---

### Post by kdreimiller on 2009-02-12
well if you cant get the 9.1 install to work you can use envy NG to install an older version of the ATI drivers.  i dont know why it doesnt install the latest version though.  at least it didnt on my computer.

did you try changing to the directory where you downloaded the file and running that command from there?

---

### Post by avtolle on 2009-02-12
Is the driver downloaded to your desktop? If it is```
cd Desktop
sudo sh ./ati-driver-installer-8.573-x86.x86_64
```

---

### Post by Therion on 2009-02-12
> **kdreimiller said:**
> did you try changing to the directory where you downloaded the file and running that command from there?
This.

Second:  Right-click on the .sh file (the file you downloaded) and "tic" the box for "Allow to run as program".  Try the sudo command again from my previous post.

---

### Post by brianfantastic on 2009-02-12
> **kdreimiller said:**
> well if you cant get the 9.1 install to work you can use envy NG to install an older version of the ATI drivers.  i dont know why it doesnt install the latest version though.  at least it didnt on my computer.

did you try changing to the directory where you downloaded the file and running that command from there?

1. Yes ive tried changing the directory and i still got the exact same errors, thanks for the suggestion though.

2. Whats envy NG? I really am very new with ubuntu. 

Thanks for bearing with me!

---

### Post by kdreimiller on 2009-02-12
it's kind of like an autoinstaller.  it will install the video drivers for you.  i think it might be in the repositories.

---

### Post by donkyhotay on 2009-02-12
The 'restricted drivers' tool that comes with ubuntu is great but sometimes has issues with ATI drivers. I've never gotten it to work with my radeon X700 and ended up using that exact same installer you said you downloaded. Here is what you need to do, first of all be aware this requires using the CLI (terminal) but don't be scared, it'll quickly become your best friend if you use linux any length of time. I'm also assuming you downloaded the file onto your desktop which is the default location. First of all go to applications > accessories > terminal. This will bring up a terminal prompt and look like an old DOS prompt if you're familiar with that. In the terminal copy and paste the following commands
```
cd ~/Desktop
chmod 744 ./ati-driver-installer-9-1-x86.x86_64.run
gksudo ./ati-driver-installer-9-1-x86.x86_64.run
```
follow the GUI prompts. If you're uncertain just use the defaults selected values. Finish that, reboot the computer, you're ready to go.

---

### Post by brianfantastic on 2009-02-12
Ok i was playing around with the name of the file because and i changed the .run extention accidentally to something random, and changed it back. Then i dragged and dropped into terminal and i got the following...

"shayn@shayn-ubuntu-desktop:~$ '/home/shayn/Desktop/ati-driver-installer-9-1-x86.x86_64.run' 
Created directory fglrx-install.gA8375
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.573...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.1 7.2 7.3
Removing temporary directory: fglrx-install.gA8375
shayn@shayn-ubuntu-desktop:~$ 
"
a window popped up before i got "Removing temporary directory..." 

and said "You need to run this as a super user"

Whats that? Sorry for my utter noobishness

---

### Post by brianfantastic on 2009-02-12
> **donkyhotay said:**
> The 'restricted drivers' tool that comes with ubuntu is great but sometimes has issues with ATI drivers. I've never gotten it to work with my radeon X700 and ended up using that exact same installer you said you downloaded. Here is what you need to do, first of all be aware this requires using the CLI (terminal) but don't be scared, it'll quickly become your best friend if you use linux any length of time. I'm also assuming you downloaded the file onto your desktop which is the default location. First of all go to applications > accessories > terminal. This will bring up a terminal prompt and look like an old DOS prompt if you're familiar with that. In the terminal copy and paste the following commands
```
cd ~/Desktop
chmod 744 ./ati-driver-installer-9-1-x86.x86_64.run
gksudo ./ati-driver-installer-9-1-x86.x86_64.run
```
follow the GUI prompts. If you're uncertain just use the defaults selected values. Finish that, reboot the computer, you're ready to go.

**WE HAVE A WINNER! I COULD KISS YOU**

Seriously, thanks. Ive got the GUI installation screen up now. 
ALthough im greatful for you giving me the information, could i be a pain in the neck and ask what it all means? Id like to know incase i encounter the problem again. It doesnt matter if you dont have time to explain, THANKS AGAIN! w00t!

---

### Post by kdreimiller on 2009-02-12
yeah there ya go.  just follow the directions on the window.  its a cinch. ;)

super user is when you act as administrator.  its preceded by the sudo command, where linux will prompt you for your password after that.

---

### Post by donkyhotay on 2009-02-12
super-user is root, what you did was the same as 
```
./ati-driver-installer-9-1-x86.x86_64.run
```
you need to put either sudo or gksudo in front of a command to launch it as root. Per my previous post per my previous post you will want to use gksudo for this particular program. Just follow the instructions I gave you exactly in my previous post and it will work.

---

### Post by kdreimiller on 2009-02-12
now i have a question.  when i installed it, i didnt use gksudo, im not totally sure i used sudo.  but the question is, whats the difference between gksudo and sudo?  and why did he need to use gksudo instead of sudo?

---

### Post by donkyhotay on 2009-02-12
> **brianfantastic said:**
> [B]ALthough im greatful for you giving me the information, could i be a pain in the neck and ask what it all means? Id like to know incase i encounter the problem again. It doesnt matter if you dont have time to explain, THANKS AGAIN! w00t!

No problem, this stuff is important in learning some very vital and important differences between windows and linux. First of all
```
cd ~/Desktop
```
just means that you navigated to your desktop
```
chmod 755 ./ati-driver-installer-9-1-x86.x86_64.run
```
means that you are taking the file ati-driver-installer-9-1-x86.x86_64.run located within the current directory (which is desktop per the previous command) and allowing the current user to read, write, & run the program while allowing everyone else the ability to only read it. This is the most important one and honestly by this point you could have just 'double-clicked' on the file to run it. By default you can not just 'run' a binary file in unix (equivalent to executable in windows) unless you have permission to do so. By default you DON'T have permission because of security concerns. So you have to tell the computer that you want to be able to run the file first. Once you've done that it's simply a matter of running the file however even though you have permission to run it, this program requires root access in order to be able to install system-wide. This is yet another security restriction put in place to protect you. So the last command
```
gksudo ./ati-driver-installer-9-1-x86.x86_64.run
```
means that you want to run the graphical program ati-driver-installer-9-1-x86.x86_64.run located in the current directory (still desktop) as root. If you were running a non-GUI program (such as nano for example) you would instead use the sudo command instead. A good example of this is gedit and nano, both are text editors and do the exact same thing but one is a GUI and the other is CLI. So you get
```
sudo nano
```
compared with
```
gksudo gedit
```
From a windows perspective the whole thing about root access and telling the computer you want to be able to execute the program is odd but it is *very* secure. These protections are the main reason it's difficult (though not impossible) for a virus to affect a linux system as compared to windows, and why all linux viruses are more theoretical constructs then something 'out in the wild' that will actually infect your system.

//edit: using sudo when you should use gksudo and vice-versa isn't that big of a deal. It's best to do it right as sometimes you'll accidently get files you can't delete without root access in your home folder but nothing thats going to harm your system in any way. Another useful tool you may want to download is nautilus-gksu which is allows you to right-click on a file and run it as root. If you want to install that it's available in synaptic or you can just 
```
sudo apt-get install nautilus-gksu
```
to install as well. Be aware you'll need to relaunch X for it to take effect and if you're learning the easiest/safest way of doing that is to just restart your computer.

---

### Post by brianfantastic on 2009-02-12
Thanks!

New problem (I know its laughable, id be laughing too if it wasnt so damn annoying)

Ive got the GUI screen up, but my resoloution is so low that it doesnt fit all of the GUI on the monitor and i cant resize the window, hense i cant click on the buttons to go to the next screen. And i cant find any resoloution settings anywear, any ideas on this ? Im so close i can taste it... lol

---

### Post by donkyhotay on 2009-02-12
Ran into that too, wish ATI would fix that with their graphics installer, they should assume anyone using this program *doesn't* have good graphics or screen resolution. The first button that isn't visible is the ok button. After selecting what you want hit 'tab' until the cursor vanishes. You will then have the 'ok' button highlighted 'below the screen' and can then just hit 'enter'. You'll then continue to the next page. You'll probably need to do that a few times until the installer actually finishes.

---

### Post by brianfantastic on 2009-02-12
> **donkyhotay said:**
> Ran into that too, wish ATI would fix that with their graphics installer, they should assume anyone using this program *doesn't* have good graphics or screen resolution. The first button that isn't visible is the ok button. After selecting what you want hit 'tab' until the cursor vanishes. You will then have the 'ok' button highlighted 'below the screen' and can then just hit 'enter'. You'll then continue to the next page. You'll probably need to do that a few times until the installer actually finishes.

Didn't work :( cant i change the resoloution manually so i can see the rest of the window?

It worked just had to give it a couple of shots and use the numpad enter button.

---

### Post by donkyhotay on 2009-02-12
> **brianfantastic said:**
> Didn't work :( cant i change the resoloution manually so i can see the rest of the window?

It's a can opener inside of a can type of problem, you can't change the resolution high enough until it's installed, but it's hard to install without a high enough resolution. A serious design flaw by ATI IMHO, especially since 90% of the installer screen is a blank gray and it could easily be smaller. I hit tab and enter to navigate when I install that driver, the most recent time was about a month ago so maybe I was wrong about the button placement. Try hitting 'tab' twice then 'enter'. It may take some trial and error to get the order right but keyboard navigation *does* work even though you can't see what you're doing.

---

### Post by brianfantastic on 2009-02-12
ahh the old catch 22.

I managed to blindly fumble my way through the installation and the drivers are all set up now. And i can tell you it was stressing me out to the point of me thinking "Is the juice worth the squeeze" 
It is now however, sorted. And thankyou for explaining the commands you had me type into terminal, i like to know why im doing something and not just do it.

So thanks for that !

---

### Post by donkyhotay on 2009-02-12
Glad you were able to get it working! I remember fumbling my way through that same problem when I migrated to linux a few years ago and how much of a pain it was. Once you get more comfortable using linux remember to come back to these forums from time to time to help out the next person who is starting out for the first time.

---

