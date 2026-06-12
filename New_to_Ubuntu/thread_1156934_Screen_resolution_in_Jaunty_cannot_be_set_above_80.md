---
title: "Screen resolution in Jaunty cannot be set above 800x600"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by VgnStirfry on 2009-05-12
Newly upgraded to Ubuntu 9.04 (Jaunty).  From a brief Google search I have determined that some users are experiencing problems with screen resolution.   Many of the discussions involve more technical knowledge than I have.

Does anyone know whether this problem can be fixed?  
Can anyone direct me to (or provide) troubleshooting instructions? 

An anticipatory thank-you!

---

### Post by stephanvaningen on 2009-05-12
Can you specify your hardware info on graphical chipset?

lspci

---

### Post by MikesGuitar on 2009-05-12
Not sure what graphics card you have but I had that problem with my Dell inspiron with an nVidia card. The card and the typical display manager cannot link up, and when I would set things in the nVidia manager they would swith back after i logged back in. When I would open the display manager a message would tell me there was an error and if I want to use the nvidia manager. I just hit no and the regualr display manager would open (not be able to detect my settings) but when I fixed my resolution in that it has worked fine. Hope this helps in some way

---

### Post by Didius Falco on 2009-05-12
If you run a slightly modified version of the command stephenvaningen recommended, it will filter out a lot of the unneeded info:

Open a Terminal (**Applications/Accessories/Terminal**) and type ```
lspci | grep VGA
``` - That is a "pipe" not an l or an i. Then copy and paste the info it returns here - it will tell us what video card/chip you have.

Next, type```
 xrandr
``` - that will tell us what resolutions your hardware will support.

Then we can help you more easily.

Regards,

Didius

---

### Post by stephanvaningen on 2009-05-12
Thanks for the clarification :)> **Didius Falco said:**
> If you run a slightly modified version of ...

---

### Post by VgnStirfry on 2009-05-12
Thanks for responding. Here is the information that people have requested:

lspci | grep VGA:[INDENT]00:08.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
[/INDENT]xrandr:[INDENT]Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0 
[/INDENT]lspci:[INDENT]00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)
00:0a.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
[/INDENT] **stephanvaningen**: I didn't realize that "lspci" was an instruction; I thought that was your signature.

---

### Post by stephanvaningen on 2009-05-12
Oh, the S3-things... there rings a bell from some months ago... hmmm, does your system use unichrome drivers? (You can find these in Synaptic Package Manager if you there search for 'unichrome')...

---

### Post by VgnStirfry on 2009-05-12
**stephanvaningen**: I searched Synaptic for "unichrome", the only installed package with that string is **xserver-xorg-video-openchrome**.  

I don't know what other drivers (if any) are in use, but I can retrieve more info if you give me instructions.

---

### Post by Didius Falco on 2009-05-12
> **stephanvaningen said:**
> Thanks for the clarification :)

No problem - I learned that when I asked someone to post the "lspci" info and someone else posted about that. That's how it works - next, you'll be passing that on to someone else, and so on. :)

VgnStirfry - according to that "xrandr" output, the best you can do at the moment is 800x600, which you are already getting.

I looked up that chipset, and I don't think you are going to be able to use 3D effects with it. Even if you could get it working, it would make your PC very slow - that chipset offloads a lot of the video card work onto the CPU.

I am curious, though - what kind of monitor do you have?

Regards,

Didius

---

### Post by Didius Falco on 2009-05-12
> **VgnStirfry said:**
> **stephanvaningen**: I searched Synaptic for "unichrome", the only installed package with that string is **xserver-xorg-video-openchrome**.  

I don't know what other drivers (if any) are in use, but I can retrieve more info if you give me instructions.

Search Synaptic for **xserver-xorg-video-savage**  I'd bet that is already installed, too.

Regards,

Didius

On Edit: I just pretty much confirmed that Compiz will not work with that chipset...Sorry about that.

---

### Post by VgnStirfry on 2009-05-12
**Didius**: 

[LIST]
[*]*xserver-xorg-video-savage* is installed.
[*]My monitor is a **Sony Trinitron Multiscan 420GS**, and I know it's capable of resolutions higher than 800x600: I can't recall exactly, but I remember that my previous resolution was "four digits by four digits", as you'd say.
[/LIST]
Luckily, I don't need 3D effects: I just need to be able to view webpages at a reasonable (i.e. readable) resolution.  And yes indeed, I hope to pass along what I learn here.  Here's hoping that it sticks. :)

Anyway... any ideas?

---

### Post by VgnStirfry on 2009-05-12
> **Didius Falco said:**
> On Edit: I just pretty much confirmed that Compiz will not work with that chipset...Sorry about that.

I appreciate you looking into it.  I don't know what Compiz would provide me, but I think I may never have been using it: one of my friends looked at my machine months ago and, as I recall, they remarked that something related to 3D graphics acceleration was not enabled at the time.  However, at the time I was using a resolution higher than 800x600.  

Any ideas?

---

### Post by halitech on 2009-05-12
this is the downside to having X autoconfigure things. 

