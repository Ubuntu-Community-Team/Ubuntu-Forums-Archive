---
title: "No Root File System Defined"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by Valas34 on 2011-08-02
I'm not sure if this is the right place for this but I am an absolute beginner so....

I wanted to try out Ubuntu. I downloaded wubi so I could use it inside windows.
I have Windows 7 64 bit. I started Wubi and got the error "No disk in drive...", I looked around and read in multiple places that this wasn't an issue and I could keep pressing continue. I did so and got to the Wubi options page.

I set my username and such and hit install. It was fine from there. I restarted when it was done and choose Ubuntu from the boot menu and let it finish installing. It loaded up Ubuntu and then I got the error "No Root File System is Defined - Please correct this from the partitioning menu.".

And I have no idea what to do. I have looked just about everywhere I could think of and the only things I found were to set partitions for Ubuntu. But I thought that wubi didn't need partitions to use Ubuntu. Any help is appreciated.

---

### Post by Rubi1200 on 2011-08-02
Hi and welcome to the forums :-)

You need to check first in the Windows Disk Management utility and make sure you do not have dynamic drives. If you do, proceeding with an install of Ubuntu whether with Wubi or normal is not advisable.

If the drives are not dynamic, look in the temp folder for the log file and post it here please so we can take a closer look.

Information about where to find the log file can be found here:
Windows side installation logs are in your user temp folder (%temp%) 
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Valas34 on 2011-08-02
Thank you for helping Rubi,
Sorry if it is a little long or if it is not the right thing.
```

[B]07-31 15:15 INFO   root: === wubi 11.04 rev211 ===
07-31 15:15 DEBUG  root: Logfile is c:\users\aaron\appdata\local\temp\wubi-11.04-rev211.log
07-31 15:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Aaron\\Downloads\\wubi.exe"']
07-31 15:15 DEBUG  CommonBackend: data_dir=C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\data
07-31 15:15 DEBUG  WindowsBackend: 7z=C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\bin\7z.exe
07-31 15:15 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
07-31 15:15 DEBUG  CommonBackend: Fetching basic info...
07-31 15:15 DEBUG  CommonBackend: original_exe=C:\Users\Aaron\Downloads\wubi.exe
07-31 15:15 DEBUG  CommonBackend: platform=win32
07-31 15:15 DEBUG  CommonBackend: osname=nt
07-31 15:15 DEBUG  CommonBackend: language=en_US
07-31 15:15 DEBUG  CommonBackend: encoding=cp1252
07-31 15:15 DEBUG  WindowsBackend: arch=amd64
07-31 15:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\data\isolist.ini
07-31 15:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-31 15:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-31 15:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-31 15:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-31 15:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-31 15:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-31 15:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-31 15:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-31 15:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-31 15:15 DEBUG  WindowsBackend: Fetching host info...
07-31 15:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-31 15:15 DEBUG  WindowsBackend: windows version=vista
07-31 15:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
07-31 15:15 DEBUG  WindowsBackend: windows_sp=None
07-31 15:15 DEBUG  WindowsBackend: windows_build=7601
07-31 15:15 DEBUG  WindowsBackend: gmt=-5
07-31 15:15 DEBUG  WindowsBackend: country=US
07-31 15:15 DEBUG  WindowsBackend: timezone=America/New_York
07-31 15:15 DEBUG  WindowsBackend: windows_username=Aaron
07-31 15:15 DEBUG  WindowsBackend: user_full_name=Aaron
07-31 15:15 DEBUG  WindowsBackend: user_directory=C:\Users\Aaron
07-31 15:15 DEBUG  WindowsBackend: windows_language_code=1033
07-31 15:15 DEBUG  WindowsBackend: windows_language=English
07-31 15:15 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 945 Processor
07-31 15:15 DEBUG  WindowsBackend: bootloader=vista
07-31 15:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 660367.484375 mb free ntfs)
07-31 15:15 DEBUG  WindowsBackend: drive=Drive(C: hd 660367.484375 mb free ntfs)
07-31 15:15 DEBUG  WindowsBackend: drive=Drive(D: hd 46.3125 mb free ntfs)
07-31 15:15 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-31 15:15 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
07-31 15:15 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
07-31 15:15 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
07-31 15:15 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
07-31 15:15 DEBUG  WindowsBackend: drive=Drive(L: removable 1940.1484375 mb free fat32)
07-31 15:15 DEBUG  WindowsBackend: uninstaller_path=None
07-31 15:15 DEBUG  WindowsBackend: previous_target_dir=None
07-31 15:15 DEBUG  WindowsBackend: previous_distro_name=None
07-31 15:15 DEBUG  WindowsBackend: keyboard_id=67699721
07-31 15:15 DEBUG  WindowsBackend: keyboard_layout=us
07-31 15:15 DEBUG  WindowsBackend: keyboard_variant=
07-31 15:15 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-31 15:15 DEBUG  CommonBackend: locale=en_US.UTF-8
07-31 15:15 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
07-31 15:15 DEBUG  CommonBackend: Searching ISOs on USB devices
07-31 15:15 DEBUG  CommonBackend: Searching for local CDs
07-31 15:15 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp is a valid Ubuntu Netbook CD
07-31 15:15 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-31 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-31 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
07-31 15:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
07-31 15:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
07-31 15:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook CD
07-31 15:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Netbook CD
07-31 15:15 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
07-31 15:15 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
07-31 15:15 INFO   root: Running the installer...
07-31 15:15 DEBUG  WindowsFrontend: __init__...
07-31 15:15 DEBUG  WindowsFrontend: on_init...
07-31 15:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\translations, languages=['en_US', 'en']
07-31 15:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\translations, languages=['en_US', 'en']
07-31 15:15 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=aaron
07-31 15:15 INFO   root: Received settings
07-31 15:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\translations, languages=['en_US', 'en']
07-31 15:15 DEBUG  TaskList: # Running tasklist...
07-31 15:15 DEBUG  TaskList: ## Running select_target_dir...
07-31 15:15 INFO   WindowsBackend: Installing into C:\ubuntu
07-31 15:15 DEBUG  TaskList: ## Finished select_target_dir
07-31 15:15 DEBUG  TaskList: ## Running create_dir_structure...
07-31 15:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
07-31 15:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
07-31 15:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
07-31 15:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
07-31 15:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
07-31 15:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
07-31 15:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
07-31 15:15 DEBUG  TaskList: ## Finished create_dir_structure
07-31 15:15 DEBUG  TaskList: ## Running uncompress_target_dir...
07-31 15:15 DEBUG  TaskList: ## Finished uncompress_target_dir
07-31 15:15 DEBUG  TaskList: ## Running create_uninstaller...
07-31 15:15 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Aaron\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
07-31 15:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
07-31 15:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
07-31 15:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-31 15:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
07-31 15:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
07-31 15:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-31 15:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-31 15:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-31 15:15 DEBUG  TaskList: ## Finished create_uninstaller
07-31 15:15 DEBUG  TaskList: ## Running copy_installation_files...
07-31 15:15 DEBUG  WindowsBackend: Copying C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
07-31 15:15 DEBUG  WindowsBackend: Copying C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\winboot -> C:\ubuntu\winboot
07-31 15:15 DEBUG  WindowsBackend: Copying C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
07-31 15:15 DEBUG  TaskList: ## Finished copy_installation_files
07-31 15:15 DEBUG  TaskList: ## Running get_iso...
07-31 15:15 DEBUG  CommonBackend: Searching for local CD
07-31 15:15 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
07-31 15:15 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
07-31 15:15 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
07-31 15:15 DEBUG  CommonBackend: Searching for local ISO
07-31 15:15 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-31 15:15 DEBUG  TaskList: New task get_metalink
07-31 15:15 DEBUG  TaskList: ### Running get_metalink...
07-31 15:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
07-31 15:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
07-31 15:15 DEBUG  downloader: download finished (read 28363 bytes)
07-31 15:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
07-31 15:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
07-31 15:15 DEBUG  downloader: download finished (read 874 bytes)
07-31 15:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
07-31 15:15 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
07-31 15:15 DEBUG  downloader: download finished (read 198 bytes)
07-31 15:15 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-31 15:15 INFO   saplog: Checking block bindings..
07-31 15:15 INFO   saplog: Key verified successfully.
07-31 15:15 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

07-31 15:15 DEBUG  TaskList: ### Finished get_metalink
07-31 15:15 DEBUG  TaskList: New task download
07-31 15:15 DEBUG  TaskList: ### Running download...
07-31 15:15 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-31 15:55 DEBUG  TaskList: ### Finished download
07-31 15:55 DEBUG  TaskList: New task check_iso
07-31 15:55 DEBUG  TaskList: ### Running check_iso...
07-31 15:55 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-31 15:55 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-31 15:55 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-31 15:55 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
07-31 15:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
07-31 15:55 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-31 15:55 DEBUG  TaskList: New task get_file_md5
07-31 15:55 DEBUG  TaskList: #### Running get_file_md5...
07-31 15:55 DEBUG  TaskList: #### Finished get_file_md5
07-31 15:55 DEBUG  TaskList: ### Finished check_iso
07-31 15:55 DEBUG  TaskList: ## Finished get_iso
07-31 15:55 DEBUG  TaskList: ## Running extract_kernel...
07-31 15:55 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-31 15:55 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-31 15:55 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-31 15:55 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
07-31 15:55 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-31 15:55 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
07-31 15:55 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 45a7bee6779b8cd75634a70fd7a566dd == 45a7bee6779b8cd75634a70fd7a566dd
07-31 15:55 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
07-31 15:55 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4aa66b9da42e1a3f667ab0c8009cc801 == 4aa66b9da42e1a3f667ab0c8009cc801
07-31 15:55 DEBUG  TaskList: ## Finished extract_kernel
07-31 15:55 DEBUG  TaskList: ## Running choose_disk_sizes...
07-31 15:55 DEBUG  WindowsBackend: total size=10000
  root=9744
  swap=256
  home=0
  usr=0
07-31 15:55 DEBUG  TaskList: ## Finished choose_disk_sizes
07-31 15:55 DEBUG  TaskList: ## Running create_preseed...
07-31 15:55 DEBUG  TaskList: ## Finished create_preseed
07-31 15:55 DEBUG  TaskList: ## Running modify_bootloader...
07-31 15:55 DEBUG  TaskList: New task modify_bcd
07-31 15:55 DEBUG  TaskList: ### Running modify_bcd...
07-31 15:55 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 660367.484375 mb free ntfs)
07-31 15:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {0c1fa138-1412-11df-81ee-18a905c0da84}
07-31 15:55 DEBUG  TaskList: ### Finished modify_bcd
07-31 15:55 DEBUG  TaskList: New task modify_bcd
07-31 15:55 DEBUG  TaskList: ### Running modify_bcd...
07-31 15:55 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 46.3125 mb free ntfs)
07-31 15:55 DEBUG  WindowsBackend: BCD has already been modified
07-31 15:55 DEBUG  TaskList: ### Finished modify_bcd
07-31 15:55 DEBUG  TaskList: New task modify_bcd
07-31 15:55 DEBUG  TaskList: ### Running modify_bcd...
07-31 15:55 DEBUG  WindowsBackend: modify_bcd Drive(H: removable 0.0 mb free )
07-31 15:55 DEBUG  WindowsBackend: BCD has already been modified
07-31 15:55 DEBUG  TaskList: ### Finished modify_bcd
07-31 15:55 DEBUG  TaskList: New task modify_bcd
07-31 15:55 DEBUG  TaskList: ### Running modify_bcd...
07-31 15:55 DEBUG  WindowsBackend: modify_bcd Drive(I: removable 0.0 mb free )
07-31 15:55 DEBUG  WindowsBackend: BCD has already been modified
07-31 15:55 DEBUG  TaskList: ### Finished modify_bcd
07-31 15:55 DEBUG  TaskList: New task modify_bcd
07-31 15:55 DEBUG  TaskList: ### Running modify_bcd...
07-31 15:55 DEBUG  WindowsBackend: modify_bcd Drive(J: removable 0.0 mb free )
07-31 15:55 DEBUG  WindowsBackend: BCD has already been modified
07-31 15:55 DEBUG  TaskList: ### Finished modify_bcd
07-31 15:55 DEBUG  TaskList: New task modify_bcd
07-31 15:55 DEBUG  TaskList: ### Running modify_bcd...
07-31 15:55 DEBUG  WindowsBackend: modify_bcd Drive(K: removable 0.0 mb free )
07-31 15:55 DEBUG  WindowsBackend: BCD has already been modified
07-31 15:55 DEBUG  TaskList: ### Finished modify_bcd
07-31 15:55 DEBUG  TaskList: New task modify_bcd
07-31 15:55 DEBUG  TaskList: ### Running modify_bcd...
07-31 15:55 DEBUG  WindowsBackend: modify_bcd Drive(L: removable 1940.1484375 mb free fat32)
07-31 15:55 DEBUG  WindowsBackend: BCD has already been modified
07-31 15:55 DEBUG  TaskList: ### Finished modify_bcd
07-31 15:55 DEBUG  TaskList: ## Finished modify_bootloader
07-31 15:55 DEBUG  TaskList: ## Running modify_grub_configuration...
07-31 15:55 DEBUG  TaskList: ## Finished modify_grub_configuration
07-31 15:55 DEBUG  TaskList: ## Running create_virtual_disks...
07-31 15:55 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 9744MB
07-31 15:55 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
07-31 15:55 DEBUG  TaskList: ## Finished create_virtual_disks
07-31 15:55 DEBUG  TaskList: ## Running uncompress_files...
07-31 15:55 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
07-31 15:55 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
07-31 15:55 DEBUG  TaskList: ## Finished uncompress_files
07-31 15:55 DEBUG  TaskList: ## Running eject_cd...
07-31 15:55 DEBUG  TaskList: ## Finished eject_cd
07-31 15:55 DEBUG  TaskList: # Finished tasklist
07-31 15:55 INFO   root: Almost finished installing
07-31 15:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pylFB62.tmp\translations, languages=['en_US', 'en']
07-31 15:56 INFO   root: Finished installation
07-31 15:56 DEBUG  root: application.quit
07-31 15:56 DEBUG  WindowsFrontend: frontend.quit
07-31 15:56 DEBUG  WindowsFrontend: frontend.on_quit
07-31 15:56 DEBUG  root: application.on_quit
07-31 15:56 INFO   root: sys.exit
08-02 13:21 INFO   root: === wubi 11.04 rev211 ===
08-02 13:21 DEBUG  root: Logfile is c:\users\aaron\appdata\local\temp\wubi-11.04-rev211.log
08-02 13:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
08-02 13:21 DEBUG  CommonBackend: data_dir=C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\data
08-02 13:21 DEBUG  WindowsBackend: 7z=C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\bin\7z.exe
08-02 13:21 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-02 13:21 DEBUG  CommonBackend: Fetching basic info...
08-02 13:21 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
08-02 13:21 DEBUG  CommonBackend: platform=win32
08-02 13:21 DEBUG  CommonBackend: osname=nt
08-02 13:21 DEBUG  CommonBackend: language=en_US
08-02 13:21 DEBUG  CommonBackend: encoding=cp1252
08-02 13:21 DEBUG  WindowsBackend: arch=amd64
08-02 13:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\data\isolist.ini
08-02 13:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-02 13:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-02 13:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-02 13:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-02 13:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-02 13:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-02 13:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-02 13:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-02 13:21 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-02 13:21 DEBUG  WindowsBackend: Fetching host info...
08-02 13:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-02 13:21 DEBUG  WindowsBackend: windows version=vista
08-02 13:21 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-02 13:21 DEBUG  WindowsBackend: windows_sp=None
08-02 13:21 DEBUG  WindowsBackend: windows_build=7601
08-02 13:21 DEBUG  WindowsBackend: gmt=-5
08-02 13:21 DEBUG  WindowsBackend: country=US
08-02 13:21 DEBUG  WindowsBackend: timezone=America/New_York
08-02 13:21 DEBUG  WindowsBackend: windows_username=Aaron
08-02 13:21 DEBUG  WindowsBackend: user_full_name=Aaron
08-02 13:21 DEBUG  WindowsBackend: user_directory=C:\Users\Aaron
08-02 13:21 DEBUG  WindowsBackend: windows_language_code=1033
08-02 13:21 DEBUG  WindowsBackend: windows_language=English
08-02 13:21 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 945 Processor
08-02 13:21 DEBUG  WindowsBackend: bootloader=vista
08-02 13:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 647488.398438 mb free ntfs)
08-02 13:21 DEBUG  WindowsBackend: drive=Drive(C: hd 647488.398438 mb free ntfs)
08-02 13:21 DEBUG  WindowsBackend: drive=Drive(D: hd 46.3125 mb free ntfs)
08-02 13:21 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-02 13:21 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
08-02 13:21 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
08-02 13:21 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
08-02 13:21 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
08-02 13:21 DEBUG  WindowsBackend: drive=Drive(L: removable 1940.1484375 mb free fat32)
08-02 13:21 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
08-02 13:21 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
08-02 13:21 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
08-02 13:21 DEBUG  WindowsBackend: keyboard_id=67699721
08-02 13:21 DEBUG  WindowsBackend: keyboard_layout=us
08-02 13:21 DEBUG  WindowsBackend: keyboard_variant=
08-02 13:21 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-02 13:21 DEBUG  CommonBackend: locale=en_US.UTF-8
08-02 13:21 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
08-02 13:21 DEBUG  CommonBackend: Searching ISOs on USB devices
08-02 13:21 DEBUG  CommonBackend: Searching for local CDs
08-02 13:21 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp is a valid Ubuntu Netbook CD
08-02 13:21 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-02 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-02 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
08-02 13:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
08-02 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
08-02 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook CD
08-02 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether L:\ is a valid Ubuntu Netbook CD
08-02 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether L:\ is a valid Kubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether L:\ is a valid Xubuntu CD
08-02 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-02 13:21 DEBUG  Distro:   checking whether L:\ is a valid Mythbuntu CD
08-02 13:21 DEBUG  Distro:     does not contain L:\casper\filesystem.squashfs
08-02 13:21 INFO   root: Running the uninstaller...
08-02 13:21 INFO   CommonBackend: This is the uninstaller running
08-02 13:21 DEBUG  WindowsFrontend: __init__...
08-02 13:21 DEBUG  WindowsFrontend: on_init...
08-02 13:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\translations, languages=['en_US', 'en']
08-02 13:21 INFO   root: Received settings
08-02 13:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\translations, languages=['en_US', 'en']
08-02 13:21 DEBUG  TaskList: # Running tasklist...
08-02 13:21 DEBUG  TaskList: ## Running Backup ISO...
08-02 13:21 DEBUG  TaskList: ## Finished Backup ISO
08-02 13:21 DEBUG  TaskList: ## Running Remove bootloader entry...
08-02 13:21 DEBUG  WindowsBackend: Removing bcd entry {0c1fa138-1412-11df-81ee-18a905c0da84}
08-02 13:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
08-02 13:21 DEBUG  WindowsBackend: undo_bootini C:
08-02 13:21 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 647488.398438 mb free ntfs)
08-02 13:21 DEBUG  WindowsBackend: undo_bootini D:
08-02 13:21 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 46.3125 mb free ntfs)
08-02 13:21 DEBUG  WindowsBackend: undo_bootini H:
08-02 13:21 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
08-02 13:21 DEBUG  WindowsBackend: undo_bootini I:
08-02 13:21 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
08-02 13:21 DEBUG  WindowsBackend: undo_bootini J:
08-02 13:21 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
08-02 13:21 DEBUG  WindowsBackend: undo_bootini K:
08-02 13:21 DEBUG  WindowsBackend: undo_configsys Drive(K: removable 0.0 mb free )
08-02 13:21 DEBUG  WindowsBackend: undo_bootini L:
08-02 13:21 DEBUG  WindowsBackend: undo_configsys Drive(L: removable 1940.1484375 mb free fat32)
08-02 13:21 DEBUG  TaskList: ## Finished Remove bootloader entry
08-02 13:21 DEBUG  TaskList: ## Running Remove target dir...
08-02 13:21 DEBUG  CommonBackend: Deleting C:\ubuntu
08-02 13:21 DEBUG  TaskList: ## Finished Remove target dir
08-02 13:21 DEBUG  TaskList: ## Running Remove registry key...
08-02 13:21 DEBUG  TaskList: ## Finished Remove registry key
08-02 13:21 DEBUG  TaskList: # Finished tasklist
08-02 13:21 INFO   root: Almost finished uninstalling
08-02 13:21 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pylE907.tmp\translations, languages=['en_US', 'en']
08-02 13:21 INFO   root: Finished uninstallation
08-02 13:21 DEBUG  root: application.quit
08-02 13:21 DEBUG  WindowsFrontend: frontend.quit
08-02 13:21 DEBUG  WindowsFrontend: frontend.on_quit
08-02 13:21 DEBUG  root: application.on_quit
08-02 13:21 INFO   root: sys.exit
08-02 13:25 INFO   root: === wubi 11.04 rev211 ===
08-02 13:25 DEBUG  root: Logfile is c:\users\aaron\appdata\local\temp\wubi-11.04-rev211.log
08-02 13:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Aaron\\Downloads\\wubi.exe"']
08-02 13:25 DEBUG  CommonBackend: data_dir=C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\data
08-02 13:25 DEBUG  WindowsBackend: 7z=C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\bin\7z.exe
08-02 13:25 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-02 13:25 DEBUG  CommonBackend: Fetching basic info...
08-02 13:25 DEBUG  CommonBackend: original_exe=C:\Users\Aaron\Downloads\wubi.exe
08-02 13:25 DEBUG  CommonBackend: platform=win32
08-02 13:25 DEBUG  CommonBackend: osname=nt
08-02 13:25 DEBUG  CommonBackend: language=en_US
08-02 13:25 DEBUG  CommonBackend: encoding=cp1252
08-02 13:25 DEBUG  WindowsBackend: arch=amd64
08-02 13:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\data\isolist.ini
08-02 13:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-02 13:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-02 13:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-02 13:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-02 13:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-02 13:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-02 13:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-02 13:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-02 13:25 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-02 13:25 DEBUG  WindowsBackend: Fetching host info...
08-02 13:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-02 13:25 DEBUG  WindowsBackend: windows version=xp
08-02 13:25 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-02 13:25 DEBUG  WindowsBackend: windows_sp=Service Pack 3
08-02 13:25 DEBUG  WindowsBackend: windows_build=2600
08-02 13:25 DEBUG  WindowsBackend: gmt=-5
08-02 13:25 DEBUG  WindowsBackend: country=US
08-02 13:25 DEBUG  WindowsBackend: timezone=America/New_York
08-02 13:25 DEBUG  WindowsBackend: windows_username=Aaron
08-02 13:25 DEBUG  WindowsBackend: user_full_name=Aaron
08-02 13:25 DEBUG  WindowsBackend: user_directory=C:\Users\Aaron
08-02 13:25 DEBUG  WindowsBackend: windows_language_code=1033
08-02 13:25 DEBUG  WindowsBackend: windows_language=English
08-02 13:25 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 945 Processor
08-02 13:25 DEBUG  WindowsBackend: bootloader=xp
08-02 13:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 658141.507813 mb free ntfs)
08-02 13:25 DEBUG  WindowsBackend: drive=Drive(C: hd 658141.507813 mb free ntfs)
08-02 13:25 DEBUG  WindowsBackend: drive=Drive(D: hd 46.3125 mb free ntfs)
08-02 13:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-02 13:26 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
08-02 13:26 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
08-02 13:26 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
08-02 13:26 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
08-02 13:26 DEBUG  WindowsBackend: drive=Drive(L: removable 1898.4921875 mb free fat32)
08-02 13:26 DEBUG  WindowsBackend: uninstaller_path=None
08-02 13:26 DEBUG  WindowsBackend: previous_target_dir=None
08-02 13:26 DEBUG  WindowsBackend: previous_distro_name=None
08-02 13:26 DEBUG  WindowsBackend: keyboard_id=67699721
08-02 13:26 DEBUG  WindowsBackend: keyboard_layout=us
08-02 13:26 DEBUG  WindowsBackend: keyboard_variant=
08-02 13:26 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-02 13:26 DEBUG  CommonBackend: locale=en_US.UTF-8
08-02 13:26 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
08-02 13:26 DEBUG  CommonBackend: Searching ISOs on USB devices
08-02 13:26 DEBUG  CommonBackend: Searching for local CDs
08-02 13:26 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp is a valid Ubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp is a valid Ubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp is a valid Ubuntu Netbook CD
08-02 13:26 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp is a valid Kubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp is a valid Kubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp is a valid Xubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp is a valid Xubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp is a valid Mythbuntu CD
08-02 13:26 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp is a valid Mythbuntu CD
08-02 13:26 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl276E.tmp\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-02 13:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 13:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 13:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-02 13:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-02 13:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-02 13:26 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-02 13:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
08-02 13:26 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:26 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-02 13:27 INFO   root: === wubi 11.04 rev211 ===
08-02 13:27 DEBUG  root: Logfile is c:\users\aaron\appdata\local\temp\wubi-11.04-rev211.log
08-02 13:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Aaron\\Downloads\\wubi.exe"']
08-02 13:27 DEBUG  CommonBackend: data_dir=C:\Users\Aaron\AppData\Local\Temp\pyl1DEC.tmp\data
08-02 13:27 DEBUG  WindowsBackend: 7z=C:\Users\Aaron\AppData\Local\Temp\pyl1DEC.tmp\bin\7z.exe
08-02 13:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-02 13:27 DEBUG  CommonBackend: Fetching basic info...
08-02 13:27 DEBUG  CommonBackend: original_exe=C:\Users\Aaron\Downloads\wubi.exe
08-02 13:27 DEBUG  CommonBackend: platform=win32
08-02 13:27 DEBUG  CommonBackend: osname=nt
08-02 13:27 DEBUG  CommonBackend: language=en_US
08-02 13:27 DEBUG  CommonBackend: encoding=cp1252
08-02 13:27 DEBUG  WindowsBackend: arch=amd64
08-02 13:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Aaron\AppData\Local\Temp\pyl1DEC.tmp\data\isolist.ini
08-02 13:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-02 13:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-02 13:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-02 13:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-02 13:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-02 13:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-02 13:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-02 13:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-02 13:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-02 13:27 DEBUG  WindowsBackend: Fetching host info...
08-02 13:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-02 13:27 DEBUG  WindowsBackend: windows version=xp
08-02 13:27 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-02 13:27 DEBUG  WindowsBackend: windows_sp=Service Pack 3
08-02 13:27 DEBUG  WindowsBackend: windows_build=2600
08-02 13:27 DEBUG  WindowsBackend: gmt=-5
08-02 13:27 DEBUG  WindowsBackend: country=US
08-02 13:27 DEBUG  WindowsBackend: timezone=America/New_York
08-02 13:27 DEBUG  WindowsBackend: windows_username=Aaron
08-02 13:27 DEBUG  WindowsBackend: user_full_name=Aaron
08-02 13:27 DEBUG  WindowsBackend: user_directory=C:\Users\Aaron
08-02 13:27 DEBUG  WindowsBackend: windows_language_code=1033
08-02 13:27 DEBUG  WindowsBackend: windows_language=English
08-02 13:27 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 945 Processor
08-02 13:27 DEBUG  WindowsBackend: bootloader=xp
08-02 13:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 658013.25 mb free ntfs)
08-02 13:27 DEBUG  WindowsBackend: drive=Drive(C: hd 658013.25 mb free ntfs)
08-02 13:27 DEBUG  WindowsBackend: drive=Drive(D: hd 46.3125 mb free ntfs)
08-02 13:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-02 13:27 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
08-02 13:27 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
08-02 13:32 INFO   root: === wubi 11.04 rev211 ===
08-02 13:32 DEBUG  root: Logfile is c:\users\aaron\appdata\local\temp\wubi-11.04-rev211.log
08-02 13:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Aaron\\Documents\\Ubuntu\\wubi.exe"']
08-02 13:32 DEBUG  CommonBackend: data_dir=C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\data
08-02 13:32 DEBUG  WindowsBackend: 7z=C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\bin\7z.exe
08-02 13:32 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-02 13:32 DEBUG  CommonBackend: Fetching basic info...
08-02 13:32 DEBUG  CommonBackend: original_exe=C:\Users\Aaron\Documents\Ubuntu\wubi.exe
08-02 13:32 DEBUG  CommonBackend: platform=win32
08-02 13:32 DEBUG  CommonBackend: osname=nt
08-02 13:32 DEBUG  CommonBackend: language=en_US
08-02 13:32 DEBUG  CommonBackend: encoding=cp1252
08-02 13:32 DEBUG  WindowsBackend: arch=amd64
08-02 13:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\data\isolist.ini
08-02 13:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-02 13:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-02 13:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-02 13:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-02 13:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-02 13:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-02 13:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-02 13:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-02 13:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-02 13:32 DEBUG  WindowsBackend: Fetching host info...
08-02 13:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-02 13:32 DEBUG  WindowsBackend: windows version=vista
08-02 13:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-02 13:32 DEBUG  WindowsBackend: windows_sp=None
08-02 13:32 DEBUG  WindowsBackend: windows_build=7601
08-02 13:32 DEBUG  WindowsBackend: gmt=-5
08-02 13:32 DEBUG  WindowsBackend: country=US
08-02 13:32 DEBUG  WindowsBackend: timezone=America/New_York
08-02 13:32 DEBUG  WindowsBackend: windows_username=Aaron
08-02 13:32 DEBUG  WindowsBackend: user_full_name=Aaron
08-02 13:32 DEBUG  WindowsBackend: user_directory=C:\Users\Aaron
08-02 13:32 DEBUG  WindowsBackend: windows_language_code=1033
08-02 13:32 DEBUG  WindowsBackend: windows_language=English
08-02 13:32 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 945 Processor
08-02 13:32 DEBUG  WindowsBackend: bootloader=vista
08-02 13:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 658009.300781 mb free ntfs)
08-02 13:32 DEBUG  WindowsBackend: drive=Drive(C: hd 658009.300781 mb free ntfs)
08-02 13:32 DEBUG  WindowsBackend: drive=Drive(D: hd 46.3125 mb free ntfs)
08-02 13:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-02 13:32 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
08-02 13:32 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
08-02 13:32 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
08-02 13:32 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
08-02 13:32 DEBUG  WindowsBackend: uninstaller_path=None
08-02 13:32 DEBUG  WindowsBackend: previous_target_dir=None
08-02 13:32 DEBUG  WindowsBackend: previous_distro_name=None
08-02 13:32 DEBUG  WindowsBackend: keyboard_id=67699721
08-02 13:32 DEBUG  WindowsBackend: keyboard_layout=us
08-02 13:32 DEBUG  WindowsBackend: keyboard_variant=
08-02 13:32 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-02 13:32 DEBUG  CommonBackend: locale=en_US.UTF-8
08-02 13:32 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
08-02 13:32 DEBUG  CommonBackend: Searching ISOs on USB devices
08-02 13:32 DEBUG  CommonBackend: Searching for local CDs
08-02 13:32 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp is a valid Ubuntu Netbook CD
08-02 13:32 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-02 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-02 13:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
08-02 13:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
08-02 13:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
08-02 13:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook CD
08-02 13:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
08-02 13:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:32 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
08-02 13:32 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:32 INFO   root: Running the installer...
08-02 13:32 DEBUG  WindowsFrontend: __init__...
08-02 13:32 DEBUG  WindowsFrontend: on_init...
08-02 13:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\translations, languages=['en_US', 'en']
08-02 13:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pyl8611.tmp\translations, languages=['en_US', 'en']
08-02 13:33 DEBUG  WindowsFrontend: frontend.on_quit
08-02 13:33 DEBUG  root: application.on_quit
08-02 13:33 INFO   root: sys.exit
08-02 13:33 INFO   root: === wubi 11.04 rev211 ===
08-02 13:33 DEBUG  root: Logfile is c:\users\aaron\appdata\local\temp\wubi-11.04-rev211.log
08-02 13:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Aaron\\Documents\\Ubuntu\\wubi.exe"']
08-02 13:33 DEBUG  CommonBackend: data_dir=C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\data
08-02 13:33 DEBUG  WindowsBackend: 7z=C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\bin\7z.exe
08-02 13:33 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
08-02 13:33 DEBUG  CommonBackend: Fetching basic info...
08-02 13:33 DEBUG  CommonBackend: original_exe=C:\Users\Aaron\Documents\Ubuntu\wubi.exe
08-02 13:33 DEBUG  CommonBackend: platform=win32
08-02 13:33 DEBUG  CommonBackend: osname=nt
08-02 13:33 DEBUG  CommonBackend: language=en_US
08-02 13:33 DEBUG  CommonBackend: encoding=cp1252
08-02 13:33 DEBUG  WindowsBackend: arch=amd64
08-02 13:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\data\isolist.ini
08-02 13:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-02 13:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-02 13:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-02 13:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-02 13:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-02 13:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-02 13:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-02 13:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-02 13:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-02 13:33 DEBUG  WindowsBackend: Fetching host info...
08-02 13:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-02 13:33 DEBUG  WindowsBackend: windows version=vista
08-02 13:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
08-02 13:33 DEBUG  WindowsBackend: windows_sp=None
08-02 13:33 DEBUG  WindowsBackend: windows_build=7601
08-02 13:33 DEBUG  WindowsBackend: gmt=-5
08-02 13:33 DEBUG  WindowsBackend: country=US
08-02 13:33 DEBUG  WindowsBackend: timezone=America/New_York
08-02 13:33 DEBUG  WindowsBackend: windows_username=Aaron
08-02 13:33 DEBUG  WindowsBackend: user_full_name=Aaron
08-02 13:33 DEBUG  WindowsBackend: user_directory=C:\Users\Aaron
08-02 13:33 DEBUG  WindowsBackend: windows_language_code=1033
08-02 13:33 DEBUG  WindowsBackend: windows_language=English
08-02 13:33 DEBUG  WindowsBackend: processor_name=AMD Phenom(tm) II X4 945 Processor
08-02 13:33 DEBUG  WindowsBackend: bootloader=vista
08-02 13:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 658008.964844 mb free ntfs)
08-02 13:33 DEBUG  WindowsBackend: drive=Drive(C: hd 658008.964844 mb free ntfs)
08-02 13:33 DEBUG  WindowsBackend: drive=Drive(D: hd 46.3125 mb free ntfs)
08-02 13:33 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
08-02 13:33 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
08-02 13:33 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
08-02 13:33 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
08-02 13:33 DEBUG  WindowsBackend: drive=Drive(K: removable 0.0 mb free )
08-02 13:33 DEBUG  WindowsBackend: uninstaller_path=None
08-02 13:33 DEBUG  WindowsBackend: previous_target_dir=None
08-02 13:33 DEBUG  WindowsBackend: previous_distro_name=None
08-02 13:33 DEBUG  WindowsBackend: keyboard_id=67699721
08-02 13:33 DEBUG  WindowsBackend: keyboard_layout=us
08-02 13:33 DEBUG  WindowsBackend: keyboard_variant=
08-02 13:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-02 13:33 DEBUG  CommonBackend: locale=en_US.UTF-8
08-02 13:33 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
08-02 13:33 DEBUG  CommonBackend: Searching ISOs on USB devices
08-02 13:33 DEBUG  CommonBackend: Searching for local CDs
08-02 13:33 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp is a valid Ubuntu Netbook CD
08-02 13:33 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-02 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
08-02 13:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
08-02 13:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
08-02 13:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
08-02 13:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu Netbook CD
08-02 13:33 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether K:\ is a valid Kubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether K:\ is a valid Xubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether K:\ is a valid Mythbuntu CD
08-02 13:33 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:33 INFO   root: Running the installer...
08-02 13:33 DEBUG  WindowsFrontend: __init__...
08-02 13:33 DEBUG  WindowsFrontend: on_init...
08-02 13:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\translations, languages=['en_US', 'en']
08-02 13:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\translations, languages=['en_US', 'en']
08-02 13:33 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=11000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=aaron
08-02 13:33 INFO   root: Received settings
08-02 13:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\translations, languages=['en_US', 'en']
08-02 13:33 DEBUG  TaskList: # Running tasklist...
08-02 13:33 DEBUG  TaskList: ## Running select_target_dir...
08-02 13:33 INFO   WindowsBackend: Installing into C:\ubuntu
08-02 13:33 DEBUG  TaskList: ## Finished select_target_dir
08-02 13:33 DEBUG  TaskList: ## Running create_dir_structure...
08-02 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-02 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-02 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-02 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-02 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-02 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-02 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-02 13:33 DEBUG  TaskList: ## Finished create_dir_structure
08-02 13:33 DEBUG  TaskList: ## Running uncompress_target_dir...
08-02 13:33 DEBUG  TaskList: ## Finished uncompress_target_dir
08-02 13:33 DEBUG  TaskList: ## Running create_uninstaller...
08-02 13:33 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Aaron\Documents\Ubuntu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
08-02 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
08-02 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
08-02 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-02 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
08-02 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
08-02 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-02 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-02 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-02 13:33 DEBUG  TaskList: ## Finished create_uninstaller
08-02 13:33 DEBUG  TaskList: ## Running copy_installation_files...
08-02 13:33 DEBUG  WindowsBackend: Copying C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
08-02 13:33 DEBUG  WindowsBackend: Copying C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\winboot -> C:\ubuntu\winboot
08-02 13:33 DEBUG  WindowsBackend: Copying C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
08-02 13:33 DEBUG  TaskList: ## Finished copy_installation_files
08-02 13:33 DEBUG  TaskList: ## Running get_iso...
08-02 13:33 DEBUG  CommonBackend: Searching for local CD
08-02 13:33 DEBUG  Distro:   checking whether C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain C:\Users\Aaron\AppData\Local\Temp\pyl18AE.tmp\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
08-02 13:33 DEBUG  Distro:   checking whether K:\ is a valid Ubuntu CD
08-02 13:33 DEBUG  Distro:     does not contain K:\casper\filesystem.squashfs
08-02 13:33 DEBUG  CommonBackend: Searching for local ISO
08-02 13:33 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
08-02 13:33 DEBUG  TaskList: New task get_metalink
08-02 13:33 DEBUG  TaskList: ### Running get_metalink...
08-02 13:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
08-02 13:33 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
08-02 13:33 DEBUG  downloader: download finished (read 28363 bytes)
08-02 13:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
08-02 13:33 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
08-02 13:33 DEBUG  downloader: download finished (read 874 bytes)
08-02 13:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
08-02 13:33 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
08-02 13:33 DEBUG  downloader: download finished (read 198 bytes)
08-02 13:33 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
08-02 13:33 INFO   saplog: Checking block bindings..
08-02 13:33 INFO   saplog: Key verified successfully.
08-02 13:33 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

08-02 13:33 DEBUG  TaskList: ### Finished get_metalink
08-02 13:33 DEBUG  TaskList: New task download
08-02 13:33 DEBUG  TaskList: ### Running download...
08-02 13:33 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
08-02 13:43 INFO   WindowsFrontend: Operation cancelled
08-02 13:43 DEBUG  WindowsFrontend: frontend.quit
08-02 13:43 DEBUG  WindowsFrontend: frontend.on_quit
08-02 13:43 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
08-02 13:43 DEBUG  TaskList: # Cancelling tasklist
08-02 13:43 DEBUG  TaskList: ### Finished download
08-02 13:43 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
08-02 13:43 DEBUG  root: application.on_quit
08-02 13:43 DEBUG  root: Forceful exit
08-02 13:43 INFO   root: sys.exit
```


[/B]I have tried it a few times after uninstalling it but it is always the same error.

---

### Post by Elfy on 2011-08-02
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header.

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Valas34 on 2011-08-02
> **forestpiskie said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header.

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

I did not know that, thank you.

---

### Post by Elfy on 2011-08-02
I'd assumed not :) 

Makes a big difference. There's more of them [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by Valas34 on 2011-08-02
> **forestpiskie said:**
> I'd assumed not :) 

Makes a big difference. There's more of them [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)


I looked at it for awhile but I really couldn't figure out how to not make it so large :D.
Thank you again.

---

### Post by Valas34 on 2011-08-02
Is there nothing I can do then?

---

### Post by bcbc on 2011-08-02
This 'no root file system defined' usually indicates the presence of:
1. unsupported raid setup
2. mix of mbr and gpt partition tables (e.g. if drive used to be on a mac)
3. partition table corruption

There's no real way to know exactly what the problem is unless you create an Ubuntu CD or USB (instructions here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) Step 2, show me how) and then boot in 'live' mode (boot from CD or USB and select "Try it" without installing) and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

The instructions are in that link. Post the results back here and hopefully that will point out the issue.

---

