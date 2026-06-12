---
title: "Firefox issue"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by MrSnuggles on 2010-01-10
I just clean installed Ubuntu 9.10, installed the updates from the update manager and now when I'm running firefox over time it starts getting slower and slower until I have to restart it, and it's running really fast again. It seems like a memory leak but I'm not sure how exactly it would be one. Any ideas?

---

### Post by lidex on 2010-01-10
Is that 3.5? Did you start with a new profile?

---

### Post by MrSnuggles on 2010-01-10
Yeah, it comes with 3.5. And new profile?

---

### Post by cyberbeast on 2010-01-10
Have you installed too many add-ons? Such problems have known to occur due to a lot add-ons being installed. Try removing certain add-ons that you do not need. It might help.

Good Luck! :)

---

### Post by lidex on 2010-01-10
> **MrSnuggles said:**
> Yeah, it comes with 3.5. And new profile?
Did you have a previous Firefox install and import/copy that profile over?

---

### Post by MrSnuggles on 2010-01-10
I have no add-ons on firefox yet, but thanks for the suggestion. I think it might be something with facebook chat, but not sure. My friend suggested that that might be it.

And no, I didn't.

---

### Post by running_rabbit07 on 2010-01-10
That is odd. I have never had any problems with FB chat slowing things down.

---

### Post by Barriehie on 2010-01-10
I run this from my /etc/crontab once a week; it cleans the sqlite database(s) and then sends me an email.

```

#!/bin/sh
##
## ffclean.sh
## 

CLEANTIME=$(date +%m-%d-20%y)

cd $HOME/.mozilla/firefox/**your_profile_folder_here**
    for F in $(find *.sqlite -print)
        do
            sqlite3 $F "VACUUM;"
        done

echo "FF-cleaned $CLEANTIME" | sendmail barrie@localhost

exit 0

```

HTH,

Edit: I'm running 3.0.16 so no guarantees as to effectiveness.  Would be wise to make a backup copy of your profile folder.

---

### Post by MrSnuggles on 2010-01-10
Yeah, I have to close Firefox every 10ish minutes because it gets to the point where it just completely stops responding (Goes grayish) and wont work.

---

### Post by running_rabbit07 on 2010-01-10
Can you get it to bog down, then open a terminal and enter this command, then post the results?```
top
```

---

### Post by MrSnuggles on 2010-01-11
I'll try tomorrow, as it seems that yeah, only facebook chat makes it slow down.

---

### Post by MrSnuggles on 2010-01-11
Ok, it slowed down and I did top, and then talked for a second and checked it. Basically, Firefox shot up to 91% CPU usage, while everything else stayed the same (Virt, Res, etc).

Before talking - 

top - 18:14:09 up  4:02,  2 users,  load average: 0.12, 0.57, 0.50
Tasks: 135 total,   3 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.5%us,  3.3%sy,  0.0%ni, 78.9%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   1026228k total,   985908k used,    40320k free,    33744k buffers
Swap:  3004112k total,        0k used,  3004112k free,   488252k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3072 mrsnuggl  20   0  440m 142m  30m R 14.9 14.2   4:29.87 firefox            
 1589 mrsnuggl  20   0  156m 5168 3936 R  3.3  0.5   1:31.12 pulseaudio         
 3146 mrsnuggl  20   0 37816  12m 9476 S  1.0  1.2   0:01.41 gnome-terminal     
 1156 root      20   0  650m  35m 9516 S  0.7  3.5   2:13.63 Xorg               
 1938 mrsnuggl  20   0 92128  17m  11m S  0.7  1.7   0:40.13 transmission       
 1726 mrsnuggl  20   0 28812  11m 8688 S  0.3  1.1   0:00.33 polkit-gnome-au    
 1733 mrsnuggl  20   0 17524 5144 3832 S  0.3  0.5   0:00.27 gnome-screensav    
    1 root      20   0  2664 1548 1128 S  0.0  0.2   0:00.80 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 async/mgr     


