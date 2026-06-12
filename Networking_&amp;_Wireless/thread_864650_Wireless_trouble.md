---
title: "Wireless trouble"
date: 2008-07-19
forum: Networking &amp; Wireless
---

### Post by Tanith12 on 2008-07-19
Well i am a new guy at this stuff and am tired of my vista dieing and deleting all of my stuff, so i decided to try ubuntu out, one of the issues i am having is connecting to the internet from the ubuntu OS, i ran a hardware check (cant remember what its really called) and it recognized my wireless card, but when i try to connect to the internet it just tries to connect then the network icon disappears.  My home network is not recognized, and its is a linksys router with WEP 128 bit, and my card is a broadcom card (cam in my HP Pavilion dv2000 laptop).  If anyone can provide some solution or anything it would be greatly appreciated.  (also i know this problem shouldnt be in this section but sometimes when i boot ubuntu i get to like a command propt screen where i can type help to list off what i can type anyone know why???)

Thanks

Will

---

### Post by falcon61102 on 2008-07-19
Could you go to your terminal by clicking on Applications>Accessories>Terminal and type in:
```
lshw -C network
```
Then post the output here.

---

### Post by Tanith12 on 2008-07-19
this is what i get

 *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:00:00:1a:73:60
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by falcon61102 on 2008-07-19
Ok... It looks like you need to install the drivers for your wireless card.  Are you currently connected through a wired connection in Ubuntu or are you using another computer to access the internet?

---

### Post by Tanith12 on 2008-07-19
I am connected with a different computer, but the computer with ubuntu i can switch to vista and use internet on it as well

---

### Post by falcon61102 on 2008-07-19
Its actually faster if you have two computers and they are close enough to go between them instead of constantly rebooting.  But either way you're going to have to download your drivers and place them on a flash drive or something similar so that you can access them in Ubuntu.

There is a great HowTo on the process to install your drivers.  I use that and a couple other places for reference but here is the link for that:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

And based on your post earlier, the link to download your drivers is:
[ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe)

Just download those and copy them into Ubuntu and I can help walk you through a couple other places since you won't have internet access in Ubuntu.

---

### Post by Tanith12 on 2008-07-19
This is quite confusing (the walkthrough page) im having trouble finding the part i need to follow, i downloaded the file you linked and already put it on ubuntu im sorry im so technically challenged on ubuntu!

---

### Post by falcon61102 on 2008-07-19
That's fine, give me a minute and I'll clarify it a lot.

Also, one more download... download this quick while you're waiting and it will make things go easier.

[http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.53.tar.gz)

---

### Post by falcon61102 on 2008-07-19
Once you have both of those somewhere that you can access in Ubuntu.  Lets start the install process.

Create a folder in your home directory and copy them both there.  Go to Places>Home and when it opens up the File Manager, just creat a folder Drivers.  Copy those two files to that folder.  Right click on both files and click Extract Here.  That will extract them so that we can install them.  To make the next step easier, you can rename the ndiswrapper folder and take away all the numbers so it just says ndiswrapper.

Go to your terminal and type:
```
cd Drivers/ndiswrapper*
sudo apt-get install ndiswrapper

```

That should install ndiswrapper for you.  Now to the drivers.  Using the cd command, change directories to the one containing your drivers, it will be the other folder that was created when you extracted those two files.  Should be:
```
cd ~/Drivers/sp34152
```
But it may have named it different.  Then run the following commands.  Explaination below.
```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

The first command is actually going to install your driver.
The second verifies that it has been installed and the next couple load the drivers and then the last ones are all configuring ndiswrapper.

You should now be able to see your wireless access points by clicking on the network manager in the upper right hand corner of the desktop.

If not, run
```
lshw -C network
```
And post the results.

---

### Post by Tanith12 on 2008-07-19
Thank you so much! Now hopefully ill be all ready to use the interweb :P

---

### Post by falcon61102 on 2008-07-19
Save that thanks until we get it working... :)

Also, you may need to have your liveCD in your drive for the install of ndiswrapper if it needs any additional packages

And if you are getting errors installing ndiswrapper, we can install an older version that will still work.
Go to System>Administation>Synaptic Package Manager

Right in the big box on the right and just type "ndis".  It will bring you to that section and look for "ndiswrapper-utils-1.9" and hit the check box to install that.  It will prompt you to install some other packages as well, just go along with it.  That should do it.

---

### Post by Tanith12 on 2008-07-20
Ok so after trying it several times, i get several issues in the process, when i put in the first code is says directory not found, and the file with my driver i cannot extract it like the ndiswrapper file, what am i doing incorrect?  I make the folders in my home area as you say now im not sure whats going wrong

---

### Post by Tanith12 on 2008-07-20
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper
will@will-laptop:~/Drivers/ndiswrapper$ cd ~/Drivers/sp34152
bash: cd: /home/will/Drivers/sp34152: No such file or directory


Thats what it says exactly

---

### Post by Tanith12 on 2008-07-20
totally didnt see your reply on the second page :P ill try that now

---

### Post by Tanith12 on 2008-07-20
i dont seem to have a ndis file in the synaptics package manager, i did the install myself ( i opened something from vista and installed it in the new partition i had maybe i missed a step and screwed myself over??)

---

### Post by falcon61102 on 2008-07-20
If  you run a search in the package manager using "ndis" it should come up.

---

### Post by Tanith12 on 2008-07-20
Nope, nothing pops up unless i search specifically under packages (the last search option) and then that file allows me to do nothing

---

### Post by falcon61102 on 2008-07-20
What happens when you type:
```
ndiswrapper
```
in the terminal?

---

### Post by Tanith12 on 2008-07-20
i get the following

will@will-laptop:~$ ndiswrapper
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found

then i typed what it told me to and got

will@will-laptop:~$ sudo apt-get install ndiswrapper-common
[sudo] password for will: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndiswrapper-common
will@will-laptop:~$

---

### Post by falcon61102 on 2008-07-20
Ok.... Sometimes the package manager doesn't load all the packages for some reason and you need to manually reload it. Try this:

Make sure you LiveCD is in your drive.  

Then go to the Synaptic Package Manager.  

I believe it's under File, but in one of the menus if gives you the choice to add a CD to the repostitories.  Click that and it will scan the cd.  Once that completes, hit the Reload button.  

Now all the packages available from your LiveCD should be available to install.  Once again, run a search for ndiswrapper.  A few things should come up, one should be "ndiswrapper-common" and the other "ndiswrapper-utils-1.9"  

Check install for both of those and then you should be good to go.

---

### Post by Tanith12 on 2008-07-21
i do not have any livecd though, was i supposed to burn something earlier???

---

### Post by falcon61102 on 2008-07-21
By LiveCD, I mean the install CD... they are one in the same.

How did you install Ubuntu?

---

### Post by Tanith12 on 2008-07-22
i downloaded it, and ran the exe file from vista and chose to install it in the empty partition

---

### Post by falcon61102 on 2008-07-22
If it's at all possible, I recommend burning a copy of the LiveCD.  Its very handy to have a times such as this.

---

