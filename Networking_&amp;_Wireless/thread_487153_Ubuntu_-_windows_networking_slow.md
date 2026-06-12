---
title: "Ubuntu - windows networking slow"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by rzj on 2007-06-28
I have a fairly fast machine (AMD64) running 32-bit feisty desktop version. Eventually I will probably rebuild it with the server version, but while I'm playing around with it I'm working on it directly. It has a lot of hard disk storage on ATA133, SATA and also USB 2.0 drives.

I want to use it as a fileserver to both windows and linux clients, uPNP server for video and mp3s, and possibly a few other things. The heavy usage is for video both to uPNP and desktops. 

I have mediatomb working fine playing into a netgear EVA700.

I now have Samba set up to allow access via a read-only account for the kids to play videos on their PC's and a read-write account for me to push files onto it.

I'm using Newsleecher on XP to download stuff, and then trying to unrar to the Ubuntu machine via Samba, which is two way traffic as both the rars and the destination are on the Ubuntu machine. It just seems awfully slow. The two machines are connect via gigabit ethernet through a netgear buffering switch with hardly any other traffic, yet the data transfer rate seems to average at under 10 Mbytes per second each way. The system performance chart shows regular "pulses" of data at about 1 per second that on the graph hit 60 and occasionally 80% peaks but I'm not sure what 100% means as it appears to sometimes rescale the display. This is probably 7 or 8 times slower than the same operation to local drives on the XP machine.

I thought I'd try bypassing samba to see if that was the cause, and tried psftp ssh file transfer but that just seems to hang in the "get" command with no actual traffic so something must be amiss with that.

Obviously I could run an nntp newsreader client on Ubuntu but I want to move towards the machine being a stable server that I don't mess with so the other household members can rely on it. I could also unrar on the XP machine and then copy the final video file to the server, but I don't think I should have to do that. 

My drives were a mix of NTFS and FAT32 but this seemed to cause huge problems for Samba write access even though I was using ntfs-3g to get write access to the partitions. I've now converted them all to ext3 so that he Linux permissions work properly and I've spent time messing about with samba to get the files written in a sensible user/group.

Maybe I should be going the other way in terms of protocols and running some kind of NFS software on the windows machines.

It would be useful if someone could suggest some kind of simple speed and bandwidth test I could try. I guess I could set up an FTP server on Ubuntu and see what throughput I get with that.

Should this all work at a decent speed or are there some limitations in the tool that mean I'm doomed to fail on the current route?

(Sorry 'bout the long post!):redface:

Ray

---

