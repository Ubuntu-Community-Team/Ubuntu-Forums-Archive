---
title: "Ubuntu freezing on boot"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by psychx on 2010-07-19
**Ubuntu 10.04 LTS** - Problem with booting/video card drivers:

I am working on a friend's computer. His video card, driver, and monitor were not operating quite right. Even after activating the recommended hardware driver, it would not display the screen resolution correctly. It would be too large, but the video card is able to handle it - and the resolution we were running is the recommended/native resolution for the monitor.

Here is the specifications of each:
Monitor: Vizio 32" V032E
Video Card: nVidia GeForce 7900 GS
Original Driver: 17x.xx (I can't remember the exact version)
Updated Driver: 256.35 (This is the driver that we attempted to install)

I downloaded the driver, which was a .run file. I attempted to run it via Terminal with the following command: ```
sudo sh /home/username/Downloads/nvidiadriver.run
```

Then it gave me an error about the runlevel. I found online that to fix this, I would have to disable the GUI then edit the config file and change a line. So here is what I did:

1. Ctrl+Alt+F1
2. cd /etc/init/
3. cp gdm.conf gdmbackup.conf
4. cd
5. sudo vi etc/init/gdm.conf
6. I then went to the line: stop on runlevel [016]
7. Deleted the 6] ending of the line
8. Hit shift A to append the end of the line
9. Added 26]
10. This appended the line to: stop on runlevel [0126]
11. ZZ in terminal which saved the file and exited the vi program.
12. sudo reboot

Then the system restarted and started the Ubuntu loading screen. It sat at this screen and did not load Ubuntu. We rebooted the computer via the power butten. It then loaded with the following text:
```

Ubuntu 10.04 LTS lgoat-desktop tty1

lgoat-desktop login  [    14.152223] hci_cmd_task: hci0 command tx timeout
[    14.655861] sd 4:0:0:2: [sde] Assuming drive cache: write through
[    14.659110] [sde] Assuming drive cache: write through
[    14.665480] [sde] Assuming drive cache: write through

```

This is where I am now. Any ideas of what I should do from here?

---

### Post by jtarin on 2010-07-19
> Even after activating the recommended hardware driver, it would not display the screen resolution correctly. It would be too large, but the video card is able to handle it - and the resolution we were running is the recommended/native resolution for the monitor.
Reverse your Overkill......use [Xrandr]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by psychx on 2010-07-19
Sorry, but what exactly do you mean by this? I read a little bit about Xrandr, but don't see any about resetting overkill. I'm still new to Ubuntu and not sure what to do from here.

Edit: Also, I did back up the config file - is there any way to load up Terminal and just replace the file?

---

### Post by jtarin on 2010-07-19
As I understand your initial post you were having problems with resolution...correct or not? If not disregrd my link and post. if yes then I would undo what you have done and attempt correcting your problem with Xrandr.If you decide to use Xrandr please read the documentation thorughly. The term overkill refers to your iniial attempt at the problem by throwing more at it than need be.;) 

What config file did you back up and what did you name it? ```
sudo nano filename.conf
```will open the file and then save as original name.[Basic Nano functions ]("http://mintaka.sdsu.edu/reu/nano.html")for your purpose.

---

### Post by psychx on 2010-07-21
Well, changing the resolution wasn't what caused the problem - in my opinion. I wasn't ever able to actually change it to what I wanted to. I was trying to go for 1280x720 and it was not showing up. What caused the problem was diabling the server and installing a new nVidia driver. After rebooting via Terminal, is when it froze. It is freezing at the Ubuntu loading/welcome screen - before it gets to the login prompt.

---

### Post by jtarin on 2010-07-21
> **psychx said:**
> Well, changing the resolution wasn't what caused the problem - in my opinion. I wasn't ever able to actually change it to what I wanted to. I was trying to go for 1280x720 and it was not showing up. **[COLOR="Red"]What caused the problem was diabling the server and installing a new nVidia driver[/COLOR]**. After rebooting via Terminal, is when it froze. It is freezing at the Ubuntu loading/welcome screen - before it gets to the login prompt.Your problem, as you state it,  initially being was that you could not obtain a resolution of 1280x720, so then you proceeded to disable the server (your words) and install a new nvidia driver.I said to undo these actions and use Xrandr to solve your resolution problem.**During boot up try pressing esc see if there is a previous kernel to boot from???**, if not then your going to need to boot from the install DVD and try to repair your system using the "Try Ubuntu" level of the DVD. [Go to this page]("https://help.ubuntu.com/community/Grub2") and scroll down until you find the Title:**Reinstalling from LiveCD**.From that point it shows you several ways to gain access to your borked system. Use one of these to correctly reinstall the driver.

---

### Post by psychx on 2010-07-21
Yeah, I thought that's what Ctrl+Alt+F1 did - was disable the GUI/Xserver. I could be wrong. When I get back over there I will check kernal upon boot. If I'm able to get into the GUI I will use Xrandr to change the resolution. If we need to format, that's fine - but hopefully this will work fine.

---

### Post by jtarin on 2010-07-21
Note my edit on my post above

---

### Post by k3lt01 on 2010-07-21
> **jtarin said:**
> **During boot up try pressing esc see if there is a previous kernel to boot from???**Talk about Overkill, you shouldn't need to boot to a previous kernel, especially if (and you don't say if it is or not) it is a new install (if its a new install you would probably only have 1 kernel anyway). Reboot and select recovery mode in GRUB for the latest kernel, then FailsafeX, and then select low graphics mode. Then see if the resolution is ok and/or adjustable.

---

### Post by psychx on 2010-07-21
Ok, I will try both. Thanks, guys!

---

### Post by jtarin on 2010-07-21
> **k3lt01 said:**
> Talk about Overkill, Maybe, but then I'm not a Grub expert coming from Slackware. Grub was never my preferential way of booting.Your method could possibly work too....if

---

