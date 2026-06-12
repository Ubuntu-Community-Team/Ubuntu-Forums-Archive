---
title: "Can't open Winetricks"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by etsah57 on 2010-12-03
[SIZE=2]I am new to Ubuntu. I have made the decision to leave Windows, but 2 programs keep me logging back into Windows XP, they are Graboid and e-sword.[/SIZE]
 

 [SIZE=2]Graboid gave me the following instructions but I am having trouble and any advice would be greatly appreciated[/SIZE]
 [SIZE=2][I]GRABOID ON LINUX:
These steps were all done using Ubuntu 10.04 Lucid Lynx, but they will be compatible with any Ubuntu version 9.x or later. 

The fist thing you want to do is gather the necessary tools. 

To do this click on System-Administration-Synaptic Packet Manager 

Once the packet manager loads up enter "wine" into the quick search box and scroll down the list until you find Wine 1.2 and a program called WineTricks mark both of these packages for installation by clicking the box beside them and click "apply" at the top. 

This will install Wine, which is a windows compatibility layer needed for Graboid to run its DLL's. Winetricks is a neat little program which makes it easy to download needed items from the linux repositories specifically designed to work with Wine. 

Once the programs are installed you should see a new section under your applications bar that says Wine. Don't worry about editing the config settings or playing around inside your new C: drive because it's about to get deleted in the next step. 

Open up your terminal under applications-accessories-terminal. Type in rm -rf .wine this will delete your Wine folder along with some of the extras that come with the program. This is necessary, because without doing this you will run into a bunch of errors when you try to install .NET Framework. Next, type sh winetricks into your terminal. This will re-create your Wine directory with only the bare essentials needed to run wine, it will also bring up a dialog similar to your package manager. Scroll down the list and select "dotnet20", and click ok. [/I][/SIZE] 
 

 In the terminal I type: rm -rf .wine
 Then sh winetricks
 But I get the error message: sh Can't open winetricks
 

 colin@ububtu:~$ rm -rf .wine
 colin@ububtu:~$ sh winetricks
 sh Can't open winetricks
 

 I have gone back to the Synaptic Package Manager and reinstalled wine 1.2 and Winetricks a few times but still I cannot open Winetricks in the terminal.  
 

 What do I do? In plain English please. I am using Ubuntu 10.04 LTS

---

### Post by Verbeck on 2010-12-03
try just *winetricks* without the *sh*

---

### Post by etsah57 on 2010-12-03
It worked! thank you!
I have no idea what the sh means and so I didn't think of not using it
:p

---

### Post by gkforcare on 2010-12-04
Hi,

sh is a shell (just like bash that is standard) that allows one to give commands (either interactively or via a script-file) and it is often used to start a script (like winetricks). But in this case you can just start winetricks without the 'sh' as it's already made executable in Lucid and place in your path. (see echo $PATH for all directories that are in your path that will be searched through to find winetricks)

wkr,
Gkforcare

PS. For those who are curious as to which path was ultimately used to start winetricks use:
```
which winetricks
```
In my case on Lucid this yields:
```
/usr/bin/winetricks
```

---

