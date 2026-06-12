---
title: "Firefox-bin Maxes CPU and Freezes in Natty"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by mlnease on 2011-06-24
Hello,

I've had a problem for the last couple days that's getting worse--on opening Firefox, the application freezes after about thirty seconds and if I check 'top' or system monitor, firefox-bin is more than maxing out the cpu usage.


```

mn@mn-OptiPlex-745:~$ top
top - 15:35:16 up  1:22,  3 users,  load average: 0.90, 0.32, 0.20
Tasks: 161 total,   2 running, 159 sleeping,   0 stopped,   0 zombie
Cpu(s): 53.6%us,  6.3%sy,  0.0%ni, 39.6%id,  0.3%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2051940k total,  1888132k used,   163808k free,    48816k buffers
Swap:  5014524k total,      244k used,  5014280k free,   780768k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                        
 5917 mn        20   0  650m 358m  30m R  113 17.9   0:51.38 firefox-bin                                                                                    
 1195 root      20   0 98.3m  31m  17m S    3  1.6   1:31.36 Xorg                                                                                           
 4424 mn        20   0 96540  14m  10m S    2  0.7   0:01.64 gnome-terminal                                                                                 
 1748 mn        20   0  177m  30m  18m S    1  1.5   0:30.51 nautilus                                                                                       
 1751 mn        20   0  257m  63m  19m S    1  3.2   0:48.64 skype                                                                                          
 1460 root      15  -5 51360  44m 1208 S    0  2.2   0:04.05 iplist                                                                                         
 1799 mn        20   0 82940  10m 8472 S    0  0.5   0:03.18 multiload-apple                                                                                
 1916 root      20   0  797m  71m  16m S    0  3.6   0:10.57 java                                                                                           
 4262 mn        20   0  173m  72m  24m S    0  3.6   0:11.89 chromium-browse                                                                                
 4368 mn        20   0  182m  65m  19m S    0  3.3   0:10.80 chromium-browse                                                                                
 4418 mn        25   5  193m  77m  19m S    0  3.9   0:13.19 chromium-browse                                                                                
 5171 root      20   0     0    0    0 S    0  0.0   0:00.32 kworker/0:1                                                                                    
 5844 root      20   0     0    0    0 S    0  0.0   0:00.07 kworker/1:0                                                                                    
 6013 mn        20   0  2632 1152  860 R    0  0.1   0:00.16 top                                                                                            
    1 root      20   0  3056 1828 1252 S    0  0.1   0:02.05 init                                                                                           
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                       
    3 root      20   0     0    0    0 S    0  0.0   0:00.18 ksoftirqd/0                                                                                    
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                    
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                    

```

Interestingly, firefox-bin continues to max out the cpu even after I've forced Firefox to quit (see attachment).

I had accidentally upgraded to FF5 a week or so ago, so thought this might be the problem.  So I downgraded to FF4--same problem.

I'm using Chromium now as a workaround but would be *most* grateful for any advice.

Is anyone else having this problem?

Thanks in advance.

---

### Post by jtarin on 2011-06-24
When in "top" if you hit the "k" key it will ask you which pid to kill.Type the pid number and hit enter. Like windows task manager.
As to your Firefox problem.....backup your bookmarks and use Synaptic to completly remove Firefox.then from the command line```
sudo rm /var/cache/apt/archives*
```then run update then reinstall whichever version you feel comfotable with. I would mark Firefox in Synaptic as "locked version" so it would not ask for update. I normally download my firefox from the current download on the mozilla site and place the extracted folder in /usr/share/lib where the old firefox is located.I usually retain my profile in my /home/username folder.

---

### Post by mlnease on 2011-06-24
> **jtarin said:**
> When in "top" if you hit the "k" key it will ask you which pid to kill.Type the pid number and hit enter. Like windows task manager.
As to your Firefox problem.....backup your bookmarks and use Synaptic to completly remove Firefox.then from the command line```
sudo rm /var/cache/apt/archives*
```then run update then reinstall whichever version you feel comfotable with. I would mark Firefox in Synaptic as "locked version" so it would not ask for update. I normally download my firefox from the current download on the mozilla site and place the extracted folder in /usr/share/lib where the old firefox is located.I usually retain my profile in my /home/username folder.

Thanks very much for the quick reply.

I don't have a problem killing the pid.  I have completely removed and reinstalled Firefox--both versions 4 and 5--repeatedly, with no effect on my problem.

I locked version 4.0 in Synaptic per your suggestion.

I'll try extracting 4.0 into /usr/share/lib and let you know if it helps.