After - 
top - 18:15:04 up  4:03,  2 users,  load average: 0.11, 0.49, 0.47
Tasks: 135 total,   2 running, 133 sleeping,   0 stopped,   0 zombie
Cpu(s): 96.7%us,  2.0%sy,  0.0%ni,  0.0%id,  1.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1026228k total,   989476k used,    36752k free,    33832k buffers
Swap:  3004112k total,        0k used,  3004112k free,   490160k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3072 mrsnuggl  20   0  440m 143m  30m R 91.1 14.3   4:51.70 firefox            
 1156 root      20   0  653m  34m 9516 S  5.3  3.5   2:15.77 Xorg               
 1704 mrsnuggl  20   0 42620  18m  13m S  1.0  1.9   0:08.02 gnome-panel        
 1589 mrsnuggl  20   0  156m 5168 3936 S  0.7  0.5   1:32.45 pulseaudio         
 1703 mrsnuggl  20   0 31716  22m 8196 S  0.3  2.2   0:13.63 compiz.real        
 1938 mrsnuggl  20   0 92128  17m  11m S  0.3  1.7   0:40.36 transmission       
 3146 mrsnuggl  20   0 37948  12m 9552 S  0.3  1.3   0:01.69 gnome-terminal     
 3167 mrsnuggl  20   0  2472 1176  884 R  0.3  0.1   0:00.34 top                
    1 root      20   0  2664 1548 1128 S  0.0  0.2   0:00.80 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.08 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 netns    

Also note that I wasn't running transmission yesterday, so that's not slowing it down.

---

### Post by running_rabbit07 on 2010-01-11
Wow, there is definitely something wrong there. Are you using NoScript? FB Chat works fine with it.

---

### Post by MrSnuggles on 2010-01-11
NoScript?

---

### Post by sandyd on 2010-01-11
[https://addons.mozilla.org/firefox/addon/722](https://addons.mozilla.org/firefox/addon/722)

---

### Post by running_rabbit07 on 2010-01-11
Thanx Carlee, ya beat me to it.

---

### Post by B-Witty on 2010-01-11
> **MrSnuggles said:**
> I have no add-ons on firefox yet, but thanks for the suggestion. I think it might be something with facebook chat, but not sure. My friend suggested that that might be it.

And no, I didn't.

Yeah, FB chat does slow things down, but if it is exited then is speeds back up for me.

---

### Post by MrSnuggles on 2010-01-11
Yeah, even with NoScript it runs the same.

---

### Post by cyberbeast on 2010-01-11
A re-install might solve your problem. Backup your bookmarks and personal data, then go to Applications>Ubuntu Software Centre and remove Firefox. After uninstalling, install it again. 

That should solve your problem.
:)

---

### Post by running_rabbit07 on 2010-01-11
No need to reinstall your system. Open Synaptic Package Manager, search for Firefox-3.5, click for complete removal, click apply. Open a terminal and run ```
sudo apt-get autoremove
``` which will remove all leftover files from Firefox being installed. Once this is finished, reinstall FF with this command or via Synaptic.```
sudo apt-get install firefox-3.5
``` I can't make any promises that this will fix the problem, but doing a complete reinstall may be a bit much.

---

### Post by DamenW on 2010-01-11
try turning off apparmor profiles for Firefox if you have them running.  This can cause this problem.

---

