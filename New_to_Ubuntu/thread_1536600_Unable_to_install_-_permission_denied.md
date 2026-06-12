---
title: "Unable to install - permission denied"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by elasticsoul on 2010-07-22
Hallelujah - Ubuntu is installed and working! Thanks to all for your help. The problem ultimately appears to have been a flaky CD drive. When I opened it and cleaned it, the installation completed. I have already contacted the seller, and he will replace the CD drive. 
 
:popcorn: for everyone!
 
Hi all,
 
Also posted in Dell support; my apologies if that's not acceptable here. 
 
 
 

I just bought a new-to-me Dell C640 with Win XP, with the intention of wiping it clean and going Ubuntu. Tired of Windows, and time to learn the future! Unfortunately, the future has been delayed due to installation issues. Here's what I did:[LIST=1]
[*]Burned a CD, checked the MD5, verified it, etc, on another computer.
[*]Attempted to boot from the CD on the 'new' Dell, but it never does.
[/LIST]There is much CD and hard drive activity, then nothing. The initial Ubuntu screen with the 5 dots (equivalent to hourglass) stays on the screen forever. When I reboot in Win XP and check the log, there are "permission denied errors" - no idea if this is the problem. 
 
UPDATE: Re-re-re-attempted installation after deleting the log file. Now getting multiple "Authentication failure" messages down the screen, alternating with what appears to be a list of tasks being attempted by the installer. The latter flashes on the screen very briefly, so it's hard to see much of it. The last line is roughly: 
[1990.numbers] SQUASHFS error: Unable to read page, block 487985, size 85ae
 
The log file is below. Please help me dump Windows...
 
Thanks all,
Brian
 
