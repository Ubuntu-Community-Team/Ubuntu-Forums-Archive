---
title: "Sudo command in Sessions??"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by palmtree on 2007-05-18
I have had problems getting my Linksys wifi to connect automatically at bootup, except when I use WEP 64 Bit and the Network Manager. 

I would like to use 128 bit, but in order to do this I have to use Wifi-Radar due to the longer HEX. I am using Ubuntu 7.04 on my IBM ThinkPad A30. My wifi card doesn't support WPA either.

I currently use the command "sudo wifi-radar -d" from terminal after my laptop boots. This gets my wifi connected and on-line after entering my password. Can anyone tell me how edit and put that command into the Sessions Startup Programs command line, so I get on-line automatically at bootup. I have tried to use the line as above but it doesn't work.

Thanks

---

### Post by freakavoid on 2007-05-18
You can edit your sudoers file and allow a certain group to use that binary without password. Something like this should work

```

%groupname ALL=(root) NOPASSWD: /path/to/wifi-radar.

```

After that 'sudo wifi-radar' shouldn't require any password if you are in that group. I'm not sure about the security issues though.

ps; you should use visudo command to do the editing.

---

### Post by palmtree on 2007-05-19
Thanks for your suggestion, but you're over my head. I am not that familiar with Ubuntu. Not sure where that sudoers file is located or how to edit it.

Is it possible to add a startup program command to the sessions?

Thanks

---

### Post by freakavoid on 2007-05-19
Hmm, obviously adding a sudo command in your session wouldn't work. Have you tried it with gksudo? If it works you will be prompted for the password by every login but you won't have to type the command. Go to system->preferences-> sessions and add a line like this:

```

gksudo wifi-radar -d

```

By the way, my first suggestion is not that hard a job. Feel free to ask if you need help there.

cheers.

ps.: there remains one question though, why do you need root privileges to connect to the net?

---

### Post by palmtree on 2007-05-19
Thanks for that gksudo tip, it works in Sessions, except it is no longer automatic. I now have to click on connect, where-as when I enter the command in terminal, it goes online automatically. Seems that in Sessions, it is ignoring the"-d" which is supposed to avoid the GUI image of the wifi-radar program. 

So ... maybe I'll try your original suggestion if you have time to give me a few more tips on using the groupname and sudoers editing.

Your question as to why Wifi-Radar asks for password, seems its required ... when it runs it comes up with a message that roughly says, "enter password ... this program requires admin password because it can make serious modifications".  I can find no references or preferences to allow disabling this password feature.

---

### Post by freakavoid on 2007-05-19
OK... The sudoers thingy is easy. First make a backup. 

```

sudo cp /etc/sudoers /etc/sudoers.bak

```

Then edit the file with

```

sudo visudo

```

That'll open up an editor in terminal. Add the following line to the end of the file. 

```

%username ALL=(root) NOPASSWD: /path/to/wifi-radar

```

where username is your user name and /path/to/wifi-radar is where wifi-radar scpript is located. Close the editor with ctrl+x and save the file by hitting y when it asks. That should do it. I am not sure though because I don't use wifi-radar and never tried this type of thing with another phyton script either. I googled a bit and the author of wifi-radar says: "I highly recommend running /etc/init.d/wifi-radar at boot time." What does this init.d script do? And there is also a configuration file. Maybe these things will provide you with a cleaner solution.

---

### Post by palmtree on 2007-05-19
Thanks very much for your help. I'll play around with this.
FYI I think the -d makes the wifi-radar program run and automatically sign-in to the strongest signal. This works OK when I do it from terminal after booting up. The terminal just shows the commands scrolling by and eventually it shows that I am connected to my router. If I drop the -d, then when I run this from terminal it starts up the Wifi Radar program and shows all the signals available, including mine. Then I select one and press connect.
Thanks

---

