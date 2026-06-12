---
title: "DWL G122 Rev B1 Installation guide for Hardy 64 Bit"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by Alien.col on 2008-05-05
Hello guys:

I've been working a lot on installing this USB stick. I'm using strangeintp guide as a baseline it can be found here: [http://ubuntuforums.org/showthread.php?t=596751](http://ubuntuforums.org/showthread.php?t=596751)

I've only tested this in 64 bit installation but it might work on 32 bit.

So here it goes:

1.  Blacklist the rt2500usb driver

[PHP]sudo gedit /etc/modprobe.d/blacklist[/PHP]

and add the following line:

[PHP]blacklist rt2500usb[/PHP]

2. Reboot - The stick's lights should be off, now we can work.

3. Get the driver

a.  Go here and download the hourly CVS tarball for rt2570:[http://rt2x00.serialmonkey.com/](http://rt2x00.serialmonkey.com/)
(Hopefully you have another internet connection around).

b.  transfer the file to an easily accesible place (/home/username/Desktop, e.g.)

c. extract the file (I used ark from the GUI, you can also navigate to that directory via command line and run the "tar -xvzf filename" on it)

4.  Follow the build instructions README: go to the Module folder in the folder you just extracted and type 'make' and 'sudo make install' in terminal

5.  open a terminal.  In the command line type:

[PHP]sudo gedit /etc/modprobe.d/aliases[/PHP]

and add the line

[PHP]alias rausb0 rt2570[/PHP]

Save and close

6.  Change the wlan0 to rausb0 as follows:

[PHP]sudo gedit /etc/network/interfaces[/PHP]

Replace instances of "wlan0" with "rausb0".  It should look like this:

[PHP]auto rausb0
iface rausb0 inet dhcp[/PHP]

save and close

(leave the 'lo' lines intact)

7. Go to the Module folder where you did the 'sudo make install' and copy the file rt2570.ko to the following folder:

[PHP]/lib/modules/2.6.24-16-generic/kernel/drivers/net/wireless[/PHP]

I usually go to the console and type 'sudo nautilus' and copy the file manually

8.  Now type the following commands in console:

[PHP]sudo modprobe rt2570 ifname=rausb0[/PHP]

and

[PHP]sudo ifup rausb0[/PHP]

You'll probably get the message that says something like "rausb0 already configured", that's cool

9. Now you just added your wireless to work with the default Ubuntu connection manager. If the lights are not on it is because that default software is not configured yet to look for wireless connection. So do the following:

a. Check that the rausb0 device is there and not the wlan0 device. Go to System>Administratin>Network Tools and look for the rausb0 device from the drop down list. If it's there that's cool go to the next step, if not reboot and check again. If wlan0 persists then you might want to try and change every reference to rausb0 to wlan0 in the files you modified  above. This happened to me once in Gutsy and i had to change every rausb0 to wlan0 and the thing worked.

b. Go to the little network icon on the top right of the desktop (beside the volume icon) and do one click. Select manual configuration. Press the unlock button and check the wireless connection tab. Then you can configure to your local wireless, WEP encryption works, everything should work fine.

10. Reboot and check everything works properly.

Hopefully this will work. I tried it in Kubuntu and it didn't :(

Cheers.

---

### Post by Jackie999 on 2008-05-06
Alien.col
I tried following your guide (above) to try and install the linux rt2870 driver, as you suggested to me in this [http://ubuntuforums.org/showthread.php?t=766850](http://ubuntuforums.org/showthread.php?t=766850)  thread.

A few things I changed, for instance I blacklisted not only the windows driver rt2870, I also had to blacklist the ndiswrapper - otherwise after reboot I still had a connection.

After reboot I showed (in iwconfig)

lo            no wireless extentions
eth0        no wireless extentions
irda 0      no wireless extentions

And I had no wireless. The blue light was on on the usb stick..it seems to always be on when the lappy is on.

I went thru all your steps, changing your rt2570 to my rt2870sta ( my file is rt2870sta.ko )

In some guides the interface shows as ra0, others it shows as rausb0 - I tried either way, not knowing if it mattered.

At the " sudo ifup rausb0 " step I get " No such device" ..and the original 3 show in iwconfig (lo, eth0 and irda)

Any other suggestions?

---

### Post by Alien.col on 2008-05-08
If it says there is no such device the problem can be anywhere lol.

But something is weird when you say "irda", is that the name of your device??? There needs to be consistency in the device name, for example I use rausb0 everywhere, in the alias, in the modprobe, in the ifup and in interfaces. so if your device name defaults to irda you should use that instead of rausb0 but use it everywhere! I once had to change all of the rausb0 to wlan0 because linux wuldn't accept it any other way.

Try and not blcaklist ndiswrapper, just uninstall any driver loaded into it.

---

### Post by tuomi on 2008-10-03
> **Alien.col said:**
> 
10. Reboot and check everything works properly.

Hopefully this will work. I tried it in Kubuntu and it didn't :(

Cheers.

I´ve been tearing my hair out over this dongle since I can't get myself a stable connection against my router which is using WPA2. I see that you mention WEP in your post but do you have any experience with the former?

Last but not least to explain my quote, did you put up this tutorial after you tried it in kubuntu and it didn't work or did I misunderstand you?

---

### Post by Alien.col on 2008-10-16
You are right tuomi wpa2 seems to be a mess, in fact i have problems with wpa not only with this dongle but with other wireless systems. WEP seems to work fine though.

About kubutu, I installed kubuntu with the dongle configured in ubuntu already and I could not get it to work.

---

### Post by tuomi on 2008-10-22
Seems to be solved for me in Intrepid, works out of the box and no drops in performance as in hardy...

---

### Post by Alien.col on 2008-11-01
Lol, i was at the make install step when i realized that i had not put in the password for the wireless. It seems to be working out of the box for intrepid in kubuntu. This is great news, if only i had not suffered some weird crashes yesterday this new release would have gotten it perfect for me.

---

### Post by chocolatecheerios on 2008-11-02
Odd. If my memory doesn't serve me entirely wrong, my D-Link DWL-G122 worked out of the box on Hardy (2.6.24-19). It is Rev C1.

Broken in hardy 2.6.24-21, though. :(

---

