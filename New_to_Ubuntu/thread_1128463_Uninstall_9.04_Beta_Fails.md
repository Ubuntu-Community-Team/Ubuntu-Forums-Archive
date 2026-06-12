---
title: "Uninstall 9.04 Beta Fails"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by coover on 2009-04-17
I wish to replace 9.04 Beta with 9.04 RC and this requires the Beta to be unistalled. When I attempt to do so, I get an error message that a file is missing. I have attached a jpg of the error message and copied the uninstall log, which I do not understand, below.

04-17 12:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile=C:\\ubuntu\\uninstall-wubi.exe']
04-17 12:16 INFO   root: === wubi 9.04 rev105 ===
04-17 12:16 DEBUG  root: Logfile is c:\users\acer\appdata\local\temp\wubi-9.04-rev105.log
04-17 12:16 DEBUG  CommonBackend: data_dir=C:\Users\Acer\AppData\Local\Temp\pylF115.tmp\data
04-17 12:16 DEBUG  WindowsBackend: 7z=C:\Users\Acer\AppData\Local\Temp\pylF115.tmp\bin\7z.exe
04-17 12:16 DEBUG  CommonBackend: Fetching basic info...
04-17 12:16 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-17 12:16 DEBUG  CommonBackend: platform=win32
04-17 12:16 DEBUG  CommonBackend: osname=nt
04-17 12:16 DEBUG  CommonBackend: language=en_US
04-17 12:16 DEBUG  CommonBackend: encoding=cp1252
04-17 12:16 DEBUG  WindowsBackend: arch=amd64
04-17 12:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\Acer\AppData\Local\Temp\pylF115.tmp\data\isolist.ini
04-17 12:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-17 12:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-17 12:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-17 12:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-17 12:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-17 12:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-17 12:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-17 12:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-17 12:16 DEBUG  WindowsBackend: Fetching host info...
04-17 12:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-17 12:16 DEBUG  WindowsBackend: windows version=vista
04-17 12:16 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
04-17 12:16 DEBUG  WindowsBackend: windows_sp=Service Pack 1
04-17 12:16 DEBUG  WindowsBackend: windows_build=6001
04-17 12:16 DEBUG  WindowsBackend: gmt=-8
04-17 12:16 DEBUG  WindowsBackend: country=US
04-17 12:16 DEBUG  WindowsBackend: timezone=America/Los_Angeles
04-17 12:16 DEBUG  WindowsBackend: windows_username=Acer
04-17 12:16 DEBUG  WindowsBackend: user_full_name=Acer
04-17 12:16 DEBUG  WindowsBackend: user_directory=Acer
04-17 12:16 DEBUG  WindowsBackend: windows_language_code=1033
04-17 12:16 DEBUG  WindowsBackend: windows_language=English
04-17 12:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz
04-17 12:16 DEBUG  WindowsBackend: bootloader=vista
04-17 12:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 124891.828125 mb free )
04-17 12:16 DEBUG  WindowsBackend: drive=Drive(C: hd 124891.828125 mb free )
04-17 12:16 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
04-17 12:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-17 12:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-17 12:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-17 12:16 DEBUG  WindowsBackend: keyboard_id=67699721
04-17 12:16 DEBUG  WindowsBackend: keyboard_layout=us
04-17 12:16 DEBUG  WindowsBackend: keyboard_variant=
04-17 12:16 DEBUG  CommonBackend: locale=en_US.UTF-8
04-17 12:16 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
04-17 12:16 DEBUG  CommonBackend: Searching ISOs on USB devices
04-17 12:16 DEBUG  CommonBackend: Searching for local CDs
04-17 12:16 DEBUG  Distro:   checking whether C:\Users\Acer\AppData\Local\Temp\pylF115.tmp is a valid Ubuntu CD
04-17 12:16 DEBUG  Distro:     does not contain C:\Users\Acer\AppData\Local\Temp\pylF115.tmp\casper\filesystem.squashfs
04-17 12:16 DEBUG  Distro:   checking whether C:\Users\Acer\AppData\Local\Temp\pylF115.tmp is a valid Ubuntu CD
04-17 12:16 DEBUG  Distro:     does not contain C:\Users\Acer\AppData\Local\Temp\pylF115.tmp\casper\filesystem.squashfs
04-17 12:16 DEBUG  Distro:   checking whether C:\Users\Acer\AppData\Local\Temp\pylF115.tmp is a valid Kubuntu CD
04-17 12:16 DEBUG  Distro:     does not contain C:\Users\Acer\AppData\Local\Temp\pylF115.tmp\casper\filesystem.squashfs
04-17 12:16 DEBUG  Distro:   checking whether C:\Users\Acer\AppData\Local\Temp\pylF115.tmp is a valid Kubuntu CD
04-17 12:16 DEBUG  Distro:     does not contain C:\Users\Acer\AppData\Local\Temp\pylF115.tmp\casper\filesystem.squashfs
04-17 12:16 DEBUG  Distro:   checking whether C:\Users\Acer\AppData\Local\Temp\pylF115.tmp is a valid Xubuntu CD
04-17 12:16 DEBUG  Distro:     does not contain C:\Users\Acer\AppData\Local\Temp\pylF115.tmp\casper\filesystem.squashfs
04-17 12:16 DEBUG  Distro:   checking whether C:\Users\Acer\AppData\Local\Temp\pylF115.tmp is a valid Xubuntu CD
04-17 12:16 DEBUG  Distro:     does not contain C:\Users\Acer\AppData\Local\Temp\pylF115.tmp\casper\filesystem.squashfs
04-17 12:16 DEBUG  Distro:   checking whether C:\Users\Acer\AppData\Local\Temp\pylF115.tmp is a valid Mythbuntu CD
04-17 12:16 DEBUG  Distro:     does not contain C:\Users\Acer\AppData\Local\Temp\pylF115.tmp\casper\filesystem.squashfs
04-17 12:16 DEBUG  Distro:   checking whether C:\Users\Acer\AppData\Local\Temp\pylF115.tmp is a valid Mythbuntu CD
04-17 12:16 DEBUG  Distro:     does not contain C:\Users\Acer\AppData\Local\Temp\pylF115.tmp\casper\filesystem.squashfs
04-17 12:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-17 12:16 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release Candidate amd64 (20090414.2)
04-17 12:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release Candidate', 'version': '9.04', 'build': '20090414.2', 'codename': 'Jaunty Jackalope', 'arch': 'amd64'}
04-17 12:16 INFO   Distro: Found a valid CD for Ubuntu: D:\
04-17 12:16 INFO   root: Running the uninstaller...
04-17 12:16 DEBUG  CommonBackend: This is the previous uninstaller running
04-17 12:16 DEBUG  WindowsFrontend: __init__...
04-17 12:16 DEBUG  WindowsFrontend: on_init...
04-17 12:16 INFO   root: Received settings
04-17 12:16 DEBUG  TaskList: # Running tasklist...
04-17 12:16 DEBUG  TaskList: ## Running Backup ISO...
04-17 12:16 DEBUG  TaskList: ## Finished Backup ISO
04-17 12:16 DEBUG  TaskList: ## Running Remove bootloader entry...
04-17 12:16 DEBUG  WindowsBackend: undo_bootini C:
04-17 12:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 124891.828125 mb free )
04-17 12:16 DEBUG  WindowsBackend: Removing bcd entry {0d17f0b0-1b2b-11de-8655-0016d3e72123}
04-17 12:16 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {0d17f0b0-1b2b-11de-8655-0016d3e72123} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 491, in undo_bootloader
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 668, in undo_bcd
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 60, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {0d17f0b0-1b2b-11de-8655-0016d3e72123} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-17 12:16 DEBUG  TaskList: # Cancelling tasklist
04-17 12:16 DEBUG  TaskList: # Finished tasklist
04-17 12:16 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {0d17f0b0-1b2b-11de-8655-0016d3e72123} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 51, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 106, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 158, in run_uninstaller
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 123, in run_tasks
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {0d17f0b0-1b2b-11de-8655-0016d3e72123} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
04-17 12:16 DEBUG  WindowsFrontend: frontend on_quit...
04-17 12:16 INFO   root: sys.exit

