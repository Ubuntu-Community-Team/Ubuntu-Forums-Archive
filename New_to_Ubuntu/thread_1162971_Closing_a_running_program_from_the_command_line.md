---
title: "Closing a running program from the command line"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by nimajiman on 2009-05-18
Hi all,

probably a simple question but just wondering what the equivalent command would be in a terminal to clicking the 'close' button (i.e. clicking the red cross at the top right corner of a window). 

Is it 'killall' (e.g. 'killall firefox') or is this a more destructive command than what happens when a window is closed the usual way?

Cheers

---

### Post by skymera on 2009-05-18
If a program is running in terminal press CTRL+C

Any program running from the terminal will be closed.

---

### Post by Joeb454 on 2009-05-18
killall will close all running instances of a process/application, that's correct :)

---

### Post by juancarlospaco on 2009-05-18
killall programname

xkill

top *(see it and kill it)*

---

### Post by kpkeerthi on 2009-05-18
> **nimajiman said:**
> Hi all,

probably a simple question but just wondering what the equivalent command would be in a terminal to clicking the 'close' button (i.e. clicking the red cross at the top right corner of a window). 

Is it 'killall' (e.g. 'killall firefox') or is this a more destructive command than what happens when a window is closed the usual way?

Cheers

The killall command sends a signal to the process. By default it sends SIGTERM signal, which is a signal to terminate the process gracefully (this give the program an option to shutdown itself properly).

If you want to kill a process "immediately", you would use **killall -s SIGKILL <program>**. The <program> cannot intercept SIGKILL and will cause it to stop unconditionally and immediately.

---

### Post by nimajiman on 2009-05-19
Thanks all for your replies - you have been a big help. 

My reason for asking was I wanted to use 'alarm-clock' to start a program at a specific time (e.g. deluge) and close it again at a specific time automatically, without me having to manually be at the computer. I was worried using 'killall deluge' as my command might somehow destroy the running process by shutting it down incorrectly or something, but I feel ok about using it now.

Loving ubuntu and a lot of that is because of the great support I always get in these forums!

Cheers

---

