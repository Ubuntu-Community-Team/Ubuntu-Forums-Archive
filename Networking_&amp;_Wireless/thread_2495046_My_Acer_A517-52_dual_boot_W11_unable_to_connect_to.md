---
title: "My Acer A517-52 dual boot W11 unable to connect to internet after 2 years"
date: 2024-02-05
forum: Networking &amp; Wireless
---

### Post by jeanmi2a on 2024-02-05
Hello,
Since april 2022, successful private usage of Ubuntu-upgraded from Focal Fossa to Jammy Jellyfish, Ubuntu 22.04 LTS...but
since january 13th I'm getting a black screen without the Gnome environment and have no access to my Home folders.
Since then two drivers were downloaded, wireless Lan card Mediatek MT7921 and Realtek RTL 8111H family controller  from the ACER site, leading to a successful Window boot.
I started to check several ubuntu events reports and Ubuntu solutions.
Today I could connect to the internet by Ethernet cable/Orange livebox and was able to get Ubuntu  updates, using command lines *sudo apt upgrade* and [I]sudo apt full -upgrade.
[/I]I would really appreciate your help, thank you in advance.
Please  see Boot-info on [https://paste.ubuntu.com/p/tZgkQzqYdJ](https://paste.ubuntu.com/p/tZgkQzqYdJ).
jeanmi2a

---

### Post by oldfred on 2024-02-05
I ge this on your pastebin:
> The Paste you are looking for does not currently exist.

Have you installed correct nVidia driver?
Of have you installed second nVidia driver without totally purging first install?

#What is installed
dkms status

Purge if necessary & install nVidia
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)

---

### Post by jeanmi2a on 2024-02-07
Thank you...
I'm happy to read your timely answer and these guidelines.
I Will be back in fews days.
Merci encore pour votre aide.
jeanmi2a

---

### Post by jeanmi2a on 2024-02-08
Hi Old Fred,
You can see the Boot-Info at [https://paste.ubuntu.com/p/Xxbr9983NY](https://paste.ubuntu.com/p/Xxbr9983NY), sorry for my early blank report !
No I didn't update the NVIDIA driver..., but as a beginner with Linux I would prefer using Windows, for a first step (1).
Do you agree ? 

(1) The ACER site display a list of VGA drivers (such as GeForce experience issued 2022/10/14).

---

### Post by oldfred on 2024-02-08
Using Windows, if you desire is totally separate from installing the nVidia driver into Ubuntu, so you do not get blank screen.

Do you get grub menu. And then boot Safe Graphics?
That may give you a low resolution video. 
You can can instlal the nVidia driver from Software settings or command line.
If you already installed a incorrect driver, you must purge old before installing new or you get conflicts.
And do not install a drive directly from nVidia, as it effectively needs reinstall with every kernel update.

More details:
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)   # 2017
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by jeanmi2a on 2024-02-09
:guitar:thank you, for this early morning answer, thank you Old Fred !
So my next step on ubuntu as shown !

---

### Post by jeanmi2a on 2024-02-11
Hi Oldfred
This is my progress report:
I'couldn't get the Grub Menu until now, so no Safe Graphics display....to fast a boot !!!
Would you please tell me more details i.e. to set the parameter (timeout).
I understand I had to purge the old NVIDIA driver before update.
So the command *sudo apt-get remove -purge nvidia-** worked.
Thanks in advance

---

### Post by oldfred on 2024-02-11
Fast boot is an UEFI/BIOS setting. It assumes no system changes and immediately boots. Usually then no time to press any key.
You often bypass fast boot setting with a "cold" boot or full power down, so system goes thru full check of configuration (still pretty quick). That typically gives just enough time to press correct key to get into UEFI.

You can reboot into UEFI/BIOS, if you can boot.
Reboot into UEFI:
sudo systemctl reboot --firmware or
sudo systemctl reboot --firmware-setup

Grub menu also have an entry to get into UEFI/BIOS.
If only one system installed, grub menu not normally shown. You have to press escape key just after vendor logo shown on screen. Often have to be quick.

Systems have been UEFI since 2012 when Microsoft required vendors to install Windows 8 in UEFI boot mode to gpt partitioned drives.
But vendors still call it BIOS. Since about 2020, many systems are UEFI only, no BIOS. But my Dell that says it only boots in UEFI mode still calls it BIOS.

---

