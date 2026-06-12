---
title: "Ubuntu detests updating my video drivers"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by darkvoid86 on 2011-04-05
I am a total newb when it comes to Linux and Ubuntu.  I have heard about the rave reviews, ease of use and security with using Ubuntu so I decided to give it a go on my laptop.  

The 10.10 version of Ubuntu installed smoothly and things looked good, however setting up programs such as Evolution for my mail wasn't going too smoothly.  I could not scroll down or drag to see the bottom of the window to click "forward" to begin the setup process.  I presumed this must be a problem due to having too low of a resolution.  The "Monitors" section would only let me go up to 800x600 so I then presumed that all I needed to do was install a driver.  Sure enough "Aditional Drivers" came up with three options.  Either:

1.  Install NVIDIA Accelerated Graphics Driver (version 173)
2.  Install NVIDIA Accelerated Graphics Driver (version current) [Recommended]
3.  Software Modem

Obviously I discarded option 3 for the moment.  I took option 2 because it implied I ought to..... it seemed to install perfectly and requested that I restart my computer for changes to take effect.  Upon restart I would see the normal jargon and then before it would go onto anything to do with Ubuntu the screen would go blank before then going white with a faint grid all over it.

I went nuts because there seemed like there was nothing I could do, pressing the arrow keys resulted in doing down a menu I couldn't see and only the options I was on were block highlighted.  So I reinstalled Ubuntu again off the USB stick and tried option 1 instead.  Upon restarting again, instead of going to a white screen, I briefly got:

Ubunto 10.10

...._" Starting ClamAV virus database up
dater freshclam
" Starting MTA
speech-dispatcher disabled: edit /etc/default/speech-dispatcher
" PulseAudio configured for per-user sessions
saved disabled: edit /etc/default/saved
" Enabling additional executable binary formats binfort support
" Checking battery stats

(I did my best transcribing this from a still taken from filming the start up process on my mobile phone)

But next the screen goes blank but still with the backlight on and then next the screen turns itself off altogether.  I am then forced to just turn off the computer by pressing down on the power button.  When I next turn on the laptop I plug in my USB key with Ubuntu, to begin reinstalling the OS again, but I receive around 5 options on how I would like to proceed starting up.  I can't remember what they were but I chose one and it then goes to another white screen very similar to the aforementioned one.

I have searched a ton on forums for solutions.  However I am ignorant of how to understand and use all the text commands listed.  I even tried to search about the hardware in my computer through Ubuntu and google results had even more text commands.......  

If Ubuntu is more reliable, stable and secure than windows then I am all up for learning all the ins and outs, and I apologise to anyone who must find me so cliche for someone so inexperienced.  Please help me!

---

### Post by davidmohammed on 2011-04-05
hi there and welcome to the forums.

Occasionally the drivers themselves need a little help to get going.  Can I suggest you try the following

one the menu thing (that is called your grub) - type e

find the line ending "quiet splash" - add the word "nomodeset" before "quiet splash"

i.e. the line should read

"... nomodeset quiet splash --" etc

Press CTRL + X to boot.

Does this get you to a desktop?

---

### Post by darkvoid86 on 2011-04-06
I could not follow what you said, apologies, I lost patience and reinstalled Ubuntu again off the USB drive.  However a strange thing occured this time, upon loading up to my desktop everything was in an insane resolution, 1440/960 I think?

I went into the monitor options and sure enough there was all the options for resolution going up to this.  I reduced it down to 1024/768 and was very happy.  I proceeded to install the hundreds of updates Ubuntu was asking for and obviously declined installing anything from NVIDIA before shutting down the laptop, to apply the changed, and opening it up today.  

