---
title: "need halp with clamav results, virus on a windows machine"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by braddcadd on 2009-01-03
Well, after three years of linux, I have no idea about windows anymore.  A friend has a virus.  Specifically this one:
[http://www.pcthreat.com/parasitebyid-6947en.html](http://www.pcthreat.com/parasitebyid-6947en.html)

However, after a livecd boot and scan with clamav, I got a lot of possible infected files.  Some of these don't look like viruses.  Can any clamav gurus help me decipher this result?

```

/media/disk/Documents and Settings/Rebecca/Local Settings/Temp/winvsnet.tmp: Trojan.VB-2883 FOUND
/media/disk/Program Files/Common Files/Microsoft Shared/VBA/VBA6/VBE6.DLL: W32.Virut.Gen.D-159 FOUND
/media/disk/Program Files/HP Games/Tinos Fruit Stand/FruitStand.exe: Trojan.Hupigon-9737 FOUND
/media/disk/Program Files/Microsoft Office/Office12/EXCEL.EXE: W32.Virut.Gen.D-163 FOUND
/media/disk/Program Files/Microsoft Office/Office12/excelcnv.exe: W32.Virut.Gen.D-163 FOUND
/media/disk/SWSetup/HPGame/games/tinosfruitstand-setup.exe: Trojan.Hupigon-9737 FOUND
/media/disk/System Volume Information/_restore{02AB5DEF-1097-4711-A644-97E93C8F5D09}/RP207/A0028273.rbf: W32.Virut.Gen.D-163 FOUND
/media/disk/System Volume Information/_restore{02AB5DEF-1097-4711-A644-97E93C8F5D09}/RP207/A0028283.rbf: W32.Virut.Gen.D-163 FOUND
/media/disk/System Volume Information/_restore{02AB5DEF-1097-4711-A644-97E93C8F5D09}/RP222/A0029981.rbf: W32.Virut.Gen.D-163 FOUND
/media/disk/System Volume Information/_restore{02AB5DEF-1097-4711-A644-97E93C8F5D09}/RP222/A0029991.rbf: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002119F20000000000000000F01FEC/12.0.4518/VBE6.DLL: W32.Virut.Gen.D-159 FOUND
/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002119F20000000000000000F01FEC/12.0.4518/XL12CNV.EXE: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002119F20000000000000000F01FEC/12.0.4518/EXCEL.EXE: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002119F20000000000000000F01FEC/12.0.6215/EXCEL.EXE: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002119F20000000000000000F01FEC/12.0.6215/XL12CNV.EXE: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/1526239.msp: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/152624b.msp: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/8a68ba5.msp: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/8a68bb7.msp: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/243d14c3.msp: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/243d14d5.msp: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/29f1e2c.msp: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/29f1e3e.msp: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/e3d43.msp: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/e3d69.msp: W32.Virut.Gen.D-163 FOUND

```

---

### Post by cariboo on 2009-01-03
A quick search using **W32.Virut.Gen.D-163** in google comes up with several links that suggest this is a false positive.

Jim

---

### Post by zenmatrix on 2009-01-03
For 

/media/disk/Documents and Settings/Rebecca/Local Settings/Temp/winvsnet.tmp: Trojan.VB-2883 FOUND
/media/disk/Program Files/Common Files/Microsoft Shared/VBA/VBA6/VBE6.DLL: W32.Virut.Gen.D-159 FOUND
/media/disk/Program Files/HP Games/Tinos Fruit Stand/FruitStand.exe: Trojan.Hupigon-9737 FOUND
/media/disk/Program Files/Microsoft Office/Office12/EXCEL.EXE: W32.Virut.Gen.D-163 FOUND
/media/disk/Program Files/Microsoft Office/Office12/excelcnv.exe: W32.Virut.Gen.D-163 FOUND
/media/disk/SWSetup/HPGame/games/tinosfruitstand-setup.exe: Trojan.Hupigon-9737 FOUND
/media/disk/System Volume Information/_restore{02AB5DEF-1097-4711-A644-97E93C8F5D09}/RP207/A0028273.rbf: W32.Virut.Gen.D-163 FOUND
/media/disk/System Volume Information/_restore{02AB5DEF-1097-4711-A644-97E93C8F5D09}/RP207/A0028283.rbf: W32.Virut.Gen.D-163 FOUND
/media/disk/System Volume Information/_restore{02AB5DEF-1097-4711-A644-97E93C8F5D09}/RP222/A0029981.rbf: W32.Virut.Gen.D-163 FOUND
/media/disk/System Volume Information/_restore{02AB5DEF-1097-4711-A644-97E93C8F5D09}/RP222/A0029991.rbf: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002119F20000000000000000F01FEC/12.0.4518/VBE6.DLL: W32.Virut.Gen.D-159 FOUND
/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002119F20000000000000000F01FEC/12.0.4518/XL12CNV.EXE: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002119F20000000000000000F01FEC/12.0.4518/EXCEL.EXE: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002119F20000000000000000F01FEC/12.0.6215/EXCEL.EXE: W32.Virut.Gen.D-163 FOUND
/media/disk/WINDOWS/Installer/$PatchCache$/Managed/00002119F20000000000000000F01FEC/12.0.6215

I would uninstall office and the fruit stand game, if that was a free game possible came from that, and the rest is installer cache for office and system restore points, then boot the system up and run a windows script call smitfraudfix and then run clamav on the windows machine and see were you get

---

### Post by LowSky on 2009-01-03
malwarebyte antimalware is free and will get rid od antivirus 2009

i used it on my dad's pc, works great and its free

[http://www.download.com/Malwarebytes-Anti-Malware/3000-8022_4-10804572.html?tag=mncol](http://www.download.com/Malwarebytes-Anti-Malware/3000-8022_4-10804572.html?tag=mncol)

---

### Post by zenmatrix on 2009-01-03
malwarebytes is great just make sure not to run it in safemode as it cause a bunch of programs and check on a windows forum for what to remove

---

### Post by braddcadd on 2009-01-03
Well the computer is completely unusable between freezes and the virus halting your every action.  I will have to remove some of the virus files with the liveCD.

---

### Post by |{urse on 2009-01-03
score another win for smitfraud.C

---

### Post by zenmatrix on 2009-01-03
Have you tried booting it into safemode /w networking.

---

### Post by braddcadd on 2009-01-03
> **zenmatrix said:**
> Have you tried booting it into safemode /w networking.


Actually, no, maybe I should try that next, but one of the earlier posts said that malwarebytes (supposedly the only virus scanner that can detect&fix this virus) does not work well in safe mode.  I am running out of options so safe mode will come soon.

Right now I have deleted the files listed here:
[http://www.pcthreat.com/parasitebyid-6947en.html](http://www.pcthreat.com/parasitebyid-6947en.html)

However there are still popups that block IE use completely.

---

### Post by 2hot6ft2 on 2009-01-03
> **braddcadd said:**
> Well, after three years of linux, I have no idea about windows anymore.  A friend has a virus.  Specifically this one:
[http://www.pcthreat.com/parasitebyid-6947en.html](http://www.pcthreat.com/parasitebyid-6947en.html)

However, after a livecd boot and scan with clamav, I got a lot of possible infected files.  Some of these don't look like viruses.  Can any clamav gurus help me decipher this result?

```

/media/disk/Documents and Settings/Rebecca/Local Settings/Temp/winvsnet.tmp: Trojan.VB-2883 FOUND
[COLOR="Red"]/media/disk/Program Files/HP Games/Tinos Fruit Stand/FruitStand.exe: Trojan.Hupigon-9737 FOUND[/COLOR]
/media/disk/SWSetup/HPGame/games/tinosfruitstand-setup.exe: Trojan.Hupigon-9737 FOUND

```
Well once you eliminate all the W32.Virut.Gen.D-163 ones all that's left are these. I would browse to them using linux and delete them by right clicking and delete permanently bypassing the trash.

Then once back in windows I would uninstall FruitStand and any reference to it and Tinos Fruit Stand turn off recovery since it's going to be in there too. clean the registry, system clean up. Then rescan to make sure it's all gone.

Then turn recovery back on.

---

### Post by braddcadd on 2009-01-03
OK, I will try that.  What do you mean by turn on/off recovery.

---

### Post by braddcadd on 2009-01-04
It was nasty but I got it.  Here are the details for others.
[B]
I had to download malwarebytes and the virus definitions on a 2nd computer (ubuntu).  Then transfer those files to the infected computer with a thumbdrive.  Then I had to run the files in safe mode (no networking).
[/B]
Here is a summary of what didn't work:
1) Windows normal mode would lockup after 30 seconds or so.
2) IE would block any attempt to download anything or get to any website.
3) Norton and Mcafee were both disables by the virus.
4) Safe Mode (with networking) crashed the same way normal mode did.
5) Deleteing the exe's & dll's with an Ubuntu LiveCD did not help at all.

