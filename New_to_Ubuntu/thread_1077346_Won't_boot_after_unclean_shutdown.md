---
title: "Won't boot after unclean shutdown"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by ogger on 2009-02-22
I am getting for the second time an unclean shutdown message when I boot (dunno why), and this time the computer is not booting all the way through and freezes on the orange screen. 

History: I had some trouble yesterday to connect my scanner, but this is fixed at the end before I shut down. I am also having trouble to connect my D-Link 321 and trying different things, but I haven't done so yesterday. Not sure if this info is helpful. 

I guess I have to go into recovery mode? What do I need to do there? I am writing this from my windows partition. 

Thanks.

---

### Post by ogger on 2009-02-22
I went e2fchk in recovery mode. (it said s.th. That it could damage my system but I went ahead - scary). The result is: 

Could not start the x server due to an internal error. Please contact your system admi jstrator of check your syslog to diagnose. In the meAntime this display will be disabled. Please restart GDM when the problem is corrected. 

What is gdm and how do I get the syslog?

I typed in grub : find syslog, but got an error 15 file not found

---

### Post by ogger on 2009-02-22
Ok I googled on another computer where syslog is And it must be in /bar/log/syslog. When I do gedit ... It says display not available .... Doh. So how can I reAd syslog do figure out what's wrong? Also, is there a way to connect to the Internet in grub to try to reinstall packages as this is an option in recovery mode?

---

### Post by shredder12 on 2009-02-22
I am not really sure about the error in syslog..
but in order to start the gdm you can use the following command..
```
sudo /etc/init.d/gdm start
```..

---

### Post by shredder12 on 2009-02-22
and about the internet.
i think by wanting internet in grub you meant by having internet working in recovery mode..
you check it by pinging a website..
like.. ```
ping google.com
```
and for connecting to internet.. in recovery mode.. you can check the ubuntu community online help articles..
visit 
[www.help.ubuntu.com](www.help.ubuntu.com)
for basic help on internet and networking..
hope this helps..

---

### Post by Gramps on 2009-02-22
You can't use gedit from the command line

```
sudo nano /var/log/syslog
```

---

### Post by ogger on 2009-02-22
Thanks, I see syslog now. Well, it doesn't tell me much unfortunatly. It has 30 pages of log just for the first attempt this morning. My best bet is probably getting Internet working in recovery mode, which is not easy. I am connected with a cable to the router eth1 and wireless wlan0 should work, too, but haveen't managed it yet. I am still looking for a manual that works.

Another question though: how do I type in a command so the output doesn't scroll over the page, if the output is longer than a page. Something similar like it was in dos I think / p or so.

---

### Post by shredder12 on 2009-02-22
if the output is longer than the page then you can use the less/more command..
eg.
```
 ls | less 
```
will show you the output of the first page only and to get the further results you can either press the down key/page down or enter.

---

### Post by shredder12 on 2009-02-22
and as far as your internet settings are concerned.. you can probably get few hints to configure you network in ifconfig's man pages
```
 man ifconfig 
```
hope this helps..

---

### Post by ogger on 2009-02-22
thanks. this all helped and this on networking [http://kubuntuforums.net/forums/index.php?topic=3100052.0](http://kubuntuforums.net/forums/index.php?topic=3100052.0)

---

