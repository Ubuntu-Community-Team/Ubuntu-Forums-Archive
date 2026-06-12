---
title: "I don't understand program installation(s) in Linux"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-03-03
Hello,

I am new to Linux and the forums.

I do not understand the nature of program installations in Linux.
Is there a way to determine where a program installs itself?

Like in Windows, programs install into the "Program Files" folder and usually puts some files into the "Windows" folder.

Can someone explain how it works in Linux?  Hypothetically, if Firefox was not installed, so I downloaded it and installed Firefox, where would the install files go?

---

### Post by jwcalla on 2011-03-03
They tend to go all over.

The binary executables usually land in /usr/bin... configuration files in /etc... documentation files somewhere else probably.  Local user settings are typically installed in the user's home directory.

If you can find the installed package in Synaptic then you can view the properties and look at the list of installed files.

---

### Post by ankspo71 on 2011-03-03
Hi,
I never quite understood the directory structure completely either, but here are some links:
_[LinuxFilesystemTreeOverview]("https://help.ubuntu.com/community/LinuxFilesystemTreeOverview")_
_[Filesystem Hierarchy Standard]("http://proton.pathname.com/fhs/")_

> Hypothetically, if Firefox was not installed, so I downloaded it and installed Firefox, where would to install files go?

Anwhere you like as far as I know. I manually installed firefox4 beta to /usr/share/firefox4/, then I made a symbolic link at /usr/bin/firefox4 pointing to the firefox executable, so firefox 4 beta can be run from the terminal by typing 'firefox4'. Then I made my start menu entry using the command 'firefox4'.

Hope this helps.

---

### Post by ender4 on 2011-03-03
Windows and Linux (or Unix based OSes in general) have very different philosophies for organizing the file system.  

On Windows, as I understand it, most of the files for a program go in a single folder stored in the "program files" folder. This has advantages (such as finding all the files for a program in the same place) and disadvantages (such as a near-useless PATH)

Linux on the other hand organizes program files according to type.  So the executables are stored in /bin and /usr/bin, libraries are stored in /lib and /usr/lib, configuration files are stored in /etc, temporary files are stored in /tmp, cache files, databases, and other various state files are stored in /var, and media, icons, and other resource files are stored in /usr/share.
This means that all your executables for instance can be found in the same place, all your libraries can be found in the same place, etc.

In addition individual users can have individual configuration files which are general stored in so-called dot-files in their home folders.  These files begin with a period, and are the Unix version of hidden files (and folders).

---

### Post by ijumpship on 2011-03-03
Let me give you the best advice do not worry yourself too much if you are are general user.

You will only interact with less than  a quarter of the files.

how I start learn it

Anything  belongs to you(me) is in my Home  eg my videos is in /home/me/Video, eg downloads are in /home/me/Downloads

Anything go wrong will be record in Logs /var/log

Tasks are done in /etc/  eg networking power management etc

Every software you install will load in many place depends what needs to be done sometimes it need to interact with some other software through libraries. and you could go on and on.

On thing for sure you cannot just go one place to find all your answer but depends on what you want.


Oh one thing about windows.It has change since windows XP now you have a home folder similar to linux its documents settings /user/
application/data and if you understand it then it should be easy.

Since windows vista ,there are two programs file one for root and one for user so if were you would not worry unless I developed programs.

---

### Post by beew on 2011-03-03
You can find out which files are install and where if you look up the program from Synaptic Package manager, right click it to bring up "properties" and check "installed files".

In Windows programs are grouped by their names, this is intuitive for humans but not efficient  in a machine sense (many files are duplicated as the same libraries and what not overlap in different programs) whereas in Linux files are grouped according to functionality and so if a whole bunch of programs use the same library only one copy of the same library is installed. This makes Linux much  leaner and more efficient (My Ubuntu installation is about 30 G with a lot of applications, several movies and a a few G of music and my Windows Xp partition is also about 30 G with hardly anything in it, I just need one or two Windows  programs for work. If only looking at programs, which include a few games my Ubuntu partition is only 11G or so)  On the downside it also makes Linux more vulnerable to dependency problems because a lot of packages are interlinked this way. That is how I understand it.

