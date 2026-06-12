---
title: "Errors when booting"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by Bv202 on 2010-10-12
Hey,

I finally managed to install Ubuntu as a dual-boot with Windows 7. I'm using the 32-bit version as the 64-bit one failed.

However, I still got some problems with it. A few minor ones, so let's list these fist:
- No auto-connect to my wireless. Is this possible?
- On every reboot, my screen brightness is at max again. Really annoying, as I'm always working on the darkest setting.

Other than this, I have a big problem: 3 fatal errors on boot. After a few seconds, my system boots and everything seems to work, but it doesn't sound good anyway. It goes too fast to write them down - can I find them in some log file so I can post them?

Thank you

---

### Post by ft-Orchard on 2010-10-12
The auto-connect, did u save the password for the wireless network? 
Right click on the network-applet icon on the panel, click "Edit connections" and go to "wireless".
Click "edit" for your wifi network and make sure "connect automatically is checked. 

For the brightness settings, go to "preferences > power management". You can set your brightness there. If it is not saved on boot, it must be a bug. You can add bugs here: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by ft-Orchard on 2010-10-12
Can u paste your boot logfile? 
**/var/log/boot**

---

### Post by Bv202 on 2010-10-12
Hey,

Thank you - wireless and brightness works now :)

Boot log: "nothing has been logged yet" :s

---

### Post by ft-Orchard on 2010-10-12
What kind of errors are these than? Do you have them written down? 

You can check your logfiles with: "administration > log file viewer"
Or, check the directory "/var/log". You can see boot.log there.

Maybe you are talking about "/var/log/dmesg"?

---

### Post by Bv202 on 2010-10-12
First I get two errors: "Fatal error: File x missing". (x = file I didn't manage to write down)

This stays for a few seconds, but it boots too fast to write them down. After a few seconds, a third error appears for a second or so, then it boots. This third error has to do with my CPU, but I can't read it that fast...

It doesn't seem to get logged:(

---

### Post by ft-Orchard on 2010-10-12
if you run:
```

dmesg | grep Fatal 

```

do you get any results?

---

### Post by Bv202 on 2010-10-12
Nope. In the terminal, right?

I've enabled boot logging (there was a file where you can enable that). This is the output:

> 'fsck' uit util-linux-ng 2.17.2

/dev/sda4: schoon, 144756/3276800 bestanden, 2108383/13106944 blokken

 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox


[74G[ OK ]

 * Setting sensors limits       [80G 
[74G[ OK ]

speech-dispatcher disabled; edit /etc/default/speech-dispatcher

 * Starting the Winbind daemon winbind       [80G 
[74G[ OK ]

 [33m*[39;49m PulseAudio configured for per-user sessions

saned disabled; edit /etc/default/saned

 * Enabling additional executable binary formats binfmt-support       [80G 
[74G[ OK ]

 * Checking battery state...       [80G 


Nothing interesting... doesn't list the errors or something.

---

### Post by ft-Orchard on 2010-10-12
Well, the error is not logged in /var/log (try: cat * | grep Fatal)
Then I'm out of options. Sorry.

---

### Post by Bv202 on 2010-10-12
> **ft-Orchard said:**
> Well, the error is not logged in /var/log (try: cat * | grep Fatal)
Then I'm out of options. Sorry.

With that command, I'm only getting some folders as the output:(

Thanks for the help anyway.

---

### Post by Bv202 on 2010-10-13
Hey,

This is the error I'm getting (I'm only getting it twice, not 7-8 times). Only the version number may differ:
[http://kerneltrap.org/node/13918](http://kerneltrap.org/node/13918)

Any idea how I can solve this?

EDIT:
The file "modules.dep" exists btw.

---

