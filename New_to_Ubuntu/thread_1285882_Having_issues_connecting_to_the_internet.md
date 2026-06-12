---
title: "Having issues connecting to the internet"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by Amockineuropa on 2009-10-08
OK I am new to Ubuntu but I have a problem. Ubuntu will not recignize my wireless card and it is not listed on ndiswrapper. I even tried to hard wire it to the internet but still no go. My Windows Vista works just fine but not my Ubuntu. So what now? I believe my wireless driver is a Atheros AR9285 which is NOT listed under ndiswrapper! Is there a substitute?
 
 [FONT=Arial Black, sans-serif]rollingstone@ubuntu:~$ sudo lshw -C network [/FONT]
[FONT=Arial Black, sans-serif]*-network UNCLAIMED [/FONT]
[FONT=Arial Black, sans-serif]description: Network controller [/FONT]
[FONT=Arial Black, sans-serif]product: AR9285 Wireless Network Adapter (PCI-Express) [/FONT]
[FONT=Arial Black, sans-serif]vendor: Atheros Communications Inc. [/FONT]
[FONT=Arial Black, sans-serif]physical id: 0 [/FONT]
[FONT=Arial Black, sans-serif]bus info: pci@0000:02:00.0 [/FONT]
[FONT=Arial Black, sans-serif]version: 01 [/FONT]
[FONT=Arial Black, sans-serif]width: 64 bits [/FONT]
[FONT=Arial Black, sans-serif]clock: 33MHz [/FONT]
[FONT=Arial Black, sans-serif]capabilities: pm msi pciexpress bus_master cap_list [/FONT]
[FONT=Arial Black, sans-serif]configuration: latency=0 [/FONT]
[FONT=Arial Black, sans-serif]*-network UNCLAIMED [/FONT]
[FONT=Arial Black, sans-serif]description: Ethernet controller [/FONT]
[FONT=Arial Black, sans-serif]product: Attansic Technology Corp. [/FONT]
[FONT=Arial Black, sans-serif]vendor: Attansic Technology Corp. [/FONT]
[FONT=Arial Black, sans-serif]physical id: 0 [/FONT]
[FONT=Arial Black, sans-serif]bus info: pci@0000:08:00.0 [/FONT]
[FONT=Arial Black, sans-serif]version: c0 [/FONT]
[FONT=Arial Black, sans-serif]width: 64 bits [/FONT]
[FONT=Arial Black, sans-serif]clock: 33MHz [/FONT]
[FONT=Arial Black, sans-serif]capabilities: pm msi pciexpress vpd bus_master cap_list [/FONT]
[FONT=Arial Black, sans-serif]configuration: latency=0 [/FONT]
[FONT=Arial Black, sans-serif]*-network DISABLED [/FONT]
[FONT=Arial Black, sans-serif]description: Ethernet interface [/FONT]
[FONT=Arial Black, sans-serif]physical id: 1 [/FONT]
[FONT=Arial Black, sans-serif]logical name: pan0 [/FONT]
[FONT=Arial Black, sans-serif]serial: 76:2a:72:66:ca:b4 [/FONT]
[FONT=Arial Black, sans-serif]capabilities: ethernet physical [/FONT]
[FONT=Arial Black, sans-serif]configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes [/FONT]

---

### Post by swoody on 2009-10-08
Try running:
```
sudo apt-get install linux-backports-modules-jaunty
```
and then restarting your computer. If you don't have an ethernet connection working on your computer let us know, and we'll get that straightened out as well :)

Edit: Sorry, just read that your ethernet connection isn't working. One second, while I find how to get that working first.

---

### Post by Amockineuropa on 2009-10-08
I will give that a try!

---

### Post by Amockineuropa on 2009-10-08
Tried and it says "couldn't find package linux-backports-modules-jaunty"

---

### Post by swoody on 2009-10-08
> **Amockineuropa said:**
> Tried and it says "couldn't find package linux-backports-modules-jaunty"
Yes, it will say that since you're not connected to the internet.

