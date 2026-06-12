---
title: "Wireless Card not supported... Screwed?"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by ShoeSh1ne on 2008-10-30
According to Device Manager, my wireless card is 'Wirelss LAN PCI 802.11 b/g adapter WN5301A' and viewing the properties for that show the manufacturer as Liteon.

Liteon is not listed on this list:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

So that that mean I won't be able to get online in Ubuntu no matter what?

Thank you.

---

### Post by inxygnuu on 2008-10-30
do you have the CD? If so, I know a very good, and easy way to help:).

---

### Post by Ayuthia on 2008-10-30
It looks like people are using ndiswrapper to make this card work.  You will need to find the XP drivers for them (.inf and .sys files -- they might have the wn5301a prefix).  The ndiswrapper packages are on the live CD so you can install ndiswrapper-utils-1.9 so that you can install them via the Terminal or I think that ndisgtk is also on the live CD and that is the GUI way to install.

---

### Post by ShoeSh1ne on 2008-10-30
> **inxygnuu said:**
> do you have the CD? If so, I know a very good, and easy way to help:).

For the modem?  No, came with the computer.

---

### Post by ShoeSh1ne on 2008-10-30
> **Ayuthia said:**
> It looks like people are using ndiswrapper to make this card work.  You will need to find the XP drivers for them (.inf and .sys files -- they might have the wn5301a prefix).  The ndiswrapper packages are on the live CD so you can install ndiswrapper-utils-1.9 so that you can install them via the Terminal or I think that ndisgtk is also on the live CD and that is the GUI way to install.

Where would I find the drivers?  Using ndiswrapper?

What are the steps to doing so... Thank you.

---

### Post by inxygnuu on 2008-10-30
> **ShoeSh1ne said:**
> For the modem?  No, came with the computer.

what do you mean? I am talking about that CD that comes with the card when you buy it. It has an .inf file that 'windows wireless drivers' (wwd)(same as ndiswrapper) can read, and therefore, if you extracted them using the CD and wwd, you could use that to connect. That is what i will do, it worked for me, until my system got screwed, during beta.:(

hope it works,
Evan;)

---

### Post by Ayuthia on 2008-10-30
> **ShoeSh1ne said:**
> For the modem?  No, came with the computer.
If it came with the computer, the files are somehwere inside of Windows.  You will most likely need to do a search for WN5301A.inf and WN5301A.sys.  This is a guess though.  I am not for sure what the filenames are for them.  The threads that I saw look like that they are using wn5301a.inf.

---

### Post by ShoeSh1ne on 2008-10-30
> **inxygnuu said:**
> what do you mean? I am talking about that CD that comes with the card when you buy it. It has an .inf file that 'windows wireless drivers' (wwd)(same as ndiswrapper) can read, and therefore, if you extracted them using the CD and wwd, you could use that to connect. That is what i will do, it worked for me, until my system got screwed, during beta.:(

hope it works,
Evan;)

Well, I didn't buy the card, it came with my computer, already installed.

---

### Post by ShoeSh1ne on 2008-10-30
> **Ayuthia said:**
> If it came with the computer, the files are somehwere inside of Windows.  You will most likely need to do a search for WN5301A.inf and WN5301A.sys.  This is a guess though.  I am not for sure what the filenames are for them.  The threads that I saw look like that they are using wn5301a.inf.

Let's say I find the file, what's next?

---

### Post by Ptero-4 on 2008-10-30
put both files in a folder and put the folder somewhere that you know it isn't going to be deleted accidentaly (I put it in /etc). Then install with oyur preferred method. For cli use > sudo ndiswrapper -i ***/path/to/driver***
then add ndiswrapper to your /etc/modules file to ensure it lods automatically at boot time.

---

### Post by Ayuthia on 2008-10-30
> **ShoeSh1ne said:**
> Let's say I find the file, what's next?

If you install ndisgtk, it would just be a matter of running the application and entering the location of that driver.

If you are using ndiswrapper-utils-1.9, you will have to be in the Terminal and go to the directory where the .inf and .sys file is located and doing the following:
```
sudo ndiswrapper -i wn5301a.inf
ndiswrapper -l
```If it says that the device is present then you can do the following:
```
sudo ndiswrapper -ma
sudo modprobe ndiswrapper
echo ndiswrapper|sudo tee -a /etc/modules
```And that should be it.

The GUI version is much easier if you do not have too much experience with Linux and just want to get it installed.

---

