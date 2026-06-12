---
title: "Wine 101 - getting apps &quot;into&quot; Wine?"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by deadmanschest on 2009-02-21
Hi all - a week of U8.10 and looking to add some desired windows apps, or at least to understand how...

"Wine 101" as in beginner's class...

I have searched, run the WineHQ guide and wiki, but sometimes stupid questions aren't answered...

I have installed Wine1.01 via the Add/Remove app. Installed and works. I'm looking at the config. I believe that Wine has created some Virtual CDrive. It is a bit odd since I am dual booting Vistax64 and share multiple partitions with U8.10, so it is weird to have virtual (?) drives named the same as my Real Drives with real data and I don't want things messed up..

WineHQ tells me to start config by searching for the .exe file of my desired Windows app...hehe

I have yet to find an explanation of how to actually download/upload and install one...

Thats the Q? Can I just move my desired app (say an oceanic tidal current predictor) to a shared drive or a USB flash drive and 'install' the app to some "virtual C:/program files", that is actually in my U8.10 install, and then transparently run the app from the desktop?

Thanks

Cheers

dmc

---

### Post by carml on 2009-02-21
As far I know,Wine creates only virtual hard disk,to match your second question,IMHO you have always to install all applications by transfering under Ubuntu the .exe file,because not always the applications on your Windows  partition run smootly using Wine.
I hope these suggestions match exactly your questions, ;)

---

### Post by deadmanschest on 2009-02-21
> **carml said:**
> As far I know,Wine creates only virtual hard disk,to match your second question,IMHO you have always to install all applications by transfering under Ubuntu the .exe file,because not always the applications on your Windows  partition run smootly using Wine.
I hope these suggestions match exactly your questions, ;)

Hi carml - thanks for the response - let me clarify, I don't want to run anything from my real Windows OS altho I can see it. I actually want to hide it. I don't want to accidentally damage my VistaOS by some inadvertent botch up in U8.10....

So, if I just move a Windows executable setup file into my U8.10 install, what should I expect to happen when I hit Install? 

Thanks!

dmc

---

### Post by david_kt on 2009-02-21
> **deadmanschest said:**
> 
I believe that Wine has created some Virtual CDrive. It is a bit odd since I am dual booting Vistax64 and share multiple partitions with U8.10, so it is weird to have virtual (?) drives named the same as my Real Drives with real data and I don't want things messed up..

I have yet to find an explanation of how to actually download/upload and install one...

Thats the Q? Can I just move my desired app (say an oceanic tidal current predictor) to a shared drive or a USB flash drive and 'install' the app to some "virtual C:/program files", that is actually in my U8.10 install, and then transparently run the app from the desktop?

When you install wine, there is no c drive yet, no configuration at all. Wine will start the create c drive and configuration file  the first time you use it. It will create /home/username/.wine directory, and then create drive_c in it.

It will not mess up your vista or whatever partition in your drive, if you run it normally.

You will need to install your application again (unless it is a  portable application). You could just double click on any installation file (exe file) on any partition/usb.

DK

---

### Post by deadmanschest on 2009-02-21
> **david_kt said:**
> When you install wine, there is no c drive yet, no configuration at all. Wine will start the create c drive and configuration file  the first time you use it. It will create /home/username/.wine directory, and then create drive_c in it.

It will not mess up your vista or whatever partition in your drive, if you run it normally.

You will need to install your application again (unless it is a  portable application). You could just double click on any installation file (exe file) on any partition/usb.

DK

Hi DK - thanks for the response. Actually, as soon as I added Wine via Add/Remove, it showed up in my Applications menu, it 'opened a cascading folder' in the menu and gave me "Program files>Notepad"; "Browse CDrive"; "Configure Wine" and "Uninstall Wine", so it has auto created the virtual CDrive and installed NotePad as an example.

What I do not "get" is do I have to "Run Wine" when I try to install a downloaded/uploaded windows app or do I just run the windows installer and see what happens?