07-21 21:28 INFO root: === wubi 10.04 rev189 ===
07-21 21:28 DEBUG root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-10.04-rev189.log
07-21 21:28 DEBUG root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
07-21 21:28 DEBUG CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.t mp\data
07-21 21:28 DEBUG WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\bin \7z.exe
07-21 21:28 DEBUG CommonBackend: Fetching basic info...
07-21 21:28 DEBUG CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
07-21 21:28 DEBUG CommonBackend: platform=win32
07-21 21:28 DEBUG CommonBackend: osname=nt
07-21 21:28 DEBUG CommonBackend: language=en_US
07-21 21:28 DEBUG CommonBackend: encoding=cp1252
07-21 21:28 DEBUG WindowsBackend: arch=i386
07-21 21:28 DEBUG CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tm p\data\isolist.ini
07-21 21:28 DEBUG CommonBackend: Adding distro Xubuntu-i386
07-21 21:28 DEBUG CommonBackend: Adding distro Xubuntu-amd64
07-21 21:28 DEBUG CommonBackend: Adding distro Kubuntu-amd64
07-21 21:28 DEBUG CommonBackend: Adding distro Mythbuntu-i386
07-21 21:28 DEBUG CommonBackend: Adding distro Ubuntu-amd64
07-21 21:28 DEBUG CommonBackend: Adding distro Ubuntu-i386
07-21 21:28 DEBUG CommonBackend: Adding distro Mythbuntu-amd64
07-21 21:28 DEBUG CommonBackend: Adding distro Kubuntu-i386
07-21 21:28 DEBUG CommonBackend: Adding distro KubuntuNetbook-i386
07-21 21:28 DEBUG CommonBackend: Adding distro UbuntuNetbook-i386
07-21 21:28 DEBUG WindowsBackend: Fetching host info...
07-21 21:28 DEBUG WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVer sion\Uninstall\Wubi
07-21 21:28 DEBUG WindowsBackend: windows version=xp
07-21 21:28 DEBUG WindowsBackend: windows_version2=Microsoft Windows XP
07-21 21:28 DEBUG WindowsBackend: windows_sp=Service Pack 3
07-21 21:28 DEBUG WindowsBackend: windows_build=2600
07-21 21:28 DEBUG WindowsBackend: gmt=-8
07-21 21:28 DEBUG WindowsBackend: country=US
07-21 21:28 DEBUG WindowsBackend: timezone=America/Los_Angeles
07-21 21:28 DEBUG WindowsBackend: windows_username=Administrator
07-21 21:28 DEBUG WindowsBackend: user_full_name=Administrator
07-21 21:28 DEBUG WindowsBackend: user_directory=C:\Documents and Settings\Administrator
07-21 21:28 DEBUG WindowsBackend: windows_language_code=1033
07-21 21:28 DEBUG WindowsBackend: windows_language=English
07-21 21:28 DEBUG WindowsBackend: processor_name= Mobile Intel(R) Pentium(R) 4 - M CPU 1.70GHz
07-21 21:28 DEBUG WindowsBackend: bootloader=xp
07-21 21:28 DEBUG WindowsBackend: system_drive=Drive(C: hd 23199.3789063 mb free ntfs)
07-21 21:28 DEBUG WindowsBackend: drive=Drive(C: hd 23199.3789063 mb free ntfs)
07-21 21:28 DEBUG WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-21 21:28 DEBUG WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-21 21:28 DEBUG WindowsBackend: previous_target_dir=C:\ubuntu
07-21 21:28 DEBUG WindowsBackend: previous_distro_name=Ubuntu
07-21 21:28 DEBUG WindowsBackend: keyboard_id=67699721
07-21 21:28 DEBUG WindowsBackend: keyboard_layout=us
07-21 21:28 DEBUG WindowsBackend: keyboard_variant=
07-21 21:28 DEBUG CommonBackend: python locale=('en_US', 'cp1252')
07-21 21:28 DEBUG CommonBackend: locale=en_US.UTF-8
07-21 21:28 DEBUG WindowsBackend: total_memory_mb=1023.4296875
07-21 21:28 DEBUG CommonBackend: Searching ISOs on USB devices
07-21 21:28 DEBUG CommonBackend: Searching for local CDs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
07-21 21:28 DEBUG Distro: does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3.tmp\casper \filesystem.squashfs
07-21 21:28 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-21 21:28 DEBUG Distro: parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
07-21 21:28 DEBUG Distro: parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
07-21 21:28 DEBUG Distro: wrong arch: i386 != amd64
07-21 21:28 DEBUG Distro: checking whether D:\ is a valid Ubuntu CD
07-21 21:28 INFO Distro: Found a valid CD for Ubuntu: D:\
07-21 21:28 INFO root: Running the uninstaller...
07-21 21:28 INFO CommonBackend: This is the uninstaller running
07-21 21:28 DEBUG WindowsFrontend: __init__...
07-21 21:28 DEBUG WindowsFrontend: on_init...
07-21 21:28 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3. tmp\translations, languages=['en_US', 'en']
07-21 21:28 INFO root: Received settings
07-21 21:28 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3. tmp\translations, languages=['en_US', 'en']
07-21 21:28 DEBUG TaskList: # Running tasklist...
07-21 21:28 DEBUG TaskList: ## Running Backup ISO...
07-21 21:28 DEBUG TaskList: ## Finished Backup ISO
07-21 21:28 DEBUG TaskList: ## Running Remove bootloader entry...
07-21 21:28 ERROR WindowsBackend: Cannot find bcdedit
07-21 21:28 DEBUG WindowsBackend: undo_bootini C:
07-21 21:28 DEBUG WindowsBackend: undo_configsys Drive(C: hd 23199.3789063 mb free ntfs)
07-21 21:28 DEBUG TaskList: ## Finished Remove bootloader entry
07-21 21:28 DEBUG TaskList: ## Running Remove target dir...
07-21 21:28 DEBUG CommonBackend: Deleting C:\ubuntu
07-21 21:28 DEBUG TaskList: ## Finished Remove target dir
07-21 21:28 DEBUG TaskList: ## Running Remove registry key...
07-21 21:28 DEBUG TaskList: ## Finished Remove registry key
07-21 21:28 DEBUG TaskList: # Finished tasklist
07-21 21:28 INFO root: Almost finished uninstalling
07-21 21:28 INFO WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl3. tmp\translations, languages=['en_US', 'en']
07-21 21:28 INFO root: Finished uninstallation
07-21 21:28 DEBUG root: application.quit
07-21 21:28 DEBUG WindowsFrontend: frontend.quit
07-21 21:28 DEBUG WindowsFrontend: frontend.on_quit
07-21 21:28 DEBUG root: application.on_quit
07-21 21:28 INFO root: sys.exit

---

### Post by roger_1960 on 2010-07-22
Hi

Are you trying to run ubuntu using wubi (ie with windows running) or by powering up the PC with the ubuntu live disk in the CD drive (should not then appear in windows log file)?

---

### Post by rustutzman on 2010-07-22
Put the Ubuntu CD in the drive. As soon as something appears on your screen hit F12. This should give you a boot device menu. Select the CD drive and you should be off and running.

Russ

---

### Post by elasticsoul on 2010-07-22
Hi Roger and rustutzman - I first tried booting from the Ubuntu CD. When that didn't work, tried running wubi.exe, which also didn't work. That may be why both appear in the log file. 
 
