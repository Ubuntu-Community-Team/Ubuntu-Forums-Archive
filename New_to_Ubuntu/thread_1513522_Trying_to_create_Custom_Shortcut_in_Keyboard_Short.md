---
title: "Trying to create Custom Shortcut in Keyboard Shortcuts"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by phubert28 on 2010-06-19
I'm running 64 bit Ubuntu 10.4

I am trying to make my Logitech Illuminated Keyboard do what I configured it to do under Windows.

I've never written a shell script in my life (tho I'd done programming (Assembly language) for pay on Mainframe systems years ago, and in a number of proprietary command languages as well, including REXX).

The following shows my attempt at a solution, along with the error generated:

I used System > Preferences > Keyboard Shortcuts

to add the custom shortcut "Underline", binding it to the F1 key.

The "Command" referenced is:

/usr/share/keycommands/SendCtrlU

which has the permissions 755 and which contains the following (cat at the bottom):

paul@Aragorn:/usr/share/keycommands$ ls -alF
total 20
drwxr-xr-x   2 paul paul  4096 2010-06-19 12:33 ./
drwxrwxrwx 382 root root 12288 2010-06-19 12:23 ../
**-rwxr-xr-x   1 paul paul   308 2010-06-19 12:33 SendCtrlU***

You see the error here:

[B]paul@Aragorn:/usr/share/keycommands$ /usr/share/keycommands/SendCtrlU
bash: /usr/share/keycommands/SendCtrlU: /usr/share/keycommands: bad interpreter: Permission denied[/B]

paul@Aragorn:/usr/share/keycommands$ cat SendCtrlU
#!/usr/share/keycommands F1
#
# Purpose: issue Ctrl-U when F1 is pressed
#
# Function: will be bound to F1 as "Underline" via System > Preferences > Keyboard Shortcuts
#
# Requires X some functions to be disabled
#
# 2010-06-19 12:32 - experimental
#
xsendkeycode 37 1;xsendkeycode 30 1;xsendkeycode 30 0;xsendkeycode 37 0

paul@Aragorn:/usr/share/keycommands$ 

The xsendkeycode commands, issued as you see them here, do not generate an error in an xterm.

Any thoughts???

I don't know about the error, but I get the impression that the xsenkeycode executes too quickly for a KEYPRESS Ctrl-U to actually be executed.

Sometimes the combination I list POSTS a 'u' output to the command line, but often it seems NOT to.

I don't see that wait or pause are designed to help this situation.

Note: if I specifically reference the file

---

### Post by phubert28 on 2010-06-19
Looks like I'm finding my answer - I need to find the directory for the bash interpreter!!!

A misunderstanding

I changed the first line to something in the Bash Cookbook

#!/usr/bin/env bash

and then got the error "Not a directory"

Progress!

**

BUT, I tried !/usr/bin bash and got 'not an interpreter' ???

So, where the heck IS bash????

I can't seem to figure out just what the File Browser's search results are telling me (like full PATH of the things it finds)

Found /bin/bash but even with permissions as rwx r-xr-x for both the directory and the file, I get permission denied... ???

---

### Post by lkjoel on 2010-06-19
```
#!/bin/bash
```I think that is what you are looking for.

---

### Post by phubert28 on 2010-06-19
Thanks! Dunno why I saw #!/usr/bin/env bash

(page 83)

In the O'Reilly "Bash Cookbook" ... I think I need another book on bash that ISN'T a cookbook.
The incremental approach is a bit annoying.

---

### Post by phubert28 on 2010-06-19
Now I don't get an error, but I also don't get my UNDERLINE in Thunderbird COMPOSE ... oh well... more investigation, I guess...

---

### Post by lkjoel on 2010-06-19
The book is probably outdated.
Maybe thunderbird doesn't include the system shortcuts.
Check in the preferences menu.

---

### Post by phubert28 on 2010-06-19
I need to do a bit more reading - it SEEMS I somewhere sometime DISABLED whatever it was in X that treated F1 as a HELP key (or whatever its default was). Since X gets to the key before the keyboard shortcuts do.

Did you mean Thunderbird preferences?

It's clear the keypress is recognized - but not processed _as expected_.

I don't know of anything in Tbird config that would address the question, however.

---

### Post by lkjoel on 2010-06-19
You probably replaced F1.
You could maybe try to do CTRL+SHIFT+U?

---

### Post by phubert28 on 2010-06-19
You mean ISSUE the xsendkeycode for Ctrl Shift U???

I INTEND to replace F1 with Ctrl-U.

