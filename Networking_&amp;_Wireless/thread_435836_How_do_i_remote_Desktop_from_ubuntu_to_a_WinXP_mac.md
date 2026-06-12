---
title: "How do i remote Desktop from ubuntu to a WinXP machine"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by exidez on 2007-05-07
i am connecting through a VPN to my work and i need to remote desktop to a winxp machine.
Remote Desktop is enabled on this particular XP machine and is working fine but how do i connection to it through ubuntu?
As it is a work computer i cannot install additional software on the XP machine. I know there is a vpnviewer but i believe they use different ports and commands...

---

### Post by eentonig on 2007-05-07
On your linux machine, by default the terminal services client is installed. This app support RDP to connect to windows machines.

applications\Internet\Terminal services client

---

### Post by exidez on 2007-05-07
ok
i do remember seeing it there just didnt know what it did :)
wil ltry it when i get home
thanks

---

### Post by exidez on 2007-05-08
ok it worked, but i ran it in full screen mode..... how to i switch from the remote pc to my linux desktop and how do i disconnect while in full screen mode

---

### Post by ALittleSlow on 2007-05-11
In the Terminal Services Client connection dialog, select the screen size or full screen from the Display tab under "Remote Desktop Size".
During an active session, toggle full screen mode on and off by pressing Ctrl-Alt-Enter.

Note that Terminal Service Client (tsclient) is just a front-end to the command-line tool rdesktop, so reading the rdesktop manual page might help.

My question: how do I redirect my local drives to the host using tsclient? (I can do it via rdesktop, but can't find it in the tsclient interface.)

---

### Post by steevc on 2007-05-11
I'm using remote desktop to my work PC on a regular basis. I use Krdc. It works pretty well, but I get the odd issue with clipboard breaking between local and remote or I'll lose the remote cursor. I've not worked out why some things only work sometimes, e.g. sometimes I can Alt-Tab and it changes windows on the remote PC, but mostly it does it for the local PC.

The main thing is that it lets me work from home rather than having to drive 90 minutes each way :) It's a pity I can't get away with it every day.

---

### Post by docsmooth on 2007-05-11
When you're in full-screen mode in rdesktop or krdc, just hit CTRL-ALT-ENTER to switch to a window of the same size.  By default in KDE, the bottom task bar will now be above the RDP window, so you can access your desktop from there.  I believe in gnome the top task bar pushes the RDP window down when you ctrl-alt-enter, so you can access that easily, too.

---

### Post by overclucker on 2007-07-02
hiya,
i'm having trouble connecting to my xphome box from my fiesty box. i have tried:
rdesktop [my xp ip] <enter>
and a screen pops up for a fraction of a second before disappearing. having never used rdp i have no clue what to expect. any idea what im doing wrong? i have enabled remote terminal services and remote desktop sharing, as well as checked that port:3389 is open on the xpbox. any help would be very. . .helpful, thanks

---

