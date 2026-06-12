---
title: "HOWTO: Install Wireshark on Gutsy"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by gammb on 2008-02-23
After reviewing all the various threads on installing wireshark, which provided a wealth of information for this noob,  I believe I fell upon an easier solution than any I'd read.  Hopefully this will be useful for others wanting to use this valuable tool in Gutsy.

BACKGROUND:
[Install and Remove Applications] says Wireshark conflicts with existing software and to use Synaptic Package Manager.

Synaptic says
- can't load wireshark because wireshark-common is unloadable
- can't load wireshark-common because libadns1 is unloadable

The dependency upon libadns1 shown, in:
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages
(this file is referenced in /etc/apt/source.list: which is used by 'apt-get' and synaptic package managers)
...and labadns1 is the only one not already present.

SOLUTION:
I located and downloaded libadns1_1.1-4_i386.deb from
[http://packages.ubuntu.com/edgy/libadns1](http://packages.ubuntu.com/edgy/libadns1)
to /var/cache/apt/archives/
...and then installed it as indicated below...

```
# cd /var/cache/apt/archives
# chmod 644 libadns1_1.1-4_i386.deb
# dpkg -i libadns1_1.1-4_i386.deb
Selecting previously deselected package libadns1.
(Reading database ... 89936 files and directories currently installed.)
Unpacking libadns1 (from libadns1_1.1-4_i386.deb) ...
Setting up libadns1 (1.1-4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
#
```

Now Synaptic allows the marking of "wireshark common" and then "wireshark" and Applying to install.  And when complete both "Wireshark" (for examining previous captures only) and "Wireshark (as root)" (for capturing packets) were found under 'Internet" on the Applications menu.

I can now capture packets.  Hot diggity.
Not bad for lacking a clue as to what I was doing.  :)

---

