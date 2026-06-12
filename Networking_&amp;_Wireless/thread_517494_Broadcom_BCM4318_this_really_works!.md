---
title: "Broadcom BCM4318 this really works!"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by kevinclemons82 on 2007-08-04
This is not my work and i will not claim it to be, but I recently switched to Ubuntu from xp. I was having a real hard time getting my BCM4318 to work like a lot of other people apparently. well i stumbled across this site [http://www.segundanariz.com/ubuntu/?p=31]("http://www.segundanariz.com/ubuntu/?p=31") and it worked for me...... and in case this link doesn't work ill copy the text and put it in here as well.  Hope this helps 

kevin

ts amazing, after months and months of trying to get my wireless to work (and eventually giving up - I bought a PCMCIA card) I found the solution.

And, no, Ndiswrapper wasnt the answer for me.

If you have tried Ndiswrapper before without luck, then you should try this! (In just 4 simple steps)

Step 1:
Type in a terminal, code:

sudo apt-get install bcm43xx-fwcutter

Step 1 addendum! If you dont have internet access at your computer, I have just added the &#8220;.deb&#8221; package for download at this location, choose the Ubuntu version you have and just double click it and install it instead of using synaptic.
Step 2:
Download this file to your Desktop.

Step 3:
Extract the file in the same location by right-clicking and selecting &#8220;extract here&#8221;
If you dont have ZIP just add it by code: sudo apt-get install zip

Step 4:
Now you have to type this code with YOUR version of your kernel so type code: uname -r
And then replace whatever the output to this code: sudo bcm43xx-fwcutter -w /lib/firmware/2.6.17-11-generic ~/Desktop/wl_apsta.o

With that done, you HAVE TO reboot Ubuntu and enable the connection at System=>Administration=>Networking

If it still doesnt work you have to code: sudo modprobe bcm43xx

Yey!

*edit (WPA Encryption, thanks VastOne!) : One user reported WPA capabilities by NOT removing the network manager, so if you are looking for a solution that includes WPA, try first to leave the network manager installed.
Also note the following: There is an issue with using the Keyring at startup with a WPA enabled WiFi.  When you first boot, there is only a manual configuration option in Network Manager icon and no WiFi due to the time sequence with WiFi and the Keyring&#8230;It looks as if WiFi and Network Manager is out of sequence when the Keyring loads on bootup.

Solution:  Once fully booted, simply disable the network and then enable it.  The Keyring password then pops up and the WiFi starts.

*edit: For Feisty Fawn users, you have to remove Network Manager, as it has conflicts with the Wireless Connection so remove it by code:
sudo apt-get remove network-manager

*edit: I am using a Gateway 7330gz laptop with this wireless card: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller



leave a comment let me know if this is helping anyone??

---