I take it your are using an eeePC? If so, this how-to should be what you're looking for:
[http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/](http://www.jfwhome.com/2009/08/06/perfect-ubuntu-jaunty-on-the-asus-eeepc-1005ha-and-1008ha/)
Just scroll down, and go through the section under 'Wired Networking'. Then once you get connected via ethernet, you can run the above command to get your wireless working.

---

### Post by Amockineuropa on 2009-10-08
I have a dual boot setup and under Windows my internet works just find BUT under Ubuntu it is a no-go. Appears to not recognize my driver! When I click on linux network icon I get NVPN connections drop down only! No other options. I think it is not compatible with my wireless card or for that matter with my internal modem

---

### Post by Amockineuropa on 2009-10-08
Have a ACER Aspire 5517 laptop

---

### Post by Amockineuropa on 2009-10-08
I am a complete moron! I follow the above address but I am not sure HOW to do what it suggests. I copied file but not sure how to run it. It just opens as a bunch of files but I dont see .exe file

---

### Post by Amockineuropa on 2009-10-08
So I get this info but not sure HOW to NAVIGATE ('cd) to the SRC directory...etc What is this and how do I do it?
 
 
Open the zip file (double-click it), and extract it to the location of your choice. Then, in a terminal, navigate (’cd’) to the ’src’ directory of the unpacked files, and type:

[I][COLOR=#3366cc]make
sudo make install
sudo insmod atl1e.ko[/COLOR][/I]

---

### Post by swoody on 2009-10-08
Well, it seems like you may not have the same computer as the link I posted above, but it seems like the networking components are the same. All the info on your model seems to use the same ethernet and wireless drivers that the eeePC uses, so try the link I posted above, and see how it works. It should be able to get your wired and wireless working, you'll just need a way to transfer the driver package from the computer you download it on to Ubuntu :)

---

### Post by Amockineuropa on 2009-10-08
I do I am using a stick memory BUT HOW do I do this part of the instructions:
Open the zip file (double-click it), and extract it to the location of your choice. Then, in a terminal, navigate (’cd’) to the ’src’ directory of the unpacked files, and type:

make
sudo make install
sudo insmod atl1e.ko

Not sure HOW to navigate cd to the src directory and unpack the files on Ubuntu

---

### Post by swoody on 2009-10-08
Yes, the 'cd' command is 'change directory' you'll need to open a terminal Applications>Accessories>Terminal, and 'cd' to the directory your just extracted. So if they're in your /home folder, you would:
```
cd /home/yourname/foldername/src
```
likewise if the extracted foler is on your Desktop:
```
cd /home/yourname/Desktop/foldername/src
```
and then the commands 'make' and 'sudo make install' need to be run in the terminal when you're in that directory. So you would just type in:
```
make
```
then:
```
sudo make install
```
and finally:
```
sudo insmod atl1e.ko
```

---

### Post by Amockineuropa on 2009-10-08
OK here is what I did I downloaded driver file to a stick memory and transfered it to my ubuntu and placed the file on its desktop! Now what should I do?

---

### Post by hockeytux on 2009-10-08
Open the terminal and type:

> cd /home/yourname/Desktop/foldername/src


...changing the name as appropriate.

then type as above:

make [press ENTER]

sudo make install [press ENTER]

sudo insmod atl1e.ko [press ENTER]

---

### Post by swoody on 2009-10-08
First, right-click on the atheros-wired-driver-1005ha-linux package, and select 'Extract Here'. That will create a new folder of the same name on your Desktop. Then open a terminal (Applications>Accessories>Terminal) and enter:
```
cd /home/yourname/Desktop/atheros-wired-driver-1005ha-linux/src
```
Please change 'yourname' above to your username. This will change your working directory to the src folder we need. Now in the terminal enter:
```
make
```
then when that's done:
```
sudo make install
```
and finally when that's done:
```
sudo insmod atl1e.ko
```

If any of the commands above output any errors, please let us know :)

---

### Post by Amockineuropa on 2009-10-08
OK I moved file to my home folder and extracted it there I tried the cmd but it says no such file or directory

---

### Post by swoody on 2009-10-08
If you extracted the package to your /home directory, you'll need to use:
```
cd /home/yourname/atheros-wired-driver-1005ha-linux/src
```
Again, replace 'yourname' with your username. And then run the commands above.

---

### Post by Amockineuropa on 2009-10-08
OK I moved file to my home folder and renamed it to just Atheros. I typed the following:
cd /home/rollingstone/atheros/src - I get no such file!
I loaded the zip file via a memory stick onto my ubuntu pc do I still use cd?

---

### Post by Amockineuropa on 2009-10-08
I right clicked said file and extracted it into my home folder and again typed:
cd /home/rollingstone/atheros/src and still it says no such file

---

### Post by swoody on 2009-10-08
And you extracted the atheros.zip file by right-clicking on it, and selecting 'Extract Here' correct? You can see in your home folder that there is a seperate atheros.zip and an atheros folder, yes?

---

### Post by Amockineuropa on 2009-10-08
Also some of the extracted file have a little lock on the them is this normal?

---

### Post by hockeytux on 2009-10-08
Try it step-by-step, and note it may be case-sensitive.

Type in the terminal:

cd /home [press Enter]

cd /rollingstone [press Enter]

cd /Atheros [press Enter]

cd /src [press Enter]



Let us know at which step it says 'no such file or directory'...

---

### Post by Amockineuropa on 2009-10-08
I tried but when I get to my username (rollingstone) it says no files/directory

---

### Post by swoody on 2009-10-08
> **hockeytux said:**
> Try it step-by-step, and note it may be case-sensitive.

Type in the terminal:

cd /home [press Enter]

cd /rollingstone [press Enter]

cd /Atheros [press Enter]

cd /src [press Enter]



Let us know at which step it says 'no such file or directory'...

You're going to get errors running it like that. You need to use a . in front of /directory, or leave the / off the command. So it would look like this:
```
cd /home
```
since /home is a location on /root.
```
cd ./rollingstone
```
The . in front of /directory tells the cd command that you want it to find that directory in your current working directory. Otherwise you may omit the / in front of the directory which will do the same thing:
```
cd rollingstone 
```
This again tells cd to find the directory 'rollingstone' in the current working directory.

So Amockineuropa, run the cd commands like this:
```
cd /home
```
```
cd ./rollingstone
```
```
cd ./atheros
```
```
cd ./src
```
and see what is giving you the error :)

---

### Post by Amockineuropa on 2009-10-08
OK that all worked I now have:
[EMAIL="rollingstone@ubuntu:~/Atheros_FILES/src$"]rollingstone@ubuntu:~/Atheros_FILES/src$[/EMAIL]
 
What now?

---

### Post by swoody on 2009-10-08
Now run the commands as posted above:
```
make
```
```
sudo make install
```
```
sudo insmod atl1e.ko
```

---

### Post by Amockineuropa on 2009-10-08
Do I run each command at a time?

---

### Post by swoody on 2009-10-08
Yes, enter one command, press [ENTER] and when it's done running, enter the next command. You'll know it's done when you wind up back at:
rollingstone@ubuntu:~/Atheros_FILES/src$

---

### Post by Amockineuropa on 2009-10-08
I get to this line of cmd "sudo insmod atlle.ko" and get can't read atlle.ko

---

### Post by swoody on 2009-10-08
Just to make sure you entered it correctly, its:
A T L 1 E . K O
but all in lowercase. Try that again :)

