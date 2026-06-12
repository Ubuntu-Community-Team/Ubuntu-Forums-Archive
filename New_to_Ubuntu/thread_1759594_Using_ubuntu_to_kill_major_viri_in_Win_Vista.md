---
title: "Using ubuntu to kill major viri in Win Vista"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by mward69 on 2011-05-15
Hey folks, thank GOD for linux!!
  Ok here is my issue...I need to use Ubu to clean a mac daddy viri in my vista boot.....{Using Dual Boot}

 The 1st viri statred off as "Vista Recovery" saying there was issues on the HD..then all hell started :(
 I can't access regedit, or ANYTHING in safemode to fix...
 Tried logging into wifes profile and got regedit..managed to DEL some of the reg entrys then Win Antiviri 2011 popped up...

 I DL'd Clamtk and tried to run it, but it fades out and fails to respond.......

 I need help killing this Vista Viri.....any help?

*******Forgot to add, this virus is hiding ALL my files in Windows!! I can see them in Linux.....*** really serious virus***

---

### Post by jtarin on 2011-05-15
> **mward69 said:**
> Hey folks, thank GOD for linux!!
  Ok here is my issue...I need to use Ubu to clean a mac daddy viri in my vista boot.....{Using Dual Boot}

 The 1st viri statred off as "Vista Recovery" saying there was issues on the HD..then all hell started :(
 I can't access regedit, or ANYTHING in safemode to fix...
 Tried logging into wifes profile and got regedit..managed to DEL some of the reg entrys then Win Antiviri 2011 popped up...

 I DL'd Clamtk and tried to run it, but it fades out and fails to respond.......

 I need help killing this Vista Viri.....any help?

*******Forgot to add, this virus is hiding ALL my files in Windows!! I can see them in Linux.....*** really serious virus***
**(1)**Transfer all your wanted files to a clean location preferably off computer. Then reinstall.
**(2)**[Google for an anti-virus boot disc .iso.]("http://www.google.com/#sclient=psy&hl=en&site=&source=hp&q=anti-virus+boot+disc+.iso&btnG=Google+Search&aq=f&aqi=&aql=&oq=anti-virus+boot+disc+.iso&bav=on.2,or.r_gc.r_pw.&fp=c1f77ad16103bc7b") Download, burn and boot to rid yourself of the virus.
There are many scenarios, but these are two.

---

### Post by tkelito on 2011-05-15
This is not a serious virus.  It hides everything in your user account, just unhide in Windows and apply to subdirectories.  Tools -> Folder Options -> Advanced

15 Minute fix -->

Windows Recovery is usually named gog.exe and is stored in 

C:\Users\%username%\AppData\Local\gog.exe (or something similar, I've seen pyk.exe, r89.exe, jdakdf.exe, you'll know it when you see it, but it will be there).

[Also check C:\Program Data -> Vista and Win 7 are secure enough to block access to System32, there is nothing damaging to the point of reload, it is bad advice.  You could just kill the user account and make a new one. Just run a rootkit scan after.]

It disables the ability to run .exes in Windows

To fix that go to [http://getavz.com](http://getavz.com) and download that avz.zip program.

Extract avz4 and rename avz4.exe to avz4.com - you will now be able to run the app.

Go to File -> System Restore and check the box next to "Reset .com, .exe, and .pifs" then Execute selected option.

Cool, now it is time to make sure you are clean.  Google search for Norton Power Eraser then download/run and allow it to fix things. Make sure to allow a restart/scan for rootkits.  

Next step, google search for TDSSKiller and download/run that.  If clean, next step.  If not allow it to do all the work for it.  Yes it is that easy.

Install Microsoft Security Essentials or your AV of choice.  If that is clean download and install CCleaner and clear out all temps and fix registry issues.  CCleaner can also edit your startup items and delete the now dead links to the fake av infection.

Should take no more than 15 minutes (this post took longer...).  And unless you have other infections you can access safe mode, that form of Malware/Scareware doesn't stop safe mode from booting.




Source: Years of beating down Windows client boxes.

---

### Post by Mark Phelps on 2011-05-16
If your PC can boot from CD, and you have access to another PC to burn CDs, go to the Kasperky site, download and burn their Rescue CD.  Boot from that, connect to the Internet and download the latest updates, and run a scan to clean your PC.

Once that works and you can boot back into Vista, download and install MalwareBytes Anti-Malware -- and run it.

Also, as previously mentioned, get the TDSSKiller from Kasepersky and run it.  That does a great job of finding and killing root kits.

---

### Post by bobbob1016 on 2011-05-16
> **jtarin said:**
> **(1)**Transfer all your wanted files to a clean location preferably off computer. Then reinstall.
**(2)**[Google for an anti-virus boot disc .iso.]("http://www.google.com/#sclient=psy&hl=en&site=&source=hp&q=anti-virus+boot+disc+.iso&btnG=Google+Search&aq=f&aqi=&aql=&oq=anti-virus+boot+disc+.iso&bav=on.2,or.r_gc.r_pw.&fp=c1f77ad16103bc7b") Download, burn and boot to rid yourself of the virus.
There are many scenarios, but these are two.

I always go for option 1.  Much easier, and you *know* for a fact, that your install is clean.

tkelito's suggestion may work, but the virus writers are always a step ahead of the anti-virus guys.  And there is no way to know which iteration of the virus you have, as it could have been tweaked a little, to avoid Norton Power Eraser.  Then once it sees another anti-virus, it could hide itself.  They are always finding crafty ways to hide.  I remember one that was hiding in the NTFS logs or whatever.

It's however you feel more comfortable, but I always opt for the reinstall.

---

### Post by tkelito on 2011-05-16
Proof of concept on this scareware infection:

1) It is designed to hold your data/computer hostage, that is why his data is now hidden and he cannot run .exes
2) The entire goal is to get the end user to purchase the software wherein their credit/debit card information will be harvested
3) It puts a blank proxy in IE so you cannot get online
4) Uses a rootkit (sometimes) to attach you to a botnet


