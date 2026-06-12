---
title: "Install programs to a different location"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Fabled One on 2009-10-11
I have vista and ubuntu dual-booting on my computer. Each OS is on their own small partition and there is a large partition that I intended to use as a shared area to save files and install programs.

When installing programs on vista, I can simply change the install path to a subdirectory on the large shared partition.

But how do I do that on Ubuntu? I  have been installing programs with synaptic and, as I understand things, all programs get installed to /usr/bin. 

Is there any way to NOT install programs to /usr/bin (install somewhere else)?
Or, is there a way to change the location of /usr/bin (place it in the shared partition)?

---

### Post by yeats on 2009-10-11
> When installing programs on vista, I can simply change the install path to a subdirectory on the large shared partition.

But how do I do that on Ubuntu? I have been installing programs with synaptic and, as I understand things, all programs get installed to /usr/bin.

Is there any way to NOT install programs to /usr/bin (install somewhere else)?
Or, is there a way to change the location of /usr/bin (place it in the shared partition)? 

When installing through synaptic, it's going install to the standard directories.  I imagine changing this is somehow possible, but I would think that it's not **advisable**.  Any particular advantage to doing things this way (having the programs use a different install directory)?

---

### Post by Fabled One on 2009-10-11
> **chrissharp123 said:**
>   Any particular advantage to doing things this way (having the programs use a different install directory)?

Well, the reason I want to do it that way is because I intsalled each of my OS's on small partitions (leaving room for system updates and such). If I keep installing programs on the Ubuntu OS partition, it will fill up fast.

Also, if I needed to do a fresh Ubuntu install, all my programs would be unafected (no need to download and re-install)

---

### Post by yeats on 2009-10-11
> Also, if I needed to do a fresh Ubuntu install, all my programs would be unafected (no need to download and re-install)

Having a separate /home directory for preserving files (and many settings) is a great way to preserve these through re-installs, but trying to preserve installed programs sounds like trouble to me.  You may get some different opinions, but I wouldn't expect this to work the way you're expecting... :-)

---

### Post by mcduck on 2009-10-11
> **Fabled One said:**
> I have vista and ubuntu dual-booting on my computer. Each OS is on their own small partition and there is a large partition that I intended to use as a shared area to save files and install programs.

When installing programs on vista, I can simply change the install path to a subdirectory on the large shared partition.

But how do I do that on Ubuntu? I  have been installing programs with synaptic and, as I understand things, all programs get installed to /usr/bin. 

Is there any way to NOT install programs to /usr/bin (install somewhere else)?
Or, is there a way to change the location of /usr/bin (place it in the shared partition)?

Actually programs are not installed to any single location. All files are put into different places based on the file's purpose, so the executable files for programs go to /usr/bin, icons and pixmpas into /usr/share/icons and /usr/share/pixmaps, documentation to /usr/share/doc, system-wide configuration files to /etc and so on..

Since these locations are pretty much a standard there's no easy way to force programs to install into a single location as they usually do in Windows. The system looks for certain files in certain places, and there's no such thing as Windows registry that could be used to define locatiosn of all files belonging to a program.

