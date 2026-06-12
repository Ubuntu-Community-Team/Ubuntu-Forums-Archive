---
title: "grub rescue &gt; grub get_charwidth not found"
date: 2010-03-26
forum: New to Ubuntu
---

### Post by quik_lives on 2010-03-26
Hi folks!

Today I was trying to wipe 10.04 and reinstall 9.10 and I clearly did something wrong. My drive had Mint 8 on the "first" partition and 10.04 alongside it, and I meant to reformat the 10.04 partition, but I've done something to the Grub loader in the process.

Now when I reboot the computer, all I get is 

error: file not found
grub rescue>

So I followed the instructions here: [https://help.ubuntu.com/community/Grub2#Rescue](https://help.ubuntu.com/community/Grub2#Rescue) Mode

and everything cruises along alright til I get to the command that begins insmod. Then I get the response "grub get_charwidth not found" and I can't get any farther.

I have a netbook, so no optical drive (though if that's the ONLY solution I can buy one) but tried booting from liveUSBs of several different kinds with no luck.

Any help would be greatly appreciated because I really need to get it working again. (though I'm not worried about loss of data, if that makes it easier.)

---

### Post by Gixxy on 2010-03-26
What happens when you boot to the live usb sticks?

---

### Post by quik_lives on 2010-03-26
It goes right back to the

error:  file not found
Grub Rescue >

screen.

---

### Post by quik_lives on 2010-03-27
Does anyone have any thoughts?  I am still looking for a solution to this problem.

I purchased an external (USB) cd drive this morning and tried to boot from my Windows XP cd, but it does the same thing -- goes straight into "error: file not found" followed by "grub rescue>."

Also, just a note about the original post -- I am setting up the live USBs on a Mac, which is the only alternative machine available to me.

Thanks in advance for your help!

---

### Post by quik_lives on 2010-03-27
Ok - after buying the external CD drive, we burned a Live CD of 9.10 instead of attempting to use liveUSB and that seems to have done the trick.

Now running fine on 9.10, online and all, but can't seem to access the repositories to download restricted extras or anything else. Will make a new thread as it's an apparently unrelated problem, just wanted to wrap up with all the info here.

---

