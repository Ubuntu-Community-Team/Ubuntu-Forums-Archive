---
title: "[SOLVED] Trouble with Trash"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by Dave B on 2009-01-01
I have a Directory with subdirectories with files in them in my TRASH BIN and i cant get it to Empty.

I have tried just empting the trash bin with no success


i have tried in command line to empty it with no success

Can Anyone help?

Then i open the traaaaash bin in the location it says : trash:///media%252fdisk%252f.Trash-1000%252fDRM

---

### Post by newbee70 on 2009-01-01
> **Dave B said:**
> I have a Directory with subdirectories with files in them in my TRASH BIN and i cant get it to Empty.

I have tried just empting the trash bin with no success


i have tried in command line to empty it with no success

Can Anyone help?

Then i open the traaaaash bin in the location it says : trash:///media%252fdisk%252f.Trash-1000%252fDRM

try 

sudo nautilus

then go into your trash and empty it there

---

### Post by drs305 on 2009-01-01
Run nautilus with *gksudo*. The trash is probably owned by root and you do not have permission to delete it. Using gksudo will enable you to delete it (use SHIFT-Delete or it may just end up back in .Trash).

Here is a tutorial on system trash and how to delete it:
[http://ubuntuforums.org/showthread.php?t=898573]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by ZeldeR on 2009-01-01
solution you can find here: [[COLOR="Blue"]Can’t delete files from my trash[/COLOR]]("http://itfriend.net/?p=50")

---

### Post by adobrakic on 2009-01-01
I just run this code

```

sudo rm -fr ~/.local/share/Trash/files/*

```

in Terminal, whenever I have deleting issues.

---

### Post by Dave B on 2009-01-01
there is still trash in the bin

---

### Post by drs305 on 2009-01-01
> **Dave B said:**
> there is still trash in the bin

If you are looking at your trash bin icon, it is possible you have trash in other partitions. Your user trash is stored in ~/.local/share/Trash/ (Hardy and later) but you can also have trash folders in other partitions, such as .Trash-1000 or whatever your UID happens to be.

This does not even take root's trash into consideration. I suggest you go through the tutorial/howto link in my signature line (Check Your Trash) and accomplish the recommended steps. Barring that, you will have to give us the exact location of the trash and why you can't delete it (error messages, etc).

This command finds all trash folders on your system:
```

sudo find / -type d -iname *Trash* | grep Trash

```

---

### Post by Dave B on 2009-01-01
Hi 

I donno if this helps

when i open the trash this is what is in the location bar.
trash:///media%252fdisk%252f.Trash-1000%252fDRM

does this help?

thanks

---

### Post by Dave B on 2009-01-01
I did 
sudo find / -type d -iname *Trash* | grep Trash

OUTPUT=

dave@dragon:~$ sudo find / -type d -iname *Trash* | grep Trash
/media/disk/.Trash-dave
/media/disk/.Trash-1000
/media/USB20FD/.Trash-1000
/media/disk-2/.Trash-1000
/media/disk-2/.Trash-dave
/media/disk-1/.Trash-1000
/media/disk-1/.Trash-dave
/home/dave/.local/share/Trash
dave@dragon:~$ 




and i still have almost a GIG of TRASH in the trash bin

---

### Post by drs305 on 2009-01-01
You should be able to navigate to each of those folders and manually delete them if you run the following command:
```

gksudo nautilus /media

```

The command will open in /media since that is where all but your local trash is located. You should then navigate to each of the folders you found in the previous post. Highlight the .Trash folder, then Shift-Delete. The .Trash folder and its contents should be permanently deleted. A new empty Trash folder will be created when needed.

Repeat this for each of the folders.

---

### Post by Dave B on 2009-01-01
HI THERE

gksudo nautilus /media   

seems to have done The trick

Thank you sooo much for the help

---

### Post by Donalb on 2009-01-23
Hi,
OK this is not a big problem, not taking any space, but annoying me nontheless.
 
I have 5 external HDDs including an Iomega Rev70 gb drive.
My system trash shows 7 folders, (originally for a Windows game on the Rev70, which contained <many> gif files, which I deleted some months ago when I installed Ubuntu). As far as I can see in Nautilus, those folders are empty (hidden files displayed).

But I can't delete the contents. 

So first I located all the trash locations to ensure this was the one where the folders were, this was how I determined it was the Rev70gb. 
 Then I tried gksudo nautilus to delete and got a permissions error. 
So then in Term I cded into 
/media/REV 70/.Trash-1000/files
then checked for any contents. I find the 7 folders. But if I try to rmdir any of them I get a "Directory not empty" message. If I cd into any of the directories, they are empty.
I tried rmdir -Rf (according to my gleaming new Linux phrasebook) but get invalid option for the -R & f options.
So stumped at the moment. 
Any thoughts appreciated?
Regards

---

### Post by drs305 on 2009-01-23
Donalb,

"gksudo nautilus" should have worked. So let's try the command line again although there may be other issues.
 
The "rm" command used with sudo is a very powerful command that can destroy a system if not run correctly so I will take a more roundabout way of deleting the folders. First we will change the trash ownership to you and then delete it as a normal user.

We will use a universal search for Trash folders:

Find all the trash folders:
```

sudo find / -type d -name *Trash* 

```

Again, sudo combined with any chown command can be dangerous. If you chown any folder of system files you may have to reinstall. Copy/Paste this command. Once you are satisfied with the results from the previous command, and that the results contain *ONLY* Trash bins you can run this. Substitute your username:
```

sudo find / -type d -name *Trash* -exec chown -R *[COLOR="DarkRed"]yourusername[/COLOR]* {} \;

```
All the trash bins should now be owned by you. You can use nautilus to try to delete them. The following command will sequentially open nautilus in the Trash bin(s). You should see 2 folders: *files* and *info*: See if you can now delete them. When you close nautilus, nautilus will reopen with the next Trash bin.
```

sudo find / -type d -name *Trash* -exec nautilus {} \;

```

As I said at the start, with "gksudo nautilus" you should have been able to get rid of any of the folders. Try this, if it doesn't work, I'd reboot and try "gksudo nautilus" again.

---

### Post by egalvan on 2009-01-23
> **drs305 said:**
> 
This command finds all trash folders on your system:
```

sudo find / -type d -iname *Trash* | grep Trash

```

I ran this command, and got the following:

```

ernest@gx280:~$ sudo find / -type d -iname *Trash* | grep Trash
[sudo] password for ernest: 

find: /home/ernest/.gvfs/media/750-data1/ernest/.local/share/Trash
/root/.local/share/Trash
/home/ernest/Music/music/for diana/Ralph White/Trash Fish
/home/ernest/.local/share/Trash

: Permission denied

ernest@gx280:~$ 

```

Any idea on what the "permission denied" means? It ran under root.

---

### Post by drs305 on 2009-01-23
When combined with the 'find' command the only  time I get the "permission denied" message is when I forget to use *sudo* in searching system files.

Is *sudo* working normally for other functions? I ask since your "gksudo nautilus" didn't seem to work and now this message. If you do a simple command such as *sudo blkid* does it run without error?

By the way, did the *chown* command work for any of the folders and could you now delete them?

---

