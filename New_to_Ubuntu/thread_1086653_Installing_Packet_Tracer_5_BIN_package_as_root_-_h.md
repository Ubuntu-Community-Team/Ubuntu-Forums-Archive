---
title: "Installing Packet Tracer 5 BIN package as root - how?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by sirsmegalot105 on 2009-03-04
I'm attempting to install Packet Tracer 5.1 in Ubuntu 8.10, the binary package **PacketTracer51_i386_installer-deb.bin** has been downloaded from my Cisco Academy account.

The problem I'm having is that it has to be installed as root and with root priviledges, at the moment when I open terminal I get **username@laptop:~$** and usually sudo when I go to install something... I take it I need to be at **root@linux:~$**?

This is what the Cisco page says I need to do

> To install the Linux BIN packages, set the permission to be executable (chmod +x PacketTracer51_*.bin) then execute the binary in the terminal.

And also in order to create custom devices (which I need to do) their FAQ states:

> In order to create a custom device, the Packet Tracer application needs to be able to write to the PT/template folder. In Ubuntu, Packet Tracer must be installed at the root level, and then run as root to successfully write to this folder.

So... how do I get this all done then? :confused: :)

BTW I've already decided not to go down the WINE route, would prefer to use the proper linux binaries that Cisco provide for a Linux installation.

---

### Post by skymera on 2009-03-04
Run it with "sudo"

So as it says, make it executable. Then run the file from terminal with sudo

---

### Post by sirsmegalot105 on 2009-03-04
Thanks, OK I think it's executable now (must be it just brought up a clean CLI prompt), but when I try running I get this:

> 
username@laptop-linux:~/Downloads$ sudo PacketTracer51_i386_installer-deb.bin
[sudo] password for username: 
sudo: PacketTracer51_i386_installer-deb.bin: command not found

Should I run this as sudo install or something else, and how would I uninstall a manual command line installation like this if there are problems later?

Thanks again for your help

---

### Post by skymera on 2009-03-04
sudo chmod +x PacketTracer51_i386_installer-deb.bin
sudo ./PacketTracer51_i386_installer-deb.bin

---

### Post by sirsmegalot105 on 2009-03-04
> **skymera said:**
> sudo chmod +x PacketTracer51_i386_installer-deb.bin
sudo ./PacketTracer51_i386_installer-deb.bin

Thank you - I forgot about the ./ bit cos I was in the folder so thought I just had to type the file name after sudo :)

I can get on with my studying now - cheers again :popcorn:

---

### Post by skymera on 2009-03-04
> **sirsmegalot105 said:**
> Thank you - I forgot about the ./ bit cos I was in the folder so thought I just had to type the file name after sudo :)

I can get on with my studying now - cheers again :popcorn:

Glad it worked out ok :)

---

### Post by bricked on 2009-03-16
help please.

i am trying to install the same program but without the tutorials as part of the package.

all i get though are errors.
 i copied and pasted the information you left but with my specific file cuz it doesn't have the tutorials added in it.

with the file sitting on my desktop i tried the following.

username@username-desktop:~$ sudo chmod +x ./PacketTracer51_no_tutorials_i386_installer-deb.bin
chmod: cannot access `./PacketTracer51_no_tutorials_i386_installer-deb.bin': No such file or directory
username@username-desktop:~$ 

and...

username@username-desktop:~$ sudo chmod +x PacketTracer51_no_tutorials_i386_installer-deb.bin
chmod: cannot access `PacketTracer51_no_tutorials_i386_installer-deb.bin': No such file or directory
username@username-desktop:~$ 

also get errors with the other line.

username@username-desktop:~$ sudo ./PacketTracer51_no_tutorials_i386_installer-deb.bin
sudo: ./PacketTracer51_no_tutorials_i386_installer-deb.bin: command not found
username@username-desktop:~$ 

i even tried selecting properties from the file and checking the "allow executing the file as a program", both checked and unchecked there is no difference in error codes. 

thanks
bricked

---

### Post by oldos2er on 2009-03-16
If the file's on your desktop, you first need to run "cd Desktop".

---

### Post by bricked on 2009-03-17
> **oldos2er said:**
> If the file's on your desktop, you first need to run "cd Desktop".

that was it, thank you. i need to remember that ubuntu is CaSe sensative.

after your tip i used a capital "D" to switch. Doh!

---

