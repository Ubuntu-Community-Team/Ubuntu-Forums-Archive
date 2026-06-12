---
title: "Ubuntu Netbook won't shut down !!!"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by paul9766 on 2011-02-19
[SIZE=3][FONT=Verdana]
I have recnetly installed Ubuntu Netbook 10.10 on my Sony Vaio Netbook VPCM11M1E/B and i'm qite happy with it.
However it will not shut down properly, all i get is a hanging purple screen, so I have to dissconect from the power supply to get the computer to shut down, how do I solve this problem please ??
Also, I have burned a copy of the full Desktop version of Ubuntu 10.10, however when I put it in the netbooks external optical drive, the files appear ok but won't load or install, how do I do this ?? you might like to know that I am having enormous difficulty accessing the BIOS, i've tried pressing ESC, F2, F10, DEL etc etc etc, but to no avail, I think I would like to overwrite the Netbook Version of Ubuntu with the Full Desktop Version, I just need to know how, please no super techy answers to this as I'm a complete linux beginner, so no endless lines of computer code or the Netbook bites the dust...Cheers
[/FONT][/SIZE]

---

### Post by NightwishFan on 2011-02-19
This likely means that the routines needed to power off your specific laptop are not supported or buggy in that release. I would try the new Ubuntu this April and see if the issue if fixed then.

As long as the disk is syncing there should be no harm in simply powering it off, even though it is less convenient. Trust me, Ubuntu is **able** to power off machines, just perhaps not that model of laptop.

A fix to the issue (if there is one) wont involves endless lines of computer code, and almost never does. That is a myth about Linux. Also most terminal commands are a simple and easy shortcut compared to fixing something manually with a text editor or etc. I would rather copy and paste a few lines of text than spend hours chatting to someone on the phone and not get it fixed any way. :lolflag:

I will look into your brand of laptop, if I find anything out I will get back to you.

---

### Post by Gordonbp531 on 2011-02-19
Did you enable the Open Office Quickstarter possibly?

---

### Post by frogotronic on 2011-02-19
> **paul9766 said:**
> 
I have recnetly installed Ubuntu Netbook 10.10 on my Sony Vaio Netbook VPCM11M1E/B and i'm qite happy with it.
However it will not shut down properly, all i get is a hanging purple screen, so I have to dissconect from the power supply to get the computer to shut down, how do I solve this problem please ??
Also, I have burned a copy of the full Desktop version of Ubuntu 10.10, however when I put it in the netbooks external optical drive, the files appear ok but won't load or install, how do I do this ?? you might like to know that I am having enormous difficulty accessing the BIOS, i've tried pressing ESC, F2, F10, DEL etc etc etc, but to no avail, I think I would like to overwrite the Netbook Version of Ubuntu with the Full Desktop Version, I just need to know how, please no super techy answers to this as I'm a complete linux beginner, so no endless lines of computer code or the Netbook bites the dust...Cheers


Hello,

Firstly, keep the font size in your posts at the default (not larger).

Secondly, to change from the netbook to the desktop "version" requires that you choose at the login screen.  You are using 10.10, which has the new Unity interface.