### Post by ShoeSh1ne on 2008-10-30
> **Ptero-4 said:**
> put both files in a folder and put the folder somewhere that you know it isn't going to be deleted accidentaly (I put it in /etc). Then install with oyur preferred method. For cli use 
then add ndiswrapper to your /etc/modules file to ensure it lods automatically at boot time.

Excellent, now do I just add ndiswrapper to the file or do I add the whole string that you posted with path to the drivers?

---

### Post by ShoeSh1ne on 2008-10-30
> **Ayuthia said:**
> If you install ndisgtk, it would just be a matter of running the application and entering the location of that driver.

If you are using ndiswrapper-utils-1.9, you will have to be in the Terminal and go to the directory where the .inf and .sys file is located and doing the following:
```
sudo ndiswrapper -i wn5301a.inf
ndiswrapper -l
```If it says that the device is present then you can do the following:
```
sudo ndiswrapper -ma
sudo modprobe ndiswrapper
echo ndiswrapper|sudo tee -a /etc/modules
```And that should be it.

The GUI version is much easier if you do not have too much experience with Linux and just want to get it installed.


I'm new to Linux so GUI sounds like the way to go.  

Did a quick browse and I can't seem to locate how to install ndisgtk.

---

### Post by Ayuthia on 2008-10-30
> **ShoeSh1ne said:**
> I'm new to Linux so GUI sounds like the way to go.  

Did a quick browse and I can't seem to locate how to install ndisgtk.

It should be on the live CD.  You should be able to add the CD in 
Synaptic.  If you have a working wired connection, you can just install ndisgtk through Synaptic.  If you don't and can't figure out how to add the CD through Synaptic, you can go into the Terminal and do the following:
```
sudo apt-cdrom add
```It will ask you to insert the CD.  Once you have done that, you can then do the following:
```
sudo apt-get update
sudo apt-get install ndisgtk
```It should install the package for you.

Hope that helps!

---

### Post by ShoeSh1ne on 2008-10-31
I've done the steps you said, but now I need to know how to actually run ndisgtk.

---

### Post by ShoeSh1ne on 2008-10-31
Well, I found the Windows Wireless program(?) after clicking System > Admin. and installed the driver that way.

It worked!  I'm stoked.  Thanks for everybody's help.

Now will it automatically connect to the network each time or is there another step involved?

Does it matter that the connection is listed under Wired?

---

### Post by Ayuthia on 2008-10-31
> **ShoeSh1ne said:**
> Well, I found the Windows Wireless program(?) after clicking System > Admin. and installed the driver that way.

It worked!  I'm stoked.  Thanks for everybody's help.

Now will it automatically connect to the network each time or is there another step involved?

If it automatically connected this time, it should do it in the future.  If for some reason the wireless does not come up, you can go into the Terminal and type:
```
echo ndiswrapper|sudo tee -a /etc/modules
```This will have the system load the ndiswrapper module after it loads all the kernel modules.

Glad to see that you found the application and got it working!

---

### Post by ShoeSh1ne on 2008-10-31
When I got it to work I was using VMPlayer... now to install and see if I can replicate it.

---

### Post by ShoeSh1ne on 2008-10-31
Ok that didn't go as planned.  I installed Ubuntu successfully and got it up and running.

Went to install ndisgtk using 

> sudo apt-cdrom add

And got an error saying the drive could not be mounted.

Tried using ndiswrapper by doing

> sudo ndiswrapper -i path/to/driver/here

And got an invalid command error

What now?

For the record, I download Ubuntu from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Is that the same thing as the Live CD found here: [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

If not, when will a Live CD for 8.10 be released/where can I find it.
Edit:  On second thought, that shouldn't matter because like I said, I got it to work in VMPlayer.

---

### Post by ShoeSh1ne on 2008-11-01
bumpity.

---

### Post by ShoeSh1ne on 2008-11-01
Another update:

Chose to get wired so I could get ndisgtk and update - Got everything to work flawlessly, was able to recognize a few wireless networks, and was able to select mine and connect.

Noticed that there was an update though Update Manager so I updated and it prompted me to restart, so I restarted and everything was gone.  Wouldn't recognize networks... this is a joke.

---

### Post by Ptero-4 on 2008-11-09
> **ShoeSh1ne said:**
> Excellent, now do I just add ndiswrapper to the file or do I add the whole string that you posted with path to the drivers?
Just ndiswrapper. The driver path was stored in the config file when you did the initial configuration.

---

