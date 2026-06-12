---
title: "Ubuntu and Nvidia Gforce 8600 GT"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Robert98374 on 2009-02-09
Ello!

I was wondering how do i install a *.run package i downloaded from the Nvidia website for drivers for my Graphics card?

---

### Post by howefield on 2009-02-09
> **Robert98374 said:**
> Ello!

I was wondering how do i install a *.run package i downloaded from the Nvidia website for drivers for my Graphics card?

You must have seen the instructions on the page you downloaded from ? Substitute the name of your file instead of the one in the example below.

-------------------------------------------
STEP 1: Review the NVIDIA Software License.

You will need to accept this license prior to downloading any files.

STEP 2: Download the Driver File
Download - NVIDIA-Linux-x86_64-180.22-pkg2.run

STEP 3: Install
Type "sh NVIDIA-Linux-x86_64-180.22-pkg2.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X server configuration file. Please see Chapter 3 of the README or run 'man nvidia-xconfig' for details on usage. Instructions for those wishing to edit their X config file by hand can also be found in the README.

If you have any questions or problems, please check the NVIDIA Linux discussion forum. If you don't find an answer to your question there, you can send email (in English) to [email]linux-bugs@nvidia.com[/email].

---

### Post by Robert98374 on 2009-02-09
I tried that but when i did copied the direct command it came up with the error
sh: Can't open NVIDIA-Linux-x86_64-180.22-pkg2.run

---

### Post by howefield on 2009-02-09
I am downloading the file, I'll try and replicate your issue, I am due to remaster the disk anyway :)

Did you cd to the folder where your file is and also use sudo to precede the command ?

Edit.
Opened fine, open terminal, cd to Desktop, and run the command with sudo . The file opens.

---

### Post by Robert98374 on 2009-02-09
heres what the terminal Says and my commands...
> robert@robert-desktop:~$ cd Desktop
robert@robert-desktop:~/Desktop$ ls
firefox.desktop  gnome-terminal.desktop  NVIDIA-Linux-x86-180.22-pkg1.run
robert@robert-desktop:~/Desktop$ sudo sh NVIDIA-Linux-x86_64-180.22-pkg2.run
sh: Can't open NVIDIA-Linux-x86_64-180.22-pkg2.run

---

### Post by howefield on 2009-02-09
The file you are trying to open is not the one on your Desktop.

When you start typing the first few letters of the file name, press tab and the file name will auto complete, saves time and typos.

---

### Post by Robert98374 on 2009-02-09
O.o not sure what you mean, the file that i downloaded from Nvidia is saved on my desktop

---

### Post by howefield on 2009-02-09
Compare the names of the files in your terminal output

NVIDIA-Linux-x86-180.22-pkg1.run is the one you have downloaded.

You are trying to open NVIDIA-Linux-x86_64-180.22-pkg2.run which you do not have and obviously cannot be opened.

I did say to substitute the name of the file you downloaded for the one I gave in the example earlier.

---

### Post by XanderCrews on 2009-02-09
Here's what you do:

```

sudo /etc/init.d/gdm stop

```

This will give you a black screen with possibly some text on it. Press
Alt + F1 to get a login line.  Login again, and make sure the nvidia package
is executable.

```

chmod +x *nameOfNvidiaPackage.run*

```

Then enter:

```

sudo ./*nameOfNvidiaPackage.run*

```

And then follow the on screen instructions.

This assumes you have the proper development headers.

I think

```

sudo apt-get install libc6-dev

```

should do it.

XC

Oh and I'm pretty sure you need the kernel source as well:

```

sudo apt-get install linux-source

```

---

### Post by houstonbofh on 2009-02-09
This may seem like a silly question, but why are you doing this?  There are drivers for your card in the repositories, and they are much easier to install than the method you have chosen.  You may want to consider that your method will also make upgrades more difficult, so if you do not have a good reason otherwise...

---

### Post by Robert98374 on 2009-02-10
I am trying to get WoW to work with wine and i am having a lot of issues with getting that up and running. So i assumed that i might need to upgrade my drivers. Also when i try to enable desktop effects its also having issues.

