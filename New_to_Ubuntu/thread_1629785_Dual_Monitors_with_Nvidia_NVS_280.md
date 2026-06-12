---
title: "Dual Monitors with Nvidia NVS 280"
date: 2010-11-24
forum: New to Ubuntu
---

### Post by Chrissd on 2010-11-24
Hi,

I've got a Dell which uses "low profile" PCI cards, and bought the only "low profile" graphics card I could find. According to NVidia, which has more information on it than I know it says
```

04:02.0 VGA compatible controller: nVidia Corporation NV34GL [Quadro NVS 280 PCI] (rev a1)

```

It uses nvidia-settings to setup the monitors, and the monitor on the left works fine, with the right resolution, but the one on the right seems to think it can only use 640x480 as a screen resolution.

In xrandr I think it thinks there is just one monitor, so I've no clue where to start to try and fix this. I want the right hand screen to have the screen resolution of 1024x768.

Output of xrandr
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 2080 x 900, maximum 2464 x 900
default connected 2080x900+0+0 0mm x 0mm
   2464x768       50.0     51.0  
   1664x768       51.0  
   2080x900       50.0     51.0* 
   2048x768       50.0  
   2048x900       51.0  
   1024x768_50.00   50.0  
  1440x900_59.90 (0x19c)  106.3MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock   55.8KHz
        v: height  900 start  901 end  904 total  932           clock   59.9Hz

```

Really appreciate any help that anyone can give me. I used to have it working, but when I upgraded the hard drive, had to start again, and I've no idea how I got it working?

---

### Post by Chrissd on 2010-11-24
Well, somehow, I fixed this myself, but I certainly have no idea what I changed to fix it.

Mystery over until next time.

---

