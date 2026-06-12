---
title: "Disk space rapidly dissappearing without doing anything"
date: 2014-06-13
forum: Networking &amp; Wireless
---

### Post by adam64 on 2014-06-13
I have used Ubuntu for a couple years(not a pro, just a casual user), and just upgraded to Ubuntu 14.04.  Yesterday I got a low disk message, so I deleted a few things and it freed up space.  It seemed to be fine, then I got the message again that I had low disk space.  I then deleted larger files, games, and such, and it freed up some space, but soon it started to go down again.  I downloaded bleachbit, ran that to clean up old/archived files.  I had 14.2 gb free at the end of all this and then shut down my computer.  I was on for a little today, I right click on home, selected properties, and still had 14.2 gb, and without doing anything, I wait a couple minutes and it's dropped to 13.8 gb.

I have no downloads going on, I have windows on one partition, and Ubuntu on another.  Has anyone else run into this problem?  Does anyone know what's going on?

---

### Post by Bashing-om on 2014-06-13
adam64; Hi !

What pops to my mind is that the logs are growing exponentially - reporting a system problem.
I would suggest you check your log files in "/var/log" an well as perhaps in your /home directory "~/.xsession-errors".

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by adam64 on 2014-06-13
Looks like I have in var/log, 26.5 gb and growing rapidly.  How would I fix that and how would I check my .xsession-errors?  I tried looking around, but couldn't find much.  
Please be as detailed as possible, I am a very casual user (noob).

---

### Post by Bashing-om on 2014-06-13
adam64; Hey,

One reads the log file to determine what the system is reporting, depending on what the situation is, is what action must be taken.

The log file will be much to large to post to the forum.. what you can do is to post the relevant portion of the log file if you are unable to determine the fault; or paste that log file to 'pastebinit' and pass the URL back so we can read the file.

[INDENT][INDENT]until you know
[INDENT][INDENT][INDENT]there is nothing you can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by adam64 on 2014-06-13
How do I open the xsession-errors file to read it?

---

### Post by Bashing-om on 2014-06-13
adam64; Sorry, missed that one.

The .xsession-errors file is a hidden (leading '.') file in your /home directory.
You can - if that file has not grown to large - read in in terminal with terminal command:
```

cat ~/.xsession-errors

```
see:
```

man cat

``` for the details of 'cat'.

Else: The GUI way from your file manager - key combo ctl+h to "show hidden files" and then open the file in the file manager window.

[INDENT]a victim of tunnel vision
[/INDENT]

---

### Post by adam64 on 2014-06-13
hmm, my xsession-errors is only 190 bytes.
looking over my disk usage analyzer, it looks like var/log is eating up my hd.  Literally, in a minute it jumped from 28.6 gb to 28.7. I looked in var/log, and I found a 17.0 gb syslog file that while I was just trying to open and look it over, jumped to 17.6 gb, and another one that's 11 gb.  So how would I fix this problem?

---

### Post by steeldriver on 2014-06-13
/var/log is a directory - can you narrow it down to a particular file (or files) in the directory?

If it's not obvious just by looking at the file sizes, here's something you can paste in to a terminal to count and list repeating error messages in the major logs:

```

for log in /var/log/{dmesg,syslog,kern.log}; do 
  echo "${log} :"
  sed -e 's/\[[^]]\+\]//' -e 's/.*[0-9]\{2\}:[0-9]\{2\}:[0-9]\{2\}//' ${log} \
  | sort | uniq -c | sort -hr | head -10
done

```

---

### Post by Bashing-om on 2014-06-13
adam64; Well,

Something is logging repeated errors to the system log files. One just has to read the file and see what is generating all those errors and take corrective action. Such that the errors are no longer being generated.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-06-13
@ steeldriver; Thanks for that !

Much better than what I had in mind to do to see what we could do to "see" those errors.

[INDENT][INDENT]a friend in deed
[/INDENT][/INDENT]

---

### Post by adam64 on 2014-06-14
looks like this error keeps getting sent over and over from file "syslog" which is 18 gb, I also have a "syslog.1" that is 11 gb with the same text in it:
```

Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error> [1402608755.122976] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error> [1402608755.123542] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error> [1402608755.124093] [nm-supplicant-interface.c:997] interface_add_cb(): (wlan0): error adding interface: wpa_supplicant couldn't grab this interface.
```

---

### Post by adam64 on 2014-06-14
Can I just disable my wireless?  I don't use it right now, but how would I fix this problem long term?

---

### Post by Bashing-om on 2014-06-14
adam64; Hey,

I am back in th saddle.

Yeah .. wireless issue.... wireless is not in my sphere of knowledge. In order to gain the views of those who do know;
how about we close this thread (solved) as the problem has been identified, and open a new thread in  the "Networking & Wireless" sub forum ( you may reference this thread).You will get a faster/better solution in that new thread. 
To mark as solved -> @ top right of post -> thread tools.

[INDENT][INDENT]If I knew all things,
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bab1 on 2014-06-14
> **adam64 said:**
> I had posted this in general at:
[http://ubuntuforums.org/showthread.php?t=2229560](http://ubuntuforums.org/showthread.php?t=2229560)
Then, I was told to post in the Networking section because I'd get someone who knows more about networking here.

I had a problem with my HD dissappearing rapidly.  I would not be doing anything and I'd go from 13.3 gb to 13.1 in a couple minutes.  Tracked down the problem file to var/log and it looks like this error keeps getting sent over and over from file  "syslog" which is 18 gb, I also have a "syslog.1" that is 11 gb with the  same text in it:

Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver  does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error>  [1402608755.122976] [nm-supplicant-interface.c:997] interface_add_cb():  (wlan0): error adding interface: wpa_supplicant couldn't grab this  interface.
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver  does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error>  [1402608755.123542] [nm-supplicant-interface.c:997] interface_add_cb():  (wlan0): error adding interface: wpa_supplicant couldn't grab this  interface.
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: dbus_g_proxy_cancel_call: assertion 'pending != NULL' failed
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <info> (wlan0): supplicant interface state: starting -> down
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <warn> Trying to remove a non-existant call id.
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: nl80211: Driver  does not support authentication/association or connect commands
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: Could not set interface wlan0 flags (UP): Cannot assign requested address
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: WEXT: Could not set interface 'wlan0' UP
Jun 12 17:32:35 adam-EP35-DS3L wpa_supplicant[1064]: wlan0: Failed to initialize driver interface
Jun 12 17:32:35 adam-EP35-DS3L NetworkManager[944]: <error>  [1402608755.124093] [nm-supplicant-interface.c:997] interface_add_cb():  (wlan0): error adding interface: wpa_supplicant couldn't grab this  interface.

any idea how to fix this?

I have a dual boot windows/ubuntu, and although I've used Ubuntu for a while, I still consider myself a noob, so please be detailed.

There is no need to post duplicate threads.  Just ask the mod's to move the original thread.  Now they need to merge them.  Use the icon at the lower left that says "Report Abuse".  It's really a direct link to the forum admins.

As far as your problem -- I haven't a clue.  :-(

---

### Post by adam64 on 2014-06-14
Sorry, I was told to solve the other one and start a new thread here.  I'll report post, but anyone else out there know what's going on?  I can't use my computer at all since every time I run Ubuntu, I loose hard drive space.

---

### Post by sandyd on 2014-06-14
sorry 'bout that
Clicked move posts instead of merge thread D:

---

### Post by bapoumba on 2014-06-14
Thread continued here : [http://ubuntuforums.org/showthread.php?t=2229675](http://ubuntuforums.org/showthread.php?t=2229675)
Closing this one.

---

