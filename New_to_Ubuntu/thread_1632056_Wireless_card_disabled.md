---
title: "Wireless card disabled?"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by Nahjil567 on 2010-11-27
Ok I am very novice user. I am having issues connecting to my wireless network. I have a Airforce One Broadcom BCM4318. Atleast that is what sudo lshw -c network is telling me. I tried blacklisting bcm43xx b43 and b43legacy then using ndiswrapper to install a .inf driver file that was supposed to be the correct driver for my network card. Still says its disabled. Though now the network notification that I could click on to connect to a network say that the device is not ready... I don't really understand what I have been doing. Anyone have any idea?

---

### Post by Nahjil567 on 2010-11-27
Thought I should add the network notification tab wasn't listing anything before I did the driver ndiswrapper thing. It just said not available.

---

### Post by Hippytaff on 2010-11-27
Have you tried
```

rfkill unblock all

```
might have a hard or soft block going on :-)

---

### Post by Nahjil567 on 2010-11-27
Thank you, I tried it and it is still telling me that the device is not ready.

---

### Post by anewguy on 2010-11-27
First, let's back up to a clean slate:

- if you installed ndisgtk with ndiswrapper (believe me, it makes your life a LOT easier when using ndiswrapper), then open ndisgtk (System/Administration/Windows Wireless Drivers) and delete any existing devices

- if you only installed ndiswrapper and not ndisgtk:

[LIST]
[*]open a terminal window (Applications/Accessories/Terminal) and type:
[*]sudo ndiswrapper -l <press enter> That's a lower case "L" for "List"
[*]For each device returned above:  sudo ndiswrapper -e xxxxx <press enter> Where xxxxx is a device returned on the list command
[*]Repeat the above 2 steps until the list returns nothing
[/LIST]

- reverse any changes you made to the blacklist.conf file

We should be back to a clean slate that way.  

Now, let's work on getting this working:

- IF you can temporarily hardwire your PC to your router:[LIST]
[*]open a terminal window (Applications/Accessories/Terminal)
[*]type sudo apt-get update <press enter> and wait for this to finish.  If prompted for a password, it is your normal password but it will not show on the screen as you type it.
[*]Now go to System/Administration/Additional Drivers.  If there is a driver listed there, such as the STA driver, be sure to enable it.  It may want to download from the net while it is installing.  Wait for this to finish.
[*]physically disconnect the hardwire connection to your router
[*]right-click on the netwok manager icon and be sure "Enable Wireless" shows and is enabled.  If it doesn't show, stop and post back.  If it shows but isn't enabled, check it to enable it.
[*]wait a minute or 2
[*]left-click on the network manager icon and see if any wireless networks show.
[*]remember that if it is a hidden network (the router is not broadcasting the ESSID), you must left-click on the network manager icon and chose "Connect To Hidden Wireless Network"
[*]encryption and encryption key(s)/passphrase must match
[*]if the first time connecting with this adapter to your router, and your router has MAC filtering, you'll need to add the MAC address of the adapter to the MAC list in the router before you can connect
[*]If you get it working this way, delete ndiswrapper (and ndisgtk if you installed it)
[/LIST]

- IF you CANNOT temporarily hardwire a connection to your router:
[LIST]
[*]you have apparently already installed ndiswrapper.  Be sure you have both the ndiswrapper common and the ndiswrapper utilities installed.
[*]install ndisgtk (you can get this from the LiveCD at /pool/main/n/ndisgtk)
[*]be sure you are using the Windows XP drivers for your adapter ONLY.  Windows 7, etc., drivers will not work.  They look like they are loaded but they will not work and the device will not become available.  Also be sure to match the "type" - if regular ubuntu the drivers must be 32-bit, if you loaded 64-bit ubuntu then the drivers must be 64-bit
[*]copy the .inf and .sys files for your driver to you desktop
[*]start ndisgtk via System/Administration/Windows Wireless Drivers
[*]do a "new", and point it to your desktop and the .inf file for your driver
[*]wait a couple of minutes
[*]right-click on the network manager icon and see if the "Enable Wireless" shows and is enabled.  If it doesn't show, stop and post back.  If it shows but is not enabled, enabled it.
[*]left-click on the network manager icon and see if networks show
[*]remember that if it is a hidden network (the router is not broadcasting the ESSID), you must left-click on the network manager icon and chose "Connect To Hidden Wireless Network"
[*]encryption and encryption key(s)/passphrase must match
[*]if the first time connecting with this adapter to your router, and your router has MAC filtering, you'll need to add the MAC address of the adapter to the MAC list in the router before you can connect
[/LIST]

Let us know what happens or if you have any questions.

Dave ;)

---

### Post by Hippytaff on 2010-11-27
Welcome back Dave :-) my god, I've missed your knowledge :-)
phew

---

### Post by anewguy on 2010-11-27
Thanks for the welcome!  My head is feeling much better now.  Besides the headaches, it was wierd not being able to "think".  I would have some thought in my mind or be midway through a sentence and it would just all disapear.  Only had liability on the car, so no car now for quite a long time (several months) but I can ride the bus so that's okay.

Dave ;)

