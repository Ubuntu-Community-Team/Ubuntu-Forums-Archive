---
title: "my ubuntu10.04 does not hibernate."
date: 2010-07-15
forum: New to Ubuntu
---

### Post by amityadav9314 on 2010-07-15
Hi!

My ubuntu 10.04 does not hibernate, it simply goes on a blank screen(lcd light goes off) and then on touchin any key on keyboard it simply takes me to the login screen.

help me if you got me.please

thanks!

---

### Post by foutes on 2010-07-15
A little info on you're setup would help.

---

### Post by amityadav9314 on 2010-07-15
I didn't get it.
What more info I need to tell you...
like what??

---

### Post by peace.gangsta on 2010-07-15
> **amityadav9314 said:**
> What more info I need to tell you...

It appears you are a new user. 
What I gather is you click on hibernate in shutdown menu, but your computer only locks down.
You can tell about your system (laptop in this case).Does your system has a graphics card?.Furthermore you can also let us know about the type of linux installation you have i.e separate from windows or on it (using wubi) ?
Anyways try this and see what happens.Open console and 
```
sudo hibernate
```
"Hibernate" is installed by default in Ubuntu. Write here what happens.

---

### Post by foutes on 2010-07-15
> **amityadav9314 said:**
> I didn't get it.
What more info I need to tell you...
like what??

Do you have a laptop?
If so what manufacturer?  
Does it have an ATI or Nvidia,Intel graphics chipset?
What driver for chipset?
Is you're Ubuntu 10.04 a fresh install?,an upgrade? wubi install? 

The reason for all the questions is there are different fixes for the problem depending on what setup you have.

