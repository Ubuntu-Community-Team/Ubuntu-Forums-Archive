---
title: "to be switched off automatically"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by fewer106 on 2009-04-21
I've created a common folder for my small network with Win xp home under Ubuntu 8.10 Everything is fine, **but** users forget to switch this computer off. How can I fix the problem? The computer has to be switched off automatically in certain time, after 7 p.m.

I suppose there should be a small script,
smthg like 'halt now...' or what, but what should be written there and where should I put it?

---

### Post by 3rdalbum on 2009-04-21
You can set what they call a "cron job". Cron is a program that keeps running all the time and checks to see if there are any commands scheduled to be run at a particular time.

The program "gcrontab" which is available from the repositories, will help you set a Cron job that will run at whatever time you want, every night.

---

### Post by aeiah on 2009-04-21
and the command you want to issue is:
```
sudo shutdown -h now
```

or indeed ```
sudo shutdown -h 19:00
``` to shutdown at 7pm. the latter can be issued at any time, the former needs to be issued at 7pm, obviously.

---

### Post by mikechant on 2009-04-21
In case someone is still logged on, it's more friendly to run something like this:

```
shutdown -h +3 System shutdown in 3 minutes, please log out now 
```

E.g. You could schedule this for 18:57 and it will give a 3 minute warning and then shut down at 19:00

This also has the advantage that if you were doing something on the machine at this time and didn't want it to shut down, you would have three minutes to type
```
shutdown -c
```
to cancel the shutdown

HOWEVER: I've just realized that I've never tried a deferred shutdown with message when using a gui, so it's occurred to me that I don't know if or how the message will appear for gui users. Can't try it at present since I haven't got access to my Ubuntu PC.

---

### Post by fewer106 on 2009-04-21
the problem is that i should be rootand it requests the root pasword.
I made 
switching of the computer by BIOS 
&
shutting down in System->Sessions->Startup Programs->add 
and placed command 

sudo shutdown -h 19:00

BUT it doesn't work..I suppose it's just because root password is required
is it possible to make it work this way? or may be any other suggestions?

---

### Post by Paqman on 2009-04-21
Check your BIOS, too. Some of them contain auto power on/off schedules.

---

### Post by MrWES on 2009-04-21
> **fewer106 said:**
> the problem is that i should be rootand it requests the root pasword.
I made 
switching of the computer by BIOS 
&
shutting down in System->Sessions->Startup Programs->add 
and placed command 

sudo shutdown -h 19:00

BUT it doesn't work..I suppose it's just because root password is required
is it possible to make it work this way? or may be any other suggestions?

From a terminal type:
```
sudo crontab -e
```

That is for cron jobs that require root permissions to run. Add the following line:
```
57 18 * * * shutdown -h +3 System shutdown in 3 minutes, please log out now
```
Save the file and exit. That will run everyday at 18:57 without prompting for a password.

Bill

---

### Post by fewer106 on 2009-04-22
I tried it but nothing happened

[B]kama@gate:~$ sudo crontab -e
no crontab for root - using an empty one
crontab: installing new crontab
root@gate:~# cron
cron: can't lock /var/run/crond.pid, otherpid may be 5236: Resource temporarily unavailable[/B]

however

[B]root@gate:~# crontab -l
# m h  dom mon dow   command
51 8 * * * halt now[/B]

I desided to use **halt** command instead of **shutdown**, because it completly switches the computer off and shutdown switches on rescue menu in the end

I have two ubuntu workstations and noone reacts properly on cron job... may be I should install some packets for it..

---

### Post by kpkeerthi on 2009-04-22
Can you be more specific as to what you mean by "not reacting propertly"? 

I would use absolute paths when referring to binaries/executables in crontab:
```

0 1 * * *  [COLOR="Red"]**/sbin/**[/COLOR]shutdown -h now

```

---

### Post by fewer106 on 2009-04-22
so I tried
```
[COLOR="Red"]/sbin/[/COLOR]halt now
```
nothing again
I mean that no reaction at all, it goes on working...

may be I should reboot or what?

I don't seem to do smthng wrong may be I don't do smthng?

---

### Post by mister_p_1998 on 2009-04-22
I just do
sudo Gedit /etc/crontab
and enter this line(s)



# Shutdown Weekdays Monday - Thursday
29 16 * * 1-4 root /sbin/shutdown -h now

# Shutdown Tuesday Lunch
00 11 * * 2 root /sbin/shutdown -h now

# Shutdown Wednesday Lunch
00 12 * * 3 root /sbin/shutdown -h now

# Shutdown Thursday Lunch
55 11 * * 4 root /sbin/shutdown -h now

# Shutdown Friday
58 15 * * 5   root /sbin/shutdown -h now

# Shutdown Weekends
30 10 * * 6,7 root /sbin/shutdown -h now

works for me...

Steve

---

### Post by fewer106 on 2009-04-22
and for me 2 Thanks!!!! everything's fine :guitar:

---

