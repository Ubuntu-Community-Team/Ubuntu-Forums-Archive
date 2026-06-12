---
title: "how can i manually edit my monitor's screen resolution?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by hanzj on 2010-05-25
how can i manually edit my monitor's screen resolution?
I ask because System//Preferences/Monitor doesn't have the right resolution. 8-(

---

### Post by -humanaut- on 2010-05-25
What type of video card are you using?

---

### Post by hanzj on 2010-05-25
How can i find the answer via terminal?

---

### Post by -humanaut- on 2010-05-25
lspci

---

### Post by hanzj on 2010-05-26
lspci
> 
0:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
05:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]
05:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)] (Secondary)


---

### Post by hanzj on 2010-05-26
well, i did a fresh-install of ubuntu 9.10  to see if that would solve the problem. It didn't.

I then switched around the 2 monitor cables at the back of my computer. that worked.

Here's the .config/monitors.xml when things are working.

> 
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="DVI-0">
          <vendor>SAM</vendor>
          <product>0x413b</product>
          <serial>0x50473139</serial>
          <width>1280</width>
          <height>960</height>
          <rate>60</rate>
          <x>1024</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="S-video">
      </output>
      <output name="DVI-1">
          <vendor>AOC</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1280</width>
          <height>960</height>
          <rate>60</rate>
          <x>0</x>
          <y>192</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="DVI-0">
          <vendor>SAM</vendor>
          <product>0x413b</product>
          <serial>0x50473139</serial>
          <width>1280</width>
          <height>960</height>
          <rate>60</rate>
          <x>1360</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="S-video">
      </output>
      <output name="DVI-1">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1360</width>
          <height>768</height>
          <rate>60</rate>
          <x>0</x>
          <y>192</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="DVI-0">
          <vendor>AOC</vendor>
          <product>0xa990</product>
          <serial>0x00009552</serial>
          <width>1280</width>
          <height>960</height>
          <rate>85</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="S-video">
      </output>
      <output name="DVI-1">
          <vendor>SAM</vendor>
          <product>0x413b</product>
          <serial>0x50473139</serial>
          <width>1280</width>
          <height>960</height>
          <rate>60</rate>
          <x>1280</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
  </configuration>
</monitors>

---

