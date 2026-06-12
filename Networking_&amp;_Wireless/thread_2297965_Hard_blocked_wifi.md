---
title: "Hard blocked wifi"
date: 2015-10-08
forum: Networking &amp; Wireless
---

### Post by zachopih on 2015-10-08
Hello. I have installed Linux and when I do sudo rfkill list, my wireless lan is hard blocked. My wireless icon is white which means it's on, and I've tried sudo mod probe -r acer-wmi and it just changed it from off to hardware disabled.. Help please

---

### Post by tgalati4 on 2015-10-08
Welcome to the forums.  Do you have a small wifi switch on the front or side of the laptop?  Check that wifi is activated in BIOS.  Open a terminal and post the output of:

```
lsmod | grep Network
```

You have a few switches to play with for the *acer-wmi* module:

> parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)


---

