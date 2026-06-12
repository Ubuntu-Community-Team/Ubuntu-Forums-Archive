---
title: "How to kill this service POLKITD?"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by vasiauvi on 2010-04-30
Hello,
Some days ago I've updated to Ubuntu Lucid and I had this [bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/569711") and unfortunately I don't know how to resolve it! 

I have this service POLKITD started with the system. It's consuming a lot of memory as long it is running (less after 30 minutes, >400MB after 1 hour) also the CPU is staying at 50% all the time, and even more.
I don't know what this service do (although [here]("http://manpages.ubuntu.com/manpages/lucid/en/man8/polkitd.8.html") it's saying what polkitd is).

I've tried 
```
start-stop-daemon -K -n polkit
update-rc.d -f polkitd remove
```
but after boot is still appearing!

Now, as I write this my system is running for 1h 30 min and polkit is 500MB of RAM.

My question is: HOW to stop/kill/murder:) this service???!

Thank you!

---

### Post by _0R10N on 2010-04-30
Check [http://ubuntuforums.org/showthread.php?t=1450707]("http://ubuntuforums.org/showthread.php?t=1450707")
You can also install rcconf and check whether is there another application related polkitd starting up.

---

### Post by Paqman on 2010-04-30
I don't really have any idea how to tackle your bug, but killing the PolicyKit daemon would be a bad idea. It's a pretty important part of the system, it's involved with privileges and security on the system.

---

### Post by vasiauvi on 2010-04-30
Hello _0R10N,
I've read that thread, thanks, I didn't knew about it!
But I still don't know what is causing the polkitd service to open on boot....
I would like to investigate further but I don't know what to do!

Any idea?
Thanks!

---

### Post by vasiauvi on 2010-04-30
Paqman,
Hmmm...but how can I remove it?
In 9.10 was not behaving like this...
Now I'm berelly can write on this threat. The RAM is full and the swap is 250MB.
The idea is that this service is increasing the memory usage every hour!
Hope to resolve this issue

---

### Post by Paqman on 2010-04-30
> **vasiauvi said:**
> 
Hmmm...but how can I remove it?


I don't think the solution to your bug is going to be removing parts of PolicyKit.

Have you tried creating a fresh account and seeing if the problem is the same?

---

### Post by vasiauvi on 2010-04-30
Jusy now I've created a new account and the CPU is at the same level because of the polkitd service (50%).
What could I do?

[EDIT]
I've restarted Ubuntu Lucid with my usual user and opened only htop.
polkitd had only some MB. I've gone out in the city and after 1h30min polkitd used 500MB.

This is not called memory leak?

---

### Post by vasiauvi on 2010-04-30
Sorry that I'm putting so quickly an other replay but I just want to share the htop output:

---

### Post by jrothwell97 on 2010-04-30
I wouldn't call this a bug.

It's a common fallacy that full RAM is bad - on the contrary, if only a little bit of RAM is being used, then you're wasting power on the remaining empty RAM.

Presuming polkitd's not actually affecting your computer's performance (swapping to the hard disk is fine, it's *designed* to do that) leaving everything as-is is just fine. Don't panic. :D

---

### Post by vasiauvi on 2010-04-30
Yes, but is not normal a script, just a little script to use all the RAM (here allmost 1GB). 
In my case polkitd is definitively affecting my computer performance!After an 1 hour or 2 the system is very very slow, I can say unusable!
Just some minutes ago I've restarted my computer because it was extremelly heavy.

A Linux system should run days without restarting!No?
This bug (in my opinion is a bug :) ) is a major one when because of it you can't use your system!

---

### Post by vasiauvi on 2010-05-01
> **Paqman said:**
> I don't think the solution to your bug is going to be removing parts of PolicyKit.


OK, but if I want to remove it how could I do this? It's seems that this program/script/daemon whatever, is "hard to kill".
I've installed policykit-gnome just to remove it afterward with hope that will remove all the polkit files. 
It didn't worked!

It's hard to believe that I'm the only one with this problem. Whit every minute this program is taking much memory...It's like a black hole for RAM.

---

### Post by Paqman on 2010-05-01
> **vasiauvi said:**
> OK, but if I want to remove it how could I do this? It's seems that this program/script/daemon whatever, is "hard to kill".


That's because removing it will break your system.

When it's eaten up a lot of your RAM, can you run the command:
```
free -m
```

and post the output here please?

---

### Post by vasiauvi on 2010-05-01
> **Paqman said:**
> That's because removing it will break your system.

When it's eaten up a lot of your RAM, can you run the command:
```
free -m
```

and post the output here please?

Thanks for helping me!
Now I'm in Windows because in Linux after 2 hour I had to restart...I will enter now in Ubuntu and put the command above!

[EDIT]
This is the output of free-m:
After starting the laptop:
```

vasia@vasia-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           875        847         28          0         67        317
-/+ buffers/cache:        462        413
Swap:         1184          0       1184

```
After starting Firefox:
```

vasia@vasia-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           875        803         72          0         32        147
-/+ buffers/cache:        623        252
Swap:         1184          2       1182

```
I will put after some minutes an other output for free -m command!

---

### Post by vasiauvi on 2010-05-01
This is the output of free -m command after some 20 minutes:
```
             total       used       free     shared    buffers     cached
Mem:           875        827         48          0          3         67
-/+ buffers/cache:        756        119
Swap:         1184         40       1144

```

Below you can see a screenshot of Terminal and Conky where it's seen that polkit has high memory usage. After 1 hour it will be more!

[EDIT]
After an other 15 minutes:
```

             total       used       free     shared    buffers     cached
Mem:           875        853         21          0          4         48
-/+ buffers/cache:        800         74
Swap:         1184        122       1062

```

I have to say that polkitd now is consuming 300MB!!
And also have to say that I don't have nothig open except Firefox and Terminal and I don't even used the system, only let it running!

---

### Post by reinis.zumbergs on 2010-05-01
I have no idea, how this would affect your systems privilage handling, but You could **make the daemon script unexecutable** as I do with another unseparable-and-very-important -part-of-system - gnome-panel.
I wouldnt remove gnome-panel package because that would remove all the dependencies I use - like gnome-session and so on. Also since year or so GNOME decided that gnome-panel is not to be replacable in its session and doesnt abide to gconf /desktop/gnome/session/required_components : panel="my-other-great-panel". And its immediately back after killed.

---

### Post by vasiauvi on 2010-05-02
> **reinis.zumbergs said:**
> I have no idea, how this would affect your systems privilage handling, but You could **make the daemon script unexecutable** as I do with another unseparable-and-very-important -part-of-system - gnome-panel.
I wouldnt remove gnome-panel package because that would remove all the dependencies I use - like gnome-session and so on. Also since year or so GNOME decided that gnome-panel is not to be replacable in its session and doesnt abide to gconf /desktop/gnome/session/required_components : panel="my-other-great-panel". And its immediately back after killed.

Hello,
Thanks for replay!I've selected polkitd service as no executable!
Now the RAM is OK (until now) but both CPUs are high at 50% all the time in idle mode (when no using any program).
The most CPU power is taking by DBUS-DAEMON....

But now I have other issue: all the time, at almost every site I use is telling me "This Connection is Untrusted" and is telling me to get the certificate. But this is happening all the time!

:) It's very frustrating!