### Post by t1nm@n on 2010-01-11
my problem is another my firefox window border is gone...but all my other appwindows work fine... can any one tell me why? and how i can get it back:(

---

### Post by running_rabbit07 on 2010-01-11
> **t1nm@n said:**
> my problem is another my firefox window border is gone...but all my other appwindows work fine... can any one tell me why? and how i can get it back:(
Dude, start your own thread.

---

### Post by MrSnuggles on 2010-01-13
Apparmor?

---

### Post by clay woodruff on 2010-01-13
whats your CPU % at when that happens, and anything in system monitor that is using a high %

oops my bad someone already addressed that

---

### Post by MrSnuggles on 2010-01-13
K, so let me try to describe what exactly is happening better. It's not actually just when I talk. If I'm talking to one person for an hour it wont slow down. The only time it slows down is which I switch between the little chat windows. So talking to more then one person slows it down to the point where it just turns grey and refuses to do anything. 

What I've tried so far is using that one security program (Forgot the name), and uninstall and reinstall. Still isn't working. Should I download Apparmor or..?

---

### Post by running_rabbit07 on 2010-01-13
> **MrSnuggles said:**
> K, so let me try to describe what exactly is happening better. It's not actually just when I talk. If I'm talking to one person for an hour it wont slow down. The only time it slows down is which I switch between the little chat windows. So talking to more then one person slows it down to the point where it just turns grey and refuses to do anything. 

What I've tried so far is using that one security program (Forgot the name), and uninstall and reinstall. Still isn't working. Should I download Apparmor or..?

AppArmor is already installed. It just has to be configured. To enable apparmor for firefox, enter this into a terminal.```
sudo enforce firefox
```If this gives you any trouble, turn it back off with. ```
sudo complain firefox
```

I am picturing your problem in my mind and I believe Facebook is the problem. every time you click to talk to the next person, one or more packets has to be sent to the FB server letting them know you have changed your target and then they respond with what the target is doing. (That is how when you click on the window, it shows the other person you are typing and vice versa.)

That said, I think the problem is with the slowness of the FB server and the speed of the networks the data is traveling on.

---

### Post by MrSnuggles on 2010-01-13
Could it also be that my mouse has something to do with it? Lately it's been double clicking and I can't seem to get it to stop. Changed ports (From a USB mouse to a whatever port the mouse normally goes into) and increased the time for double clicking (In Preferences > Mouse). The double clicking occasionally opens and closes the window before it even comes up.

---

### Post by running_rabbit07 on 2010-01-13
You could try another browser, such as [Epiphany]("https://help.ubuntu.com/community/Epiphany"), [Google Chrome]("http://www.google.com/chrome"), or [Opera]("https://help.ubuntu.com/community/OperaBrowser").

---

### Post by running_rabbit07 on 2010-01-13
> **MrSnuggles said:**
> Could it also be that my mouse has something to do with it? Lately it's been double clicking and I can't seem to get it to stop. Changed ports (From a USB mouse to a whatever port the mouse normally goes into) and increased the time for double clicking (In Preferences > Mouse). The double clicking occasionally opens and closes the window before it even comes up.

That could be part of the problem.

---

### Post by running_rabbit07 on 2010-01-13
I just installed Chrome to check it out and I must say it is faster and may be what you need for speeding up Facebook.

---

### Post by MrSnuggles on 2010-01-13
I'll try it and get back to you if it doesn't fix it. Any ideas on the double clicking or should I make a new thread or..?

---

### Post by running_rabbit07 on 2010-01-13
> **MrSnuggles said:**
> I'll try it and get back to you if it doesn't fix it. Any ideas on the double clicking or should I make a new thread or..?

Time for a new mouse? Or is it still pretty new? Try blowing it out with compressed air.

---

### Post by Bone Crusher on 2010-01-13
Firefox was working really slow for me too. I also installed Google Chrome and I think it is faster. I would recommend Google Chrome to anyone.

---

### Post by MrSnuggles on 2010-01-13
I took the mouse from my dad's computer and I'm still getting the same issue.

EDIT: The comp slowing down issue is fixed with Chrome. I meant the mouse thing there.

---

### Post by running_rabbit07 on 2010-01-13
I am glad to hear the Facebook issue is fixed. If there is a problem with mice working with your system, then I'd recommend a new thread, so that the right people can see the title.

Good luck.

---

### Post by MrSnuggles on 2010-01-13
Thanks for the help.

---

