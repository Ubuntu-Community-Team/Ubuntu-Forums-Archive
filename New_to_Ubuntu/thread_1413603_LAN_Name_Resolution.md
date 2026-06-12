---
title: "LAN Name Resolution"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by KlytusLord on 2010-02-22
Hello, I have read several posts about my problem, but I have been unable to get things resolved, so I am hoping I can get some help here.  I realize this questions has been asked several times already.

My LAN setup is as follows:

1 Windows Server 2008 machine
8 Windows 7 machines
2 Ubuntu machines (version 9.10)

The problem is that the Ubuntu machines cannot ping or access web sites hosted on any of the Windows machines using their machine names.

I cannot rely on using IP address because those are not static.  I can change to static IP address, but I have tested it and Ubuntu can still not browse the default websites by IP, though ping does work when using the IP approach.

On a Windows machine, I can simply type [http://ComputerName/](http://ComputerName/) in the browser and the default site hosted on the ComputerName machine will load without trouble.  I am so far unable to replicate this ability in Ubuntu.

I have installed winbind and samba and have also tried using ComputerName.local to ping and browse other computers.  ComputerName.local only allows me to ping from Ubuntu machine to Ubuntu machine; it still fails when attempting to ping a Windows machine from a Ubuntu machine.

As I said, I am a little lost on the information I have found on this so far, so any help is appreciated.  Many thanks!

---

### Post by cariboo on 2010-02-23
Where are the Ubuntu computers getting their ip addresses from? Are they in the same workgroup/netblock as the Windows systems?

---

### Post by KlytusLord on 2010-02-23
Hello Cariboo

Yes, the two ubuntu machines are in the same workgroup as 5 of the Windows 7 machines, which are the ones I need to have access to.  The rest of the machines are in a separate workgroup, but they rarely need access to and from the ubuntu machines, so getting it to work within the same workgroup would be fantastic.

---

### Post by Iowan on 2010-02-23
[This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To *might* be helpful - although it doesn't exactly sound like your problem...

---

### Post by KlytusLord on 2010-02-24
Thanks Iowan!

This got me farther than anything else so far.  I am now able to ping my machines using their names.

The only remaining issue is I am still not able to browse the websites hosted on those same machines.  In Firefox, [http://MachineName/](http://MachineName/) leads to the error: "Firefox can't find the server at MachineName."

Making progress!  Thanks for all the help.

---

