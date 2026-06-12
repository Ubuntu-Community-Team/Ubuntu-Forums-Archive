---
title: "Transmission 1.90 on Ubuntu 9.04"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by h8uthemost on 2010-02-20
I don't think there's much help that can be given to me, but I thought I would ask just incase.

I need to get Transmission 1.90 on my Ubuntu 9.04 Jaunty computer. But it looks like 1.90 is only available to Lucid through Synaptics. And I have never, ever, been able to get any app installed to Linux through a tarball.

So is there any other option for me? Besides updating to 9.10 Lucid? Anyone have a .deb of 1.90?

Thanks for any help.

---

### Post by stmiller on 2010-02-20
[http://packages.ubuntu.com/lucid/all/transmission/download](http://packages.ubuntu.com/lucid/all/transmission/download)

You can download that lucid .deb and see if it will install at your own risk:

```

sudo dpkg -i transmission_1.90-0ubuntu1_all.deb

```

---

### Post by h8uthemost on 2010-02-20
Nah, that didn't work. I get the error:

```
Error: Dependency is not satisfiable: transmission-cli (>= 1.90-0ubuntu1)
```

And I downloaded the i386 release, and I get this error:

```
Error: Dependency is not satisfiable: libc6 (>= 2.11)
```

---

### Post by h8uthemost on 2010-02-20
Ok, if I can't update to 1.90, how can I rollback to an older version like 1.7? I"m currently on 1.83. And there's a reason why the 1.8x version are banned for a couple trackers. They don't report stats correctly.

So my only choice is to go to 1.90(which I can't), or rollback to 1.75.

Thanks.

EDIT: I've downloaded the .deb for 1.75, but when I go to install it I get an error that says A Later Version Is Already Installed. So do I just uninstall 1.83, and then 1.75 will install? But if I do this then I'll lose all my torrents that's loaded in my client, right?

---

### Post by mikewhatever on 2010-02-20
You won't loose any torrents, unless you delete the settings. Use remove instead of purge from cli, or mark for removal from Synaptic.

---

### Post by h8uthemost on 2010-02-21
Thank you mike. I'm going to give one more try at building 1.90 myself. And if that doesn't work then I'll rollback to an earlier version.

Thanks for your help.

---

### Post by mikewhatever on 2010-02-21
Hey, you don't have to. 1.90 for Jaunty has just been added to the ppa. Those guys are awesome.:D

[https://launchpad.net/~transmissionbt/+archive/ppa/+packages](https://launchpad.net/~transmissionbt/+archive/ppa/+packages)

---

### Post by h8uthemost on 2010-02-21
I know! I just noticed that. That is awesome. :) I was wondering how my machine update to 1.90. So I guess that's how.

Well, I'm officially on 1.90. :) Thanks. And yes, they are indeed awesome.

---

### Post by h8uthemost on 2010-02-21
Ok, here's another problem I ran into. You guys can probably see what's wrong. I'm trying to get to Deluge 1.2.1. It's not totally important since I think I'm going to switch to Transmission now for good. But just incase, I would like to be at this new update of Deluge. So anyways, I followed the [_PPA instructions_](https://launchpad.net/~deluge-team/+archive/ppa?field.series_filter=karmic) on how to update. And this my process and problem.

I did what the instructions said on the PPA page. I added the two lines into Software Sources and reloaded. But then problem I run into is with the key. On the PPA page, the last part of the key is: 249AD24C

So, I add this to Terminal and run it: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 249AD24C. And everything goes ok. I don't get an error until I run the command: sudo apt-get update. When I do that it goes through a long process, but at the end of the process I get this error:

```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 976B5901365C5CA1
W: You may want to run apt-get update to correct these problems
```

There error says to run apt-get update to correct the problems. I run that command, and I get the same error.

But then...I look into Synaptics under Deluge, and there is an Upgrade mark Deluge to 1.2.1. But when I try to upgrade I get this error:

```
deluge:
 Depends: deluge-gtk but it is not going to be installed
```

So does anyone see what the problem is, or what I'm doing wrong? There is no deluge-gtk in Synaptics for me to install. However, there is a deluge-torrent in Synaptics. And under Description it says: bittorrent client(gtk ui transitional package). But I installed that, then tried upgrading to 1.2.1 again, and I still get the same error as above.

Thanks.

---

