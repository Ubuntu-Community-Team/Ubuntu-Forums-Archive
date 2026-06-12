---
title: "Step-By-Step guide to manually installing Nvidia drivers."
date: 2009-06-03
forum: New to Ubuntu
---

### Post by Steelmourne on 2009-06-03
[SIZE=2]Edit bodhi.zazen: Although this is a nice guide, there is some confusion.

The nvidia drivers are in the Ubuntu Repositories and you should use this how to only if you have a specific need to install the nvidia drivers from the web site.

It is quite easy to install the nvidia drivers from the repositories see :

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

```
sudo apt-get install nvidia-glx-180 nvidia-settings
```If you install the nvidia drivers from the repositories they will be automatically updated. This is most important when installing an new updated kernel.

If you install from the nvidia site, using this how to, you will need to manually run the installer with every update (or write hooks to initrd) and X will fail with each kernel update until you re-install the driver.

/end edit

Here is a step-by-step guide to manually installing nvidia drivers. The newest drivers should always be used, both for better performance and fixing other issues that may seem unrelated. These are based on 32 bit drivers but 64-bit drivers are available. The instructions are the same, just note the name of the downloaded file (x86_64). I used ubuntu 9.04 with 180.60 drivers on a Geforce Go 7400 laptop card, but the steps should still apply to kubuntu and other variants with NVIDIA drivers:[/SIZE]
 [SIZE=2]
[/SIZE] 
 
[LIST=1]
[*][SIZE=2]Go to the nvidia driver website     [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).     Download the drivers to your Desktop. Write down the package name.[/SIZE]
[*][SIZE=2]Run this command in terminal:     &#8220;sudo apt-get install build essential check install&#8221;. No quotes.     Enter &#8220;y&#8221; when asked, then enter. This ensures that the drivers     can be compiled against your kernel.[/SIZE]
[*][SIZE=2]Go to System &#8211; Preferences &#8211;     Appearance and select the Visual Effects tab. Change the settings to     none. This will only have to be done once when manually installing     nvidia drivers for the first time.[/SIZE]
[*][SIZE=2]Go to System &#8211; Adminstration &#8211;     Hardware Drivers and click remove for any installed drivers. As with     Step 3, this only has to done once. The drivers can be re-enabled at     any time at your option. The manual installation will be smoother     with them disabled.[/SIZE]
[*][SIZE=2]Log out by clicking on your     name/fast user switcher on the far right and selecting the option to     log out.[/SIZE]
[*][SIZE=2]Press Ctrl+Alt+F1.[/SIZE]
[*][SIZE=2]Log into the virtual console as     you would normally with your username and password.      [/SIZE]
[*][SIZE=2]Type &#8220;sudo /etc/init.d/gdm     stop&#8221;, without the quotes.[/SIZE]
[*][SIZE=2]You'll see the gnome display     manager stopped with the message &#8220;OK&#8221;.[/SIZE]
[*][SIZE=2]Change to your Desktop folder with     &#8220;cd Desktop&#8221;, without the quotes. Watch for the capital D.[/SIZE]
[*][SIZE=2]Type &#8220;sudo sh     NVIDIA-Linux-xxxxxxxx&#8221;, replace the x's with the package name, and     no quotes. I used NVIDIA-Linux-x86-180.60-pkg1.run[/SIZE]
[*][SIZE=2]Accept the agreement to install     with the arrow keys.[/SIZE]
[*][SIZE=2]Select no when the installer asks     to go online.[/SIZE]
[*][SIZE=2]Select yes to recompile drivers     against the kernel.[/SIZE]
[*][SIZE=2]Wait a few minutes.[/SIZE]
[*][SIZE=2]Select yes to update the xorg     file.[/SIZE]
[*][SIZE=2]Back at the prompt, type &#8220;sudo     reboot&#8221;, no quotes.[/SIZE]
[*][SIZE=2]Log back in, the NVIDIA X Server     settings have moved your preferences menu. Re-enable desktop     effects.[/SIZE]
[*][SIZE=2]That's it. Just follow these steps     for any new drivers that NVIDIA releases, omitting steps 2,3, and 4.[/SIZE]
[/LIST]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Post any comments/suggestions.[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]Hope this helps![/SIZE]