---

### Post by 2hot6ft2 on 2009-01-04
> **braddcadd said:**
> OK, I will try that.  What do you mean by turn on/off recovery.
Windows system recover/system restore it creates a backup so you can restore it to a previous state. It's been a while but let's see if I remember where it is.
Start->Programs->Accessories->System Restore should be at the bottom.
You can turn it off, recover to a previous state, set it to how often to make a backup, and a few other options. If you get it running you may want to restore it to one of the backups say 2 weeks back you know one where you know it was before getting the virus before turning it off.

Once you do that you'll want to turn it off so it's not saving the virus in infected files. After the virus is cleaned out and you're sure it's gone you'll want to reboot before turning it back on..
> **braddcadd said:**
> 
Here is a summary of what didn't work:
1) Windows normal mode would lockup after 30 seconds or so.
2) IE would block any attempt to download anything or get to any website.
3) Norton and Mcafee were both disables by the virus.
4) Safe Mode (with networking) crashed the same way normal mode did.
5) Deleteing the exe's & dll's with an Ubuntu LiveCD did not help at all.
1) Do you have a windows install disc or is there a recovery option at boot?
 If there is or you do you can boot into recovery mode and select restore system, It's one of the options and what it does is replace any damaged or missing system files using the ones on the disc or recovery partition. Not a complete system reinstall. That way most everything will still work....apps and such.

