---
title: "Connecting to a Windows network"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by longtom on 2009-02-03
Hi,

my PC is part of a simple Windows Network.  When I run WinXP, I am certainly part of it - but not in Ubuntu.  Since I don't have a local printer, this would be of some importatnce.

How do I get the Ubuntu machine to recognise the Windows machines?  Is it a big deal, maybe too much for a beginner?

Greetings

longtom

---

### Post by jimv on 2009-02-03
Is this a Windows domain with a domain controller, or is it just a Workgroup?

---

### Post by johnjohn2 on 2009-02-03
1, Create a workgroup in windows and share some folders!
2, Install Samba in ubuntu from synaptic!
3, I like to reboot here!
3, open run dialogue by pressing ALT and F2
4,Type > shares-admin
5, unlock with your password!
6, Select the folders you would share!
7, nearly there, click the second tab "General Properties"and enter the workgroup name!

Congrats you should be up and running

John
:popcorn:

---

### Post by longtom on 2009-02-03
> **jimv said:**
> Is this a Windows domain with a domain controller, or is it just a Workgroup?

just a workgroup.  I'll try the approach of johnjohn2.  Let you know...

longtom

---

### Post by longtom on 2009-02-03
All up and running - you guys are great.

One more problem...one of those winXP PCs has a printer, I want to access.  Is that possible and if yes, how?

Greetings

longtom

---

### Post by johnjohn2 on 2009-02-09
> **longtom said:**
> All up and running - you guys are great.

One more problem...one of those winXP PCs has a printer, I want to access.  Is that possible and if yes, how?

Greetings

longtom

Thanks

What printer do you have?

---

### Post by longtom on 2009-02-09
Got it right eventually:

[http://ubuntuforums.org/showthread.php?t=1061773](http://ubuntuforums.org/showthread.php?t=1061773)

Thank you for asking.

longtom

---

### Post by johnjohn2 on 2009-02-09
> **longtom said:**
> Got it right eventually:

[http://ubuntuforums.org/showthread.php?t=1061773](http://ubuntuforums.org/showthread.php?t=1061773)

Thank you for asking.

longtom

lovely

now you have to get rid of xp

---

### Post by longtom on 2009-02-10
> **johnjohn2 said:**
> lovely

now you have to get rid of xp


I wish - it appears to be still a long way to go.  Photoshop is one reason (doesn't help I run Gimp and the rest of the crowd doesn't) and Access is the other.  Can't read mdb files - not even mentioning editing.

So XP it still will be for a while I guess....

Greetings

lt

---

### Post by johnjohn2 on 2009-02-10
> **longtom said:**
> I wish - it appears to be still a long way to go.  Photoshop is one reason (doesn't help I run Gimp and the rest of the crowd doesn't) and Access is the other.  Can't read mdb files - not even mentioning editing.

So XP it still will be for a while I guess....

Greetings

lt

If you  have a decent pc use virtual box.
Wine will run a few vindows apps check out

[www.winehq.com](www.winehq.com)

---

### Post by longtom on 2009-02-10
Tried wine - no joy.  To much inbedded in Windows I guess.

I have Ubuntu only on a 30Gb HD.  I mean, I was only testing it.  Now I'm on it whole day and sitting with a 200GB Windows HD doing very little.

Bugger...

lt

Edit:  Isn't there a way to repartion the Win HD in order to find some space for VirtualBox?  I'll go searching - but if somebody knows a good guide or link for that, pls let me know.

lt

---

### Post by johnjohn2 on 2009-02-10
> **longtom said:**
> Tried wine - no joy.  To much inbedded in Windows I guess.

I have Ubuntu only on a 30Gb HD.  I mean, I was only testing it.  Now I'm on it whole day and sitting with a 200GB Windows HD doing very little.

Bugger...

lt

Edit:  Isn't there a way to repartion the Win HD in order to find some space for VirtualBox?  I'll go searching - but if somebody knows a good guide or link for that, pls let me know.

lt


Yes there is,

Are you running XP or Vista
Is Ubuntu installed through WUBI
Photoshop CS3 is working perfectly for me as are some vindows games

---

### Post by longtom on 2009-02-10
Right Johnjohn2, here is the deal.

Installed are:

WindowsXP SP2 on a 250GB HD (not 200...) with 140GB free space (and once I get the old stuff off, probably even more.

Ubuntu 8.10 on a seperate harddrive.

> Is Ubuntu installed through WUBI

Nope - dualboot

> Photoshop CS3 is working perfectly for me as are some vindows games

It is?  How did you get that going?

questions over questions....

lt

---

### Post by johnjohn2 on 2009-02-10
> **longtom said:**
> Right Johnjohn2, here is the deal.

Installed are:

WindowsXP SP2 on a 250GB HD (not 200...) with 140GB free space (and once I get the old stuff off, probably even more.

Ubuntu 8.10 on a seperate harddrive.



Nope - dualboot



It is?  How did you get that going?

questions over questions....

lt

Thank you,

You can shrink the XP Volume by using the Ubuntu Live Disk and using Gparted from System,Admin. I think it is called partition manager.

The reason why i was asking about WUBI was because it is installed through windows it is much harder and sometimes impossible to change.

CS3 worked out of the box using the development version of wine, check the link i posted earlier for a quick how to.

Also VirtualBox from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) allows you to run Windows as a virtual machine.
If you have a Dual Core CPU and Plenty of RAM i suggest you do this.

See attached Screenshot

---

### Post by longtom on 2009-02-11
> **johnjohn2 said:**
> 
Also VirtualBox from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads) allows you to run Windows as a virtual machine.
If you have a Dual Core CPU and Plenty of RAM i suggest you do this.


With you guys I'm never sure what you consider a decent PC.
Will this be sufficient for running Photoshop CS1 in VBox:

Intel Core 2 Duo 2.4 Ghz
2GB Ram
250 GB Sata Seagate HDD?

Greetings

longtom

---

### Post by johnjohn2 on 2009-02-11
> **longtom said:**
> With you guys I'm never sure what you consider a decent PC.
Will this be sufficient for running Photoshop CS1 in VBox:

Intel Core 2 Duo 2.4 Ghz
2GB Ram
250 GB Sata Seagate HDD?

Greetings

longtom

LOL

Your specs are ok matey.
Should run without a hitch.

If you need any other help please feel free to send me a PM

John

---

