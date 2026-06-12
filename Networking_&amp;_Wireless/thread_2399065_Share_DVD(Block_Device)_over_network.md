---
title: "Share DVD(Block Device) over network"
date: 2018-08-21
forum: Networking &amp; Wireless
---

### Post by 3djake on 2018-08-21
Hello

I am looking for a solution to share encrypted DVD's over the network. Ideally I would just share the block device and mount it on the remote machine.
The main issue is that the intended use will be for encrypted DVD's, so using something like sshfs would not work as libdvdcss runs into issues.

Have any of you managed to share encrypted DVD's over the network and managed to get them to play (including menus)?

I have experimented with using nbd and that works fine for unencrypted DVD's, if I can get it working with copy protected DVD's then that would be perfect.

Update:
I did some further testing using sshfs and got it to work.

On server.
```
sudo umount /dev/sr0
mkdir /tmp/DVD
sudo mount /dev/sr0 /tmp/DVD
```

and on client

```
mkdir /tmp/DVD
sshfs user@hostname:/tmp/DVD /tmp/DVD
vlc /tmp/DVD
```

This works smoothly, however I would still rather use nbd and I would rather not have to unmount and then remount the device.
I tried again with nbd and got it to work but is was too slow. With a bit of tweaking I think I can get it playing nice with nbd and not have to unmount.

Regards, Jake.

---

### Post by 3djake on 2018-08-23
Ok, I figured out why the encrypted DVD worked, it was because I opened the DVD in VLC player on the host machine which did something with the keys using libdvdcss.

Why can't libdvdcss get the keys on the client machine without doing so on the server machine first?

---