---

### Post by Canime on 2011-03-03
Use the software center. Its the best and easiest way to get the software.

If you downloaded, then navigate to the download directory, you are going to find your downloaded files. 

Then run the system extraction tool that Linux comes with. Choose a directory you want to install into, and install your software there. 

Even extracting using the command line requires you to specify a directory. In that case you should choose a good directory from the ones listed above, and extract there. That's up to you.

---

### Post by Learning Linux 2011 on 2011-03-03
Thank you for responding.  

I guess why I asked this question is:

I tried to install a new version of Firefox by downloading it from the Mozilla web site, rather than from within Linux.

I downloaded and installed it, but I couldn't figure out where the actual program was located to run it.  I thought this is probably fairly common.  What if you don't use any update software within Linux, but download software directly from the web?  Where would it normally install to?  I.e. where do you go to find the actual program to run it?

---

### Post by Th3W1z4rD on 2011-03-03
> **Learning Linux 2011 said:**
> Thank you for responding.  

I guess why I asked this question is:

I tried to install a new version of Firefox by downloading it from the Mozilla web site, rather than from within Linux.

I downloaded and installed it, but I couldn't figure out where the actual program was located to run it.  I thought this is probably fairly common.  What if you don't use any update software within Linux, but download software directly from the web?  Where would it normally install to?  I.e. where do you go to find the actual program to run it?

Sometimes you can't install it from the vendor website. Some programs don't offer a linux alternative and you have to run them thru WINE which is off and on sometimes. I never use it anymore I just boot into my windows 7 if I need to do windows related things.

the linux .bin files are similar to windows .exe files. its like an installer. I believe .deb files also require little interaction from the user. Don't quote me on that as I too am a new linux user. this is just from my personal experience. 

hope you figure everything out, sorry I couldn't be more help

---

### Post by piquat on 2011-03-04
> **Learning Linux 2011 said:**
> I tried to install a new version of Firefox by downloading it from the Mozilla web site, rather than from within Linux.

 
If you DL'd a .msi or .exe file, it won't work here. What you usually find on a site for download, is a tarball (a compressed file, think zip file). When you open it, it's usually source code that needs compiled, IOW, not anything that is going to install easy for you.
 
My suggestion is that you stop DL'ing software from sites on the internet. It's a windows way of doing things and it can bring undesirable code with it. Any site worth DL'ing from will have a personal PPA set up, and even then I wouldn't be the first to dip my toe in that water.

---

### Post by mastablasta on 2011-03-04
don't download from web. you install from software center. you will then also get any programme updates through update manager.
 
PPA, .deb and compiling source codes - it's almost like running exe files and we all knwo where that leads us (regarding security and malware)
 
@ beew - my windows install is abot 9 - 10 GB. aside form windows i have thunderbird, firefox, office 2003. antivirus, firewlal, ATI drivers, m extra Mobo& sound drivers, GIMP, inkscape.. in short plenty of smaller and a bit larger programmes. i am not sure what you are doing to go up to 30GB.
 
I also have another computer where i have XP on about 5GB disk partition. that one has a problem due to updates and i had to move the page file to another disk. but sitll it leaves it about 800 MB free. i think that one has only the system a drivers, with some smaller programmes as Firefox and Tb and such is on another partition.
 
my bro has a bit more programmes (virtual boxes, WAMP server...) but stil he doesn't go over 20 GB (which is the size of his winXP partition). so my giess is that XP with all the service packs, security and some light programmes is also about 10-12 GB.

---

### Post by ijumpship on 2011-03-08
Oops wanted to make a post but was busy this weekend.

In a terminal 

if you want to find where a software was install type

[B]whereis [software]
[/B]
  eg. whereis vlc

if you want to see every path of the software type at the terminal

[B]locate [software] 
[/B]
   eg. locate vlc


hope this help.

change files at your own risk,you will break the system



remember to type solved if this thread is to be closed.

---

