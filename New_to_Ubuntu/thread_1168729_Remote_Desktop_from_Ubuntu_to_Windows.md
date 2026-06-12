---
title: "Remote Desktop from Ubuntu to Windows"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by ridergroov1 on 2009-05-24
Hi folks.  I'm trying to get into using Linux more here but still need to remote desktop into my Vista machine periodically.  Can this be done from Ubuntu 9?  I have all the updates installed.  Thanks.

---

### Post by mellowd on 2009-05-24
Yes, install terminal server client in ubuntu.

Make sure Vista is set up as well to be rdp'd into

---

### Post by MockY on 2009-05-24
I strictly use rdesktop. It is already installed on your machine.
Once you have set up the parameters you like, make a launcher and put it on the desktop or in the menu. For my laptop, I use the following:
```
rdesktop ipnumbertoserver -0 -u username -p password -g 1275x743
```
-0 (that's a zero) tells rdesktop to use the console session, which is probably what you want if you just want to manage the windows machine.
The other flags are pretty self explanatory. The size of the window can be changed to whatever you want to fit your screen. You could instead of the -g flag followed by the size, use -f in order to use full screen. But you have to logoff from the Windows machine once you are done in order to get back your Ubuntu desktop.
Just type
```
rdesktop --help
```
to get a list of everything redsktop is capable of.

If you don't want to fiddle with any flags, rdesktop works with defaults as well
```
rdesktop ipnumber
```

---

### Post by ridergroov1 on 2009-05-24
Is there a way to make a shortcut for the desktop for this?  Also, I use custom port numbers.  Does this support this?  Can I only launch this through terminal?  Thanks for th newb help.

---

### Post by NTolerance on 2009-05-24
Gnome-RDP makes all this very easy, no terminal commands necessary.  I also find it superior to Terminal Server Client, which hasn't been updated in a long time.

```
sudo apt-get install gnome-rdp
```

After installing you can find it in the Applications -> Internet menu.

---

### Post by MockY on 2009-05-24
> **ridergroov1 said:**
> Is there a way to make a shortcut for the desktop for this?  Also, I use custom port numbers.  Does this support this?  Can I only launch this through terminal?  Thanks for th newb help.

If you read my post again properly, you will see that I did say you can:  > make a launcher and put it on the desktop or in the menu 
If you don't know how, simply right-click on your desktop and select Create Launcher. Name it what ever you want by typing the name in the Name box (this will appear underneath the icon). Then just type in the command string you want to use in the Command box. To use what I had in the first post, just paste the following in to the Command field (changing the entires to fit your server or machine you want to connect to.)
```
rdesktop ipnumbertoserver**:port** -0 -u username -p password -g 1275x743
``` You can also click on the icon to change the default launcher icon to something you want. Once done, hit OK, and your new "shortcut" will be visible on the desktop. Just double click on it and it will connect to your server if you changed the string to reflect your server. If you rather have a menu icon to click on (under Internet or something), start Alacarte, and drag the icon you just made to the menu you want it in.
Notice I added a the port to the ip string. This can be any port you want. I use many different ports on multiple Windows servers (I have never used the default/standard port).

Again, everything is explained if you type rdesktop --help in terminal. This includes flags for print/device/sound redirection and all other options rdesktop supports.
Using a GUI interface to connect to your servers just adds extra steps, as well as they are bloated and often disconnects you. Making custom launchers tailored for your needs is the best way to go.
Besides, once you have made a launcher like this successfully, making it again is not particularly hard. I have an entire menu entry in my Gnome Menu dedicated to all my rdesktop (or RDP) launchers, right under Internet. Navigate - Click - Auto connect. Works flawlessly, quickly, and totally without any bloated GUI, whioch in this case is completely unnecessary.

---

### Post by tmsandeep on 2010-11-19
> **ridergroov1 said:**
> Hi folks.  I'm trying to get into using Linux more here but still need to remote desktop into my Vista machine periodically.  Can this be done from Ubuntu 9?  I have all the updates installed.  Thanks.
Hey guys its pretty easy to control your ubuntu desktop from windows pc. Just you need to install any VNC viewers like windowsVNC viewer or tightVNC viewer. After that you hust need to give static IP as server address in icon that appears . Thats it you can access your ubuntu desktop. But be sure that  in ubuntu system you need to enable Remote desktop access. That icon you can see in PREFERENCES

---

