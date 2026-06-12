---
title: "Wifi won't turn on"
date: 2014-08-02
forum: Networking &amp; Wireless
---

### Post by kira-yamato-2008 on 2014-08-02
I keep getting an error that Wifi is disabled by hardware switch, is there some way to circumvent this?

---

### Post by jeremy31 on 2014-08-02
```
[COLOR=#000000][FONT=Ubuntu Mono] wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

Run the command in terminal and post the resulting wireless-info.txt or attach the wireless-info.tar.gz, it depends on the size of the file

It will help get the info needed to fix your wireless[/FONT][/COLOR][COLOR=#000000][/COLOR]

---

### Post by kira-yamato-2008 on 2014-08-02
Actually I fixed it by enabling network boot options, because apparently the Wifi wasn't on by default. So marking this one solved.

---

