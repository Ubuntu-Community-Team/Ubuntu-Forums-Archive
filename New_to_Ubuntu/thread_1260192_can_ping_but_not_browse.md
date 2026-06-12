---
title: "can ping but not browse"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by sayo9394 on 2009-09-07
Hello,
I installed the same Ubuntu 9.04 using VMWare Station on a laptop running Win XP, and desktop running Windows 7. Both machines are connected to the same ADSL Modem/router.
when running Ubuntu on the laptop, i'm able to ping and browse the internet with no problems. But when on the desktop, i'm not able to browse the net, i'm only able to ping.

I don't want you to think that i didn't google the problem, here are the links that i looked at with no success.
[http://www.1earthadventures.com/2008/02/08/techie-stuff/ubuntu-can-ping-websites-but-cant-browse-in-firefox/]("http://www.1earthadventures.com/2008/02/08/techie-stuff/ubuntu-can-ping-websites-but-cant-browse-in-firefox/")
[http://ubuntuforums.org/showthread.php?t=201127]("http://ubuntuforums.org/showthread.php?t=201127")
[http://ubuntuforums.org/showthread.php?t=282034]("http://ubuntuforums.org/showthread.php?t=282034")

Again, the same image used in the installation on the laptop running XP was used for the PC running Windows 7, and same VMWare Station.
so the variable here is the Network Card.

Thank you,

Simon

---

### Post by Kobalt on 2009-09-07
Then please tell us a little bit more about this Network Card :)
Did you try to toggle different network settings, such as using bridged connection instead of NAT?

---

### Post by Old_Grey_Wolf on 2009-09-07
I don't see Windows 7 in the list of supported operating systems at [http://pubs.vmware.com/ws65_ace25/ws_user/man_intro.3.10.html#989513](http://pubs.vmware.com/ws65_ace25/ws_user/man_intro.3.10.html#989513). I assume you are using VMware Workstation.

Edit: I didn't find Ubuntu 8.10 or 9.04 or Redhat 5.3 on the list so they must not have updated the list.

---

### Post by Old_Grey_Wolf on 2009-09-07
> **Kobalt said:**
> Then please tell us a little bit more about this Network Card :)
Did you try to toggle different network settings, such as using bridged connection instead of NAT?

I found this page that may help [http://www.archy.net/2009/05/14/vmware-workstation-nat-problem-on-windows-7-rc-build-7100/](http://www.archy.net/2009/05/14/vmware-workstation-nat-problem-on-windows-7-rc-build-7100/). And this page for the Windows 7 RTM [http://www.archy.net/2009/08/10/vmware-workstation-nat-problem-on-windows-7-rtm/](http://www.archy.net/2009/08/10/vmware-workstation-nat-problem-on-windows-7-rtm/).

---

### Post by sayo9394 on 2009-09-08
Hi guys,
 
Sorry for the delay, and thank you heaps for your prompt answers :)
I realised i made a mistake describing the problem, stating there's only one variable between the two machines; the network cards, but missing another MAJOR difference which is the OS itself.
 
Thanks to your hints, VMware station VS windows 7 compatibility, i simply resized my C: drive freeing 40Gb, then installed Ubuntu 9.04 on it's own partition setting my machine as a dual boot :)
 
As expected, the internet connection worked fine, and i was able to browse to any website. Also i was able to set up dual monitors with ease :) and connect to my printer. I'm attempting to move away from Windows, but sadly Crisis can't be installed on Linux.
 
Thank you again, and let the fun begin with Linux :) 
 
Cheers,
Simon

---

