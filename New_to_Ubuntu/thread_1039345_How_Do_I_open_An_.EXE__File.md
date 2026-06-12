---
title: "How Do I open An .EXE  File?"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by jozmoz on 2009-01-14
Hi,

I'm trying to open an .exe file to upgrade my bios, But when I click on the file it just opens up the 'open with' box. Does anyone know how to open executable files?

Thanks.

---

### Post by taurus on 2009-01-14
.exe is a windows executable file.  You cannot just run it in Ubuntu unless you use wine.  If you want to update your BIOS, why not just copy it to a floppy or a CD and boot from either floppy disk or a CD to update your BIOS.

---

### Post by piousp on 2009-01-14
To run an .EXE file on linux, you need the WINE library.

---

### Post by jozmoz on 2009-01-14
thanks for your reply. What is it I should copy to floppy or cd? When I go to the dell website, its just a download. Isn't that going to be an exe file?

---

### Post by Titan8990 on 2009-01-14
BIOS upgrades do not occur from within an OS. It must be done from your BIOS.

Also, upgrading your BIOS carries the risk of "bricking" your motherboard. It is not recommended to upgrade your BIOS unless there are features or bug fixes that are "must have."

---

### Post by Terl on 2009-01-14
> **jozmoz said:**
> Hi,

I'm trying to open an .exe file to upgrade my bios, But when I click on the file it just opens up the 'open with' box. Does anyone know how to open executable files?

Thanks.

I had a program like this to upgrade the bios in my Dell.  I ran mine using windows installation and then got rid of windows later.

Titan is right, these updates carry some risk with them.  I would not necessarily do the update if everything is running fine.

---

### Post by jozmoz on 2009-01-14
Its for a bug fix. My version bios won't allow me to upgrade my memory, just keeps failing. But as it seems its quite risky, i might leave it alone.

thanks for your help

---

### Post by Terl on 2009-01-14
> **jozmoz said:**
> Its for a bug fix. My version bios won't allow me to upgrade my memory, just keeps failing. But as it seems its quite risky, i might leave it alone.

thanks for your help

If you have windows on the box do it through there.  What brand pc do you have?  

The risky part comes in with doing it exactly as they say to do it.  I have upgraded my dell using the exe files they provide.  You run it in windows and it shuts the pc down and flashes the bios.  It worked.  I would not attempt to do it through WINE though.  That I would think would be risky.

---

### Post by boof1988 on 2009-01-14
If you absolutely need to flash your bios, there are some links that I can post for you that tell you how to make the boot media (with bios-flash exe included).

I have done this and boy I WAS NERVOUS.  Fortunately I didn't *brick* my computer.  I performed it on an extra computer so that there would be no severe loss if/when I screw it up.

Good luck with whatever choice you make.

---

### Post by fuser312 on 2009-01-14
i got it this way
1) start a terminal
2) sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list
3) sudo apt-get update
4) sudo apt-get install wine

i got it this way
then you could find your wine in application menu and start browsing for exe files and yes it becomes the default application for all your .exe files


but why should one go to linux if he still wants to open windows application, there is a easy way then, stick to windows and upgrade your bios  from there, but if i am right yes bios is not updated from a os

---

### Post by Terl on 2009-01-14
> **fuser312 said:**
> i got it this way
1) start a terminal
2) sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list
3) sudo apt-get update
4) sudo apt-get install wine

i got it this way
then you could find your wine in application menu and start browsing for exe files and yes it becomes the default application for all your .exe files


but why should one go to linux if he still wants to open windows application, there is a easy way then, stick to windows and upgrade your bios  from there, but if i am right yes bios is not updated from a os

While this is very helpful for installing WINE, the program he is trying to run is one that will flash his BIOS.  It won't work correctly I believe through WINE.  It is not just a routine windows program he is trying to run.

Your advice is good though for normal windows programs.

---

### Post by WitchCraft on 2009-01-14
> **fuser312 said:**
> 
but why should one go to linux if he still wants to open windows application, there is a easy way then, stick to windows

Dell only releases BIOS update exe's for windows.
There's no other way to run it than wine or windows.

Yes, I think the others are right when they say that using wine to run a BIOS update is dangerous. [COLOR="Red"]BIOS updates are dangerous. If they crashes right in the middle of the process, they can render your computer unusable **PERMANENTLY**. It's thus not recommendable using wine, since wine has many compatibility problems...
[/COLOR]

I'd do a minimal windows XP install, run the bios update, and whipe the XP partition afterwards.

---