---

### Post by MisterLambda on 2010-05-02
Removing PolicyKit general messes up security in execution and websites.

dbus allows processes to talk to other processes: removing it generally ends up even worse.

---

### Post by vasiauvi on 2010-05-02
> **MisterLambda said:**
> Removing PolicyKit general messes up security in execution and websites.

dbus allows processes to talk to other processes: removing it generally ends up even worse.
Hello,
Yes, I've seen that this policykit removal has messed up my security. But what to do??? If I enable it again my system is heavy and must be restarted after 1h30 min, if I let like it is is frustrating and annoying!
.....what to do, what to do??? :(

---

### Post by MisterLambda on 2010-05-02
The only thing I can think of is pretty much reinstalling using the alternate CD. Log in, and you'll end up at a terminal.

You'll then want to ```
sudo apt-get install lxde xorg firefox menu-xdg synaptic

```This is give you an LXDE install. Not as pretty or simple, but should be much faster.

---

### Post by vasiauvi on 2010-05-03
Hello,
Thanks again for the efort of helping me!
I think that I will clean install Ubuntu Lucid or maybe try a different distribution like Mint, Fedora or even Slakware.

I will close this topic!
Thank you again!

---

### Post by duanedesign on 2010-05-03
Here are some bug reports on this issue:

[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/570015](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/570015)
[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/572813](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/572813)

---

### Post by vasiauvi on 2010-05-03
> **duanedesign said:**
> Here are some bug reports on this issue:

[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/570015](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/570015)
[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/572813](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/572813)

Hello,
Yes, the las bugreport was filled by me!
The first I've read it just now but there isn't showed a clear resolvability!
I will try to delete some .* folders and files in my /home directory.

---

### Post by vasiauvi on 2010-05-03
I've deleted some .* folders and files from some applications that I've used before and unistaled and now the system is OK (I hope).

But I think that the problem was .pulse folder from pulse-audio. After deleting this folder my CPU was in the normal state. Looking inside the folder I've seen that were appearing some files and disappearing(like some services) very quickly!

After restarting the PC the CPU is fine and also the memory!

The idea is that the problem on my system was .pulse folder. After deleting this folder and also .dbus folder everything was OK.

Thanks for helping me and hope that this issue will not appear anymore!
After almost a week this problem is solved for me!

I will let the topic open for a day or two to see how my system behave and after that I will mark as SOLVED!

---

### Post by mastapat11 on 2010-05-18
> **vasiauvi said:**
> 
.
.
.

The idea is that the problem on my system was ***_.pulse_*** folder. After deleting this folder and also .dbus folder everything was OK.
.
.
.


[SIZE="3"]this was my exact problem and this issue worked for me as well.
it also fixed my issue w/ PulseAudio not working before (E: module.c: Failed to load module "module-alsa-sink")
[/SIZE]
[SIZE="4"]THANKS!!![/SIZE]  :popcorn:

---

### Post by pritchard92 on 2010-06-07
I would like to add that I too was having this problem - CPU usage would increase and increase with polkitd's memory usage increasing too. A quick google search led me to this thread.

After deleting my .pulse and .dbus folders, as mentioned by vasiauvi, the problem disappeared! This means I can get back to sequentially watching the Star Wars series! Happy days.

---

### Post by Vetal_ca on 2010-09-19
I fixed it differently. 

I allowed updates yesterday. These updates killed my audio, so I needed to recompile ALSA drivers. Non-functional audio made pulse audio to be non-functional too. As result polkitd took 50% (1 core)  of my CPU. Deleting ~/.pulse/* didn't resolve the problem and ~/.pulse recreated. 

I restored my ~/.pulse/daemon.conf and recompiled the ALSA drivers. After the reboot audio went normal and nobody taking my CPU anymore.

Here is an apt.log. Sorry, I'm not experienced enough to pick the package that broke the audio.

> Start-Date: 2010-09-19  01:43:41
Upgrade: linux-image-2.6.32-24-generic (2.6.32-24.42, 2.6.32-24.43), xulrunner-1.9.2 (1.9.2.9+build1+nobinonly-0ubuntu0.10.04.1, 1.9.2.10+build1+nobinonly-0ubuntu0.10.04.1), linux-headers-2.6.32-24 (2.6.32-24.42, 2.6.32-24.43), smbclient (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), hpijs (3.10.2-2ubuntu2, 3.10.2-2ubuntu2.1), apt-transport-https (0.7.25.3ubuntu9.1, 0.7.25.3ubuntu9.3), hplip (3.10.2-2ubuntu2, 3.10.2-2ubuntu2.1), linux-libc-dev (2.6.32-24.42, 2.6.32-24.43), libsmbclient (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), apt-utils (0.7.25.3ubuntu9.1, 0.7.25.3ubuntu9.3), apt (0.7.25.3ubuntu9.1, 0.7.25.3ubuntu9.3), firefox (3.6.9+build1+nobinonly-0ubuntu0.10.04.1, 3.6.10+build1+nobinonly-0ubuntu0.10.04.1), samba-common-bin (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), libhpmud0 (3.10.2-2ubuntu2, 3.10.2-2ubuntu2.1), linux-headers-2.6.32-24-generic (2.6.32-24.42, 2.6.32-24.43), firefox-gnome-support (3.6.9+build1+nobinonly-0ubuntu0.10.04.1, 3.6.10+build1+nobinonly-0ubuntu0.10.04.1), samba (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), libwbclient0 (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), samba-common (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), firefox-branding (3.6.9+build1+nobinonly-0ubuntu0.10.04.1, 3.6.10+build1+nobinonly-0ubuntu0.10.04.1), winbind (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), libpam-smbpass (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), ureadahead (0.100.0-4.1.2, 0.100.0-4.1.3), gzip (1.3.12-9ubuntu1, 1.3.12-9ubuntu1.1), hplip-data (3.10.2-2ubuntu2, 3.10.2-2ubuntu2.1)
End-Date: 2010-09-19  01:52:19

---

### Post by sberla54 on 2010-09-20
>  The idea is that the problem on my system was .pulse folder. After deleting this folder and also .dbus folder everything was OK.
Thank you dude!
I've had the same problem and fixed it using your tip! :)
I confirm it worked well for me!

---

### Post by CarlesOriol on 2010-10-20
removing .pulse worked for me too. Thanks.

---

### Post by basich on 2011-02-10
something renamed /etc/pulse/default.pa to /etc/pulse/default.pa.old.0

renamed this back and rebooted and all works

---

