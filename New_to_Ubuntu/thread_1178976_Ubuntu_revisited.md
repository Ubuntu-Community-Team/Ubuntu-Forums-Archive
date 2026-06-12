---
title: "Ubuntu revisited"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by brett@gogetgeek on 2009-06-05
Hello,

I'm trying to give Ubuntu a shot again and have installed it in a virtual machine. Right off the bat, it has been difficult setting up my Yahoo email, installing vmware tools so that I can cut and paste, and my cursor just jumps all over the place unlike my other virtual machines (I have to use CTL+ALT or CTL+G and wait before I can switch in and out).

Don't get me wrong, I think the interface and design of Ubuntu is very cool, but I still find this very challenging to learn. Unlike Windows or Mac where you can just start using the OS right away, the learning curve of Ubuntu is much higher. 

On that note, can anyone recommend free tutorials or videos, in person user groups, mentor programs, or anything where I don't have to spend money on training or read manuals and waste tons of time and frustration trying to learn this? I am so pro open source, but this just seems really hard.

Thanks for your suggestions,
Brett

---

### Post by nothingspecial on 2009-06-05
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[https://help.ubuntu.com/9.04/index.html](https://help.ubuntu.com/9.04/index.html)
[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

Of course the  best place to find out anything about ubuntu is [[COLOR="Red"]this website[/COLOR]]("http://www.google.co.uk/")

Also I notice from you`re using 6.06. A more up to date version might work better. 9.04 is the current release. Learning Ubuntu/linux is no more difficult than any other os. It`s unlearning windows that is hard.

---

### Post by prvteprts on 2009-06-05
Well, first of all, don't think of any part in learning something- in this case Ubuntu- as a waste of time, because it isn't.

Also, unlike Mac and Windows (which were probably installed natively when you used them), Ubuntu was installed using virtualization. You might be having problems because of this install method. I use Ubuntu everyday, and I can assure you the cursor doesn't jump randomly over the screen.

Right off the bat, it seems to me you are making things harder for yourself. Since you are quite new to Ubuntu, as I am, I would suggest the following:

1) Install Ubuntu on an older computer natively (as the sole OS or dual-boot), if you have one at your disposal
2) If you are using Windows, use WUBI to install
3) Do not install Ubuntu, just use the LiveCD instead to familiarize yourself with the interface

As for learning more about Ubuntu as a beginner, check out the sticky threads in this Absolute Beginner section.

---

