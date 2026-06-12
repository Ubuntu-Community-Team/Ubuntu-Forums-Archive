---
title: "Ubuntu ubuntu-9.04-server-i386.iso"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by GirlindaLinuxworld on 2009-04-30
[COLOR=black][FONT=Verdana]Hi There,[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I am new to ubuntu and badly need help. I have read and read and me eyes are so sore, but I wont give up on this. I have three issues apart from not knowing what I am doing. I am testing it for work purposes but not getting very far. I am on a windows based domain with ISA 6.[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Ok Yday I downloaded from the net Ubuntu ubuntu-9.04-server-i386.iso (Jaunty Jacklope)and installed this ISO using VMserver (free edition) and it installed fine. [/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]First would you please point me in the direction of a beginners manual for -9.04-server-i386.iso (Jaunty Jacklope) I click on links for it and get page cannot display I'm located in Dublin, IRE.[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Next I cannot resolve my machine name to the ipaddress. I have edited the /**etc hosts** file and it looks fine I can ping by ipaddress for , gateway, dnserver, localhost and get reply but when I try by hostname cannot resolve by hostname. I have restarted network services and restarted the machine as well. I have looked at the /**etc/network/interfaces** and **resolv.conf** and host file and I cannot find anywhere else where further name configuration should take place can you help me or point me in the correct direction?[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]David do you know how I would install the GUI from the command line. Is it part of this iso image? I have tried to install using the[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
**[COLOR=black][FONT=Verdana]apt-get install x-window-system-core xserver-xorg gnome-desktop-environment for starter[/FONT][/COLOR]**[COLOR=black][FONT=Verdana]s Error it returns is Couldn't find package gnome-desktop-environment and when I try the following **sudo apt-get install ubuntu-desktop **I get error Cannot find package ubuntu-desktop. Is there an easier way if I try apt-get update I get another error Its too long to write in here but I have taken a print screen unless you know how I can copy test from a VM console to this message that would be great.[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Then my poxy proxy ISA /etc/apt/apt.conf and in here I am confused as to how the user name and creditional are entered. The threads tell you to enter it as **Acquire::httproxy [http://:username: password@proxyport]("http://:username:%20password@proxyport"); **but it does not advise you if the user name and password are added to this file i.e typed in and in plain text?? or if the brackets of quotes appear around the user credentials either way I'm confused and can't get on the internet. I can ping ISA by Ip address not by it name ...[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]So really I need a lot of advice cause I don’t want to stop learning now I learned a lot in two days but am stuck now. Will you please help me or point me in direction of someone who can? Apols for spelling mistakes. Thanks a mill GirlindaLinuxworld[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by taurus on 2009-04-30
If you want a GUI, why not just install the Ubuntu LiveCD or the alternate CD?  It's easier and faster then install the server and then install the ubuntu-desktop package.

---

### Post by Didius Falco on 2009-04-30
Unfortunately, I can't help you with any of your server-specific questions. What I can do is point you to some server specific resources.

First, I think you would have a lot more success in the server section of the forum.

[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

There you'll find people who are much more familiar with the server version.

Here is the Server section of the Community Documentation.

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)


Here is a guide from HowtoForge:

[http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2)

I was not able to load the 9.04 server documentation either. I'd imagine things are pretty frantic right now with the new release, and they probably just haven't updated that section yet.

I'd imagine that much of the information from 8.10 would still be valid, so I'd use this section

[https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)

and ask about any discrepancies in the server section of the forum.

Finally, here is a link to the release notes of 9.04 that may be useful.

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Good luck in your endeavors!! 

I hope this helps...

---

