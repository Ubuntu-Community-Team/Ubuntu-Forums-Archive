---
title: "BOINC Running in Background"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Ramalan on 2008-12-23
Hey everyone,

I just started up my computer, and I was wondering why my cpu fan was going non-stop, so I went into the terminal and did "top" and here's what it showed:

>   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5902 boinc     39  19  277m  76m  964 R 99.2  7.6   0:22.08 wcg_faah_autodo    


I have BOINC installed for the WCG and Einstein@Home and everything has been running fine on 8.10.  I was just wondering if anyone else has come across this, or knows a way to stop this from running on startup.  Thanks in advance!

---

### Post by Raynman37 on 2008-12-23
(I can't log into my account that posted this because I forgot the password and I used an old email that I don't use :P)

I was going to edit my previous post because I wanted to add, I switched into root and killed the process and so far it seems to have disappeared, but every time I log on it still comes back.  Is there any way to stop it from starting at the startup?

---

### Post by RomeReactor on 2008-12-23
Hi. Did you install Boinc from the repositories, or did you follow instructions from a web page or a guide?

---

### Post by Raynman37 on 2008-12-23
I installed boinc-manager and boinc-client from the repos, which is what the BOINC site said to do.

[http://boinc.berkeley.edu/download.php](http://boinc.berkeley.edu/download.php)

---

### Post by XCan on 2008-12-23
Did you uncheck the option "While computer is in use" under Preferences -> processor usage? Also, is the "Run based on preferences" selected under "Activity"?

---

### Post by Raynman37 on 2008-12-23
Yeah, actually I've been reading that there is a bug in BOINC that makes it so it doesn't detect when a computer is coming out of idle (i.e. it was idle, i move the mouse or open an app and it doesnt stop).  I have run BOINC on many windows computers at my work, so I have all of my preferences set properly (99% sure...*runs back to check*).

The not running to my preferences part is a different question that I will ask about later if I have indeed not set anything up wrong.  What I want to know is what this process is and why it runs at startup (taking up the entire cpu)...and if there is a way or script (whatever the solution) to stop it from running at startup.

I'm also fairly certain this isn't the BOINC-manager running at startup, because the GUI does not come up and when I go to *Applications > System Tools > BOINC Manager* that is when the GUI comes up.  Is this maybe a problem with the boinc-client?

---

### Post by XCan on 2008-12-23
I've also noticed on my comp that boinc only detects the computer as being used if I press a key on the keyboard. Doing stuff with mouse doesn't seem to be detected at all.

---

### Post by RomeReactor on 2008-12-23
> **Raynman37 said:**
> I installed boinc-manager and boinc-client from the repos, which is what the BOINC site said to do.

That may be why it's running as a background process. If you want to run it only at certain times and on certain days you can set that option by going to the 'Advanced' view, then to 'Advanced->Preferences', in the 'processor usage' tab.

Otherwise, you can download the client from Berkeley's site; opening or closing the Boinc manager will also start or stop the processes. Once you download it and install it, you can run it like this:
```
sh -c "cd /PATH/TO/FILE && ./boincmgr"
```

Just substitute "/PATH/TO/FILE" with the actual location of 'boincmgr'.

---

### Post by Raynman37 on 2008-12-23
Yeah, I have the preferences set up properly (see picture) and it does suspend everything until the computer is idle, but then when I come back and move the mouse, press buttons, open applications, it still runs.

[IMG]http://i555.photobucket.com/albums/jj443/Raynman37/boinc_prefs_sc.png[/IMG]

It also seems that this is a known bug:

[https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/128357](https://bugs.launchpad.net/ubuntu/+source/boinc/+bug/128357)

My real question though was the process that was running when I turned my computer on this morning.  I hadn't touched the manager or any program for that matter and yet the process was running and using my whole processor.

I've sort of resorted to the idle thing not working until they fix it, but I don't want to have to go kill that process every time I start up my computer.  Is there a way to run some sort of script to automatically kill it if there is no other fix?

---

### Post by Raynman37 on 2008-12-23
Actually, I just restarted my computer, and the process did not start! Yay!

I will mark this thread as solved tomorrow morning unless people want to discuss the BOINC not listening to any of my preferences part here (I'd love to discuss it more, but maybe we should make a different thread?).

Thanks everyone for the help!

---

### Post by Raynman37 on 2008-12-26
Ok, the problem is back and worse than ever.  I just started up my computer again and noticed that the fan was running at full speed the whole time so I opened terminal and when I did "top" it showed using up my CPU:

  ```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
19088 boinc   39  19 85544  62m 4264 R 95.2  6.1   3:22.81 wcg_hpf2_rosett    

```

The only problem now though, is that when I kill the process, it starts a new one.  This process begins right when I start up, before I even click to open any programs.  Are there any good places to look to see if there is something in a startup folder somewhere (I'm new to Ubuntu, so something like Windows' "run" folder in the registry)?  

Could it be that BOINC isn't quitting properly when I shut my computer down and there is some residual process running somewhere?

Any help would be appreciated!

---

### Post by RomeReactor on 2008-12-26
Hi again. Try going to 'System->Preferences->Sessions' and see if there's an entry for Boinc.

You could also just uninstall it and download the client from the Berkeley site. See my post in the previous page.

---

### Post by Raynman37 on 2008-12-28
I'm going to try using the new version from the Berkeley website because the versions are different between the Berkeley site and the repos.  I'll use it over the next few days and get back to you if the bug is gone or there.

---

### Post by Skip Da Shu on 2008-12-28
As I understand it scripts (or links to scripts in this case) in the rc3.d folder get executed at 'run level 3' in the boot process.  You can see the link to the boinc-client script in **/etc/rc3.d/S20boinc-client**.

I'm just not sure the proper way to remove this link and leave the script it points to intact so you can still start/stop it later with the commands listed further down.

Might be via rcconf ur maybe some rc-update.d command... but I can't provide the details this minute... off to read up on it.

**EDIT:**  Found this link on it: [removing-or-editing-a-startup-script/]("http://ubuntu.wordpress.com/2005/09/09/removing-or-editing-a-startup-script/")

**EDIT2: Be Careful!**  I used rcconf to remove S20boinc-client and couldn't get it back with update-rc.d... ended up doing a complete removal of the boinc-client package and the marking it for install again... fortunately the complete removal gave me the option of leaving the data directory so no WUs lost.  Whew...

**EDIT3:** Of course I find the below /etc/rc3.d/readme after the fact...

```
The scripts in this directory are executed each time the system enters
this runlevel.

The scripts are all symbolic links whose targets are located in
/etc/init.d/ .

To disable a service in this runlevel, rename its script in this directory
so that the new name begins with a 'K' and a two-digit number, where the
number is the difference between the two-digit number following the 'S'
in its current name, and 100.  To re-enable the service, rename the script
back to its original name beginning with 'S'.

For a more information see /etc/init.d/README.
```  **IF** I read this correctly I could've just renamed /etc/rc3.d/S20boinc-client to /etc/rc3.d/K80boinc-client and then, to get it back you just rename it back to what it was.  Well today was a learning day :-)


Personally I leave it enabled and stop it with this:

```
sudo /etc/init.d/boinc-client stop
```

Then when you desire, restart it with:

```
sudo /etc/init.d/boinc-client start
```

You can even make these two commands desktop launchers.  Besides "start" and "stop" you can also "status" and "restart" and I know all this works w/o breaking anything.

---

### Post by Raynman37 on 2008-12-29
Thanks a bunch!  I renamed the file and I'm going to monitor my system on startups to make sure I did it right.  Thanks again!

---

### Post by Skip Da Shu on 2009-05-20
BTW, 
I've been playing around with a sorta 'BOINC specific distro' called Dotsch/UX.  I originally did this to set up a machine to boot and run BOINC off of a USB stick.  Which I've since broken and couldn't get to rebuild correctly but not the point... 

Using the Dotsch/UX distro (an Ubuntu v8.10 derivative) I set up a 'server' and converted some of the dedicated number crunchers to run w/o HDDs in them.  Dotsch/UX server can be set up to be the DHCP server for your LAN and sets up a copy of the OS for the disk-less clients to boot from (PXE).  Sorta cool (and it is cooler with less HDDs running).  

Of course having a few extra HDDs laying around then led to some other self-generated projects around Linux software RAID.  

I don't think I'd recommend Dotsch/UX for regular desktop usage (It's trimmed down to be a bit more minimalistic for BOINC and small devices) but if you've got a machine whose primary purpose in life is BOINC it'd be a great choice.  Comes with BOINC v.6.4.5 installed and the UCB style scripts (personally I like the Ubuntu scripts better).  His page is [**_[COLOR="Blue"]HERE[/COLOR]_**]("http://www.dotsch.de/boinc/Dotsch_UX.html")

---

