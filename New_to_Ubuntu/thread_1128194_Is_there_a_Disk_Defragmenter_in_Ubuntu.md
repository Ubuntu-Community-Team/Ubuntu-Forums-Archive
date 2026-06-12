---
title: "Is there a Disk Defragmenter in Ubuntu?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-04-17
Is there a Disk Defragmenter in Ubuntu? How can I keep my programs running fast? How can I increase flash-cache? :)

---

### Post by LowSky on 2009-04-17
ext3 and ext4 are journalling file systems. the fragmation rate is less than 5%, no need to worry about that

---

### Post by UbuntuNerd on 2009-04-17
if you want to keep things clean look at this simple [guide](http://my.opera.com/ubuntunerd1/blog/keeping-ubuntu-clean)

---

### Post by mikechant on 2009-04-17
Here's a quote from the wikipedia ext3 page:
> While ext3 is more resistant to file fragmentation than the FAT filesystem, nonetheless ext3 filesystems can and do get fragmented over time. Consequently the successor to the ext3 filesystem, ext4, includes a filesystem defragmentation utility and support for extents (contiguous file regions).

I.e. ext3 does not have a defrag util as such (although there are ways round this; see the wikipedia page), but ext4 will have and you may benefit from using it in certain cases.

I say 'will have' because (despite the wikipedia quote above) the ext4 defrag program is not ready yet. See this request:
[https://bugs.launchpad.net/ubuntu/+bug/321528](https://bugs.launchpad.net/ubuntu/+bug/321528)

So don't worry about it at the moment - it'll probably be in the release after 9.04/jaunty.

---

### Post by lavinog on 2009-04-17
> **LesterPalooza said:**
> Is there a Disk Defragmenter in Ubuntu? How can I keep my programs running fast? How can I increase flash-cache? :)

fragmentation shouldn't be a issue unless you run low on disk space. Try and keep at least 10% free on your drive.
The same principle applies to the longevity of your drive...If you keep your HD full, you hard drive works alot harder to find free space to store data...along with the way the hd manages bad sectors...many times you will never see bad sectors because hds have dedicated storage to replace those bad sectors...when the dedicated storage is used up, bad things happen.

Adding memory makes the biggest difference in performance. All your free memory will be used to cache data from your hd.

---

### Post by Mulenmar on 2009-04-17
Aside from the above statements, there's always some fancy partioning you can do when first installing the GNU/Linux distro. Isolating data that changes frequently in it's own partion only further slows fragmentation. ;)

---

