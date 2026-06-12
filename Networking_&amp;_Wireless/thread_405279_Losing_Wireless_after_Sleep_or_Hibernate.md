---
title: "Losing Wireless after Sleep or Hibernate"
date: 2007-04-09
forum: Networking &amp; Wireless
---

### Post by mikeyk on 2007-04-09
Hi all,

Running Feisty, totally loving it. The only problem I'm having is that my Wireless Connection (an Intel 2200a/b/g builtin card) works well on first boot, but will often stop working if I sleep and wake up. In that situation, the Gnome networking applet in the top right corner will read "No network devices configured". 

If I try to sudo ifdown eth1 and then sudo ifup eth1, it complains that eth1 no longer exists. If I run iwconfig, it still shows an entry for eth1 and claims it's connected to my university network's SSID, but I can't connect anywhere.

Has anyone run into this before? Is there a way of having Ubuntu rescan my computer for the wireless device to have it re-enable itself? Rebooting every time is kind of a drag.

Thanks!

---

### Post by tommie74 on 2007-06-17
My computer with Xubuntu feisty had a problem with getting an ip-adress after waking from hibernation. I´ve solved this problem by changing /etc/default/acpi-support

Editing this file, look for the line below, where to add [networking] after that no problems anymore:

# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"

Hope this will work for you to,
Thomas.

---

### Post by Chaotic Thought on 2007-08-15
Thanks for the tip. I had a similar problem but with a wired connection. Anyway, adding **networking** to the STOP_SERVICES list worked perfectly. I suspect this is a bug--having "networking" in the list should probably be the default.

Anyway, I'm just glad to have suspend to disk working on my Laptop (in Linux). Though, restoring from hibernate still doesn't seem as quick as Windows.

---

### Post by Ariondys on 2008-03-25
OK, really noob to Linux.  Clearly a windows noob too cuz I made the switch after "trying" to fix my Windows and mucking it up pretty bad -- no windows install CD either.

Ubuntu:
I am wired not wireless.
I started using Hibernate because [COLOR="DarkOrange"]clearly[/COLOR] using Suspend would make the Connection go down.  However it is more subtle perhaps using Hibernate and the Connection appears to stay on, but then I just had to reboot because Mozilla couldn't find any webpages after I came back from Hibernate... I'm sure I have been able to do this before.

Also I try to edit this file: /etc/default/acpi-support
but it says I do not have permission even though I am the one with permission to do whatever I want.  =(

---

### Post by Ariondys on 2008-03-25
sudo gedit acpi-support
OK, I found it.  lmao... I can be master of my computer but only if I type sudo before I do anything... that's going to seem superfluous after a while.  So hopefully no more networking problems now  *fingers crossed*

---

