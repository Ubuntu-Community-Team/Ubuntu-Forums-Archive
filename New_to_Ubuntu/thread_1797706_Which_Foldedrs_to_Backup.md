---
title: "Which Foldedrs to Backup"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by Chrissd on 2011-07-05
Hi all,

Have been researching backups in the event that I need to do a full or partial restore. Many articles talk about different options when it comes to backing up, however, none of them really talk about what I should be backing up.

Can you tell me what you'd recommend what to backup in the event that I need to restore my computer and settings back to how it was prior to disaster.

Thanks

---

### Post by nothingspecial on 2011-07-05
It depends how you have your computer set up.

I have a seperate data partition that is backed up -- er seperately.

That way, My / partition is relatively small. Then you can back up the whole thing excluding /proc /mnt /tmp /lost+found and /media

---

### Post by aeiah on 2011-07-05
one every few months i make a new clonezilla image

every day i backup my important data (not settings) to a couple of separate drives.

but i dont make too many changes or play around too much any more, so its unlikely my system will break too badly

---

### Post by Jacobonbuntu on 2011-07-05
Hi Chrissd,

I would say the most important question is: where do you store your essential documents? That would of course be the first priority to backup. Setting files are secundary, but most of the time stored in invisible directories in /home/yourname -folder (for example /home/yourname.local, thunderbird mail is stored in /home/yourname/.thunderbird), starting with a dot. However, it is not always a good idea to move *all* these directories to a new installation, to prevent conflicts with newer versions.

---

### Post by Frogs Hair on 2011-07-05
I only backup home folders since I do a clean installation of the latest release every six months .

---

### Post by mcduck on 2011-07-05
I'd say your personal files are the only really important thing, everything else can be easily replaced. So back up your home directory. That will save your own files and all your settings.

Of course if you are running servers or something like that you might want to backup their data directories and config files as well.

---

### Post by oscarper on 2011-07-05
Backup configuration really depends on your needs. That is maybe the reason why you will not find a recommendation on the web about what to backup.

You need to define the level of data you need to restore your work or important files. As an example, if you work with design, you will most likely need only your design files, as applications can be installed from zero and it is easier than trying to restore them into the system. 

Now if you run an FTP server, or have some specific applications installed on your computer that you cannot obtain again, you will raise the scope into a full backup.

Do remember increasing the scope will require additional storage and backup time. Also remember some applications may not necessary work if the original files are restored, some of them have self developed methods to restore working data.

I will recommend you to use Cobian backup. it is an interesting system and has quite good tutorials that will help you get through backup.

---

### Post by Chrissd on 2011-07-05
Hi,

So basically /home/ which is where all my users documents are stored and /etc/ with the config files are the only things I need to backup? I don't want to have to go through the hassle of trial and error setting up my SSH, VPN and Apache2. This way I can install all my old programs, then restore the settings and everything be back the way it was?

Thanks

---

### Post by nothingspecial on 2011-07-05
I just tried it using this

```
before="$(date +%s)"; sudo tar --same-owner -cpvzf /media/backup/11.04_050611_Backup.tgz  --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/tmp  --exclude=/media /; after="$(date +%s)"; echo "Elapsed time: $(expr $after - $before) seconds.";
exit 0
```
 
Took about 6 minutes and I have a 1.7 gig tarball containing my entire system (minus stuff like Music, Videos, Documents etc which are symlinked to my /home/$USER from another partition), a full blown natty install with all the bells and whistles.

---