### Post by markharding557 on 2009-06-05
hello and welcome back
first off i recomend installing direct as a duel boot,this removes your vmware problems which are actually nothing to do with ubuntu.
your best point of reference in order is:
1/this forum
2/search engine
3/ubuntu documentation[http://www.ubuntu.com/support]("http://www.ubuntu.com/support")

also if you have problems you need help with post a separate thread for each in the correct section,you will get a better response that way.

---

### Post by Tibuda on 2009-06-05
> **brett@gogetgeek said:**
> Unlike Windows or Mac where you can just start using the OS right away, the learning curve of Ubuntu is much higher.
No, you can't. In Windows you have to spend hours finding the drivers in the Internet, and installing them. You don't realise this because Windows was already installed when you bought your computer. You don't have this problem in Mac because both the hardware and the software are from Apple.

---

### Post by tiyowan on 2009-06-05
Hi there,

It seems to be me that some of the problems that you have described (i.e. cutting and pasting) are related to setting up VMware. Personally, I think the most hassle-free way for anyone to try Ubuntu is to boot from the LiveCD and spend some time getting to know the system.

Cheers.

---

### Post by decoherence on 2009-06-05
> **brett@gogetgeek said:**
> Hello,

I'm trying to give Ubuntu a shot again and have installed it in a virtual machine. Right off the bat, it has been difficult setting up my Yahoo email, installing vmware tools so that I can cut and paste, and my cursor just jumps all over the place unlike my other virtual machines (I have to use CTL+ALT or CTL+G and wait before I can switch in and out).



It sounds like things are broken on your system. What kind of trouble are you having setting up Yahoo email? How does vmware tools not work? The cursor issue is likely related to not having vmware tools.

In my experience takes way longer to set up a Windows system than an Ubuntu system. You have to hunt down drivers and god help you if you have a white-box computer and aren't sure of the components. Quite often you need to install a 3rd party tool to get useful information about hardware. That's fun when ethernet doesn't even work. And don't even get me started on the updating process...

If you want to start using the OS right away, get a computer with Ubuntu pre-installed, just like for Windows or Mac.

---

### Post by brett@gogetgeek on 2009-06-05
Thank you for the responses, especially from those that provided some resources. But due to the amount of response, I believe that this forum will provide a lot of help. 

First of all, I downloaded Ubuntu from ubuntu.com, so I believe I'm on the latest release. I clicked on Systems | About Ubuntu and this is in the resulting page: [INDENT]*Thank you for your interest in Ubuntu 9.04*- the Jaunty Jackalope - released in April 2009.

[/INDENT]Secondly, I was able to set up Yahoo! mail, just that my point was that I couldn't find an explanation of the settings in Evolution on the Internet and I had to rely on trial and error with the different settings. For example, I didn't know what the difference was between Plain, Login, and Password.

The cursor issue is related to VMware. It doesn't really jump around, it has to do with when I move my cursor to the outside edge and me having to use a keystroke to get in and out of the virtual machine. Anyway, the solution is to install VMware tools and this is part of the instructions that I don't understand:[INDENT]INSTALLING/UPGRADING

  To install/upgrade VMware Tools for Linux, 
  run the program "vmware-install.pl" from a command prompt, either in text 
  mode or from a terminal inside an X session. You must have super user 
  privileges (i.e. be logged as root) to run it.

     ./vmware-install.pl

[/INDENT]I'm sure you are all tired of hearing Windows users complain about Linux, but I don't understand the above. In Windows you just click the setup.exe (usually) and it installs. Also, even in Vista, I have rarely needed to search for drivers and if I need an updated one, Windows Update usually downloads and installs it automatically or I can easily find it via Google.

Back to the installation: the vmware-install.pl file is inside a folder on the Desktop called vmware-tools-distrib. I know how to open a terminal window, but I'm not sure if it's like a command prompt in Windows where I have to change directory first (cd): what is the script to change directories? Also, am I supposed to do something with "sudo"? 

Thanks for you help. I'm really determined to get the hang of this due to your encouragement.

---

### Post by carml on 2009-06-05
Yes the terminal is like the Windows prompt of command,so open the terminal and simply type```
yourname@yourmachinename:&#65279;~$ cd /theExactNameOfThe/DirectoryOnYourDesktop 
```,then insert the commands to run the script in order to install the tutilitis of Vmware.
I use Virtualbox and I had to follow a similar procedure.:)

---

### Post by doas777 on 2009-06-05
> **brett@gogetgeek said:**
> Thank you for the responses, especially from those that provided some resources. But due to the amount of response, I believe that this forum will provide a lot of help. 

First of all, I downloaded Ubuntu from ubuntu.com, so I believe I'm on the latest release. I clicked on Systems | About Ubuntu and this is in the resulting page:[INDENT]*Thank you for your interest in Ubuntu 9.04*- the Jaunty Jackalope - released in April 2009.

[/INDENT]Secondly, I was able to set up Yahoo! mail, just that my point was that I couldn't find an explanation of the settings in Evolution on the Internet and I had to rely on trial and error with the different settings. For example, I didn't know what the difference was between Plain, Login, and Password.

The cursor issue is related to VMware. It doesn't really jump around, it has to do with when I move my cursor to the outside edge and me having to use a keystroke to get in and out of the virtual machine. Anyway, the solution is to install VMware tools and this is part of the instructions that I don't understand:[INDENT]INSTALLING/UPGRADING

  To install/upgrade VMware Tools for Linux, 
  run the program "vmware-install.pl" from a command prompt, either in text 
  mode or from a terminal inside an X session. You must have super user 
  privileges (i.e. be logged as root) to run it.

     ./vmware-install.pl

[/INDENT]I'm sure you are all tired of hearing Windows users complain about Linux, but I don't understand the above. In Windows you just click the setup.exe (usually) and it installs. Also, even in Vista, I have rarely needed to search for drivers and if I need an updated one, Windows Update usually downloads and installs it automatically or I can easily find it via Google.

Back to the installation: the vmware-install.pl file is inside a folder on the Desktop called vmware-tools-distrib. I know how to open a terminal window, but I'm not sure if it's like a command prompt in Windows where I have to change directory first (cd): what is the script to change directories? Also, am I supposed to do something with "sudo"? 

Thanks for you help. I'm really determined to get the hang of this due to your encouragement.

well, in terms of sudo, you'll want to learn about it almost immediately (but it isnt; hard, just indespensibe).

Ubuntu does not have a single "Admin" or "root" account. all users run as normal users. adminstrators have the ability however to request that a command runs with root privledges.

sudo is the command you use to say "hey, I want to run this as an Admin!". all you do is put it in front of the command you want to run at the command line.

