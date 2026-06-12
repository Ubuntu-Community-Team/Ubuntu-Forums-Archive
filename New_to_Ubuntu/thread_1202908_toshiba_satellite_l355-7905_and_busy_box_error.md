---
title: "toshiba satellite l355-7905 and busy box error"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by lsl01 on 2009-07-02
hi i just bought a toshiba satellite l355-7905 it has vista already install but i want to install ubuntu 9.04 instead so i download the ubuntu-9.04-desktop-i386 already in the iso format and burn it to a cd now i am trying to install the os but it will boot up in cd and show the primary display of choose language and how i want to install and after i choose to install it gives me a black screen and it says "busybox v1.10.2 (ubuntu 1:1.10.2-2ubuntu7) built in shell (ash) enter 'help' for a list of commands and then it gives me a prompt of (initramfs) i check to see what else i have to do but i cant find anything on this can someone please tell me what i have to do now thank you pleaseeeeeeeeeeeee help

---

### Post by synapsys on 2009-07-02
First try the 'try ubuntu without changing my computer' option then it should boot to desktop. Click the install icon.

If that doesn't work, check the md5 of your download to make sure it is not corrupt. If it's not corrupt. Re-burn the iso at a slower speed [4x or less]

PS That is a problem, normally you should have a totally graphical installation which is pretty straightforward.

---

### Post by oldos2er on 2009-07-02
You should first run 'Check CD for defects', or md5sum ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)).

---

### Post by nhasian on 2009-07-03
Hello,

according to [Intel]("http://ark.intel.com/Product.aspx?id=36681") your CPU supports 64-bit instructions.  why dont you download Ubuntu 64-bit instead of the i386 one?

---

### Post by frunns on 2009-07-03
If your problem persists you can try and enter the command quit or exit, can't remember which one. You might have to do it a few times, but it might continue booting by doing so. Have had the same problem with the live-USB.

And as long as you're not going to try and use more than 3-4GB RAM, the benifits of 64bits are few, and might create a few problems for a new user.

---

### Post by Jazzy_Jeff on 2009-07-03
I also get the busybox error every time I try and use the live cd. I downloaded the alternate install cd and installed from that without any problem. It is a text based install but easy to use.

---

### Post by Sef on 2009-07-03
> I also get the busybox error every time I try and use the live cd. I downloaded the alternate install cd and installed from that without any problem. It is a text based install but easy to use.

If you want to dual boot or set up a home partition, then it can get a little tricky.  Nothing hard, but just doing it the first time can be nerve wracking.

---

### Post by lsl01 on 2009-07-03
thank you fo all your helpfully suggestions it seems lol that you cannot burn the live cd at any high speed i did what synapsys suggested and burned at 4x and wahlaa it worked i am not gonna say how stupid i was at first i burn at 8x and i thought it would have been slow enough lol but thank you all again i love this os so far looking forward to be a active member in this community

---

