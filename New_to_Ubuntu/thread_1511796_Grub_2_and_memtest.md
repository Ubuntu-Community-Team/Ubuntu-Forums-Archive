---
title: "Grub 2 and memtest"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by akelsall on 2010-06-17
I recently upgraded to 10.04 and moved from Grub to Grub2. With the old Grub, one of the menu items was memtest86+.  I'm now trying to duplicate that in Grub 2. Here's what I've done so far:

1. modified /etc/grub.d/40_custom    The entry I made to this file was:

    [INDENT]menuentry	"Ubuntu 10.04, memtest86+" {
uuid		2bcf5946-8d1d-4016-97e6-1c9ecb636158
linux           /boot/memtest86+.bin
}
[/INDENT]

The UUID was determined by using the commmand **sudo grub-probe -t fs_uuid /boot/grub/**

[COLOR="Blue"]After making the changes, I did run update-grub. [/COLOR]

I'm not sure if the UUID I'm using is correct. 

Now, when I boot, I see the menu "Ubuntu 10.04, memtest86+", but when I try to use that menu item, it gives me an error message (I can't recall exactly what it said. If it would help, I can post). I'm guessing there's something else I'm doing wrong.

One question I have it about the memtest86+ item. Is that a file I should be able to locate on my HDD? When I search for just memtest86 (without the "+"), I get this back:

[INDENT]hiker@eno:  /etc/grub.d$ locate memtest86
            /etc/grub.d/20_memtest86+
            /var/lib/dpkg/info/memtest86+.list
            /var/lib/dpkg/info/memtest86+.postrm[/INDENT]

Any ideas on what I'm doing wrong? I really need to get this working, because I need to test my new memory modules (I'm only seeing 4Gb of 6Gb,and they are inserted into the correct positions on the MOBO).

Thanks,

Andy

---

### Post by akelsall on 2010-06-17
The error I am seeing is "error  - file not found". I found another posting about memtest and tried adding the following in my 40_custom file. I commented out the previous entry I made, saved the file, then ran update-grub again. Same problem.

[INDENT]### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux	(hd0,1)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###
[/INDENT]

Is there some file I need to install for memtest86+ to run?

Thanks,

Andy

---

### Post by akelsall on 2010-06-17
I came across a posting saying that the LiveCD for 10.04 does not come with the memtest. Why did the dev team decide to drop something so many people use???!!!!

I ended up booting to my Ubuntu 8.04 LiveCD and used the memtest from that CD. So, if you're looking for memtest on Lucid, forget it. Burn a LiveCD of 8.04 and boot to it. When you boot, you have to select your language first before you see the main menu (which includes memory test).

Andy

---

