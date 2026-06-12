---
title: "Dual boot with preinstalled vista and 2 HDs"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by shaggorama on 2008-12-04
I just received my new laptop (an ACER 4163 from NewEgg) yesterday, and I was hoping to give Linux a shot this time around. It came with vista installed, and I've got a new job coming up that is going to require that I keep vista and probably install the whole office suite and adobe creative suite. There are 2 160GB HDDs.

My hope is to set this baby up in such a way that I can share data between the two installations. I want to use ubuntu as my primary, but still leave enough space for the windows partition to stretch its legs with the programs I'm going to need for work.

I've already transferred a ton of music on my 2nd HDD, so I'd rather not repartition it if I don't have to. Right now, it's presumably NTFS). In any event, my questions are:

How should I partition my drives? 
Should I put both operating systems on the same drive and leave part of that drive and the rest of the second as free space? 
About how much space should I leave for the dedicated Ubuntu/vista installs vs. shared space? 
What format would be best for the shared space if I can't leave it the way it is (which is what i'm guessing)?
Do i need to make a /home partition? 
If I find later on that I need more space, is it possible to steal space from partition and add it to another?

thanks, and sorry for the onslaught. I browsed around the forums and google and couldn't find aything that addressed my particular problem sufficiently.

Also, for the record, I did literally just get this computer yesterday. I still need to make a backup of the OS (since acer apparently doesn't come with a boot disk) but if I need to repartition the whole thing, I don't think it would be the worst thing in the world.

---

### Post by Michael.Godawski on 2008-12-04
For dual boot see:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

A separate home is always recommend so you can upgrade your whole ubuntu system and keep all your private data untouched.

---

### Post by shaggorama on 2008-12-04
I ran across the apcmag article before I posted here, but i don't think the suggested method is optimal for my setup. In the installation phase (p3), the tutorial instructs to install ubuntu to "the largest continuous free space." If I use shrink to free up a partition on the disk that vista is installed on, then the largest continuous free space will be on my 2nd HDD won't it? 

I could be wrong, but I think it would be best to put both OS on the same disk and leave the other disk as a a shared data space. That second link you posted makes the partitioner tool in the ubuntu installer look easy enough, but still I'm concerned about how much space I should commit to the respective partitions (provided I pull off the install ok): I dunno, should I just play it safe and just divide the HDD in half?

---

