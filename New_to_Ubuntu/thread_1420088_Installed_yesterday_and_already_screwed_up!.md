---
title: "Installed yesterday and already screwed up!"
date: 2010-03-02
forum: New to Ubuntu
---

### Post by scc1909 on 2010-03-02
I downloaded 9.10 yesterday onto my Averatec 3250 laptop w/WinXP Pro, followed the instructions to make a CD, and got up and running without any notable issues. Surfed the web, logged into my webmail, played with the desktop, etc. So far, so good.

This morning I booted up in Unbuntu and pretty much right away got a notice saying it needed to download 244 mb of updates, so I clicked yes and went about surfing while the download ran in the background. At some point I clicked the shut-down icon to reboot to XP to get my Thunderbird email ready to move over, forgetting that I had a download running in the background.

After some housecleaning in XP I rebooted to Ubuntu, but it stalled out without getting to the login screen. Oops! So I tried rebooting in safe mode...same result. After a couple of unsuccessful reboot attempts I looked in Ubuntu's help section where it suggests using Windows' uninstall utility. That worked fine and Ubuntu's uninstall wizard indicated that the uninstall was successful. I made sure the Live CD was in the drive and attempted a reboot to Ubuntu with no luck. All I get are some lines of error messages.

What should I do now?

Thanks in advance!

---

### Post by Ozymandias_117 on 2010-03-02
Trying to understand, did you set it up as a dual-boot, or did you install ubuntu inside of windows using wubi?

---

### Post by Ghost|BTFH on 2010-03-02
The method to fix this depends on your determination:

Option A) Reinstall.  If you created a separate partition for **/home**, don't format it, just relabel it to **/home** again and everything you've set up so far will still be there.

Option B) Get Ubuntu to boot up to the command line and use it to complete the upgrade using:

[I]sudo apt-get update
sudo apt-get upgrade
sudo reboot[/I]

Which should fix everything.

Cheers,
Ghost|BTFH

---

### Post by scc1909 on 2010-03-02
> **Ozymandias_117 said:**
> Trying to understand, did you set it up as a dual-boot, or did you install ubuntu inside of windows using wubi?
I don't know. I simply followed the instructions on this page: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Specifically, I first clicked the download link on the page above, which downloaded a 175mb file named ubuntu-9.10-desktop-i386.iso. I then downloaded and installed Infra Recorder, and used it to create the Live CD. Leaving the CD in the drive I rebooted and went through the Ubuntu installation.

The comment in Step 3 (on the Ubuntu download page) imply that all that's needed to run Ubuntu is the CD, because it says one may copy and pass around the CD.

---

### Post by sgosnell on 2010-03-02
The install CD will either do a full install or install via wubi, if you do it from Windows.  Did you boot from the CD, or did you run the install from Windows?

---

### Post by audiomick on 2010-03-02
> **scc1909 said:**
> I don't know. I simply followed the instructions on this page: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Specifically, I first clicked the download link on the page above, which downloaded a 175mb file named ubuntu-9.10-desktop-i386.iso. I then downloaded and installed Infra Recorder, and used it to create the Live CD. Leaving the CD in the drive [COLOR=Red]I rebooted and went through the Ubuntu installation.[/COLOR]

The comment in Step 3 (on the Ubuntu download page) imply that all that's needed to run Ubuntu is the CD, because it says one may copy and pass around the CD.
That will be a dual boot, and not a wubi, I think. If you didn't see windows after re-booting and before installing, it is a "normal" dual boot.

The instructions that Ghost|BTFH posted should sort you out, I think.

edit: given that the install is only a day old, you probably haven't got much to lose if you do a fresh install even if you don't have a separate /home partition. If you do a new install, it is not a bad idea to make a /home partition if you haven't already. To do that, you need to choose the "manual" option when the installer gets up to the partitioning stage. There is info about partitioning here:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by scc1909 on 2010-03-02
It appears that I installed Ubuntu from wubi. I found wubi.exe in the Downloads directory, and when I clicked the program it followed the same processes as yesterday...i.e., it went out to the internet and began downloading a very large torrent. After things slow down this evening I will run it again and try to reinstall it.

Or is there a way to get the CD to do a full install? When I look at My Computer, it doesn't see anything on the CD.

---

### Post by scc1909 on 2010-03-02
> **audiomick said:**
> That will be a dual boot, and not a wubi, I think. If you didn't see windows after re-booting and before installing, it is a "normal" dual boot.

The instructions that Ghost|BTFH posted should sort you out, I think.
I don't recall seeing anything like /home during the initial install.

And how do I get Ubuntu to boot up to the command line?

---

### Post by audiomick on 2010-03-02
To do a normal install, your BIOS has to be set to boot from the CD first, before any of the HDs.

Have a look at the installation guide here
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
under "standard installation"

It sounds like you do have a wubi install, despite what I wrote in my last post...:oops:
I haven't done one, but as far as I know, you can remove a wubi install from windows using the program manager thing, same as you can remove any other program. You can then do another wubi install or do a normal dual boot install (set your BIOS to boot from the CD first)

---

### Post by sandyd on 2010-03-02
here. do this.
boot into the livecd.
go to accessories -> terminal
type this all in....
```

sudo fdisk -l
```take note of the "/dev/sdaxxx" section of the output (the /dev/sdaxxx is only an example of what it should look like). the line which you are taking it from should say "ntfs"

now, replace "dev/sdax" with the "/dev/sdaxxx" that you just noted
```

sudo mount -t ntfs /dev/sdax /media/windows
sudo mount -o loop /media/windows/wubi/disks/system.virtual.disk /mnt
sudo mount --bind /dev /mnt/dev[FONT=Verdana]
[/FONT]sudo mount --bind /proc /mnt/proc
sudo mount --bind /tmp /mnt/tmp[FONT=monospace]
sudo[/FONT] mount --bind /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
sudo dpkg --configure -a
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