That is it.  It does not infect System32 past what NPE/TDSSKiller will fix and is not worthy of a reload.  The infections from XP days do not hit Vista and 7 (especially 64-bit) with the wrath of god as they do with XP.  


I work in the security field and deal with Rogue Security Products on a daily basis.

1) Delete infection from AppData
2) Run AVZ to restore .exe's
3) Norton Power Eraser
4) TDSSKiller (Should be clean but it is an extra rootkit precaution)
5) CCleaner to kill Temps, broken registry and delete bad msconfig items
6) Microsoft Security Essentials
7) Install Firefox and/or Chrome with Adblock Plus

7) If really nervous run Malwarebytes AntiMalware and either post or PM me a HiJackThis log.


This infection encompasses 2 files in Appdata\Local\xyz.exe and a xyz.sys (both hidden/system files).  It only adds 2 registry keys and one is just to link to msconfig for it to autostart.

These guys aren't clever virus writers, the prey on the end user who has been conditioned to just hit continue anytime they see User Account Control pop up in the Windows world.

---

### Post by bobbob1016 on 2011-05-16
It could be the part you recognize, the one you know how to fix, plus a much deeper payload as well.  There is no way to tell.  If the virus is beyond detection at the moment, there will be no way to attribute it to the current infection.  When you run a scan later, and they are able to detect the deeper infection payload, you could simply say you caught another virus, not that this current one installed it.

tldr; There could be a more devious virus that is distracting you with an "easy" to remove virus.

---

### Post by Allavona on 2011-05-16
This reminds me of a video I saw once where a guy was installing XP and got the "your computer is infected" virus before the system was even installed!!

> These guys aren't clever virus writers, the prey on the end user who has  been conditioned to just hit continue anytime they see User Account  Control pop up in the Windows world. 	

Amen to that! The thing I tell everyone about windows user account control is this: It, if it does anything else, will tell you whats going on. Take the extra second to read what windows is telling you!

---

### Post by tkelito on 2011-05-16
> **Allavona said:**
> This reminds me of a video I saw once where a guy was installing XP and got the "your computer is infected" virus before the system was even installed!!