---

### Post by M Star on 2009-06-04
I was looking for something like this I am going to try it and let you know if it works.
:KS

Do I need separate drivers for separate NVidia grphics card?

---

### Post by Steelmourne on 2009-06-04
You only need one set of drivers, so one package. How many video cards do you have?

---

### Post by MMD1990 on 2009-06-04
on the second step I get the output "E:couldn't find package build"
Any ideas?

---

### Post by M Star on 2009-06-04
> **Steelmourne said:**
> You only need one set of drivers, so one package. How many video cards do you have?
Really my friend has a broadband connection and he uses a NVidia 8600..... 
I don't have a fast enough internet to download driver for my NVidia 5200 fx so if one package  can support both Cards then my friend can download it for himself and I could use it for myself.

---

### Post by Bearly Able on 2009-06-04
Hi Steelmourne,

Thanks for the guide; I'll give it a go.  

Just one question.  I upgraded from Hardy, where I had no graphics problems, and then suffered repeated freezes, crashes and X server errors under Jaunty.  The only solution I found was to completely remove nvidia-glx-180 from my system.  However, I still have some other Nvidia packages installed.  Should I remove them, too, before downloading and trying the latest version?  Thanks.

---

### Post by kpkeerthi on 2009-06-04
Install nvidia with dkms module so you do not loose your 'X' in the event of a kernel upgrade.

