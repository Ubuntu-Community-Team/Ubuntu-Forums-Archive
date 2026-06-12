---
title: "Internet suddenly went buggy..."
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by holdie on 2007-01-30
My internet had been working properly for the past couple of months, but about a week ago it just randomly went on the fritz...

Upon checking the network monitor, it says the signal is at 0%, but has a bunch of packets being recieved, although very few is sent...the status is constantly shifting between sending, recieving, and idle, although I can't connect to any websites.

Before, I just had it automatically detect wireless networks, so i'm not sure what may have happened to mess it up.  I went and cleared my /etc/resolv.conf file, but that didn't do anything...

I can't seem to figure out what's goin wrong here, any suggestions?

---

### Post by holdie on 2007-01-31
...any ideas?  it's getting annoying to switch back and forth between OSs each time i have something new to try

---

### Post by mayonaise15 on 2007-02-01
what do you get out when you put in this command?

```
cat /etc/resolv.conf
```

---

### Post by holdie on 2007-02-01
I ran that command and all it did was show a blank line and then gave me the command again...not really sure what that means but does that look wrong?

---

### Post by holdie on 2007-02-01
I'm trying to download network manager and bring it over to my linux partition, however when I attempt to run the program i get a message that says that nm-applet doesn't exist or something to that effect...

---

### Post by holdie on 2007-02-02
and yeah, i can't really come with an excuse for another flagrant bump so bump

---

### Post by holdie on 2007-02-02
.

---

### Post by mayonaise15 on 2007-02-02
sorry to keep you waiting holdie,

You need to have the IP Address of at least one DNS server in your /etc/resolv.conf file.  Start by opening up that file with this console command:

> gksudo gedit /etc/resolv.conf

Then add this line and save it:
> nameserver 4.2.2.2

You may need to restart your network service with the following command:
> sudo /etc/init.d/networking restart

Let us know if this solves your problem or not.

---

### Post by holdie on 2007-02-03
I went through all the steps you gave me, restarted the wireless, and it came up with the whole looking for a DHCP thing but didn't find any, it finished saying that it couldn't find any sources so it was "sleeping" (I dunno if that was it exactly but something like that)

anyways, the internet still wouldn't work...anything else I can do?

and thanks for helping by the way haha

---

### Post by holdie on 2007-02-03
alright I decided to boot up with the ubuntu distro CD, and the internet wasn't working there either...so maybe this has something to do with a change in the router settings or something.

I know that we recently switched to a more secure setting, so maybe that has something to do with it although windows.  Is there any way I can access a more comprehensive set of options for the wireless card in linux?

---

### Post by mayonaise15 on 2007-02-04
> I know that we recently switched to a more secure setting, so maybe that has something to do with it...

That could very well be.  If you have switched over to WPA2 authentication/encryption, you may need to [follow this guide]("http://www.ubuntuforums.org/showthread.php?t=318539").

---

### Post by holdie on 2007-02-05
interestingly enough, I tried out my computer at a local coffee shop and my computer read that there was a pretty strong signal (unlike at my house).  However, it still wouldn't connect to whatever server was broadcasting that signal.  I don't think it was encrypted or anything, because windows connected fine, but it seemed as though my wireless was disabled unless i told it specifically what server to look for...any way I can get it to just automatically connect?

---