Under Windows, with Logitech's SetPoint software, I had my Illuminated Keyboard configured so that F1-F7 were Ctrl-U, Ctrl-I, Ctrl-B, Ctrl-C, Ctrl-V, Ctrl-X and Shift-Delete ... I want to do the same (and more) under Linux.

SetPoint, of course, doesn't RUN under Linux! Tho I lobbied Logitech to PROVIDE it.
The other advantage to their software is that they provide FAR better POINTER acceleration than the host OS (or X windows, in the case of Linux).

Not used to such a slow mouse! :-)

However, any Linux is better than any Windows...

---

### Post by lkjoel on 2010-06-19
Oh I see.
Some apps just don't care about the linux standard.
So you might want to just configure the apps who do not care about the linux standard.

---

### Post by phubert28 on 2010-06-19
Well, lkjoel, you answered the question I needed answered here... from what I've read, the keybinding issue is a little more complex and, as I indicated, has something also to do with how X handles the keys.

It will just take some more experimentation and reading, I think, but at least my command file is recognized and processed.

It could be that xsendkeycode ISN'T what I need (tho it LOOKS like the best thing so far)... I'll just keep playing with it. Problem is, I got away from it and promptly forgot much of what I'd read! And here I've been TRYING to document everything I do as I go along!!!

Anyway, thanks again. On to the next step. This has to work in every application where Ctrl-U is accepted for underline... it isn't an application issue, however.

How DO I set this as "Solved"??

---

### Post by lkjoel on 2010-06-19
I think it is in Thread tools. (just above your last post)
Also you can edit your first post, and change the prefix to SOLVED.
I'm glad you were able to fix it.


You might just want to get [LinuxEssentials]("http://ubuntuforums.org/showthread.php?t=1513068").
It will help your system. If you downloaded it, just run it at every login.
There might be a few bugs, so just be sure to check [URL="http://code.google.com/p/linuxessentials/issues/list"]http://code.google.com/p/linuxessentials/issues/list
[/URL]

---

### Post by phubert28 on 2010-06-19
In playing with the command string, I commented-out the 'release key' commands and managed to screw up X... forgot what the combination was to restart X so rebooted (not much difference between the two anyway).

Frustrating.

I am wondering if this CAN work. Thought I was on the right path.

---

### Post by lkjoel on 2010-06-19
Where's the keyboard shortcut file located?
And I think ANYTHING is possible to do with linux (even if that means crashing it 500 times), but it just takes time and patience.

That also reminds me of what I said earlier about LinuxEssentials.
LinuxEssentials is supposed to ELIMINATE the need of rebooting the system.

---

### Post by phubert28 on 2010-06-19
Keyboard shortcut file... good question.

Just did a google and came up with this answer:

there isn't one particular file. it's in the gnome registry, and is  stored somewhere under ~/.gconf/apps/metacity...

Q.: Does it mean that it will be better for me to use a third-party keyboard  shortcuts program?

A.: no not at all. it's just not really designed to be maniuplated outside  of gconf. I'm sure you can just copy the relevant %gconf.xml files  wherever you wish


issue:

gconf-editor

Select metacity

---

### Post by lkjoel on 2010-06-19
What were you using to change the keyboard shortcuts then?

---

### Post by phubert28 on 2010-06-19
Not really. I was trying to create CUSTOM shortcuts by re-mapping the function keys.
I don't use keyboard shortcuts, but I use underline, bold, italics and copy/paste/cut, shift-delete, select-all (Ctrl-A) and would like to make a single key do Ctrl-A, Ctrl-C.

---

### Post by lkjoel on 2010-06-19
What is the difference between custom and keyboard shortcuts then?

---

### Post by phubert28 on 2010-06-19
Well, I'm looking at a number of things.

gconf-editor (not installed by default) vs. the keyboard shortcuts under system > preferences.

For the latter, one can look at EXISTING shortcuts.
Custom would simply be whatever you want to do... specifying a command FILE - hence the script.

If I could figure out just what is happening in the metacity stuff, the gconf-editor might be the best solution ... :-)

---

### Post by lkjoel on 2010-06-19
Oh I get it. But does it work?

---

### Post by phubert28 on 2010-06-19
:-)

I have yet to find out!!!

This will take some time (especially with all the distractions - a friend calling to ask how to boot into a DOS prompt (he has Win98 ) - another friend a little ticked because I DIDN'T buy an OEM WinXP from him (he was too slow on the draw... already had it ordered online after getting a response from the supplier regarding return policies)

That's O.K. according to Nat Geo. either the sun or one of our enemies will destroy our entire electrical grid and all electronic equip. ... won't need Linux anymore THEN! :-)