---

### Post by Nahjil567 on 2010-11-27
Well I have gotten ndistgk installed and the previous drivers uninstalled. I am stuck on how to reverse what I did to the blacklist. this is the command I used to do that. echo -e "blacklist/bcm43xx/nblacklist b43/blacklist b43legacy/nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist 
Thank you for your time.

---

### Post by anewguy on 2010-11-27
If you:

sudo gedit /etc/modprobe.d/blacklist 

you will see a line for each of the items you were blacklisting.  However, I'm not sure if it makes any difference - it you indeed just echoed to /etc/modprobe.d/blacklist I don't think it sees that file now - it was changed to /etc/modprobe.d/blacklist.conf a while ago.  So you may want to check.  

Also note that when using ndisgtk you don't have to do any edits, modprobe's, etc. - ndisgtk takes care of this for you.

Dave ;)

- Gotta go for a while - perhaps Hippytaff can help you on the rest.  I'l check back later.

---

### Post by Nahjil567 on 2010-11-27
Thank you I will check.

---

### Post by Nahjil567 on 2010-11-27
I have to be leaving for work now, so it will be awhile before I can check this. I got a driver set from fedora's wiki on my particular issue. "bcmwl5.inf" was the file name. It is on my desktop and loaded. The ndistgk Says hardware:yes although sudo lshw -C network is still telling me disabled. I will try once I get home to redownload and make sure I have the 32 bit version. Anything else I should check? I do not have the ability to hardwire the computer at the moment. I will work on that though.

---

### Post by pastalavista on 2010-11-27
I had your card (bcm4318) in a desktop that I've since sold and the driver I needed was "b43-fwcutter" which is open source and can be found in Synaptic.

---

### Post by Hippytaff on 2010-11-27
> **pastalavista said:**
> I had your card (bcm4318) in a desktop that I've since sold and the driver I needed was "b43-fwcutter" which is open source and can be found in Synaptic.

Can you explain in detail how you did it? just because I'm an amateur and would benefit from a step by step account...for future reference, if you can be arsed :-)

Thanking you in advance :-D

---

### Post by pastalavista on 2010-11-27
You'll need to connect to the router via ethernet cable to download the packages. After connecting, run System-->Administration-->Hardware Drivers which should automatically download 'b43-fwcutter' from the repositories and give you the option to 'Activate' it. After which, a reboot should have your wireless up and running.

---

### Post by Hippytaff on 2010-11-27
Thanks for that...remember to mark the thread as solved :-) you know why :-D

---

### Post by anewguy on 2010-11-27
EDIT-EDIT:  This almost sounds like a mismatch between OS type and driver type.  Be *SURE* the driver you are using in ndiswrapper is the Windows XP one - nothing else will work.  Also be absolutely sure you have match type - 32-bit or 64-bit.  Usually this results in the error you are seeing.

(I removed text that was here about the blacklist.conf file).

What I would like to see is:

a listing of your /etc/modprobe.d/blacklist.conf file

the output of ndiswrapper -l (lower case "L")

a screen print of the ndisgtk screen showing the device as active

the output of iwconfig

the output of lshw -C network

If you decide to try the firmware cutter, there is no need to go online for the firmware cutter - it is on the LiveCD as well, in:

/pool/main/b/b43-fwcutter


They put it there, just like they put ndiswrapper and ndisgtk in /pool/main/n, exactly for situations like this:  the user has no way to get online, their wireless doesn't work, and they need the tools.  My understanding is that the firmware cutter isn't a driver by itself, but that it grabs the firmware from the device.

After you boot Ubuntu, put the LiveCD in the drive - if it says a software CD is detected just cancel.  Now use "Places" and navigate to the /pool/main/b/b43-fwcutter on the CD, double-click the file and the installation will begin.  If it asks for a password just use your regular password - it won't show as you type it.

Dave ;)

EDIT:  Back the last time when I had a BCM 4318, I think the file was bcmwl5a.inf and .sys.  I have no idea if it makes much difference or not.

---

### Post by Nahjil567 on 2010-11-28
Ok I'm just gonna go buy a new network card. That way I will have the correct drivers and really it is way past time anyway this card is 4 years older then the computer it is installed on which is 3 years old itself. Thank you all for trying and I will post if I have issues with the new card.

---

### Post by anewguy on 2010-11-28
Please oh PLEASE check the online list of cards/adapters that work with ubuntu BEFORE you buy a new one!  Just because it's new doesn't mean it will work without still needing to fool around with loading drivers.  If you want to avoid doing that with a new one, and want it to "just work", please check the list, check the forum, and ask about the one(s) you're looking at on the forum before you ever buy!

Dave ;)

---

### Post by Nahjil567 on 2010-11-28
ok I wanted to get this going as I have been trying for awhile and yeah here is some screen shots of what I am getting

---

### Post by Nahjil567 on 2010-11-28
I was able to finally get online. I used b43-fwcutter. I had an error and on further investigation I had to patch it manually. I would like to thank everyone who attempted to help me out. I am now marking this solved.

---

### Post by anewguy on 2010-11-29
Glad it's working for you!

Dave ;)

---

