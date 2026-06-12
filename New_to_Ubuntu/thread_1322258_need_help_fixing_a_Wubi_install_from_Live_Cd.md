---
title: "need help fixing a Wubi install from Live Cd"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by djm227 on 2009-11-10
About a week back I did a Wubi install of Ubuntu on a buddy of mines PC over Vista.  He called me today and said that he kicked out the power cable by accident, and now Wubi won't start ("no kernal detected" or something like that).   I live out of town, so i need to walk him through all of these steps through email. 

I know that hard shut downs are really hard on Wubi, so i looked into how to fix it. In the Wubi wiki page, it says how to boot into existing Wubi installation and repair it from a Live Cd.  [(Here]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?"))  There are a few things i really don't get, since I am new at this.  If someone could walk me through it that would be great.

The wiki says "Replace sda1 with the appropriate device".  So what exactly would that be? He only has one hard drive....so would it be "C1"?  Do I just tell him to copy paste these commands into terminal in order?  Will that do the trick, or is it more complicated then that? 

> sudo mkdir /win
sudo mount /dev/sda1 /win
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
sudo fsck /win/ubuntu/disks/root.disk

Also, the wiki says "Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access."  I have NO idea what that means.

Thanks a lot for the help.

---

### Post by djm227 on 2009-11-11
can anybody help me with this?  That entry in the wiki isn't exactly noob friendly.

---

