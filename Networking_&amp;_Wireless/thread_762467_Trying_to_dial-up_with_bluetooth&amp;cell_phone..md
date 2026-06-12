---
title: "Trying to dial-up with bluetooth&amp;cell phone."
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by socialistic on 2008-04-22
On windows, I use a bluetooth usb adapter+software to "dial up" through my cell phone to my cellular provider's data network.  Basically I load the software, double click the icon designated for my phone(this enables bluetooth and pairs the pc and phone), then click the internet button on the software interface, then click "connect" on the net connection dialog window that comes up.

I use these settings to connect at that dialog window...

Username: myphonenumber
Password: none
number to dial: #777

My phone is an Alltel Blackberry Pearl 2 (8130) smartphone/pda.  Cellular provider is Alltel.  The number used to dial up to the Alltel Data Network(internet) is #777, as stated above.

It's fairly straight-forward and simple.  I've toyed with the ubuntu bluetooth program...but can't seem to make sense of it, nor will it try to pair with my phone.  My phone finds my pc...and my pc recognizes the bluetooth usb adapter and shows my phone in the connect list...but that's where I get stuck.

I know it's possible to use this method to connect to the net on Ubuntu...I just don't know how to do it.  I found some links to various walk-throughs...but they were rather complicated.

I'm 100% brand new to Ubuntu...I've used windows since I first started messing with computers back in the early 3.1 days.  I don't know much of anything about linux...but I'm dying to learn, and try out this nice looking OS.

Any help/suggestions are greatly appreciated...and please, keep in mind that I am a complete and total 'newb' to anything linux, try to keep it simple for me. :)

---

### Post by socialistic on 2008-04-22
Update:

When my bluetooth USB adapter is plugged in, the bluetooth icon is in the tray...meaning ubuntu recognizes the device.  When I right click that icon, click "browse devices"...the dialog that appears show's my phone's address.  After a few seconds it refreshes itself and doesn't show the address anymore...it says "Blackberry 8130" which means ubuntu recognizes my phone as well.

The problem I run in to is when I highlight my phone, click connect...an error pops up.  This error says...

"obex://[00:1c:cc:be:94:54]" is not a valid location.  Please check spelling and try again.

My only option is to click "OK".  Now...what do I do to fix this?  It seems that Ubuntu does recognize my bluetooth USB adapter AND my phone, and my phone does find my computer when I do a search for devicers...but I can't figure out how to pair from pc, or pair from phone.  I think that if I can get that error fixed...it should work after I configure a few things.

Not having net on my desktop is killing me right now since it's my main computer.  I mean...I can reboot into WinXP to get online...but so far I've noticed linux is pretty useless without the net.  Right now I'm on my WinXP laptop in order to get online.  I'm using the bluetooth net right now...since it's the only form of internet I can get in my area, other than 56k dial-up...so it's used on all my computers.

Thanks in advance for the help.  :)

---

### Post by socialistic on 2008-04-23
Anyone have any suggestions or steps to fix this?

I'm S.O.L., without internet on my desktop. :(

---

