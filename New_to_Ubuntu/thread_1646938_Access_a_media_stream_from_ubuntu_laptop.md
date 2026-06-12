---
title: "Access a media stream from ubuntu laptop"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by gredawarha on 2010-12-16
Hi all

Apologies if this has been asked but I could not find what I was looking for.

I have a desktop running Kubuntu  10.04 it has a number of video and music files on it.  I use ps3 media server to stream to my ps3 so I can watch movies and music on my TV in another room.

My girlfriend has Ubuntu 10.04 installed on her laptop.  How can she access the media so that she can watch the files on the desktop.  She is not technical savvy so the easier the better as I will not always be there to do it for her.

Many thanks

---

### Post by Wobblybob on 2010-12-18
not having a ps3 I assume the server you are using streams Upnp, if so install the VLC media player from the software centre open [View], [Playlist] select [Local networks] on the left hand side and open [Universal Plug'n'Play] and hopefully your server will show and allow you to open the media on your server.

---

### Post by gredawarha on 2010-12-19
Hi

Thought that VLC would be a good start but so far no joy. Tried your suggestion but the server did not show.

---

### Post by Wobblybob on 2010-12-20
try adding djmount to your girlfriend's lappy as follows [it works for my media server Mediatomb which is upnp]

Firstly add the following by running these command in a terminal or synaptic if you prefer

sudo apt-get install build-essential

sudo apt-get install libfuse-dev

$ sudo apt-get install djmount

create the mount point;

cd /media
sudo mkdir upnp
sudo chmod 777 upnp

Now mount the upnp in the folder

sudo modprobe fuse
sudo djmount -o allow_other /media/upnp

You should now have a folder /media/upnp and inside it a folder from your media server should show up which you can navigate. If not you may need to check any firewalls you have setup on both PC's. If it's worked then the previous advice for VLC should now work.

To auto mount;

The following steps do work for auto starting djmount under ubuntu using a script called djmount:

cd /etc/network/if-up.d
gksudo gedit ./djmount

paste these contents into the file:

#!/bin/sh
# Not for loopback!
[ "$IFACE" != "lo" ] || exit 0
modprobe fuse
fusermount -u /media/upnp
djmount -o allow_other /media/upnp

then save it and exit gedit, now add the permissions;

sudo chmod 755 ./djmount
sudo chown root ./djmount
sudo chgrp root ./djmount

---

### Post by gredawarha on 2010-12-21
Hi WobblyBob

I will give it  a try and let you know how I get on.

Thanks

---