OK--I don't seem to have a /user/share/lib--have I misunderstood?  Thanks for your patience.

---

### Post by jtarin on 2011-06-24
> **mlnease said:**
> 
OK--I don't seem to have a /user/share/lib--have I misunderstood?  Thanks for your patience./user/lib
:P

---

### Post by lovinglinux on 2011-06-24
If the problem occurs on both versions, then I do not recommend locking the version. Firefox 5 is mostly a security update for Firefox 4, which will not receive further updates.

Instead, start Firefox in safe mode from a terminal and disable all add-ons:

```
firefox -safe-mode
```

If the problem doesn't happen in safe mode, then it is some add-on that is causing the issue. You will then need to enable one by one and restart Firefox to find the culprit.

Also, do you start Firefox with many tabs opened? If yes, then it could be a page causing the problem, specially if it has some bad javascript or flash. I recommend using [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") and make sure it also block flash or use [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/").

If the problem still occurs in safe mode, then you could try a new Firefox profile. See [http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting](http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting)

---

### Post by mlnease on 2011-06-24
> **jtarin said:**
> /user/lib
:P
OK, got it--extracted FF4 into /user/lib

---

### Post by mlnease on 2011-06-24
> **lovinglinux said:**
> If the problem occurs on both versions, then I do not recommend locking the version. Firefox 5 is mostly a security update for Firefox 4, which will not receive further updates.

Instead, start Firefox in safe mode from a terminal and disable all add-ons:

```
firefox -safe-mode
```If the problem doesn't happen in safe mode, then it is some add-on that is causing the issue. You will then need to enable one by one and restart Firefox to find the culprit.

Also, do you start Firefox with many tabs opened? If yes, then it could be a page causing the problem, specially if it has some bad javascript or flash. I recommend using [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") and make sure it also block flash or use [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/").

If the problem still occurs in safe mode, then you could try a new Firefox profile. See [http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting](http://www.webgapps.org/tutorials/firefox/troubleshooting/general-troubleshooting)
Thought I'd already posted this, sorry if it's a duplicate.

I did start FF in safe mode--the problem didn't occur so, yes, it's most likely an addon.  I already use NoScript and Flashblock but quite a few others as well, so it was probably a conflict between add-ons.

Anyway, FF4 seems to work swimmingly now, thanks to my having deleted all my add-ons.  I'll unlock FF4, re-upgrade to FF5, begin replacing my add-ons one by one and post the results if I'm able to reproduce the problem in that way.

Thanks *very *much again for your time and advice.

Cheers,

mn

---

### Post by lovinglinux on 2011-06-24
> **mlnease said:**
> Thought I'd already posted this, sorry if it's a duplicate.

I did start FF in safe mode--the problem didn't occur so, yes, it's most likely an addon.  I already use NoScript and Flashblock but quite a few others as well, so it was probably a conflict between add-ons.

Anyway, FF4 seems to work swimmingly now, thanks to my having deleted all my add-ons.  I'll unlock FF4, re-upgrade to FF5, begin replacing my add-ons one by one and post the results if I'm able to reproduce the problem in that way.

Thanks *very *much again for your time and advice.

Cheers,

mn

You are welcome.

---

### Post by jtarin on 2011-06-24
If you downloaded and extracted a firefox installation to /user/lib then you can delete that install if your going to unlock Synaptic an upgrade all future versions through apt.Personally I have always downloaded and installed firefox manually....I get the untouched version that way....before someones mad a package out of it and %$#@* it up.

---

### Post by mlnease on 2011-06-24
> **jtarin said:**
> If you downloaded and extracted a firefox installation to /user/lib then you can delete that install if your going to unlock Synaptic an upgrade all future versions through apt.Personally I have always downloaded and installed firefox manually....I get the untouched version that way....before someones mad a package out of it and %$#@* it up.
More sound advice, no doubt--can you tell me how to delete the /user/lib install without messing with the apt?

Thanks Again,

mike

---

### Post by jtarin on 2011-06-24
> **mlnease said:**
> More sound advice, no doubt--can you tell me how to delete the /user/lib install without messing with the apt?

Thanks Again,

mikeI see you really pay attention to what is instructed......nothing I related had anything to do with installing Firefox through apt.....only freezing the version when it wants to upgrade.....nothing installed through apt......nothing to remove through apt.....just delete it.

---

### Post by mlnease on 2011-06-24
> **jtarin said:**
> I see you really pay attention to what is instructed......nothing I related had anything to do with installing Firefox through apt.....only freezing the version when it wants to upgrade.....nothing installed through apt......nothing to remove through apt.....just delete it.
Got it--thanks again!

---