---

### Post by phubert28 on 2010-06-19
Well, lkjoel, I was making this WAY too hard!

sudo gconf-editor
Select Apps
Select Metacity
Select keybinding_commands

In this case, I set command_1 to Ctrl-U

Select global_keybindings

Change run_command_1 to F1

F1 now issues Ctrl-U

---

### Post by phubert28 on 2010-06-19
So, I THOUGHT, anyway.

At first, the UNDERLINE worked. Then it didn't.

AND, it causes other problems with applications - messing with my FONTS, for example.

So, although I've found what seems as though it should be a solution, it doesn't appear to work.
There have to be other things involved.

---

### Post by lkjoel on 2010-06-20
I think its because some fonts don't support underline.

---

### Post by phubert28 on 2010-06-20
Nice thought, lkjoel, BUT, using Ctrl-U or the GUI controls manually WORKS, while using my remapped key seems to bounce me OUT of my selected font (where both the original font and the resulting font accept underlines, done 'manually').

So, it's clear I don't understand all the elements involved. As I said, there's more TO this.

Reminds me of green screen terminal controls in the early 80's where the target terminal type was being EMULATED by new controller hardware. The LAYERS of process from the user program, through the OS, through the somewhat foreign (UNIVAC had bought RCA's mainframe computing business, the two architectures were very different, UNIVAC began integrating its own hardware into the mix, while trying to maintain compatibility) new serial I/O communications controller box, eventually to the terminals. I was trying to CODE for screen control without having complete end to end documentation.

THIS reminds me of THAT.

There MUST be a way! ...in the meantime, I'll continue taking twice as many keystrokes to complete my tasks, it seems. But, then, that's what I had to do before I got the nifty new Logitech keyboard (under Windows) in the first place.

But AS TO fonts, Tbird is somewhat limited there. I can USE all my system fonts, but its support for fonts and font SIZES, in particular, doesn't come close to that of a full-blown word processor... not that I should expect it of a mail client!

Yeah, I happen to LOVE fonts ... look up Alexa, for example... I use it quite a lot. I know I'm a bit weird for an old diehard, dedicated, fanatical Assembly language programmer. But, then, THAT alone probably qualifies me as weird, huh?

---

### Post by lkjoel on 2010-06-20
Can you change the [FONT="Comic Sans MS"]_font_[/FONT] back to its original font?

---

### Post by lkjoel on 2010-06-21
Yeah, I love [FONT="Impact"]fonts[/FONT] too.
In Tbird, can you check the HTML source code?
If so, then you can change everything. (fonts to font sizes to color to everything)

---

### Post by phubert28 on 2010-06-21
For the first question, no, I wasn't able to change back. Haven't tried to view the HTML source ... but I see your point. For now, I'm going to set this issue aside. I figured out two paths to reach my goal, implemented both separately, and it seemed to work partially, but caused other issues. Enough for now. I'll let it drop and just use the two keystrokes or additional mouse movement to do my underline, italic, bold, etc. Given how many are beginning to abandon Windows and Mac for Linux, maybe Logitech will have gotten around to porting its software by the time I get BACK to the subject!

I've other fish to fry in the meantime... like the 10" Radial Arm saw arriving Thursday... or the upgrades for a friend's computer to see if I want to install Ubuntu alongside windows (his desktop has only a 70G HD and he has only 1G RAM)

---

### Post by lkjoel on 2010-06-21
Ok, sure.

I'll let you know if I find a link, or if I find how to get the Underlines working.

---

### Post by phubert28 on 2010-06-22
I'd appreciate that. Look forward to chatting again! I'm always around at Nick Petreley's varlinux.org.

---