---

### Post by Robert98374 on 2009-02-10
> **XanderCrews said:**
> Here's what you do:

```

sudo /etc/init.d/gdm stop

```

This will give you a black screen with possibly some text on it. Press
Alt + F1 to get a login line.  Login again, and make sure the nvidia package
is executable.

```

chmod +x *nameOfNvidiaPackage.run*

```

Then enter:

```

sudo ./*nameOfNvidiaPackage.run*

```

And then follow the on screen instructions.

This assumes you have the proper development headers.

I think

```

sudo apt-get install libc6-dev

```

should do it.

XC

Oh and I'm pretty sure you need the kernel source as well:

```

sudo apt-get install linux-source

```

After i went through that process, i started Ubuntu back up but after the screen that says Ubuntu and the progress bar, all that happens is a black screen.So what do i do from here? Everything installed without a problem till i tried to get back into Ubunutu. 

I restarted the computer and i had the exact same issue. What should i do now?

---

### Post by bailbath on 2009-02-10
Can you tell us your hardware?
For instance I have 2 8600 in sli and when I installed the Nvidia driver it did not know which to use so i had to edit xorg.conf
See this thread
[http://ubuntuforums.org/showthread.php?t=1043813](http://ubuntuforums.org/showthread.php?t=1043813)
Ian

---

### Post by Robert98374 on 2009-02-10
I checked out that topic but i have a few questions

Where do i exactly add that line?
```

Busid      "PCI:1:0:0"

```

Second, i have to be root but i dont know how to access my linux partition in liveCD?

---

### Post by LowSky on 2009-02-10
first go to synaptic and remove the old nvidia driver, then reboot, then folllow the instructions included earlier to compile the driver by hand, then reboot.

Personally I have the same card and it works fine using the repo's driver.

Side not you cant run compiz and WoW at he same time, install fusuion icon to turn off and on compiz

---

### Post by Robert98374 on 2009-02-10
What are they called in symnaptic?

---

### Post by bailbath on 2009-02-11
> **Robert98374 said:**
> I checked out that topic but i have a few questions

Where do i exactly add that line?
```

Busid      "PCI:1:0:0"

```

Second, i have to be root but i dont know how to access my linux partition in liveCD?

That was really a example of solving one problem and may not apply to you but we don't know your hardware. You need to supply us with info about your setup.From the command line/terminal if you put in  lspci that will supply you and us with the info. To find the command line/terminal goto applications-accessories-Terminal.
Also these Nvidia drivers are available from your package manager then you will find that you will not have to update them yourself but it will be done automatically. The package manager is called synaptic and can be found system-administration-synaptic package manager. For you to use that I think it would be good for you to start again reinstall and learn from your mistakes it's the way most of us on here learnt Linux. There will people who don't agree with a reinstall and would rather solve a problem but sometimes starting over will give you more confidence.
You also seem confused by what we are trying to tell you to do.
Perhaps I can suggest that you check this link to learn some basics so that you can follow what we are saying.
[http://www.ubuntupocketguide.com/index2.html](http://www.ubuntupocketguide.com/index2.html)
Ian

---

### Post by Robert98374 on 2009-02-11
I have reinstalled Ubuntu. I did that before i read your post. As for the information from lspci
```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
```

I am assuming the information that i need to mess with the buss id would be the last line?
[CODEQUOTE]02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)[/CODE]

---

### Post by bailbath on 2009-02-12
Ok where are you at with the install?
You don't need to put the bus id in as you have a single card not sli.
Ian

---

### Post by Robert98374 on 2009-02-13
Actually there was an option to use restricted drivers for my video card popping up. Went through that and let ubuntu do its thing, now it runs great, even better in Ubuntu than Windows.

Next issue on the agenda....How to get vent installed as a native package and make it so i am able to talk to people...

---

### Post by bailbath on 2009-02-13
You did what I would have suggested nextand it sounds all good!
Well done all the best
Ian

---

### Post by Ripose on 2009-02-13
Where does this go? 
Use "sax2 -r" for X.Org configuration.

---