Thanks

dmc

PS - probably getting cross-posted here....hehe..

---

### Post by mcduck on 2009-02-21
You do both. You run the installer *with* wine.

Usually this means opening a terminal and running "wine *installer*.exe"

---

### Post by deadmanschest on 2009-02-21
Update - I just tried to run a Portable App from a shared drive that is FAT32 under my U8.10 install, and I got a window from 'Archive Manager' that said ERROR. That clearly doesn't work seamlessly.

I will move an installer and a portable app to the U8.10 desktop and try install, see what happens....

cheers

dmc

---

### Post by mcduck on 2009-02-21
Portable apps should work just fine form removable drives. You just need to make sure that you are running the app with Wine, and not trying to open it with anything else.

In this case .exe files are probably configured to be opened with the archive manager, so you need to right-click the .exe and select Open With-> Wine instead of simply trying to click the file. You have to remember that even with Wine installed the .exe files are not considered as programs in Ubuntu, they are just like any other files you have. They only work as programs when you open them with Wine.

---

### Post by david_kt on 2009-02-21
> **deadmanschest said:**
> Actually, as soon as I added Wine via Add/Remove, it showed up in my Applications menu, it 'opened a cascading folder' in the menu and gave me "Program files>Notepad"; "Browse CDrive"; "Configure Wine" and "Uninstall Wine", so it has auto created the virtual CDrive and installed NotePad as an example.

What I do not "get" is do I have to "Run Wine" when I try to install a downloaded/uploaded windows app or do I just run the windows installer and see what happens?


I would check again if now wine immediately create /home/username/.wine on installation, not the first run.
To run wine,
1. just double click on any exe file.
2. If it pull a different application such as archive manager, right click on the exe file and choose run with different application, and select wine.
3. If you could not find wine after right click on exe file, choose custom command and type wine.

DK

---

### Post by deadmanschest on 2009-02-21
> **mcduck said:**
> You do both. You run the installer *with* wine.

Usually this means opening a terminal and running "wine *installer*.exe"

Hey mcduck - thanks, starting to make a little more sense to me. 
It seemed odd that in the default Applications>Wine> cascading folders that there was no Run Wine....

So there's no GUI for doing so in the default install. If I open Terminal and run Wine to install, I assume that I do not have to do so subsequent when I run the app?  That is, that I a) run Wine via Terminal command each time I want to install a windows app and b) just run the app (fingers crossed) thereafter?

Query b) assumes that Wine will add that app to the cascade folder under the Applications Menu tab....

Thanks
Cheers

dmc

---