UNFORTUNATELY when turning the laptop back on I found myself back at square one...... the resolution was automatically reduced to 800x600 and I cannot go any higher again........... oh and for some reason the refresh rate went from 60hz, when it was working as it should, up to 61hz (which is what it was at before when it could only go up to 800x600, I don't know if this information helps?)

AAAAAAAAAAAAAAAAAAAAAAAAAAAH!

In regards to your post, davidmohammed, I didn't know which instance you wished for me to click at the "top" and find the "grub" to type things in or how to summon it.  I managed to be able to run Ubuntu off the USB and that is how I have been able to write these posts on the forum before starting all over again......

---

### Post by darkvoid86 on 2011-04-06
I did some more reading, is it "TERMINAL" under Applications/Accessories that you use to type all the commands that I have read about on the internet?

---

### Post by searchfgold6789 on 2011-04-06
> Occasionally the drivers themselves need a little help to get going.  Can I suggest you try the following

one the menu thing (that is called your grub) - type e

find the line ending "quiet splash" - add the word "nomodeset" before "quiet splash"

i.e. the line should read

"... nomodeset quiet splash --" etc

Press CTRL + X to boot.

Does this get you to a desktop?     Here's the process step by step:

[LIST=1]
[*]Reboot. When it comes time to select your Operating system (you have to press Enter here to boot to Ubuntu), press "E" on your keyboard.
[*]Using your keyboard, find the line that ends in "quiet splash". Edit the line so that it says ```
nomodeset quiet splash
``` at the end of the line.
[*]Save and exit by pressing Ctrl and X at the same time.
[/LIST]
If you need different instructions, feel free to post back and I will suggest a video.
 - search

P.S.
When you find a command on the internet, unless it is specified otherwise, yes enter it into the terminal. If the command has to be run as root, put "sudo" before the command.

---

### Post by darkvoid86 on 2011-04-06
I only have Ubuntu on this computer so there is no screen to choose from different operating systems.  I restarted the laptop and tried pressing "e" at various points after the first start up screen that lets you access your booting options to no avail.

The instructions to find "quiet splash" and put "nomodeset" before it in the "grub"...... what was that intended to do? Was it a resolution fix or something else?

---

### Post by Elfy on 2011-04-06
reboot - once bios has finished - hit shift when grub is starting - then you'll be able to follow what you've been asked to do

what you are in fact doing is adding an option to the boot - once 

if it works you'll need to add it to the grub conf file

---

### Post by darkvoid86 on 2011-04-06
Hmmmm, I tried tab at various points and my computer proceeded to load up to my desktop........

---

### Post by davidmohammed on 2011-04-06
hi there,
  just after the bios splash screen press and hold the shift key.  This will display your grub menu containing various kernels.

---

### Post by Elfy on 2011-04-06
> **darkvoid86 said:**
> Hmmmm, I tried tab at various points and my computer proceeded to load up to my desktop........

whoops - sorry about that - it's a long long time since I needed to do anything to see the grub menu.

---

### Post by darkvoid86 on 2011-04-06
I am guessing the splash screen is where I am given the option to press F2 to go into setup mode when I first turn the computer on.  I held down Tab right after this and instead my computer proceeded to load up normally.

In case I was wrong I restarted the computer and held down tab right after you see the Ubuntu logo appear on a purple back drop, with five dots underneath that change from white to orange in sequence from left to right.  I also tried holding down tab when this image appears as opposed to afterwards........ no joy.

Are you supposed to install Grub or does it come with it already?  Everyone has generally been so clear with their instructions........ I really don't understand where I am going wrong........

---

### Post by alphacrucis2 on 2011-04-06
> **darkvoid86 said:**
> I am guessing the splash screen is where I am given the option to press F2 to go into setup mode when I first turn the computer on.  I held down Tab right after this and instead my computer proceeded to load up normally.

In case I was wrong I restarted the computer and held down tab right after you see the Ubuntu logo appear on a purple back drop, with five dots underneath that change from white to orange in sequence from left to right.  I also tried holding down tab when this image appears as opposed to afterwards........ no joy.

Are you supposed to install Grub or does it come with it already?  Everyone has generally been so clear with their instructions........ I really don't understand where I am going wrong........

Use the SHIFT key. Not TAB.

---

### Post by darkvoid86 on 2011-04-06
I read something online about accessing grub from the terminal and all you do is type "grub".  What it told me was that Grub was not installed and that if I wanted it to be, I needed to type:

sudo apt-get install grub

So I did and I am guessing it is installed, when I type "grub" into the terminal I now have options.  I tried to hold tab after doing this following the splash screen and still no joy.........

---

### Post by darkvoid86 on 2011-04-06
> **alphacrucis2 said:**
> use the shift key. Not tab.

holy ********* i am such a douche

---

### Post by darkvoid86 on 2011-04-06
YAY, I have opened up the grub and added the "nomodeset" as requested, I still don't really understand what I have achieved by doing this but I am game.  What to do next?

I am obviously far too ignorant and really need to study up and learn everything and anything I can about Ubuntu.  I found some guides online to get me started from a website called dedoimedo.com regarding dual booting, commands, configurations and grub boot loading.  Is the website and topic choices the right place/way to start from where I am? i.e. scratch.....

---

### Post by darkvoid86 on 2011-04-07
I turned on my computer for the first time today and my resolution problems have gone away again........ is this a permanent change or is there a chance it will go back again.....?

---

### Post by Elfy on 2011-04-07
If you have just added the nomodeset to the boot line from the grtub menu then it needs to be added to your grub file to make it permanent.

Edit the file as root - back it up first.

```
sudo cp /etc/default/grub /etc/default/grub.bak
```to backup

```
gksudo gedit /etc/default/grub
``` will open the file as root for editing

Find the line with quiet and splash and add in nomodeset so it looks like 

nomodeset quiet splash

I think that it is between " " - make sure it still is.

Then save the file.

Now update grub

```
sudo update-grub
```

---

### Post by darkvoid86 on 2011-04-08
okey doke, I am going to write my interpretations of your instructions so that there is little room for me to make a major newb mistake.

"Edit the file as root" means, edit it as administrator? (I believe my profile as it is gives me all administrator privileges)

1.  Open up the terminal and type:

sudo cp /etc/default/grub /etc/default/grub.bak

this will instantly back up the default settings of "grub" itself?

2.  Next type in the terminal on the next available command line:

gksudo gedit /etc/default/grub

This will either take me to a black and white screen or open a window where I can text edit the grub settings as administrator.

3.  Find the line with "quiet splash" again and add to make "nomodeset quiet splash", quotations marks will be there and must be kept.  (the last time I did this, "quiet splash" had three spaces before it and the last bit of text, if this is the case again, do I need to keep those three spaces before "nomodeset quiet splash"?)

4.  Save the file.  (this eludes to me that I am editing a text file like you would with notepad in windows and it is a simple process of just clicking save under "FILE" at the top?)

5.  Go back to the terminal and type:

sudo update-grub

This will transfer the changes to the text file to the actual grub itself?

Again guys, apologies for my ignorance.  I plan to be doing a lot of reading on the websites mentioned before to educate myself, unless someone knows a better set of guides?

---

### Post by Elfy on 2011-04-08
> "Edit the file as root" means, edit it as administrator? (I believe my profile as it is gives me all administrator privileges) - Yes

> 1.  Open up the terminal and type:

sudo cp /etc/default/grub /etc/default/grub.bak

this will instantly back up the default settings of "grub" itself? - Yes 

> 2.  Next type in the terminal on the next available command line:

gksudo gedit /etc/default/grub - 

This will either take me to a black and white screen or open a window where I can text edit the grub settings as administrator.Should open the file in gedit, gksudo is the 'graphic type' sudo - you'll need your normal password 


> 3.  Find the line with "quiet splash" again and add to make "nomodeset quiet splash", quotations marks will be there and must be kept.  (the last time I did this, "quiet splash" had three spaces before it and the last bit of text, if this is the case again, do I need to keep those three spaces before "nomodeset quiet splash"?) - Working from memory (using fedora atm and it uses grub legacy) there were no spaces in mine. So "nomodeset quiet splash"

> 4.  Save the file.  (this eludes to me that I am editing a text file like you would with notepad in windows and it is a simple process of just clicking save under "FILE" at the top?)Yes - the file is a text file that is used to setup (along with some other files) grub.

> 5.  Go back to the terminal and type:

sudo update-grub

This will transfer the changes to the text file to the actual grub itself?Yes 
> 
Again guys, apologies for my ignorance.  I plan to be doing a lot of reading on the websites mentioned before to educate myself, unless someone knows a better set of guides?No worries.

Grub - [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Root - [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

