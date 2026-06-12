---
title: "dev/lirc0 not created on startup"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by Rayn on 2009-06-08
I just upgraded from Gutsy, where my MythTV setup was working, to Hardy because I needed to install a new package. 

Big mistake for me as I've had a lot of problems.

A big problem for me is lirc no longer works and I don't know where to start in the troubleshooting.  I got things going last night by creating the device on channel 61 (??) after googling for hours and just trying everything.

So I rebooted hoping everything would work again.  No dice. 
This is the information I can give you, I would really appreciate any help anyone can offer.

I'm using a Hauppage 250 PVR
Everything was working before but I think the upgrade changed some of my files.

dmesg | grep lirc
returns nothing.

/etc/lirc/hardware.conf
> REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc/0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

 cat lircd.conf
> begin remote
  name            hauppauge_pvr
  bits            13
  flags           RC5|CONST_LENGTH
  eps             30
  aeps            100
  one             969   811
  zero            969   811
  gap             114605
  toggle_bit      2
  plead           1097

  begin codes
       Power           0x00000000000017FD
       Go              0x00000000000017FB
       1               0x00000000000017C1
       2               0x00000000000017C2
       3               0x00000000000017C3
       4               0x00000000000017C4
       5               0x00000000000017C5
       6               0x00000000000017C6
       7               0x00000000000017C7
       8               0x00000000000017C8
       9               0x00000000000017C9
       Back/Exit       0x00000000000017DF
       0               0x00000000000017C0
       Menu            0x00000000000017CD
       Red             0x00000000000017CB
       Green           0x00000000000017EE
       Yellow          0x00000000000017F8
       Blue            0x00000000000017E9
       Ch+             0x00000000000017E0
       Ch-             0x00000000000017E1
       Vol-            0x00000000000017D1
       Vol+            0x00000000000017D0
       Ok              0x00000000000017E5
       Mute            0x00000000000017CF
       Blank           0x00000000000017CC
       Full            0x00000000000017FC
       Rewind          0x00000000000017F2
       Play            0x00000000000017F5
       Forward         0x00000000000017F4
       Record          0x00000000000017F7
       Stop            0x00000000000017F6
       Pause           0x00000000000017F0
       Replay          0x00000000000017E4
       Skip            0x00000000000017DE

  end codes

end remote

cat lircmd.conf
> #UNCONFIGURED
#
# To find out how to get a proper configuration file please read:
#
#       /usr/share/doc/lirc/README.Debian

 ls -al /dev/lirc*
(the link to lirc0 is in red)
> lrwxrwxrwx 1 root root 10 2009-06-08 22:56 /dev/lirc -> /dev/lirc0
srw-rw-rw- 1 root root  0 2009-06-08 22:56 /dev/lircd

 /etc/init.d/lirc start
> Starting lirc daemon: lircd lircmdlircmd: could not connect to socket
lircmd: Connection refused
.

> root@myth:/etc/lirc# irw
connect: Connection refused

I replace /etc/init.d/lirc with /etc/init.d/lirc.dpk-dist
and rm /dev/lirc

so then I tried this:
> root@myth:/etc/init.d# ./lirc start
 * Starting remote control daemon(s) : LIRC                              [ OK ]
root@myth:/etc/init.d# ./lirc start
 * Starting remote control daemon(s) : LIRC                              [fail]


> root@myth:/etc/init.d# irw
root@myth:/etc/init.d# irw
connect: Connection refused


> root@myth:/etc/init.d# ls /dev/lir*
/dev/lircd

so I tried following information in this thread:
[http://ubuntuforums.org/showthread.php?t=767597&page=4](http://ubuntuforums.org/showthread.php?t=767597&page=4)

> root@myth:/etc/udev/rules.d# /etc/init.d/lirc start
 * Loading LIRC modules                                                  [ OK ]
 * Starting remote control daemon(s) : LIRC                              [fail]
root@myth:/etc/udev/rules.d# lsmod | grep -i lirc
lirc_i2c               11140  0
lirc_dev               15732  1 lirc_i2c
i2c_core               24832  18 cx88xx,bttv,lirc_i2c,msp3400,saa7115,wm8775,cx25840,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,ivtv,nvidia,i2c_algo_bit,tveeprom,i2c_nforce2


Can someone point me in the right direction as to what I should try to do next?  I've been at this for hours but I think I may be making it worse.

---

### Post by Rayn on 2009-06-09
Well, I rebooted cold.

(it takes me 4 minutes to start up for some reason, that's another thread)

I have some progress but no remote activity.

> root@myth:/var/log/mythtv# ls -al /dev/lirc*
lrwxrwxrwx 1 root root    10 2009-06-08 23:56 /dev/lirc -> /dev/lirc0
crw-rw---- 1 root root 61, 0 2009-06-08 23:56 /dev/lirc0
srw-rw-rw- 1 root root     0 2009-06-09 00:02 /dev/lircd

> root@myth:/var/log/mythtv# irw
connect: Connection refused

> root@myth:/var/log/mythtv# /etc/init.d/lirc start
 * Loading LIRC modules                                                                                               [ OK ]
 * Starting remote control daemon(s) : LIRC                                                                           [ OK ]

root@myth:/var/log/mythtv# ps aux | grep lirc
root      7910  0.0  0.0      0     0 ?        S    Jun08   0:00 [lirc_dev]
root      8871  0.0  0.0   2932   496 ?        Ss   00:06   0:00 /usr/sbin/lircd --device=/dev/lirc/0
root      8876  0.0  0.0   3004   748 pts/0    R+   00:06   0:00 grep lirc

so I changed hardware.conf to use the device /dev/lirc0

I think it's working now

for the life of me I have no idea what I changed :(

maybe this helps someone else though.

---