---

### Post by Amockineuropa on 2009-10-08
Ok that seemed to work (sudo insmod atl1e.ko) now I am back to the [EMAIL="rollingstone@ubuntu:~/Atheros_FILES/src$"]rollingstone@ubuntu:~/Atheros_FILES/src$[/EMAIL] line. What now?

---

### Post by swoody on 2009-10-08
Now test out your ethernet connection. It should work. If not, try rebooting your comp with the ethernet cable plugged in :)

---

### Post by Amockineuropa on 2009-10-08
I am still not connected. I tried to reboot WITH ethernet cable to laptop but still a no go. I understand that I am a real pain BUT I am learning and U have been most helpful.

---

### Post by oldsoundguy on 2009-10-08
> **Amockineuropa said:**
> I am a complete moron! I follow the above address but I am not sure HOW to do what it suggests. I copied file but not sure how to run it. It just opens as a bunch of files but I dont see .exe file


There are no .exe files in Linux. .exe files are Windows executables (the same ones that give you malware in Windows.)

---

### Post by Amockineuropa on 2009-10-08
Hey I fixed it! I went under network connections and put in the password for my router and hardwired it works!! Thank you so much for your efforts.D oU know HOW to get it to work via wireless?

---

### Post by swoody on 2009-10-08
It's no problem at all. Just remember Linus Torvalds was 'learning' at one point, too ;)