### Post by lkjoel on 2010-07-06
Try here: [http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

---

### Post by phubert28 on 2010-07-06
Hi, lkjoel!

That looks VERY similar to what I tried... but re-mapping the function keys, which is what I needed for this Logitech Illuminated Keyboard to match its functions under Logitech SetPoint software on Windows, caused problems for me.

The difficulty seems to be that X intercepts and acts upon key presses BEFORE the Metacity assignments. So, it depends on where you are and whether X gets 'in front' of your configuation.

So, while I got the F1 key to issue a Ctrl-U, THAT caused other problems.

I have language software installed as well for keying in Korean or Japanese (not that I've been DOING this yet!!!!!) I have notes about what I did, but without them I don't recall, I'm afraid.

The setup for that apparently includes spell checking for English???

Anyway, in Tbird, there are times when I use a manual Ctrl-u when it highlights the little box for the language keying software and underlining IN Tbird gets all messed-up (Tbird is buggy in that area, anyway).

I've given up for now. I think the only REAL hope, slim as it is, is for Logitech to PORT their SetPoint software TO Linux!! And me on 64 bit to boot!!! :-(

---

### Post by lkjoel on 2010-07-06
> **phubert28 said:**
> Hi, lkjoel!

That looks VERY similar to what I tried... but re-mapping the function keys, which is what I needed for this Logitech Illuminated Keyboard to match its functions under Logitech SetPoint software on Windows, caused problems for me.

The difficulty seems to be that X intercepts and acts upon key presses BEFORE the Metacity assignments. So, it depends on where you are and whether X gets 'in front' of your configuation.

So, while I got the F1 key to issue a Ctrl-U, THAT caused other problems.

I have language software installed as well for keying in Korean or Japanese (not that I've been DOING this yet!!!!!) I have notes about what I did, but without them I don't recall, I'm afraid.

The setup for that apparently includes spell checking for English???

Anyway, in Tbird, there are times when I use a manual Ctrl-u when it highlights the little box for the language keying software and underlining IN Tbird gets all messed-up (Tbird is buggy in that area, anyway).

I've given up for now. I think the only REAL hope, slim as it is, is for Logitech to PORT their SetPoint software TO Linux!! And me on 64 bit to boot!!! :-(
Have you tried WINE?
WINE emulates windows.

---

### Post by phubert28 on 2010-07-06
I tried Codeweavers, lkjoel, but it has no support for the programs I want to run. I'm mystified by a project that I understood to have tried to emulate API's. One would think that once 'legacy' API's had been handled, that part would be STABLE, but one of our varlinux.org regulars tells us that his company's home-grown apps were BROKEN by LATER versions of Codeweavers.

I HAVE installed an OEM WinXP SP3 in a VM under Oracle's VirtualBox but there's a tweak I need to do to get it to recognize my Dymo Labelwriter 400 turbo printer. I haven't gotten back to it.

AND, I haven't tried to install Logitech's SetPoint software there, yet, either.

Have to do errands now & am about to start a project to paint the outside of the house (badly in need of it as the roof is badly in need of repair!!).

**

I get the impression Wine and Codeweavers' only serious goal is to enable MICROSOFT applications and only the CURRENT ones, at that.

Makes one wonder if MS is paying $$ under the table.

---

### Post by lkjoel on 2010-07-06
> **phubert28 said:**
> I tried Codeweavers, lkjoel, but it has no support for the programs I want to run. I'm mystified by a project that I understood to have tried to emulate API's. One would think that once 'legacy' API's had been handled, that part would be STABLE, but one of our varlinux.org regulars tells us that his company's home-grown apps were BROKEN by LATER versions of Codeweavers.

I HAVE installed an OEM WinXP SP3 in a VM under Oracle's VirtualBox but there's a tweak I need to do to get it to recognize my Dymo Labelwriter 400 turbo printer. I haven't gotten back to it.

AND, I haven't tried to install Logitech's SetPoint software there, yet, either.

Have to do errands now & am about to start a project to paint the outside of the house (badly in need of it as the roof is badly in need of repair!!).

**

I get the impression Wine and Codeweavers' only serious goal is to enable MICROSOFT applications and only the CURRENT ones, at that.

Makes one wonder if MS is paying $$ under the table.
I don't think so, because MS does not want people to switch to linux.

---

### Post by phubert28 on 2010-07-06
OTOH do they want people using OTHER apps they've NOT paid-for under Linux?
Better they can use MS apps they've PAID for, don't you think?
It's still lock-in.

---

### Post by lkjoel on 2010-07-07
> **phubert28 said:**
> OTOH do they want people using OTHER apps they've NOT paid-for under Linux?
Better they can use MS apps they've PAID for, don't you think?
It's still lock-in.
Yes, but wouldn't MS pay WINE to close down?

---

### Post by phubert28 on 2010-07-07
Too obvious. Anyway, WINE is a FLOSS project. Codeweavers is COMMERCIAL (and, yes, most WINE developers work for Codeweavers).

PCs running Linux pose little threat to M$, but I'm just trying to figure out WHY WINE is such a useless project! Aside from Microsoft software there is so little it will run!

---

### Post by lkjoel on 2010-07-07
> **phubert28 said:**
> Too obvious. Anyway, WINE is a FLOSS project. Codeweavers is COMMERCIAL (and, yes, most WINE developers work for Codeweavers).

PCs running Linux pose little threat to M$, but I'm just trying to figure out WHY WINE is such a useless project! Aside from Microsoft software there is so little it will run!
Are you kidding? Microsoft software is 1/1000000000 of the software out there for windows!
WINE is NOT a useless project. Millions of Code Contributers help WINE out.
If MS tries to pay ALL of the Code Contributers AND the WINE team, Microsoft would be quite poor.

---

### Post by phubert28 on 2010-07-07
Alright. IF that is the case, why can't just ANY Windows app run under Wine... especially simple ones like Dymo's label design/printing/address book software?

Or OLD STANDARDS like WORDPERFECT suite???

Or why do subsequent versions of Codeweavers BREAK existing home-grown Windows applications.

From what I have seen of the VERIFIED list, the programs supported are negligible with the only notable ones being the LATEST VERSIONS of MICROSOFT softsare?????

Are you using WINE to run Windows programs?
If so, which ones???

---

### Post by lkjoel on 2010-07-07
> **phubert28 said:**
> Alright. IF that is the case, why can't just ANY Windows app run under Wine... especially simple ones like Dymo's label design/printing/address book software?

Or OLD STANDARDS like WORDPERFECT suite???

Or why do subsequent versions of Codeweavers BREAK existing home-grown Windows applications.

From what I have seen of the VERIFIED list, the programs supported are negligible with the only notable ones being the LATEST VERSIONS of MICROSOFT softsare?????

Are you using WINE to run Windows programs?
If so, which ones???
I use many apps, and sometimes some config is needed.
Try installing playonlinux.
```
sudo apt-get update
sudo apt-get install playonlinux
```

---

### Post by phubert28 on 2010-07-07
Does it run on 64 bit?
And what is it???
Does it have access to USB printers???? (my Dymo)

...for not being available you've sure been available! :-D

---

### Post by lkjoel on 2010-07-08
I'm pretty sure that it can run on everything (except on a windows machine)

---

### Post by phubert28 on 2010-07-08
I don't see anything in Wine configuration about printer configuration...

---

### Post by lkjoel on 2010-07-08
There might be a printer port.

---

### Post by phubert28 on 2010-07-08
Well the Dymo printer IS USB-attached. So, it's more a plug 'n play issue, isn't it??

---

### Post by lkjoel on 2010-07-08
> **phubert28 said:**
> Well the Dymo printer IS USB-attached. So, it's more a plug 'n play issue, isn't it??
Check in the AppDB for any software that uses printers that could work on WINE

---

### Post by phubert28 on 2010-07-08
Pardon my vast ignorance, lkjoel, but where do I find the AppDB??? Also, I see "Applications" "Add application" but not how I get WINE to SEE my exe... of course running most Windows apps means installing them with all their attendant files, not just having an executable to run... so does this mean an .msi or startup.bat, etc.???? Not QUITE sure what I'm doing with WINE at this point.

---

### Post by lkjoel on 2010-07-08
> **phubert28 said:**
> Pardon my vast ignorance, lkjoel, but where do I find the AppDB??? Also, I see "Applications" "Add application" but not how I get WINE to SEE my exe... of course running most Windows apps means installing them with all their attendant files, not just having an executable to run... so does this mean an .msi or startup.bat, etc.???? Not QUITE sure what I'm doing with WINE at this point.
Sorry! It was a website:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by phubert28 on 2010-07-09
:-D

Thanks!

---

### Post by phubert28 on 2010-07-09
However, from that HQ link:

**Allows Windows program to interface with:**

 
[LIST]
[*]Sound devices via ALSA, OSS, JACK, Core Audio, libaudio, etc.
[*]Multi-lingual keyboards and CJK input method support via XIM
[*]Modems, serial devices
[*]Networks (TCP/IP and IPX)
[*]ASPI Scanners
[*]Windows Tablets via XInput (eg. Wacom)
[/LIST]
No mention of printers.
Dymo software not in DB
Wordperfect Office listed as "garbage" and NO support for Wordperfect X4/X5 (latest versions)

Also:

Printing via [PostScript]("http://wiki.winehq.org/PostScript") driver or legacy native Win16 printer drivers 

I TRIED running the Dymo software under the latest Codeweavers - NO luck. Wouldn't even install.

Looks like only the Pro version of the Oracle VirtualBox with an OEM disk of XP holds any hope... and that requires some effort to get a usb printer recognized.

The next version down of VirtualBox doesn't even offer USB support.

---

