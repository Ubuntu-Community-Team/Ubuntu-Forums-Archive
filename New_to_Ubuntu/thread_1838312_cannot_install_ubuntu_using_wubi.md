---
title: "cannot install ubuntu using wubi"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by dbzsongoku123 on 2011-09-03
hi, 

a brief background:

i run a intel  2.27 GHz processor with 1 GB RAM with Windows XP SP2. i installed ubuntu using wubi, and then uninstalled it.

Now, when i try to install ubuntu again using wubi, i get an error saying that vmlinuz is corrupt.   Here is the log.  Please Help. Thanks in advance





09-03 20:10 INFO   root: === wubi 11.04 rev211 ===
09-03 20:10 DEBUG  root: Logfile is c:\docume~1\siddha~1\locals~1\temp\wubi-11.04-rev211.log
09-03 20:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Siddharth\\My Documents\\Downloads\\wubi.exe"']
09-03 20:10 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\data
09-03 20:10 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\bin\7z.exe
09-03 20:10 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
09-03 20:10 DEBUG  CommonBackend: Fetching basic info...
09-03 20:10 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Siddharth\My Documents\Downloads\wubi.exe
09-03 20:10 DEBUG  CommonBackend: platform=win32
09-03 20:10 DEBUG  CommonBackend: osname=nt
09-03 20:10 DEBUG  CommonBackend: language=en_US
09-03 20:10 DEBUG  CommonBackend: encoding=cp1252
09-03 20:10 DEBUG  WindowsBackend: arch=i386
09-03 20:10 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\data\isolist.ini
09-03 20:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-03 20:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-03 20:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-03 20:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-03 20:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-03 20:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-03 20:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-03 20:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-03 20:10 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-03 20:10 DEBUG  WindowsBackend: Fetching host info...
09-03 20:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-03 20:10 DEBUG  WindowsBackend: windows version=xp
09-03 20:10 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
09-03 20:10 DEBUG  WindowsBackend: windows_sp=Service Pack 2
09-03 20:10 DEBUG  WindowsBackend: windows_build=2600
09-03 20:10 DEBUG  WindowsBackend: gmt=5
09-03 20:10 DEBUG  WindowsBackend: country=US
09-03 20:10 DEBUG  WindowsBackend: timezone=America/New_York
09-03 20:10 DEBUG  WindowsBackend: windows_username=Siddharth
09-03 20:10 DEBUG  WindowsBackend: user_full_name=Siddharth
09-03 20:10 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Siddharth
09-03 20:10 DEBUG  WindowsBackend: windows_language_code=1033
09-03 20:10 DEBUG  WindowsBackend: windows_language=English
09-03 20:10 DEBUG  WindowsBackend: processor_name=              Intel(R) Pentium(R) 4 CPU 2.26GHz
09-03 20:10 DEBUG  WindowsBackend: bootloader=xp
09-03 20:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 6317.8515625 mb free ntfs)
09-03 20:10 DEBUG  WindowsBackend: drive=Drive(C: hd 6317.8515625 mb free ntfs)
09-03 20:10 DEBUG  WindowsBackend: drive=Drive(D: hd 385.453125 mb free ntfs)
09-03 20:10 DEBUG  WindowsBackend: drive=Drive(E: hd 217.33984375 mb free ntfs)
09-03 20:10 DEBUG  WindowsBackend: drive=Drive(F: hd 237.171875 mb free ntfs)
09-03 20:10 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
09-03 20:10 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free cdfs)
09-03 20:10 DEBUG  WindowsBackend: uninstaller_path=None
09-03 20:10 DEBUG  WindowsBackend: previous_target_dir=None
09-03 20:10 DEBUG  WindowsBackend: previous_distro_name=None
09-03 20:10 DEBUG  WindowsBackend: keyboard_id=67699721
09-03 20:10 DEBUG  WindowsBackend: keyboard_layout=us
09-03 20:10 DEBUG  WindowsBackend: keyboard_variant=
09-03 20:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-03 20:10 DEBUG  CommonBackend: locale=en_US.UTF-8
09-03 20:10 DEBUG  WindowsBackend: total_memory_mb=1015.484375
09-03 20:10 DEBUG  CommonBackend: Searching ISOs on USB devices
09-03 20:10 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-11.04-desktop-i386.iso
09-03 20:10 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-11.04-desktop-i386.iso
09-03 20:10 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
09-03 20:10 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
09-03 20:10 DEBUG  Distro: wrong arch: i386 != amd64
09-03 20:10 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-11.04-desktop-i386.iso
09-03 20:10 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-11.04-desktop-i386.iso
09-03 20:10 DEBUG  CommonBackend: Searching for local CDs
09-03 20:10 DEBUG  Distro:   checking whether C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp is a valid Ubuntu Netbook CD
09-03 20:10 DEBUG  Distro:     does not contain C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-03 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-03 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-03 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-03 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-03 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-03 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-03 20:10 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-03 20:10 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-03 20:10 INFO   root: Running the installer...
09-03 20:10 DEBUG  WindowsFrontend: __init__...
09-03 20:10 DEBUG  WindowsFrontend: on_init...
09-03 20:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
09-03 20:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
09-03 20:10 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=5000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=siddharth
09-03 20:10 INFO   root: Received settings
09-03 20:10 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\translations, languages=['en_US', 'en']
09-03 20:10 DEBUG  TaskList: # Running tasklist...
09-03 20:10 DEBUG  TaskList: ## Running select_target_dir...
09-03 20:10 INFO   WindowsBackend: Installing into C:\ubuntu
09-03 20:10 DEBUG  TaskList: ## Finished select_target_dir
09-03 20:10 DEBUG  TaskList: ## Running create_dir_structure...
09-03 20:10 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-03 20:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-03 20:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-03 20:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-03 20:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-03 20:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-03 20:10 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-03 20:10 DEBUG  TaskList: ## Finished create_dir_structure
09-03 20:10 DEBUG  TaskList: ## Running uncompress_target_dir...
09-03 20:10 DEBUG  TaskList: ## Finished uncompress_target_dir
09-03 20:10 DEBUG  TaskList: ## Running create_uninstaller...
09-03 20:10 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Siddharth\My Documents\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-03 20:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-03 20:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-03 20:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-03 20:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-03 20:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-03 20:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-03 20:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-03 20:10 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-03 20:10 DEBUG  TaskList: ## Finished create_uninstaller
09-03 20:10 DEBUG  TaskList: ## Running copy_installation_files...
09-03 20:10 DEBUG  WindowsBackend: Copying C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-03 20:10 DEBUG  WindowsBackend: Copying C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\winboot -> C:\ubuntu\winboot
09-03 20:10 DEBUG  WindowsBackend: Copying C:\DOCUME~1\SIDDHA~1\LOCALS~1\Temp\pyl1D.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-03 20:10 DEBUG  TaskList: ## Finished copy_installation_files
09-03 20:10 DEBUG  TaskList: ## Running get_iso...
09-03 20:10 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-11.04-desktop-i386.iso
09-03 20:10 DEBUG  TaskList: New task is_valid_iso
09-03 20:10 DEBUG  TaskList: ### Running is_valid_iso...
09-03 20:10 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-11.04-desktop-i386.iso
09-03 20:10 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-11.04-desktop-i386.iso
09-03 20:10 DEBUG  TaskList: ### Finished is_valid_iso
09-03 20:10 DEBUG  TaskList: New task check_iso
09-03 20:10 DEBUG  TaskList: ### Running check_iso...
09-03 20:10 DEBUG  CommonBackend: Checking E:\ubuntu-11.04-desktop-i386.iso
09-03 20:10 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-11.04-desktop-i386.iso
09-03 20:10 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-11.04-desktop-i386.iso
09-03 20:10 DEBUG  TaskList: New task get_metalink
09-03 20:10 DEBUG  TaskList: #### Running get_metalink...
09-03 20:10 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) > C:\ubuntu\install
09-03 20:10 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-03 20:10 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink) > C:\ubuntu\install
09-03 20:10 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-03 20:10 DEBUG  TaskList: #### Finished get_metalink
09-03 20:10 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for E:\ubuntu-11.04-desktop-i386.iso, ignoring
09-03 20:10 DEBUG  TaskList: ### Finished check_iso
09-03 20:10 DEBUG  TaskList: New task copy_file
09-03 20:10 DEBUG  CommonBackend: Copying E:\ubuntu-11.04-desktop-i386.iso > C:\ubuntu\install\installation.iso
09-03 20:10 DEBUG  TaskList: ### Running copy_file...
09-03 20:11 DEBUG  TaskList: ### Finished copy_file
09-03 20:11 DEBUG  TaskList: ## Finished get_iso
09-03 20:11 DEBUG  TaskList: ## Running extract_kernel...
09-03 20:11 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\installation.iso
09-03 20:11 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\installation.iso
09-03 20:12 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\installation.iso
09-03 20:12 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\installation.iso
09-03 20:12 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-03 20:12 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
09-03 20:12 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = cdf34c9d9ae13a985678744b4023c1f1 != db0104e80bc7e667344a14af3515de25
09-03 20:12 ERROR  TaskList: File C:\ubuntu\install\boot\vmlinuz is corrupted
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 526, in extract_kernel
Exception: File C:\ubuntu\install\boot\vmlinuz is corrupted
09-03 20:12 DEBUG  TaskList: # Cancelling tasklist
09-03 20:12 ERROR  root: File C:\ubuntu\install\boot\vmlinuz is corrupted
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 526, in extract_kernel
Exception: File C:\ubuntu\install\boot\vmlinuz is corrupted
09-03 20:12 DEBUG  TaskList: # Finished tasklist

---

### Post by bcbc on 2011-09-03
This is the ISO it's using for the install: E:\ubuntu-11.04-desktop-i386.iso

You're running wubi without internet access so it cannot check the md5sum, so it could be corrupted. If you did't intend to install with that ISO you need to remove it from E:\ or rename the .iso extension, because Wubi looks for and uses ISO's in the root of partitions before it will use the one in the current directory (e.g. where wubi.exe is run from).

You can also check the md5sum of the ISO yourself: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