### Post by sleepyjon on 2009-03-17
I know you said you didn't want to go the wine route, but the last time I used packet tracer  (december 2008) the linux version didn't work very well, and the wine version worked perfectly.

The linux version was prone to freezing, had trouble rendering text, and was generally a mess.

---

### Post by MaindotC on 2009-03-26
I've got the 32-bit package but I'm using x64.  I've googled the forums and it seems to be difficult to install a 32-bit package on a 64-bit machine.  Anyone have an idea how I can go about this?
```

Attempting to install package now
dpkg: error processing PacketTracer-5.0-u.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 PacketTracer-5.0-u.i386.deb
./PacketTracer5_i386_installer-deb.bin: line 12: cd: /media/disk/PacketTracer: No such file or directory

```

---

### Post by linnyguy on 2009-04-18
hi i'm new to Ubuntu i having a problem with Packet Tracer... i did the chmod, cd to Desktop, and ran the install with what appeared to be no problems.  my problem is, now I cannot find where it was installed to... any hints?
thank you in advance

---

### Post by sleepyjon on 2009-04-18
> **linnyguy said:**
> hi i'm new to Ubuntu i having a problem with Packet Tracer... i did the chmod, cd to Desktop, and ran the install with what appeared to be no problems.  my problem is, now I cannot find where it was installed to... any hints?
thank you in advance


try running packettracer from the terminal.

---

### Post by linnyguy on 2009-04-18
as in sudo ./packettracer?

never mind that comment, it did not work. tried a "whereis packettracer" with no results

Intel Core2 T7200@2.00Ghz|3GB Corsair DDR2|
Lenovo ThinkPad Z61e|Ubuntu 8.10 Intrepid Ibis|

---

### Post by sleepyjon on 2009-04-18
> **linnyguy said:**
> as in sudo ./packettracer?

never mind that comment, it did not work. tried a "whereis packettracer" with no results

Intel Core2 T7200@2.00Ghz|3GB Corsair DDR2|
Lenovo ThinkPad Z61e|Ubuntu 8.10 Intrepid Ibis|

```

Jon@myComp$ packettracer

```

---

### Post by linnyguy on 2009-04-19
hey thanks sleepyjon.  i must have installed it wrong because the command returns this:

steve@steve-laptop:~$ packettracer
bash: packettracer: command not found

any other suggestions?

in the "how the heck did I do that?" area, I had some problems with sound (alsamixer) and the latest updates fixed that :)

TYIA

---

### Post by MaindotC on 2009-04-19
It should be in  /usr/local/PacketTracer5/packettracer but you should also have it installed in your menu under "Internet".

---

### Post by linnyguy on 2009-04-19
thanks strAlan,  must be going blind, I know I looked there :(  
i found it and it opens without any hitches ;)

glad I found this group, thanks to all! :popcorn:

---

### Post by pfum on 2009-04-22
> **sleepyjon said:**
> I know you said you didn't want to go the wine route, but the last time I used packet tracer  (december 2008) the linux version didn't work very well, and the wine version worked perfectly.

The linux version was prone to freezing, had trouble rendering text, and was generally a mess.
Could u tell me more about the wine route, koz actually it's having trouble rendering text(i am using Ubuntu 8.10) 'n it's pissing me off to loose so much time...
thx

---

### Post by MaindotC on 2009-04-22
I haven't installed it via Wine because it works fine natively.  If you're having problems with the wine install, tell us where you're having trouble and post the output.

---

### Post by sleepyjon on 2009-04-22
> **pfum said:**
> Could u tell me more about the wine route, koz actually it's having trouble rendering text(i am using Ubuntu 8.10) 'n it's pissing me off to loose so much time...
thx

First install wine, it should be in the repositories. If not you can get a deb from getdeb.

```

sudo aptitude update && sudo aptitude install wine

```

Configure wine. You need to run the command, but you don't need to actually run anything.

```

winecfg

```

download the windows version of packet tracer.

Use wine to run the installer. Assuming you saved the installer to your desktop the command would be:

```

wine ~/Desktop/whatevertheinstallis.exe

```

The installer should put an icon in your menu someplace, at least it does in xfce. If not you can run it by something like:

wine ~/.wine/drive_c/"Program Files"/rest of the path here

Good luck.

---

### Post by pfum on 2009-05-05
thank you sleepyjon 'n StrAlan.
:) it's now working perfectly!

---