I also notice a lot of 'uninstall'-related info in the log file. When I tried to run wubi, it detected an existing installation of Ubuntu and asked to first uninstall it, which I told it to do. 
 
To double-check this, I just deleted the log file and am now booting from the CD.

---

### Post by Jazzy_Jeff on 2010-07-22
If the live cd does not work for you try downloading the alternate install cd and use that. It is text based but easy to follow. I always seem to have problems with the live cd's myself.

---

### Post by elasticsoul on 2010-07-22
UPDATEd original post as follows:
 
UPDATE: Re-re-re-attempted installation after deleting the log file. Now getting multiple "Authentication failure" messages down the screen, alternating with what appears to be a list of tasks being attempted by the installer. The latter flashes on the screen very briefly, so it's hard to see much of it. The last line is roughly: 
[1990.numbers] SQUASHFS error: Unable to read page, block 487985, size 85ae, and there are lots of lines like this. 
 
I will now attempt the alternate install....

---

### Post by Am Elder on 2010-07-22
Posting in this thread instead of the [one in the Dell Ubuntu forum]("http://ubuntuforums.org/showthread.php?t=1536593") because this doesn't seem to be tied to the computer model.

A little more time with Google and here's what I've found.  Other  people have got the **SQUASHFS error:** and the problem has been [registered with the  bug tracker]("https://bugs.launchpad.net/ubuntu/+bug/172937"), but according to the write-up it's not an issue  with Ubuntu as far as anyone knows.

There's a list of possible causes on Launchpad and [on the wiki]("https://help.ubuntu.com/community/SquashfsErrors").  You might have a  hardware problem.  You seem to be pretty comfortable trouble shooting and problem solving yourself, but come back to us if you need any help at all figuring out how to test the suggestions in Launchpad or on the associated wiki page (they're pretty much the same).

[**Edit:** this isn't a solution to the first problem you were having.]

---

### Post by elasticsoul on 2010-07-22
Thanks very much, AM. I am currently running the Windows Memory Diagnostic (no errors so far). It could also be the CD drive, but that did successfully boot from the memory test CD. Next I'll try the alternate Ubuntu installation CD and see how that goes.

---

### Post by Am Elder on 2010-07-22
Well, if it's a new computer for you, it'd be really nice if it *weren't* a hardware problem.

---

### Post by elasticsoul on 2010-07-22
It certainly would! My blood pressure went up when I saw that the list of likely problems consisted of all hardware issues (I had already checked the CD image). The vendor I bought it from would repair it for free, but then of course there's the hassle and time lost to do that.

---

### Post by egalvan on 2010-07-22
Did you run the "check media for errors" boot option?

It should be just before the memory test option (but my memory on this is fuzzy)


I try to always use torrents, with their built-in error checking, 
then always run the "check media" option to be *sure* it's OK.

---

### Post by elasticsoul on 2010-07-22
The alternate installation failed, too. During the "Select and install software" step, approximately when retrieving file 929, it bombed out.

---

### Post by RJARRRPCGP on 2010-07-22
> **elasticsoul said:**
> The alternate installation failed, too. During the "Select and install software" step, approximately when retrieving file 929, it bombed out.

Sounds like the optical drive may be garbage.

---

### Post by Am Elder on 2010-07-22
I'm sorry to hear that didn't work.  The first time I installed Ubuntu,  it took me quite a long time and I had a fairly smooth ride.

I guess you've eliminated the following possibilities:
- It's not a corrupted ISO.
- It's not a bad memory module.
- The computer doesn't just need the alternative install disk.

---

### Post by elasticsoul on 2010-07-22
I'm leaning heavily toward that. The seller will swap it out later today...just means 2 hours of my time to go get it done, plus the several I've spent (so far) trying to install Ubuntu.

---

### Post by elasticsoul on 2010-07-22
Thanks everyone for your help so far. With your help I've checked, and in some cases double and triple-checked, the CD, the RAM, the iso images for graphical and alternate installs, and a few things I've forgotten. It looks like the CD drive may be the culprit, and I'll be getting it swapped out later today...

---

### Post by walt.smith1960 on 2010-07-22
Using the LiveCD, does it ever get to the point where you have a choice to either run from the CD or install?  Do you get all the installation errors if you don't attempt to install to the hard drive?

---

### Post by elasticsoul on 2010-07-22
Hi Walt - no, I just get the 5 dots. It never boots into Ubuntu to run from the CD or to install.

---

