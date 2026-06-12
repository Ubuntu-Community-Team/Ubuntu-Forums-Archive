---
title: "Beginner to Linux having problems with connecting..."
date: 2008-08-20
forum: Networking &amp; Wireless
---

### Post by e_torano on 2008-08-20
Hello there. I am completely new to Linux at all but decided to install Ubuntu 8.04 about a week ago. I then decided to try and connect it to my wireless network, already working on my vista computer and an xp computer with no problem. So, I went to [http://www.linuxemporium.co.uk/products/wireless/#pid88171](http://www.linuxemporium.co.uk/products/wireless/#pid88171)
after a quick google search and ordered the "Edimax 54 Mbps Wireless USB stick" as seen on the page. it arrived the other day but when i tried to use it, I couldn't get it to work. I had a look round here but couldn't really find anything and I also went through everything on the supplied CD but that didn't help either.

So, if anyone can help, i'd really appreciate it but please remember that I'm new to Linux and will probably need everything explained pretty well ;)
Thanks.

---

### Post by e_torano on 2008-08-24
So, no one can help? Please?

---

### Post by Hazer on 2008-08-24
Hello, I'm not sure if Ubuntu has the drivers, but if it has usually there will be an icon with 2 computers and an exclamation mark near the clock in the top right hand corner of the sreen.  click it and select your wireless network, and enter the pass phrase  (wep or wpa key)

---

### Post by burnit on 2008-08-24
You ndiswrapper to simulate driver and XP driver *.inf about your card

learn about ndiswrapper

---

### Post by e_torano on 2008-08-25
> **Hazer said:**
> Hello, I'm not sure if Ubuntu has the drivers, but if it has usually there will be an icon with 2 computers and an exclamation mark near the clock in the top right hand corner of the sreen.  click it and select your wireless network, and enter the pass phrase  (wep or wpa key)

Thanks for replying. However, I have tried this and no networks show up ;)

> **burnit said:**
> You ndiswrapper to simulate driver and XP driver *.inf about your card

learn about ndiswrapper
This sounds hopeful- thanks! I'll try doing this then get back to you if I need help.

---