See this post here for a more complete explanation: [http://ubuntuforums.org/showpost.php?p=10269943&postcount=9](http://ubuntuforums.org/showpost.php?p=10269943&postcount=9)

As to your shutdown issues, it is likely related to a video driver issue.  Try using the X-SWAT PPA

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

To install the PPA packages, go to System>Administration>Software Sources.  Choose the "Other Sources" tab.  Click on the "Add" button and in the APT line, enter **ppa:ubuntu-x-swat/x-updates**.

*Aside: Also make sure that you are selecting all possible updates - see attached screen shot*

Reload the packages (it will prompt you) and then install any updated packages.

Thirdly, you might try updating the BIOS, which is a pain on a SONY.  Here's a howto: [http://opennomad.com/content/flashing-vaio](http://opennomad.com/content/flashing-vaio) 

I'd be a little averse to the BIOS update
[http://support.vaio.sony.eu/computing/vaio/downloads/info/info.aspx?l=en_IE&url=VAIO/Updates/EP0000225555.exe&m=VPCM11M1E_B&ip=EP0000225555.htm](http://support.vaio.sony.eu/computing/vaio/downloads/info/info.aspx?l=en_IE&url=VAIO/Updates/EP0000225555.exe&m=VPCM11M1E_B&ip=EP0000225555.htm)

As it appears to be just for improved password interaction and not anything major.

- CH

---

### Post by grahammechanical on 2011-02-19
What does the netbook user manual say about accessing the BIOS and shutdown and suspend and hibernate and switching off? Are you saying that the machine does not have a power on/off button?

Regards.

---

### Post by frogotronic on 2011-02-19
To access BIOS (from manual):

To change or remove the power-on password (user password)
1 Turn on the computer.
2 Press the F2 key when the VAIO logo appears.
The password entry screen appears. If the screen does not appear, restart the computer and press the F2 key several
times when the VAIO logo appears.
3 Enter the user password and press the Enter key.
4 Press the < or , key to select Security to display the Security tab, select Set User Password, and then press the
Enter key.
5 On the password entry screen, enter the current password once and a new password twice, and then press the Enter key.
To remove the password, leave the Enter New Password and Confirm New Password fields blank and press the Enter
key.
6 Press the < or , key to select Exit, select Exit Setup, and then press the Enter key.
At the confirmation prompt, press the Enter key.

---

### Post by paul9766 on 2011-02-20
> **NightwishFan said:**
> This likely means that the routines needed to power off your specific laptop are not supported or buggy in that release. I would try the new Ubuntu this April and see if the issue if fixed then.

As long as the disk is syncing there should be no harm in simply powering it off, even though it is less convenient. Trust me, Ubuntu is **able** to power off machines, just perhaps not that model of laptop.

A fix to the issue (if there is one) wont involves endless lines of computer code, and almost never does. That is a myth about Linux. Also most terminal commands are a simple and easy shortcut compared to fixing something manually with a text editor or etc. I would rather copy and paste a few lines of text than spend hours chatting to someone on the phone and not get it fixed any way. :lolflag:

I will look into your brand of laptop, if I find anything out I will get back to you.

Thank you for the advice, still no luck however, it could be that I just sinply don't understand Linux ( Ubuntu ) just yet, it seems a fairly steep learning curve to me after windows, my little netbook was running Win 7 starter, which was woefully slow, a friend suggested Ubuntu Netbook edition, all was going well with the install untill I got to the "Restart" stage of the process and everything just froze up, however i've now managed to find my way into the BIOS......F2 on Sony at the Vaio splashscreen, also I've found out that with the Netbook edition you get the choice of loading the Netbook Edition or the Full Version at the log on stage, nice touch I thought, still no luck with the Restart, Shutdown issue however, so i'm at a loss :(

---

### Post by paul9766 on 2011-02-20
> **gendibal said:**
> Did you enable the Open Office Quickstarter possibly?

Please explain more ?? thanks, all was going well with the install of Ubuntu Netbook untill it got to the Reboot stage of the install and everything just froze up, so now to power down the computer I have to yank the power supply and the battery out, which is a real pain, and doesn't make me feel all that wonderful about storing data on the system just yet, thanks for the help, much appreciated.:(

---

### Post by paul9766 on 2011-02-20
> **cement_head said:**
> Hello,

Firstly, keep the font size in your posts at the default (not larger).

Secondly, to change from the netbook to the desktop "version" requires that you choose at the login screen.  You are using 10.10, which has the new Unity interface.

See this post here for a more complete explanation: [http://ubuntuforums.org/showpost.php?p=10269943&postcount=9](http://ubuntuforums.org/showpost.php?p=10269943&postcount=9)

As to your shutdown issues, it is likely related to a video driver issue.  Try using the X-SWAT PPA

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

*Aside: Also make sure that you are selecting all possible updates - see attached screen shot*

Reload the packages (it will prompt you) and then install any updated packages.

Thirdly, you might try updating the BIOS, which is a pain on a SONY.  Here's a howto: [http://opennomad.com/content/flashing-vaio](http://opennomad.com/content/flashing-vaio) 

I'd be a little averse to the BIOS update
[http://support.vaio.sony.eu/computing/vaio/downloads/info/info.aspx?l=en_IE&url=VAIO/Updates/EP0000225555.exe&m=VPCM11M1E_B&ip=EP0000225555.htm](http://support.vaio.sony.eu/computing/vaio/downloads/info/info.aspx?l=en_IE&url=VAIO/Updates/EP0000225555.exe&m=VPCM11M1E_B&ip=EP0000225555.htm)

As it appears to be just for improved password interaction and not anything major.
To install the PPA packages, go to System>Administration>Software  Sources.  Choose the "Other Sources" tab.  Click on the "Add" button and  in the APT line, enter **ppa:ubuntu-x-swat/x-updates**.
- CH


Thank you so  much for this advice, much appreciated, I've been at this Ubuntu stuff  for just 2 days so far, and i'll confess to knowing diddly squat, after  Windows this seems like a huge learning curve for me, so some history  for you, the Netbook was running Win 7 starter, which was truly awful,  slower than a snail on mogadon, a friend suggested I try Ubuntu netbook  edition, so with gritted teeth I gave it a go. All was bobbing along  nicely with the install process untill right at the very end when I had  to Restart my computer, clicked on restart, result hanging purple  screen, so to shut down I have to disconnect from the power supply and  battery too, complete pain....
I've now discovered, many thanks, that I can select either the netbook  version or the desktop version at the log on stage, nice touch I  thought, thanks for that.
I've now also found my way into the BIOS....F2 at the Vaio splashscreen, fabulous.
I've also made the changes you suggested as per your screenshot, on my  version it was System > Update Manager > Settings.....I added the  ppa:ubuntu-x-swat/x-updates and ticked all the boxes too, run it as you  suggested, which is where I became confused, as it kept asking me to put  the install disk back in the optical drive and asked me to open with a  thing called "Package Manager", ??? for whatever reason it escapes me,  any way I did the best I could with it, alas still to no avail, click on  Restart or Shutdown and I still get the hanging purple screen.....so  I've given up now and don't know what to do next, so any further help  would be appreciated....Thanks !!   :sad:

---

### Post by frogotronic on 2011-02-20
I'd try the 10.04 LTS release - it's way more stable.  See if the live disc works on shutdown.


- CH

---

### Post by paul9766 on 2011-02-21
Thanks for the continued advice, I have taken your advice, downloaded, burnt and installed Ubuntu 10.04 (Lucid) and the computer even shuts down now which is a major step forward, and it looks very pretty too, however another problem has popped up now, it won't connect to the internet, my computers wireless switch is in the on position, and when I click on the wireless icon in the notification area, I don't see any networks listed at all, what do I do ??? and when connected what should I do about Anti-virus, firewall, security etc etc....thanks again friend

---

### Post by frogotronic on 2011-02-21
> **paul9766 said:**
> Thanks for the continued advice, I have taken your advice, downloaded, burnt and installed Ubuntu 10.04 (Lucid) and the computer even shuts down now which is a major step forward, and it looks very pretty too, however another problem has popped up now, it won't connect to the internet, my computers wireless switch is in the on position, and when I click on the wireless icon in the notification area, I don't see any networks listed at all, what do I do ??? and when connected what should I do about Anti-virus, firewall, security etc etc....thanks again friend

Okay, this is good progress.  

If you haven't installed it (10.04 LTS) on your hard-drive, do so now (erasing the 10.10 distro; backup your data files to a USB drive).  Lucid Lynx (10.04 LTS) is going to much more stable for you, as long as you don't do the distribution upgrade.  Make sure your update manager (Software Sources) is set for LTS releases only (see attached screenshot).

**_For the wireless:_**

1) Find an ethernet cable.
2) Plug your computer into the internet via the ethernet cable.
3) System>Administration>Hardware Drivers.  You should now see a choice of wireless drivers.  If there is one required, choose it and activate it (see screenshot).
4) Reboot.
5) You should now be able to connect to wireless networks.

