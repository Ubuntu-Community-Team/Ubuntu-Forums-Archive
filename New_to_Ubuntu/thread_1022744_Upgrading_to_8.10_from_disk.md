---
title: "Upgrading to 8.10 from disk"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by MaxVK on 2008-12-27
Hi. Iv been running 7.10 since its release - This has been my first fully fledged installation of Ubuntu, and Iv enjoyed it very much.

I have now received my 8.10 Desktop Edition disk and I would like to upgrade to this version, but I'm not entirely sure how to proceed.

My initial thought is that I boot from the CD and run the install from there, but Id very much like to keep my data, which is on a separate home partition, but I'm concerned that when I specify the home location things will be overwritten.

Could someone describe the process (assuming that I was correct in the first place!) just so I know what to expect, and whats going to happen. (I'm thinking that my programs will need to be re-installed, but that their settings should be kept etc - Is this correct? Will specifying my home partition overwrite anything?)

Since it might be important my system is built like this:

hda1 - Windows 2000
hda5 - Windows Data Drive
hda6 - Windows Data Drive
hda7 - Small Ubuntu 7.10 Installation
hda9 - Small Ubuntu 7.10 home partition

hdb1 - CURRENT 7.10 installation that wants to upgrade to 8.10
hdb2 - NTFS Data drive (Still used by Ubuntu and Windows)
hdb3 - CURRENT 7.10 installation home partition

The strange setup comes from the original installation, where Windows 2000 had its own partition, while Windows Apps and Data also had their own partitions (All hda). The original Ubuntu was installed experimentally on another Windows partition on hda, and when I decided to use Ubuntu I installed the current version on hdb, which was one large data partition. I still use the smaller Ubuntu installation as an experimental base, and I keep Windows there because every now and then I need a couple of programs that I wrote that wont work under WINE.

Please feel free to dissect and advise.

regards

Max

---

### Post by Partyboi2 on 2008-12-27
When you run the installer and get to the partitioning stage you will need to choose "manual" then you will need to tick the box to format your / partition (hdb1)  and make sure the mount point is set to /. With your /home Partition (hdb3) **[COLOR=black]do not[/COLOR]** tick the format box instead just set the mount point again to /home and proceed with the install. If you don't reset the mount point Ubuntu will create a /home folder on / which is not what you want. 
This will remove all the program you had installed because you are formating / but all the settings that are in your /home partition will not be effected so you should be able to use them with 8.10 as long as you have the programs installed.

---

### Post by drs305 on 2008-12-27
*Got distracted and forgot to hit Post for 15 minutes. What PartyBoi said with a few additions.*

It appears you wish to do a clean install rather than a dist-upgrade. The first thing to do is make sure you back up all your important data files. Even if you don't plan on touching those partitions, mistakes are sometimes made. If you can save the data to an external source, I'd recommend do so.

Second, you might want to copy your current home files to the 'experimental' home or test partition just to have a backup of your current home configuration files. It would not hurt to have an easily accessible copy of them available for reference.

As far as the installation for a clean install, you would select the 'manual' partition option. Select your existing HOME partition, designate it as your new HOME partition, and make sure you **DO NOT have it ticked for formatting**. Your home settings will be modified as necessary to accommodate the new distro but your personal settings will remain basically intact.

---

### Post by terabyte1 on 2008-12-27
If you want to keep all of your previous files and/or settings, it is better to go to Synaptic and look for upgrading your system to 8.10. Because Ubuntu does the upgrade by each release, you may find that to upgrade to 8.10 irksome as Ubuntu will first upgrade to 8.04 first, then, when it is fully upgraded, it will alow you to upgrade to 8.10.


I've found this route better (and quicker) for me as there is less chance of mistakes taking place. Give it a go!:lolflag:

terabyte1:guitar:

---

### Post by MaxVK on 2008-12-27
Thanks for the replies.

As drs305 said, it seems that I want to do a clean install, although this wasn't necessarily what I meant (My fault). Yes, Id like to do a clean install, BUT... if the upgrade route is feasible that seems the easiest way, even if it means going via 8.04 first.

Of course the next question has to be: "Is the upgrade via synaptic option going to be as stable at the end, as a clean install?" My long time Windows self would scream NO very loudly at this, but with Ubuntu, I'm not so sure.

Thanks for the pointers about the clean install - I would back up first anyway, but at least now I know what to be looking out for. But can anyone advice on my new question: Upgrade or Clean install?

Cheers

Max

---

### Post by drs305 on 2008-12-27
I generally do clean installs just for 'housekeeping' purposes but I have done numerous dist-upgrades and really haven't had a problem related to that form of update. You will get various opinions and a search on the forum will show a fairly balanced division. I think that it comes down to personal choice, but I will state that there is no overwhelming opinion that doing a dist-upgrade is a bad choice. If it were a generally bad idea it would be well documented on the forums (and it isn't).

My suggestion would be to make a copy of your OS using partimage. Make images of both your /home and / partitions. I do this all the time and making and restoring the images is very easy.  Then I would go the dist-upgrade route. If it doesn't work out, revert to your old setup or do a clean install at that time.

Here is a link to using partimage:
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")

---

### Post by Partyboi2 on 2008-12-27
I agree with drs305, I think it really comes down to personal choice. What ever method you choose make sure you do a backup of your important stuff.

---

### Post by Norm24 on 2008-12-27
I've upgraded both ways and have no real issues either way.As stated already,whatever you feel comfortable with.

---

### Post by MaxVK on 2008-12-27
Thanks guys, appreciated.

Regards

Max

---

