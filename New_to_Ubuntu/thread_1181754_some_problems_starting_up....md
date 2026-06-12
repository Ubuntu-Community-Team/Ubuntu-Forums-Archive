---
title: "some problems starting up..."
date: 2009-06-08
forum: New to Ubuntu
---

### Post by thepiratefish on 2009-06-08
Hi there

I recently had a copy of Ubuntu sent to me through the mail, and last night I installed it. Everything was going swimmingly, until I plugged in my external hard drive. I keep getting an error message saying "Cannot mount the drive". I tried rebooting, unplugging and turning off the external harddrive, and I'm still getting the same error message.

All of my music and everything else is on there...is there any way I can force it to mount? the error message gave me some coding that I could type in, but I'm not sure what I'm doing with that.

any help would be greatly appreciated!!

---

### Post by unutbu on 2009-06-08
With the drive plugged in, open a terminal (Applications>Accessories>Terminal) and type
```

sudo fdisk -l
```
Please post the output.

---

### Post by AutumnPhoenix on 2009-06-08
One of the problems that I had with my external mounting is that I never properly ejected it while using windows.   If you do have a windows computer available plug it in and then right click and you should see either "stop" "unmount" or "eject". You will notice that any lights will stop blinking. This will close it.  After I did that I never had a problem with the external again.

---

### Post by wpshooter on 2009-06-08
Did you have the external hard drive plugged in when you installed Ubuntu ?

---

### Post by dileepm on 2009-06-08
Go to terminal
```

sudo gedit /etc/hal/fdi/policy/preferences.fdi

```

replace all the false to true reboot the system then hot plug/unplug any storage devices you are done

---

### Post by LewRockwell on 2009-06-08
if none of the above works for you then you might see if windoze will mount it.

if windoze won't mount it then I'd say you've fallen under the spell of the "unclean dismount".

---

### Post by blur xc on 2009-06-08
> **LewRockwell said:**
> if none of the above works for you then you might see if windoze will mount it.
 
if windoze won't mount it then I'd say you've fallen under the spell of the "unclean dismount".
 
Yeah- What gives w/ that anyway?  I've seen the unclean dismount on a coworker's pc once a while back, but I habitually yank usb drives and flash memory cards out of slots all the time w/o stopping them first.  99% of the time when I try to be "good" and stop it, all I get is "device cannot be stopped right now" crap...
 
BM

---

### Post by abhiroopb on 2009-06-08
You always force mount it. I think it shows the command when it fails to mount normally.

---

### Post by LewRockwell on 2009-06-08
> **Barna Madau said:**
> Yeah- What gives w/ that anyway?  I've seen the unclean dismount on a coworker's pc once a while back, but I habitually yank usb drives and flash memory cards out of slots all the time w/o stopping them first.  99% of the time when I try to be "good" and stop it, all I get is "device cannot be stopped right now" crap...
 
BM

all depends on whether or not the device is in use by some process when it gets yanked.

Rule Number One concerning external media: dismount, Dismount, DISMOUNT...

(did I mention dismounting)

Never give up, never surrender!

---

### Post by thepiratefish on 2009-06-08
ok...so I can either plug it back into a windows pc and then properly stop the drive, or I can force it with some code?
 
I was really worried that my 60 gigs of music would be lost

---

### Post by abhiroopb on 2009-06-08
It could be a physical problem, wouldn't rule that out yet. But there have been lots of times that a drive has failed to mount on the first try.

You can try this....

1. In a terminal: 
sudo fdisk -l

Along with your hd your external hd should also show up: e.g
internal hd: /dev/hdb
external hd: /dev/sdb

2. To mount:

sudo mkdir /media/disk-1
sudo mount /dev/sdb /media/disk-1

What happens when you do all that?

---

### Post by 3rdalbum on 2009-06-08
> **Barna Madau said:**
> but I habitually yank usb drives and flash memory cards out of slots all the time w/o stopping them first.  99% of the time when I try to be "good" and stop it, all I get is "device cannot be stopped right now" crap...

That's a really bad habit to be in, especially for somebody using Linux as most distributions mount removable storage as "async".