**_For Antivirus:_**

System>Administration>Synaptic Package Manager

install clamtk

**_For Firewall:_**

System>Administration>Synaptic Package Manager

install gufw

activate it under System>Administration>Firewall

**_For security:_**

Ubuntu is mostly secure as long as you don't run things as an Administrator (called "root" or "super-user" in Linux).  Most things will not be run as root.  The exception is installing software.  But you will be prompted with a window dialogue as necessary.

- CH

---

### Post by gabriel6ft on 2011-03-22
> **paul9766 said:**
> [SIZE=3][FONT=Verdana]
I have recnetly installed Ubuntu Netbook 10.10 on my Sony Vaio Netbook VPCM11M1E/B and i'm qite happy with it.
However it will not shut down properly, all i get is a hanging purple screen, so I have to dissconect from the power supply to get the computer to shut down, how do I solve this problem please ??
Also, I have burned a copy of the full Desktop version of Ubuntu 10.10, however when I put it in the netbooks external optical drive, the files appear ok but won't load or install, how do I do this ?? you might like to know that I am having enormous difficulty accessing the BIOS, i've tried pressing ESC, F2, F10, DEL etc etc etc, but to no avail, I think I would like to overwrite the Netbook Version of Ubuntu with the Full Desktop Version, I just need to know how, please no super techy answers to this as I'm a complete linux beginner, so no endless lines of computer code or the Netbook bites the dust...Cheers
[/FONT][/SIZE]

