---
title: "Can't get wifi to work (BCM4303)"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by JayStayPaid9888 on 2010-06-27
I recently installed Ubuntu on a desktop that was gathering dust in my house. I absolutely love everything about it so far and I'm learning something new everyday. However, I have spent the past few days following every tutorial I can find in an effort to get my wireless to work to no avail. I have a BCM 4303 wireless card (apparently the most aggravating card on the market) and the chipset is 14e4:4301. I am connected to the internet through my laptop currently. I have tried ndiswrapper (no luck) as well as b43-fwcutter (no luck), but perhaps now that I have a whole wonderful community behind me, I might make a little more progress! Let me know whatever info I need to post and I will do it asap. Thanks so much in advance!

---

### Post by anewguy on 2010-06-27
If you at least have some form of internet access, what you should try is:

- open a terminal window (applications/accessories/terminal)

- type:

sudo apt-get update <press enter>  It will ask for a password - use your regular login password.  It will look like nothing is being entered but that's ok - when you finish typing the password just press enter.

- now, check under System/Administration/Hardware Drivers and see if there is a driver there you can enable.

Be aware that if you have already messed around with ndiswrapper (BTW - when you want to use ndiswrapper, be sure to install ndisgtk as it is a GUI'd front-end to ndiswrapper and saves a LOT of typing) and combine that with also trying the firmware cutter, I personally would reinstall first, especially since this is a new install, so that you are working from a clean slate instead of who knows what has changed, modules blacklisted, modules added, etc..  It would just make troubleshooting a lot easier.

Dave ;)

---

### Post by anewguy on 2010-06-27
I guess I'll go ahead and post here what I posted in reply to another thread last week and one just a few minutes ago.  If you have a "clean slate" you'll be much better off:

There are many, many posts on the forum for wireless adapter help, but a basic strategy would be:

(1) Check for restricted driver:

- connect your computer via a hard wired connection to the internet

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo apt-get update <press enter>

After this completes, close the terminal window, then go to System/Administration/Hardware Drivers and see if a driver is listed there. If so, enable the driver (I would also just reboot after this).

(2) If a hard wired connection is not an option, or if you tried but no driver showed in System/Administration/Hardware Drivers, your next step would be to try ndiswrapper. There are 3 main things needed for this: ndiswrapper and its utility, the Windows XP driver files (.inf and .sys) for the adapter, and ndisgtk. The following is how to install ndiswrapper, the ndiswrapper utilities, ndisgtk, and install the driver using these tools. Please note you will need to locate the Windows XP driver files for your adapter first.

- copy your Windows XP driver files (.inf and .sys files) to your desktop

- spin up the Ubuntu LiveCD you installed from. When a message comes up about a CD with packages being found, just cancel out of it.

- via "Places", open the LiveCD in the file browser

- navigate to the pool/main/n folder. You should see 2 folders here: 1 for ndiswrapper and 1 for ndisgtk. Ndiswrapper must be installed first, so do the following:

    * navigate to the ndiswrapper folder
    * double click on the ndiswrapper-common file to start its installation
    * when ndiswrapper has finished installing, double click on the ndiswrapper utilities file to start installing it
    * navigate back one folder to the pool/main/n folder again, then click on the ndisgtk folder
    * double click on the ndisgtk file to starts its installation


- go to System/Administration/Windows Wireless Drivers. This will start ndisgtk (it's gui'd front end to ndiswrapper).

- if anything shows in ndisgtk, delete it so the "slate is clean"

- click add and point it to the Windows XP driver .inf file on your desktop. This should install the driver.

As with anything, there are exceptions. Some may require some special configuration of the wireless connection via such things as iwconfig, etc.. Some laptops also have a key (or set of key combinations) that physically turn the wireless adapter off or on - you have to be sure you have it on. Sometimes other things crop up - when they do just post back to the forum and people will try to help you.


Now for a couple things common to all:

- know your routers configuration - you will need to know such things as:

    * The network (ESSID) name, especially if your router is "hiding" the network by not broadcasting the name.
    * What type of security is being implemented - WEP, WPA, WPA2, etc.
    * The network key if security is being implemented
    * Is MAC filtering enabled - if so, you'll need to add the adapters MAC address to the table in the router or you will never connect to it


- right click on the network manager icon and be sure "Enable Wireless" is checked

- check in network manager for wireless networks. If you can see available wireless networks your adapter is now working. Please note that if the only network(s) available in your area are "hidden" (the router is not broadcasting a network name), you will not see them in network manager. You must manually add the new connection via network manager.


Dave ;)

---

### Post by JayStayPaid9888 on 2010-06-28
Ok, guys. I reinstalled and am now working with a clean slate. I did apt-get update and also enabled the b43legacy driver found under System>Hardware Drivers. However, when I click the Network Manager and try to enable wireless, I find that it says wireless is disabled and Enable Wireless is blacked out when I right click. This is where I've been stuck for quite a while. Where should I go from here?

---

### Post by JayStayPaid9888 on 2010-06-29
Not sure where to go from here guys... anyone got any pointers? I've followed TONS of tutorials with no luck, so I figured posting here with my specific case would be the thing to do.

---

### Post by achase79 on 2010-06-29
did you go to System->Administration->Hardware Drivers and see if anything was there to install?

---

### Post by JayStayPaid9888 on 2010-06-29
As I stated above, "Ok, guys. I reinstalled and am now working with a clean slate. I did  apt-get update and also enabled the b43legacy driver found under  System>Hardware Drivers. However, when I click the Network Manager  and try to enable wireless, I find that it says wireless is disabled and  Enable Wireless is blacked out when I right click. This is where I've  been stuck for quite a while. Where should I go from here?"

---

### Post by JayStayPaid9888 on 2010-06-29
Ok, so I went ahead and moved to trying ndiswrapper. I cabextracted the WinXP drivers I found here: [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-31559-1&lc=en&cc=us&dlc=en&product=437690&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-31559-1&lc=en&cc=us&dlc=en&product=437690&os=228&lang=en)

I then moved the files bcmwl5.inf and bcmwl5.sys to my desktop. I started ndisgtk and selected the bcmwl5.inf which it installed with no problems. Then I restarted my computer, just for good measure, but the "Enable Wireless" option is still faded when I right click Network Manager and it says "Wireless is Disabled." I'm very new to Ubuntu so any direction from here is greatly appreciated!

Also, I'm using a Dell desktop.

---

### Post by anewguy on 2010-06-30
It's possible you need to add b43 and ssb to the blacklist.conf file to stop default drivers from stepping on what you are trying to install.  The same applies to the restricted driver.  If you still have it enabled you must disable it before you can have any success with another driver and method.  Same  goes  for the firmware cutter.

It's also possible you need to do a ifup on wlan0 or some such thing - you'd need to lshw -C network to see which you wireless adapter is.

---

### Post by JayStayPaid9888 on 2010-06-30
> **anewguy said:**
> It's possible you need to add b43 and ssb to the blacklist.conf file to stop default drivers from stepping on what you are trying to install.  The same applies to the restricted driver.  If you still have it enabled you must disable it before you can have any success with another driver and method.  Same  goes  for the firmware cutter.

It's also possible you need to do a ifup on wlan0 or some such thing - you'd need to lshw -C network to see which you wireless adapter is.


Thanks so much for the feedback. I decided the support forums would be a more appropriate place for this. The new thread can be found here: [http://ubuntuforums.org/showthread.php?t=1520457](http://ubuntuforums.org/showthread.php?t=1520457)

---