Probably a boot sector rootkit on a different partition that he ran a recovery from.  Manufacturers like Toshiba install the Boot to the D: and not the C: which is almost frustrating as you have to run (in a recovery console or preinstallation environment)

cmd
D:
bootrec /fixboot
bootrec /fixmbr
bootrec /rebuildbcd

On all of them if they get a rootkit.  


To anyone paranoid, I've been following the evolution of the Rogue Security Products for almost 4 years.  It is something I consider myself an expert in.

---

### Post by jtarin on 2011-05-16
> **tkelito said:**
> Probably a boot sector rootkit on a different partition that he ran a recovery from.  Manufacturers like Toshiba install the Boot to the D: and not the C: which is almost frustrating as you have to run (in a recovery console or preinstallation environment)

cmd
D:
bootrec /fixboot
bootrec /fixmbr
bootrec /rebuildbcd

On all of them if they get a rootkit.  


To anyone paranoid, I've been following the evolution of the Rogue Security Products for almost 4 years.  It is something I consider myself an expert in.
I think he was refering to a comedic video.

---

### Post by 3602 on 2011-05-16
Anti-virus disk is your friend. AVG or Kaspersky up there.
And please get yourself an anti-virus software. I used Avast! Free for a while.

---

### Post by coffee412 on 2011-05-16
Hello, 

Interesting subject going here. Id like to chime in. However, Iam no expert at viruses. However, Iam persistant :P

I usually just boot into safe mode and install and run Malwarebytes. Then reboot and install avast. I have been paying more attention to rootkits now however and the earlier posts about tdsskiller is much appreciated.

I do alot of this for a living right now and sometimes its just less expensive to the customer to backup their personal files and reinstall. Otherwise its big bucks. So, I dont really dig really deep to get rid of stuff as its just not worth the money for the customer.

Thanks for all the hints everyone,

coffee :P

---

### Post by crispy_420 on 2011-05-16
So what is the _exact_ name of the fake AV program that took over your system? An exact name will help me find a solution for you.

From the linux side try installing BitDefender, they have a free version for home use. Update and scan the Windows partition. AVG also has a command line version I think.

---

### Post by conveyancingquote on 2011-05-16
Well it can be a boot virus. Maybe you can install the latest avast version. There is an option called boot scan. most probably it will remove every infections. But try first whether u are able to install anything new.

---

### Post by mward69 on 2011-05-16
Hey folks, thanks for the reply's...in finally gave up, burned any pics and what-nots I wanted and reinstalled Vista....
  The viri was Vista Recovery...but I do remember win 2011 popping up also...{Got to stay away from those Adult sites} :P  j/k

  The problem that pissed me off was even under safe mode, it's wouldn't allow me to do hardly anything....I did manage to run a few progs. that were sugg., but they came up clean. Every time I would edit the REGEDIT, the dang keys would re-write themselves.

 I got it back running for the wife, I stay in Ubu......trying to get her to enjoy it. She had to use it all day today, but as she put's it..."it's not windows"......well DUH! :P

---

### Post by jtarin on 2011-05-16
> **coffee412 said:**
> 
I do alot of this for a living right now and sometimes its just less expensive to the customer to backup their personal files and reinstall. Otherwise its big bucks. So, I dont really dig really deep to get rid of stuff as its just not worth the money for the customer.

Thanks for all the hints everyone,

coffee :PMy philosophy also......by experience a backup,off-disk, is the best way to go.Fast and cheap.

---

### Post by tkelito on 2011-05-17
> **mward69 said:**
> Every time I would edit the REGEDIT, the dang keys would re-write themselves.


You needed to browse to AppData and delete the .sys and .exe.  They rebuild the registry keys for the program to autorun everytime it starts or every x minutes.


Glad you are happy with the end result though.

---

### Post by crispy_420 on 2011-05-18
If it comes back again or are just curious, here is a good removal guide:

[http://www.bleepingcomputer.com/virus-removal/remove-windows-vista-recovery](http://www.bleepingcomputer.com/virus-removal/remove-windows-vista-recovery)

Looks like removal is complicated but not the worst I have seen.

---

