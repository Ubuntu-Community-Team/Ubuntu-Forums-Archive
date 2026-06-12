---
title: "Can't browse my Windows network with Nautilus/Konqueror"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by Xzyx987X on 2007-01-14
I've successfully managed to set up file/printer sharing between my Windows and Linux computers, more or less... I still can't get the Linux share's hostname to resolve, so I have to access it by ip. Not a huge issue, but if anyone knows a fix (besides manually adding it to the hosts file) I'd be glad to know about it. Anyway, that's beside the point, because the problem I'm most concerned about now is that I can't browse my Windows network from my Linux box with either Nautilus or Konqueror. Both are able to see mshome in smb:/, but when trying to open it Nautius tells me "Sorry, couldn't display all the contents of 'Windows Network: mshome'.", and Konqueror complains "Timeout on server mshome". There are no errors being reported in samba's log files, so I'm kind of at a loss here. Does anyone know how to fix this?

---

### Post by tpg on 2007-01-14
If you're using KDE, you could try ticking the "Enable Zeroconf Network Browsing" option in System Settings->Network Settings->Zeroconf Service Discovery. Also see if the correct settings are present under System Settings->Sharing.

---

### Post by Xzyx987X on 2007-01-14
No, I'm still getting the timeout error in konqueror even after doing that. Any other ideas?

---

### Post by tpg on 2007-01-15
There might be a firewall getting in the way on the Windows end. Or perhaps the computers need to think they are members of the same workgroup (I seem to remember Samba having some kind of setting for this). I'm afraid I haven't had much personal experience, so I'm just guessing!:)

---

### Post by ivan.tg on 2007-02-14
hi
i had similar issue accessing windows share on a specific computer. In the end it turned out to be very simple issue... in my case though. 
On the remote windows pc "File and Printer sharing for MS nets" was not checked in "This connection uses the following items" in the Local Aarea Connection Properties.
When my girlfriend set the sharing of her pc she has missed this.

---

### Post by stormzen on 2008-03-03
Wow... this thread is over a year old... and yet, with Gutsy, I'm here to report that I have run across the bug.  Got a bit of a breakthrough on it, too, here: [http://www.linuxquestions.org/questions/linux-newbie-8/cant-browse-network-by-workgroup-name-in-konqueror-623178/](http://www.linuxquestions.org/questions/linux-newbie-8/cant-browse-network-by-workgroup-name-in-konqueror-623178/)

When I discovered that konqueror had a similar issue when I tried to browse the network.  Looks like we're not all crazy, after all...  There is a work-around there, too.  You can use smb://ip.address.of.client.machine on both nautilus and konqueror to get the shares for that client to show up.

Just for grins, I went ahead and shared a network folder on the win-box (it is a VMware machine) -- but ensuring that every PC on the network had at least one share did not fix the problem.

Incidentally, I also didn't share any printers.  Don't know if that would cause any problems or not.  Anyway, wanted to at least post the work-around tonight.

---

