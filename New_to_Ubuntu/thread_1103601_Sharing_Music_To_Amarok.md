---
title: "Sharing Music To Amarok"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Sethalos on 2009-03-22
I have a main system that runs windows xp, my laptop has Ubuntu on it, they network fine and I can share files, etc.

My problem is that I have a external usb hard drive that contains all of music (300 gigs), and I want to allow Amarok to browse to this external drive and populate the music there. 

I've tried mounting the volume on Ubuntu, but I still can't manage to add this music to my library. The USB drive is connected to the main system running xp.

I've tried placing the addy in, I've tried dragging and dropping, and trying to find the mount, but to no avail.

Seth

---

### Post by Xiong Chiamiov on 2009-03-23
What happens when you tell amarok to include music from that drive?

---

### Post by hyper_ch on 2009-03-23
amarok 2?

---

### Post by Sethalos on 2009-03-23
It's just the original Amarok. Nothing really happens, it added about 1207 songs, then just stops.

I also can't seem to find the mount anywhere's in the listings.

---

### Post by hyper_ch on 2009-03-23
I don't really remember how amarok 1.4 worked.. but if you attach the usb drive it should get mounted somewhere. All you need to do is then tell amarok to also scan that folder for music.

---

### Post by Sethalos on 2009-03-23
It's mounted now. The icon is on my desktop, however, when I go to browse it doesn't show up at all.  What it's doing when I drag and drop is just putting in the main folder, and not the mp3's in that folder.

I've pretty much tried everything I can think of now.

---

### Post by hyper_ch on 2009-03-23
what's the output of

```

df -h

```

---

### Post by Sethalos on 2009-03-23
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  8.6G   26G  26% /
tmpfs                 188M     0  188M   0% /lib/init/rw
varrun                188M  112K  188M   1% /var/run
varlock               188M     0  188M   0% /var/lock
udev                  188M  2.8M  185M   2% /dev
tmpfs                 188M  904K  187M   1% /dev/shm
lrm                   188M  2.0M  186M   2% /lib/modules/2.6.27-12-generic/volatile

---

### Post by hyper_ch on 2009-03-23
(1) when posting the output of a command or file enclose it in [noparse]```

```[/noparse] brackets. That maks it easier to read.

(2) I don't see anything else mounted thatn /dev/sda1 as root.

---

### Post by BDNiner on 2009-03-23
Have you checked the permissions on the USB drive from windows to make sure that you have the correct permissions to write to the drive?

---

### Post by Sethalos on 2009-03-23
Yes, the permissions are set properly, I can access all of the music, the problem is that it's not coming up.

The drive says that it's mounted, perhaps I did something wrong. I could try unmounting it, and remounting it.  Also, it's connected to the windows computer, and not to my laptop, so I'm trying to share the music from there to the laptop running Ubuntu.

---

### Post by MrWES on 2009-03-23
If you're running iTunes on the Widows machine, why not enable sharing on iTunes? However, I don't think Amarok supports mt-daap shares. But Rhythmbox and Songbird do. I currently run mt-daapd on my server and everyone in the house can share/listen, etc. from one library.

[http://ipod.about.com/od/itunesbasics/ss/itunes_sharing.htm]("http://ipod.about.com/od/itunesbasics/ss/itunes_sharing.htm")

[http://www.fireflymediaserver.org/]("http://www.fireflymediaserver.org/")

Firefly is the new name for mt-daap, but it's still in the repositories as mt-daapd.

Bill

---

### Post by Sethalos on 2009-03-23
Ok, so I downloaded and have the Firefly installed now...quick question though, am I supposed to run this on my linux laptop, or on the Win XP computer that has the external drive connected to it. I'm assuming that it's a network server of sorts, so most likely run on the WinXP box.

Seth

---

### Post by MrWES on 2009-03-23
> **Sethalos said:**
> Ok, so I downloaded and have the Firefly installed now...quick question though, am I supposed to run this on my linux laptop, or on the Win XP computer that has the external drive connected to it. I'm assuming that it's a network server of sorts, so most likely run on the WinXP box.

Seth

Well you can go about it two ways. You can leave the external drive connected to the XP machine and share the library via iTunes, as described in the first link I posted. Or, get your drive situated in Ubunut and install mt-daapd from the repositories.

```
sudo apt-get install mt-daapd
```

Then you'll need to configure the /etc/mt-daapd.conf file; pretty straight forward, and there are comments in the conf file to help you along. Reboot and the mt-daapd daemon should run; you can check that with

```
ps aux | grep mt-daapd
```

Goto the windows machine (I'm assuming your network is up and running already, e.g. you can ping each other) and fire up iTunes and within a couple of seconds you should see the shared library towards the bottom left corner of iTunes. Also, any other Ubuntu machines running Rhythmbox should see the shared library.

I've attached a screen shot from Rhythmbox, and you'll notice at the bottom left hand corner 'MyJuekBox on ubuntu'. Give me shout -- I think it's worth setting up, and once you have it working it's very reliable and fast.

Bill

Bwhaha...I just noticed I spelled Juke wrong in my configuration file -- duh!

---

### Post by dwasifar on 2009-03-23
Let me see if I understand this correctly.  You're trying to use Amarok (on your laptop) to index files over the network that are stored, not on your XP desktop itself, but on a USB drive attached to the XP desktop?

I'm not surprised it's not working.  Amarok collection scanner does a buttload of i/o to the drive when it tries to build a collection.  If it loses track because of i/o problems, it grinds to a halt, and your setup there is just begging for exactly that kind of problem.

Try this: temporarily, mount the USB drive to the laptop directly, to the same mount point where you had it mounted over the network, so the files appear to be on the same path.  Then start Amarok and do your scan.  Shut down Amarok, restore how things were, and fire it up again, and see if Amarok now sees the files.

If that works, then all you have to worry about is the periodic collection updates.

---

