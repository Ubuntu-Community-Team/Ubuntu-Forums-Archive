---
title: "lirc is eluding me"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by rmhurt on 2009-02-09
i'm attempting to switch to MythBuntu (Intrepid 8.10) from a 3-year-old ill-maintained Gentoo box i was running Mythtv on.  so far everything has gone fairly smoothly except for getting my IR receiver to recognize my remote control.  i've spent a few days looking over many posts in ubuntuforums and elsewhere and trying many different setups, and i'm now convinced i need help on this.  help!

here's some info for you lirc experts.  as you can see, all of this came with me logged in as root.
```

root@bobuntu:/etc/lirc# apt-cache policy libirman-dev
libirman-dev:
  Installed: 0.4.4-2
  Candidate: 0.4.4-2
  Version table:
 *** 0.4.4-2 0
        500 http://archive.ubuntu.com intrepid/main Packages
        100 /var/lib/dpkg/status

root@bobuntu:/etc/lirc# apt-cache policy lirc
lirc:
  Installed: 0.8.3-0ubuntu2
  Candidate: 0.8.3-0ubuntu2
  Version table:
 *** 0.8.3-0ubuntu2 0
        500 http://archive.ubuntu.com intrepid/universe Packages
        100 /var/lib/dpkg/status
```

if i "cat /dev/ttyS0" and push buttons on my remote i get to see garbage, so i know the connection is there.  i also downloaded and built libirman-0.4.4 so i could test the receiver with test_io, and that also shows the hex version of my remote buttons.  so far so good.  but now i try to run lircd and irw in separate terminal sessions and i have two problems.  one, lircd doesn't seem to want to recognize /etc/lirc/hardware.conf, and two, even when lircd seems to be running okay irw doesn't show anything from my remote.

here are my failed lircd attempts.  all of them start with the "ready" statement, but as soon as i start irw in a different session (noted by "accepted new client"), they all aborted:
```

root@bobuntu:/etc/lirc# lircd -n
lircd-0.8.3[8577]: lircd(userspace) ready
lircd-0.8.3[8577]: accepted new client on /dev/lircd
lircd-0.8.3[8577]: could not get file information for /dev/lirc
lircd-0.8.3[8577]: default_init(): No such file or directory
lircd-0.8.3[8577]: caught signal

root@bobuntu:/etc/lirc# lircd -n -d /dev/ttyS0
lircd-0.8.3[8579]: lircd(userspace) ready
lircd-0.8.3[8579]: accepted new client on /dev/lircd
lircd-0.8.3[8579]: could not get hardware features
lircd-0.8.3[8579]: this device driver does not support the new LIRC interface
lircd-0.8.3[8579]: major number of /dev/ttyS0 is 4
lircd-0.8.3[8579]: LIRC major number is 61
lircd-0.8.3[8579]: check if /dev/ttyS0 is a LIRC device
lircd-0.8.3[8579]: caught signal

root@bobuntu:/etc/lirc# lircd -n --driver="irman"
lircd-0.8.3[8575]: lircd(userspace) ready
lircd-0.8.3[8575]: accepted new client on /dev/lircd
lircd-0.8.3[8575]: readlink() failed for "/dev/lirc"
lircd-0.8.3[8575]: No such file or directory
lircd-0.8.3[8575]: could not create lock files
lircd-0.8.3[8575]: caught signal
```

this one remains running and i can see my remote light blinking when i press buttons, but there is no output by irw and i thought there would be.
```

root@bobuntu:/etc/lirc# lircd -n -d /dev/ttyS0 --driver="irman"
lircd-0.8.3[8572]: lircd(userspace) ready
lircd-0.8.3[8572]: accepted new client on /dev/lircd
```

when i throw /etc/lirc/hardware.conf into the parameter mix, lircd tells me it doesn't like the file.  in fact. it doesn't like every single statement in hardware.conf; i verified that by commenting every line one by one.  but also, why isn't it reading /etc/lirc/hardware.conf by default?  i would expect to see the "error" message every time.
```

root@bobuntu:/home/bob# lircd -n -d /dev/ttyS0 --driver="irman" /etc/lirc/hardware.conf
lircd-0.8.3[10200]: error in configfile line 5
lircd-0.8.3[10200]: reading of config file failed
lircd-0.8.3[10200]: lircd(userspace) ready
```

my /etc/lirc/hardware.conf file:
```

#Chosen Remote Control
REMOTE=""
REMOTE_MODULES=""
REMOTE_DRIVER="irman"
REMOTE_DEVICE="/dev/ttyS0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"
START_LIRCMD=""

# Default configuration files for your hardware if any
LIRCMD_CONF=""

FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

my /etc/lirc/lircd.conf file come directly from my Gentoo box where the IR works, as does the .lircrc file which defines what the remote buttons do.  i moved my Gentoo's .lircrc file to both /root/.lircrc and /home/bob/.lirc/mythtv (bob is the user running mythtv), just as a guess as to where they should go.  but since i can't run lircd directly i have no faith in it running as a daemon.

i'm desperately hoping someone can straighten me out!

---

### Post by llamabr on 2009-02-09
Hi, Bob.  Frankly, this doesn't seem like an absolute beginner question.  Finally time, maybe, to admit that you're no longer a noob, and take this question to the appropriate forum.  Does ubuntuforums have a mythtv thread?

---

### Post by rmhurt on 2009-02-11
point taken.  i'm brand new to ubuntu and went back and forth on where to post this, and probably chose incorrectly.

i read somewhere that lircd works differently with the "-n" parameter than it does when running as a daemon.  i also did a big update of 154 files and when i rebooted, the irw program began to show me my button labels with lircd running as a daemon.  i have no idea what i did...

---