Async is a good mode to mount a drive in, because it results in higher transfer speeds. But if you copy data from a fast disk to a slow disk, the copy operation will report "complete" when all data has been copied off the fast disk, NOT when it's finished copying to the slow disk (there's a buffer). If you yank the slow disk straight after the File Transfers window has closed, then the file has not finished copying.

In the same vein, small changes to disk data are not written immediately, instead they are buffered until they reach a certain size.

So, you MUST unmount, because unmounting will flush the buffer (write all pending data to disk). You probably wouldn't want to lose the last 20 kilobytes of changes to your doctorate essay!

---

### Post by thepiratefish on 2009-06-08
good point. I think I just yanked it when I was shutting down windows for the last time. When I get home from work, I'll post what happens

---

### Post by thepiratefish on 2009-06-08
How do I enter it into the terminal? when I open the terminal, it starts off with this string of text:
benpouliot@benpouliot-laptop:~$ sudo fdisk -l
[sudo] password for benpouliot: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdf723289

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9729     2996122+   5  Extended
/dev/sda5            9357        9729     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b08e65d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

that's what happened when i put it in...still can't open my external...gives me the same error message as before. should i try the other solution now, unplugging it, plugging it into a windows machine, then properly stopping it?

---

### Post by abhiroopb on 2009-06-08
Sorry if I wasn't clearer. Basically, your external harddrive is /dev/sdb1. So, in a type in a terminal:

sudo mkdir /media/disk-1
sudo mount /dev/sdb1 /media/disk-1

---

### Post by thepiratefish on 2009-06-08
k...

tried that, and this is what the output was:

benpouliot@benpouliot-laptop:~$ sudo mkdir /media/disk-1
benpouliot@benpouliot-laptop:~$ sudo mount /dev/sdb1 /media/disk-1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/disk-1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/disk-1 ntfs-3g force 0 0
benpouliot@benpouliot-laptop:~$ mount -t ntfs-3g /dev/sdb1 /media/disk-1 -o force
mount: only root can do that

---

### Post by abhiroopb on 2009-06-08
Type:

**sudo** mount -t ntfs-3g /dev/sdb1 /media/disk-1 -o force

---

### Post by thepiratefish on 2009-06-08
I think it worked this time...I haven't tried opening the volume, but this is what the output said when I typed that in

$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.


That means the log file was reset, and the mount was successfully forced, correct?

---

### Post by thepiratefish on 2009-06-08
beautiful! it works wonderfully!

And I like Ubuntu's music player...so much simpler than WMP 11...thanks so much!

---

### Post by abhiroopb on 2009-06-08
No worries, just bear that command in mind. Its happened to me many times, as ejecting in Windows can be a PAINFUL affair!!

---

### Post by thepiratefish on 2009-06-08
got it.

like i said, I'm brand-spankin'-new to Linux. I was raised on Windows but I thought this looked cool and its not just out to make money like microsoft.

Do a lot of functions require use of the terminal?

I just tried loading some of my games...they don't seem to respond well. In fact, they don't open at all haha. Is there a way to force them to load? or some sort of emulator or something i can run them through?

---

### Post by s4stevo on 2009-06-08
I've also had this problem starting up, almost from the begining the letters on almost everything have been messed up. At first I almost thought it was a problem with the computer's pixels because thats what it almost looks like. Anyway I just installed this and I'm eager to play with ubuntu but the letters are really irritating. Can I get some help?

---

### Post by thepiratefish on 2009-06-08
well, i just installed it last night, but i think there's a way to change the font scheme from the main desktop area. you can right-click, and then select change desktop background. that brings up an appearances menu, and there's a font tab on the top, along with some other options.

I think that can help...

---

### Post by s4stevo on 2009-06-08
No.. that didn't help. I'm not really sure whats going on though. I restarted my computer after changing the font settings and it seemed ok until I started opening things up and now its messed up again.

---

### Post by s4stevo on 2009-06-08
Also how do I post a thread on here? I only know how to reply

---

### Post by thepiratefish on 2009-06-08
Go to the main page (ubuntuforums.org) and then click on one of the categories...Absolute Beginner Talk to start a new thread in this section.

Once you do that, you'll be taken to a page with all of the Absolute Beginner Talk threads. At the top, you'll see a button that says "New Thread." just type in a subject, select a prefix (that says which OS you're discussing) and type in the first post.

---

