---
title: "Deleted wrong files in Jaunty. Need to repair thru terminal (PLEASE HELP)"
date: 2011-05-20
forum: New to Ubuntu
---

### Post by kingschild on 2011-05-20
Hi ALL!
I am a newbie to Jaunty, so please forgive my descrip. terminology.
I need help please.
I am experiencing a great amount of grief with my Jaunty install.
I can no longer get a login screen in Jaunty. When I try to boot  normally for this install I get an unclean shutdown  screen & it goes into the "checking drive" mode.  I uninstalled some  applications  such as has to do with touchpad, remote desktop, xorg-driver-fglrx etc. I  reinstalled xorg-driver-fglrx, which I later found out that I do not  need. I have an AMD64 HP system with ATI graphics onboard.

 I need to find out how to load graphic user interface in Jaunty. Some  of the necessary files have been completely removed by me & I need  to reload the repositories and update my current install.

 The partition  is encrypted but I have been able to login with the  username & password for THIS encrypted install using the "repair  broken  system" part of the GRUB screen. 

 How do I go into the terminal and load  repositories, and maybe the kernel so I can do an update/upgrade? I do  not know if upgrade is part of what I need to do........
I wanna keep my Jaunty install so I can access 50G of data that is on this install. I have made no backup of this data!!!

 I am able to login to my install using my username & password after I get to the 
"#" prompt, so I know it can be done. I just need to know what to TYPE  into the terminal to restore the necessary files in the right place to  make it run.

Can someone please help me? 
Thank you,
kingschild

---

### Post by Elfy on 2011-05-20
Thread moved to Absolute Beginner Talk.

---

### Post by wildmanne39 on 2011-05-20
> **kingschild said:**
> Hi ALL!
I am a newbie to Jaunty, so please forgive my descrip. terminology.
I need help please.
I am experiencing a great amount of grief with my Jaunty install.
I can no longer get a login screen in Jaunty. When I try to boot  normally for this install I get an unclean shutdown  screen & it goes into the "checking drive" mode.  I uninstalled some  applications  such as has to do with touchpad, remote desktop, xorg-driver-fglrx etc. I  reinstalled xorg-driver-fglrx, which I later found out that I do not  need. I have an AMD64 HP system with ATI graphics onboard.

 I need to find out how to load graphic user interface in Jaunty. Some  of the necessary files have been completely removed by me & I need  to reload the repositories and update my current install.

 The partition  is encrypted but I have been able to login with the  username & password for THIS encrypted install using the "repair  broken  system" part of the GRUB screen. 

 How do I go into the terminal and load  repositories, and maybe the kernel so I can do an update/upgrade? I do  not know if upgrade is part of what I need to do........
I wanna keep my Jaunty install so I can access 50G of data that is on this install. I have made no backup of this data!!!

 I am able to login to my install using my username & password after I get to the 
"#" prompt, so I know it can be done. I just need to know what to TYPE  into the terminal to restore the necessary files in the right place to  make it run.

Can someone please help me? 
Thank you,
kingschildHi, can you get a terminal that you can type in? Follow jemofthewest directions that shouuld work, also you do need those xorg drivers most likely because you can not load a graphical interface with out the xorg server.

---

### Post by jemofthewest on 2011-05-20
If you don't have a login screen you're probably missing gdm... try reinstalling that:

sudo apt-get install gdm

Since that is the GNOME login manager.

Otherwise, if you're getting to the command line, try startx.  That's the usual way to start up a GUI if you still have one installed...

Repositories are located in /etc/apt/sources.list if you don't have them in there... try looking in their and adding any you don't have.  See below:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

After that, the command line way to update and upgrade is:

$sudo apt-get update
$sudo apt-get upgrade

---

### Post by Elfy on 2011-05-20
It's been a long day - I'll have a look again tomorrow, but to be frank at the moment I do not see how a reset for unity will be of any use.

---

### Post by Elfy on 2011-05-20
couple of things to read ... 

[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory)

[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

you might also find that if you've uninstalled things you shoudln't have (long shot called by long day) reinstalling from recovery 

boot to recovery (2nd/4th/6th options generally) choose root prompt with netowrk
apt-get update && apt-get install ubuntu-desktop && apt-getupgrade && reboot

should update/install/upgrade and then reboot 

try the gdm install first though

---

### Post by mc4man on 2011-05-20
While i've never had reason to - jaunty is EOL so to re-install packages that aren't in the /var/cache/apt/archives then I'd think you'd need to switch your sources to the old-release repos

---

### Post by kingschild on 2011-05-22
Hello again,
In order to repair my install & get my data,
I have tried to run the sudo apt-get install for gdm, sources.list, update & upgrade to no avail.
I have burned a Knoppix disk & was able to get the corrupted sda5 mounted.

When I boot from the GRUB, it goes through a disk check and gives me a prompt.

I am also running a dual-boot with WindowsXP.....forgot to say that in prev. post.

I have tried to install another instance of Jaunty, but when I tried to resize the sda5 (Jaunty) partition,
the install informed me that there are disk errors that need to be fixed. It would go no further.

I have tried to get the encryption passphrase (which I did not write down) by using
"sudo ecryptfs-unwrap-passphrase  /home/username/.ecryptfs/wrapped-passphrase" command from the prompt  after login with my username & password.

As I said, I was able to mount & see the directories in the encrypted "home" directory......but not the files.

I might be using a version of Knoppix that is not quite suitable for this operation. Any suggest for Knop Version?

At this point, I would like to be able to just get the data from the  home directory & reformat the partition, then do an install of the  latest distro of ubuntu.

I have also gotten a lot of multiply-claimed blocks. I was given a  choice of cloning the blocks & I said yes to each time it asked.  After an hour or so, I just hit the power strip & rebooted.

How can I copy all 50 GIG of files to a place where I can put them on another drive.
I really wanna fix the disk errors too.
Can I do this using Knoppix and a USB external hard-drive?......or maybe install Jaunty on the external after a swap 2 of the separate drive devices?

Thank you all,
kingschild

---

### Post by fritz269 on 2011-05-22
Have you tried booting from a live cd to see if you can access the files to back them up?

---

