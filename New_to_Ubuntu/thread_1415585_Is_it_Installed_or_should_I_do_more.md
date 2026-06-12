---
title: "Is it Installed or should I do more?"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by yogiman on 2010-02-25
I downloaded Ubuntu netbook remix eee iso and used Universal USB program to install on SD card. This is my first time, ever. I emptied the 2G SD card and used the program to format correctly. The install seemed to take place with the black box and all the green type going on for half hour. Then I got message that it was successful. But when I open the Ubuntu icon I can't find what it is I need to do to get the system booted. If I click on the Ubuntu program icon It tells me that Installation will start. I don't know if this is what I am supposed to do. Should I not Install? Would there be risk of overwriting my Windows XP? Does it give me option to partition after? Does it give me option to Install on SD or HD? I thought it was installed already but I'm not sure as I have never done this before and I am a Mac veteran who doesn't even know WIndows very well. Thank you for your help and I look forward to using this OS for many years to come.

---

### Post by cap10Ibraim on 2010-02-25
It will give you the option to partition but I don't think it will show the SD there

---

### Post by 3rdalbum on 2010-02-25
What you just did is put Ubuntu onto your SD card.

Ubuntu is not a program that you run on Windows, it's an operating system. So shut down your computer and go into your BIOS settings (i.e. "Press Tab to enter SETUP") and set your computer to start up from the SD card.

Now Ubuntu will load.

---

### Post by NefariousNobo on 2010-02-25
Just thought that I would mention: It's highly unlikely that Ubuntu could delete your Windows XP while running under it, so if you want to, go ahead an install. The way you'd probably want to do it *full* is to reboot and select the SD card as your boot device.

---

### Post by mikeyphi on 2010-02-25
Which Eeepc do you have?

When you power-on do you have any boot options?

Try pressing 'Esc' key after power-on, What options show?

It's the 'Ubuntu icon' that sounds strange! If you have installed Ubuntu you should see either a log-on screen or the remix desktop with several icons. If you are looking at the 'live-CD' you should see 2 icons, a folder called Examples and an icon called 'install Ubuntu'

Have you, by any chance, installed Ubuntu into your XP partition?

