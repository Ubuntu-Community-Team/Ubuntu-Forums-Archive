---
title: "dmraid issue"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by thirdrev on 2009-02-12
I'm running ubuntu 8.10 64bit and am trying to get linux to recognize a raid. when I run dmraid -ay -v I get the error:
ERROR: via: invalid checksum on /dev/sdc
ERROR: via: invalid checksum on /dev/sdb

What does this mean? How do I fix it?

---

### Post by thirdrev on 2009-02-15
Solution
Nothing quite like solving your own problem...
for others out there I will explain what worked for me:
first, I should point out that I have a bios Raid setup utility which I had used for my fakeraid ( don't know if that matters, but it may be a factor).
Whenever I was running sudo dmraid -ay -v it would spit out:
ERROR: via: invalid checksum on /dev/sdb
ERROR: via: invalid checksum on /dev/sda
RAID set "nvidia_dadbbhhb" already active
So my raid was seen, just not mounting. The only thing I found to work was creating an executable for startup to mount the drive using the mount command
run
sudo gedit /etc/init.d/<myscript>

and insert into the file
sudo mount -t ntfs-3g /dev/mapper/<myraid> /<mymountlocation>

once the file is created you need to make it executable:
sudo chmod +x /etc/init.d/<myscript>

then set it to run at startup:
sudo update-rc.d myscript start 51 S .
(don't miss the period at the end)

Note:
the name for <myraid> should be found listed at /dev/mapper/
<myscript> and <mymountlocation> can both be named whatever you want, but <mymountlocation> needs to refer to an existing folder.
I had been trying to refer to a folder I had not yet created and ran into errors.

BTW I'm running 8.10 32bit from the alternate install cd,
but given the output I was getting when I was running 8.10 64bit off the regular install
this probably would have worked to fix the problem for 64bit as well,
but I had already reinstalled in an effort to solve the problem before I found the eventual solution.

---

