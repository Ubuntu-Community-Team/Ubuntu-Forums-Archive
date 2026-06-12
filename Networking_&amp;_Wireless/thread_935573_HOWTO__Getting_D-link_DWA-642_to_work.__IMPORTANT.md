---
title: "HOWTO:  Getting D-link DWA-642 to work.  IMPORTANT"
date: 2008-10-01
forum: Networking &amp; Wireless
---

### Post by FAJALOU on 2008-10-01
Edit:

For 9.04, I found that one has to install ndiswrapper and follow the certain steps for ndiswrapper (like normal), and also remove the blacklist in /etc/modprobe.d/ for ath_pci (should be under blacklistath_pci.conf or something like that).  And then reboot, and wallah!  If that doesn't work, feel free to contact me... The only thing that I noticed is that the lights on the adapter do not function properly (the connection one just blinks), but it still connects to the Internet just fine, nothing a little black duct tape doesn't solve!
Personally I use WICD not gnome-network-manager, and I would recommend WICD over Network-Manager any day, but whatever suits your fancy!

**N.B.** Due to recent updates with ndiswrapper, I, along with others, have been able to run the DWA-642 cards without using madiwifi at all.  First try using the card with only ndiswrapper [(instructions found here)]("http://www.google.com/url?sa=t&source=web&ct=res&cd=2&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FWifiDocs%2FDriver%2FNdiswrapper&ei=zej0SaK7NJTitQOpm8nPCg&usg=AFQjCNE3_HnEDUDQBVYWKHVN86jQzFVZ8A&sig2=ehp0Y7BU_PDJhIgvwNKEdg").  Supposedly there *is* now support for this card with [ath9k]("http://wireless.kernel.org/en/users/Drivers/ath9k") in 8.10 and probably 9.04.  It would be interesting if people could try using it; I tried it a long **long** time ago and it didn't work for me; so I just went with better safe than sorry now!

*Before we go on:* You need to make sure that you have removed any old attempts to get this card to work.  This would include removing linux-restricted-modules, and removing ndiswrapper, so we can start totally from new. Hopefully this will help make your life down the road easier

My dad had the card mentioned above and I could not get it to work.  I finally figured out how to get it to work, this is what you do:

First, download and install ndiswrapper-common and ndiswrapper-utils:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
```
These commands are for hardy only, and may change with new updates.  If you cannot get onto the internet at all from the computer, you can find both of the packages here:  
[http://packages.ubuntu.com/hardy/ndiswrapper-common](http://packages.ubuntu.com/hardy/ndiswrapper-common)
[http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/hardy/ndisgtk](http://packages.ubuntu.com/hardy/ndisgtk)

Download these to a flash drive, and then bring to your computer and make sure that you install them in the order above.

Next, go to System>Administration>Windows Wireless Drivers.  After typing in your password, click Install Driver.  Then navigate to the CD and find the drivers.  Most of the time, XP drivers work fine.  Also, each CD has it's own directory for drivers.  Most of the time, it can be found in Setup, or in Drivers.  For the DWA-642 the driver is found in Setup/Drivers/.

Then click ok, install, and exit Windows Wireless Drivers.

Finally (for this part) add ndiswrapper to the modprobe by typing in ```
sudo modprobe ndiswrapper
```
If you find this not to work for you, and you have to type this in every time you log in, do the following
```
sudo gedit /etc/rc.local
```
Find right above the exit 0 and add;
```
sudo modprobe ndiswrapper
```

*Next*, you have to install madwifi.  Madwifi is *supposed* to come with Ubuntu restricted modules, but this way worked for me.  First download the latest source code (found here:  [http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz](http://downloads.sourceforge.net/madwifi/madwifi-0.9.4.tar.gz), **EDIT I have noticed that the above version does not work real great, however this one: [http://snapshots.madwifi.org/madwifi-trunk/madwifi-trunk-r3856-20080903.tar.gz](http://snapshots.madwifi.org/madwifi-trunk/madwifi-trunk-r3856-20080903.tar.gz) works really really well   note that if you use this one you will have to change the cd command to correspond to madwifi-trunk-r3856-20080903 not madwifi-0.9.4, if this gives you issues, contact me, but as I said, I have found this trunk to be more stable for what we are doing.)** and extract it into your $HOME directory.  After it is compiled, change directories to it with the following:
```
cd ~/madwifi-0.9.4
```
Note that this command will be different if you are using a different version of madwifi possibly from the madwifi site.
After the above command do this:
```
sudo make
sudo make install
```
And wallah madwifi is now compiled, if it asks you any questions, say yes.
Finally, type in ```
sudo modprobe ath_pci
```
to allow madwifi to work.  As above, if you find that you have to type this in every time you log in, add this to /etc/rc.local  as   ```
sudo modprobe ath_pci
``` right under sudo modprobe ndiswrapper.

After this is done, restart your computer and there is your card.  This is a two pronged attack, and I could see someone getting messed up on it.  Please *please* post a reply of how it went down for you, and also if it worked, that way I can know that I am helping someone:D :guitar:
Good luck, and feel free to respond

NB:   Something that I noticed:  After many of the software upgrades, this last update updated nautilus, and vlc (guessing nautilus update is the culprit) you will need to recompile and install the madwifi-trunk drivers, because it will not work after a software upgrade.  Other than that have fun :D

---

### Post by Virtual_Linuxuser on 2009-02-12
Newbie here, I just setup a dual boot on my Vista desktop with Ubuntu 8.04 LTS. I was told that D-Link DWA-542 Wireless Adapter will work right out of the box with most of the distros. But Ubuntu disappointed me, so after some digging around I came across your article, followed it religiously and it worked like a charm. . Thanks a million. Cheers.

---

### Post by FAJALOU on 2009-02-12
Sweet this is good to know.  I actually noticed after a new install that ndiswrapper got the 642 working with no need for ath_pci, but if this works go for it :KS

---

### Post by Virtual_Linuxuser on 2009-02-18
The wireless signal strength is around 54-60%, it never reaches the 100% mark.  My router is a Linksys WRT160N, physically located on the first floor and desktop is on the second floor, about 15 feet above it. Not sure if it's the drive or the card itself is the reason behind it.  Is there any tweaking I could do to get the full or near full signal strength? Thanks again.:KS

---

### Post by FAJALOU on 2009-02-18
> **Virtual_Linuxuser said:**
> The wireless signal strength is around 54-60%, it never reaches the 100% mark.  My router is a Linksys WRT160N, physically located on the first floor and desktop is on the second floor, about 15 feet above it. Not sure if it's the drive or the card itself is the reason behind it.  Is there any tweaking I could do to get the full or near full signal strength? Thanks again.:KS


Hello!  It is great to know that you have it up and working.  Personally I would not trust the 'signal strength' indicator on network-manager for *beans*.  It just doesn't work. ;)

Now saying that... There is one way I know of to figure out the actual strength:
Go to your gnome-panel>Right Click>Add to panel...>Network Monitor
And add it, then when it is there, click on it once to open it up and bamo, your true signal strength should be right there.  I don't know really *how* otherwise to find this number, but as long as this way works ;).  Hopes this helps.

---

### Post by Virtual_Linuxuser on 2009-02-19
Thanks bud...It shows the signal strength around 90%. Couldnt ask for more.  Would you happen to know any good book on Ubuntu? more like a administrative manual..thanks again.

---

### Post by FAJALOU on 2009-02-19
Uhm Google :D.  I pesronally have found that, when I have an issue, Google and the Forums are the best places to go.  If you don't get an answer, the #ubuntu room in Freenode is good too.  I don't know of any books... per se, because I have not used any for in depth study; I have primarily used Google, the Forums, and the IRC.  But, I do know that if you go to the computer section in any of the stores like Barnes & Noble and/or Borders, they do have books on Ubuntu, that may fit your fancy.  Good luck!

---

### Post by Virtual_Linuxuser on 2009-02-22
Good stuff..thanks bro.:D

---

### Post by ffaker on 2009-04-22
This is a draft N card: is it working in Ubuntu at draft N speeds?

---

### Post by FAJALOU on 2009-04-22
No.  Currently Ndiswrapper does not have N support yet.  Nor does Madwifi, I think, but they are getting close!

---

### Post by Treecounter on 2009-04-26
Fajalou, thanks for the great directions.  My newbie experience today: the second link to madwifi in your first post was broken.  I played around with the first link, the Sourceforge version, and got repeated errors trying to  $ make the file. Finally I scrolled to the bottom of your post, read that you'd gotten the D-link to work with only ndiswrapper in newer versions of Ubuntu.  Like magic, I restarted the computer and there was the internet.  THANKS!

One question-- I have no idea how to uninstall or decompile the failed $ make of madwifi.  Should I be worried about that?

---

### Post by FAJALOU on 2009-04-26
Treecounter,
    How far along did your compiling go?  if it didn't get past make, then I wouldn't worry about it, you could just delete the folder; that should work.  Otherwise, you could try cding to the folder and then running ```
sudo make uninstall
```.  *Then* after that you could just delete the folder.  I will update the how-to to make sure that ndiswrapper is seen as first option now, seems how it seems to be working without the madwifi!  Thanks for your help!

---

### Post by linuxdave1 on 2009-05-17
I have a DWA-542 on Ubuntu 8.10 desktop edition. The wireless card worked (more or less) using the built in ath9k driver that is installed with the OS, but occasionally I would lose connectivity with large xfers or sometimes for seemingly no reason, so I decided to follow the instructions to use ndiswrapper at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Well I followed the instructions exactly and now I have no wlan0 at all so I uninstalled the Windows driver for the DWA-542 adapter, then uninstalled ndiswrapper altogether and still have no wlan0 device.

How can I get it back using the default ath9k drivers that come with 8.10?

---

### Post by FAJALOU on 2009-05-17
Dave,
   This calls for a different thread all together.  Sorry for the lack of help here, but you will get better support if you start your own post.

---

### Post by linuxdave1 on 2009-05-17
No problem Fajalou. I actually got everything working by going through the comprehensive ndiswrapper guide. :D

Thanks though.

---

