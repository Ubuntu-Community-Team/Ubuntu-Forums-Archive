---
title: "changing connection timeouts?"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by cfp on 2008-07-01
I have autofs set up as follows:

#/etc/auto.master
/mnt	/etc/auto.misc --timeout=60 --ghost

#/etc/auto.misc
laptop -fstype=nfs,soft,intr holdenlt:/home/holden

(where holdenlt is specified correctly in hosts).

In breazy badger opening the home folder in nautilus was instant with this set up whether or not holdenlt was currently on the network and (if I remember right) doing "cd /mnt/laptop" would return an error instantly if the laptop wasn't on the network.

With Hardy Heron however there's about a minutes delay on opening nautilus (any folder) and a similar delay upon typing "cd /mnt/laptop", when the laptop is not connected. My first reaction was to change the number after --timeout in auto.master, but experimentation and further reading revealed this to be the disconnect timeout, not the connect one.

So my question is whether there's any way of reducing the connect timeout? (And better still stopping nautillus for waiting for a connection before showing the home folder...) From looking at /var/log/messages I'm guessing this is a networking issue as there's the message:

Jul  1 15:02:57 holdendt kernel: [ 1041.265670] rpcbind: server holdenlt not responding, timed out

Any help would be appreciated, as this is incredibly annoying at the moment.

Thanks in advance,

Tom

---

### Post by EnlistedSquire on 2008-08-16
I'm looking for something similar. Using autofs on a wi-fi connected laptop is really slowing down my Gnome login time because I think autofs is trying to mount the drives before the wi-fi is connected.

Any help please?

Thanks.

---

