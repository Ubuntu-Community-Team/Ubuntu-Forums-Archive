---
title: "broadcom 4306 help please"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by mastermarcus355 on 2008-08-27
So I'm new to ubuntu and everything seems to be fine except my wireless. I've searched the forums and found multiple people with my same problem. My issue seems to be that I can't hardwire my laptop to the internet so I'm unable to get access to packages through synaptic and when downloading then in windows I can't seem to get them to work in ubuntu. I'm really excited about using ubuntu but with out access to the internet I'm unable to use it practically. I'm trying this on an hp laptop with a dual boot setup and have a broadcom 4306 wireless card. Any help is greatly appreciated so thanks in advance.:confused:

---

### Post by Crafty Kisses on 2008-08-27
Try this:
```

sudo su
apt-get install ndiswrapper-utils
ndiswrapper -i bcmwl5.inf
ndiswrapper -m
modprobe ndiswrapper
``` Make sure you're in the same folder as bcmwl5.inf (your windows driver) and bcmwl5.sys.

Then verify it installed and worked:

```

ndiswrapper -l
```Should say something along the lines of hardware detected and supported or whatever.

then, 

```

 nano /etc/modules.d/blacklist
```(or is it module(no "s").d?)
and add the line "blacklist broadcom43xx" to the end. Reboot and you should be on your way to glory.

On the side, I'd recommend you install network-manager-gnome (not just the "network-manager" that ships with Dapper). It works really well with wireless.

---

### Post by mastermarcus355 on 2008-09-05
aorry it took so long for me to get back on here I've been increadibly busy. Ok so now I've been tryin this and other ways and still nothing. The problem I am having is getting this system to see the packages. I download them (.tar, .gz, .tar.bz2, .tar.tar, .tar.dff) and then I try to unpackage them but it says it can't find the packages!! I have no idea what I'm doing wrong! I have no internet connection on the ubuntu laptop so I can't connect to any servers to get the packages through ubuntu it's self. PLEASE HELP THANKS!!!

---

### Post by Crafty Kisses on 2008-09-10
So I've found that there is a lot of ways you can get this particular card to work. First install this package: ```
sudo apt-get install ndisgtk
```
Then you need to find the Broadcom 4306 XP drivers, which you can get right [**here**]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?dlc=en&lc=en&os=228&product=433741&lang=en&cc=us&softwareitem=ob-26984-1"). 

After you have the XP drivers, find the **.inf** file in the package, and then open up **ndisgtk** you should see something like "Insert .inf file here" so obviously you want to put the .inf file in there, then click the install button.

After that, try this in the Terminal: ```
ndiswrapper -l
``` to make sure everything installed correctly. If you are still having problems after all this, you may want to try: ```
 sudo gedit /etc/modules.d/blacklist
```
Once the text-editor has popped up add the following line at the end:```
blacklist broadcom43xx
```Then after that, reboot and it should start working. If that doesn't work the card may not even be getting detected, so try this command and see if you get an output:
```
sudo pccardctl ident
```After that command, just hope you get something like this: ```
Socket 0:
    product info: "Atheros Communications, Inc.", "AR5001-0000-0000", "Wireless LAN Reference Card", "00"
    manfid: 0x0271, 0x0012
    function: 6 (network)
```
If you don't get anything back that means your Wireless card is not detected, and in that case I'll do more troubleshooting with you and see what we can do. For now try my steps and see if they work, they probably should work, but if they don't let me know.

---

### Post by mastermarcus355 on 2008-09-11
Great this seemed to work! Now it seems I have a new problem :-( The update manager said I had 272 updates so I proceded to dl them and when installing my computer froze on me. When I rebooted everything seemed fine..I typed in my username and password..then at the main screen my cursor was stuck! I could use the keyboard but it seemed that my touchpad wasn't working. Also there was an error that popped up...Instalation error - The configuration files for GNOME Power Manager were installed incorrectly please reinstall before configuring. I have no Idea what this means!

---

### Post by Crafty Kisses on 2008-09-11
If you can somehow get to a Terminal of some sort, try booting up into recovery mode, or press ```
Cntrl+Alt+F1
``` Then type the following:
```
sudo dpkg --configure -a
```
Then after that, try running: ```
sudo apt-get update
```
The last thing after you've done those two commands is: ```
sudo shutdown -r now
```
Let's see if that springs Ubuntu back to life. :)

---

### Post by mastermarcus355 on 2008-09-12
Thanks for the suggestions although I'm still stuck...I ran all the commands as you said but the error still pops up upen reaching the main page in ubuntu...Installation Error - The configuration files for GNOME Power Manager were installed incorrectly please see your computer administator. I should also add that I'm able to move the cursor at both the username and password screens. Again I have no Idea how to go about fixing this.

---

### Post by Crafty Kisses on 2008-09-12
Try the following, not sure what the package name is for the Power Management, but try this:
```
sudo apt-get remove --purge program_name
```

---

### Post by TSupra88 on 2008-09-12
your solution: [http://tsupra88.blogspot.com/](http://tsupra88.blogspot.com/)

---

### Post by mastermarcus355 on 2008-09-12
Thanks again for all the help codename! I too don't know what the package name for power manager is but I'm thinking it's gnome-power-manager. I'll give this new approach a try tonight when I get home from work.

---

