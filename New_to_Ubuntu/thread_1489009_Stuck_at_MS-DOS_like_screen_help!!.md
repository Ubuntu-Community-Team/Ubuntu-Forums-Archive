---
title: "Stuck at MS-DOS like screen help!!"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by davepimp00 on 2010-05-20
I just installed Ubuntu 10.04 from my Vista.  i installed and erased the entire hard for ubuntu.  i installed it fine and was able to do whatever on my new ubuntu system.  after some time on the system i restarted my computer.  as it was booting it took me to this "MS-DOS like" screen and asked me for my SN and password.  i entered it and it just said some stuff and said welcome to ubuntu.  but im just stuck in this black and white hell and cant get into ubuntu.  AHHH HELLP IM NOOOOOB!!!

---

### Post by quinnten83 on 2010-05-20
try pressing ctr-alt-F7.
Any change?

---

### Post by davepimp00 on 2010-05-20
well it no longer has a command line.  it says something about starting post fix mail transport

---

### Post by davepimp00 on 2010-05-20
Pressing Ctrl+Alt+f1-f5 takes me to a new command line screen.  i dont know where im stuck at is called, it just looks like MS-Dos.  it has the command line like it does inside of "terminal" and is waiting for me to type.  this is my first reboot since installing also.

---

### Post by tad1073 on 2010-05-20
> **davepimp00 said:**
> Pressing Ctrl+Alt+f1-f5 takes me to a new command line screen.  i dont know where im stuck at is called, it just looks like MS-Dos.  it has the command line like it does inside of "terminal" and is waiting for me to type.  this is my first reboot since installing also.
ctrl+alt+f7

---

### Post by posburn on 2010-05-20
Perhaps this is a stupid question, but did you by any chance unintentionally install the server, minimal, or alternate CD versions of Lucid Lynx?

---

### Post by tad1073 on 2010-05-20
> **posburn said:**
> perhaps this is a stupid question, but did you by any chance unintentionally install the server, minimal, or alternate cd versions of lucid lynx?
+1

---

### Post by davepimp00 on 2010-05-20
not stupid, and very possible considering how noob i am.  but im pretty sure i didnt install anything other than the OS itself.

---

### Post by Peter09 on 2010-05-20
try typing 
```
startx
```
when you get to the command line prompt

---

### Post by davepimp00 on 2010-05-20
sorry, yes i did push alt ctrl f7 and it was no change.  but pushing ctrl alt f1 - f5 took me to other screen that said tty1 tty2 tty3 ect

---

### Post by cph05a on 2010-05-20
If you have a terminal, log in and try
```
sudo /etc/init.d/gdm restart
```

---

### Post by posburn on 2010-05-20
You should try Peter09's and cph05a's suggestions. If you do and nothing happens, or you get an error, then I suspect you may have one of those other versions I mentioned installed.

The Server, Minimal, and Alternate versions of Ubuntu are bare-bones installations which generate a version of Ubuntu with no graphical interface; they are "the OS itself", just with no graphical shell on top of it.

---

### Post by Peter09 on 2010-05-20
Hi Posburn,
I think the OP said in his first post that he had a normal graphical interface when he first booted up. However if I am wrong he should be able to get going by installing gnome-desktop.

---

### Post by posburn on 2010-05-20
Peter09 - right you are. My mistake. Perhaps he should try

```
sudo apt-get install ubuntu-desktop
```

at the terminal.

---

### Post by ryan858 on 2010-05-20
Yes, try** startx** and then try 
```
sudo start gdm
```or
```
sudo service gdm start
```

---

### Post by davepimp00 on 2010-05-21
Sorry guys, inputting these codes only runs the system through a test/ and sends me right back to square one.  Im going to try re-installing and seeing if the problem persists.

---

### Post by davepimp00 on 2010-05-27
so yes i am still getting the same problems as before.  after a few days of troubleshooting im still finding my self in the same situation.  only now ive narrowed it down to this.  My Nvidia card is a GeForce 6150SE nForce 430.  only when i install the drivers for the card and restart am i then not able to access the desktop.  i was told to go to terminal and type "sudo nvidia-xconfig" before restarting. i did this and i am still getting the same problem.  

while i cant get into my desktop i have to purge nvidia from my computer using "sudo apt-get --purge remove nvidia*-"  after i restart i can get back to desktop and my normal interface using "low resolution" option.  

im using 10.04, and i have been reading alot of forums on this and i still cant seem to figure it out.  im very new and its possible i need this broken down so a child could understand it.  im doing my best and learning along the way, its just crazy to me that installing a nvidia driver is causing this much trouble.  help?

---

### Post by pzkfw on 2010-05-27
Try downloading the drivers straight from nvidia's website.
[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)


Ubuntu comes with ntfs-3g installed right?  if not apt-get install ntfs-3g
If you can't get on the internet from that computer, copy the right drivers to a flash drive from another pc.  Once you connect the flash drive it should be auto mounted.  Look in /media/ for /disk/ (or the name of the flash drive mfg.) or /mnt/.

get to the directory using cd.  ie cd /media/disk and then type ls or dir.
The nvidia drivers are an .sh script.  Get root priveliges and type killall x.
then sh nameofdriver* (use the asterisk to not have to type out the whole thing).
It should then install the drivers through their wizard

---

### Post by oldfred on 2010-05-27
I have a newer nvidia card, not sure which driver is best for yours.

I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.

---

### Post by davepimp00 on 2010-05-28
> **oldfred said:**
> I have a newer nvidia card, not sure which driver is best for yours.

I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.

i have seen you post on another forum, i tried it and it did not work for me.i could of possibly done it wrong though.  when i booted from CD i hit space bar at the "keyboard = Human" screen and then i hit F6.  i checked nomodeset and hit enter and nothing happened, so i hit escape.  then there was a line there and i saw "quiet splash" i deleted it and typed nomodeset.  i restarted and got nothing but blank screen.  i had to then reinstall again because i couldnt access the internet, so now i just run without a driver for my graphics card.

---

### Post by Beanmonster on 2010-05-28
Dave,[ this solution]("http://ubuntuforums.org/showthread.php?p=9376370#post9376370") worked for me. Give it a try. :)

---

### Post by Jakiejake on 2010-05-28
> **davepimp00 said:**
> Pressing Ctrl+Alt+f1-f5 takes me to a new command line screen.  i dont know where im stuck at is called, it just looks like MS-Dos.  it has the command line like it does inside of "terminal" and is waiting for me to type.  this is my first reboot since installing also.

That is Linux it is a terminal

---

### Post by cazzie on 2012-08-26
):P> **davepimp00 said:**
> sorry, yes i did push alt ctrl f7 and it was no change.  but pushing ctrl alt f1 - f5 took me to other screen that said tty1 tty2 tty3 ect
did this work for you, because i have same problem and i know nothing, thanks

---