..not that forcing programs to install into single directory would really even make any sense in most cases. If you thought about using the *same* partition for both Windows and Linux programs it wouldn't work anyway. Windows doesn't have any support for Linux filesystems, while Linux needs certain filesystem features to actually handle the programs. (For example executable files are handled by marking the file as executable, which is a filesystem feature, not by file name extensions like in Windows. Also most Linux programs are pretty strict about ownership and permissions of the program's files, and Windows filesystems are not able to handle those as they are used in Linux/Unix systems.

edit: There's no easy way to avoid having to reinstall programs after reinstaling the OS, but at least avoiding having to download the programs again is easy. Apt-get caches all installed packages in /var/cache/apt/archives, so all you have to do is backup the files form there, and after reinstalling the OS put the files in some directory and run "sudo dpkg -i *.deb" in that directory to install all of them at once.

All your personal settings are stored in your home directory so simply backing up your home (or placing it on a separate partition) will always keep your settings.

---

### Post by philinux on 2009-10-11
+1 mcduck. Linux is not windows. Check this out for the file system details.

[http://library.gnome.org/users/user-guide/stable/nautilus-directories-file-systems.html.en](http://library.gnome.org/users/user-guide/stable/nautilus-directories-file-systems.html.en)

---

### Post by Fabled One on 2009-10-11
> **chrissharp123 said:**
> Having a separate /home directory for preserving files (and many settings) is a great way to preserve these through re-installs, but trying to preserve installed programs sounds like trouble to me.  You may get some different opinions, but I wouldn't expect this to work the way you're expecting... :-)

Would preserving my /home maintain my compiz settings, for example? So all the window effects and keyboard shortcuts would work after a reinstall?

---

### Post by Fabled One on 2009-10-11
Cool, 

I never intended on using win apps in ubunutu or ubuntu apps in windows, I just didn't want to assume how much space I needed for either OS. That's why I thought 1 huge shared partition would work.

But I guess I can't get around the fact that, ubuntu doesn't play nice with ntfs. Oh well.

I'll maybe do a fresh Ubuntu install when 9.10 comes out, and increase the partition size..


Thanks for all the help guys.

---

### Post by mcduck on 2009-10-11
> **Fabled One said:**
> Would preserving my /home maintain my compiz settings, for example? So all the window effects and keyboard shortcuts would work after a reinstall?

Yes, all your personal settings (as in any setting you can change without having to use "sudo" and give your password) will be stored in your personal configuration files, located inside your home directory.

---

### Post by Fabled One on 2009-10-11
Nice! Thanks again!

---

### Post by penguintutor on 2009-10-11
This is perfectly valid based on standard unix / Linux methodology. Typically /usr/local or /opt is used for programs installed outside of the main operating system install. These would normally be installed on a separate partition.

This doesn't however work so well using distro repositories (e.g. Synaptic / apt) to install the applications as the directories are already included in the package and typically point at /usr.

To install outside of the standard /usr location then you'll need to forgo the convenience (and the tweeks / compatibility testing) of Ubuntu packages and install the applications manually. 

If you are lucky then there may be a binary package with an install script that can do this already or it may be as simple as untarring the binary file into the appropriate directory. You cannot normally use .deb packages.

If not then you will need to compile the programs yourself specifying the install path during the compilation (either by editing the Makefile, or by giving the appropriate command parameters when installing). This is normally explained in the INSTALL file contained within the source code.

---

### Post by Bölvaður on 2009-10-11
> **Fabled One said:**
> 
But I guess I can't get around the fact that, ubuntu doesn't play nice with ntfs


Actually it's more like ntfs isn't feature rich enough to handle permissions of files, which is essential to programs in linux. It is really not a good filesystem compared to modern filesystems.


Also the config files are hidden in your /home

just open nautilus under /home/you  and press ctrl+h and you'll see many hidden folders appear. Those directories hold config files for your currently installed applications and other stuff that you own (but cannot store anywhere else because you dont have right to it)

---

### Post by RegsaGC on 2010-06-05
Hmm... *** far as I know it should be possible to save a program somewhere else, however I am looking around these forums myself to find out exactly how. As far as I know the only thing the icon does is to tell where to find the program using pipes. I think you just have to change those pipes. :-k

---

### Post by 3rdalbum on 2010-06-05
> **RegsaGC said:**
> Hmm... *** far as I know it should be possible to save a program somewhere else, however I am looking around these forums myself to find out exactly how. As far as I know the only thing the icon does is to tell where to find the program using pipes. I think you just have to change those pipes. :-k

No you   can't   change the   location   at   all.   The   package   says   where  it   needs   to   go,   full-stop.

Also with Ubuntu  you  can   still   have your  home  on  the  same  partition  and   it   will  still  be   preserved  adter  a  reibstall.

---

