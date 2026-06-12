---
title: "Recently ditched windows for Ubuntu, and internet keeps dropping out"
date: 2017-09-28
forum: Networking &amp; Wireless
---

### Post by nancyrowina on 2017-09-28
I've completely wiped windows from my dell latitude D430 and installed Ubuntu, everything is running fine but my internet connection keeps dropping out, when it does my wifi completely disappears from the list, and I have to restart the computer to get it to reconnect. It's not my internet provider as other devices are not having the same problem. Is this a common problem and is there anything I can do about it?

---

### Post by wildmanne39 on 2017-09-28
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by nancyrowina on 2017-09-28
It just keeps asking for a password and won't let me type anything.

---

### Post by wildmanne39 on 2017-09-28
Type your password and hit enter, it does not show the password in the terminal.

---

### Post by nancyrowina on 2017-09-28
Thanks

```
Get:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:4 http://archive.canonical.com/ubuntu xenial InRelease                     
Get:5 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:6 http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu xenial InRelease [17.6 kB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [60.3 kB]
Get:8 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [633 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [62.6 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [49.2 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [74.6 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [605 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [305 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [211 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [172 kB]
Get:16 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [232 kB]
Get:17 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,888 B]
Get:18 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:19 http://gb.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [4,588 B]
Fetched 2,743 kB in 9s (289 kB/s)                                              



```

Do I need to reboot now?

---

### Post by wildmanne39 on 2017-09-28
No, go to the next step and run the wireless script and post the file so we can see what is going on with your wifi.

Thanks

---

### Post by nancyrowina on 2017-09-28
Do you the pastebinit part or the dist upgrade part? Sorry new to linux. :)

---

### Post by wildmanne39 on 2017-09-28
Yes please do the pastebin part then post the link created here.

---

### Post by nancyrowina on 2017-09-28
This is what appeared in terminal?
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  pastebinit
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 14.6 kB of archives.
After this operation, 160 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu xenial/main amd64 pastebinit all 1.5-1 [14.6 kB]
Fetched 14.6 kB in 0s (93.7 kB/s) 
Selecting previously unselected package pastebinit.
(Reading database ... 234295 files and directories currently installed.)
Preparing to unpack .../pastebinit_1.5-1_all.deb ...
Unpacking pastebinit (1.5-1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up pastebinit (1.5-1) ...



```

I see the link now too, it's in there lol.

---

### Post by wildmanne39 on 2017-09-28
Now post the link here so we can click on it.

---

### Post by nancyrowina on 2017-09-28
[http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/main

Is that right?

---

### Post by wildmanne39 on 2017-09-28
No it will be a pastebin link, did you say yes when asked to create the pastebin link?

Did you actually run the script? This is the command to run the script.

```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

---

### Post by nancyrowina on 2017-09-28
Now when I run the code it's just telling me pastebinit is installed, no links.

Sorry got it now

[http://paste.ubuntu.com/25634355/](http://paste.ubuntu.com/25634355/)

---

### Post by wildmanne39 on 2017-09-28
Please copy and paste these commands into the terminal one line at a time then hit enter after each line:
```
echo "options iwl3945 disable swcrypto=1" | sudo tee /etc/modprobe.d/iwl3945 .conf
sudo modprobe -rfv iwl3945
sudo modprobe -v  iwl3945
```
Thanks

---

### Post by nancyrowina on 2017-09-28
My internet just disconnected and reconnected, are we done now?

Thanks

---

### Post by wildmanne39 on 2017-09-28
That should help, if it still disconnects we can make more adjustments.

---

### Post by nancyrowina on 2017-09-28
I'll mark this thread as solved for now, but come back if it persists. that's the first time it's ever reconnected on it's own without a restart though so I think it's worked.

Thanks for your help.

---

### Post by wildmanne39 on 2017-09-28
I hope so, that is just the minimal we can do but I like to keep it simple.

---

### Post by nancyrowina on 2017-10-10
hello again, the problem has started up again, internet drops out and i have to restart to get it to reconnect, can anyone help? Thanks in advance. if you've read through the whole thread you can see what has already been done, just need to know what to try next. since the last time i posted i've also somehow created an error trying to get a printer to install that says "error broken count>0" too, don't know if that has anything to do with the internet problem.

hello, still need help here?

have also noticed updates are not installing, when i click install they start to, the orange line appears, then they just switch back to install again as if nothings happened.

and now have this if it helps.

[http://paste.ubuntu.com/25719497/](http://paste.ubuntu.com/25719497/)

---

### Post by howefield on 2017-10-11
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by jeremy31 on 2017-10-11
This could be caused by wifi power management```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
See if it works better

---

### Post by nancyrowina on 2017-10-11
thanks, it disconnected and reconnected i'll see if it remains stable and return if not :)

actually have just noticed updates still aren't installing.

---

### Post by jeremy31 on 2017-10-11
See if there are any errors when you try
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by nancyrowina on 2017-10-11
yes i have this error ever since I tried to install a printer and it didn't work, tried running the apt-get - f install but that doesn't work either.

```
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 libgcc1:i386 : Depends: libc6:i386 (>= 2.2.4) but it is not installed
 lsb-core : Depends: libc6:i386 or
                     libc6-i386 but it is not installed
 zlib1g:i386 : Depends: libc6:i386 (>= 2.4) but it is not installed
E: Unmet dependencies. Try using -f.



```

get this when i try to apt-get - f install

```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?



```

here is a thread I started while trying to install the printer with all the info, I don't even care about the printer now, just want to undo whatever damage I've done that is stopping me installing updates.

[https://ubuntuforums.org/showthread.php?t=2373196](https://ubuntuforums.org/showthread.php?t=2373196)

---

### Post by ian-weisser on 2017-10-11
Read the error message carefully: A 'permission denied' error means that you forgot to use 'sudo'
It even gives you a hint: 'Are you root?'

---

### Post by nancyrowina on 2017-10-12
Thanks guys, the error has gone and updates appear to be installing again. :)

---

### Post by vasa1 on 2017-10-12
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

