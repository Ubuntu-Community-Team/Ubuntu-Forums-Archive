---
title: "Can't get Windows Wireless Drivers Network Configuration Tool Working"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by mikegerard on 2009-04-09
I am trying to connect a Dell 1350 wlan wireless card.

I go to system/administration/windows wireless drivers and open the tool.

Then I pick install new driver.  I pick the .inf file from the list (had it on my thumb drive already)

I can see on the screen that my hardware driver "bcmwl5" is there and there is a notice that says the hardware is present.  

so I'm almost there.  Then I press "Configure Network" and get a "Could not find a network configuration tool" popup.  

Any ideas on how to add my network configuration tool? I have already installed all the gnome network tools but I must be missing something.

Thanks for your help in advance,

Mike

---

### Post by cariboo on 2009-04-10
Are you running ndisgtk as root? Press Alt-F2 and type:

```
gksu ndisgtk
```

Jim

---

### Post by mikegerard on 2009-04-10
Yes, I'm running as root.

I'm doing it through the gui System/Administration/Windows Wireless Drivers
so I was not sure but I ran the command you gave me from a terminal window and get the same message....could not find a network configuration tool.

I also looked at the dell bios and wireless should be on and should be toggled by pressing fn + f2.  Tried that and nothing happens.

---

