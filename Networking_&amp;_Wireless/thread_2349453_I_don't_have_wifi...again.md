---
title: "I don't have wifi...again"
date: 2017-01-14
forum: Networking &amp; Wireless
---

### Post by manatee.madness on 2017-01-14
So I made an earlier thread ( [https://ubuntuforums.org/showthread.php?t=2348220](https://ubuntuforums.org/showthread.php?t=2348220) ) about my NETGEAR USB wireless thing not picking up any wifi networks. After running some dude's wireless script and a turning "secure boot" off, I was able to connect to my home network.

However, one of my games on Steam froze, and I couldn't do anything. So I restarted my computer, and when it started up, it didn't connect to my wifi network. Normally it does this automatically, and if I click the icon in the top bar, it shows me several nearby networks. Not a single one is showing now. I have visited several threads and consulted Reddit, but none of the commands have worked, and people on Reddit stopped responding to my post.

I am posting this on my Windows 10 Laptop, as my Desktop, which is, of course, running Ubuntu, can't connect to my wifi network. It is the weekend, I want to play my games and watch stuff on YouTube and other stuff on a computer that doesn't take 5 minutes to process an action. Please, help me. As I am not on my desktop, I obviously can't post the output of any command because I need internet access to do that. I guess if it's ABSOLUTELY NECESSARY, I COULD move this whole setup back downstairs to the Ethernet cable if someone NEEDS to see the output of any commands.

It should also be noted that I have WINE installed. I tried running the disk that is SUPPOSED to set up the NETGEAR USB thing, but an error occurs before it the Setup Wizard can finish all the stuff.

---

### Post by jeremy31 on 2017-01-15
Reboot and use the Grub menu through Advanced options to use an older kernel to boot into and you should have wireless again
Please post results for ```
dkms status
```

See [http://askubuntu.com/a/832741/300665](http://askubuntu.com/a/832741/300665) to fix the dkms.conf file

---

### Post by manatee.madness on 2017-01-15
Is the grub menu the same as the BIOS menu? If not, how to I access the grub menu, and how do I change to an older kernel from there?

---

### Post by jeremy31 on 2017-01-15
Press the shift key during boot and the Grub menu should appear.  Some sites say it needs to be the right shift and some people have seen it where only the ESC key will bring up the Grub menu at boot

---

### Post by manatee.madness on 2017-01-15
Is this only doable on prebuilt computers with Linux installed? My computer was built from scratch, and I can't seem to access this menu. I've tried both shift keys AND the ESC key, but it just boots up normally (still not connecting to my wifi network).

---

### Post by jeremy31 on 2017-01-15
It should work on any computer.  Lets try to modify the grub file so you get a countdown
```
sudo -H gedit /etc/default/grub
```

Go to the line that starts with
```
GRUB_HIDDEN_TIMEOUT=
```

And make it ```
GRUB_HIDDEN_TIMEOUT=10
```
Do the same with this line ```
GRUB_TIMEOUT=
```
Save and exit the text editor then ```
sudo update-grub
```

Reboot and you should notice a countdown in the upper left of the screen, press ESC before it hits 0 and you should get the Grub menu so you can go into Advanced options and pick an older kernel to boot to

---

### Post by manatee.madness on 2017-01-15
I am now in the menu, but there are several options to choose from. Does it matter which one I choose? They all generally say

Ubuntu, with Linux 4.4.0-xx (31, 57, and 59 in place of xx) generic (upstart or recovery mode)

---

### Post by jeremy31 on 2017-01-15
I would use
Ubuntu with Linux 4.4.0-57-generic
No upstart or recovery mode

---

### Post by manatee.madness on 2017-01-15
I just chose one with .57 instead of ,59, and my NETGEAR found all the nearby networks it used to. 

Although, running "dkms status" does nothing...

I'm not really sure WHY booting on an older kernel worked, but for future reference, should I do this every time my NETGEAR can't find my wifi?

---

### Post by jeremy31 on 2017-01-15
Now see the wireless script in my signature and post your results along with results for ```
dpkg -l | grep 8812
```

---