### Post by hovrashko on 2009-09-06
[SIZE=4][B]Well, is here any ideas how to install Packet Tracer on ubuntu 9.04 x64?
[/B][/SIZE]

---

### Post by MaindotC on 2009-09-06
Open two terminals.  In one terminal, execute the installation file:
```

amd64@amd64:~/Desktop$ ./PacketTracer5_i386_installer-deb.bin 
Self extracting archive...

```

There will be a bit of a delay while the .deb file is downloaded to your /tmp folder.  When it is complete, you should see this:
```

Welcome to Packet Tracer 5 Installation

```

Go to the other terminal.  Look in /tmp/ and you should see a folder starting with the phrase "selfextract".  Follow these commands:

```

amd64@amd64:/tmp$ ls
gconfd-amd64     orbit-amd64      selfextract.ADu978  virtual-amd64.IWsHr5
gconfd-root      orbit-root       ssh-mDGWOq7868
hsperfdata_root  plugtmp          tmp.hAZODZ7815
keyring-PAY1p0   seahorse-o2wd1C  Tracker-amd64.8000
amd64@amd64:/tmp$ cd selfextract.ADu978/
amd64@amd64:/tmp/selfextract.ADu978$ ls
eula.txt  installer  PacketTracer-5.0-u.i386.deb
amd64@amd64:/tmp/selfextract.ADu978$ cp PacketTracer-5.0-u.i386.deb /home/amd64/Desktop/

```

The suffix following "selfextract" may vary.  Once you copy it from the /tmp folder you can Ctrl + C the other terminal and stop the initial installation.  Then you can install the .deb file by using the following command:

```

amd64@amd64:~/Desktop$ sudo dpkg -i --force-architecture PacketTracer-5.0-u.i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package packettracer.
(Reading database ... 175811 files and directories currently installed.)
Unpacking packettracer (from PacketTracer-5.0-u.i386.deb) ...
Setting up packettracer (5.0-1) ...
Installed files. Please wait for post-install operations to finish..
gtk-update-icon-cache: Cache file created successfully.
Finished

```

It should now be listed in Applications -> Internet -> PacketTracer 5.0.

---

### Post by boublik on 2009-09-20
Hi,
I'm completely new to linux and i'm trying to install the packet tracer:

I tried the sudo ./home/john/PacketTracer52_i386_installer-deb.bin 
but it keeps telling me no such file or directory. I'm not even familiar with how to access files and folders through the terminal. some help or references would be much appreciated. 
Thanks

---

### Post by MaindotC on 2009-09-20
You can't execute files using dot-slash unles you're in the directory where the executable program is located.  Navigate to /home/john/ and THEN type ./PacketTracer52_i386_installer-deb.bin.

---

### Post by boublik on 2009-09-21
> **strAlan said:**
> You can't execute files using dot-slash unles you're in the directory where the executable program is located.  Navigate to /home/john/ and THEN type ./PacketTracer52_i386_installer-deb.bin.

Thanks dude, got it and the installation

---

### Post by robertrose6 on 2009-09-25
how did it work for you. I installed packettracer and it didnt seem to work to well

---

### Post by MaindotC on 2009-09-25
Need more information.

---

### Post by boublik on 2009-09-28
I haven't really used the software as to tell about the performance or errors anywhere, but the file menu font is weird, the 'File, Edit,...' are small or just messed up. All font including devices names, damn, all unclear. Any suggestions would be gratefully appreciated.

---

### Post by boublik on 2009-10-08
Hello again, 
The first normal installation, and after fonts were fixed did not work properly. I removed it and installed it using Wine. The installation process was fine but it crashed 1 sec after loading with and 'unexpected error' message that could not be read due to the rapidity and brutal force of the crash :) 
Thought I'd give y'all some insight,
Cheers

---

### Post by MaindotC on 2009-10-10
Depends on a lot of things and you don't have your machine specs listed in your signature nor any other info that can help us determine the issue.  Just install .deb file and I suggest you try downloading different fonts from the repos.  Specifically you may want to try installing msttcorefonts or any other restricted formats.

---

### Post by boublik on 2009-10-11
Sorry, haven't thought about it. I have an IBM Thinkpad T41 with 1.4ghz CPU and 1.2 Gb Memory.

---

### Post by MaindotC on 2009-10-11
Nothing I just said has anything to do with the requirements of your machine.  Please follow my advice and explain where you need help or cease posting questions on this thread.

---

