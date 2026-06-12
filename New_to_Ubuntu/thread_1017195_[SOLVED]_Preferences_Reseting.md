---
title: "[SOLVED] Preferences Reseting"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by SportsGuy2 on 2008-12-20
I recently installed ubuntu to my flash drive a using unetbootin, and it works great. 

I am really enjoying it, but every time I boot it up, all of my preferences are reset. Things like my wallpaper, mozilla preferences, and other visual mods are all reset.

Does anyone have any solutions?

Thanks,
SportsGuy

---

### Post by SportsGuy2 on 2008-12-20
Can anybody help me?

---

### Post by StevenHarper on 2008-12-20
The problem is that your Live USB pen is just like a LIVE CD, it doesn't remember stuff.

Now if I was going to try something I would create a small ext3 partition at the end of the pen and mount it as /home/ then your preferences would get stored there. (modify /etc/fstab to make the mount permanent)

However this may or may not work.

Steve

---

### Post by SportsGuy2 on 2008-12-20
How would I do that???

(Sorry, I'm almost illiterate in ubuntu :P)

---

### Post by StevenHarper on 2008-12-20
hmmm its not a simple job : and you will have to risk losing data on the USB pen, but if your ok with that lets try!

Ok boot off a Live CD, or into your Hard disk Ubuntu and open the System | Partition Manager (you may have to install it if your on a HD install)

Now change the Right hands drop down so its you USB pen (double check the size of your drive - you dont want to break you actual hard disk installs)

Now resize that partition down a bit (free up as much space as want for your home directory) (dont try to make it as small as possible leave a few Megs Gap minimum

Now in the new space create a new ext2 partition.

now run this command and get the UUID of your new partiton

blkid

Now mount the first partition on the pen, find where its mounted and go and edit the /etc/fstab file (do this as super user)

Add a line (with your UUID)

UUID=3358a83d-8cb8-4887-a2cf-23bf2fa4b350	/home	ext2    relatime,errors=remount-ro 0       1

Unmount the pen and try to boot off it : good luck


p.s. you have me interested now : I may try this tomorrow myself

---

### Post by SportsGuy2 on 2008-12-21
I'm not worried about lost data on my pen drive, i just formated it. :)

but i used the live cd to install it on my flash drive, i clicked on the full disk and then went to my flash drive and installed it, but then it required the flash drive to be plugged in for the bootloader to work...

---