You could try the info here:[http://forums.debian.net/viewtopic.php?f=16&t=26577](http://forums.debian.net/viewtopic.php?f=16&t=26577)

Hopefully you can set things up manually and have it work

---

### Post by Bartender on 2009-05-12
I'll assume you have an AGP port or maybe some version of PCI-X available.

Instead of fighting the S3 chipset, buy a basic Nvidia graphics card, turn off and unplug the PC, install the Nvidia card, turn the PC back on, ask Synaptic to Reload, then go to System>Administration>Hardware Drivers and "Activate" whatever Nvidia package is identified.  If you have a broadband connection your PC will download the Nvidia package to your PC.  Shut the PC off, turn it back on, find "Nvidia X Server" under Administration and check the settings.

---

### Post by stephanvaningen on 2009-05-12
If it's for using compiz: try KWin instead for this card...

---

### Post by Didius Falco on 2009-05-12
I take it from the thread title that you have gone to **System/Preferences/Display** and the best it offers is 800x600?

Let's try to reconfigure your xorg.conf file, but first we are going to make a backup of it so that if there is a problem, you can restore the old one. First run ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.800600
```To make a backup copy. If there is a problem and you wind up with a weird looking screen, you can reboot into Recovery Mode and select the Command Line option and run ```
sudo cp /etc/X11/xorg.conf.800600 /etc/X11/xorg.conf  
``` and it will restore the original file. Make a note of that,just in case - and note the capital X in X11, as linux is case-sensitive.

After you've backed up the file, run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```.

After you've finished that, reboot.

Regards,

Didius

On Edit: Three good suggestions right before my post. If you are comfortable editing the xorg.conf by hand, that looks like a good guide to use -I've bookmarked it for further study.

The kwin idea is good as well.

Probably the best of the lot, including mine, is buying a newer video card, if that is feasible for you.

At any rate, you have lots of options now. That's one of the best things about Ubuntu - not only is Ubuntu itself very good, this forum and its members are a compelling reason to use it.

---

### Post by VgnStirfry on 2009-05-12
**halitech**: That is good info, but unfortunately I don't fully understand how to use it. I am concerned that if I edit xorg.conf, and make errors, that I will lose my display entirely and not know how to restore it.  

Do you know of any further tutorials, or any way to do this automatically?  I have found plenty of info, but none that is written for people at my skill level.  Thanks. 

**bartender**: While that is not an option at the moment, I will keep it in mind if things change; thanks. 

**stephanvaningen**: Sorry, I don't understand: if _what_ is for using Compwiz?  Thanks for your help so far.

---

### Post by halitech on 2009-05-12
just make a backup using Didius's first command first
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.800600
```

there's no way to do it automatically, xorg is doing that now which is why you have the issue you do.

---

### Post by VgnStirfry on 2009-05-12
OK, **Didius** and **halitech**, I am editing xorg.conf; I used the gtf tool to give me a modeline for 1280x1024 @ 60Hz.  I am not sure if 1280x1024 will work.  I remember that my preferred resolution only allowed one choice of refresh rate, and I can't remember which it was.  So, I am trying this.

Here is what I have planned for xorg.conf at the moment:[INDENT]  Section "Device"
     Identifier    "Configured Video Device"
 EndSection

 Section "Monitor"
     Identifier    "Configured Monitor"
     Modeline    "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
 EndSection

 Section "Screen"
     Identifier    "Default Screen"
     Monitor        "Configured Monitor"
     Device        "Configured Video Device"
     SubSection "Display"
         Modes    "1280x1024_60.00"
     EndSubSection
 EndSection
[/INDENT]ETA: I did use indents in my xorg.conf text, but they are are not displaying properly here.  They do exist in the real version, if that matters.
Two questions:

[LIST=1]
[*]Do you know of any way to get a list of the resolutions and refresh rates that work with a Sony Trinitron Multiscan 420GS? I could not find anything through Sony's website.
[*]What should I put in for the default depth (as described in the example [here]("http://forums.debian.net/viewtopic.php?f=16&t=26577"))? I don't know what "default depth" means.  Is it necessary to specify a default depth?
[/LIST]

I am going to try this and see; I have the backup and have written down how to restore it.  Thanks for pointing me in the right direction.  Here's hoping you know the answer to the above.

---

### Post by halitech on 2009-05-12
Not sure on the refresh specs

the default depth is the color resolution and 16 should be safe and still give good color.

---

### Post by Didius Falco on 2009-05-12
Here is a link to a PDF with all the resolution and refresh rate specs:

[http://www.docs.sony.com/reflib/docget.asp?manualid=19315&template_id=1&region_id=1&DL=](http://www.docs.sony.com/reflib/docget.asp?manualid=19315&template_id=1&region_id=1&DL=)

My Google-Fu is working pretty well tonight. 8-)

Regards,

Didius

---

### Post by VgnStirfry on 2009-05-12
Hey, that's my monitor!  Wow!  Thanks so much, this is just the information I needed.  What a relief.

> **Didius Falco said:**
> My Google-Fu is working pretty well tonight. 8-)

Clearly.  The 'fu is strong with this one. 

So... two more questions, I guess:

[LIST=1]
[*]What display depth should I be using?  Does that document provide that information?  (I couldn't tell.)
[*]I'm editing xorg.conf from within the terminal, but I can't figure out how to save it; help?
[/LIST]
Wow; this is moving along nicely; thanks so much.

---

### Post by Didius Falco on 2009-05-12
> **VgnStirfry said:**
> 
So... two more questions, I guess:

[LIST=1]
[*]What display depth should I be using?  Does that document provide that information?  (I couldn't tell.)
[*]I'm editing xorg.conf from within the terminal, but I can't figure out how to save it; help?
[/LIST]
Wow; this is moving along nicely; thanks so much.

I'd start with 16, as Halitech suggested. If that works okay, in a couple of days you can bump it up to 24 - which is what Windows calls "32 Bit".

It isn't the monitor that will hold you back, it's the Video card.

Actually, I have the reverse problem - I have a good video card (ATI 4870 PCIE) and a pretty craptacular monitor (Acer AC713) - wanna trade monitors? No!! Oh well...<G>

What editor are you using to edit xorg.conf?

---

### Post by VgnStirfry on 2009-05-12
> **Didius Falco said:**
> What editor are you using to edit xorg.conf?

I think I'm using **GNU nano**.  

Yes, of course I want your crappy monitor... just not in that way.

---

### Post by Didius Falco on 2009-05-12
> **VgnStirfry said:**
> I think I'm using **GNU nano**.  

Yes, of course I want your crappy monitor... just not in that way.

CTRL + X - nano will ask if you want to save the file, type Y and you are all set. I had to look that up - those old editors give me bad Dos editor flashbacks. The horror!!

Regards,

Didius

---

### Post by VgnStirfry on 2009-05-12
OK, so I changed my approach and used gedit to edit xorg.conf.  I saved the file.  I rebooted and it's still in 800x600.  I opened up xorg.conf and all of my changes are still saved.  Do I need to tell the system to use this particular file?  There are other files called "xorg.conf.(various numbers)", including that backup I made.  Please advise.

---

### Post by halitech on 2009-05-12
CTRL + O will save the file then CTRL + X to close

or as Didius says, CTRL + X, say yes and it will save as well

I used to use Gedit for everything then I messed up my GUI so I learned nano basics in a hurry and kinda like it for quick fixes :)

---

### Post by Didius Falco on 2009-05-12
> **VgnStirfry said:**
> OK, so I changed my approach and used gedit to edit xorg.conf.  I saved the file.  I rebooted and it's still in 800x600.  I opened up xorg.conf and all of my changes are still saved.  Do I need to tell the system to use this particular file?  There are other files called "xorg.conf.(various numbers)", including that backup I made.  Please advise.

It'll use the one named "xorg.conf" - the others are just backups. Post the contents of the new xorg.conf file so we can have a look at it. Just copy/paste it and put code (# on the menu bar) tags around it.


Halitech - it'd probably be a good idea for me to do that too, but I just fall back on one of the other 4 installs I have, or the Live CD.

Regards,

Didius

---

### Post by VgnStirfry on 2009-05-12
**Current version of xorg.conf**:
```

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline    "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    DefaultDepth   16
    Device        "Configured Video Device"
    SubSection "Display"
        Depth    16
        Modes    "1280x1024_75.00"
    EndSubSection
EndSection
```Voila.  What did I do wrong?

---

### Post by halitech on 2009-05-12
> **Didius Falco said:**
> 
Halitech - it'd probably be a good idea for me to do that too, but I just fall back on one of the other 4 installs I have, or the Live CD.

Regards,

Didius

I only have Debian installed on this system and I find I can usually fix things faster from the CLI then I can by firing up one of my laptops and figuring things out that way :)

---

### Post by Didius Falco on 2009-05-12
> **VgnStirfry said:**
> **Current version of xorg.conf**:
```

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Modeline    "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    DefaultDepth   16
    Device        "Configured Video Device"
    SubSection "Display"
        Depth    16
        Modes    "1280x1024_75.00"
    EndSubSection
EndSection
```Voila.  What did I do wrong?

Okay, now I'm fishing around the web for answers, which means two things: 1. I can't vouch for any of this working, but it is worth a try. 2. Backup what you've done so far with a name that is meaningful to you, using the command listed earlier. Then add this to the file:

```
Section "Device"
   Identifier "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
   Boardname "savage"
   Busid "PCI:1:0:0"
   Driver "savage"
   Screen 0
EndSection
```

Save, reboot, report back, hopefully in marvelous large-screen technicolor.

Regards,

Didius

---

### Post by Didius Falco on 2009-05-12
Now I'm getting nervous....

---

### Post by VgnStirfry on 2009-05-12
> **Didius Falco said:**
> Now I'm getting nervous....

And rightly so!  :)  I write to you in exile, from a friend's computer.  

I replaced, rebooted, and now I'm getting this looping... situation... where the same error appears again and again.  I haven't found a way to get a terminal session in order to replace xorg.conf with the backup.  I can get into grub, but I don't know if I can do it from there, or what to do. Help?  :confused:

---

### Post by NHArticleTen on 2009-05-12
> **VgnStirfry said:**
> And rightly so!  :)  I write to you in exile, from a friend's computer.  

I replaced, rebooted, and now I'm getting this looping... situation... where the same error appears again and again.  I haven't found a way to get a terminal session in order to replace xorg.conf with the backup.  I can get into grub, but I don't know if I can do it from there, or what to do. Help?  :confused:

Use Jaunty in Live CD mode to get back to your older xorg.conf 

oh, and delete the one that didn't work...lol.

let us know when you're back to a working machine again

no sense in adding any more to this if you've already figured it out

---

### Post by VgnStirfry on 2009-05-12
> **NHArticleTen said:**
> Use Jaunty in Live CD mode to get back to your older xorg.conf

I may be able to make one on my friend's machine, but that may take a while, any other ideas?  (In case we cannot make one or cannot make one quickly.)

---

### Post by Didius Falco on 2009-05-12
Hi,

You should have a **Recovery Mode** option on your **Grub** menu, right under the regular boot. Select that and it'll bring you to a menu, where you should choose **Command Line** or **Command Line with Networking**.

Once you have the Command Line type ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.wip
```That will back up the one you've been working on - we may still be able to get it to work. Then type ```
sudo cp /etc/X11/xorg.conf.800600 /etc/X11/xorg.conf
``` That will restore the original one. Then reboot into 800x600 glory.

Regards,

Didius

On Edit: If your friend has a printer, print out this thread, it'll make it easier to keep the commands straight.

---

### Post by VgnStirfry on 2009-05-12
Hi!  Boy, am I glad to see you.  :)

I tried Recovery Mode, but there is no option for Command Line or Command Line with Networking.  We can only get the grub command line, and we can't su or sudo or anything useful from there.  Any ideas?

---

### Post by Didius Falco on 2009-05-12
What, exactly happens when you try Recovery Mode? That should start booting up...

Didius

(Not sure how much regard you have for me now) <G>

---

### Post by VgnStirfry on 2009-05-12
> **Didius Falco said:**
> What, exactly happens when you try Recovery Mode? That should start booting up...

Didius

(Not sure how much regard you have for me now) <G>

Pshaw, I've got that in spades.  ;)

When I start Recovery Mode, it just starts booting up, but all of the text scrolling by is visible (rather than hidden behind a shiny ubuntu logo).  I can hit "e" for "edit" in order to edit the individual lines (boot, kernel, and so forth) but haven't been able to get a full terminal by any means.  We've got another person trying to troubleshoot over AIM but any further thoughts on the matter would be appreciated (if not helpful :P)!

---

### Post by Didius Falco on 2009-05-12
> **VgnStirfry said:**
> Pshaw, I've got that in spades.  ;)

When I start Recovery Mode, it just starts booting up, but all of the text scrolling by is visible (rather than hidden behind a shiny ubuntu logo).  I can hit "e" for "edit" in order to edit the individual lines (boot, kernel, and so forth) but haven't been able to get a full terminal by any means.  We've got another person trying to troubleshoot over AIM but any further thoughts on the matter would be appreciated (if not helpful :P)!

Okay - that is what you want to see. Don't hit "e" - that interrupts the boot process and takes you to grub. Let the text keep on rolling by and it'll take you to a menu box where you can choose the Command Line option. Once you do that, stand by for a bit more scrolling text and you'll wind up with a command line and a black screen.

That's where you want to be. Then you can do the commands listed above in #36 to backup the current one and then copy the working xorg.conf.800600 to xorg.conf.

After you've done that, type ```
sudo reboot
``` and when the grub menu comes up again, pick the regular boot. That will take you back to your original 800x600 desktop.

Regards,

Didius

---

### Post by Didius Falco on 2009-05-12
I tried to stay up until you got back into the desktop, but it is pushing 10 am here, and after an all-nighter like that, I'm getting pretty fuzzy.

I hope to see you around  the forum this evening (my time).

Regards,

Didius

---

### Post by VgnStirfry on 2009-05-13
> **Didius Falco said:**
> Okay - that is what you want to see. Don't hit "e" - that interrupts the boot process and takes you to grub. Let the text keep on rolling by and it'll take you to a menu box where you can choose the Command Line option. 

Unfortunately, that isn't what happens.  I power up, hit ESC at the point that allows me to choose recovery mode, then I choose the uppermost version of recovery mode.  The text scrolls and scrolls, and then finally stops.  No menu box ever appears.  The person who was troubleshooting via AIM (a friend of the friend who has lent me their computer) thinks that the xorg.conf file might have been written to a bad sector of the drive.  I am in over my head, so I was going to burn a Live CD and then see if I can fsck the disk and replace the xorg.conf file with the 800600 backup.  I'm not sure how to do all of this or if it is the right thing to do (the friend and the friend's friend are not available at the moment, but I have a deadline so I'm trying to work through this on my own).  

I think this has gotten complicated so if you can't assist that is fine (though I wouldn't turn it down if you offered!)  :)

---

### Post by matey3 on 2009-05-13
My problem was solved when I picked the right model of my Monitor (Not the video card)!
Now I get up to 1600x1200 but I prefer 1280x 1024.

Have you tried that?

---

### Post by Didius Falco on 2009-05-13
Try this:

Boot the PC up. When the Grub menu appears, use the down arrow key to scroll down to the Recovery Mode line - it should be the second menu choice. When it is highlighted, press enter and just wait. Do not hit any other keys - when you hit the Esc key, you are, in essence, telling Grub - stop everything, I'll take over from here, and Grub is doing just that. 

It is normal to see a bunch of text scrolling past. It will do that for a bit (how long depends on how fast your PC is), and then will show a menu that offers various choices. Again, use the up/down arrow keys to get to the "command Line" choice. Press Enter again and wait. You'll see more text scrolling past and then it will take you to a black screen with a command line prompt at the bottom.

That is where you type in the commands. First type in ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.wip 
```That makes a copy of the currently no-working one to xorg.conf.wip (for "work in progress"). Next type in ```
sudo cp /etc/X11/xorg.conf.800600 /etc/X11/xorg.conf
```That one copies the backup you made of your original xorg.conf file back.

Finally, type ```
sudo reboot
```When it gets back to the Grub menu, boot into the normal choice, and you will be back in with a GUI desktop interface, albeit a 800x600 GUI.

Regards,

Didius

---

### Post by VgnStirfry on 2009-05-13
> **Didius Falco said:**
> Try this:

Boot the PC up. When the Grub menu appears, use the down arrow key to scroll down to the Recovery Mode line - it should be the second menu choice. When it is highlighted, press enter and just wait. Do not hit any other keys - when you hit the Esc key, you are, in essence, telling Grub - stop everything, I'll take over from here, and Grub is doing just that.

I don't think I explained it correctly.  When I boot the PC up and do not touch anything, I first see the BIOS information, then options (F1 for BIOS menu, F10 for system recovery).  Then I see an option to hit ESC to enter the Grub menu.  

If I ignore the option to hit ESC, then the Ubuntu logo appears, with the animated bar scrolling back and forth.  Eventually the Ubuntu logo disappears, and then scrolling text appears on the screen, with error messages within.  Finally, it stops, and does not respond.

If I boot the PC up and hit ESC to enter the Grub menu, I see nine choices, including eight labeled 9.04 (it goes: 9.04, 9.04 recovery mode, and repeats four times for a total of eight choices), the ninth is a memory test.

Regardless of which recovery mode I choose, I still see that same scrolling text laden with errors, which eventually stops and does not respond.  

I think something is seriously wrong with my computer, because when I booted from the Live CD and went to the menu, if I chose "check the CD for errors", I got that same scrolling text, and if I chose "use ubuntu without any changes to your computer" or however it's stated, I got that scrolling text again.  

I really am at a loss as to what to do.  I'm hoping my friend and friend's friend can help.  Any thoughts?

---

### Post by unutbu on 2009-05-13
Just before you started getting this new behavior, did you change anything in the BIOS? If you are getting the same problem when booting from the LiveCD, the problem must have to do with either a change in hardware (including cables and connections) or a change in the BIOS.

If you have a way to take a digital picture of the error messages, it might be helpful if we could take a look at that too.

---

### Post by Didius Falco on 2009-05-13
> **VgnStirfry said:**
> I don't think I explained it correctly.  When I boot the PC up and do not touch anything, I first see the BIOS information, then options (F1 for BIOS menu, F10 for system recovery).  Then I see an option to hit ESC to enter the Grub menu.  

If I ignore the option to hit ESC, then the Ubuntu logo appears, with the animated bar scrolling back and forth.  Eventually the Ubuntu logo disappears, and then scrolling text appears on the screen, with error messages within.  Finally, it stops, and does not respond.

If I boot the PC up and hit ESC to enter the Grub menu, I see nine choices, including eight labeled 9.04 (it goes: 9.04, 9.04 recovery mode, and repeats four times for a total of eight choices), the ninth is a memory test.

Regardless of which recovery mode I choose, I still see that same scrolling text laden with errors, which eventually stops and does not respond.  

I think something is seriously wrong with my computer, because when I booted from the Live CD and went to the menu, if I chose "check the CD for errors", I got that same scrolling text, and if I chose "use ubuntu without any changes to your computer" or however it's stated, I got that scrolling text again.  

I really am at a loss as to what to do.  I'm hoping my friend and friend's friend can help.  Any thoughts?

My apologies - I obviously did not understand the problem.

It's hard to say with any certainty what the trouble could be, though. The fact that it won't boot the CD, which should work even without a hard drive in the PC at all, is troubling.

You aren't hearing a series of beeps when you boot up? Hardware troubleshooting is one of the harder things to do. 

Can you see what any of the errors are saying? that might give a clue...

Have a sniff at the fan on the power supply - smell anything funny?

What does the F10 option on your Bios do? What kind of Recovery is that referring to?

Didius

---

### Post by VgnStirfry on 2009-05-13
> **unutbu said:**
> Just before you started getting this new behavior, did you change anything in the BIOS? If you are getting the same problem when booting from the LiveCD, the problem must have to do with either a change in hardware (including cables and connections) or a change in the BIOS.

If you have a way to take a digital picture of the error messages, it might be helpful if we could take a look at that too.

I made one change to xorg.conf just before this happened.  See reply #31: at the poster's suggestion, I added the following code to my xorg.conf file:
 
[INDENT]Section "Device"
   Identifier "S3 Inc. VT8375 [ProSavage8 KM266/KL266]"
   Boardname "savage"
   Busid "PCI:1:0:0"
   Driver "savage"
   Screen 0
EndSection
[/INDENT]
I rebooted, and since then, it's been borked.  My friend's friend thinks that the xorg.conf file might have gotten written to a bad sector on my HD.  He thought fsck-ing it might help, but we haven't found a way to do that.  

I do have digital pictures and will upload them momentarily.  In the meantime, any ideas?

---

### Post by VgnStirfry on 2009-05-13
Didius: I will reply shortly, after I fuel up.  Thanks for sticking around to help! I'll be back in a few minutes.

---

### Post by CatKiller on 2009-05-13
Obviously you've got other problems to sort out first - hardware troubleshooting isn't fun - but you might want to try putting ```
HorizSync     30-96
VertRefresh     48-120
``` in the monitor section of your xorg.conf. I got the numbers from the PDF that was posted earlier.

It doesn't seem likely that you writing to a text file has caused your current problem. It's probably just a coincidence. Sudden failure like that might be caused by overheating from a failed fan, or it might be a vented capacitor on the motherboard. Or a handful of other things. As I said, not fun. Good luck.

---

### Post by VgnStirfry on 2009-05-13
Here is a link to a Google Document containing three images of the boot process.  
[http://docs.google.com/Doc?id=ddzp9xg2_0fp29tw47](http://docs.google.com/Doc?id=ddzp9xg2_0fp29tw47)

I have taken more photos, but am having trouble with the card reader.  I will post more as soon as I am able.  Any help to understand what is going on would be appreciated!

---

### Post by CatKiller on 2009-05-13
> **VgnStirfry said:**
> Here is a link to a Google Document containing three images of the boot process.

It does look like a hard drive problem. Sometimes hard drives do just die - they are usually the first component to fail. It's happened to me before. Or it could be the drive controller. That's happened to me before, too.

Do you get any noises from the hard drive? Clicking, for example.

---

### Post by VgnStirfry on 2009-05-13
> **CatKiller said:**
> It does look like a hard drive problem. Sometimes hard drives do just die - they are usually the first component to fail. It's happened to me before. Or it could be the drive controller. That's happened to me before, too.

Do you get any noises from the hard drive? Clicking, for example.

The drive is less than a year old and is not (nor had it been, prior to this issue) making any weird noises.  I was not experiencing anything that might be attributed to drive errors, prior to this.  Things were OK, I changed the xorg.conf file, and the next boot was as pictured above.  I can't rule out a hard drive failure of some sort, of course, but it seems suspiciously coincidental, considering that there was no warning.  I don't know what to do now.  Any ideas?

---

### Post by VgnStirfry on 2009-05-13
> **Didius Falco said:**
> My apologies - I obviously did not understand the problem.

No apology necessary.

> It's hard to say with any certainty what the trouble could be, though. The fact that it won't boot the CD, which should work even without a hard drive in the PC at all, is troubling.Just to be clear (for any newcomers): the initial menu for the Live CD does appear (with choices for "load live cd environment without making changes to your computer", "check the cd for errors" "do a memory test", etc), but the environment won't load and neither will the cd error-check.

Yes, it is troubling!  :(

> You aren't hearing a series of beeps when you boot up?Nope, no beeps at any point.  

> Can you see what any of the errors are saying? that might give a clue...See the [Google Document]("http://docs.google.com/Doc?id=ddzp9xg2_0fp29tw47") I uploaded.  (More images will come, if I can manage to get the card reader working).

> Have a sniff at the fan on the power supply - smell anything funny?There are no horrible smells.  The fan on the power supply blows air that has a very faint smell of "metal" for lack of a better word, but nothing alarming or unusual.

> What does the F10 option on your Bios do? What kind of Recovery is that referring to?Apparently, it does nothing.  :(

I am still hoping to fix this problem!  My friend believes that it is not a hard drive error, but a media error, based on the timing of the error, and the text of the error itself.  My friend's friend thinks it might be that the xorg.conf file got written to a bad sector of the drive, but my friend and I are not sure of that because we fsck-ed the disk just before the upgrade to 9.04 (which we did on the same day).

Any help would be appreciated!

---

### Post by CatKiller on 2009-05-13
> **VgnStirfry said:**
> The drive is less than a year old and is not (nor had it been, prior to this issue) making any weird noises.  I was not experiencing anything that might be attributed to drive errors, prior to this.  Things were OK, I changed the xorg.conf file, and the next boot was as pictured above.  I can't rule out a hard drive failure of some sort, of course, but it seems suspiciously coincidental, considering that there was no warning.  I don't know what to do now.  Any ideas?

I've seen drives fail after that short a period of time. It does happen. Some are DOA, but three years is the most that you'd expect a hard drive to last. Quite a lot will fail before that.

Check your connections. Check the motherboard for capacitors that are bulging or leaking. Check that all your fans are going round. The hard drive manufacturer will have a utility on their website that you can download and boot from that will check the hard drive for problems. Do that. Run a memtest, just on the off-chance. Check the voltages from your PSU.

There are quite a few stages that the data goes through from the hard drive to actually being run, so something else could be happening to it, making the other tests worthwhile to pinpoint the problem. Sudden hard drive failure seems like the most likely to me at this point, though.

---

### Post by Didius Falco on 2009-05-13
I'm doing some googling on the error messages you are getting.

It's looking like its a kernel error. This page has the same errors you are getting:

[http://ata.wiki.kernel.org/index.php/Libata_error_messages](http://ata.wiki.kernel.org/index.php/Libata_error_messages)

I also found this:

[http://www.gossamer-threads.com/lists/linux/kernel/932495](http://www.gossamer-threads.com/lists/linux/kernel/932495)

In post #3 of the above, it says:

> [FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]In particular, timeouts may be solved by acpi=off or 'noapic' or 
pci=nomsi or pci=biosirq. [/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]So you could try booting, hitting e and adding those options (one per boot) to the kernel line.

For a more permanent fix, I found this thread here in the forums:

[http://wiki.ubuntuforums.org/showpost.php?p=6520039&postcount=1](http://wiki.ubuntuforums.org/showpost.php?p=6520039&postcount=1)  

where hobong says:

> I Have just replace the Hard Drive but the messages are still spaming my system. Any one could please help me ? I also attach the log from dmesg command output.

Thank You

U'm using Ubuntu 8.10 II 
Proc 3.1 Ghz
Hard Drive 320 GB 
Mem 2 GB

It's Kernel bug on ata acpi 
Put "options libata noacpi=1" on /etc/modprobe.d/options 
solved the problemHe also posts a dmesg log with similar errors to yours.

(Didius raises right hand)
>  I do solemnly swear that I have never advised hobong to change a single setting in a single file, up to and particularly including his xorg.conf file. You can try adding those settings one per boot to the end of the kernel line for the Recovery Mode and if one works you can then copy the xorg.conf.800600 file over the xorg.conf file, resetting that.

Then you'd need to add the same option again to boot into the regular boot. Once that got you into the gui, you could add the setting that worked permanently to your kernel lines in menu.lst, or try the approach that worked for hobong. Hobongs' approach might be better, as you wouldn't have to remember to add it every time the kernel was updated, though it is possible that the updated kernel wouldn't cause that problem.

After you get your PC working properly again, and have rested up, you might consider filing a bug report and maybe save someone down the line the same problem.

I *really * hope this helps!!

Regards,

Didius

---

### Post by Didius Falco on 2009-05-13
Still digging, and I think I've found an easier way to approach this. It suddenly struck me to look into how you could use that kernel setting with the Live CD.

Have a look at the F6 option on this page:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[]("http://https//help.ubuntu.com/community/BootOptions")
If that worked, it would greatly simplify the recovery process. You could take care of the kernel option without all the tedious grub menu fiddling around, and you could replace the xorg.conf file and set the kernel option that worked on all the kernel lines in your menu.lst in fell swoop.

Regards,

Didius

P.S. It was the CD giving the same errors that made me start looking for kernel errors, as the PC shouldn't give a hoot about the status of the hard drive when booting from a CD - you should be able to boot a Live Cd even with no hard drive in the PC...

---

### Post by CatKiller on 2009-05-13
> **Didius Falco said:**
> P.S. It was the CD giving the same errors that made me start looking for kernel errors, as the PC shouldn't give a hoot about the status of the hard drive when booting from a CD - you should be able to boot a Live Cd even with no hard drive in the PC...

I'm not saying you're wrong, but if there's a hard drive in there that has a swap partition on it, the live cd will use that for swap to help performance. Which will then throw up the error if the hard drive's knackered. There's probably an option to turn that behaviour off, but I don't know what it is.

I hope it is a kernel error, although I don't know that it would be; the changes to xorg.conf won't be read until the very end of the boot process, and not at all in recovery mode. If he'd been adding kernel modules, then maybe, but AFAIK (I came into this thread late) he hasn't been.

---

### Post by Didius Falco on 2009-05-13
> **CatKiller said:**
> I'm not saying you're wrong, but if there's a hard drive in there that has a swap partition on it, the live cd will use that for swap to help performance. Which will then throw up the error if the hard drive's knackered. There's probably an option to turn that behaviour off, but I don't know what it is.

I hope it is a kernel error, although I don't know that it would be; the changes to xorg.conf won't be read until the very end of the boot process, and not at all in recovery mode. If he'd been adding kernel modules, then maybe, but AFAIK (I came into this thread late) he hasn't been.

If it keeps throwing up that error after trying the options I outlined, that will lean more towards it being a hard drive problem.

Still, I'd rather investigate the kernel error first - it's a possible fix that is much easier than the elimination process required to track down the hardware problem. 

I'm certainly no kernel expert, but the googling I was doing on the error messages kept leading me back in that direction - not only for Ubuntu but for other distros as well.

I agree about xorg.conf, and I'm at  a loss to think of any way that editing that file could do more than scramble the display temporarily.

It's hard enough to figure out possible hardware errors when it's right in front of me - trying to do it from Australia to Boston is downright maddening, especially when you take the time differential into account. I'm getting tired... <G>

---

### Post by VgnStirfry on 2009-05-14
Hey, Didius and CatKiller. ):P 

Just an update: I will be busy for at least another day, but I am hoping to get some work done on this over the weekend.  I hope I will be able to catch at least one of you then.  Thank you so much for your support thus far.  Until then.

---

### Post by Didius Falco on 2009-05-14
Thanks for checking in. "See" you in a day or so.

Regards,

Didius

---

### Post by VgnStirfry on 2009-05-17
Argh!  Just wrote a full reply, it got eaten.  Ah, well.

So!  Hello!  Here is the update.  I tried the non-grub-menu-fiddling method outlined in #57 (I opted not to attempt the suggestions in #56).  I tried every possible combination of the first three, then the fourth, alone, then all four.  None of these worked.  I then opted to install a new HD and new video card and install 9.04 on it.  I now am using Nvidia driver v 180.44 and have full Desktop Effects, as well as the highest resolution possible on my monitor (1600x1200).  That's the good news.

The bad news is that when I put my old HD in the slave position, I get the same errors as before.  I searched and found this thread*, where people are experiencing similar problems, but if I am not mistaken it seems like at least one person found their way out of this.  Is there any hope of retrieving my data?  Can you help?

* [http://ubuntuforums.org/showthread.php?t=937872](http://ubuntuforums.org/showthread.php?t=937872)

---

### Post by CatKiller on 2009-05-17
> **VgnStirfry said:**
>  Is there any hope of retrieving my data?

The hard drive manufacturer's diagnostic tool may provide a method to re-map the data from the damaged sections of the hard drive long enough for you to boot successfully and back up your data. It may even be able to fix it permanently, depending on what the problem was. I'd recommend that.

If you could find an option to stop the live cd from using your swap partition, you might be able to do a fsck on the drive. That might work, too.

---

### Post by VgnStirfry on 2009-05-17
Thank you; I will confer with my friend and let you know what happens.

---

### Post by Didius Falco on 2009-05-17
+1 on CatKiller's thoughts on the HD manufacturer utils.

Depending on your success with the HD utils, you could also download Knoppix - it has a noswap option at boot, and you might be able to rescue your files from there.

Here is a list of mirrors you can download it from:

[http://www.knopper.net/knoppix-mirrors/index-en.html](http://www.knopper.net/knoppix-mirrors/index-en.html)

Here are some documents that may help with using it:

[http://www.knopper.net/knoppix-info/index-en.html](http://www.knopper.net/knoppix-info/index-en.html)

This would be a good thing to have - Knoppix Cheat Codes for booting:

[http://www.kernel.org/pub/dist/knoppix/knoppix-cheatcodes.txt](http://www.kernel.org/pub/dist/knoppix/knoppix-cheatcodes.txt)

You could also run fsck on the drive from Knoppix, but if you can see and get your files without it, I'd recommend doing that first.

Regards,

Didius

---

### Post by VgnStirfry on 2009-05-17
The beleaguered drive is a Samsung, and neither HUTIL nor ESTOOL appear to offer any way to fix bad sectors other than to erase the HD (not an option, obviously).  As I cannot find information on how to use the Live CD to get around the errors and fsck the drive, I think I am going to go ahead and try Knoppix; thanks for the suggestion, Didius.

Thanks for staying on the case, Didius and CatKiller; I'll keep you posted.

---

### Post by LeonBlade on 2009-05-17
I had the same problem... once I installed my graphics drivers I was able to use the NVIDIA X Server Settings to set my resolution.

---

### Post by VgnStirfry on 2009-05-21
No updates on the HD yet, as I don't know how to use Knoppix to access my HD... however, I could use some help on these situations:

[http://ubuntuforums.org/showthread.php?t=1165937](http://ubuntuforums.org/showthread.php?t=1165937) - Monitor *was* working properly, now is not.

And, less important, but still annoying:
[http://ubuntuforums.org/showthread.php?t=1165931](http://ubuntuforums.org/showthread.php?t=1165931) - Forums themselves are not working properly.

Thanks to anyone who is still reading.

---

### Post by Rasiq on 2009-09-24
To access your HD use Parted Magic > [http://partedmagic.com/](http://partedmagic.com/) - it's linux livecd distro to be used on these "bad luck" situations. Download, burn a ISO and you can mount and change everything to restore your system. 

Good Luck!

Regards

Rasiq

---

### Post by cormocodran on 2009-11-06
I'm new to Ubuntu, using 9.04 and have the same problem: resolution can't be higher than 800x600. I followed the instruction in this thread until  post #30, and I doubt if I should follow the suggestion in #31. I figured I'd better be cautious.

this is the information I got from the following command

lspci | grep VGA
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0 

Any help will be highly  appreciated!

---

