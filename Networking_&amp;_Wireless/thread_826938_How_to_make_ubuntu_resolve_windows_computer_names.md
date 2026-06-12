---
title: "How to make ubuntu resolve windows computer names?"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Habbit on 2008-06-12
I'd like my Ubuntu box to be able to resolve the windows computer names of other boxen, both windows and ubuntu/samba. Right now this only works within Nautilus, for SMB connections, but if I try to access MythWeb in my mediacenter box by [http://mediacenter/mythweb](http://mediacenter/mythweb) in Firefox, or ping it by its name, or whatever not in Nautilus, I get "unknown host errors".

With older versions of Ubuntu, I had simply added "wins" to the "hosts" lines of /etc/nsswitch.conf. This still works but borks the Nautilus SMB capability, as it somehow confuses gvfsd-smb so it starts throwing strange timeouts. Is there another way to make the system resolve windows computer names without breaking gvfs? I need some help here, as typing 192.168.1.100 is a bit annoying. I'd prefer not to install a DNS server for my LAN, but if it's the only choice, I'll take it.

---

### Post by Habbit on 2008-06-12
Bump. I'm quite pulling my hairs out with this problem.

---

### Post by prshah on 2008-06-12
> **Habbit said:**
> 
With older versions of Ubuntu, I had simply added "wins" to the "hosts" lines of /etc/nsswitch.conf. 

To resolve windows host names to ipaddresses: (For cases where samba can connect to a machine/share/printer with ipaddress, but not with hostname)

change /etc/samba/smb.conf 
name resolve order = lmhosts bcast host wins
(add "wins" to the end)

The order in which you add wins is important.Any network names given are resolved in the order of the methods mentioned above; eg. "wins" is last above, so it's the last used for name resolution.

If that doesn't work, create a file "/etc/samba/lmhosts" and add your NetBIOS servers names with the following format as a guide:```

192.168.100.5   SERVER
192.168.100.7   CLIENT1
192.168.100.11  CLIENT2
```

Save, exit, restart networking and samba:
```

sudo /etc/init.d/networking restart
sudo /etc/init.d/samba restart
```

Hope this helps.

---

### Post by Habbit on 2008-06-12
> **prshah said:**
> To resolve windows host names to ipaddresses: (For cases where samba can connect to a machine/share/printer with ipaddress, but not with hostname)

I am not having problems with samba itself, I want _other programs_ using libc to resolve addresses to be able to resolve windows host names. As I explained, the way I did that before, using nsswitch.conf, is now inviable because it confuses gvfsd-smb and makes it fail with spurious timeouts.

---

### Post by Fire_Chief on 2008-06-12
Then just add entries for the other systems on your network to the /etc/hosts file. Note, this is dependent on those other systems having static IP addresses.

Cheers!

---

### Post by Habbit on 2008-06-12
> **Fire_Chief said:**
> Then just add entries for the other systems on your network to the /etc/hosts file. Note, this is dependent on those other systems having static IP addresses.

That is exactly why I cannot use a hosts files - I use DHCP :(

---

### Post by rickyjones on 2008-06-12
Is winbind installed? If memory serves me right then this is the needed component to resolve Microsoft SMB names.

-Richard

---

### Post by Habbit on 2008-06-12
Winbind is installed, however I don't know how to make other, non-SMB related programs (aka firefox) query it or whatever necessary to resolve windows host names.

---

### Post by jetsam on 2008-06-12
I think I've run into the same thing.  I'm able to get both Nautilus browsing working as well as have wins in the nsswitch.conf if I force Samba to prefer broadcast name resolution by adding this to the global section of the smb.conf:
```
name resolve order = lmhosts bcast wins host
```

My nsswitch.conf line reads:
```
hosts:		files dns wins
```

This isn't ideal (broadcast name resolution isn't the most efficient), but it seems to work.  This problem seems to be new to Hardy.  

It's confusing how all this gets applied.  Nautilus/gvfs refers to the smb.conf for it's name resolve order first.  That line in the smb.conf says to do things in this order:
1.) look for the lmhosts file.
2.) look for broadcast responses on the network.
3.) look for a wins server.
4.) look at the nsswitch.conf and try its methods.

Probably the most confusing thing: "wins" in nsswitch.conf means use winbind name resolution.  "wins" in the smb.conf line means use a wins server.

---

### Post by Habbit on 2008-06-12
I think that did it, but I'll have to do some stress-testing on Nautilus SMB and gvfsd-smb. I think I won't have bigger resolve times because I didn't have a local DNS server, and thus bcast was already being used. Thank you very much!!

---

