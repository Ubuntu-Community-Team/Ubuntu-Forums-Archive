---
title: "Firefox problem"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by iggy pop on 2010-03-20
I booted up the computer this and then clicked on Firefox but for some reason it just won't open? I have even gone to the terminal and typed 'Firefox' with the same result? Can anyone help please.

---

### Post by r-senior on 2010-03-20
Is it already running and not happy? If you startup "System Monitor", go to the "Processes" tab and sort by "Process Name" is "firefox" listed?

If it is, you could try right-clicking on the firefox process and "End Process". If that doesn't kill it, try "Kill Process". Once it's gone, try running again normally.

The terminal equivalent to the above is

$ ps -ef | grep firefox 

(You'll see two lines if it is running: one for Firefox and one for your search).

Then

$ killall firefox

which tries to end the process gracefully, or 

$ killall -KILL firefox

which unconditionally clobbers it.

---

### Post by iggy pop on 2010-03-20
Went along to System Monitor -> Process Tab and Firefox was not listed. So i opened a terminal and typed: $ ps -ef | grep firefox and got the following output:

iggy@iggy-desktop:~$ ps -ef | grep firefox
iggy 2809 2788 0 09:17 pts/0 00:00:00 grep --color=auto firefox
iggy@iggy-desktop:~$

---

### Post by r-senior on 2010-03-20
It's not running then. The line that refers to "grep" on the process listing is your process that's doing the search. If Firefox was running, you'd get two lines:

```

username  28561  1666 14 08:53 ?        00:06:59 /usr/lib/firefox-3.5.8/firefox
username  29192 29117  0 09:40 pts/0    00:00:00 grep --color=auto firefox

```

So it's not running. Do you get any error messages when you type "firefox" in a console?

Have you done anything immediately prior?

Is it still installed?

$ which firefox

Should return /usr/bin/firefox.

---

### Post by iggy pop on 2010-03-20
I opened a terminal and typed: firefox and got the following output: 

iggy@iggy-desktop:~$

(firefox: 3092): GLib-WARNING **: g_set_prgname() called multiple times
iggy@iggy-desktop:~$

Firefox is still installed on my computer. Would it help if i was to un-install and then re-install it?

---

### Post by r-senior on 2010-03-20
I don't think that message you get is an error. Reinstalling shouldn't do any harm:

$ sudo apt-get install --reinstall firefox

---

### Post by iggy pop on 2010-03-20
A stupid question i know but if i was to use the code you provided: $ sudo apt-get install --reinstall firefox it wouldn't leave me with two separate Firefox installs? Thanks for all the help r-senior

---

### Post by r-senior on 2010-03-20
It won't leave you with two installs of Firefox. It will just reinstall Firefox using the latest version from the repository.

You should really precede the command I gave with an "apt-get update" to make sure your view of the repository is up to date:

$ sudo apt-get update
$ sudo apt-get install --reinstall firefox

You can do the same with the Synaptic program of course. Find Firefox and you can mark for reinstallation by clicking the little green box and picking from the menu.

If you are doing this, it might be worth looking in the bottom left corner of Synaptic for the check for broken packages?

---

### Post by iggy pop on 2010-03-20
Have un-installed Firefox, updated Synaptic and then re-installed Firefox but i still can't get it to run?

---

### Post by r-senior on 2010-03-20
I'm running out of suggestions ...

Do you keep your system up to date with Update Manager? Have you tried rebooting? What version of Ubuntu are you running?

Anything unusual in the logs?

$ tail /var/log/syslog
$ tail /var/log/messages

Did Synaptic report any broken packages?

---

### Post by iggy pop on 2010-03-20
I am running Ubuntu 9.10 and i have used the Update Manager to check for updates this morning.

iggy@iggy-desktop:~$ tail /var/log/syslog
Mar 20 12:38:49 iggy-desktop console-kit-daemon[746]: WARNING: Couldn't read /proc/1552/environ: Failed to open file '/proc/1552/environ': No such file or directory
Mar 20 12:38:49 iggy-desktop kernel: [ 1709.319038] mtrr: no MTRR for d8000000,4000000 found
Mar 20 12:38:50 iggy-desktop acpid: client 929[0:0] has disconnected
Mar 20 12:38:50 iggy-desktop acpid: client connected from 2228[0:0]
Mar 20 12:38:50 iggy-desktop kernel: [ 1709.677445] [drm] Setting GART location based on new memory map
Mar 20 12:38:50 iggy-desktop kernel: [ 1709.678521] [drm] Loading R300 Microcode
Mar 20 12:38:50 iggy-desktop kernel: [ 1709.678543] [drm] Num pipes: 4
Mar 20 12:38:50 iggy-desktop kernel: [ 1709.678550] [drm] writeback test succeeded in 1 usecs
Mar 20 12:39:04 iggy-desktop init: tty2 main process ended, respawning
Mar 20 12:39:29 iggy-desktop pulseaudio[2378]: pid.c: Stale PID file, overwriting.
iggy@iggy-desktop:~$


iggy@iggy-desktop:~$ tail /var/log/messages
Mar 20 12:10:33 iggy-desktop kernel: [   13.018869] [drm] Loading R300 Microcode
Mar 20 12:10:33 iggy-desktop kernel: [   13.018891] [drm] Num pipes: 4
Mar 20 12:10:33 iggy-desktop kernel: [   13.018899] [drm] writeback test succeeded in 1 usecs
Mar 20 12:11:34 iggy-desktop kernel: [   74.140042] Clocksource tsc unstable (delta = -161809241 ns)
Mar 20 12:38:49 iggy-desktop kernel: [ 1709.220754] [drm] Num pipes: 4
Mar 20 12:38:50 iggy-desktop kernel: [ 1709.677445] [drm] Setting GART location based on new memory map
Mar 20 12:38:50 iggy-desktop kernel: [ 1709.678521] [drm] Loading R300 Microcode
Mar 20 12:38:50 iggy-desktop kernel: [ 1709.678543] [drm] Num pipes: 4
Mar 20 12:38:50 iggy-desktop kernel: [ 1709.678550] [drm] writeback test succeeded in 1 usecs
Mar 20 12:39:29 iggy-desktop pulseaudio[2378]: pid.c: Stale PID file, overwriting.
iggy@iggy-desktop:~$

---

### Post by r-senior on 2010-03-20
OK, a couple more things to try ...

$ firefox -safe-mode

This disables any extensions or themes, in case they are the cause of the problem.

$ firefox -jsconsole

This is supposed to open an error window that shows problems.

---

### Post by iggy pop on 2010-03-20
Success!

I typed $ firefox -safe-mode

A pop-up box appeared and there were a few options to choose from. So i choose to disable all add-ons and restart Firefox and it worked.

Suppose i will have reconfigure Firefox but that's the least of my worries.

Real big thanks for all the help.

---

### Post by lovinglinux on 2010-03-20
> **iggy pop said:**
> Success!

I typed $ firefox -safe-mode

A pop-up box appeared and there were a few options to choose from. So i choose to disable all add-ons and restart Firefox and it worked.

Suppose i will have reconfigure Firefox but that's the least of my worries.

Real big thanks for all the help.

If you have Prism installed, remove it and it should fix the problem. It is causing this problem, at least with Firefox 3.6. Nevertheless, it could be another extension.

For future reference see the [COLOR="Sienna"]**troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