so if you are in the directory that contains your install.pl, you would want to put in the command :
```
sudo ./vmware-install.pl
```

now sudo was made to work with command line apps. and can malfunction if you run a gui application with it (ie: 'sudo gedit /filename'). in that case you want to use 'gksu'
for instance, If I wanted to open a file window that has root privledges, i would open a terminal or hit Alt + F2 to open the "Run Tasks" bar, and enter:
```

gksu nautilus

```

check out this page on sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

have fun and good ubuntuing,

---

### Post by brett@gogetgeek on 2009-06-05
I  was able to get into the directory and tried this:

[INDENT][I]sudo apt-get install vmware-install.pl
sudo apt-get install .vmware-install.pl

[/I][/INDENT]but the response was this: 

[INDENT]*E: *Coundn't find package vmware-install.pl
[/INDENT]

---

### Post by Tibuda on 2009-06-05
> **brett@gogetgeek said:**
> Back to the installation: the vmware-install.pl file is inside a folder on the Desktop called vmware-tools-distrib. I know how to open a terminal window, but I'm not sure if it's like a command prompt in Windows where I have to change directory first (cd): what is the script to change directories? Also, am I supposed to do something with "sudo"? 
Yes, you are right, you have to change the working dir first and then run the script with sudo:
```
cd Desktop/vmware-tools-distrib
sudo ./vmware-install.pl
```
sudo is the command to run a script with root privileges.


Please remember that this has nothing to do with Ubuntu. This is how VMWare is distributing its software.

---

### Post by Tibuda on 2009-06-05
> **brett@gogetgeek said:**
> I  was able to get into the directory and tried this:

[INDENT][I]sudo apt-get install vmware-install.pl
sudo apt-get install .vmware-install.pl

[/I][/INDENT]but the response was this: 

[INDENT]*E: *Coundn't find package vmware-install.pl
[/INDENT]

apt-get does not install software from files, but from the Ubuntu online software repositories. It will download it for you and install it. apt-get is the command-line tool, but you should check the synaptic package manager in system > admin. See this for more about installing software in ubuntu: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by brett@gogetgeek on 2009-06-05
sudo ./vmware-install.pl worked, but now I have this issue (how to uninstall):
[INDENT]The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmci
vmxnet
vmblock
vmmemctl

I.e. - 'rm /lib/modules/2.6.28-11-generic/misc/<ModuleName>.{o,ko}'

Execution aborted.

[/INDENT]

---

### Post by decoherence on 2009-06-05
> **brett@gogetgeek said:**
> sudo ./vmware-install.pl worked, but now I have this issue (how to uninstall):
[INDENT]The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmci
vmxnet
vmblock
vmmemctl

I.e. - 'rm /lib/modules/2.6.28-11-generic/misc/<ModuleName>.{o,ko}'

Execution aborted.

[/INDENT]

It's asking you to run these commands in the terminal

```
rm /lib/modules/2.6.28-11-generic/misc/vmci.{o,ko}
rm /lib/modules/2.6.28-11-generic/misc/vmxnet.{o,ko}
rm /lib/modules/2.6.28-11-generic/misc/vmblock.{o,ko}
rm /lib/modules/2.6.28-11-generic/misc/vmmemctl.{o,ko}

```

you will probably need to preface each command with a 'sudo' -- make sure there aren't any typos!! (use the tab key to automatically fill in parts of the path)

---

### Post by brett@gogetgeek on 2009-06-05
Thanks decoherence, that worked beautifully. And I had a chuckle when I reinstalled the vmware-tools.plc and the terminal replied with something like "Somebody already uninstalled it."

And it was cool how I just followed the prompts (questions) and they suggested the answers or directories ([yes]) in brackets.

And I got a "thank you" when I was done installing...:o.

Also, after a quick Google search I was able to export my contacts from Outlook 2007 in Vista and import into Evolution!!!

Now, I think I am getting the hang of the terminal and ubuntu running blind right away, but I downloaded the ubuntu pocket guide and will go through that at some point. I am certainly hooked this time and maybe by this time next year, I'll be mostly in Ubuntu and only using programs (like QuickBooks) in Windows when I have to. Thanks everyone for you help.

I found this link, which is very helpful if someone else is interested in full instructions on installing VMware Tools:
[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

---

### Post by nothingspecial on 2009-06-05
If you want to get the most out of Ubuntu I suggest installing it as part of a dual boot system.

If you need help doing this come back here.

It is a reversible operation.

If you decide to go it alone - back up all your important stuff. Mistakes can be made.

---

