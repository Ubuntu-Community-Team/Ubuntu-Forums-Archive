---
title: "can't log in due to &quot;home directory does not appear to exist&quot;"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by scotcella on 2009-05-18
Hi all,

I did a fresh upgrade (install) my laptop Dell Inspiron.

Installation went very well and everything was working just fine. I attempted to make a separate home partition following [Psycho cats guide]("http://www.psychocats.net/ubuntu/separatehome")  and followed the instructions without any issues.

Now my problem is before the log in page appears, I have a black screen with a pop up that says:

> Your home directory is listed as: '/home/chrissy' but it does not appear to exist. Do y,
ou want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.

Since that happened, so I rebooted into recovery mode and followed pyschocats suggestions further down the page... 

> chown -R username:username /home/username
chmod 644 /home/username/.dmrc
chmod 644 /home/username/.ICEauthority
exit

which the Chmody things are not recognised or something along those lines. Argh! 

Since that didn't work so, I followed the next step after that booted up the live CD, went to the terminal, and pasted in

> sudo mkdir /recovery
sudo mount -t ext3 /dev/sda1 /recovery
sudo cp -R /recovery/home_backup /recovery/home
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab

Then the next thing that happens is:

The pop up is the same!

Can anyone please help me, what step to take next?

---

### Post by taurus on 2009-05-18
Do you remember to mount /dev/sda1 (if that is where the new partition for /home) to /home in /etc/fstab?

Boot into recovery mode and post the outputs of these commands.

```
fdisk -l
blkid
cat /etc/fstab
df -h
```

---

