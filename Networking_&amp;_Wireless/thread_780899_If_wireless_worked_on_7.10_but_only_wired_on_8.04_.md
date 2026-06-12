---
title: "If wireless worked on 7.10 but only wired on 8.04 read this!"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by imaworrier on 2008-05-03
I have noticed hundreds of people seem to have the same problem I had after upgrading to 8.04....the wlan is on, the driver enabled (in my case broadcom 43) but yet no wireless networks appear. As well I was receiving a message at boot that network manager caught a termination command etc. I picked this tip up from another stream that I can"t find. the trick is to hit ESC during boot at the grub command and load from the older kernel (the .22 one as opposed to the .24 one). The only problem is that if you installed 8.04 from cd the kernel is not there, so you need to reload 7.10 first. if you did not have 7.10 running before you can get it from ubuntu. Ok here goes and i hope this works for some of you.....I have spent a week running lpci, -c network et al, but this solution, while time consuming was painless:

Step 1: Reinstall ver 7.10n directly from the cd with no internet support (if you leave the ethernet cable plugged in it seems to install with the new stuff as well)

Step 2: Reinstall the old driver you used to run your wlan under 7.10 (for broadcom 43 users that were not using 7.10 you can get the driver from the ubuntu wiki, download the .tz file and extract to the desktop, open a terminal and simply drag and drop the file from desktop into the terminal and press enter, a window will open, find the install.py file and run, choose the top option, a new terminal will open and install the driver, press Ctrl C to close the terminal and reboot)

*Note, my wlan did not work at this point because I did not do all the blacklisting etc I had to previously do when I originally installed the old drivers, however this did not affect my final outcome.

Step 3: After reboot plug in the ethernet cable. You should have at least a wired connection by now. Next go to System>Administration>Upgrade Manager. Upgrade the packages normally. (I had 211 files and 96 upgrades...took about an hour and a half). Reboot.

Step 4: After reboot: System>Administration>Upgrade Manager and upgrade to 8.04 all over again. Sorry, I did say it was time consuming. Reboot.

Step 5: After reboot you should have 8.04 installed. Reboot again and this time hit ESC during boot at the Grub prompt. You should now have the option of loading the newer .24 kernel and the older .22. Load the .22.

Step 6: After reboot....System>Administration>Synaptic Package Manager and search for 'bcm'.If your card is not broadcom search for your driver. Scroll down the results and you should see your old driver and the newer 8.04 drivers...in my case...b43-fwcutter and the older bcm43xx-fwcutter. Install both of them, if one is already installed, reinstall it.

Step 7: At this point I removed the ethernet and voila, I had wireless networks to connect to. If not yet reboot and make sure to hit ESC again and load the .22.

Odd thing for me....I rebooted 6 times to make sure this worked and I have not had to load the kernel manually at start up, it seems to do it automatically. Also, it was not until I shut down and powered up again that I actually saw a driver under System>Administration>Hardware Drivers but yet I was able to connect. Good luck and feel free to pm me if you need help. Be aware though that 7.10 was my first Linux so I am not that tech savvy; I just got lucky on someone else's tip.

peter.

---