2) It's probibly blocking sites using anti virus blocklists which brings us to 3

3) This sounds a lot like what I got in windows which helped prompt me to stop using it. IN linux browse to the anti virus applications folders they'll be in the programs folder and listed by name like Norton and look for files like "exceptions.txt" anything that sounds like it's for things to allow or block. Open them with a text viewer and if anything looks wrong remove it. Like an exceptions list you may want to make it an empty list file.
What it does is adds itself to an exceptions list or to an allow list. That way the program will ignore it.

4) I always hated safe mode in windows. It always screwed my graphics up in real mode. No help there.

5) It helped you just aren't seeing it yet after all they were infected. 
Is it xp or vista? If it's xp I can copy and attach my clean files from xp and you can put them where the dirty files were since they may be needed by the system to work properly.

If it's vista you would either have to get them from another vista pc or off the vista cd. Since I don't have vista on either of my pc's.

You may also want to try running AVG on your livecd and having it look at her windows the install would work it just wouldn't be there after a reboot since it would only be in RAM. [https://help.ubuntu.com/community/Antivirus/Avg](https://help.ubuntu.com/community/Antivirus/Avg)

While AVG wont remove anything it finds it will show you where they are. Then you just browse to them and kill them.

Another thing. Do you have right click delete bypassing the trash enabled? If not it would be a good idea to enable it otherwise you're putting the infected files in a trash bin on the infected pc.

Open a folder with nautilus then Edit->Preferences->Behavior-> last option at the bottom.

Hope this is helpful.

---

### Post by 2hot6ft2 on 2009-01-04
Here's another livecd with 3 anti virus programs already on it in case you want to give it a try. I keep one around just in case. It's called the Ultimate Boot CD and has
F-Prot Antivirus for DOS
McAfee Antivirus Scanner
and
BugHunter

It's here. [http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/)

And was found here. [http://www.livecdlist.com/?pick=Linux_x86&showonly=Rescue](http://www.livecdlist.com/?pick=Linux_x86&showonly=Rescue)

Free Vista recovery cd's are available for download here
[http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/](http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/)
Pick the 32 bit or 64 bit that matches the system she has.

---

### Post by 2hot6ft2 on 2009-01-04
Must be Vista. I just checked and I don't have the same folders she does so can't be of any help with replacing the infected files after all.

---

