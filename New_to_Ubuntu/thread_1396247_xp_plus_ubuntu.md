---
title: "xp plus ubuntu"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by DD70 on 2010-02-01
[SIZE=2]Been offline lately. We are in the process of moving house. Do i need to say more?
Have struggled with Ubuntu with about a 60% success rate. Some thing I like others I hate. Like my camera doesnt work as it should, printing pics is nor as easy as it was under XP, my mp3 playerr doesnt work as well and etc .
What I thought was to install XP home on a dual system. That way I can pick and choose which to use from the best of both systems. Can I do this and if i can then how do i go about it[/SIZE]

---

### Post by samantha_ on 2010-02-01
Im assuming you currently have XP installed over the entire HD of your computer k?

So, when you get to the partitioning stage, there should be an option to "install side by side"
that option will resize the windows partition and use the freed space to install ubuntu.

Ubuntu will automatically then add an entry to the bootloader for windows at startup.

---

### Post by niffcreature on 2010-02-01
you can find this information somewhere else, and much more easily. there are guides. [http://www.google.com/search?aq=1&oq=dual+booting+xp&sourceid=chrome&ie=UTF-8&q=dual+booting+xp+and+ubuntu](http://www.google.com/search?aq=1&oq=dual+booting+xp&sourceid=chrome&ie=UTF-8&q=dual+booting+xp+and+ubuntu)

---

### Post by SPazzo on 2010-02-01
Try this link: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

That should help.

---

### Post by ssulaco on 2010-02-01
I would also like to suggest a Wubi install,Ubuntu runs very well within Windows
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by DD70 on 2010-02-02
I got this desktop with ubuntu pre installed. So having xp pre installed is not an option. What i need is to install xp or windows 7 over the top of linux and have them both on my pc. I know that I can install xp or 7 and then install ubuntu. but can i do it in the reverse order?

---

### Post by Some Penguin on 2010-02-02
You'll probably to shrink the Ubuntu partition yourself to make some space, and to fiddle with the bootloader later (a search for 'EasyBCD' might be relevant and helpful), but it should work.

---

### Post by niffcreature on 2010-02-02
its more of a windows problem in that case.

what you need to NOT do is rewrite the entire disk without noticing. there will be a step in windows installation were you can partition and linux needs to keep its own partition separate. 

after that, you will need to reinstall the grub bootloader to work with linux. i believe there is a simple application to do this from windows. here [http://www.supergrubdisk.org/index.php?pid=12](http://www.supergrubdisk.org/index.php?pid=12)

oh one more thing... windows cant access linux partitions by default, so dont expect to be able to download that and then install windows and get it.

good luck. i think thats all you can really know to do this, just go for it.

---

### Post by anaconda on 2010-02-02
My favourite way is to have XP on a different harddisk, or in a virtual machine inside ubuntu.(eg. virtualbox)

But then I always seem to have old harddisks lying around... So it doesnt cost anything.

And when installing an os to one harddisk I disconnect the other one, so I wont accidentally overwrite anything on the first hd.  Or accidentally install grub on the MBR of the windows disk. (which would result in windows being unable to boot if he ubuntu hd is not present....)

Then when booting the machine I use Bios bootmanager, or change the boot order from bios.

And nowadays I have windows only on a dualbooted laptop. (on the same hd)

---

