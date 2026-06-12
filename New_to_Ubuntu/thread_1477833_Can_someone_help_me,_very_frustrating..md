---
title: "Can someone help me, very frustrating."
date: 2010-05-09
forum: New to Ubuntu
---

### Post by BadlyNeedHelp on 2010-05-09
Right,

Can someone please help me on how to get my BUFFALO External Hard Drive to connect?

I try to connect it, and it just keeps saying

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

It is really annoying, I have stuff on there that I really need.

I can't run chkdsk, because I haven't got a windows disk.

If you tell me to run somthing in terminal, please explain what to do after I put the code in, because I am new to Ubuntu, and wont know what to do/write when the results come up from the code I just put in.

---

### Post by unmole on 2010-05-09
Try NTFSFIX. It *might* be able to help you.

---

### Post by arpanaut on 2010-05-09
Try plugging back into your windows machine, see if the drive is recognizeed, if so, try unmount/safely remove hardware in windows. Then remove from window machine and try it in Ubuntu again.

---

### Post by BadlyNeedHelp on 2010-05-09
I really don't know how to do that, I looked it up and google and the bits I understood just made this happen..

I get a box pop up and says NTFS Write support configuration tool

Enable write support for internal device - enable write support for external device

I clicked  enable write support for external device, and nothing has happend...

Why cant anything be straight forward :(

---

### Post by BadlyNeedHelp on 2010-05-09
When I plug it into Ubuntu, I can see it there.

As I said before, I don't have a windows machine.

---

### Post by BadlyNeedHelp on 2010-05-09
Guys please help, i really don't want to lose all my things on my hard drive..

---

### Post by Sir Jasper on 2010-05-09
Hi,

My advice is be patient and someone is very likely to help you.

Meantime, if you google search the first line of your error message:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).

you will probably get some helpful information.

My regards

---

### Post by BadlyNeedHelp on 2010-05-09
Solved.

My hard drive now connects, and this is how I did it.

Code:
 $ sudo apt-get install ntfsprogs This package has a nice collection of tool for ntfs drives. To fix your problem let's say your drive is /dev/sda2 

     Code:
     $ sudo ntfsfix /dev/sda2 This should fix the disk. Reboot after this. 

i shall add make sure your extension is the right one you can find this on the original error message you got.

---

### Post by sbeddow on 2012-08-21
Thank you so much Badly, this saved me a lot of stress and headaches, u rock buddy

---