### Post by Crafty Kisses on 2008-08-25
Try looking at this > [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by ugm6hr on 2008-08-25
Those Edimax USB wifi sticks are supposed to be supported by Ubuntu / Network Manager, but it's not perfect.

I would advise against ndiswrapper (altho it is an option).

My suggestion (which I got to work with [Edimax 7318usg]("http://www.linuxemporium.co.uk/products/wireless/#pidR26728") )
[http://ubuntuforums.org/showthread.php?p=5468482#post5468482](http://ubuntuforums.org/showthread.php?p=5468482#post5468482)

---

### Post by e_torano on 2008-08-25
> **Codename said:**
> Try looking at this > [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

> **ugm6hr said:**
> Those Edimax USB wifi sticks are supposed to be supported by Ubuntu / Network Manager, but it's not perfect.

I would advise against ndiswrapper (altho it is an option).

My suggestion (which I got to work with [Edimax 7318usg]("http://www.linuxemporium.co.uk/products/wireless/#pidR26728") )
[http://ubuntuforums.org/showthread.php?p=5468482#post5468482](http://ubuntuforums.org/showthread.php?p=5468482#post5468482)

Thanks to both of you. I'll look at ugm6hr's suggestion first seeing as it's already worked with a similar stick, but, if that fails I'll look at Ndiswrapper. Thanks a lot:)

---

### Post by Crafty Kisses on 2008-08-25
No problem, please post back. :)

---

### Post by e_torano on 2008-08-25
> **Codename said:**
> No problem, please post back. :)

Ok, will do.

By the way, I'm looking through the given link ([http://ubuntuforums.org/showthread.php?p=5468482#post5468482)and](http://ubuntuforums.org/showthread.php?p=5468482#post5468482)and) it says:

> 
I followed instructions 1-13, then installed RutilT...

Does that mean to follow the instructions 1-13 in the .pdf supplied on the Linux CD that came with the stick?

---

### Post by owenll on 2008-08-25
I've bought some stuff from linuxemporium (a laptop and a wireless usb stick like yours) in the past. I found them very helpful and easy to deal with. Have you tried giving them a ring? Obviously not today as it's a Bank Holiday!

0121 313 3857

It does say on their website...

**This card uses the RT2571 chipset and works "out of the box" with Ubuntu 8.04 Hardy Heron.**

...so they should provide you with help if it doesn't

---

### Post by e_torano on 2008-08-25
> **owenll said:**
> I've bought some stuff from linuxemporium (a laptop and a wireless usb stick like yours) in the past. I found them very helpful and easy to deal with. Have you tried giving them a ring? Obviously not today as it's a Bank Holiday!

0121 313 3857

It does say on their website...

**This card uses the RT2571 chipset and works "out of the box" with Ubuntu 8.04 Hardy Heron.**

...so they should provide you with help if it doesn't

Haha, thanks. I've actually sent them an email. 

**EDIT: sorted, found it after a while :P**

---

### Post by e_torano on 2008-08-25
Ok, I installed NDISwrapper and now I need to find the following drivers:

> rt73.inf and rt73.sys from directory ndis5 in data1.cab on CD that came with the device.

However, I do not have this CD as my device is manufactured by another company that's device has the same ID. I was wondering if anyone knows where I can get this? I tried the website of the device manufacturers but all that gave me was an exe file :(

---

### Post by ugm6hr on 2008-08-25
> **e_torano said:**
> Ok, will do.

By the way, I'm looking through the given link ([http://ubuntuforums.org/showthread.php?p=5468482#post5468482)and](http://ubuntuforums.org/showthread.php?p=5468482#post5468482)and) it says:

Does that mean to follow the instructions 1-13 in the .pdf supplied on the Linux CD that came with the stick?

No.

Look at post #1 in that link for steps 1-13 [http://ubuntuforums.org/showthread.php?p=2395871#post2395871](http://ubuntuforums.org/showthread.php?p=2395871#post2395871)

---

### Post by e_torano on 2008-08-25
> **ugm6hr said:**
> No.

Look at post #1 in that link for steps 1-13 [http://ubuntuforums.org/showthread.php?p=2395871#post2395871](http://ubuntuforums.org/showthread.php?p=2395871#post2395871)

Right, thanks.

I tried setting up that other way (ndiswrapper) and now it's finding my network and (sometimes) connecting but I still can't connect to the internet and when I go to network info it comes up blank... :confused:

God, I'm a noob at linux lol

---

### Post by e_torano on 2008-08-25
Ok, I tried your way ugm6hr. It still didn't work even after doing everything *exactly* as told. To show what's wrong, I took a screen shot. This is below:

[IMG]http://i225.photobucket.com/albums/dd201/dabigE_2007/Screenshot-1.png[/IMG]

As you can see, the device is finding the network, connecting then doing nothing much else really lol.

I have no idea what's wrong in truth. I entered all the correct settings and everything :(

---

### Post by e_torano on 2008-08-25
Can anyone help? Sorry for BUMPing but I'm getting a bit desperate lol

---

### Post by ugm6hr on 2008-08-25
> **e_torano said:**
> Ok, I tried your way ugm6hr. It still didn't work even after doing everything *exactly* as told. To show what's wrong, I took a screen shot. This is below:


The screenshot shows that the device is still using ndiswrapper, not the serialmonkey RT drivers.

If you want to try my method, you will have to blacklist ndiswrapper first.  To do this, add an extra line to the blacklist file (step 11) with:
```
ndiswrapper
```

Then reboot, and follow the steps again.

NB: You will need wired internet to get the files - if you don't - we'll have to do some transferring of files manually.

---

### Post by e_torano on 2008-08-26
> **ugm6hr said:**
> The screenshot shows that the device is still using ndiswrapper, not the serialmonkey RT drivers.

If you want to try my method, you will have to blacklist ndiswrapper first.  To do this, add an extra line to the blacklist file (step 11) with:
```
ndiswrapper
```

Then reboot, and follow the steps again.

NB: You will need wired internet to get the files - if you don't - we'll have to do some transferring of files manually.

Ok, thanks ugm6hr. I don't currently have the internet working on the ubuntu computer at all. I have to either use this machine, my family's XP machine or a laptop :)