### Post by DrCoolSanta on 2008-04-23
When I looked up google, I found
[http://tuxomaniac.wordpress.com/2007/12/20/airtel-gprs-on-linux-with-nokia-phone/](http://tuxomaniac.wordpress.com/2007/12/20/airtel-gprs-on-linux-with-nokia-phone/)
might be helpful to you.

Otherwise just search gogle for more results.

---

### Post by fhantazm on 2008-04-24
This may or may not be of help to you. But I found that using a cable tether is about 2x faster than the bluetooth. I am using a Moto e815 on Alltel EVDO and have reached about 1.1mbs down. The fastest Ive seen connected BT is 500k. If you have a cable for your phone, I would suggest using it. Linux had the driver for my phone preinstalled, all i had to do was run wvdialconf to make it detect and write the config file. I then edited the etc/wvdial.config file with kate, added the line "stupid mode = 1", filled in the name and password, #777 for the number, saved, ran wvdial and viola. It worked. You can also use gnome-ppp to manage the connection after the inital config file is written. Coincedentally getting bluetooth to work is very similar to this and uses the wvdial config as well. I have found a couple of links for you concerning bluetooth tether:

[http://www.spiration.co.uk/post/1307](http://www.spiration.co.uk/post/1307)

[http://www.howtoforge.com/linux_internet_access_gprs_edge_via_bluetooth_gsm_phone](http://www.howtoforge.com/linux_internet_access_gprs_edge_via_bluetooth_gsm_phone)

---

### Post by socialistic on 2008-04-26
I do have the USB cables to tether my phone to my PC, so I'll have to look in to that and see if it works.

I'll take a look at those links and see if I can get it to work.  Appreciate the help! :)

EDIT:  Ran into problems right away on the first link, second link looks a bit too complicated for me to understand.

johnny@GOD:~$ sudo apt-get install bluez-utils
Reading package lists...Done
Building dependency tree
Reading state information...Done
bluez-utilz is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

johnny@GOD:~$ sudo apt-get install blues-pin
Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package blues-pin**(I tried bluez-pin as well)**

johnny@GOD:~$ sudo apt-get install ppp
Reading package lists...Done
Building dependency tree
Reading state information...Done
ppp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


johnny@GOD:~$ hcitool scan
Device is not available: No such device.

It seems like the blues-pin is keeping me from moving to the next step.  bluez-utils and ppp look to be already installed.  Is there a factor I'm not seeing here?

---

### Post by TimHeckman on 2008-04-26
> **socialistic said:**
> I do have the USB cables to tether my phone to my PC, so I'll have to look in to that and see if it works.

I'll take a look at those links and see if I can get it to work.  Appreciate the help! :)

EDIT:  Ran into problems right away on the first link, second link looks a bit too complicated for me to understand.

johnny@GOD:~$ apt-get install bluez-utils
E: Could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: Unable to lock the administration directory /var/lib/dpkg/), are you root?

johnny@GOD:~$ apt-get install blues-pin
E: Could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: Unable to lock the administration directory /var/lib/dpkg/), are you root?

johnny@GOD:~$ apt-get install ppp
E: Could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
E: Unable to lock the administration directory /var/lib/dpkg/), are you root?

johnny@GOD:~$ hcitool scan
Device is not available: No such device.

Ignore his previous edit.  He did not utilize the "sudo" command.  I directed him in the correct direction, everything seems to be going okay.

---

### Post by socialistic on 2008-04-26
I used the correct commands after realizing I forgot sudo...ran into other problems.  I'm going to remove the bluetooth usb adapter from this laptop and plug it back in the pc, and do this all again so i can highlight the trouble areas in order for the issues to be diagnosed.  Should take about 15 minutes.

Also...I edited/updated my previous post to reflect what happens when the correct commands were used.

EDIT:

Here's some info from my terminal to give an idea of what's going on so far.

johnny@GOD:~$ sudo apt-get install bluez-utils
Reading package lists...Done
Building dependency tree
Reading state information...Done
bluez-utilz is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

johnny@GOD:~$ sudo apt-get install blues-pin
Reading package lists...Done
Building dependency tree
Reading state information...Done
E: Couldn't find package blues-pin(I tried bluez-pin as well)

johnny@GOD:~$ sudo apt-get install ppp
Reading package lists...Done
Building dependency tree
Reading state information...Done
ppp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

johnny@GOD:~$ hcitool scan
Scanning ...
00:1C:CC:BE:94:54 BlackBerry 8130

johnny@god:~$ sudo hcitool cc 00:1C:CC:BE:94:54**(pairs phone and pc correctly)**

johnny@god:~$ sudo hcitool auth 00:1C:CC:BE:94:54
Not Connected.**(phone and pc are no longer paired as soon as I enter this auth command.)**

**I tried the sdptool browse command...and it worked...my dial-up networking rfcomm channel was 3. It only worked if I did the cc command, and not the auth command(which instantly unpairs my phone and pc if entered.)**

**After my system halted/froze, and I rebooted...I tried the two above commands again(cc and auth), here is what happened.**

johnny@god:~$ sudo hcitool cc 00:1C:CC:BE:94:54
Can't create connection: Input/Output Error.
johnny@god:~$ sudo hcitool auth 00:1C:CC:BE:94:54
Not Connected.

**So now the cc command doesn't even work, auth command still doesn't work. I also tried edited /etc/bluetooth/rfcomm.conf...but it keeps telling me I don't have permission to save the changes.**

**Why did the cc command work before, and now it doesn't work/pair anymore? Why doesn't the auth command work at all, and why did it keep un-pairing my phone/pc when cc command did work/pair? Why can't I save the changes I make to /etc/bluetooth/rfcomm.conf? Why doesn't blues-pin install?**

**Thank you for your time.**

---

### Post by maks_zbogar on 2008-07-16
I have googled "Couldn't find package blues-pin" and all it finds is this thead. 

I too want to use my cell phone to connect to gprs via bluetooth and I have exactly same problem when I try to install blues-pin:

Couldn't find package blues-pin

Should I add any repositories?
Any help would be appreciated.

---

### Post by galileon on 2009-03-14
[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284073/comments/2](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284073/comments/2)

---