---

### Post by cariboo on 2009-04-17
You could just upgrade to the RC. :) I would suggest you delete your 9.04 beta installation. then install the Release Candidate.

Jim

---

### Post by coover on 2009-04-17
The problem is that the installation is within a Windows Vista Installation and not on a separate part of the hard drive. In order to upgrade to RC from Beta, an uninstall is necessary.

---

### Post by coover on 2009-04-17
The problem has been solved. 

After my first failed attempt to uninstall 9.04 Beta, I found I no longer had dual boot capibilities. Even though Ubuntu, itself, failed to completely uninstall, I could not get into the original installation. So I did a search of my hard drive for "Ubuntu" and found a folder with less than 2 MBs of files. I deleted it and again attempted to install the new 9.04 RC. It worked and I am back with Ubuntu.

---

### Post by arafatc on 2009-06-04
> **coover said:**
> The problem has been solved. 

After my first failed attempt to uninstall 9.04 Beta, I found I no longer had dual boot capibilities. Even though Ubuntu, itself, failed to completely uninstall, I could not get into the original installation. So I did a search of my hard drive for "Ubuntu" and found a folder with less than 2 MBs of files. I deleted it and again attempted to install the new 9.04 RC. It worked and I am back with Ubuntu.

I have windows vista installed and i installed ubuntu at second partition (that is D:/). I want to reinstall ubuntu by removing it so i did uninstall first and it didn't work same as above problem. then I deleted ubuntu folder and i can install ubuntu using wubi setup but the only problem is still no dual boot appears at system boot. Any suggestions ?

---

### Post by sathpra on 2010-11-01
Buddy!

I had the same problem. Try this first and then uninstall Ubuntu.


From command prompt (Run as admin)

C:\>Diskpart

C:\Diskpart> List volume

C:\Diskpart> Select volume 1 (Considering this is 100 MB system partition)

c:\Diskpart> Online volume

C:\Diskpart> exit

---

### Post by Iowan on 2010-11-01
Thread closed - according to the note I got on my Jaunty Laptop, 9.04 is past EOL.

---