---

### Post by ugm6hr on 2008-08-26
> **e_torano said:**
> Ok, thanks ugm6hr. I don't currently have the internet working on the ubuntu computer at all. I have to either use this machine, my family's XP machine or a laptop :)

Blacklist ndiswrapper first, make sure **rt73** is not blacklisted, then reboot.

Download this file somewhere: [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)

Transfer the above file to your Ubuntu machine (In "Home Folder").  Then follow step 4 (instead of 3).

The rest should work just fine (depending on what else you did when trying to use ndiswrapper).

What security do you use on your router?

---

### Post by e_torano on 2008-08-26
> **ugm6hr said:**
> Blacklist ndiswrapper first, make sure **rt73** is not blacklisted, then reboot.

Download this file somewhere: [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)

Transfer the above file to your Ubuntu machine (In "Home Folder").  Then follow step 4 (instead of 3).

The rest should work just fine (depending on what else you did when trying to use ndiswrapper).

What security do you use on your router?

I've got a WEP key on my router but I know the actual code anyway. When setting up ndiswrapper, I followed all the steps in the guide. I'll try what you said right now then be back to you very soon. thanks for all this.

so, how do i blacklist ndiswrapper?

---

### Post by e_torano on 2008-08-26
Right now I just got this, i'm not sure if it's a problem:

[IMG]http://i225.photobucket.com/albums/dd201/dabigE_2007/Screenshot.png[/IMG]

(look at the 2nd last line in the terminal...)

---

### Post by ugm6hr on 2008-08-26
Blacklist ndiswrapper using point 11 - add **ndiswrapper** to the file.

Not sure that the make install "error" is a problem.

Just keep going and see what happens.

---

### Post by e_torano on 2008-08-26
> **ugm6hr said:**
> Blacklist ndiswrapper using point 11 - add **ndiswrapper** to the file.

Not sure that the make install "error" is a problem.

Just keep going and see what happens.

Ok then. I'll go ahead now.

---

### Post by e_torano on 2008-08-27
Ok, I retried again (I blacklisted ndiswrapper, whether I did it correctly or not is another matter :P) and this is what I'm now getting:

[IMG]http://i225.photobucket.com/albums/dd201/dabigE_2007/Screenshot-2.png[/IMG]

Notice the odd symbol where the network status is (not sure what on earth it is lol...)

---

### Post by ugm6hr on 2008-08-27
Start from the beginning:
```
lshw -class network
iwconfig
```

I assume you are using WEP with a hex key.

EDIT: 
The network status icon is Network Manager.  That is the "I'm trying to connect to a wifi network" signal.
I will re-read the previous posts, but I was suggesting you use Rutilt or the command line.  You have to remove network manager to do this.

---

### Post by ugm6hr on 2008-08-27
OK.  Re-updated myself on your situation.  A summary for my benefit (please check to ensure this is all correct):

1. Installed then blacklisted ndiswrapper
2. No wired internet on desktop
3. Installed serialmonkey rt73 driver
4. Network Manager still installed
5. Intermittent success with ndiswrapper
6. WEP security on router

I would suggest using the command line to connect for now.  I assume you don't need wireless roaming (if this is not true, let me know, and we can use RutilT later).

