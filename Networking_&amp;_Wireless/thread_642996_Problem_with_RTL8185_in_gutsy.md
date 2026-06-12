---
title: "Problem with RTL8185 in gutsy"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by SegaFan on 2007-12-17
This is on a PC I have built, I have only just got it up and running and I have installed Ubuntu. It's a 32-bit AMD. Everything else works more-or-less fine.

My wireless network card is a Realtek RTL8185, and the driver is rtl8180. This driver came with the distro, I haven't set up anything myself. When connecting to my wireless network it completely locks up. It can see the network beforehand, but after I enter my WEP key as soon as it starts trying to connect it freezes, I can't do anything except reset.

NOTE: I am a complete beginner with Linux, searching these forums I found several people with problems with this card, for instance in:
[http://ubuntuforums.org/showthread.php?t=642360](http://ubuntuforums.org/showthread.php?t=642360)
[http://ubuntuforums.org/showthread.php?t=210958](http://ubuntuforums.org/showthread.php?t=210958)
[http://ubuntuforums.org/showthread.php?t=585712](http://ubuntuforums.org/showthread.php?t=585712)
[http://ubuntuforums.org/showthread.php?t=584046](http://ubuntuforums.org/showthread.php?t=584046)

It appears to be that I've got to install a new driver.

But... I have been using Linux for less than a day, so in short, I don't know what I'm doing! But this appears to be quite a common problem with that driver, and other people have managed to solve the problem to various extents. I was hoping someone could explain to me what I've got to do to get this working.

I tried the absolute beginner forum but didn't get very far, since this is a specialist problem that some people here have dealt with before I thought it would be better here.

---

### Post by lvleph on 2007-12-17
Okay there are a few things you need to do.
NOTE: I use tab alot so a directory name or file may not be exactly correct. I suggest using tab to complete file names and directories.
in a terminal
```
sudo apt-get install build-essential
```
then open /etc/modprobe.d/blacklist
```
sudo gedit /etc/modprobe.d/blacklist
```
and add the following to the bottom if it is not already there.
```

r8180
r8185
```
Then download the drivers and ndiswrapper
```
wget ftp://152.104.238.19/cn/wlan/RTL8185_6.1102.0702,UI_1.00.0006.zip
wget http://superb-west.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.50.tar.gz
```
once those have downloaded untar the ndiswrapper and install
```
tar -xvzf ndiswrapper-1.50.tar.gz
cd ndiswrapper-1.50
sudo make uninstall
make
sudo make install
```
Now that ndiswrapper has been installed, it is time to install the drivers.
I use the archive manager and extract the files in the Win2000 folder. There should be three of them. To install them after you extract them
```
sudo ndiswrapper -i net8185.inf
```
Check to see if it worked
```
ndiswrapper -l
```
should show you the installed driver.
Now activate the driver
```
sudo modprobe ndiswrapper
```
To get it to run at startup. Edit the modules file.
```
sudo gedit /etc/modules
```
and place the following at the bottom
```
ndiswrapper
```
Everything should work.

Once all that is done you can delete the extra folders and files that have been created in you working directory. To see those files type the following in terminal.
```
ls
```
I would save the ndiswrapper tar and the 3 drivers.

If this does nothing for you, please post your errors and results. I will try to help you when I am at my computer.

---

### Post by SegaFan on 2007-12-17
OK thanks a lot.

Didn't take long to get stuck though!

I typed:
sudo apt-get build-essential

and get (after entering my password):
E: Invalid operation build-essential

---

### Post by lvleph on 2007-12-17
Sorry I screwed that up.
```
sudo apt-get install build-essential
```

---

### Post by SegaFan on 2007-12-17
When I open /etc/modprobe.d/blacklist and add r8180 and r8185, do you mean I should type:
```
blacklist r8180
blacklist r8185
```
And then save it? That is what I've done, but I really want to be absolutely sure with what I'm doing.

And don't I need an internet connection to download the drivers? That's what I'm trying to get. If I'm required to download drivers from the internet the best I can do is download them on my Windows laptop and transfer them via memory stick.

---

### Post by lvleph on 2007-12-17
> **SegaFan said:**
> When I open /etc/modprobe.d/blacklist and add r8180 and r8185, do you mean I should type:
```
blacklist r8180
blacklist r8185
```
And then save it? That is what I've done, but I really want to be absolutely sure with what I'm doing.

And don't I need an internet connection to download the drivers? That's what I'm trying to get. If I'm required to download drivers from the internet the best I can do is download them on my Windows laptop and transfer them via memory stick.

Download the drivers however you need to. I assumed you had a wired connection sorry. You did the blacklist correctly from your description.
The one issue will be the directory you need to be in. If you transfer the drivers and ndiswrapper to your desktop you will need to move to that directory.
```
cd ~/Desktop
```
Then proceed from after the download drivers section.

---

### Post by Kiioro on 2007-12-17
I have the *exact* same problem. I'm trying this as soon as I get home from work, thank you ^10!

---

### Post by SegaFan on 2007-12-17
It works!! Thank you so much, lvleph, that was such a big help! So good to finally be able to use the internet on my new PC. I've learnt so much as well.

I won't mark it as solved just yet in case Kiioro has any problems.

---

### Post by Kiioro on 2007-12-18
Thanks...

Do I need the network manager for this? Because I uninstalled it (I had read in another thread that I would replace it with kwifimanager but it didn't work), This seems to have worked so far, at least, every step was confirmed. 

I'm not able to re-install it, I'm trying on the Add/Remove part. After saying that I need to reload the list, I do so, it seems to download something, but nothing happens. I click on "Network Manager" again and it prompts the same notice, claiming that I must reload the list, over and over again...

Or, if I don't need it, how can I input the password for my wireless connection?

---

### Post by lvleph on 2007-12-18
You could try using the LiveCD to reinstall the networkmanager. Insert the LiveCD and it should ask you if you want to use it as part of your repositories; click yes. If it doesn't ask you, go to synaptic package manager>>settings>>repositories. Somewhere in there you will see a selection to include a cd.  You don't need it, but I cannot remember how to do it on command line.

---

### Post by Kiioro on 2007-12-19
I tried but it won't allow me, it says:

E: Could not get lock /var/lib/apt/lists/lock - open (Resource temprarily unavailable)
E: Unable to lock the list directory

When I try to do it with the CD or from the internet directly... what am I doing wrong here?

---

### Post by lvleph on 2007-12-19
Either you are using apt-get already or you have synaptic open. If neither are in use and you are not updating your system there is probably something else wrong. I would do a search for you problem.

---

### Post by Kiioro on 2007-12-21
Aaaah, it worked! I had to move a few things (that I sincerely forgot now what was it, because I tried a bunch), but IT WORKED!

Thank you! =D>

---

### Post by swissjon on 2008-01-01
This worked for me.

I had problems with an RTL8185 card and wasted lots of time with the RTL8185 Linux driver on the Realtek site which is buggy and doesn't work.

I compiled the ndiswrapper V 1.50 as you suggested and it works fine.

Thanks

---

### Post by notiones on 2008-01-02
Thanks SagaFan. I couldn't get the Gutsy drivers to work at all and the Realtek drivers were spotty at best. Also for the ftp link to the drivers for I had none.

---

### Post by Tierial on 2008-01-09
I know this is slightly different, but I'm using a Linksys WPC11 v.4 on my Laptop and it freezes every time I connect to the wireless (loads a few seconds, locks with the flashing lights), and on the NDISwrapper page, I was directed to use the RTL8180L from Realtek, however, I downloaded this and put it in the NDISwrapper folder, and when I
```
sudo ndiswrapper -i net8180.inf
```
i get
```
couldn't open net8180.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.
```
does anyone have any idea?

(Using Gutsy xUbuntu [the lightweight installation?] on my Laptop)

---

### Post by notiones on 2008-01-09
If I am not mistaken, it sounds like you are running the command from the wrong directory. Change into the directory where you downloaded the files and run your command again.

---

### Post by JohnnyVW on 2008-01-10
> **notiones said:**
> Thanks SagaFan. I couldn't get the Gutsy drivers to work at all and the Realtek drivers were spotty at best. Also for the ftp link to the drivers for I had none.

First off...  This worked great for my Latitude with Xubuntu Gutsy and a Linksys WPC11 v4 card.  I was having the same locking up issues...

notiones, I had a similar problem come up.  One way to do it is (while in terminal) change directories to where you downloaded and expanded the drivers.

Type:

**sudo ndiswrapper -i ./NET8180.INF**

note the dot slash and all caps (it is case sensitive) 

I also found that I had to remove the old 8180 drivers before I could install the new one.  

I used:

**sudo ndiswrapper -r n8180**
**sudo ndiswrapper -r net8180**

Oh, my card uses the 8180 driver instead of the 8185 driver.  Change the above as necessary.

Hope this helps!

---

### Post by benjellos on 2008-02-03
I have same chipset wireless card and encounter the same problem.  I tried to follow steps exactly but it was early morning and I was half asleep.  I can't remember the exact errors I got last night but pretty sure I know I did something wrong.

I have two questions, hopefully someone can help.


[QUOTE=lvleph;3967740]Okay there are a few things you need to do.

then open /etc/modprobe.d/blacklist
```
sudo gedit /etc/modprobe.d/blacklist
```
and add the following to the bottom if it is not already there.
```

r8180
r8185
```

Do you need to have the blacklist before r8180 and 8185?
 
Running ndiswrapper -l
netr8180 : driver installed
        device (10EC:8180) present (alternate driver: r8180)

I've added ndiswrapper to my modules
I've blacklist both r8180 and r8185

I still get the same problem, when connecting to my wireless, it hangs.

I'm running a IBM T22, Gusty 7.10, Trendnet wireless card.

---

### Post by Poliwop on 2008-02-07
I've been having the same problem, with a bit of a twist.

I'm at a college campus and there are two networks here, one guest network (unencrypted) and one encrypted network which, if I recall correctly, uses PEAP and 802.11x, although I'm honestly not entirely sure what that means.  I can get on the unencrypted network just fine.  But when I attempt to connect to the encrypted network, the computer freezes and I need to do a hard reboot.

I've followed the instructions here (thanks!) and I get no error messages, but it does not fix the problem.  Well, actually, it just says "manual config" and doesn't give me the option of finding a network using Network Manager's GUI.  So I'm not sure if it would freeze if I tried to connect.

Does it matter what directory I install ndiswrapper or the drivers from?  Also, there are drivers for each Windows OS, in the instructions Win2000 was used, does it matter which I use?

Thanks for the help.

---

### Post by Rob V on 2008-02-07
Another, satisfied customer here. Thanks.

It worked first time after I'd spent about 4 hours solid trying other walkthroughs and reading other threads.

:)

---

