---
title: "RAID, Backups and HTPC"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by wigout on 2011-05-02
I have heaps of old drives laying around. I have copied and recopied old  files from old installations of different windows machines and a couple  of ubuntu machines.

I've been lucky to only really lose a couple  of drives along the way and was able to recover the files in spite of  that using testdisk and photorec from [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

I'm finally really really ready to try, I mean really try to set up some sort of sane backup/redundancy system.

I have a dell inspiron 530 Core 2 Quad Processor Q6600. 
Here's  a list of specs that I can find for it (and here's a link to the more  complete official dell specs-  [http://support.dell.com/support/edocs/systems/inspd530/en/om/html/appendix.htm#wp1052310](http://support.dell.com/support/edocs/systems/inspd530/en/om/html/appendix.htm#wp1052310)  ):
> # Chipset
    * ICH9 and Intel G33
# Processor
    * Intel Core 2 Quad processor. FSB up to 1333MHz
    * Intel Pentium Dual-Core processor
    * Socket LGA775
# Memory
    * 4x 667-MHz, 800-MHz DDR2 SDRAM
    * 4gb Max Total
# Audio
    * Integrated Realtec ALC888 (7.1 Channel audio)
# Video
    * Intel integrated video
# Expansion Capabilities
    * 2x PCI Slots
    * 1x PCI-e x1 Slot
    * 1x PCI-e x16 Slot
# Peripheral Interfaces
    * 1x VGA Monitor Port
    * 1x RJ-45 10/100 Ethernet/LAN Port
    * 4x USB 2.0 Ports
    * 6x Audio Connectors for 7.1 Surround SoundIt can take 4 sata drives. I've heard that the Core 2 Quad board can take up to 8gb of ram.

I have it dual booting windows xp and ubuntu (8.04 LTS), one drive, 4gb of ram.

This is currently serving as a sort of rudimentary home server (samba). 

I want to move it down to the TV room and use it as a htpc.

I  think I need to buy a video card for HDMI output- and it seems like an  ATI HD 4670 will fit/work for my needs. The TV I'd hook it up to takes  HDMI input and has a pc/monitor input as well. I don't know if the  monitor input would work for HD input (or if the onboard graphics would  be sufficient in any case).

As well as an HTPC, I'd have it serve  as the backup repository for the house's laptops and, probably most  importantly, home videos and photographs.

So....

The age-old question that seems to have rapidly evolving and fiery devotees:
Should I have a raid setup?
Should it be software or hardware?
Raid 1 or Raid 5?

I  have gathered that everyone says to use a separate drive or partition  for the OS (that is, don't have the OS on the raid it self).

What I'd like to have is this:
Use one internal drive for the OS & general media friendly, browsing friendly software.
Use  the three internal drives (and a fourth esata drive? I'll need an esata  card too) in a raid configuration, probably 2tb drives (maybe samsung  spinpoints).

After reading all over the dang place, this guy's  approach seems most like what I'd like to do (from  [http://www.linuxquestions.org/questions/linux-server-73/to-raid-or-not-to-raid-871165/](http://www.linuxquestions.org/questions/linux-server-73/to-raid-or-not-to-raid-871165/)  ):
> The use of Raid 1 (mirrored) drives can be used as a backup and disaster recovery strategy.
You purchase 3 drives labelled 1 2 & 3 and use an external caddie  for your second drive. At regular backup intervals you fail and remove  the drive in the caddie (you can do this simply by shutting down the  machine and removing the drive from the caddie if it's not a hotswap  sata device). Replace the second drive with the third then add and  resync. Place the second drive in a secure location. At the next backup  remove the third drive and replace it with the second and so forth. This  way if a catastrophic disaster happens you can boot the spare drive and  be back online within minutes. I've been using this technique now for 6  years to provide redundancy to my customers. The added advantage is  that on failure you do not rebuild your linux distribution which could  take days. By using software raid the solution is flexible and the  resync time does not impact significantly upon the computers  performance.I am terribly new to considering such things  at the moment. So I am looking for advice that is relatively easy to  follow and (because it is relatively easy to follow) will lead to a  successful redundancy/backup solution.

So... can I / should I setup a raid like the quoted fellow? With four drives (three internal, one external)?
Is  it sound to do so in a machine that I expect to use every other day for  internet/media or should I really be looking at getting a separate nas  with a raid built-in? (I was just going down that road but realized I  have a fully functioning computer that could be purposed to such a task,  with the right equipment/software & time...)

Finally, as the  extra-credit portion of this endeavor- when I get around to setting up  the backup of the laptops.... (and all of these headaches is why I never  actually get around to creating backups in the first place).... how do I  do that exactly? Should I just back up the core documents/files,  knowing that if the drive/laptop fails, I'll just be reinstalling the os  anyway? Or should I do some sort of disk-imaging snapshot thing? And to  keep things complicated, one laptop has ubuntu and the other windows  vista. And both of those laptops are typically connected to the network  via wifi (not wired) so whole disk-backups might be foolish to even  consider.

I know this is a whole tangle of problems here. I  apologize in advance if there is an idiots guide to setting up a raid  and backing up your multi-os wifi'd laptops out there.

Thanks for listening and any insight,
wigout

This guide seems to be as good a guide as any:
[http://www.howtogeek.com/51873/how-to-setup-software-raid-for-a-simple-file-server-on-ubuntu/](http://www.howtogeek.com/51873/how-to-setup-software-raid-for-a-simple-file-server-on-ubuntu/)
though the author is talking about setting up a raid10, and is expecting that the server won't be getting heavy use otherwise.

---

