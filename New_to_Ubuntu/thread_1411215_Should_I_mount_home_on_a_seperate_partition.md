---
title: "Should I mount home on a seperate partition?"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by TurnOfTide on 2010-02-19
Does anyone else here do this? I am curious if I should as well.

---

### Post by WannabeFantasma on 2010-02-19
I'm doing it, it's really handy, re-installed my sisters laptop and all documents were still there! (even desktop image!)

so I would reccomend it :)

---

### Post by SuperSonic4 on 2010-02-19
I recommend it. I've found it causes less trouble when upgrading and keeps your data away from system data. Plus you can encrypt it for more security.

---

### Post by doas777 on 2010-02-19
YES!!!!!

you will be really happy you did, when it comes time to clean install lucid. just don;t format over your /home and tell the partitioner where it mounts to. all your settings will stick, though you will have to reinstall some apps.

---

### Post by Tibuda on 2010-02-19
Yes, it is a very good thing to do.

Psycocats explains it very well: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Gone fishing on 2010-02-19
Yes

---

### Post by mjitkop on 2010-02-19
Absolutely. That's the best way to do it in my opinion. 
 
As already mentioned, this makes it very easy to do a clean install of a new version of Ubuntu without losing your documents and settings. However, it is always a good idea to back up your /home before you do a clean install... just in case. ;)

---

### Post by jcseeger on 2010-02-19
And another yes.

---

### Post by Endomancer on 2010-02-19
I keep all my files on an external hard drive in much the same way, but this offers me the ability to unmount it and then mount it on a different machine or take the files with me and mount it to someone elses machine

---

### Post by puzzler995 on 2010-02-19
Bump


How big should it be though?

---

### Post by WannabeFantasma on 2010-02-19
I got
10GB for Linux
2 for swap
and the rest (900gb?) for home

Guess it depends on how big your HDD is :)

---

### Post by bowens44 on 2010-02-19
> **TurnOfTide said:**
> Does anyone else here do this? I am curious if I should as well.

Yes, you should. It makes it so easy to re-install should you need to.

---

### Post by 416inversed on 2010-02-19
My home partition is only 10GB, with remainder as a separate 'Data' partition.

---

### Post by Morbius1 on 2010-02-19
No. I have a separate Data partition instead. 

Keeping the old /home partition and carrying it to a new version of the OS will bring with it not only the data that you want to keep but also every tweak and workaround that you created because of bugs or application deficiencies in the old version of the OS. It may take longer to set up the new system this way but it's worth the effort to have a clean slate.

I do however only update once a year starting with the LTS version, not every 6 months so it's a lot less work overall for me.

You wanted an opinion, right?

---

### Post by jim Kane on 2010-02-19
> **TurnOfTide said:**
> Does anyone else here do this? I am curious if I should as well.

                                       i use Sbackup onto an external usb drive
    [LEFT]so i can do....[/LEFT]
    [LEFT]a clean install and then just copy the home/usr into the new install.[/LEFT]
    [LEFT]if the HD fails or i want to try a new version of buntu on another PC again i have all my settings emails even the fav from firefox reinstalled.[/LEFT]

---

### Post by hortstu on 2010-02-19
I recently tried to do this and screwed up my install with psychokitty's tutorial... wasn't the tutorial obviously it was me...

I managed to save everything important and then set my new install up on one giant extended partition.

Within the extended I set up

15GB for hardy
3 for home
15 for lucid when it comes out
3 for lucid home
6 for swap at the end of the drive 
and the remainder of my 160 gb drive is for data

I had a lot of help from this forum getting to that final setup.  There are definite advantages to having separate partitions.

---

### Post by audiomick on 2010-02-19
I have a separate home along the lines of
10 -15 GB /
swap = RAM
the rest for home.
I have also seen posts from a few people who keep /home smallish ( a few GB) and use symlinks to a larger data partition. There is probably merit in that, but I haven't looked into how to do it yet (lazy)

I have been very happy to be able to simply re-mount my home  on a number of occasions, and can heartily recommend it. Having said that, I know I will be wanting to do a clean out when I do the planned really fresh install of 10.04.

---

### Post by mechro on 2010-02-19
> **Morbius1 said:**
> No. I have a separate Data partition instead. 

Keeping the old /home partition and carrying it to a new version of the OS will bring with it not only the data that you want to keep but also every tweak and workaround that you created because of bugs or application deficiencies in the old version of the OS. It may take longer to set up the new system this way but it's worth the effort to have a clean slate.

I do however only update once a year starting with the LTS version, not every 6 months so it's a lot less work overall for me.

You wanted an opinion, right?

I agree. I don't have separate home and prefer the clean slate approach. Usually I have latest Ubuntu and previous Ubuntu co-existing and gradually migrate settings and files as needed.

---

### Post by Miljet on 2010-02-19
And I have to side with Morbius1 and mechro. There is no need to keep config files for programs that you tried and decided not to keep. And there is always the possibility of old config files conflicting with newer versions of programs.

Like mechro, I keep two versions of Ubuntu on each computer and move files as needed.

---

### Post by Rex Bouwense on 2010-02-19
> **Miljet said:**
> And I have to side with Morbius1 and mechro. There is no need to keep config files for programs that you tried and decided not to keep. And there is always the possibility of old config files conflicting with newer versions of programs.

Like mechro, I keep two versions of Ubuntu on each computer and move files as needed.

Because you asked for opinions you are getting the whole gamut.  There are plus and minus for both sides.  I initially did not install a separate Home but back up my data to an external flash drive which you ought to do anyway because clean installs are sometimes iffy and there is no guarantee.  With the release of the new LTS in April, I too will install side by side since my hard drive is large enough to do that.  It is really up to you.  Read all you can and make your choice.  There is no correct answer.  Enjoy.

---

### Post by switch10 on 2010-02-19
I backup my /home every few weeks.  So when I do a clean install, I just copy over a backup.  It works well.

---

### Post by SoFl W on 2010-02-23
> **danielrmt said:**
> Yes, it is a very good thing to do.
Psycocats explains it very well: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Followed this and it did not go well.  I tried to do a backup before I did this only some of the files were copied.  I lost quite a bit but was able to recover most.

The "What if this doesn't work" part also did not work.  The /home/users area were there but there were no files in the directories.

I lost my pictures directory and my documents directory. Is my old home directory files hidden away anywhere?  I am believe I am using the new home partition, the files from the old partition are not there.  I renamed home homeBAD and home_backup back to home.

I would like to recover the lost files but I am unsure that I can.  The percentage free of the "/" partition is exactly the same as it was before I attempted this so the files could still be there.  I believe I partitioned my windows partition.

UPDATE:
I edited my fstab file commenting the line,* "#/dev/sda4/ /home/ ext3 nodev,nosuid 0 2"**, *rebooted, now everything seems to be back to where it was before my attempt.  Renamed my "home" partition "badhome" and I am going to leave it for the time being.

---

