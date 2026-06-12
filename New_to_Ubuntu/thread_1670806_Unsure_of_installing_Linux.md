---
title: "Unsure of installing Linux"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by hobden81 on 2011-01-19
Hi everybody. My name is Ben. I am a hobbyist 3d artist, and I have been looking to apply for some jobs recently which involve a familiarity with Linux. In conversation with a work colleague recently, he said ubuntu was a poplular and 'friendly' way to get into Linux. All I really understand is that Linux is an operating system, such as is windows vista and mac os. I am interested in installing a form of linux on my PC, but Im terrified that I will lose all my software and files that I have on my windows vista. Is there a real possibility of this happening? I wouldnt consider myself very tech minded but I am intrigued by Linux and would like to get myself familiar with some basic commands and how it works. Can anyone suggest the best way for me to get some experience of Linux on my own PC, without losing my windows vista? Is it possible for two operating systems to co-exist on a single pc?

---

### Post by kaldor on 2011-01-19
Backups are a must in **all** Operating systems and **all** areas of computing; if you don't already have a backup of your files, buy an external drive as it may save you a load of headaches in the future even if you don't try Ubuntu/Linux.

Ubuntu is, indeed, a Friendly way of using Linux. It's simple to use and most of the dirty work is done out of the box. For learning Linux, here is what I recommend:

1) _Back up all files_ and install Ubuntu. Get the latest (10.10) disc and select the option to install both operating systems (Vista and Ubuntu) Side by side. This gives a genuine Dual-boot.

2) This method is slow and not as useful, but is almost impossible to end up causing any damage (I have never heard of it, but remember computer suck ;) ). Use WUBI to install Ubuntu inside of Windows as a regular program. Reboot and you can choose between Vista and Ubuntu. Due to depending on Windows, Ubuntu will have just as much issues with defrags, slow downs, and other annoying Windows issues as well. Drivers may not work properly and you need to cleanly shut down Windows in order for Ubuntu to boot. This is the perfect way of testing the waters with Ubuntu, but it's very limited.

