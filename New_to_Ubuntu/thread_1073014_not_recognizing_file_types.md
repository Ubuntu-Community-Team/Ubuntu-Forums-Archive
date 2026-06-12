---
title: "not recognizing file types"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Vicfred on 2009-02-17
ubuntu is not recognizing the file types, every time i want to open certain files i have to open them with "Open with other Application"

---

### Post by jerome1232 on 2009-02-17
Try right clicking the file, clicking properties, click the "open with" tab, select the program you want to be the default program that opens the file.

---

### Post by DGortze380 on 2009-02-17
> **Vicfred said:**
> ubuntu is not recognizing the file types, every time i want to open certain files i have to open them with "Open with other Application"

what file types?

---

### Post by Vicfred on 2009-02-17
> **jerome1232 said:**
> Try right clicking the file, clicking properties, click the "open with" tab, select the program you want to be the default program that opens the file.

already did that, didn't work.

@DGortze380

avi, jpg, png, mp3, tar.bz2, tar.gz, flv... :(

---

### Post by Vicfred on 2009-02-18
bump

---

### Post by SunnyRabbiera on 2009-02-18
well for multimedia I understand it not working, by default Ubuntu cant preinstall codecs for stuff like .avi, .mp3 and so fourth.
But if its having issues with .tar, thats very strange...
Did you use the restricted extras package?

---

### Post by DGortze380 on 2009-02-18
try installing ubuntu-restricted-extras via synaptic

---

### Post by Vicfred on 2009-02-18
it was working fine, and lots a things are not working, text files, media, etc, etc. ubuntu-restricted-extras didn't fix anything.

---

### Post by Bladeforger on 2009-02-18
And if you "open with other application" does Linux then open that software and read the file properly?  If so, then it's a file association problem.  If not, then it's a file corruption problem.

Keith

---

### Post by Vicfred on 2009-02-18
yes, i can open the files with "open with other application" (i posted it in the first post)... it's getting worse

Could not open location 'file:///home/vicfred'
There is no default action associated with this location.

lol... I'd take a screenshot but...
There was an error running "gnome-screenshot":
Failed to execute child process "gnome-screenshot" (No such file or directory).

---

### Post by jerome1232 on 2009-02-18
Sounds like something went seriously wrong with your installation... I'm really not sure what to start looking at though, perhaps ensure your disk isn't full and run a fsck on the drives from a live cd to make sure it's not a disk problem.

To check disk usage run df

```
df -h
```

--edit-- and is there anything indicated errors in you system logs?

---

### Post by Vicfred on 2009-02-18
I restarted and it failed to load gnome...

---

### Post by jerome1232 on 2009-02-18
> **Vicfred said:**
> I restarted and it failed to load gnome...

Is your disk full? Did you run the disk check?

---

### Post by Vicfred on 2009-02-18
I had to install kde in command line interface...

results of df -h
```
/dev/sda2              24G  5.7G   17G  26% /
tmpfs                 253M     0  253M   0% /lib/init/rw
udev                   10M   92K   10M   1% /dev
tmpfs                 253M     0  253M   0% /dev/shm
/dev/sda3              13G  815M   12G   7% /home
/dev/sda1             196G  103G   93G  53% /media/windows
```

---

