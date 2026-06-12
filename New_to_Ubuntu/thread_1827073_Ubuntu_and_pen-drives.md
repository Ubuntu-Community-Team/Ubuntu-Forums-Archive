---
title: "Ubuntu and pen-drives"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by medusa93 on 2011-08-17
I am new to the world of Ubuntu but have been on WindowsXP since its release. What I want to know is how to remove pen-drives or other hard disks connected to USB ports on the laptop.

In Windows there is this routine of closing all the files on the concerned drive ---clicking the "Safely remove" tray icon -- the pop-up screen displays list of plugged in drives --choose the one you've had enough of --click close --trays icon shows the balloon notification "it is safe to remove blah blah" Sometimes Windows refuses permission to remove the drive (most of the times for God knows what reason) and then I have to be careful. Either chance my luck and yank out the drive or wait to power off the computer

How is it in Ubuntu?

---

### Post by Rex Bouwense on 2011-08-17
Merely right click the device and choose safely remove device.  Simple.:popcorn:

---

### Post by nwadams on 2011-08-17
In Nautlius (the file manager) You should see an icon next to the USB drive on the left pane that looks like an eject icon. 

The safest way to safely remove the drive is to close the programs that are using files on the pen-drive and then click that icon. You don't need to worry about if you are in the pen drive's directory tree in Nautilus. An error will pop up if something is preventing the drive from being unmounted.

If you have unity (ubuntu 11.04) you should see an icon in the launcher. You can also right click on that icon and an option will be present to unmount the drive

---

### Post by spiceminesofkessel on 2011-08-17
The drive should show up on your desktop. You can simply right-click the drive's icon and choose the option, "Safely remove." Also, when you open your Home folder, you might see the drive listed in the sidebar on the left of the window. Next to each removable drive should be an eject icon. Clicking that eject icon will safely remove the drive.

[Sorry for the redundant post. The above replies came in as I was typing this one.]

---

### Post by mkhaytman on 2011-08-17
Yikes, I've just been unplugging the drives without ejecting them first. I don't seem to have suffered any negative effects, and I've been doing this for years now... Has anyone damaged a USB drive by not "safely removing" before yanking it out of the port?

---

### Post by elgordodude on 2011-08-17
Not damaged per se, but once when I wasn't thinking I yanked a drive and then it wasn't recognized when I put it back. A reformat on another machine and all was well again, but yes you should always "safely remove drive" :)

---

### Post by bodhi.zazen on 2011-08-17
> **mkhaytman said:**
> Yikes, I've just been unplugging the drives without ejecting them first. I don't seem to have suffered any negative effects, and I've been doing this for years now... Has anyone damaged a USB drive by not "safely removing" before yanking it out of the port?

You can usually do that (yank them out), but to answer your question that is not really best practice.

You will loose any recent data that has not been written to the device and I have seen damage to the filesystem and more data loss after such behavior.

Is it so difficult to eject or remove the device or perhaps you do not value the data on your usb.

---

### Post by pi.boy.travis on 2011-08-17
I've bricked a USB drive by not ejecting it before.

---

