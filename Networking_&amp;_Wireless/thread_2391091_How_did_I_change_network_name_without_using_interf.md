---
title: "How did I change network name without using interfaces?"
date: 2018-05-05
forum: Networking &amp; Wireless
---

### Post by Keith Myers on 2018-05-05
Last year, I was bugged by the constant renaming of the network interface name on my Ryzen system after every BIOS update of which there were dozens.  So after searching for a solution I somehow, somewhere made a change that changed the network interface name from something like enp38s0 to lan0.  I see eth0 renamed to lan0 in syslog at each boot.  But I have been crashing the system every day when the dhcp session is renewed from the syslog trail.

So I wanted to revert the interface back to the standard eth0 name to see if I can stop the crashing.  I am on Ubuntu 16.04 LTS, kernel 4.13.0-39-generic.  I have searched every file and script having anything to do with networking looking for the file that I changed to rename the interface lan0.  I can't find it and I can't remember which file I changed.

There is no /udev/rules.d persistence file in use.  No /udev/rules.d files in fact. /etc/network/interfaces has the standard entries for lo and eth0:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


#eth0
auto eth0
iface eth0 inet dhcp



```

I also have made the preferred change to grub with the ```
GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0"
```

Nothing I have done is able to revert the interface name to eth0 from lan0.  I would be happy to get the firmware defined interface name back even. Removing the ```
GRUB_CMDLINE_LINUX="net.ifnames=0 biosdevname=0"
```
doesn't change anything.  The network interface name persistently remains lan0.

Can anyone help me to figure out what file is causing the default eth0 interface name to be changed to lan0 automatically. Where should I look?

---

### Post by TheFu on 2018-05-05
After you modify any grub settings, you have to run update-grub and for some settings, there are a few other tools that need to be run to update the initrd boot file.  Did you do those?  I'd have to google the commands, so figured you could do that too. Perhaps *update-initramfs* with some options?

BTW, with systemd, eth0 is **NOT** the standard NIC device name any more and /etc/udev/rules.d/ doesn't seem to be used any longer. The name is dependent on the specific driver used and the MAC for the card/device.  This was deemed "better" for systems with lots of network interfaces to prevent conflicts.  I never had issues with eth0/1/2/3/4, but others did.  It wasn't a change for change sake even if you and I didn't want it.

---

### Post by Keith Myers on 2018-05-05
Yes. grub was updated. I know that eth0 is not the "standard" name anymore with systemd.  The BIOS name is standard now.  But since that is what the system defaults to when booting before it is changed by whatever to lan0, I thought if I could get the system to boot with what it is set for now, that would help eliminate one variable with the system crash when the dhcp session is renewed each day.  If it was easy to completely reset the network installation to default and then somehow reinstall it (without a network connection obviously) I would have done so already.  My other Intel Linux system is just running with the default network names of enp2s0f0 and enp2s0f1.  I have no problems with that.  It only recently changed from enps19 and enps20 do to some updates recently supposedly.  And I am likely finished with the weekly BIOS updates on the Ryzen system that made it so frustrating when the BIOS firmware name changed every time.  So going back to the standard BIOS enumeration scheme would be amenable now.  I just can't get the system to do that for some reason.

---

### Post by TheFu on 2018-05-05
[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) is how this is supposed to work from the horses mouth.  The .link seems like it could be on your system.

---

### Post by Keith Myers on 2018-05-06
> **TheFu said:**
> [https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/) is how this is supposed to work from the horses mouth.  The .link seems like it could be on your system.

Looked everywhere.  No .link files on the system anywhere.  Made various ones from the document instructions.  Still cannot get the interface to be named anything other than lan0.

Did ```
$ nmcli conNAME             UUID                                  TYPE            DEVICE 
Auto Ethernet    5259eb49-1b7b-4e42-b7b3-8c12b8dc0619  802-3-ethernet  lan0   
Ifupdown (eth0)  681b428f-beaf-8932-dce4-687ed5bae28e  802-3-ethernet  --     
keith@Darksider:~$ 