You need more that 2GB for the full remix OS, look here for info:
[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

---

### Post by yogiman on 2010-02-25
> **mikeyphi said:**
> Which Eeepc do you have?

When you power-on do you have any boot options?

Try pressing 'Esc' key after power-on, What options show?

It's the 'Ubuntu icon' that sounds strange! If you have installed Ubuntu you should see either a log-on screen or the remix desktop with several icons. If you are looking at the 'live-CD' you should see 2 icons, a folder called Examples and an icon called 'install Ubuntu'

Have you, by any chance, installed Ubuntu into your XP partition?

You need more that 2GB for the full remix OS, look here for info:
[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)


No, there are no boot options on startup.

Nothing happens on pressing 'esc'

Looks like I only put it on the SD card without installation. But I don't really understand. It took half hour to go onto the SD I thought that was installation. If it is installed on XP partition I am unaware of it. There was no option to partition either.

I suppose I should just click the icon and choose install and see what happens. I just don't want to make any irreversible mistakes.

---

### Post by yogiman on 2010-02-25
> **3rdalbum said:**
> What you just did is put Ubuntu onto your SD card.

Ubuntu is not a program that you run on Windows, it's an operating system. So shut down your computer and go into your BIOS settings (i.e. "Press Tab to enter SETUP") and set your computer to start up from the SD card.

Now Ubuntu will load.

I rebooted holding down the 'Tab' key and it just opened 'Windows' as usual. No difference.

---

### Post by RedDog1 on 2010-02-25
Actually, you have to press F2 on the EEEPC when you are starting the machine to access the panel where you choose where the pc boots from. I just loaded Ubuntu on my EEEPC, and that is what I had to do to load Ubuntu.

---

### Post by yogiman on 2010-02-25
> **NefariousNobo said:**
> Just thought that I would mention: It's highly unlikely that Ubuntu could delete your Windows XP while running under it, so if you want to, go ahead an install. The way you'd probably want to do it *full* is to reboot and select the SD card as your boot device.

The icon that is in drive 'D' which is the SD card is called 'wubi' When I click it is asks me to install with passwords and all. No option for partition. I don't know how to reboot to SD card or anything else for that matter. I held "tab' during startup but nothing changed. I started the Install but cancelled it because I want to do it *full* as you suggested. I'm wondering why I didn't get option to partition?

---

### Post by mikeyphi on 2010-02-25
> **yogiman said:**
> 
I suppose I should just click the icon and choose install and see what happens. I just don't want to make any irreversible mistakes.

If you do that it will want to install somewhere - but obviously not on the SD card..... You should get an option of where to install but I would be concerned about damaging your XP install.

Consider this: Get a larger SD card - say 8GB, and use the USB installer to install Ubuntu to the SD card, you can then boot Ubuntu from the SD card.

Note that you need to be able to choose how to boot: USB drive: SD card: other drive: as required.
Are you able to access your Boot options?

You didn't mention which Eeepc you have?

---

### Post by yogiman on 2010-02-25
> **NefariousNobo said:**
> Just thought that I would mention: It's highly unlikely that Ubuntu could delete your Windows XP while running under it, so if you want to, go ahead an install. The way you'd probably want to do it *full* is to reboot and select the SD card as your boot device.

I could not select the SD as boot device. Probably just don't know how. I am used to Mac and this is my very first Windows computer. I have had it for one week. Don't know much about anything. Also when it gives option for Install it says that it is 17GB with option to change the size more or less. I suppose if I choose 24GB it will operate better because of more space?

It also gave me option to choose 'Ubuntu', 'Ubuntu netbook remix' and 6 or so others. I downloaded the 'netbook remix and figure I should choose that. But not clear on why the options.

---

### Post by yogiman on 2010-02-25
> **mikeyphi said:**
> If you do that it will want to install somewhere - but obviously not on the SD card..... You should get an option of where to install but I would be concerned about damaging your XP install.

Consider this: Get a larger SD card - say 8GB, and use the USB installer to install Ubuntu to the SD card, you can then boot Ubuntu from the SD card.

Note that you need to be able to choose how to boot: USB drive: SD card: other drive: as required.
Are you able to access your Boot options?

You didn't mention which Eeepc you have?

Sorry all. I have the eee PC 900HD. I am getting a 32GB high speed SD for this purpose. I still thought I should run it on the HD but did not decide that yet. 

So someone else said I could not damage the XP install but you are concerned. I am concerned because I don't know. Looks like it was going to do some kind of install, seemed safe but I stopped it.

---

### Post by yogiman on 2010-02-25
> **RedDog1 said:**
> Actually, you have to press F2 on the EEEPC when you are starting the machine to access the panel where you choose where the pc boots from. I just loaded Ubuntu on my EEEPC, and that is what I had to do to load Ubuntu.

I pressed the F2 during the entire reboot and still no change.

---

### Post by mikeyphi on 2010-02-25
> **yogiman said:**
> The icon that is in drive 'D' which is the SD card is called 'wubi' When I click it is asks me to install with passwords and all. No option for partition. I don't know how to reboot to SD card or anything else for that matter. I held "tab' during startup but nothing changed. I started the Install but cancelled it because I want to do it *full* as you suggested. I'm wondering why I didn't get option to partition?

Ah!! Now it makes sense!!
wubi is the installer to install Ubuntu within windows....go ahead and install (as long as you have the space in your windows drive)
the installation will put the OS into windows and give you an icon on your normal windows screen from where you start the OS.

---

### Post by RedDog1 on 2010-02-25
> **yogiman said:**
> I pressed the F2 during the entire reboot and still no change.
 
Hmmm, that is odd. Press F1, and search for boot device. That should then tell you what to do to get to the boot screen on your pc. That is what I did, and my eeepc told me to press F2 once the machine started up. Then, when I got the gray Asus screen, I pressed F2 again, and got to the screen where you choose where to boot from. I hope that helps.

---

### Post by yogiman on 2010-02-25
> **mikeyphi said:**
> Ah!! Now it makes sense!!
wubi is the installer to install Ubuntu within windows....go ahead and install (as long as you have the space in your windows drive)
the installation will put the OS into windows and give you an icon on your normal windows screen from where you start the OS.

Great! Wish I knew that earlier. I did start the Installation but stopped it because I was afraid of doing the wrong thing. That was the wrong thing to do, I shouldn't have stopped it. So I tried again now realizing that everything was ok. But to do it again it told me to uninstall. I did that. Now on re-installing I choose 30GB space instead of 17 default. I get the error right away saying: An error occurred. Cannot downoad the metalink and therfore the ISO. For more information please see the log file: c:\docume~1\pauljj~1\locals~1\temp\wubi-0.10ubuntu1-rev160log.

I have not the knowledge to access this file. New to Windows as of last week. So seems I messed something up by stopping the installation, of all things.

---

### Post by linuxman94 on 2010-02-25
> An error occurred. Cannot downoad the metalink and therfore the ISO. For more information please see the log file: c:\docume~1\pauljj~1\locals~1\temp\wubi-0.10ubuntu1-rev160log.


Copy & paste c:\docume~1\pauljj~1\locals~1\temp\wubi-0.10ubuntu1-rev160log into the windows explorer address bar and post what it says.

---

### Post by yogiman on 2010-02-25
> **linuxman94 said:**
> Copy & paste c:\docume~1\pauljj~1\locals~1\temp\wubi-0.10ubuntu1-rev160log into the windows explorer address bar and post what it says.

I'm sorry. I'm not only new to Linux but I am new to Windows. I am a veteran Mac user who is strongly considering leaving. 

I found this thing called "Windows Explorer" and could not find an address bar. So I pressed on "Search" and it came up with nothing. "Search is complete. There are no results to display."

Everything was installing fine when I first pressed Install. I botched it. I thought it needed a partition to Install. Apparently this version boots up from within WIndows. When I decided to stop the Install it was already going for a few seconds and I had to Uninstall in order to Install again. Something got confused and seems now I made a mess where there was none.

---

### Post by -memetic- on 2010-02-25
The little manual that came with your Eee explains how to boot to a sd (or usb) in a couple easy steps. After you do that use UNetbootin to put the linux iso on your sd card. Then, reboot and the linux live will load and from there you can install (there is an install icon on the desktop). If you follow these instructions I can help you.

---

### Post by yogiman on 2010-03-02
> **-memetic- said:**
> The little manual that came with your Eee explains how to boot to a sd (or usb) in a couple easy steps. After you do that use UNetbootin to put the linux iso on your sd card. Then, reboot and the linux live will load and from there you can install (there is an install icon on the desktop). If you follow these instructions I can help you.

I read through that entire little book. In fact there where 2 of them, almost identical in information. There was nothing about booting to the SD card.

---

### Post by yogiman on 2010-03-02
> **yogiman said:**
> I'm sorry. I'm not only new to Linux but I am new to Windows. I am a veteran Mac user who is strongly considering leaving. 

I found this thing called "Windows Explorer" and could not find an address bar. So I pressed on "Search" and it came up with nothing. "Search is complete. There are no results to display."

Everything was installing fine when I first pressed Install. I botched it. I thought it needed a partition to Install. Apparently this version boots up from within WIndows. When I decided to stop the Install it was already going for a few seconds and I had to Uninstall in order to Install again. Something got confused and seems now I made a mess where there was none.

Linuxman, did I do the right thing or did you give up on me?

---

### Post by yogiman on 2010-03-03
Thanks everyone! Solved!

I went to Microcenter for assistance because I knew there was nothing in the books about booting etc. The Techy confirmed that it is not in the book. We found out that I did not even know how to shut down a Windows Machine! I was pushing the button like on my Mac and thinking that the Machine was shutdown but it was not. I never ever had it shut down. So on rebooting I chose to Install Ubuntu and it worked!

Said I was a rank beginner.....

---

### Post by yogiman on 2010-03-19
I finally got the Ubuntu Installed. Everything seemed fine. I left for India and have been using Windows. Now after a couple of weeks I tried to open Ubuntu with no success. I keep getting messages like "killed" and "terminated" I don't know what this all means but it doesn't seem good.

---

