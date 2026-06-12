---
title: "Help! Ubuntu 10.04 boots to command line!"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2010-09-08
When my computer boots Ubuntu 10.04 Lucid Lynx, it goes straight to the command line. It then prompts me for me login. Once I log in, I enter this command:

```
 startx 
```

My computer then goes to a black screen and stays there.

Here is a video of the whole sequence:

[http://www.youtube.com/watch?v=OADFZ1mocCY](http://www.youtube.com/watch?v=OADFZ1mocCY)

Eventually, I would love for my computer to boot straight to the GUI. However, for now, I just want to get past the black screen. 

Please help. Thanks!

---

### Post by Peter09 on 2010-09-08
Sounds like you have an incorrect driver for your video card. Try holding the shift key during the boot phase. this should take you to the grub menu. From there select recovery mode (normally one down) and hit enter. You should boot into a menu, one option being to reconfigure your graphics. Try that and see where you get.

---

### Post by JohnHeikkila on 2010-09-08
Sony Vaio has a Nvidia and Intel graphics card, so called "Speed" and "Stamina" modes. At least some of those PCs.

---

### Post by anewguy on 2010-09-08
Try getting to the boot editor - like Peter09 said - > Try holding the shift key during the boot phase. this should take you to the grub menu
However, instead of choosing recovery mode, follow the screen and edit the normal boot line - you should try adding nomodeset to the boot line and then booting.  If this works, we can give you instructions for making it permanent.

Dave

---

### Post by Ranger_Joe on 2010-09-08
I'm sorry anewguy, I'm VERY new to this. How do I add something to the boot line? Can I do that from the command line? I hope so... because that's the only place I can go.

What would the EXACT command be? Should I just type this?:

```
 nomodeset 
```

---

### Post by JKyleOKC on 2010-09-08
When you have the boot menu on screen, press the "e" key to enter edit mode. The display will show several lines, one of which begins with "kernel" or "linux" (one was the older version and the other the newer; I don't remember which is which and cannot check while on line). Arrow down to that line, press the "end" key to go to the end of the line, and type ```
" nomodeset"
``` to add it as the last word on the line. Then press ctrl-x (both keys at the same time) to boot with the changed line.

This is a temporary fix to see if that will cure the problem. Let us know what happens; if it does fix it we can then walk you through making it permanent, and if it does not we can suggest other possible cures.

Good luck and welcome to Ubuntu!

---

### Post by Ranger_Joe on 2010-09-08
JKyle,
I did exactly what you said. I hit "e" from the GRUB and it took me into edit mode. I arrowed down to the linux line you spoke of. Then I hit end and typed this:

```
 " nomodeset" 
```

*notice the space before "nomodeset" to separate it from the rest of the line

I then hit ctrl + x

My computer then "booted" if you could call it that. It was like a half boot. It didn't power off or anything. It again went straight to the command line, only this time, it looks like safe mode. Font is bigger, the splash screen looks all pixelated etc. 

From this new safe-like command line, I typed in my login and the command:

```
 startx 
```

Again nothing happened. It just went straight to a black screen still. 

Basically this process yields the same results with larger font.

Am I doing something wrong? Any other suggestions?

---

### Post by JKyleOKC on 2010-09-08
No, you didn't do anything wrong. This simply means that the "nomodeset" option didn't fix your problem.

The next thing to try is the recovery mode. Get to the boot menu screen but this time arrow down to the recovery line, usually the second line on the screen, and hit Enter. This should get you a different menu that will list a number of things you can do. One of them should be to fix video; choose that one with the arrow keys, and then hit Enter.

It may, or may not, solve the problem. Either way let us know what happens. And don't get too frustrated by these "failures" because each of them narrows down the search for the real cure. What you are going through happens all too often these days; there are so many different combinations of video out there that it's impossible to test against all of them, and sometimes fixing a problem for one person's system can cause new problems in other systems. However a systematic troubleshooting process usually gets to the bottom of things fairly quickly. The good news is that once we find the cause and lead you to a permanent fix, that fix should last until some future upgrade introduces a new gremlin.

---

### Post by Ranger_Joe on 2010-09-09
Jkyle, let me just say right now, that you rock. Not because you've helped me figure this out (yet), but because you're willing to help. When diving into Linux, that's important, as there is no real "customer support." You're the man. 

Now... I tried what you suggested. I booted my computer in Ubuntu Recovery mode and did in fact find this menu, where I should be able to reconfigure my graphics. However, when I try to do so. Nothing happens. I select the reconfigure graphics box, click "ok" and then nothing happens. The screen stays exactly where it is.

I have created a photo album of the sequence of 4 screens and 4 different menus that appear. I always get stuck on the 4th screen.

Here is the link to the album:
[http://ubuntuhelp.shutterfly.com/pictures/8](http://ubuntuhelp.shutterfly.com/pictures/8)

---

### Post by anewguy on 2010-09-09
When the system boots, and you are at the command line, please do the following:

lspci <press enter>  If you don't know, we are asking Ubuntu to list "ls" all devices it knows about on the PCI "pci" bus.  The video adapter being used by your system will show in that output.

Post the output of that back here so we can see which video adapter you are using.  From there, we can look at guiding you through getting this set up so you can run X.

If you are more ambitious, you can check the X log after you try startx and it fails:

- again in the command line:

ls /var/log/X*.* <press enter>

You should see something similar to (I'm not in Ubuntu right now so I can't give the exact name) Xorg-0.log or some such thing.

Using the name identified above:

cat /var/log/xxxx | more <press enter> where xxxx is the file name determined above.  This will dump the file to the terminal screen and you can use "Enter" to scroll a line, or use the space bar to scroll a page down (if I'm remembering correctly).  You want what will be close to the end of the file - you should see an error, denoted by "***" that will give some text explaining why X didn't start.  If you do this, please also post that back here so we can see it.

Dave ;)

---

### Post by JKyleOKC on 2010-09-09
> **Ranger_Joe said:**
> Jkyle, let me just say right now, that you rock. Not because you've helped me figure this out (yet), but because you're willing to help. When diving into Linux, that's important, as there is no real "customer support." You're the man.As you can see it's not just me. The thing that makes Ubuntu so great is the way its users help each other, and especially the way the group helps newcomers. Some of the older Linux distributions built a reputation of being elitists and brushing off help requests by telling folk to just read the manuals -- which are great once you learn the jargon but are sometimes devoid of meaning for a newcomer. This group help feature is why I say "we" and "us" rather than "I" in this thread...

The hints from anewguy are very good. The Xorg log may well give us the clues as to what is going wrong. Look especially for lines that begin with (EE) because that's how the log flags errors. My own Xorg.0.log file has all the video information in its first 200 lines; from there on to the end it's dealing with configuring the keyboard and the mouse. Incidentally you may find several Xorg log files; the one you want will be the most recent one, and you can get the timestamps by ```
ls -l /var/log/X*
``` The "-l" gets a "long" listing.

When you tell us the result of the "lspci" command that will help a lot. There are three major manufacturers of video adapters, plus a host of smaller ones. The big three are Intel, ATI, and nVidia. Their products differ greatly internally, so each requires its own video driver software -- and it's quite likely that your system isn't loading the correct version for your hardware. That seems to be quite common with the newer Ubuntu versions; it took me several days to get my systems working after I installed Lucid, because the new boot code wasn't getting information about the monitors that it could recognize. There are ways to force the right info into place, but it took a while to determine exactly what I needed to force...

---

### Post by Ranger_Joe on 2010-09-09
Jkyle,
You're right. All you guys rock. If it weren't for the community... I'd be absolutely lost.

Anewguy,
I wasn't feeling ambitious... so I simply entered the command:
```
 lspci 
```

Here's the output I got (photo is a bit grainy but readable):
[http://ubuntuhelp.shutterfly.com/pictures/18](http://ubuntuhelp.shutterfly.com/pictures/18)

What, if anything, does this tell us?

---

### Post by anewguy on 2010-09-09
Aah - that explains the problems.  You are using the integrated graphics for Intel core processor - I've seen some things very recently (mid to late August) on the net about problems exactly like yours and trying to get it to work.  Some of these involve forcing the X video driver to vesa - not the best but if it would at least get you to a GUI that would be better than where you are now.

I'm going to do some more searching on the net and post back again later.

Dave ;)

---

### Post by JKyleOKC on 2010-09-09
Looks like Dave (anewguy) has things well in hand. The Intel video seems to have more problems than the others, with ATI running a close second. However my own troubles were with nVidia, so all three can pose problems.

In outline, the cure is probably going to be creating a file at /etc/X11/xorg.conf that will force the proper driver for your video hardware. This file used to exist automatically, created by the installation routines, but the trend for a couple of years has been to go away from it and consequently Lucid doesn't have it by default. What Dave will be looking for is the exact procedure you'll need to create the file and populate it with the correct information.

I'll be following along but will leave the details to Dave...

---

### Post by Ranger_Joe on 2010-09-09
Anewguy, Jkyle, love it. Thanks again for all the help. Let me know exactly what I need to do when you find out.

Anewguy (Dave), you said that this is "not the best." Why is that? Is it hard? Am I going to break my computer? What are the risks? Please let me know. Thanks!

---

### Post by JKyleOKC on 2010-09-09
No, it won't break the computer, but it won't have all the bells and whistles that some games need either. The "vesa" driver is a sort of generic one-size-fits-all driver that doesn't do anything with the parts of the hardware that differ so widely between Intel, ATI, and nVidia gear. It concentrates entirely on parts that are common to all three, so it can work when not much of anything else can. However this prevents most of the bells and whistles featured in the ads from working. So long as you're not doing video editing or high-powered games, you may not even notice the difference.

I used the vesa driver for a year or so on an ancient Gateway box that's no longer in service; it had a very old nVidia graphics card in it, and none of the current (at the time) nVidia drivers would work properly with it. They would display everything, but folded in half so that the top half of the screen was on the bottom half of the display and vice versa. Switching to the vesa driver made everything work right so long as I used that box.

---

### Post by Ranger_Joe on 2010-09-09
Jkyle,
Will the graphics card only lose the bells and whistles when running Ubuntu? Like, if I wanted to play games by booting to Windows 7, would that be cool? Would it have it's original functionality or no?

Not that I even play PC games... I'm a console guy. But still... just curious.

---

### Post by JKyleOKC on 2010-09-09
No, the drivers used by Linux won't have any effect at all on Windows operation. They don't modify the hardware, just send transient commands and data to it.

---

### Post by anewguy on 2010-09-10
First, I promise things will still work as they always have in Windows!  A driver, such as what we are trying to find for your video adapter, is a piece of software that basically tells the system how best to use the piece of hardware.

From what I've seen (believe me, this is new to me, so *ANY* help is appreciated!) it appears there is no driver yet (unless Intel has one for Ubuntu on their site) for your adapter, core processor integrated graphics controller (rev 02).  Based on that, and something I read on the net, I believe the way to get you going is by using what is called the VESA driver.  Basically, this is a stripped down driver so that it works with a lot of different controllers, but doesn't take advantage of the power of any of them.  For example, you may not be able to run desktop effects - Compiz (you may have seen reference to "the cube") - do to the driver not supporting everything your adapter can do.

Now, I haven't configured xorg.conf in a long time, as everything has been automatic for me in the last few releases with the changes to xorg.  I do know from searching on the net that the location for the file xorg.conf, if used, has been moved from /etc/X11 to just /etc.  This file defines your environment to the X system (what gives you windows).  I put together a basic one that did run on my system, but when I boot with it I get a warning that it is running in low graphics mode, and then an error box where I have to "OK" it using the current desktop configuration.  Not knowing enough about the xorg.conf file contents (never was any form of expert - just made changes like most did according to what we found on the net), *ANY* help by *ANYONE* would be greatly appreciated to hopefully improve the OP's environment.

EDIT:  As pointed out by mastablasta, for some reason I forgot you didn't have a GUI, so the instructions I provided below for creating the file don't apply to you.  You need to load the file from the command line.

SKIP:  To create that file, do the following:

:::::::::       - open terminal window (Applications/Accessories/Terminal)
:::::::::       - type:

:::::::::       sudo gedit /etc/xorg.conf <press enter>

:::::::::      - copy the following and paste it into that file (should initially be :::::::::        empty):


DO THIS INSTEAD:

sudo cat > /etc/xorg.conf <press enter>  This will take input from the keyboard and create the /etc/xorg.conf file. (For those interested ">" forces it to create where ">>" would append to the file).

Type in each of the following lines, pressing enter after each:
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "extmod"
    Load "freetype"
    Load "glx" # 3D layer
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	Option	    "DPMS"
	ModeLine "800x600" "1024x768"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "vesa"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
EndSection


SKIP THIS:  Then click "save".

::::::::            Exit the editor

DO THIS INSTEAD:

hold down the ctrl key and press the "z" key.  This terminates the input and closes the file.

Restart your computer. If the computer refuses to start correctly, restart again and select the recovery console.  From it, do the following:

sudo cp /etc/xorg.conf /etc/bad_xorg.conf <press enter>

sudo rm /etc/xorg.conf <press enter>

Then restart again and you should end up back to where you were before we tried this.

BTW - if anyone with more knowledge of this graphics adapter or the contents of xorg.conf PLEASE chime in!!

Dave ;)

EDIT:  Just a couple of quick notes.  It *may* be possible to specify the driver as "Intel", but I think it would require something additional from the package manager and probably changes to the xorg.conf, and I wouldn't know what those are.

I have also sent a private message to someone who is an ubuntu guru, even though we normally aren't supposed to do so.  They may be able to help sort things out here.

EDIT-EDIT: As pointed out by mastablasta, I initially gave you instructions here for creating the file using a GUI'd application (gedit).  Since you don't have a GUI yet, I modified the instructions here to copy the file from the keyboard to the file.  In addition, my later post following that by mastablasta contains other ideas.  Sorry for the confusion - I'm just used to using a GUI so it didn't even occur to me at the time!

---

### Post by mastablasta on 2010-09-10
> **anewguy said:**
> 
- open terminal window (Applications/Accessories/Terminal)

 
if i understand the user can't get to GUI so i think this part is skipped. and the rest he will need to use some CLI text editor and probably just type it all in.

---

### Post by anewguy on 2010-09-10
> **mastablasta said:**
> if i understand the user can't get to GUI so i think this part is skipped. and the rest he will need to use some CLI text editor and probably just type it all in.

Crap!!  You're exactly right - I wasn't thinking!!  The whole idea is to GET him to a GUI - I must have had a huge brain malfunction! ;)

OP - forget using gedit as it is GUI based.  Instead, do:

sudo nano /etc/xorg.conf

then type the lines in

Ctrl/O to save the file

Ctrl/X to exit nano


Here's another idea as well:

If you can, use Windows and copy/paste the file contents I provided into notepad, then save the file as xorg.conf (be sure the file type is set to all files so it doesn't by default append .txt to the file name).

Burn a CD containing the file.

Boot Ubuntu to the command line.

Oooppppss - originally had this in the things you type, when you don't type it at all, do it:

load the just burned CD


Type:

sudo mkdir test

sudo mount /dev/cdrom0 test

sudo cd test

sudo cp xorg.conf /etc/xorg.conf


Sorry about all that confusion.  I'm just so used to using the GUI I totally forgot you didn't have that when I was initially telling you how to create the file.

If you have ANY questions, please let us know.

mastablasta - thanks again for catching my idiotic mistake!

Dave ;)

---

### Post by QLee on 2010-09-10
[QUOTE=anewguy]...
sudo cp xorg.conf /etc/xorg.conf
...[/QUOTE]

anewguy, are you sure you don't want to proofread your set of commands?

---

### Post by JKyleOKC on 2010-09-10
For starters, the xorg.conf file is still located at /etc/X11/xorg.conf in the 10.04 release. And as Dave has amended his instructions, use nano instead of gedit as the text editor to create the file. The file itself that he came up with looks perfectly adequate to get you to a GUI without even having to type "startx" so it's definitely the next step.

If, when you reboot after creating the file, you get the dialog that talks about low-resolution graphics mode, tell it to continue booting. The type may be large and clunky, and the buttons on various screens may be off the display so that you can't get to them, but it will at least verify that your video hardware is working. You can press ctrl-alt-F1 to get back to the text mode so that you can reboot or shut down; you'll be asked to log in again. Ubuntu has six such "virtual terminals" (F1 thru F6 together with ctrl-alt) and all can run at the same time, even with six separate users, if the box has enough RAM. They come in quite handy when solving problems such as this one. 

This low-res mode is, in my experience anyway, due to the X window program not being able to determine exactly what resolutions your monitor can handle. In such a situation, it defaults to 640x480, which was the standard display some 25 to 30 years ago and which is safe with most all monitors -- but today's programs are designed for much higher resolution. Once we've got you to the point of having a GUI albeit a rather useless one, we can help you modify the xorg.conf file to tell X the right settings for your monitor, and you'll be up and running.

---

### Post by Ranger_Joe on 2010-09-10
Ok, I will try to delve into this tonight and let you know the result.

Just out of curiosity, does this information at all help?:

[http://www.intel.com/support/graphics/sb/CS-010512.htm](http://www.intel.com/support/graphics/sb/CS-010512.htm)

I guess what I'm asking is the webpage talks about obtaining the source code for the Intel graphics driver. How hard would it be for someone to re-write that and retrofit it to Lucid Lynx?

---

### Post by anewguy on 2010-09-10
> **QLee said:**
> anewguy, are you sure you don't want to proofread your set of commands?

Okay, I'm probably being really stupid, which isn't unusual for me ;), so I have to ask:

If:

- creating a folder
- mounting a cd to that folder
- changing default to that folder

then:

- what is wrong with copying the file from there (the CD) to /etc?

I know it's been mentioned that xorg.conf still goes in /etc/X11 in 10.04, but according to the docs it supposedly now goes in /etc alone.  That's where I put it when I tested yesterday, so I know it at least worked from there.

So, anyway, not trying to get serious or anything here, so could you please tell me what I wrote wrong so I can be sure not to do it again?

Thanks!

Dave ;)

EDIT:  If you meant that I had "mount the CD" inside of the instructions the OP was to type, you are correct - I just edited that.  Thanks!

---

### Post by JKyleOKC on 2010-09-10
Dave, you got my curiosity up so I went to "man xorg.conf" and found this:

```
The xorg.conf configuration file is searched for in  the  following  places
       when the server is started as a normal user:

           /etc/X11/<cmdline>
           /usr/etc/X11/<cmdline>
           /etc/X11/$XORGCONFIG
           /usr/etc/X11/$XORGCONFIG
           /etc/X11/xorg.conf-4
           /etc/X11/xorg.conf
           /etc/xorg.conf
           /usr/etc/X11/xorg.conf.<hostname>
           /usr/etc/X11/xorg.conf-4
           /usr/etc/X11/xorg.conf
           /usr/lib/X11/xorg.conf.<hostname>
           /usr/lib/X11/xorg.conf-4
           /usr/lib/X11/xorg.conf

       where  <cmdline> is a relative path (with no “..” components) specified
       with the -config command line option, $XORGCONFIG is the relative  path
       (with  no  “..” components) specified by that environment variable, and
       <hostname> is the machine's hostname as reported by gethostname(3).
```It looks like there's not really **any** single "standard" location for it, but a number of them. Thus, we're both right -- or both wrong, whichever you prefer:).

The important thing for Ranger_Joe is that once the xorg.conf file is located where the program can find it, it will over-ride the (failing) automatic detection, and let the X server do its work for him.

---

### Post by Ranger_Joe on 2010-09-10
Ok, what do you guys think of modding the source code?

---

### Post by JKyleOKC on 2010-09-10
I'm not sure which source code you're referring to, but if it's the Intel drivers mentioned in that link from Intel that you posted, it would be a pretty risky thing to try unless you have lots of experience dealing with hardware at the assembly-language level. Once you've got a workable xorg.conf file in place and are able to make full use of your system, we can then help you determine how to get the most out of your Intel video hardware without having to modify any sources and recompile.

Your posting of the results from "lspci" showed us that it's an Intel video package, but it didn't provide the model number. Not your fault; the Intel chip simply didn't report it to the PCI tables. However we really do need that number to follow up on the Intel site; you probably saw how many different models they list! You may be able to get it by doing ```
grep Intel /etc/var/xorg.0.log
``` and digging it out from the three or four rather cryptic lines that will probably result. When I do this for my nVidia card on this machine, I get this:
```
jk@mehitabel:~$ grep nVidia /var/log/Xorg.0.log
(--) PCI:*(0:0:13:0) 10de:03d0:103c:2a6c nVidia Corporation C61 [GeForce 6150SE nForce 430] rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
```which indicates that it's a GeForce 6150SE. Since I don't have an Intel video adapter in any of my systems I can't tell you how to spot it in your result but this may give you some ideas. Once we have the model number we can dig through the Intel site for more assistance...

---

### Post by anewguy on 2010-09-10
Hi Jim!

I didn't know either that xorg.conf could be in so many places!  I was just starting to understand the new X configure stuff, like making section files, etc., on their own, and never knew this.  Thanks for clearing that up!

For the OP:

Jim is right - you don't even want to think about modding a driver source file.  It does require knowledge of low-level functioning in the OS, a lower-level language like C or C++ and some assembler, and a very detailed knowledge of the adapter - what registers it uses for commands, what the commands are, where the data from commands go - the list is huge and very technically detail oriented.

Jim is also right in that we need to see more about your video adapter.  That's why I was hoping you could take a look at the X log file - it will tell us what it thinks it is and the problems it is having with it.  If you don't want to look at it on your own, try the following:

- open a terminal window (Applications/Accessories/Terminal)
- type:

sudo rm /var/log/Xorg.0.log <press enter>.  This will be sure we will start with a brand new log file the next time (I don't know - might be the default anyway).

startx <press enter>  When this fails, scan through the file using:

EDIT:  Changed the below to pipe to "less" to allow for scrolling forwards and backwards as per Jim - thanks Jim!

cat /var/log/Xorg.0.log | less <press enter>  Look there for the error line(s), what it thinks your video adapter is and the driver it tries to load (if it makes it that far).  Copy those lines and post them back here.  If you dual-boot with Windows, give us an idea of how your hard drive is partitioned (1 for Windows, 1 or 2 for Linux, etc.) as we may be able to give you instructions for mounting your Windows partition at the command line and just copy the log file there for posting back here.  I can't remember by default if the Windows partition is already mounted by boot nor do I have any idea what partition id it might be (like /dev/sda0 or something like that).

Hang in there - we'll get you to a GUI and then tweak everything from there.  It just takes some time, some typing, and a great amount of the fantastic patience you have show so far!

Thanks again Jim for helping out here!  Hopefully between the 2 of us we can get the OP to a GUI then let the tweaking begin!

Dave ;)

---

### Post by JKyleOKC on 2010-09-10
No need to remove the old log file. The current xorg routines rename the existing one by adding ".old" and start fresh each time.

I prefer to pipe output to "less" rather than to "more" since "less" allows me to scroll back toward the start if I want to refer back to something. Otherwise it works exactly the same way.

It's just barely possible that ```
lshw|less
``` might get the model number we need; it's worth a try, anyway.

---

### Post by anewguy on 2010-09-10
Tried posting a reply a couple of minutes ago, but it looks like it failed.  If for some reason there later are 2 replies here in a row about the same thing from me, then you know why.

Jim - great points!  I wasn't sure if X created the log file new each time or not, but it makes a lot of sense that it would.

Your suggestion for using "less" is spot on, and something I completely forgot about.  I modified the last post where I used "more" to "less" with an edit note following your suggestion here and it should make life a little easier for the OP.

If listing the hardware does show the model number - and I've got to believe this things is known by something like 985 or something and not just the weird title it shows - then that would be great!  OP - please try this suggestion from Jim!

If needed, I think we could also get a copy of the log file, pipe the output of the hardware list, etc., to disk and copy those files to the OP's Windows partition for posting back here.  we can do that at the command line quite simply as long as we know the id of the Windows partition (perhaps using parted from the command line and doing a list).

Thanks again!
Dave

BTW - the guru I mentioned is going to look at this and see if there is something they can add/call me an idiot ;) , etc..

---

### Post by anewguy on 2010-09-10
Just FYI for everyone - I opened a question on Intel's site for general questions trying to find out how this adapter is really id'd.  hopefully someone there can provide an answer as well.

Dave ;)

---

### Post by putu.sundika on 2010-09-10
or might be problem comes after installing something ? just like my experience on redhat, after write down some line on cronjob, my server start black screen after reboot, but, it still 100% working, i knew that working because i try remote via ssh. perhaps ?

---

### Post by anewguy on 2010-09-10
Good point - we can look at that if trying to get a GUI still fails.  I would still prefer to work until a GUI is available, but when all else fails we can indeed follow your suggestion!

Thanks!
Dave ;)

---

### Post by jtarin on 2010-09-11
Another trail to follow finding the graphics chip info might be cross-referencing it with the motherboard. This command will get your MB info.
```
sudo dmidecode | more
```

---

### Post by anewguy on 2010-09-11
I like that idea as well - OP, if you could, type what they mentioned at the command line and post back the result.  Obviously it is some sort of Intel chip, and as such there really should (if Intel is still following what they've done for decades) be a more useful "title" to the graphics adapter.

Thanks for the great suggestion!

Dave ;)

---

### Post by anewguy on 2010-09-11
Here's something you can do that will provide the answer for us:

While booted in Windows, get on the net and go to the following address:

[Intel Page To Identify Your Product]("http://www.intel.com/support/idyp.htm")

I would try the "Automatically detect your product" link first, since it sounds like it id's all of your Intel products and provides links about them as well.

When you have done that, copy everything and paste it in a reply here (or screen print and post a link to it).

This should help us greatly by identifying what you have.

Dave ;)

---

### Post by anewguy on 2010-09-13
Ranger_Joe - haven't seen anything here for a couple of days.  I hope it's just because it was the weekend - otherwise I fear we either scared you off or you gave up, neither of which I hope is true!

Dave ;)

---

### Post by anewguy on 2010-09-14
To anyone reading this to help troubleshoot:  did I do something wrong or stupid that may have scared the original poster away?  I need to know so I can change future responses if needed.  Just trying my best, but I'm hoping my best isn't what lost the OP.

Dave ;)

---

### Post by jtarin on 2010-09-14
I wouldn't worry about it. People solve their problems and move on without informing anyone. People give up on solving their problems and inform no one.Sometimes it takes days for people to respond.

---

### Post by excetara2 on 2010-09-20
Found this thread and ran nomodeset to fix my problem of the driver. It came when I installed the Catalyst Ati Driver. I wanted to try it because I was switching to three monitors so I was going to see if it worked because with compiz and the default configuration I can't get three monitors working.

I had tried the ATI in the past but suspend didn't work and since it is a laptop this is a must so have always used the generic. I think I will just continue using the generic and get rid of the ATI driver. What is the best way to do this? Just uninstall the driver and then cp over the xorg.conf with a back xorg file. Also, how do I boot directly to the command line? I couldn't remember the boot option to do that.

Cheers

---

### Post by Ranger_Joe on 2010-09-24
Hey everyone, I'm incredibly sorry for the delay in getting back to you. I'm a full time student with a BRAND NEW baby. I've had a bunch of stuff going on and just got bogged down. Didn't have time to mess around with Ubuntu, even though I still DESPERATELY want it to work. I went to Intel's website and used their automatic product detection utility. 

Here is the entire output:

Intel System Identification Utility Reference Number: 0016 4021 
Date Created: Friday, September 24, 2010 8:16:30 AM
BASIC

 SYSTEM INFORMATION
Computer Manufacturer	Sony Corporation
Computer Model	VAIO
Operating System (O/S)	Microsoft Windows 7 Home Premium Edition
Operating System Build (O/S)	(build 7600), 64-bit
Operating System (version)	6.1.7600
System RAM	3.7 GB
CD or DVD Device	MATSHITA BD-CMB UJ141AL
System Hard Drive Overview
System Total Storage size:	134.6 GB
Local Disk C:	134.6 GB
Used space:	40.3 GB
Free Space:	94.3 GB
 GRAPHICS INFORMATION
Graphics Product	Intel® HD Graphics
Graphics Driver Version	8.15.10.2008
3D Acceleration	Yes
Hardware Transform & Lighting Support	Yes
Video Memory	1.7 GB
Vertex Shader Support	4.0
Pixel Shader Support	4.0
Microsoft DirectX* Version	10.0
 MOTHERBOARD INFORMATION
Manufacturer	not detected
Model	VAIO
AA Number	not detected
BIOS Vendor	American Megatrends Inc.
BIOS Version	R0270Y8
BIOS Release Date	09/23/09
System Memory	3.7 GB
Sound Card	Intel(R) Display Audio
 PROCESSOR INFORMATION
Manufacturer	GenuineIntel
Model	Intel(R) Core(TM) i5 CPU M 450 @ 2.40GHz
Intel Processor analysis tools	Intel Processor analysis tools
CPU Speed	2.39 GHz
Link to Processor Specification	Link to Processor Specification
 WIRED NETWORKING INFORMATION
Wired Networking Product	not detected
Driver Version	not detected
Intel PROSet Version	not detected
 WIRELESS NETWORKING INFORMATION
Wireless Networking Product	Intel® Centrino® Advanced-N 6200
Driver Version	13.1.1.1
Intel PROSet/Wireless Version	13.1.1.0

Anewguy, you didn't scare me away dude. Everything is cool. I'll be better about checking this board because I REALLY want to figure this out. It's driving me nuts.

---

### Post by JKyleOKC on 2010-09-24
Good to see you back, and congratuations on the new baby! Your absence is understandable under the circumstances!

---

### Post by Ranger_Joe on 2010-09-25
Jkyle! What's up man? Good to be back. I feel like we're one step closer to solving this thing and I feel good about it. Hey... this is just a stab in the dark but do any of you guys play PS3? You guys seem cool so if so, I'd like to be your friend on Playstation Network. Knowing how savvy you guys are... you probably play Xbox and boot Linux on that.

---

### Post by JKyleOKC on 2010-09-25
Nope, I'm not a gamer (except for Solitaire). Never got into it at all. In the early days, graphics were just too clunky. That's no longer the case, of course. I do occasionally fire up Microsoft's Train Simulator (I was a model railroad buff some 30 years ago) but that's about my limit, and running the train tends to get a bit boring after 30 minutes or so...

I was disappointed that the Intel report didn't at least give some indication of a model number for your graphics adapter. Guess we'll just have to go with generic vesa as the starting point. I think anewguy has the best approach so I'll just lurk in the background and let him take the lead, but I'll still be here so long as the thread stays active.

---

### Post by Ranger_Joe on 2010-09-25
Sounds good JKyle.

Anewguy,
What exactly is it that I need to do now? Did you learn anything of use from the Intel output?

---

### Post by Ranger_Joe on 2010-09-28
One thing I'm concerned about is my graphics card not being able to handle 'the cube.' That's a really attractive feature of Ubuntu that I want to take advantage of.

At this point, do I have any options?

---

### Post by Ranger_Joe on 2010-10-01
Anything new on this? Anyone?

---

### Post by Peter09 on 2010-10-02
Hi,
I've been keeping an eye on this thread since my first post, could you just give us a refresh on your current position and problems and also the model number of the machine you have a problem with. 

One of the troubles with the forum is that a lot of people want to help and offer opinions and solutions and you can get to the stage where the machine ends up in an indeterminate state with several solutions half completed or conflicting -if you still have the problem it is time to take stock of what you have done and what state the machine is in.

---

### Post by anewguy on 2010-10-02
Sorry to be so late - I lost my internet for over a week due to my brother inlaw's DSL modem biting it and having to wait for a new one to come.

First off, congratulations on the baby, and man are you busy!

I reviewed your outputs and see it's the intel core i5 processor with HD graphics.  It's a little strange - a search of the net seems to indicate this works fine with 10.04, so I'm a little confused.  I did see one mention of an intel open source driver for this so I'll see if I can find anymore on that.

Dave ;)

---

### Post by anewguy on 2010-10-02
Ok, there is a Windows XP version driver for your video.  What I'm not sure about is exactly how to get it to you and install it without having a GUI.  So, reviewing the thread I noticed that I don't think we got all the way through something:  did you try creating the xorg.conf file and rebooting, and did this help in any way to at least get a GUI running?

Dave ;)

---

### Post by Ranger_Joe on 2010-10-04
Dave,
I didn't. I was hoping there was another way. I'll go back and read that post and try to do exactly as it says. I'll let you guys know as soon as I've tried.

---

### Post by Ranger_Joe on 2010-10-06
Dave, Here's what you told me:

> OP - forget using gedit as it is GUI based. Instead, do:

sudo nano /etc/xorg.conf

then type the lines in

Ctrl/O to save the file

Ctrl/X to exit nano


Exactly where do I do this? From the command line I get when attempting to start Ubuntu?

---

### Post by Crazedpsyc on 2010-10-06
Hello Ranger_Joe, I had the same problem for a while and I think I know how to fix it for you:
In the system specs you posted the following:
> Operating System Build (O/S)	(build 7600), 64-bit
meaning your computer is 64 bit. To get the graphics working you have to have the 64 bit version of Ubuntu as well. You can download this (if you have a download allowance limit greater than about 700 megabytes) or you might be able to find it in the magazine section of a big bookstore, although that is unlikely. Otherwise, I'm not sure how to get it

---

### Post by Ranger_Joe on 2010-10-06
Crazedpsyc, I can only hope that the solution is this easy. I downloaded the 64 bit version of Ubuntu and burned it to a disc. Then, I booted my computer with the disc in the tray and installed it. 

This partitioned a third section on my hard drive. Now, when I boot my computer, I see WAAAAAAAY too many options, as I have a dead 32 bit Ubuntu, this new 64 bit Ubuntu, as well as Windows 7 and Windows Vista.

Back to that in a second.

So I tried launching this new Ubuntu but it's doing the same thing. I suspect because it's getting confused and booting the 32 bit. 

Here's what I need to know right now. How can I COMPLETELY uninstall both of them and un-partition my hard drive, so I can start ALL over with the 64 bit Ubuntu? 

Basically, I want to restore my computer to exactly the way it was before I started all this so I can start over clean and fresh. 

If you know, please tell me. Thanks!

---

### Post by jtarin on 2010-10-06
Use Win 7 disk management to delete and format the unwanted partitions.

---

### Post by Ranger_Joe on 2010-10-06
Sorry Jtarin,
I'm basically a newbie at tinkering with computers period. How exactly would I do that?

Also, will that make Window 7 boot automatically? Like will all the options at start go away?

---

### Post by jtarin on 2010-10-06
> **Ranger_Joe said:**
> Sorry Jtarin,
I'm basically a newbie at tinkering with computers period. How exactly would I do that?

Also, will that make Window 7 boot automatically? Like will all the options at start go away?
No this action will not change the MBR of the disk from GRUB2 to Win7. You must use System Recovery. To access the System Recovery Environment in Windows 7, simply boot your PC,then from the Grub menu choose Windows and  just before the system loads the Windows operating system, hit the [F8] Function 8 key on your keyboard which will launch the Advanced Boot Options menu. There you will see a new option 'Repair Your Computer', select this option and hit 'Enter' on your keyboard. Startup Repair - Automatically finds and fixes boot errors in the Windows Vista Startup Process (including corrupted Boot Configuration Data files).

To open Disk Management, open the Start menu of Windows Vista or Windows 7. 
In the search box type diskmgmt.msc, typing the command then the file will appear in the box, just click the file to open the tool. 
Wait for the loading of the service. 
With thatyou have now opened the Disk Management of Windows 7, which provides for basic actions on partitions as: Creating new partitions (pieces), delete partitions (pieces), resizing and other features.

---

### Post by Ranger_Joe on 2010-10-07
Ok everyone, time out. Something pretty amazing just happened.

I pushed the power button on my computer and walked away to do some other things. When I got back, the Ubuntu GUI was loaded and everything was cool.

Now, I've been inside the GUI before as it loaded for me a few times in the very beginning, but I couldn't ever replicate it. So, to make sure it wasn't a freak occurrence, I powered down and did the same thing again.

It seems as though I have an issue when I select Ubuntu in the GRUB menu, instead of letting it automatically select itself at start. Make sense?

FYI: I believe my computer is running the 32 bit version right now. 

Number one: I'd like to get people's thoughts on this. I want to believe so bad that I have this figured out. Could it really be that simple??

Number two: If this is going to continue to work, how can I COMPLETELY un-install the 64 bit version? Jtarin mentioned two approaches but I'm not sure which one I should do. Both?

Thanks to everyone for continuing to try and troubleshoot this problem! I love Sony products, especially my Vaio. But... if I'm stuck running Windows 7, it totally sucks. Ha ha ha.

BTW: I'm in Ubuntu right now and it rocks.

---

### Post by Ranger_Joe on 2010-10-08
Ok everyone, I feel like an absolute idiot. I'll be changing my pic to one of Tim Tebow with "rookie" stamped across his forhead. It boots fine if I just let it. I'm so sorry for wasting everyone's time. Thanks  everybody.

---

### Post by JKyleOKC on 2010-10-10
I don't consider the time I've spent on this thread wasted; I learned a bit from it, and several other people seem to have gotten a bit of help from it also.

Good to know you're now up and running properly!

---

### Post by anewguy on 2010-10-10
The only person who loses via a thread like this is the person who doesn't have an open mind to learn, share and try to help.  Nothing in this thread was EVER a waste of anyones' time!

I'm just glad things are working for you, as some of this was becoming a bit of a mystery!

Best of luck!

Dave ;)

---

### Post by Ranger_Joe on 2010-10-11
You guys are awesome.

---

### Post by Scorcher21 on 2010-10-16
Ok hate to bring up an old thread and all but he seemed to have almost exactly the same problem Im having. Except I was able to get to my gui by removing nouveau and letting my nvidia take over. But I still go straight to command line from start up though and I have to use startx to get to gui but Im having problems there. I figured Id try what either anewaguy or JKyleOKC said  with the sudo  cat > / etc/xorg.cof but when I attempt that through command line it says permission denied. 

Just thought of this since i can get to gui Ill try through terminal, but didnt want to have to erase all this and rewrite it in ten mins when this fails also.... not having much luck these past few days optimism is at a low.

_**EDIT:**_   OK as I figured that didnt work. I was able to do it by using nano instead of cat > but same thing once I saved and rebboted it goes to command line. And I guess I should be precise here it doesnt go directly to command line.. the screen flashes a dark green then brings up the purple ubuntu screen for like a quarter to half second then goes to commandline. Any help would be greatly appreciated.

---

### Post by JKyleOKC on 2010-10-16
It sounds as if for some reason your system is not running the gdm (Gnome Display Manager) program, which is what handles the GUI login process and starts the GUI. It probably has nothing at all to do with xorg.conf, which doesn't come into play until the X server is started.

Just for future reference, the ">" redirection operator won't work with a "sudo"ed command, because it launches its process under the original non-super user ID. It always gives "permission denied" in these cases. The workaround is to pipe the result of the original sudoed command to another one: "sudo tee " followed by the filename you want to write. It's a bit of a pain, but it works and doesn't have to be done very often.

Now back to your gdm problem. The first step in troubleshooting it is to go through several of the boot-time logs, including dmesg and syslog, looking for any mention of "gdm" to try to determine whether it's even being called. You'll find these in /var/log and you won't have to use sudo to read them with any text editor. If you find something, post it in the forum -- but preferably in a brand new thread titled "No Automatic GUI" or something like that, which will get the attention of people who know more about this kind of problem than I do! Even if you don't find anything in the logs, starting such a thread is a good idea since the people who know what goes on behind the scenes at boot time are not likely to see this one...

EDIT: It's possible, too, that misconfiguration of the X server is causing it to fail, which was what was happening to the original poster, so you might want to try doing "sudo nano /etc/xorg.conf" and typing in the rudimentary configuration file suggested earlier in the thread, to overcome the permissions problem, and see whether that works!

---

### Post by Scorcher21 on 2010-10-16
I did start one shortly after I posted this I realized my error kinda straight away... Ill go get those los now but im not 100% sure what Im looking for.

---

### Post by JKyleOKC on 2010-10-16
Notice that I had an afterthought that you may not have seen...

---

### Post by anewguy on 2010-10-17
> **JKyleOKC said:**
> It sounds as if for some reason your system is not running the gdm (Gnome Display Manager) program, which is what handles the GUI login process and starts the GUI. It probably has nothing at all to do with xorg.conf, which doesn't come into play until the X server is started.

I agree 100%

> Just for future reference, the ">" redirection operator won't work with a "sudo"ed command, because it launches its process under the original non-super user ID. It always gives "permission denied" in these cases. The workaround is to pipe the result of the original sudoed command to another one: "sudo tee " followed by the filename you want to write. It's a bit of a pain, but it works and doesn't have to be done very often.

That's the one thing I don't like with ubuntu's restricted access to root - it provides better security (and stops some new people from hosing their systems) - but it also makes some other things more difficult.  I've even gone to the trouble to put alias's in some of the system files so that a command can be run by a non-root user but that needs root priviledges multiple times - like in the example you site.

Good hearing from you again!

Dave ;)

---

