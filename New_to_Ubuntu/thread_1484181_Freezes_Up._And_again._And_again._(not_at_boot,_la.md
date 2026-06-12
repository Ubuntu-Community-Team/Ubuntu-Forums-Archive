---
title: "Freezes Up. And again. And again. (not at boot, later on)"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by penguinv on 2010-05-15
I have Ubuntu 9.10 on an AMD 32 machine with 1.2G RAM.

It freezes. I've been asking in #ubuntu for weeks but no luck. 

The last 2 times a write from one hard drive to another was being done. This was today.
I'd previously suspected flash but it does not always happen in the browser. When it hangs and it's in a video I get an audio loop. I have been only using chrome and no longer using firefox (based on a suggestion).

Could it be that I have low HD space free? (There is data below.)

Could it be some tsr/init? (what is that called in linux?) (I give data on what is running below.)

Someone said to look at the system log file. (It is below.)

Thank you for helping!


ATTACHED.
3 things here: memory use, what's running now, syslog

tinyogen@tinyogen-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.0G  7.9G  688M  93% /
udev                  597M  276K  596M   1% /dev
none                  597M  872K  596M   1% /dev/shm
none                  597M  200K  596M   1% /var/run
none                  597M     0  597M   0% /var/lock
none                  597M     0  597M   0% /lib/init/rw
/dev/sdb1              38G   35G  2.8G  93% /media/269023B4902388FF


tinyogen@tinyogen-desktop:~$ ps all
F   UID   PID  PPID PRI  NI    VSZ   RSS WCHAN  STAT TTY        TIME COMMAND
0     0   992     1  20   0   1700   548 n_tty_ Ss+  tty4       0:00 /sbin/getty
0     0   999     1  20   0   1700   548 n_tty_ Ss+  tty5       0:00 /sbin/getty
0     0  1006     1  20   0   1700   544 n_tty_ Ss+  tty2       0:00 /sbin/getty
0     0  1007     1  20   0   1700   544 n_tty_ Ss+  tty3       0:00 /sbin/getty
0     0  1009     1  20   0   1700   544 n_tty_ Ss+  tty6       0:00 /sbin/getty
4     0  1325  1303  20   0  40248 31876 poll_s Ss+  tty7      11:39 /usr/bin/X
0     0  1612     1  20   0   1700   544 n_tty_ Ss+  tty1       0:00 /sbin/getty
0  1000  2490  2488  20   0   6184  3452 wait   Ss   pts/1      0:00 bash
0  1000  3382  2490  20   0   2424   824 -      R+   pts/1      0:00 ps all

This is /var/sys/log after it froze and I hardbooted.
----------------------------------------------------
May 15 05:33:36 tinyogen-desktop anacron[1641]: Job `cron.daily' terminated
May 15 05:33:36 tinyogen-desktop anacron[1641]: Normal exit (1 job run)
May 15 06:17:01 tinyogen-desktop CRON[2917]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 15 06:25:01 tinyogen-desktop CRON[2921]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
May 15 06:29:30 tinyogen-desktop pulseaudio[1815]: ratelimit.c: 128 events suppressed
May 15 07:05:30 tinyogen-desktop pulseaudio[1815]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
May 15 07:05:30 tinyogen-desktop pulseaudio[1815]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_via82xx'. Please report this issue to the ALSA developers.
May 15 07:05:30 tinyogen-desktop pulseaudio[1815]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
May 15 07:17:01 tinyogen-desktop CRON[3118]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 15 07:28:46 tinyogen-desktop pulseaudio[1815]: ratelimit.c: 1 events suppressed
May 15 07:29:42 tinyogen-desktop pulseaudio[1815]: ratelimit.c: 1 events suppressed
May 15 07:30:01 tinyogen-desktop CRON[3196]: (root) CMD (start -q anacron || :)
May 15 07:30:01 tinyogen-desktop anacron[3199]: Anacron 2.3 started on 2010-05-15
May 15 07:30:01 tinyogen-desktop anacron[3199]: Normal exit (0 jobs run)

---

### Post by penguinv on 2010-05-16
Please someone help me.

is it the ALSA thing?

I'm stymied.

---

### Post by 4Orbs on 2010-05-16
You might be able to free up some space by entering in a terminal:
```
sudo apt-get clean
```
Your root partition appears to be filled to its limits.

---

### Post by nhasian on 2010-05-16
where's your swap partition?  did you check to see if your computer is overheating?  are the fans RPMs okay?  you can check your voltages, temperatures, and RPMs with the command:

```
sensors
```

you may need to install:

```
sudo apt-get install lm-sensors
```

to configure it to your system run:

```
sudo sensors-detect
```

---

### Post by penguinv on 2010-05-18
> **nhasian said:**
> where's your swap partition?  did you check to see if your computer is overheating?  are the fans RPMs okay?  you can check your voltages, temperatures, and RPMs with the command:

```
sensors
```

you may need to install:

```
sudo apt-get install lm-sensors
```

to configure it to your system run:

```
sudo sensors-detect
```
--- doing the sensors-detect - did not tell me about any missing kernel drivers but did say: Found `Winbond W83697HF/F/HG Super IO Sensors'   Success!   (address 0x295, driver `w83627hf')  but then tinyogen@tinyogen-desktop:~$ sensors said :"No sensors found!  Make sure you loaded all the kernel drivers you need.  Try sensors-detect to find out which these are."  -- So I did it again and checked. Same

