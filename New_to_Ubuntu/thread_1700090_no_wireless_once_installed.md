---
title: "no wireless once installed ??"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by xwhyz on 2011-03-04
right thought i'd give unbuntu a go.

so tried a live cd and loved it, picked up my wifi straight away.

so i installed it as dual boot on a win7 system

now it can't find the wifi

any ideas what i've done wrong?

---

### Post by grahammechanical on 2011-03-04
What have you done wrong? Now, you are tempting me.

Seriously, do you see a network icon? It should be like four curved arcs radiating upwards and there should be a red exclamation mark against it.

You do not tell us what kind of computer you have or what version of Ubuntu you have installed.

If it is a laptop, then make sure that the wireless adapter is switched on through the keyboard. As you were able to use wireless with the live CD there must be a network icon.

Right click the icon and make sure that there is a tick mark against both of the lines Enable Networking and Enable Wireless. If there is not then click on each line.

Left click the network icon and see if there are any wireless networks available. A reboot might be useful.

How did you connect whilst using the live CD? Do the same now.

Regards.

---

### Post by xwhyz on 2011-03-04
thanks for the the quick reply

i realise i haven't been to clear in the original post.
its unbuntu 9.10 64 bit
on an R2 unit (mini tower pc)
when itried it live it instantly found my wifi connection a black box appeared in top right of desktop to say wireless networks found click here to connect, which i did entered my key and away it went, tested a few other things like sound and decided to install it.
once installed and booted it now says there is no network, its enabled.

just a bit daft the live version works better than an installed version

the usb dongle is a tenda (Ralink Technology, Corp)

really want to give linux ago :)

---

### Post by spiky001 on 2011-03-04
Can you connect a wire connection and run the updates this might cure your problem

---

### Post by xwhyz on 2011-03-05
just needed to restart it doh!

---

### Post by xwhyz on 2011-03-05
well it still dosent work

it can see the network but it wont let me connect, keeps saying i'm disconnected.
i click on network manager, under wireless it says disconnected
under available is my network i click on that (following the faq) and nothing happens.

so i left click on network manager and edit connection
i input my password and click ok

the icon spins for a while but still dosnt connect
and the black box appears saying i'm disconnected.

i'll be looking for the how to unstall linux topic next lol

---

### Post by willhurley82 on 2011-03-05
I don't think you've done anything wrong, so to speak.  As a rule of thumb, it's easiest to install Linux with a wired connection and update so that you may update your wireless capabilities.  I'd try going wired, hitting the software manager, installing the ndis software, then going into system->administrator->synaptic package manager and do the network backends.  I had a similar problem and just went through and installed everything that had to do with wireless networking.  My Ubuntu keeps my internet speed at 100kps or better, where windows would fluctuate from 7 to 100kps.

---

### Post by grahammechanical on 2011-03-05
Are you absolutely sure that you are putting in the correct pass phrase? I once put in my log in password and it failed to connect. It took me several minutes to work out what I had done wrong.

Not only that but, network manager remembers whatever you put in as a password. So, it will try with the wrong password and not inform you that it is the wrong password. It will just ask you to authenticate all over again.

By the way, the network icons are different in 9.04 than in 10.10. This is why the version of Ubuntu is useful information. But you noticed that.

Regards.

---

### Post by wep940 on 2011-03-05
+1 on the password error, with an addition:  network manager will remember your attempt thereby not allowing a new password to take, as already mentioned, but if you look under network manager and edit connections, then delete your existing connection definition it should clear it.  Then try to connect from scratch again, being sure to watch your password (you can check the box to view the password you have typed).

---

### Post by xwhyz on 2011-03-07
to fix this problem i got the new 10.10 64 bit iso
stuck it on a flash drive
went live, connected to the Internet
used g parted to delete the previous install
and installed from the desktop
then i had to edit the grub menu to remove the old Linux entry.

yipee

---