See [http://ubuntuforums.org/showthread.php?t=1036788]("http://ubuntuforums.org/showthread.php?t=1036788")

---

### Post by Steelmourne on 2009-06-04
double check any commands typed into the terminal. the build essential packages are necessary. And yes, one set of drivers will work for any nvidia video cards as long as they are supported:

[http://www.nvidia.com/object/linux_display_ia32_180.60.html](http://www.nvidia.com/object/linux_display_ia32_180.60.html)

On the left is a link to the supported drivers. If your card is listed then the procedure should work.

---

### Post by M Star on 2009-06-04
> **Steelmourne said:**
> double check any commands typed into the terminal. the build essential packages are necessary. And yes, one set of drivers will work for any nvidia video cards as long as they are supported:

[http://www.nvidia.com/object/linux_display_ia32_180.60.html](http://www.nvidia.com/object/linux_display_ia32_180.60.html)

On the left is a link to the supported drivers. If your card is listed then the procedure should work.
thnx

---

### Post by skompier on 2009-06-04
Instead of remembering the driver name, in Terminal type sudo sh NV and then hit TAB. It will automatically fill in the rest of the name if that's the only file with that name in the folder. Pretty slick.

---

### Post by DnDer on 2009-06-04
I am getting "E: Couldn't find package build," as well. You said this should work with any *card*. My video is GeForce8300 and it's built into the motherboard. Does that change the rules?

The link provided says both versions of the 8300 are supported. I've double-checked my spelling, and that's correct. I downloaded the right file (NVIDIA-Linux-x86-180.60.pkg1.run) and it's sitting on my desktop...

What am I failing at?

---

### Post by Steelmourne on 2009-06-05
If you are getting build errors, fire up synaptic and search for build essential. It should have a filled in green box. You must have this package installed or installation will fail. Do the same for check install. Both have to be installed.

---

### Post by DnDer on 2009-06-05
I went through synaptec and could not find check install. I did find build essential, which I had to download and install.

I tried running the command you have in your first post. The following error appeared (corrected for line breaks):
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

Did I break something?

---

### Post by Steelmourne on 2009-06-05
Another package manager is running. Close down synaptic, add/remove programs, and terminal and try again.

---

### Post by DnDer on 2009-06-05
Still "couldn't find package build."

Where, specifically can I find and get check install? When I searched for it using synaptec, I did not find any matches. It's the only thing in your directions that I can't confirm if I have.

---

### Post by kpkeerthi on 2009-06-05
> **Steelmourne said:**
> 
[*][SIZE=2]Run this command in terminal: 	&#8220;sudo apt-get install build essential check install&#8221;. No quotes. 	Enter &#8220;y&#8221; when asked, then enter. This ensures that the drivers 	can be compiled against your kernel.[/SIZE]

The instructions are incorrect. I recommend [this method]("http://ubuntuforums.org/showpost.php?p=7398479&postcount=7") I posted earlier.

If you still want to continue with this method, change packages names as below:
```

sudo apt-get install build-essential checkinstall

```

---

### Post by jenkinbr on 2009-06-05
> **Steelmourne said:**
> 
[*][SIZE=2]Run this command in terminal: 	&#8220;sudo apt-get install build essential check install&#8221;. No quotes. 	Enter &#8220;y&#8221; when asked, then enter. This ensures that the drivers 	can be compiled against your kernel.[/SIZE]


should be ```
sudo apt-get install build-essential checkinstall
```

edit: bah, kpkeerthi beat me :)

---

### Post by Steelmourne on 2009-06-05
Yes, check install should be checkinstall. My mistake.

---

### Post by ozzyprv on 2009-06-05
This is what I keep getting:

[PHP]
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Jun  5 01:33:42 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 180.60.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).[/PHP]

---

### Post by kpkeerthi on 2009-06-05
sudo apt-get install linux-headers-generic

---

### Post by ozzyprv on 2009-06-05
kp...: whats is this suppose to do?
just checking, I have installed 9.04 32-bit server edition to be able to "see" the 4 Gb of RAM. I do not want to change that...

> **kpkeerthi said:**
> sudo apt-get install linux-headers-generic

---

### Post by jenkinbr on 2009-06-05
That just installs the header files for the linux kernel.  Header files are bits of source code that other source code files can call on.

you can safely install that package to your system without messing up your server install.

---

### Post by ozzyprv on 2009-06-05
This is what I get:

```
os@shaman:~$ sudo apt-get install linux-headers-generic
[sudo]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

After getting this I tried again with no success. Same error message.

O.

---

### Post by bodhi.zazen on 2009-06-05
Your guide is nice, but IMO you should include 2 pieces of additional information :

1. How to re-install the nvidia drivers with kernel upgrades (other wise the new users tend to get confused when they reboot and drop to a command line).

2. How to user the nvidia tool to configure monitors, especially helpful if people have multi monitors.

```
gksu nvidia-settings
```

But, in general, unless you have a clear need, probably best to use the nvidia drivers in the repos, especially for new users.

---

### Post by jenkinbr on 2009-06-05
> **bodhi.zazen said:**
> Your guide is nice, but IMO you should include 2 pieces of additional information :

1. How to re-install the nvidia drivers with kernel upgrades (other wise the new users tend to get confused when they reboot and drop to a command line).

2. How to user the nvidia tool to configure monitors, especially helpful if people have multi monitors.

```
gksu nvidia-settings
```

But, in general, unless you have a clear need, probably best to use the nvidia drivers in the repos, especially for new users.
+1

I prefer the repo versions because I've had a lot of problems with the nVidia binaries when it comes to kernel updates

---

### Post by DnDer on 2009-06-06
The first time I tried to use **sudo /etc/init.d/gdm stop**, the computer went to a list of checks in black and white text - I lost the GUI - and then froze (I think) when it told me it was checking for a battery (!?), at which point, I had to manually restart the computer.

I just ran the command again, and it told me "* Reloading Common Unix Printing System: cupsd" and, justified right on the screen was the text "* Reloading system log daemon..."

After several minutes, I have four new lines of text:
[random #.random #] ath5k phy0: noise floor calibration timeout (2457 MHz)

...I really screwed this up. Should have been much easier, right? >_<

NEW DEVELOPMENT:
After about 5-7 minutes of having those timeout notices on-screen, my monitor just went black. I'm not sure what to do, for fear of messing things up worse.

---

### Post by ozzyprv on 2009-06-07
> **kpkeerthi said:**
> sudo apt-get install linux-headers-generic

I finally got the driver installed.

The key point for me was making sure that linux-headers-2.6.28-11-server
was installed. I am running that kernel to get the 4GB RAM recognized.

The "generic" one did not work.

Thank you.

---

### Post by Boeruitafrika on 2009-06-07
Thanks mate. I am new to Linux and seem to keep messing up. I installed Ubuntu on my sons desktop and it worked like a charm. The Nvidia driver performs impressive for normal tinkering.
 
I have a Intel® Core™2 Duo Processor T9400 2.53 GHz , Level 2 cache 6 MB, 1066 MHz FSB with a NVIDIA GeForce 9600M GT with a WXVGA display laptop. I started off with open SUSE, then got bogged in the linux lingo and the nvidia driver was without a cursor. Great, try work a GUI without a cursor.
 
The I installed Debian 5.0 (i686). Were stable, sound worked well, ect. But in some sense very basic. So now I have Ubuntu, installed for the 3 time from scratch. And still no go. I downloaded the i386 version, so I assume it is the 32 bit version. How do I actually check if it is 32 bit or 64 bit?
 
I downloaded the NVIDIA-Linux-x86-185.18.14.pkg1.run version and the list say it is supported. I tried to follow the ubuntuguide.org for the Jaunty Jakalas. The command "sudo killall gdm" killed a lot of stuff, but did not get anything going.
 
Then I tried the boot option without a graphics interface and got to this [EMAIL="root@...-laptop$"]root@...-laptop$[/EMAIL] prompt. But the "dir" and the "cd" commands are not functional. I also uninstalled the xdriver package and of cause do not know how to reinstall it. So I jus reinstall it from scratch, formated and everything.
 
I tried the aptoncd and tried to install some of the Debian 5.0 package that seems nice. Ugh, that also got a bit messy and did nit help with installing the driver. I am currently not connected to the internet, IT limitation, so I use a memory stick instead.
 
I am also not able to switch users or log on as root. The root terminal from the menu also do not work. That was something that did work in Debian 5.0. It also asked during installation for a root password. In Ubuntu it just ask for the user password.
 
In the mean time many thanks for the instructions, I will give it a go.

---

### Post by bodhi.zazen on 2009-06-07
> **Boeruitafrika said:**
> Thanks mate. I am new to Linux and seem to keep messing up. I installed Ubuntu on my sons desktop and it worked like a charm. The Nvidia driver performs impressive for normal tinkering.
 
I have a Intel® Core™2 Duo Processor T9400 2.53 GHz , Level 2 cache 6 MB, 1066 MHz FSB with a NVIDIA GeForce 9600M GT with a WXVGA display laptop. I started off with open SUSE, then got bogged in the linux lingo and the nvidia driver was without a cursor. Great, try work a GUI without a cursor.
 
The I installed Debian 5.0 (i686). Were stable, sound worked well, ect. But in some sense very basic. So now I have Ubuntu, installed for the 3 time from scratch. And still no go. I downloaded the i386 version, so I assume it is the 32 bit version. How do I actually check if it is 32 bit or 64 bit?
 
I downloaded the NVIDIA-Linux-x86-185.18.14.pkg1.run version and the list say it is supported. I tried to follow the ubuntuguide.org for the Jaunty Jakalas. The command "sudo killall gdm" killed a lot of stuff, but did not get anything going.
 
Then I tried the boot option without a graphics interface and got to this root@...-laptop$ prompt. But the "dir" and the "cd" commands are not functional. I also uninstalled the xdriver package and of cause do not know how to reinstall it. So I jus reinstall it from scratch, formated and everything.
 
I tried the aptoncd and tried to install some of the Debian 5.0 package that seems nice. Ugh, that also got a bit messy and did nit help with installing the driver. I am currently not connected to the internet, IT limitation, so I use a memory stick instead.
 
I am also not able to switch users or log on as root. The root terminal from the menu also do not work. That was something that did work in Debian 5.0. It also asked during installation for a root password. In Ubuntu it just ask for the user password.
 
In the mean time many thanks for the instructions, I will give it a go.

Is there a reason you are not using the nvidia driver from the repositories ?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

```
sudo apt-get install nvidia-glx-180 nvidia-settings
```

If you are new to Linux and Ubuntu, and do not need the proprietary drivers, use the repos.

---

### Post by jenkinbr on 2009-06-07
> **bodhi.zazen said:**
> Is there a reason you are not using the nvidia driver from the repositories ?

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

```
sudo apt-get install nvidia-glx-180 nvidia-settings
```

If you are new to Linux and Ubuntu, and do not need the proprietary drivers, use the repos.
Correction: The drivers in the repos are proprietary as well, however, they have more support from the ubuntu community being that they are in the repos.

---

### Post by Boeruitafrika on 2009-06-08
To use the repositories you have to have a internet link? I can type on here and use a memory stick to get some files, but I do not have a direct connection. But when i get the opportunity to connect, I will give that a go :) Thanks.

---

### Post by bodhi.zazen on 2009-06-08
> **Boeruitafrika said:**
> To use the repositories you have to have a internet link? I can type on here and use a memory stick to get some files, but I do not have a direct connection. But when i get the opportunity to connect, I will give that a go :) Thanks.

You will need an internet link to install the drivers either way. If you download the driver form nvidia you still need build essential and the headers from the Ubuntu repositories.

---

### Post by Boeruitafrika on 2009-06-09
I do? What I have done was this:
 
[COLOR=blue]Ctrl+Alt+F1[/COLOR]
 
Then I got a text screen and logged in as myself. Then I did
 
[COLOR=blue]ls        [/COLOR][COLOR=black] ~ to see what is in the directory[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=blue]cd Desktop[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=blue]sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run[/COLOR]
 
It complained again about xserever, so I did
 
[COLOR=blue]sudo killall gdm[/COLOR]
 
and then again
 
[COLOR=blue]sudo sh NVIDIA-Linux-x86-185.18.14-pkg1.run[/COLOR]
 
And I follwed through the optioned it gave me, reboot and it worked. Just like that. Yeah!!!

---

### Post by Boeruitafrika on 2009-06-10
It can't do 3D graphics, it need some openGL goodies?

---

### Post by Steelmourne on 2009-06-11
As bodhi.zazen said, the repositories are the easiest way to update (sudo apt-get install nvidia-glx-180 nvidia-settings) and manual drivers require more work, especially with new kernels.

---

### Post by Boeruitafrika on 2009-06-17
I tried several option and after 8 fresh installations with disk formats, for the i386 the best result is the manual driver first thing after install. Somehow the apt and synaptic install do not work?

Also got Compiz, Emerald and AWN going with the cool icons from Mac4Lin. With all the stuff going, i am reluctant to make lost of changes and redo everything. Which leads me to another question. Is there a undo function for nautilus?

---

### Post by M Star on 2009-06-19
[COLOR=Sienna][SIZE=4][FONT=Comic Sans MS]:D
It worked!!!!!
step 2 showed an error [/FONT][/SIZE][/COLOR]> E: somrthin something not found[COLOR=Sienna][SIZE=4][FONT=Comic Sans MS]but i continued and it works!!!!![/FONT][/SIZE][/COLOR]

---

