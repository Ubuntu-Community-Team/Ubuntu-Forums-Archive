---
title: "Can't find network"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2009-08-08
Using Ubuntu 8.04 and want to join my lan at home (2 more computers [Windows]) and a USB HDD. But I just can't find my way. Have opened

System/Admin/Network, and
System/Admin/Network Tools

but still cannot figure out how to reach the other computers (I know their IP #'s and can ping them, but just cannot seem to add them.

Can anyone either refer me to a very basic linux network configuration tutorial or step me through it? TIA

Also may have a network place name incompatibility. Both of my windows computers shows Mshome for one area and Workgroup for the linux computer and the USB HDD, and unsure if this is a problem or one go them needs to be changed to the same as the other?

And, 'ifconfig' gives you the ip# of the computer you are on. Is there a shell command that interrogates all other devices on the network and returns their ip #'s?

---

### Post by mikewhatever on 2009-08-08
Places->Network, that's where you should see the other computers. From what I know (which isn't much), the workgroups need to be the same. Ubuntu's default is workgroup, so you might try changing that to MShome.

---

### Post by Odyssey1942 on 2009-08-09
Sometimes the solution is right under your nose. It is there indeed. Thanks. All done.

---

