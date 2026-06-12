---
title: "Unable to connect to a corporate 802.1x EAP network"
date: 2019-02-15
forum: Networking &amp; Wireless
---

### Post by mattig89ch on 2019-02-15
Hello all,  First and foremost, this is a Linux Mint 19.1 question.  I'm asking here, because mint is based on Ubuntu, and noboby over on the mint forums seems to be able to help me.  First post about this issue here: [https://forums.linuxmint.com/viewtopic.php?f=90&t=286983](https://forums.linuxmint.com/viewtopic.php?f=90&t=286983), and second post here: [https://forums.linuxmint.com/viewtopic.php?f=53&t=287514](https://forums.linuxmint.com/viewtopic.php?f=53&t=287514) .  So I'm hoping there will be folks here who can help. The gist is this.  My company lets its employees connect to its internal wifi, using our Domain Username and Password.  My tablet, phone, and windows machine, all can connect and use this wifi no problem.  And I know a few people around the office have apple phones also on the company wifi.  I would just chock it up to them not accepting incoming linux connection requests, but I'm having the exact same issue connecting to a password protected wifi, comonly available from my local ISP (Optimum, if it helps).  The issue is, when I try connect to either of these two wifi connections, the little symbol thats supposed to show activity (a spinning circle in this case) starts going.  Then the screen refreshes, and its like I never clicked on the wifi connection in the first place.  I've tried 4 or 5 times in a row now, and I get the same result.  There is no error, no sound, nothing.  Which is why I can't just google this, and get a result.  I have tried googling this issue, and have come up blank.  If anyone has any ideas for even starting to trouble shoot this, I would appreciate it.  Edit: and all my formatting is gone too.

---

### Post by praseodym on 2019-02-15
Lets try
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by mattig89ch on 2019-02-16
Ok, I'm running the commands now.  Is that second command supposed to take a while?  That sudo tee command I mean.  I ran it, and my command prompt is just sitting there for 5 minutes or so.  I did try closing and re-opening the prompt, then starting again.  But I've gotten the same result so far.  Edit: So just an update.  I let the command line sit there for about a half hour.  There was nothing happening, so I killed the command with ctrl+z.  Is this something I can do myself?  Or does it need to be done via the command line?

---

### Post by praseodym on 2019-02-16
These are two lines only. You better c/p them one by one

---

### Post by mattig89ch on 2019-02-16
ah, ok.  So I ran the commands as 2 lines instead.  And...it seemed to run fine.  tbh, I can't tell myself.  I did get prompted to enter my admin password once.  I also grabbed a screenshot of the output, let me know if you'd like to see that.  Is there another step, or do you think I should now be able to connect to my companies wifi?  Edit: still can't connect. Can you use the command line to connect to a EAP network?  Its not as simple as typing in a password and going.  All of the google results of 'how to connect to a wifi from the command line' are all returning results for just needing a password.

---

### Post by mattig89ch on 2019-02-16
Just figured it out.  I found the answer here: [https://forums.linuxmint.com/viewtopic.php?t=188155](https://forums.linuxmint.com/viewtopic.php?t=188155).  > Re: Network Manager won't ask for password  Post by mcganical » Wed Apr 15, 2015 1:12 pm  I found a simple solution:  Open 'Network Settings' Choose 'Connect to a Hidden Network' For Network Name, put the name of the network (in my case is was 'eduroam') For Network Security, choose 'WPA & WPA2 Enterprise' For Authentication, choose the last option: Protected EAP (PEAP) Then add your username and password  Hope this helps someone else.  This worked for my corporate wifi.  I'm not going to mark the topic solved until I test it for my local wifi hotspot.  But I've got company wifi now!

---

