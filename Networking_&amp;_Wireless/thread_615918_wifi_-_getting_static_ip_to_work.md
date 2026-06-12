---
title: "wifi - getting static ip to work"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by netreg on 2007-11-17
Hi all, 

i apologize in advance if I am going over old ground but I couldn't find anything similar in the search. I use static IP addresses and i have continuously tried to get wifi working with a wpa and static ip..

I get the first two working out of the box but as soon as i try to set a static ip, the wifi icon disappears at the top and i loose connectivity...

I am now booting from the new 7.10 live cd and it is still the same..

is there a fix/workaround for this.


thanks again

---

### Post by x64Jimbo on 2007-11-17
See if your router supports static IP assignment through DHCP. None of my computers have static IPs set in the OS, but rather the router knows what IP to assign each machine based on its MAC address. It's much simpler this way.

---

### Post by netreg on 2007-11-18
i have the linksys wag354g which doesn't do that...

---

### Post by kevdog on 2007-11-18
You might not need WPA, however take a look at this post.  It gives you a guideline how to set it up:

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

If all else fails then you could go for a manual connection.  This post gives you basics of how to set up a manual wireless connection using dhcp, but not specifically with static IP addresses.  If you use this method, and can get dhcp to work, please post back so I can include the static IP address instructions.
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by Blutack on 2007-11-18
Use WICD
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
It's my goto for anything static and wireless.  Should do exactly what you want.

---

### Post by netreg on 2007-11-18
thanks for the response guys..

Blutack, i will check out the link :)

thanks again

---

### Post by x64Jimbo on 2007-11-18
That looks like a nice little piece of software there. I'll have to try it sometime.

---

### Post by netreg on 2007-11-19
> **Blutack said:**
> Use WICD
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
It's my goto for anything static and wireless.  Should do exactly what you want.

Hi Blutack,

i have installed wicd and it works  - thank you.

I just have one point if i may, i followed the instructions about adding the repository and installed wicd and version 1.3.1 has been installed, yet it seems that 1.3.3 is the latest..  would you know how i could get the upgrade?

many thanks

---

### Post by Limulf on 2007-11-19
Hello. I had the same problem as netreg, so I bookmarked this thread.

 In my case, Wicd is not able to connect via wireless, but following the very easy [instructions]("http://ubuntuforums.org/showthread.php?t=571188") that kevdog mentioned in his post, I finally made my wireless card work properly. Thanks a lot.
 
There was a small thing that delayed me a bit while setting the wifi: my WEP key's last character is "#". I don't know why, but I found by "trial and error" that if I didn't enclose the WEP key within "", bash did not end the iwconfig command when I pressed the enter key, but waited for me to enter more data in a new line that started with ">".

 Best regards.

---

### Post by x64Jimbo on 2007-11-19
The repository will always deliver an application to you in an easy to install format - the deb file. However, it will not guarantee latest version. This is because every time there is a new version of the source code, the repository maintainer must re-compile the source into a deb file to put in the repository. You trade cutting edge-ness for ease of installation. Nearly every package in Ubuntu is chronically out of date because they opt for stability over newness.
If you're interested in always having the latest of a particular program, you might want to consider subversion. It's a great way to stay on top of the latest source and still keep it all manageable.

---

### Post by netreg on 2007-11-20
> **x64Jimbo said:**
> The repository will always deliver an application to you in an easy to install format - the deb file. However, it will not guarantee latest version. This is because every time there is a new version of the source code, the repository maintainer must re-compile the source into a deb file to put in the repository. You trade cutting edge-ness for ease of installation. Nearly every package in Ubuntu is chronically out of date because they opt for stability over newness.
If you're interested in always having the latest of a particular program, you might want to consider subversion. It's a great way to stay on top of the latest source and still keep it all manageable.

x64Jimbo, thanks.  I will have a look around and see how to setup subversion.

regards
netreg

---