### Post by Titan8990 on 2009-01-14
> I had a program like this to upgrade the bios in my Dell. I ran mine using windows installation and then got rid of windows late


Good info, didn't know it was possible.

---

### Post by Bölvaður on 2009-01-14
*deleted*

TO FUSER312:
There is an up to date version of wine in the repos, so you could have just installed it via add/remove or apt-get install it right away. Building from source would be the best way to get everything new and working.

*deleted*

---

### Post by donkyhotay on 2009-01-14
Couldn't the OP just make a windows boot disk from another computer with windows on it and use that instead of full-blown windows?

---

### Post by timcredible on 2009-01-14
if dell sold you the computer with ubuntu on it, then call them and ask them how you are supposed to be able to upgrade the bios since they sold you the pc with ubuntu and they should be responsible to provide you a way to upgrade their product with the software they provided.  if it came with windows, then they wouldn't be responsible for that.

---

### Post by Terl on 2009-01-14
> **timcredible said:**
> if dell sold you the computer with ubuntu on it, then call them and ask them how you are supposed to be able to upgrade the bios since they sold you the pc with ubuntu and they should be responsible to provide you a way to upgrade their product with the software they provided.  if it came with windows, then they wouldn't be responsible for that.

@jozmoz:  He is right; did you get the Dell with Ubuntu?  If they sold it to you that way they should have the bios fix for you as well.  Mine came with Vista and I just did the update and trashed Vista after that.

---

### Post by Titan8990 on 2009-01-14
Last time I checked the only Dell's that came with Ubuntu pre-installed were the Dell Mini Netbooks.

---

### Post by Bölvaður on 2009-01-14
> **timcredible said:**
> if dell sold you the computer with ubuntu on it......

Actually even if you didn't buy it with ubuntu on it it is still wrong of them to requiring you to have Windy as that is a customer choice that he can make afterwards which can be personal preference and doesn't break the warrenty.

---

### Post by Titan8990 on 2009-01-14
> **Bölvaður said:**
> Actually even if you didn't buy it with ubuntu on it it is still wrong of them to requiring you to have Windy as that is a customer choice that he can make afterwards which can be personal preference and doesn't break the warrenty.

It is wrong, but it is a reality. This is why I never buy pre-built machines.

---

### Post by Terl on 2009-01-14
> **Titan8990 said:**
> Last time I checked the only Dell's that came with Ubuntu pre-installed were the Dell Mini Netbooks.

A while back they did offer laptops and desktops with Ubuntu on them.  When I bought my laptop it was on the cheap because of Vista.  I googled the hardware and saw it would all work with Linux so I bought it with the intent of ditching windows.  

It would suck if they have no way to do the bios update without windows...but it would not surprise me.

---

### Post by Titan8990 on 2009-01-14
The BIOS of pre-built machines are typically VERY limited anyways... What is really bad is that consumers have no way of assembling their own laptops.

---

### Post by spcwingo on 2009-01-14
> **donkyhotay said:**
> Couldn't the OP just make a windows boot disk from another computer with windows on it and use that instead of full-blown windows?

+1  To make a MS-DOS boot floppy under XP just insert the floppy, open "My Computer", and right click "A:".  Choose create MS-DOS boot disk and press OK.  Just delete the autoexec.bat and config.sys on the floppy and transfer the bios .exe file to the floppy.  That's what I had to do on my old Dell Optiplex GX110 to update the bios.  Just take note that you won't be able to see autoexec.bat and config.sys on the floppy in windows unless you change the file settings to "display hidden system files".  Instead of doing that you can simply pop the floppy in an Ubuntu machine and delete them from there.

---

### Post by WitchCraft on 2009-01-14
> **Titan8990 said:**
> 
It is wrong, but it is a reality.


Sadly that's true. That's why I leave some 100 GB of my 250 GB hard disk to Windows. 60 for XP, 40 for Vista crap.

130 go to Linux, and 20 disappear for partitioning.

I'd whipe the Windows partitions if only wine worked better, so that I could run MS-Office and LotusNotes, which I need because I need them at my workplace, f***ing windows mafia. Or if OpenOffice wouldn't be the crap it is.

Wouldn't there be Windows, I'd finally have space to install and try FreeBSD on a computer with decent performance.


> **Titan8990 said:**
> 
This is why I never buy pre-built machines.


Me too, especially I hate having to buy Windows preinstalled on it, because I really hate putting money in Microsoft's A$$. But with a Laptop/Notebook, that is difficult...

---

### Post by chriscross93 on 2009-01-14
Ya, i'm gonna agree that flashing your bios with wine is REALLY risky.

---

