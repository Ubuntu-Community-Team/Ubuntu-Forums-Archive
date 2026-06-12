---
title: "How to back up Network manager before installing wicd"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by taronski on 2009-02-02
Hiya, it seems recomended to backup n/w manager before installing wicd but I am not sure how do it.

Thanks a lot

Taron

---

### Post by handydan918 on 2009-02-02
You can't "backup" networkmanger because it conflicts with wicd. Both cannot be installed at the same time. 
What are you trying to do?

---

### Post by taronski on 2009-02-02
Long story but the origin of the problem is a dodgy Belkin wifi card/driver.   Sees wifi does not connect through security. Trying to sort it by ditching nm and go for wicd. 

My concern is that if something fails in the install I will be without connectivity altogether. Being new i probably have good chance of messing something up, so I wanted a "restore" option.

What would be the best way to proceed.

Thanks

---

### Post by ugm6hr on 2009-02-02
Download the relevant (i.e. i386 or amd64) packages for:
[network manager]("http://packages.ubuntu.com/intrepid-updates/network-manager")
[network manager gnome]("http://packages.ubuntu.com/intrepid-updates/network-manager-gnome")

If Wicd doesn't work, you can just install these back.

---

### Post by taronski on 2009-02-02
Thanks a lot ugm6hr, gpt them saved and installed Wicd but ... after a reboot lost the whole GUI ](*,)] 

Once rebooted I just got the terminal back...

Any suggestion on next steps to get the GUI back?

Thanks

taron

---

### Post by ugm6hr on 2009-02-02
Not sure - what did you do?

Installing Wicd certainly has no effect on the Gnome desktop.  Or any desktop.

But you could try:
```
startx
```

---

### Post by taronski on 2009-02-03
I installed wicd by adding the third party address in synaptic manager, reloaded but could not find wicd in the synaptic search box, so I found advice on how to install from the terminal (sudo aptitude update? and sudo install) got wicd up but then had to reboot for unrelated reasons.

When I repowered up got the user / password mix, getting the blue screen but the only thing on the screens are a terminal and the files had saved on my desktop.  There is no border with applications/places/calendar etc.

Which makes it v difficult for me to do anything since I know - NOT A LOT - about commands in the terminal.

BTW i did a starx and got X: user not authorised to run x server, aborting.

Then I tried sudo startx and got Fatal Server Error:  Server is already active for display 0....

Also when I tried to fire up wicd with sudo wicd client, I dont get the client GUI but a mere var/run/wicd/wicd.pid which means I don't have i/net access on that PC.

Hope this helps.

Thanks

Taron 
 was told that I did not have the privliges to run, i tried sudo startx and got a fatal error.

I am not sure what I did wrong though.

---

### Post by handydan918 on 2009-02-03
> **taronski said:**
> Long story but the origin of the problem is a dodgy Belkin wifi card/driver.   Sees wifi does not connect through security. Trying to sort it by ditching nm and go for wicd. 


Thanks
In most troubleshooting/diagnostic scenarios, it's best to eliminate variable. 
Lose the encryption.
Try to get connected with encryption "off" at the router, and once you get it going, THEN you can play with encryption.

---

### Post by ugm6hr on 2009-02-03
> **taronski said:**
> When I repowered up got the user / password mix, getting the blue screen but the only thing on the screens are a terminal and the files had saved on my desktop.  There is no border with applications/places/calendar etc.

You should have said this to start with!

Press Alt+F2: this opens a box.

Type: **xfce4-panel**

---

### Post by taronski on 2009-02-03
Got my panel back...thanks a lot :D:D

Took the encription off and got connected (it is a 2wire 2700 supplied by BT in the UK), which is great.

Any idea on how to connected once I get encription back on?

Thanks a lot again

taron

---

### Post by ugm6hr on 2009-02-03
To ensure the panel problem doesn't recur - add **xfce4-panel** to your autostarted applications list. Not sure why, but it doesn't autostart with Xubuntu all the time.

Are you using Wicd then?

What encryption would you like to use?

Essentially, Wicd is pretty straightforwards.  Try the password with and without " at the start and end.  Also, you can try entering the password like this **s:password**

---

### Post by taronski on 2009-02-04
Thanks and thanks sorted both.

The problem was that encription on the router was set to WEP open whilst WiCD only does WEP shared.  I changed it on my 2wire and bang got an IP address and all is working.

Fantastic I brought a new lease of life into a 10 years old P3 thanks to Linux (and the community).  

Thanks again

---