### Post by jeanmi2a on 2024-02-13
Hi Oldfred
I'm on the right track after reading your replies and also 7 pages of Ubuntu GRUB2 official description, but  
my ACER dual boot taking too much time/almost frozen, my guess GRUB not set correctly.
So I just edited the GRUB config :
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR='lsb_release -1 -s 2> /dev/null || echo Debian'
GRUB_CHDLINE_LINUX_DEFAULT="quiet splash"
GRUB_LINE_LINUX=""
Unable to decrypt these settings and remedy to any errors, I need your help.
I goofed in writing the last line, so you should read instead:
GRUB_CHDLINE__LINUX="".

---

### Post by oldfred on 2024-02-13
Those look like standard settings for grub.
I do change several, but not required.
I like to see boot process, or many lines scrolling by. Often now too fast to follow, but same info is in log files.
I like to force boot to grub menu.
I change default of 10 sec to 3 or just enough time if I am quick to change grub to another entry.

My settings, but you do not have to use them.
> [FONT=monospace][COLOR=#000000]GRUB_TIMEOUT_STYLE=menu [/COLOR]
GRUB_TIMEOUT=3 
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian` 
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"

[/FONT]

I also change these as I have several versions of Ubuntu and want to keep track of which is which. And then I update 40_custom with any other boot stanzas I want, so do not need os-prober scanning system.
> [FONT=monospace][COLOR=#000000]GRUB_DISABLE_OS_PROBER=true [/COLOR]
GRUB_DISTRIBUTOR=jammy
[/FONT]

If you want to change you can use this:
[FONT=monospace]sudoedit /etc/default/grub

Then to use changes in grub.
sudo update-grub 

But if booting is slow this is one of many threads on other suggested settings:

[/FONT][https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)

---

### Post by jeanmi2a on 2024-02-13
Thanks for this super fast answer ...I'dn't believe it, 
good night  !!!
):P

---

### Post by jeanmi2a on 2024-02-18
> **oldfred said:**
> Using Windows, if you desire is totally separate from installing the nVidia driver into Ubuntu, so you do not get blank screen.

Do you get grub menu. And then boot Safe Graphics?
That may give you a low resolution video. 
You can can instlal the nVidia driver from Software settings or command line.
If you already installed a incorrect driver, you must purge old before installing new or you get conflicts.
And do not install a drive directly from nVidia, as it effectively needs reinstall with every kernel update.

More details:
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)   # 2017
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

Jeanmi2A to Oldfred
I was trying to execute the last command from your above post #2017:
after choosing between either :
1) ubuntu driver auto-install "recommended by you "
or 2)  installing a NVIDIA driver from their list "why not to try ?"
Both commands rejected by the system  for some reason... 
user access control rights ? 
or "not found" syntax error ?
Would you please help me, thank you

---

### Post by oldfred on 2024-02-18
Please copy & paste each of these & post both command and results if you get an error then stop.
sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers autoinstall

---

### Post by jeanmi2a on 2024-02-19
re. your 18 feb post, 
my console outputs from commands are
sudo apt-get remove-purge nvidia-* .....' *l'opération apt-get remove-purge n'est pas valable* (french for not valid)
sudo ubuntu-drivers autoinstall.............all the available drivers are already installed.
(NOTE Copy- Paste  thru *pastebinit* being such an hard work, so I'm unable to share with you the the whole screen output)
waiting for your answer

---

### Post by tea for one on 2024-02-19
There is a syntax error in your command.
```
sudo apt-get remove-purge nvidia-* .....' *l'opération apt-get remove-purge n'est pas valable* (french for not valid)

sudo apt-get remove --purge nvidia-*  [COLOR="#0000FF"]# copy and paste this line in your terminal[/COLOR]
```

---

### Post by oldfred on 2024-02-19
Is Internet working?

Run this to see what is installed
dkms status

I have not used nVidia for years, not a gamer.
But I can still run command:
```
fred@Z170-jammy:~$ sudo apt-get remove --purge nvidia-*
[sudo] password for fred: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'nvidia-firmware-535-535.154.05' for glob 'nvidia-*'
Note, selecting 'nvidia-cuda-toolkit-doc' for glob 'nvidia-*'

```
And a screen full of other drivers it could not uninstall.

---

### Post by jeanmi2a on 2024-02-19
Yes Internet connection is working (on Linux only with Ethernet cable).
The above command result was a list full of nvidia "XXX by version number.... "not installed and therefore that could'nt be cancelled". That's OK.
I ran this command a few days ago !!!
About dkms status could provide me an example, not working now here. (I saw a long synopsis in Linux manuel, such as argument, option etc..).
From UEFI firmware update i'll check on ACER site.

---

### Post by jeanmi2a on 2024-02-29
Hey OldFred
A very simple straightforward command worked
sudo apt-get install ubuntu-desktop...
There was my favorite GNOME background, i could see
"la petite sirène" a underwater diving spot in the Martinique island.
Thank you once again for your help

---

