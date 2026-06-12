---
title: "Resize Home partition maverick"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by lbarnes on 2010-12-15
Here's what my gparted looks like.  I didn't realize ubuntu wouldn't need 180gb's all to itself, what's the best way to get a lot of this space into my home partition?  My swap partition looks like it might like some crumbs too.  Much thanks for any help.

[IMG]http://img130.imageshack.us/img130/2312/screenshotdevsdagparted.png[/IMG]

---

### Post by Elfy on 2010-12-15
Boot with your livecd or usb - start partition editor from sys admin menu.

Right click swap partition - sda1 - turn off swap

Right click /partition - shrink it 

You can then add the unallocated space to /home

It's unlikely the swap needs more - depends on your RAM.

[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

---

### Post by Paqman on 2010-12-15
I agree with forestpiskie. You can go ahead and shrink your root partition waaaay down. 20GB should be plenty, and will leave you with lots of room available in /tmp for stuff which creates really massive temporary files (like authoring DVDs). Swap is fine, if you've got 1GB or more of RAM you probably almost never even touch your swap.

Take a backup of your important data before you go messing about with partitions, just in case.

---

### Post by lbarnes on 2010-12-15
Thanks for the replies, this sounds easy enough...
So do I leave swap turned off or do I turn swap on once resizing the / and /home partitions??  My ram is 8gb.

Edit: The reason I gave / so much space is I figured the virtualbox os's would take up space on the / partition

---

### Post by Quackers on 2010-12-15
Turn swap on again before leaving gparted.

---

### Post by lbarnes on 2010-12-15
Thanks quackers, I turned swap on just before hitting "apply all changes" in gparted, too early??  Resizing now...

---

### Post by oldfred on 2010-12-15
In your case if not modifying the swap partition whether it is mounted or not does not matter. In fact having it mounted may speed things up.Gaprted normally mounts swap to speed things up a little.

Normally we recommend unmounting swap as it is inside the extended partition and mounting any logical partition locks the entire extended partition, so you cannot modify any other logical partitions inside the extended.

---