Here is a link to a post on hibernate not working in 10.04
[http://ubuntuforums.org/showthread.php?t=1469340](http://ubuntuforums.org/showthread.php?t=1469340)

---

### Post by faical117 on 2010-07-15
maybe the problem is with the swap partition.

---

### Post by amityadav9314 on 2010-07-15
i have installed ubuntu under windows 7
i am using laptop--->>compaq 601
i have ATI
i have a fresh install ubuntu 10.04, no upgrades.



after writin..."sudo hibernate" in terminal, i got this result



amit@ubuntu:~$ sudo hibernate
sudo: hibernate: command not found
amit@ubuntu:~$ 


and i am a new user

---

### Post by tarps87 on 2010-07-15
Try installing the hibernate program.


Quick way:
Copy/paste the following into the terminal
```

sudo apt-get install hibernate -y

```
Enter your login password and hit enter
then run **sudo hibernate** again

---

### Post by amityadav9314 on 2010-07-15
i have done this and here is the output....---->>


amit@ubuntu:~$ sudo apt-get install hibernate -y
[sudo] password for amit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  liblzo2-2 uswsusp
Suggested packages:
  915resolution splashy
The following NEW packages will be installed:
  hibernate liblzo2-2 uswsusp
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
5 not fully installed or removed.
Need to get 318kB of archives.
After this operation, 1,176kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main liblzo2-2 2.03-2 [63.4kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe uswsusp 0.8-1.1ubuntu3 [158kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe hibernate 1.99-1.1 [96.1kB]
Fetched 318kB in 11s (27.5kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package liblzo2-2.
(Reading database ... 164257 files and directories currently installed.)
Unpacking liblzo2-2 (from .../liblzo2-2_2.03-2_i386.deb) ...
Selecting previously deselected package uswsusp.
Unpacking uswsusp (from .../uswsusp_0.8-1.1ubuntu3_i386.deb) ...
Selecting previously deselected package hibernate.
Unpacking hibernate (from .../hibernate_1.99-1.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up linux-image-2.6.32-23-generic (2.6.32-23.37) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found Windows 7 (loader) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error
run-parts: /etc/kernel/postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-23-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-23-generic; however:
  Package linux-image-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.23.24); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-No apport report written because the error message indicates its a followup error from a previous failure.
                                           No apport report written because the error message indicates its a followup error from a previous failure.
                                                                     headers-2.6.32-23-generic (2.6.32-23.37) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-23-generic; however:
  Package linux-headers-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up liblzo2-2 (2.03-2) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already

Setting up uswsusp (0.8-1.1ubuntu3) ...
update-initramfs: deferring update (trigger activated)

Setting up hibernate (1.99-1.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Errors were encountered while processing:
 linux-image-2.6.32-23-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-23-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
amit@ubuntu:~$ sudo hibernate
hibernate:Warning: Tuxonice binary signature file not found.
amit@ubuntu:~$ 



Is it done?

---

### Post by amityadav9314 on 2010-07-15
So tell me what next?

---

### Post by tarps87 on 2010-07-16
> **amityadav9314 said:**
> So tell me what next?

Sorry, it appears my post didn't submit properly.
I has installed, but I am assuming your PC did not hibernate after you run it. It should still work despite the errors, this is a different issue with the command being replaced (not important).

Can you post the output of
```
swapon -s
```

---

### Post by amityadav9314 on 2010-07-16
here is the output




amit@ubuntu:~$ swapon -s
Filename				Type		Size	Used	Priority
/host/ubuntu/disks/swap.disk            file		261112	0	-1
amit@ubuntu:~$

---

### Post by Braik on 2010-07-16
> **amityadav9314 said:**
> i have installed ubuntu under windows 7
i am using laptop--->>compaq 601
i have ATI
i have a fresh install ubuntu 10.04, no upgrades.
 
after writin..."sudo hibernate" in terminal, i got this result
 
amit@ubuntu:~$ sudo hibernate
sudo: hibernate: command not found
amit@ubuntu:~$ 
 
and i am a new user
 
Hi there,
From this post I was already supposing that the installation was made ON WIN7 with Wubi.
 
> **amityadav9314 said:**
> here is the output
 
amit@ubuntu:~$ swapon -s
Filename Type Size Used Priority
/host/ubuntu/disks/swap.disk file 261112 0 -1
amit@ubuntu:~$
 
And from this one I have the confirmation (/host/ubuntu). I am not an expert, but, it is possible to hibernate with this kind of installations?

---

### Post by tarps87 on 2010-07-16
> **Braik said:**
> Hi there,
From this post I was already supposing that the installation was made ON WIN7 with Wubi.
 

 
And from this one I have the confirmation (/host/ubuntu). I am not an expert, but, it is possible to hibernate with this kind of installations?

I'm glad you asked that question, a quick look at the wubi site and hibernation is not supported.  This does make sense that it is, due to the swap partition being a file on the host (windows) machine an therefore not a 'stable' partition.
It may be possible to tweak the install to hibernate but this is not guaranteed to be 100% successful.

If hibernation is important to you I would suggest looking at a dual boot set up

---

### Post by bcbc on 2010-07-16
Hibernation is not supported on wubi installs as it uses a swap file. Ubuntu requires a swap partition to hibernate. While it is possible to use a swap partition from a wubi install, the whole point of wubi is that you can run ubuntu without partitioning your drive.

If hibernation is important, and you would like to partition your drive, you should probably do a direct install to partition.

---

### Post by amityadav9314 on 2010-07-16
okay i can understand that.

---

### Post by SaintDanBert on 2010-10-24
It seems to me that nothing happened because of the message text and the fact that your shell continued running. Here is how I talk about this stuff.

HIBERNATE -- suspend-to-disk
SLEEP -- suspend-to-ram
Both of these activities are collectively known as "suspend" operations.

"Hibernate" copies all of the state date for the currently running system
and leave behind several breadcrumbs. When finished preserving the state, hibernate does a power-off shutdown.

"Sleep" does exactly the same thing as hibernate.  However, instead of a power-off shutdown, it goes into a power-on idle mode. Most workstations have some sort of indicator lamp or LED to show that your are asleep with power on instead of no-indicator power off.  For me, I have a "new moon" LED.

Regardless of the style suspend, when you wake from suspend, the system startup sees the available breadcrumbs and restores the system state data.
In addition, any active network connections, wire or wireless interfaces will require a restart. Also, there might be some restart needed for your video.

I get this same "TuxOnIce" message when I try to run hibernate.

Cheers,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2010-11-04
I found this post [http://ubuntuforums.org/showpost.php?p=9178083&postcount=5](http://ubuntuforums.org/showpost.php?p=9178083&postcount=5) while searching for solutions to this question.

I'll need to rummage to discover which packages or modules are needed so that the various "ibm" and "thinkpad" special keys and buttons get enabled. You may PM if you have specific questions.

[color=green]
:EDIT:  
There are details here [http://ubuntuforums.org/showpost.php?p=9919010&postcount=6](http://ubuntuforums.org/showpost.php?p=9919010&postcount=6) that speak to the needed package.  Also, all of this gets configured dynamically as part of the new 'xinput' configuration.  Try ```
prompt$ xinput --list
``` to see what devices your workstation understands.
:EDIT-END:
[/color]
There is yet other configuration for X11 and Xorg so that things will launch and dispatch from within the desktop.

I have an X61-tablet and all of these keys mostly works for me ... so long as I meet all of the other requirements.

It seems that "thinkpad special keys" yielded useful details as a search in several places.  NOTE -- all sorts of "xinput" changes happened for Ubuntu Lucid (v10.04 LTS). These changes mean that key and button specific packages might have slipped by in other testing.

Bonne chance,
~~~ 0;-Dan

---

