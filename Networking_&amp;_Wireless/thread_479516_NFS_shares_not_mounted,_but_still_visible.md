---
title: "NFS shares not mounted, but still visible"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by TheThirdBardo on 2007-06-20
I came across a strange problem when I changed from dynamic (dhcp) to static IP on my workstation: After rebooting, my NFS-mounts were not visible when running the "df" och "mount" commands, but I could list the files in the NFS-exported directory as if it was mounted.

After testing back and forth I noticed that it has to do with the dhcp/static setting somehow.
I change this in the systemsettings-application, under Networking (sorry if not specifying the correct texts on labels and buttons, but my language is set to swedish, and systemsettings seems to ignore the LANG-variable), I select my network interface, double-click, change TCP/IP-address from dynamic to manual; the IP-adress is entered correctly, I acknowledge, and reboot.
After reboot, I type "mount" in a terminal, no NFS-shares come up. If I try to mount it manually I get the response
```
[tomas@nyarlathotep] ~$  sudo mount -a -t nfs
mount: 192.168.12.9:/export/files already mounted or /net/files busy
```

And I have also disabled the zeroconf-stuff under systemsettings->networking, it seemed appropriate.


/etc/fstab on the workstation (Kubuntu Feisty, IP 192.168.12.4)
```

...
192.168.12.9:/export/files /net/files nfs nouser,auto,rw,nodev,exec,nosuid,rsize=32768,wsize=32768,hard,intr 0 0

```

/etc/exports on the server (Debian Testing, IP 192.168.12.9)
```

/export/files           192.168.12.4(rw,sync,no_root_squash)

```


It's not the biggest problem, I can use DHCP, but since the workstation seems to freak out when my DHCP-server is out of order, it would be nice to fix.

Oh, and why is it a problem, you may ask? :)
Well because I like to have control over stuff, and I freak out when stuff is happening above my head (thats why I prefer Linux/BSD). And also because I want to see how much space is used on the disk on the file-server, the disk should be listed when i type "df" in a terminal.

---