I also trashed some movies on the disk and did sudo apt-get clean (doing the command gave me no feedback, just a pause and a new prompt.

Someone in #ubuntu suggested: acpi=off apm=off
I don't know how to do that but I did this.
I found out that ACPI is Advanced Configuration and Power Interface. I went to system> preference> power management> AC and set them both to Never.

I'll give it some days and report back.

And thanks for the hints.

---

### Post by penguinv on 2010-05-21
OK reporting back.

It did it again last night, while youtube played, the usual audio loop.

Here's the report including my 4 line log file...
[http://ubuntu.pastebin.com/dWLKEHjQ](http://ubuntu.pastebin.com/dWLKEHjQ)

I'll copy 4 lines here:

May 21 10:53:52 tinyogen-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="730" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May 21 10:55:30 tinyogen-desktop anacron[1727]: Job `cron.daily' terminated
May 21 10:55:30 tinyogen-desktop anacron[1727]: Normal exit (1 job run)
 

--
To my problem:
"One of these days, and it won't be long,
I'll look at my window any you'll be gone"

---

### Post by gandaran on 2010-05-21
could be the /temp directory runs out of space when you play videos, when you get a freeze just delete all temporary files in /temp, if it resolves then you know that is the problem.

---

### Post by sydbat on 2010-05-21
Can we get your system specs? That might help us help you. Please post the output of```
sudo lshw
```

---

### Post by Total AI on 2010-05-21
*I had the same problem,I was running Ubuntu on a dell with a celeron processor,the processor didn't have enough memory cache to keep the system going,thus,a freeze up*,worth a thought

---

### Post by penguinv on 2010-05-22
*[SIZE="2"]Three posts answered and some documentation provided[/SIZE]*.

> **gandaran]Re: Freezes Up. And again. And again. (not at boot, later on)
could be the /temp directory runs out of space when you play videos, when you get a freeze just delete all temporary files in /temp, if it resolves then you know that is the problem.[/QUOTE]

When I freezes "I cant do anything." That is what I meant by freeze. But temp could be it. What can I do to tell?


* * *


[QUOTE=Total AI]Re: Freezes Up. And again. And again. 
I had the same problem,I was running Ubuntu on a dell with a celeron processor,the processor didn't have enough memory cache to keep the system going,thus,a freeze up,worth a thought[/QUOTE]

df -h (my memory) [http://ubuntu.pastebin.com/9jPcntNF](http://ubuntu.pastebin.com/9jPcntNF)

   I think you mean enough swap space. I thought that would show the swap but it didnt. Swap is around 479. I tried to make it double that but instead it gave me an extra partition of the same value, 481. I have 1.2G of RAM so what you said could be a good call.


* * *


[QUOTE=sydbat said:**
> Can we get your system specs? That might help us help you. Please post the output of```
sudo lshw
```

Here's my **system hardware**: [http://ubuntu.pastebin.com/XmiVaLtB](http://ubuntu.pastebin.com/XmiVaLtB)

 
* * *

And my logfile:  **/var/log/syslog**   tinyogen, AMD, May 2010
[http://ubuntu.pastebin.com/t18B7k0z](http://ubuntu.pastebin.com/t18B7k0z)


And...  I **thank you** so much for participating with me.

---

