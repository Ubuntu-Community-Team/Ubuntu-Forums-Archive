---
title: "samba client side hangs when burning CD"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by rolfbeethoven on 2007-07-23
I think this is a network/samba problem rather than a burning problem.

Server runs feisty, client runs feisty.  Connected via a samba share.

Using k3b, gnomebaker or file manager I can start a DVD or CD burn but it hangs about 10% of the way through the burn.  I can kill the process and click around other windows, but my network connection (hardwired ethernet) is gone and restarting the session (ctrl-alt-bksp) doesn't restore it.  I have to restart the computer to get the network back.

If I copy the files from the server to the client and burn the files from the client, k3b works fine.
If I boot up Knoppix on the client and burn the files from the server share, k3b works fine.

As I mentioned before, I can copy the entire files from the server w/o problem.

I would like some advice on how to isolate and fix this problem.  It's a pain to boot up into Knoppix everytime I want to burn a disk.

I search web and this forum for similar problem but couldn't find one that matched closely.

Thanks.

---

### Post by reckless2k2 on 2007-07-23
how are you accessing the samba client? through the GUI using network  and navigating to the share? if so, try mounting it traditionally as a directory and it should work then. i had similar issues with playback or burning and they were resolved by mounting it.

if you need to know how perm or temp...check this out..it answers all:

[http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently](http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently)

---

### Post by rolfbeethoven on 2007-07-23
Share is mounted in fstab but when I had the network hang up problems I umounted and mounted via
sudo mount -t smbfs //ip/share /localmountpoint -o username=user

This is the same command that works with Knoppix.  (With Knoppix livecd I have to install smbfs as well.)

---

### Post by reckless2k2 on 2007-07-24
oic. hhmm....i was counting on that you mounted it through the network connection mod. maybe a samba ninja will jump on or you might have to report it. with a mounted filesystem, i haven't had issue viewing, "streaming", or burning. If you were able to do it in knoppix without a problem, it could be an ubuntu issue that should be reported.

---

### Post by rolfbeethoven on 2007-07-24
I've never reported anything before.  Can you point me in the right direction?

---

