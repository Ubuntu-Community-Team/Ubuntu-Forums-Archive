---
title: "Ubuntu Netbook - missing WiFi Internet Icon?"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by listerdl on 2009-10-05
Hi, my net book doesnt connect to the internet. What has happened is that the Wifi connectivity symbol is missing!!

How can I fix this - 

THANKS FOR ALL HELP!!!!

---

### Post by tsger on 2009-10-05
Some more info would be helpful...which version of Ubuntu are you using?  Your sig says 9.04, but your post says 8.10.

---

### Post by listerdl on 2009-10-05
> **tsger said:**
> Some more info would be helpful...which version of Ubuntu are you using?  Your sig says 9.04, but your post says 8.10. Hi thanks - My signature is for another computer.

The icon I am referring to is the one that has two computer screens - thanks

---

### Post by listerdl on 2009-10-05
> **listerdl said:**
> Hi thanks - My signature is for another computer.

The icon I am referring to is the one that has two computer screens - thanks

Normally all I need to do is go to the top bar and right click and it will say + Add to Panel - this then allows me to add the Network Monitor - however with my netbook Asus EEE running Ubuntu netbook it doesnt give me this option?

Im at a loss here! THanks for all help!!!

---

### Post by fooman on 2009-10-05
> **listerdl said:**
> Normally all I need to do is go to the top bar and right click and it will say + Add to Panel - this then allows me to add the Network Monitor - however with my netbook Asus EEE running Ubuntu netbook it doesnt give me this option?


which option is not there?   

...the option to "add to panel"?

...or the "network monitor" option is missing when you click add to panel?

if its the latter...i do not have a network monitor in add to panel either.  if it is just the connection icon that you are referring to,  i believe that is a part of the "notification area".  try right-clicking in the top panel and choose "notification area" and see if that has what you're looking for.

---

### Post by listerdl on 2009-10-05
> **fooman said:**
> which option is not there?   

...the option to "add to panel"?

...or the "network monitor" option is missing when you click add to panel?

if its the latter...i do not have a network monitor in add to panel either.  if it is just the connection icon that you are referring to,  i believe that is a part of the "notification area".  try right-clicking in the top panel and choose "notification area" and see if that has what you're looking for.

Thanks for the help - I really appreciate it.

The problem I have is that I am unable to connect my Asus EEE to the internet (wifi). I run other computers that work fine over Wifi - but this particular ubuntu remix netbook wont help!

If I type "iwconfig" into the terminal it says:


[HTML]lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

[AND then some other code] 

[/HTML]

As you can see - the machine and OS simply doesnt want to pick up any wifi....

Any help very much appreciated - thanks again!!

---

### Post by fooman on 2009-10-05
try going to administration > software sources...click the updates tab and put a check next to "unsupported updates (jaunty backports)".  close the software sources box.

open a terminal and type or copy/paste the following:

```
sudo apt-get update && sudo apt-get install linux-backports-modules-jaunty
```

it may grab another package or 2 with it as dependencies.  when it completes,  reboot and see if you have wireless.

hope it helps.

---

### Post by listerdl on 2009-10-05
Thanks but I guess I need to be on the internet though? Let me get a wired connection then report back - thanks I appreciate your help.

---

### Post by mikewhatever on 2009-10-05
If the icon in the panel is missing, the network manager must have failed to start or something. You can try launching it with alt+f2, **nm-applet --sm-disable**. If that doesn't work, try adding the notification to the panel.

---

### Post by jlgregory on 2009-11-27
It could be that he hasn't applied his password to the key ring, until this is entered the icon does not appear (UNR 9.10).

---

### Post by iphone3gs110 on 2010-05-08
[SIZE=4][COLOR=Red]hi

open add to panel[/COLOR][/SIZE][SIZE=4][COLOR=Red]
add notification area
[/COLOR][/SIZE][SIZE=4][COLOR=Red]I try many time ...[/COLOR][/SIZE]
[SIZE=4][COLOR=Red]some time wifi icon coming back
some times no coming
this is a bug
[/COLOR][/SIZE]

---

