---
title: "Remote control in ubuntu"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Archer Troy on 2009-02-09
hey guys, So i just bought the streamzap remote. Even though it was supposed to configure itself to LIRC automatically it didnt. So i input the lirc.conf file i found on the lirc website.

lirc.conf
```
#
# this config file was automatically generated
# using lirc-0.7.1-CVS(serial) on Fri Feb  4 23:20:56 2005
#
# contributed by Christoph Bartelmus
#
# brand:                       Streamzap
# model no. of remote control: PC Remote
# devices being controlled by this remote: USB receiver
#

begin remote

  name  Streamzap_PC_Remote
  bits            6
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           907   804
  zero          907   804
  plead         949
  pre_data_bits   8
  pre_data       0xA3
  gap          108344
  toggle_bit      2


      begin codes
          0                        0x00
          1                        0x01
          2                        0x02
          3                        0x03
          4                        0x04
          5                        0x05
          6                        0x06
          7                        0x07
          8                        0x08
          9                        0x09
          POWER                    0x0A
          MUTE                     0x0B
          CH_UP                    0x0C
          VOL_UP                   0x0D
          CH_DOWN                  0x0E
          VOL_DOWN                 0x0F
          UP                       0x10
          LEFT                     0x11
          OK                       0x12
          RIGHT                    0x13
          DOWN                     0x14
          MENU                     0x15
          EXIT                     0x16
          PLAY                     0x17
          PAUSE                    0x18
          STOP                     0x19
          |<<                      0x1A
          >>|                      0x1B
          RECORD                   0x1C
          <<                       0x1D
          >>                       0x1E
          RED                      0x20
          GREEN                    0x21
          YELLOW                   0x22
          BLUE                     0x23
      end codes

end remote


```

also it comes with a hardware.conf

hardware.conf
```
REMOTE="Windows Media Center Remotes (old version MicroSoft USB ID)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="Custom"
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
```

this seems wrong as it says its using mce remote...

i cant find anything online about how to fix this...

here is irw
irw
```
romanhtpc@romanhtpc-desktop:~$ irw
00000000000028d0 00 UP Streamzap_PC_Remote
00000000000028d0 01 UP Streamzap_PC_Remote
00000000000028d0 02 UP Streamzap_PC_Remote
00000000000028d0 03 UP Streamzap_PC_Remote
00000000000028d0 04 UP Streamzap_PC_Remote
00000000000028d0 05 UP Streamzap_PC_Remote
00000000000028d0 06 UP Streamzap_PC_Remote
00000000000028d0 07 UP Streamzap_PC_Remote
00000000000028d4 00 DOWN Streamzap_PC_Remote
00000000000028d4 01 DOWN Streamzap_PC_Remote
00000000000028d4 02 DOWN Streamzap_PC_Remote
00000000000028d4 03 DOWN Streamzap_PC_Remote
00000000000028d4 04 DOWN Streamzap_PC_Remote

```
does anyone know how to make this remote work in my mythtv?

---

### Post by Archer Troy on 2009-02-11
any takers?

---

