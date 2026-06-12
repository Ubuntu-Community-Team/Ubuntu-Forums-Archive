---
title: "Ndiswrapper 54g issues..."
date: 2005-12-02
forum: Networking &amp; Wireless
---

### Post by kufford on 2005-12-02
Hello all, 

I've been running ubuntu for several months now on a Compaq 3230US notebook PC. I'm having trouble installing and configuring ndiswrapper correctly in order to gain the use of my wireless card. Yes, I have one of those horrible Broadcom 54g abhorations that everyone hates.

I've followed several tutorials and googled repeatedly for assistance to no avail. Here's what I've done so far. 

sudo apt-get install ndiswrapper-utils
sudo apt-get install ndiswrapper-source
sudo apt-get install ndisgtk

Then, I booted into Windows and extracted the appropriate driver file from Compaq's driver support data base - "bcmwl5.inf", copied it onto a USB disk and copied to desktop.

cd .../Desktop
sudo ndiswrapper -i bcmwl5.in
sudo ndiswrapper -l

Then I recieve the following output:

installed ndis drivers:
bcmwl5 invalid driver!

If I open up the ndiswrapper gui and try to add the .inf file with that method, it outputs "Hardware present: no"

I'm at a loss... feel free to email me at [email]kufford@....removeme.....gmail.com[/email] or post up in the thread. I hope I included enough info, please let me know if left something out. Thank you...

---

### Post by ckempo on 2005-12-03
I've been playing with Ndiswrapper trying to get it to work for me and my brother on our laptops.... after doing much reading around, I think you should extract EVERYTHING from your driver package and place the lot in a directory somewhere (I've been using "/broadcom" and "/USRobotics" for my two laptops). 

The .inf is not enough, you need at least another .sys file.

If you open the .inf in a text editor, and read through, you'll see reference to multiple required files, make sure all these are present. Or do something like "grep sys bcmwl5.inf" (on your Linux box, obviously) to pull out all the lines with reference to .sys files.  Make sure they're all present.

Then try your ndiswrapper setup again - so use "ndiswrapper -e bcmwl5.inf" (or whatever the remove command is, writing this from memory) then set it up again using your commands from before.

Hope this helps a little - somebody will be able to help you out a bit more than I can with my limited knowledge!

---

### Post by Joeak on 2005-12-03
Below is my full writeup of a similar situation.  Based on your post it sounds like you just didn't extract the sys file to go with the inf.  Open the inf in an editor and you should see one reference to a sys file or other named file.  put it in the same directory as the inf and re-try the ndiswrapper -i command.

I had to do the Columbo thing to figure out how to enable a Linksys WPC54GS wireless pcmcia card on my Debian Sarge install on a Dell Inspiron 3500.  THe main help I found was:

     [http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683)

I believe the gist of what I had to do was:

     apt-get install kernel-image-2.6-386    < I think maybe ndiswrapper in Debian is only for 2.6, and only for the -386 version too

Restart, then verify that you're running the 2.6-386 version:

     uname -r    < shows currenly running kernel version

Download the Windows drivers for the card, such as from:

     [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

I had to install unzip for file-roller to be able to open it:

     apt-get install unzip zip

Open the zip and extract the driver's inf and sys files from the zip, in this case I extracted bcmwl5.sys and lsbcmnds.inf into the /root/Desktop/ folder.

If you have already been fighting with ndiswrapper, remove it and delete the traces of your fiddling:

modprobe -r bcmwl5
rmmod ndiswrapper
apt-get remove ndiswrapper-utils
rm -r /etc/ndiswrapper/

rm -r /etc/modprobe.d/ndiswrapper


apt-get install ndiswrapper-utils
ndiswrapper -i ~/Desktop/lsbcmnds.inf
ndiswrapper -l     < should show it as installed and hardware present

ndiswrapper -m


Reboot the laptop.

    

modprobe ndiswrapper   < should not error
iwconfig               < should list wlan0 now


Open the networking configuration tool Applications --> System Tools --> Networking

     Add, wireless, wlan0, dhcp, my "network id" I think is my WAP's ssid, "joespears"

    ifconfig    < showed wlan0 with an ip address from my WAP

I hot-unplugged my 10Base-T card, and I could still ping the router, but not any internet addersses.  To re-set the DNS, default gateway, etc., I did:

    ifdown wlan0
    ifup wlan0

VOILA!

I had to repeat the last few steps every time I wanted to use wireless after rebooting.  I just added ndiswrapper to the /etc/modules file and rebooted with the CAT5 line unplugged, and it did come up properly.  (There was a delay apparently while the system tried to get eth0 to connect before it failed over and tried wlan0.)

---

### Post by kufford on 2005-12-03
Thanks for the assistance. I really appreciate it. 

I did somemore digging and found a tutorial that said that I should try the bcmwl5a.ini driver. So I did followed the tutorial through again, rebooted my box, and  when the light didn't come on, i modprobed ndiswrapper and managed to connect. I'm under a university VPN and I haven't tried to tackle that yet, however, my wnic light comes on and I can run a wlan sniffer and pickup the network. I'm going to take it to an open wlan and see how that goes later tonight. Hopefully, this post can help someone else with the same troubles. I'll post up again if it doesn't work.

---

