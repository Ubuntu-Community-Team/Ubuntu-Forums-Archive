---
title: "Running out of space on /"
date: 2010-03-07
forum: New to Ubuntu
---

### Post by Mylorharbour on 2010-03-07
Hi guys,
I've installed Karmic (not UNR) on an Asus eee which only has 4Gb on the primary drive. It's working fine but since I installed Ksudoku I now get a Low Disk Space warning saying I only have 123Mb left. I suspect I've loaded it up with a bunch of KDE files. Any ideas how I can delete those and Ksudoku and free up some space?

Edit -
I only have / on that partition. /home and swap are on another.

---

### Post by woodmaster on 2010-03-07
do you really need the swap?  How much RAM do you have.  If your RAM usage isn't running high(I have 2 Gig and NEVER use SWAP cause my usage stays around 23% of the 2 Gig), you could remove the filesystem on the swap partition and enlarge your / and/or /home

---

### Post by jmszr on 2010-03-07
Mylorharbour,

This thread - Posts #1 & #2 especially - may be of help: [http://ubuntuforums.org/showthread.php?t=592141](http://ubuntuforums.org/showthread.php?t=592141)

---

### Post by 2hot6ft2 on 2010-03-07
What are the results of
```
df -h
```
in a terminal
Applications > Accessories > Terminal

You can't go by Disk Usage Analyzer see this:
[[SOLVED] Low Disk Space Warning, A bug? Or a limitation?]("http://ubuntuforums.org/showthread.php?t=1410114")

See the link in my sig. below to clean up some files.

---

### Post by Mylorharbour on 2010-03-08
Thanks guys.

Result of df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  3.4G  123M  97% /
udev                  498M  272K  497M   1% /dev
none                  498M  184K  497M   1% /dev/shm
none                  498M   84K  498M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw
/dev/sdb5              14G  1.7G   12G  13% /home

I'll take a look at the other links a bit later. 

sda is a 4GB SSD primary drive. sdb is a built in secondary 16Gb SSD configured with 1Gb swap and 15Gb /home. RAM is 1Gb.

---

### Post by Paddy Landau on 2010-03-08
> **Mylorharbour said:**
> I suspect I've loaded it up with a bunch of KDE files. Any ideas how I can delete those and Ksudoku and free up some space?
If you're correct, and the new files came with Ksudoku, then you can enter the following commands in a terminal.
```
sudo apt-get purge ksudoku
sudo apt-get autoremove
sudo apt-get clean
```
[LIST]
[*] The first command uninstalls ksudoku completely.
[*] The second command removes packages that are no longer needed (they were dependent on ksudoku or something else, but those dependencies no longer apply).
[*] The third command will clean out unneeded files from the packages.
[/LIST]
 You can run the second and third commands on a regular basis to reduce the space on your home drive.

You could try running just the second and third commands without running the first; if you're lucky, that will free enough space that you still have ksudoku available to use.

---

### Post by mikechant on 2010-03-08
With this size disc, it's probably worth going through all the software on the menus and removing everything you don't want, particularly large packages - e.g. do you need openoffice at all on this machine? If you do need it, do you need the word processor, spreadsheet and presentation application or just one or two of them etc?

---

### Post by Mylorharbour on 2010-03-08
You guys always come up trumps....Thank you.

Autoclean and Clean freed up almost 500Mb and should do the trick. The Office packages are used and as I shouldn't now need to delete Ksudoku she can still give that a try. I'll bear all your tips in mind though as I'm pretty certain we'll need them again in future,

---

