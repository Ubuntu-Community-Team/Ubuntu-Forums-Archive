---
title: "Executable bit"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by Aure217 on 2011-04-09
Hi all,
I just installed Ubuntu today. Looks nice so far. Lots of learning to do though.

Okay, I can't seem to set the executable bit on a file (just a configure file).
I've tried chmodding with sudos and whatever. Can't seem to get it to work.
I am the owner of the file.
The file is on an NTFS partition.
This partition was not automatically mounted, but will mount when I navigate to it through the "Places" menu.
If I try to change the right click=>"Properties" stuff, it reverts instantly.

What settings am I missing etc? Did the partition mount with some kind of noexec flag?

thanks
x

Also, is there a way to slim down the authentication-ness? Eg, I don't want to enter my user password every time the wireless tries to connect.

---

### Post by Karlchen on 2011-04-09
Hello, Aure217.

The crucial detail is this: [quote=Aure217]The file is on an NTFS partition.[/quote] You cannot assign Linux permissions (read write execute) to a file on an NTFS partition, because NTFS uses quite a different set of access permissions.

Kind regards,
Karl

---

### Post by TeoBigusGeekus on 2011-04-09
The ntfs file system does not support permissions as the linux/unix file systems do.
Move your script/binary to an ext partition and then apply the executable permission.

As for the wireless, go to network connections (System or Preferences? - can't remember), find your wireless connection and check the available for all users checkbox.

---

### Post by Aure217 on 2011-04-09
Ah, thanks.
Well, that sucks. However, I guess I don't really want to put Win exes and Linux exes on the same partition anyway. That partition is going to be pure data only, I suppose D:


Re: Wireless thing, didn't work :(
The box was already ticked anyway. Maybe it's because it's a non-broadcasting router, and I need to connect to it manually, which needs to go through some authentication for the command itself. I dunno.

---