3) Virtual machines are *very* helpful for learning about how Linux works. You'll need at least 2 GB of RAM for this to go smoothly, but 1 GB will suffice. You can install a software called Virtualbox in Windows Vista which lets you install Guest Operating Systems in that program. Virtualbox is basically a hardware emulator. It's very easy to use, but is slow (due to dedicating RAM to it. The added benefit to this is that you can install multiple Linux operating systems on this program and no matter what, the changes you make will not harm your computer. If you take this route, I suggest you try both Ubuntu and Fedora.

Good luck!

---

### Post by kg87 on 2011-01-19
well, you've got multiple options, but, i would consider the safest bet would be to run it in virtual box. 

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181513&stc=1&d=1295456988[/IMG]

Simply because you're not altering your physical system. AND you'll also be able to use stuff like Blender in it aswell.
oh and its free.  

if you like it then, then you could go and find tuts to install along side vista (although im sure its awkward if memory serves).

---

### Post by lol768 on 2011-01-19
If you are wary of installing a dual boot then why not use WUBI (stands for windows ubuntu installer). It's a much safer method of installing Ubuntu as it installs Ubuntu like a program which you can easily install/uninstall through the control panel. There is little (if not no danger at all) that you will lose any files at all.

Link to WUBI: [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by kwacka on 2011-01-19
There is ALWAYS the possibility that you can lose software (which can easily be replaced) & data (which can't) which is why you religiously backup everything, right?

The act of re-partitioning your harddrive to install Ubuntu (or Windows 7) will increase the risk of data loss, but it isn't a problem I've encountered.

My advice would be to download a copy of Ubuntu Desktop, burn to a CD or USB memory stick and boot your computer from that.

Of course it will load more slowly than from a HD installation but you will get an idea of Ubuntu.

---

### Post by kg87 on 2011-01-19
well, you've got multiple options, but, i would consider the safest bet would be to run it in virtual box. 

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=181513&stc=1&d=1295456988[/IMG]

Simply because you're not altering your physical system. AND you'll also be able to use stuff like Blender in it aswell.
oh and its free.  

if you like it then, then you could go and find tuts to install along side vista (although im sure its awkward if memory serves).

---

### Post by lol768 on 2011-01-19
If you are wary of installing a dual boot then why not use WUBI (stands for windows ubuntu installer). It's a much safer method of installing Ubuntu as it installs Ubuntu like a program which you can easily install/uninstall through the control panel. There is little (if not no danger at all) that you will lose any files at all.

Link to WUBI: [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by Mark Phelps on 2011-01-19
A simple and low-risk way of developing some familiarity with Ubuntu is to install it INSIDE MS Windows using Wubi. That avoids messing with partitioning, and although the results is slightly less performant than a separate install, it serves the purpose for getting some experience using it.

Problem is, after a while, you will end up massively customizing it and even (shudder!) attempting to update it.  That's when you will run into problems because (1) is it a difficult process to "migrate" the wubi installation to a separate partition and (2) recent Wubi updated have had a nasty history of rendering Ubuntu unusable.

Also, don't let anyone tell you it is a simple matter to let the Ubuntu installer load Ubuntu "side by side" with your Vista install -- it is NOT.  Allowing the installer to resize your current partitions is asking for the very kind of trouble you are trying to avoid.

---

### Post by lol768 on 2011-01-19
If you are wary of installing a dual boot then why not try using WUBI which installs Ubuntu like a program in Windows which can easily install and uninstall. There is very little danger that you will lose any files and this method allows you to try out Ubutnu before deciding whether you want to keep it or not.

More info: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Download WUBI: [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by oldos2er on 2011-01-19
Yes, two (or more) OSes can be installed on one computer. Back up any sensitive data before you begin.

Creating a LiveCD and booting from it is one way to check out Ubuntu without any changes to your system. [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Then there's Wubi, which is a method of installing Ubuntu into your current Windows' partition, as if it were a Windows program. [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Then there's the traditional way of installing Ubuntu into its own partition(s). [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

More general info: [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

[http://ubuntuguide.org/wiki/Ubuntu:Maverick](http://ubuntuguide.org/wiki/Ubuntu:Maverick)

---

### Post by lol768 on 2011-01-19
If you are wary of installing a dual boot then why not try using WUBI which installs Ubuntu like a program in Windows which can easily install and uninstall. There is very little danger that you will lose any files and this method allows you to try out Ubutnu before deciding whether you want to keep it or not.

More info: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Download WUBI: [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by lol768 on 2011-01-19
Note: be sure to backup all your files anyway -- that way nothing can go wrong
[]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")

---

### Post by kg87 on 2011-01-19
sry!

---

### Post by Paqman on 2011-01-19
> **hobden81 said:**
> I am intrigued by Linux and would like to get myself familiar with some basic commands and how it works.

TBH, it works pretty much the same way as any other OS. The only difference is you have to install it yourself, which can be a little daunting. Once installed you don't really need to do anything to it, it's pretty low-maintenance.

Much more important than the OS is the apps. You're likely to be switching to a different suite of apps for getting 3D work done, so the real learning curve will be familiarising yourself with those.

I'll just reiterate what the others have said, if you're concerned about losing anything, make sure your backups are up-to-date, then go for it. Installing Ubuntu is actually really easy, as is uninstalling it. You've got nothing to lose really!

---

### Post by Paqman on 2011-01-19
> **hobden81 said:**
> I am intrigued by Linux and would like to get myself familiar with some basic commands and how it works.

TBH, it works pretty much the same way as any other OS. The only difference is you have to install it yourself, which can be a little daunting. Once installed you don't really need to do anything to it, it's pretty low-maintenance. There's no need to use the command line if you don't want to.

Much more important than the OS is the apps. You're likely to be switching to a different suite of apps for getting 3D work done, so the real learning curve will be familiarising yourself with those.

I'll just reiterate what the others have said, if you're concerned about losing anything, make sure your backups are up-to-date, then go for it. Installing Ubuntu is actually really easy, as is uninstalling it. You've got nothing to lose really!

---

### Post by ppv on 2011-01-19
Based on the first post the safer way would be a live system. This can be followed by virtual system then Wubi and then dual boot.

Virtual systems are also safe but could be a bit slow based on the PC that it is used on. Live system can be run in two ways, live CD and a live USb drive. From Live CD and live USB, live CDs would be slower.



For live CD
- Download the ubuntu live cd iso from the ubuntu website. Version 10.04 can be preferred becuase it is a long term release.
- Burn the downloaded iso to a CD
- Restart the PC with the CD in the drive
- If not already set, set the first boot device as CD/DVD drive in your bios when the system boots
- Choose the option "Try ubuntu without installing" in the menu that appears once your PC boots from CD.


For live USB
This method and its steps are almost similar to the live CD option with the difference that one uses a USB flash drive as the medium to boot from.
For this you would need USB support on your motherboard. You would most likely have it if your computer is not very old..about 4-5 years. A thumb drive of atleast 1GB is required.

-Download the Ubuntu live iso from the Ubuntu website
-Download unetbootin from sourceforge. Unetbootin is a software that will help you make a live Ubuntu USB from the iso that you downloaded. It is fairly simple to use.
-Using unetbootin create a flash drive with Ubuntu on it.
- Plug it into your computers USB port and reboot.
- This time you need to have USB / removable media as the first choice in your bios boot options menu.
- Select try without installing option in the Ubuntu menu that appears.


If you choose to use Wubi
- Download Wubi from the ubuntu website.
- Run the downloaded wubi.exe
- In the next screen choose the options that you would prefer abut the size of installation and username and password. An installation size of 25-30 GB is decent.
- After the installation reboot.
With this method upon every reboot you will have the option to choose either Windows or Ubuntu.

Instructions for virtual system are specific to the software you choose but you would find guides to it in this forum.

---

### Post by ppv on 2011-01-19
Double post.

---

### Post by T-rock007 on 2011-01-19
Ubuntu is great for new Linux users you can always give it a shot in Virtual Box or dual boot it but i say go for it

---

### Post by fballem on 2011-01-19
Some other things to be aware of:

1/ Linux is not Windows. Most of your Windows programs, like Microsoft Office or your current graphical editing program, will not run directly in Linux. There is an option called WINE that will allow some Windows programs to run, but since you wanted to become familiar with Linux, this would defeat the purpose.

2/ If you are using Microsoft Office (Word, Excel ...) in Windows, then you are likely going to be using OpenOffice in Linux.

3/ You have not said what programs you are currently using. If you provide such a list, then others here may be able to suggest Linux equivalents.

Be patient with yourself - it took me about three months to get comfortable - and I am technicaly literate. This is one time when being a power user (in Windows) was a disadvantage. I expected Linux to always behave like Windows. Since you are not as technically comfortable, it may be easier for you to learn the Linux way of doing things.

Hope this helps,

---