### Post by mcduck on 2009-02-21
Actually I think you should be able to right-click any .exe file and select open with->wine to run it without using a terminal. (as far as I remember, it's been years since I had Wine installed). Also, if you don't need to use any .exe archives, you could just configure .exe files to be opened with Wine by default. Just right-click some .exe file, select Properties->Open With->Wine.

And if I remember right, after you have installed the app with Wine it should be added into your menu. Even if not, you can do that yourself so you definitely don't need to always start the programs from a terminal. If you do it yourself, just set the command to launch the program as "wine /path/to/program.exe", not just "/path/to/program.exe".

---

### Post by deadmanschest on 2009-02-21
Hi all - starting to get crossed up with posts....hehe...

Give me a half hour to get a couple of apps, installer and portable, into U8.10, then run Terminal commands to get Wine going (should be a GUI in the Applications folder menu, seems to me) and see what happens.

Thanks for all the input, clears up little things that are missing from the WineGuide and the Wiki - always a problem when people who know what they are doing are writing for people who do not know what they are doing...hehe

Cheers

dmc

---

### Post by Cannaregio on 2009-02-21
Depending from the windows program, some programs NEED to be properly installed through wine in order to run. 
By all means, not all.
Some others can just be taken "as they have been installed" in windows, from an external usb hard drive for instance, and will run with wine immediately [COLOR="Blue"]without[/COLOR] proper installing.

In the first case you have to insert your CD/DVD (or to mount the iso on a virtual cd) and then execute the proper install command, say, 

[COLOR="#0000ff"]wine install.exe[/COLOR]

In the second case you just navigate to the windows folder as it is (working in windows) and try the proper run command, say

[COLOR="Blue"]wine run.exe[/COLOR]

Of course the real programs you'll try out will have different names.

The advantage of NON installing a windows program through wine and running it from its windows folder instead is obvious: spared space & simplicity, but, as said, it wont work with all applications/games.

Just to make some examples, auran trainz, hoyle casino 2006 (poker), panzer general 2 version 102 and silent hunter III work all perfectly with wine out of their respective windows folders WITHOUT installing.

---

### Post by deadmanschest on 2009-02-21
Ooops - computer with Win9x setup just tells me that my Data partition and Ghost image partitions 'do not exist' so may be more than 1/2 hour to find and send over desired Windows apps....stupid windows...

I know they exist, but have to go to Linux based recovery disk to find the ***** things..

Sorry. Be back in an hour.

Thanks.

---

### Post by deadmanschest on 2009-02-21
Hi all - other computer churns away partitioning & trying to restore data...

I loaded a portable app into U8.10;

As per mcduck instr. I simply right-clicked and had a context menu entry for "Open with Wine.." I also had "Open with Archive Manager..." as mentioned.

Now the interesting part. I clicked Open w. Wine and the app opened. Happens that its old and runs on win9x. There was an error. Sounded like a Windows error. I recalled that Wine was config'd to emulate (?) XP so went into Wine>Config and changed default (for now) to ME or 9X, can't recall, and then right clicked and ran the portable app from the desktop from the context menu for Wine and it ran fine....

So then I happened to reboot, as the app is an audio one, and I find that 
U8.10 is continually freezing up when using Audio controls (grrrr!) and after reboot, I try run the app from the desktop with a double-click and it defaults to open>Archive Manager.

Reconfigured to open by default with Wine and works fine...

Thanks to all. Now to run an actual windows installer and see what happens.

Side note - I find that Wine has added a ton of cr*p Windows style folders to the virtual CDrive. Right down to the (cringe) 'My Documents' and 'My frigging whatever'. It occurs to me that should I want to install anything more than portable apps that maybe all this cr*p is needed?

Sigh.....

Thanks to all...

dmc

---

### Post by deadmanschest on 2009-02-21
Hi all - hope that this (long) thread might help others new to Ubuntu.

Got the portable app running fine. Finding the virtual CDrive not so much as it is .wine and is hidden by default from Places menu.

It does appear under the Applications>Wine>CDrive menu.

I was surprised to find a whole (it seems) Windows installation on the virtual CDrive, but I think its just a fake to fool windows apps. Example - there is an Internet Explorer folder in Program Files, but its only a few kb.

The entire Windows folder is 19MB...hehe.

Some things did not work. The Applications>Wine>Programs>Accessories>NotePad works to launch the clone of NotePad, but it offers context menu options such as to 'send launcher to Desktop..Panel ' etc. They don't work.

I will try install and run an "installer-style" app and come back in a while....I have to go nurse a sick Win9X box...

Thanks

dmc

---

### Post by mcduck on 2009-02-21
Just like you guessed, all the extra directories inside the "fake" c-drive are there because Windows programs expect them to exist. But no worries, wine installs as little unnecessary stuff as possible, its not trying to be a complete Windows, only as much as needed for Windows programs to work.

I think the notepad exist in Wine just because sometimes program installers want to open text files (like license agreements) for you to read in Notepad and would fail to work if it wasn't available. I wouldn't even expect it to be fully functional copy as there's hardly any reason to use Notepad for any real tasks when every Linux distribution has better text editors included by default.

---