I have the same laptop, everything is fine except for the shutdown and restart, which i will try now after i have fixed the **ppa:ubuntu-x-swat/x-updates**. i learnt from here, i am almost like a newbie too, but Ubuntu seems so interesting, that i can't seem to sleep, i have been awake all night playing with it. Note that i still have my windows 7 starter on. i replied to this post to suggest somethings, first, the desktop is better than the netbook ubuntu, in my own opinion. second to get rid of the cd rom window (as our netbook don't have one). Go to update manager, click on settings and on the ubuntu software tab, uncheck CD Rom with Ubuntu 10.10 Maverick Meerkat. Then you can upload your ubuntu first, do the **ppa:ubuntu-x-swat/x-updates**. advise as posted earlier, and lastly restart your wireless router if your Internet starts refusing(switch off mains and switch it back on), seems like linux chokes it sometimes, LOL... hope this helps.

---

### Post by BunTai on 2011-03-29
you need to do like this..it works like charm for me..

You need to have both modules available in order to be able to switch. Check this in a terminal by typing:

lspci -k|grep -i network --after-context 3
03:00.0 Network controller: RaLink RT2860
 Subsystem: Foxconn International, Inc. Device e002
 Kernel driver in use: rt2800pci
 Kernel modules: rt2800pci, rt2860sta

Here, rt2800pci and rt2860sta are both available, while rt2800pci is in use.

Make a file that allows you to easily switch between the two driver modules. For this open a terminal and then open nano by typing:
sudo nano /etc/modprobe.d/blacklist-wlan.conf
Write this two lines in nano:
blacklist rt2800pci
#install rt2860sta /bin/false

Save this (ctrl+O; return; ctrl+X).
If you now shut down and boot your system will then use the rt2860sta.

If, on the other hand, you want to make sure that the rt2860sta does _not_ get used, comment out the other line
sudo nano /etc/modprobe.d/blacklist-wlan.conf
#blacklist rt2800pci
install rt2860sta /bin/false
(Don't forget to save.)
If you now shut down and boot your system will then use the rt2800pci.

The "#" makes everything behind it a comment. It is ignored.

Why not just write blacklist rt2860sta?
A blacklisted module can still be pulled into use under certain circumstances. With the install rt2860sta /bin/false line we can prevent the rt2860sta from ever loading. Such stronger means have so far not turned out to be necessary with the other module.
What does this install line do?
It tells the system that whenever rt2860sta is to be loaded, the command /bin/false is to be executed instead.
What does /bin/false do?
false is a command on your system. So you can find out what it does by typing man false in a terminal.

source : [https://answers.launchpad.net/ubuntu/+question/132350](https://answers.launchpad.net/ubuntu/+question/132350)

---

### Post by frogotronic on 2011-03-30
> **BunTai said:**
> you need to do like this..it works like charm for me..

You need to have both modules available in order to be able to switch. Check this in a terminal by typing:

lspci -k|grep -i network --after-context 3
03:00.0 Network controller: RaLink RT2860
 Subsystem: Foxconn International, Inc. Device e002
 Kernel driver in use: rt2800pci
 Kernel modules: rt2800pci, rt2860sta

Here, rt2800pci and rt2860sta are both available, while rt2800pci is in use.

Make a file that allows you to easily switch between the two driver modules. For this open a terminal and then open nano by typing:
sudo nano /etc/modprobe.d/blacklist-wlan.conf
Write this two lines in nano:
blacklist rt2800pci
#install rt2860sta /bin/false

Save this (ctrl+O; return; ctrl+X).
If you now shut down and boot your system will then use the rt2860sta.

If, on the other hand, you want to make sure that the rt2860sta does _not_ get used, comment out the other line
sudo nano /etc/modprobe.d/blacklist-wlan.conf
#blacklist rt2800pci
install rt2860sta /bin/false
(Don't forget to save.)
If you now shut down and boot your system will then use the rt2800pci.

The "#" makes everything behind it a comment. It is ignored.

Why not just write blacklist rt2860sta?
A blacklisted module can still be pulled into use under certain circumstances. With the install rt2860sta /bin/false line we can prevent the rt2860sta from ever loading. Such stronger means have so far not turned out to be necessary with the other module.
What does this install line do?
It tells the system that whenever rt2860sta is to be loaded, the command /bin/false is to be executed instead.
What does /bin/false do?
false is a command on your system. So you can find out what it does by typing man false in a terminal.

source : [https://answers.launchpad.net/ubuntu/+question/132350](https://answers.launchpad.net/ubuntu/+question/132350)

@BunTai

Does suspend/hibernate/shutdown work for you using this solution?

Thanks,
CH

---

