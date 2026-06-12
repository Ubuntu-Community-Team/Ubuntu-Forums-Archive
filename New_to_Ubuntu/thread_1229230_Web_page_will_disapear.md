---
title: "Web page will disapear"
date: 2009-08-01
forum: New to Ubuntu
---

### Post by oz756c on 2009-08-01
I will be on a web page, I'll minimize it, but am unable to recover the minimized page. There is no reference to it in any of my tool bars. Is there a keyboard function I can use to make the minimized web page pop back up? or maybe a way to visualize the minimized page that that used to me in tool bar? I am using Ubuntu 8.04 ---Thanks

---

### Post by HiImTye on 2009-08-01
when you minimize it, hit alt+f2 and type 'gnome-system-monitor' (it should auto-complete). check to see if there is a 'firefox' (or whatever browser you're using) in the 'processes' tab.

this is the first step to diagnosing the problem as this will tell us if the program is crashing and force closing or not.

second, load it in a terminal (in a terminal type 'firefox' for instance) when it crashes it should spew out an error message

---

