---
title: "Wireless Config Vostro 1500"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by MikeM6244 on 2011-06-22
I'm new to Linux and Ubuntu. I downloaded Ubuntu 11.04 a few days ago on my Dell Vostro 1500 (I also have a Dell XPS 15z that I may try to configure later). I know there are a few other threads on this forum regarding my laptop, but I'd like to have personalized/individual help with this so I don't get too confused.

The first thing I want to do is get my wireless working. I have a Broadcom DW1390 wireless card. I type 'iwconfig' in the Terminal and I get this:

wlan0 IEEE 802.11bg ESSID:off/any
      Mode:Managed Access Point: Not-Associated  Tx-Power=0 dBm
      Retry long limit:7   RTS thr:off   Fragment thr:off
      Power Management:off

lo and eth0 say 'no wireless extensions.'

Another topic said to type 'sudo aptitude update' and 'sudo aptitude upgrade' into the Terminal. The command line then reads: '[sudo] password for mike:' I try to type my password, but nothing happens. It won't let me type anything. Do I need 'sudo' before those two commands? And can I get this to work without having an active internet connect on my Vostro 1500?

Thanks!

---

### Post by TeoBigusGeekus on 2011-06-22
About wireless: have you checked in Additional Drivers whether there is a proprietary driver for your wireless card? If so install it. (You will of course need a wired connection for this.)

About apt: whenever you type your password in ubuntu (command line) nothing shows up. Just type it - correctly - and press enter.

---

### Post by MikeM6244 on 2011-06-22
I connected my computer to the internet using a wired connection. When I checked Additional Drivers (System > Administration > Additional Drivers), I was told that "No proprietary drivers are in use on this system." In addition, there is nothing to "enable" in the boxes below - they're empty/blank.

In regards to the Terminal password issue, I'm sure I typed my password correctly because I opened the Terminal, entered the command 'sudo aptitude update' and purposefully entered my password incorrectly, and received the message "Sorry, try again." When I did enter the correct password, I was told 'sudo: aptitude: command not found'. What does that command do, by the way? I entered it because I read it somewhere else on the forum, but I'd like to understand the purpose behind the command.

Thanks again!

---

### Post by TeoBigusGeekus on 2011-06-22
Try
```
sudo apt-get update
sudo apt-get upgrade
```
The first one will search for updates for your system; the second one will install them.
Aptitude is not installed by default in ubuntu any more (I think). Apt is the default package manager.

Can't help you with your wireless card though, sorry...

---

### Post by MikeM6244 on 2011-06-22
It took a few minutes, but after a software update, the additional drivers were available to install. I installed the Broadcom STA wireless driver and the NVIDIA accelerated graphics driver. Both drivers are currently in use.

After that, I tried the codes you listed above while wired to the Internet. I got this from the Terminal:

```
mike@ubuntu:~$ sudo apt-get update
[sudo] password for mike: 
Ign http://security.ubuntu.com natty-security InRelease
Ign http://us.archive.ubuntu.com natty InRelease
Ign http://us.archive.ubuntu.com natty-updates InRelease
Hit http://security.ubuntu.com natty-security Release.gpg
Hit http://us.archive.ubuntu.com natty Release.gpg
Hit http://security.ubuntu.com natty-security Release
Hit http://us.archive.ubuntu.com natty-updates Release.gpg
Hit http://us.archive.ubuntu.com natty Release  
Hit http://us.archive.ubuntu.com natty-updates Release
Hit http://security.ubuntu.com natty-security/main Sources
Hit http://us.archive.ubuntu.com natty/main Sources
Hit http://us.archive.ubuntu.com natty/restricted Sources
Hit http://us.archive.ubuntu.com natty/universe Sources
Hit http://us.archive.ubuntu.com natty/multiverse Sources
Hit http://us.archive.ubuntu.com natty/main amd64 Packages
Hit http://security.ubuntu.com natty-security/restricted Sources
Hit http://security.ubuntu.com natty-security/universe Sources
Hit http://security.ubuntu.com natty-security/multiverse Sources
Hit http://security.ubuntu.com natty-security/main amd64 Packages
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com natty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com natty/universe amd64 Packages
Hit http://us.archive.ubuntu.com natty/multiverse amd64 Packages
Ign http://us.archive.ubuntu.com natty/main TranslationIndex
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex
Hit http://security.ubuntu.com natty-security/universe amd64 Packages
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages
Ign http://security.ubuntu.com natty-security/main TranslationIndex
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-updates/main Sources
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources
Hit http://us.archive.ubuntu.com natty-updates/universe Sources
Ign http://security.ubuntu.com natty-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com natty-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex
Ign http://security.ubuntu.com natty-security/main Translation-en_US
Ign http://security.ubuntu.com natty-security/main Translation-en
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com natty-security/multiverse Translation-en
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en
Ign http://us.archive.ubuntu.com natty/main Translation-en_US
Ign http://us.archive.ubuntu.com natty/main Translation-en
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty/restricted Translation-en
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty/universe Translation-en
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en
Reading package lists... Done
mike@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@ubuntu:~$ ^C
mike@ubuntu:~$
```

I'm going to keep messing with it myself, but please continue helping me :)

---

### Post by wildmanne39 on 2011-06-22
Hi run these three commands in a terminal
```
lspci -nn
```
```
lsmod
```
```
iwconfig
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

