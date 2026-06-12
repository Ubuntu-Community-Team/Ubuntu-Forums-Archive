---
title: "Ubuntu netbook won't install"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Charlie Chick on 2009-02-17
Hello Everybody,

I've just downloaded the new Ubuntu Netbook remix and burned the iso to a DVD, as it's too large for a CD. I then tried to install it onto a HP Compaq 2133 mini note using an external USB dvd drive.

Unfortunately, it hangs with the Ubuntu screen showing and the word 'install.....' underneath. Can anybody tell me what I'm doing wrong, please?

Many thanks,

Charlie

---

### Post by Charlie Chick on 2009-02-18
Interestingly, if I put in an older disk, like 7.10, it installs without problem, as does Windoze XP. My Micro$oft loving colleagues are are having a good laugh at Ubuntu's expense, which upsets me a bit.

Why will an older version install on a brand new computer where a newer version won't?

Charlie.

---

### Post by peakshysteria on 2009-03-10
I did the following on my better half's Mini Note:

**Installing from an external CD/DVD Drive**

1. If you have one available, installing from an external CD/DVD drive is the simplest installation method. Download a copy of Ubuntu 8.10 Intrepid Ibex and burn the image to an installation CD. Connect an external CD/DVD drive to the USB port and load the installation CD.

2. Put your finger somewhere close to **the F9 key**, because the Mini-Note's BIOS options pass quickly. Start or restart the computer and **press F9**, which will bring up the Boot Device menu.
Base Installation
Then;

1.When the language menu comes up, select your preferred tongue and hit enter. At the Ubuntu install menu **hit F6**, which will bring up the Boot Options line. Add the word **xforcevesa** at the end of the line and hit enter. The installer will then load the kernel and begin the installation process. It is normal for the progress bar to freeze for a short period of time. Have patience.

2. Eventually you should hear the welcoming sounds of Ubuntu through the Mini-Note's ample speakers, and see the Intrepid Live session desktop. While wireless networking is not available at this point, you should be able to connect to the internet through a wired ethernet connection if necessary. Double-click on the "Install" icon and follow the wizard through the subsequent screens, selecting your location and keyboard layout.
   
3.Step 4 will ask you how you'd like to partition the disk. If you're comfortable with losing everything currently on the disk, select "Guided - use entire disk". Otherwise, choose the option that makes the most sense for you. Ubuntu works just fine sharing the drive with a Windows install, and it will even read and write to your NTFS partition out-of-the box. REMEMBER - If you choose the entire disk, you will kill everything else on your hard drive. BACK UP FIRST! Continue through the wizard, filling in your user information, password and computer name. When you're sure you're ready to make changes to your hard-disk, hit "Install" on the final page.
   
4.The "Installing System" dialog will come up next. Grab a tasty beverage and watch the progress bar slowly creep across the screen. When installation is complete, hit Restart Now. The CD should eject, and remove it from the tray/slot at this time. Press enter to restart your computer. 

After install I ran the update manager a coupla times. This resulted in 263 updates or so. After installing these and rebooting I went to the hardware manager where I enabled the WiFi driver.

All went pretty smooth actually. I still got the wrong resolution though (1280x700 instead of 1024x768). All else seems very good.

---

