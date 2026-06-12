---
title: "Streamzap Remote IR Transmitter"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by CSharpe67 on 2011-01-27
Hi All,

I just bought a Streamzap remote with a Streamzap IR transmitter (model USBIR2) to use with mythbuntu 10.10

I have selected Streamzap PC remote for the remote control and for the  IR Transmitter:

I first selected the **SB-UIRT2: Scientific Atlanta Cable** but it skipped menu options with both the up and down arrows so I changed it to  **SB-UIRT2: Pioneer Cable box.  **Same problem.  Then I selected **none.**  Same problem.  I am guessing that the issue is the button mapping for the Streamzap remote.  Upon looking at other post I found that I should include the /etc/lirc/lircd.conf

```

#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Streamzap PC Remote remote:
include "/usr/share/lirc/remotes/streamzap/lircd.conf.streamzap"

```the /usr/share/lirc/remotes/streamzap/lircd.conf.streamzap

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

  one           889  889
  zero          889  889
  plead         889
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
Any ideas as to why it skips menu items?

Thanks in advance for any help or suggestions.

---

### Post by whosmatt on 2011-01-28
Mine is doing this too... upgraded from mythbuntu 10.04 to 10.10 last night.  The channel up/down buttons don't skip menu items.

I've also notice that the left/right buttons don't seem to work anymore either.

-Matt

---

### Post by CSharpe67 on 2011-01-29
I was searching and this looks like a confirmed bug 

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663651](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663651)


possible workarounds

[http://wiki.xbmc.org/index.php?title=Streamzap_PC_Remote#Remote_Button_Configuration](http://wiki.xbmc.org/index.php?title=Streamzap_PC_Remote#Remote_Button_Configuration)

---

### Post by CSharpe67 on 2011-01-29
**[SIZE=3][B]Using option 1 worked for Mthtv**[/SIZE]
  [/B]

**Option 1: Disable Streamzap Xinput Device usign Xorg Configuration **

 The correct way to disable Xinput device on Xorg 1.8 and higher is to  use one or more of Match* statement and "Option Ignore" in an "Input  Class" Section. 
The following configuration block needs to to be added to xorg configuration. 
 Section "InputClass"
  Identifier "Ignore Streamzap IR"
  MatchProduct "Streamzap"
  MatchIsKeyboard "true"
  Option "Ignore" "true"
EndSection
There are two ways to do it: 
 
[LIST]
[*] **Recommended:** add a 90-streamzap.conf file to a xorg.conf.d directory
[*] add the configuration directly to /etx/X11/xorg.conf
[/LIST]
 **  xorg.conf.d locations **

 xorg.conf.d location may vary on your system. 
 
[LIST]
[*] Ubuntu 10.10 (Maverick Meerkat): /usr/share/X11/xorg.conf.d
[*] Ubuntu 10.04 (Lucid Lynx): /usr/lib/X11/xorg.conf.d
[*] ArchLinux: /etc/X11/xorg.conf.d/
[/LIST]
 So on Ubuntu 10.10 (Maverick Meerkat) run the following command and paste the configuration into the file. 
 sudo nano -w /usr/share/X11/xorg.conf.d/90-streamzap.conf

---

