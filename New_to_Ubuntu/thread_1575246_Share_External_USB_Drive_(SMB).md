---
title: "Share External USB Drive (SMB)"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by cdybdahl on 2010-09-15
Here is what I am looking to accomplish:
I am setting up a media server, so my first thought was that the stability and user friendliness of Ubuntu would be the best choice. My media files live on an external HD. I would like to be able to browse to the shared folders on this drive from anywhere on the network, so that I can add and maintain content from anywhere on the LAN. The server will be headless.

Here is what I've done:
1. Install Ubuntu 10.04 LTS on an old P3 machine.
2. Booted up and plugged in my USB HD. It mounts fine.
3. Right-clicked on a folder I want to share and set up the Sharing Preferences (I want read/write access for anyone, so I checked that box, but not the anonymous/guest access box). I needed to install a couple of packages for samba before it would let me set up the share, but I did this and it appeared to work fine.
4. Set up a new samba user called xbox.
5. I went to my (original) Xbox, on which I am running XBMC, browse for smb shares, and nothing showed up. 

I also tried the instructions here, to no avail:
[http://ubuntuforums.org/showthread.php?p=2758412](http://ubuntuforums.org/showthread.php?p=2758412)

This seems like something that ought to be pretty straightforward. I understand the desire to lock things down and that smb might constitute a security risk for an inexperienced user, but I never in my wildest dreams imagined that setting up samba under Ubuntu to behave as it does on other platforms would be such a challenge.

Please help! I'm relatively inexperienced with Linux generally, but am comfortable enough with command-line stuff to be dangerous.

---

### Post by vcuncg on 2010-09-16
Check out the first post at the link below.  It worked well for me...
[http://ubuntuforums.org/showthread.php?t=1468498](http://ubuntuforums.org/showthread.php?t=1468498)

Good luck!

---

### Post by dmizer on 2010-09-16
To share an external hard drive, you will first need to provide a permanent hard-mount for the drive in /etc/fstab. Here is some good information on how to do that.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you need help, please ask.

---

### Post by cdybdahl on 2010-09-21
Thanks so much for the replies.
I am going to document things here as I do them, so that someone smarter than I can point out after the fact where it all went horribly wrong.

Note: This is all from a completely fresh install of 10.04. I wanted to make sure my messing around from earlier didn't interfere.

1. Determine the /dev address of the USB drive (partition, really, I guess): sudo fdisk -l. In my case, the address was /dev/sdb1.
2. Add a mount point for the partition: sudo mkdir /media/media. Maybe confusing, but that's what I wanted to call it.
3. Edit fstab: sudo gedit /etc/fstab.
4. Add the following line to fstab: /dev/sdb1 /media/media  auto  rw,auto,user
5. Follow the instructions in this thread for installing and configuring samba: [http://ubuntuforums.org/showthread.php?t=1502265](http://ubuntuforums.org/showthread.php?t=1502265)

I am now able to browse to my smb shares from any other location on the network. It's not terribly secure, but it works. 

Thanks again!

Edit:
After further review, the steps above do not allow read/write access to other machines on the network. Adding the option "umask=000" in fstab did the trick here. This was an important requirement for me, but you should make sure your network is locked down nice and tight if you choose this route.

---