After posting the details from my prior post for me to review, if everything is OK - you can proceed as below:
1. Check that you followed steps 1-13 (i.e. don't bother with 14) here: [http://ubuntuforums.org/showpost.php?p=2395871&postcount=1](http://ubuntuforums.org/showpost.php?p=2395871&postcount=1)
2. In Terminal: sudo aptitude remove network-manager
3. In Terminal: gksu gedit /etc/modprobe.d/blacklist
Check that *ndiswrapper* is on a separate line on its own in that file - if not, add it and resave.
4. Reboot
5. Follow advice here for WEP (assuming that is your security on router): [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by e_torano on 2008-08-27
> **ugm6hr said:**
> OK.  Re-updated myself on your situation.  A summary for my benefit (please check to ensure this is all correct):

1. Installed then blacklisted ndiswrapper
2. No wired internet on desktop
3. Installed serialmonkey rt73 driver
4. Network Manager still installed
5. Intermittent success with ndiswrapper
6. WEP security on router

I would suggest using the command line to connect for now.  I assume you don't need wireless roaming (if this is not true, let me know, and we can use RutilT later).

After posting the details from my prior post for me to review, if everything is OK - you can proceed as below:
1. Check that you followed steps 1-13 (i.e. don't bother with 14) here: [http://ubuntuforums.org/showpost.php?p=2395871&postcount=1](http://ubuntuforums.org/showpost.php?p=2395871&postcount=1)
2. In Terminal: sudo aptitude remove network-manager
3. In Terminal: gksu gedit /etc/modprobe.d/blacklist
Check that *ndiswrapper* is on a separate line on its own in that file - if not, add it and resave.
4. Reboot
5. Follow advice here for WEP (assuming that is your security on router): [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Yes, that is all correct. once again, thank you very much. you have been a great help :)

---

### Post by e_torano on 2008-08-28
Ok, I'm going to try using what was said above now. Hopefully this will get it working :)

---

### Post by e_torano on 2008-08-28
Ok, that worked :) (using ubuntu atm) however, every time I restart the computer or anything, I have to enter all the info into the terminal again (only the WEP stuff provided before). Is there a way to stop me having to do this?

---

### Post by ugm6hr on 2008-08-28
> **e_torano said:**
> Ok, that worked :) (using ubuntu atm) however, every time I restart the computer or anything, I have to enter all the info into the terminal again (only the WEP stuff provided before). Is there a way to stop me having to do this?

Yes.  It was just worth ensuring that it works first...

```
gksudo gedit /etc/network/interfaces
```

Add this to the file (note similarities to manual entries - with "pre-up"):

```

auto wlan0
iface wlan0 inet dhcp
 pre-up ifconfig wlan0 down
 pre-up dhclient -r wlan0
 pre-up ifconfig wlan0 up
 pre-up iwconfig wlan0 essid ESSID
 pre-up iwconfig wlan0 key HEX_KEY
 pre-up iwconfig wlan0 mode Managed
 pre-up dhclient wlan0

```

Then reboot.

Keep your fingers crossed - it should hopefully work without the manual Terminal commands!

---

### Post by e_torano on 2008-08-28
> **ugm6hr said:**
> Yes.  It was just worth ensuring that it works first...

```
gksudo gedit /etc/network/interfaces
```

Add this to the file (note similarities to manual entries - with "pre-up"):

```

auto wlan0
iface wlan0 inet dhcp
 pre-up ifconfig wlan0 down
 pre-up dhclient -r wlan0
 pre-up ifconfig wlan0 up
 pre-up iwconfig wlan0 essid ESSID
 pre-up iwconfig wlan0 key HEX_KEY
 pre-up iwconfig wlan0 mode Managed
 pre-up dhclient wlan0

```

Then reboot.

Keep your fingers crossed - it should hopefully work without the manual Terminal commands!

Thank you very much ugm6hr for all your help! Lol, I'll have to give you more thanks :)

I had to open the file through the file browser then save it to the desktop and paste it to the directory /etc/network using sudo but oh well.

---