In a terminal again, try:
```
sudo modprobe atl1e
```
and restest your wired connection. If it's still a no-go, right-click on the network icon in the top right, and make sure 'Enable Networking' is checked. If it is unselected, check the box next to it, and try connecting again. If that's still not working, can you run this command in a terminal, and give us any output:
```
sudo lsmod | grep atl1e
```

---

### Post by swoody on 2009-10-08
> **Amockineuropa said:**
> Hey I fixed it! I went under network connections and put in the password for my router and hardwired it works!! Thank you so much for your efforts.D oU know HOW to get it to work via wireless?

Ok, that's great to hear! You can ignore my last post then :)

For wireless, go to System>Administration>Software Sources and under the 'Updates' tab, make sure that the option that includes (jaunty-backports) is selected. Then you can close that window. If it asks you to refresh the package info, allow it to do this. Then when this is done, open a terminal again, and enter:
```
sudo apt-get install linux-backports-modules-jaunty
```

---

### Post by Amockineuropa on 2009-10-08
I take it that is sudo modprobe "atL1e" just in small case?

---

### Post by swoody on 2009-10-08
You can ignore that post since you got wired connection working :)

See my last post for how to get wireless working.

---

### Post by Amockineuropa on 2009-10-08
I am downloading the requested files and will try your suggestions after it loads

---

### Post by Amockineuropa on 2009-10-08
This is what I got:
 
[FONT=Arial Black, sans-serif][EMAIL="rollingstone@ubuntu:~$"]rollingstone@ubuntu:~$[/EMAIL] sudo apt-get install linux-backports-modules-jaunty [/FONT]
[FONT=Arial Black, sans-serif]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable) [/FONT]
[FONT=Arial Black, sans-serif]E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? [/FONT]
[FONT=Arial Black, sans-serif]rollingstone@ubuntu:~$ [/FONT]

---

### Post by swoody on 2009-10-08
This is an issue with gaining the lock on your packages. Make sure the Software Sources windows have completely closed, and try it again.

---

### Post by Amockineuropa on 2009-10-08
Since it got online it is currently downloading software updates would this be ths issue?

---

### Post by swoody on 2009-10-08
Oh no, that's a very good thing :) Since this is your first time running updates on your computer, this may take a while. Just be patient, and let the updates complete, and then run the command again.

---

### Post by Amockineuropa on 2009-10-08
I ran the requested cmd and what now?

---

### Post by Amockineuropa on 2009-10-08
IT WORKS! I now have internet BOTH wired/wireless! Thanks

---

### Post by swoody on 2009-10-08
Glad to hear it's up and working for you :D

Just as a side note, as a new user I think you may find the Ubuntu Pocket Guide a very useful guide to have on hand. I know I've learned a lot from it, myself :)
You can download a free copy here, and have a read:
[www.ubuntupocketguide.com](www.ubuntupocketguide.com)

---

### Post by Amockineuropa on 2009-10-08
I would like to take the time to personally thank you since U went out of yours to help me!

---