### Post by boublik on 2009-10-11
I cannot see the time when in real time, the numbers are on top of each other, and when i try to enter and IP address into a device i can only see the first number i enter, yet the IP would be set if i just type the right numbers. Thanks for the tips, and take it easy.

---

### Post by tad1073 on 2009-10-15
I have PacketTracer52.tar.gz and extracted it to my desktop and installed from there, I installed to the default location which /opt/pt and created a symlink to /usr/local but, I am unable to run it. I issue "packettracer" and get "Starting Packet Tracer 5.2" but the program doesn't launch.

---

### Post by MaindotC on 2009-10-15
Look you don't have to create symlinks or put it in different directories or anything like that.  It should be a .deb file!  If you are getting some messed up tar.gz pm me and I'll help you further.

---

### Post by boublik on 2009-11-03
> **strAlan said:**
> Depends on a lot of things and you don't have your machine specs listed in your signature nor any other info that can help us determine the issue.  Just install .deb file and I suggest you try downloading different fonts from the repos.  Specifically you may want to try installing msttcorefonts or any other restricted formats.

It's working fine now after installing the fonts. 
Thanks again

---

### Post by reve99 on 2010-01-02
really thanks man,that was really usefull

---

### Post by infiniti on 2010-11-13
I have a problem. I installed packet tracer and it's working, BUT there is a huge font and terrible letters on the interface. can someone tell me how to change appearance of packet tracer interface?

I am using ubuntu remix 10.10. 

regards

---

### Post by wahsape on 2010-12-22
Install ttf-mscorefontsinstaller from Synaptic Package Manager.

That will solve your font problems.

---

### Post by Valthronis on 2011-03-31
Hi, I'm completely new to Ubuntu and was wondering if someone could help me out with installing Packet Tracer in Ubuntu, Ive been attempting this all mourning with no success. 

After I download the bin file off of the cisco site what should my next move be?

--Val

---

### Post by uRock on 2011-03-31
Place the binary in your home folder then run the following commands to install.```
chmod 700 PacketTracer*
```This makes the binary executable.
```
./PacketTracer*
```This executes the binary.

---

### Post by Valthronis on 2011-03-31
PacketTracer532_i386_installer-deb.bin

. . . is located in my home folder

when attempeted?

me@me-Inspiron-1564:~$ chmod 700 PacketTracer*
me@me-Inspiron-1564:~$ ./PaketTracer*
bash: ./PaketTracer*: No such file or directory
me@me-Inspiron-1564:~$

---

### Post by uRock on 2011-03-31
> **Valthronis said:**
> PacketTracer532_i386_installer-deb.bin

. . . is located in my home folder

when attempeted?

me@me-Inspiron-1564:~$ chmod 700 PacketTracer*
me@me-Inspiron-1564:~$ ./P[COLOR="Red"]ak[/COLOR]etTracer*
bash: ./PaketTracer*: No such file or directory
me@me-Inspiron-1564:~$

You misspelled Packet in the second command.

---

### Post by Valthronis on 2011-03-31
HA HA!!! silly me!

Worked awesome, thanks for the assist!

--Val

---

### Post by uRock on 2011-03-31
> **Valthronis said:**
> HA HA!!! silly me!

Worked awesome, thanks for the assist!

--Val

You're welcome and good luck with your CCNA and/or CCNP training. I will be testing for certification in the next few months.:D

---

### Post by LostarIshaKa on 2011-09-20
Hello, I've tried most if not all of the methods on this topic, trying to get PackerTracer to run. Using the method described in the post just prior to this one, I still get this:
  ```
dpkg: error processing PacketTracer-5.3_2.i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 PacketTracer-5.3_2.i386.deb
lostar@ubuntu:~/PacketTracer$ 
```any ideas, I've been at this for hours...

---

### Post by Hakunka-Matata on 2011-09-21
> **LostarIshaKa said:**
> Hello, I've tried most if not all of the methods on this topic, trying to get PackerTracer to run. Using the method described in the post just prior to this one, I still get this:
  ```
dpkg: error processing PacketTracer-5.3_2.i386.deb (--install):
 [COLOR=Red]package architecture (i386) does not match system (amd64)[/COLOR]
Errors were encountered while processing:
 PacketTracer-5.3_2.i386.deb
lostar@ubuntu:~/PacketTracer$ 
```any ideas, I've been at this for hours...

download the correct package (64bit) for your system.  You have evidently downloaded the 32 bit (architecture) package

---

