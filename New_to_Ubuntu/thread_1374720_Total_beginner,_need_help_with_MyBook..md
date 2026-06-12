---
title: "Total beginner, need help with MyBook."
date: 2010-01-07
forum: New to Ubuntu
---

### Post by JasonGOrtiz on 2010-01-07
First time posting. Hope this is the proper place for this thread.

Before I detail the problem I'm having I wanna take the time to explain that I'm am an absolute newbie when it comes to Ubuntu. I've had it for a while, but never really had any problems and never had to use the terminal or anything like that. I've tried solving this new problem on my own by tirelessly looking through other posts and clumsily attempting to fix it myself. I have no idea what I'm doing and have come to the point where I need to reach out for some help. Any feedback would be eternally appreciated. Now, on to the problem.

For Christmas I received a new 1tb MyBook Essential external hard drive. I also own a 350gb MyBook that contained all of my music. The 350gb was completely full and I decided to transfer all my music to the new 1tb drive. I did so, deleted all the files from the old one when they were safely transfered to the new one and everything was going fine. I was able to access all my files and everything was in perfect working order. A day or so later, my 4 year old son managed to pull the USB chord that connected the new 1tb to the back of my computer while it was running. Ever since then I cannot open my new MyBook and access my files. I can still see the icon for it when I open Places, but every time I click the icon it gives me this message:

Cannot Mount Volume.

Unable to mount the volume 'My Book'.

ntfs_attr_pread: ntfs_pread failed: Input/output error Failed to read NTFS $Bitmap: Input/output error NTFS is either inconistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk f on Windows then reboot into Windows TWICE. The usage of the /f parameter is very important! If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details.

That's the entire error message verbatim. I have absolutely no clue what any of that means. I called Western Digital and they told me that they couldn't help with linux issues. They also told me to take my drive to a computer with windows and see if it will work on that. The problem there is that I don't know anyone with Windows any more, believe it or not. They then said I can contact a data recovery service, but they charge at least $1,600 and I barely have $16. So they told me that worst case scenario I can call them back and they will walk me through reformatting the drive, but I would lose all my files. I don't know about anyone else, but that 350gb of music has taken me a couple years to download and tag and means a lot to me. Obviously, I don't want to have to just give it up. I'm still clinging to a little hope that I can salvage everything and solve the problem. I know this is quite a little mess I've gotten in and dealing with someone who knows nothing about ubuntu can be trying, but I would sincerely appreciate any suggestions. Even if it's just brutal honesty and you tell me I need to say goodbye to music and start over. Thanks.

---

### Post by ajgreeny on 2010-01-07
If you had, or knew someone with a windows computer, that would solve the problem which simply results from the inadequate shutdown of the external disk before unplugging it.  I am assuming the disk is formatted to ntfs.

I think you will need to either find a computer shop which is friendly enough to just plug it in and then remove safely, or you will have to force the mount of the disk.

How you do that will depend on the dev name and needs a mount point for the disk, so attach the disk and run ```
sudo fdisk -l
```The output will show the disk/partition device name (and filesystem on it), then you should be able to mount it with the following command.

To make the mountpoint and force mount the disk:-
```
sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/sdx# /media/disk -o force
```
If that does not work, or the partition is shown as fat32, I am baffled as I was under the impression that it was only ntfs that had this "locked system" problem.

---

### Post by louieb on 2010-01-07
Try ntfsfix.

**[*Ubuntu* Manpage: *ntfsfix* - fix common errors and force Windows to [B]...**]("http://www.google.com/url?sa=t&source=web&ct=res&cd=2&ved=0CBYQFjAB&url=http%3A%2F%2Fmanpages.ubuntu.com%2Fmanpages%2Fhardy%2Fman8%2Fntfsfix.8.html&ei=qNZFS8_NDIyCNrr5zfMC&usg=AFQjCNFM7jcgV0GMwXP0dm9NrbVGbJ8Pdg&sig2=4glcMl9MjN56c1Zsxx7HPA")[/B]

Does not alway work.


**[*ntfsfix* says it is fixed but ntfs-3g cannot mount! - *Ubuntu* Forums]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&ved=0CAkQFjAA&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D484566&ei=qNZFS8_NDIyCNrr5zfMC&usg=AFQjCNFSKqCqJYHdnbMv6B03e8c6K-3Kmg&sig2=_iwfezlH6ACyIjjLrc4pAQ")**

---

### Post by JasonGOrtiz on 2010-01-07
First of all, thanks for the suggestions. I'm very grateful for the help.

OK, so I talked to my Dad this morning and he actually just got Windows Vista for one of his home PCs. I'm thinking I should take my drive over there and see what happens when I plug it in and run Vista. Gonna try and take it over there tomorrow afternoon. I'm hoping that might shed a little light on my situation. I can't stand Windows, that's why I switched to Ubuntu about two years ago, so this will be the first time I've had to deal with it in quite a while. But I guess it's a necessary evil for me right now. What am I going to be looking for? If I am able to see the icon for MyBook should I just try to "safely remove hardware" and then bring it back to my computer and see if that worked?

---

### Post by JasonGOrtiz on 2010-01-07
New develpopment.

Just ran the "sudo fdisk -l" command in terminal.

This is what popped up:


Disk /dev/sda: 60.0 GB, 60000000000 bytes
255 heads, 63 sectors/track, 7294 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        7293    58540860    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

Disk /dev/sdc: 999.5 GB, 999501594624 bytes
255 heads, 63 sectors/track, 121515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002ae3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121516   976074752    7  HPFS/NTFS


I guess the new 1tb MyBook is the one marked /dev/sdc. So if I try to force mount, would the code be: 

sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/sdc/media/disk -o force

Is that right?

---

### Post by JasonGOrtiz on 2010-01-07
Didn't work. 

I created the "media/disk" directory, but then when I tried "sudo mount -t ntfs-3g /dev/sdc1 /media/disk -o force" in the terminal it just gave me the same exact error message from before: "ntfs_pread failed".

---

### Post by louieb on 2010-01-07
When you get it hooked up to Vista go to MyComputer - right click on the drive - select properties. IIRC you can get windows to run chkdsk from there. That should get it clean.

---

### Post by Captain_tux on 2010-01-07
I have the same device... sorry to hear of your problems. Is it possible that the USB cord is bad?

Can you post the result of **df -h**...

---

