---
title: "wireshark vs. wireshark root"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by shahin on 2007-04-16
Greetings-
   What is the difference between regular wireshark instance vs. the root?  I just installed it on a edgy machine and there are two icons.

---

### Post by ohioboy757 on 2007-04-17
wireshark root is required to have access to the NIC to capture packets but to read previous captures just use wireshark.

---

### Post by pawhe955 on 2008-05-27
:confused: I just added/installed Wireshark (under hardy, 8.04) and expected to see 2 entries in the "Applications"->"Internet" list - one "Wireshark" and one "Wireshark (root)" - but only the first one is listed, so I can't run it as root, and I can't capture packets.

Any ideas how I either edit the existing one to run as root; or add a 2nd entry that runs as root?

Thanks,

---

### Post by tastyllama on 2008-06-23
> I just added/installed Wireshark (under hardy, 8.04) and expected to see 2 entries in the "Applications"->"Internet" list - one "Wireshark" and one "Wireshark (root)" - but only the first one is listed, so I can't run it as root, and I can't capture packets.

Any ideas how I either edit the existing one to run as root; or add a 2nd entry that runs as root?

Thanks,

I ran into this same problem on Hardy 8.04  All you have to do is go to System > Preferences > Main Menu

Then find and right click on "Wireshark".  A menu will pop up, click properties.

Change command from ```
wireshark
``` to ```
gksu -u root /usr/bin/wireshark
```

Then you will have wireshark run as sudo.  Alternatively, you can create a new entry with name: "Wireshark (as root)" and command:"gksu -u root /usr/bin/wireshark".  Then you will have both of your icons.:)

-tastyllama

---

### Post by beep_gr on 2008-06-23
> **tastyllama said:**
> I ran into this same problem on Hardy 8.04  All you have to do is go to System > Preferences > Main Menu

Then find and right click on "Wireshark".  A menu will pop up, click properties.

Change command from ```
wireshark
``` to ```
gksu -u root /usr/bin/wireshark
```

Then you will have wireshark run as sudo.  Alternatively, you can create a new entry with name: "Wireshark (as root)" and command:"gksu -u root /usr/bin/wireshark".  Then you will have both of your icons.:)

-tastyllama

I have a problem when I run wireshark as root user via 'gksu -u root /usr/bin/wireshark'
The program freeze and I have to close it via 'force quit'

When I run the program from terminal 'sudo wireshark', the program works fine...

---

### Post by tastyllama on 2008-06-23
Works fine on my computer, Hardy heron 8.04.

Maybe something wrong with your gksu command?

When I try sudo wireshark it works for me, so you can put that in the command line instead of the other.  I just looked at the way Etherape did it, and followed suit.

-tastyllama

---

### Post by scotty64 on 2008-07-01
> **beep_gr said:**
> I have a problem when I run wireshark as root user via 'gksu -u root /usr/bin/wireshark'
The program freeze and I have to close it via 'force quit'

When I run the program from terminal 'sudo wireshark', the program works fine...

I can confirm this - same here.

---

### Post by tastyllama on 2008-07-02
See [This Thread]("http://ubuntuforums.org/showthread.php?t=761461") for more info.  Looks like there are some different solutions.  Also saw "gksudo -u root /usr/bin/wireshark" as a solution.

On my computer, all the commands work fine.  Even tried on another computer, with same results.  Make sure your system is updated.  Otherwise, maybe try removing and reinstalling wireshark package.

-tastyllama

---

### Post by Master Chief on 2008-07-02
Just don't use [COLOR="Red"]gksu -u root /usr/bin/wireshark[/COLOR] but use [COLOR="SeaGreen"]sudo -S /usr/bin/wireshark[/COLOR] instead and you're fine to go.

Remark: I just checked it and that doesn't work either. In fact I can only start it from the console ?!?

---