```

Tried deleting the lan0 uuid.  Just comes back after re-login/reboot.  The new eth0 interface is listed.  I just can't figure out how to enable it and select it as default over the lan0 interface.

Still having the system  freeze ever day at dhcp renewal.  Always the last thing in syslog before the reboot log entries.  This was not a problem until maybe a week ago.  It was perfectly happy with the lan0 interface name and never caused issues.  So I assume something caused by one of the updates since the system was stable caused this new problem. But I have no clue which update might have caused this.

---

### Post by Keith Myers on 2018-05-06
Well, I just tried the nuclear option.  I removed and purged the network-manager.  Rebooted and had no network connection.  Looked around the drive for vestiges of files that i had created or edited in trying to resolve the issue.  Looked like the purge did a pretty good job of removing the network software.

Reinstalled the network-manager software from the packages I had previously downloaded.  Rebooted and had network connectivity again.  Unfortunately, I still have the lan0 interface name.  Will have to wait and see whether the system still freezes at dhcp renewal tomorrow.

---

### Post by TheFu on 2018-05-07
I didn't refresh my memory, but ... 
Any consideration for increasing the lease period to a week?  At least that way the issue wouldn't happen nearly as often.
Or just using static IP on lan0?

---

### Post by Keith Myers on 2018-05-07
> **TheFu said:**
> I didn't refresh my memory, but ... 
Any consideration for increasing the lease period to a week?  At least that way the issue wouldn't happen nearly as often.
Or just using static IP on lan0?
Actually, I had been thinking of that. And the static IP makes sense also, in fact it makes sense for all my hosts.  Right now the IP's are virtually static anyway.

I think this is going to remain a mystery.  Somewhere in the dark recesses of this installation, some file is changing the network name but I am out of ideas of where that is taking place or what mechanism is causing it.

And the issue won't be around much longer I expect since I will blow away the installation and start from scratch when the Ubuntu 18.04.x LTS distribution is offered up to me automatically or whenever.

---

### Post by TheFu on 2018-05-07
> **Keith Myers said:**
> And the issue won't be around much longer I expect since I will blow away the installation and start from scratch when the Ubuntu 18.04.x LTS distribution is offered up to me automatically or whenever.

18.04 brings a whole new set of issues.  Be certain to search these forums carefully and review the release notes before  deciding.

I'm holding off on even bringing up a test box with 18.04 on it for a few months so some things can be corrected.  Probably won't touch it for production systems until sometime in the fall, assuming most of the issues are addressed.  I have no current plans to migrate any 16.04 systems to 18.04 for at least 2 more years.  It would defeat the purpose for running LTS releases which is mainly about stability with only security updates.

---

### Post by Keith Myers on 2018-05-07
> **TheFu said:**
> 18.04 brings a whole new set of issues.  Be certain to search these forums carefully and review the release notes before  deciding.

I'm holding off on even bringing up a test box with 18.04 on it for a few months so some things can be corrected.  Probably won't touch it for production systems until sometime in the fall, assuming most of the issues are addressed.  I have no current plans to migrate any 16.04 systems to 18.04 for at least 2 more years.  It would defeat the purpose for running LTS releases which is mainly about stability with only security updates.

I know what you mean.  If it wasn't for my Ryzen system and the next two Ryzen builds I will do in a month or so, I would just stick with 16.04 LTS.  But I really want to get at least the 4.15 or preferably the 4.16 kernel with all the Ryzen fixes baked in.  The Intel box will probably just sit on 16.04 LTS for another year at least.

---

### Post by Keith Myers on 2018-05-10
Just looked at the system today and see that it has reverted to the standard v197 predictable naming scheme for the network interface.  All on its own.  I hadn't done anything to the system since my last post.  The interface name is enp4s0 now.

I wonder if it took a DHCP renewal for things to straighten themselves out from the last configuration changes that the network-manager installation did.  Haven't had a reboot/crash either.

So mark this thread as solved with no real reason that I can figure out other than the network-manager reinstallation.

---

