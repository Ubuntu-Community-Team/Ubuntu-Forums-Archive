---
title: "make localhost program listen on network"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by benfindlay on 2009-06-03
Hi all,

I have a program that runs and to use it I point my web broswer at 127.0.0.1:[port]/progname to access it. What I would like to do is make this accessible to all machines on the local network. Any ideas as to how I would go about doing this?

Thanks

Ben

---

### Post by Celauran on 2009-06-03
Replace 127.0.0.1 with your LAN IP

---

### Post by benfindlay on 2009-06-03
> **Celauran said:**
> Replace 127.0.0.1 with your LAN IP

Unfortunately that doesn't work. I already tried doing that and it just hangs. From what I can tell the program isn't actually listening for anything on IP addresses other than localhost. Using ```
netstat -an | grep 12345

``` I get the following: > tcp        0      0 127.0.0.1:12345          0.0.0.0:*               LISTEN

Any ideas?

---

### Post by Celauran on 2009-06-03
Without knowing specifically what we're talking about? No. From your description, it sounds like Apache should be doing the listening. Is Apache working properly aside from with this one application?

---

### Post by benfindlay on 2009-06-03
I'll try and explain:

I have a forensic program called autopsy, which provides a browser based interface for various command line tools which are part of another forensic program called sleuthkit. Autopsy provides a nice clean html interface, which I access via directing my browser at [http://localhost:9999/autopsy](http://localhost:9999/autopsy) on the machine running it. What I am trying to do is set up a server which can then be accessed by other machines on my LAN to use the program.

Thanks

Ben

---

### Post by Celauran on 2009-06-03
You need to specify the remote host address when you start autopsy. To allow connections from, say, 192.168.0.101, run

```
sudo autopsy 192.168.0.101
```

You'll get an address in the terminal window giving you the address to connect to; something along the lines of [http://hostname:9999/57432658746856783265978436/autopsy](http://hostname:9999/57432658746856783265978436/autopsy)

---

### Post by benfindlay on 2009-06-03
> **Celauran said:**
> You need to specify the remote host address when you start autopsy. To allow connections from, say, 192.168.0.101, run

```
sudo autopsy 192.168.0.101
```

You'll get an address in the terminal window giving you the address to connect to; something along the lines of [http://hostname:9999/57432658746856783265978436/autopsy](http://hostname:9999/57432658746856783265978436/autopsy)

Thanks, that's good to know! So is it possibleto use wildcards (or some other method), so I can allow multiple remote machines to have access, for example averyone with a 192.168.1.X IP address?

Thanks again

Ben

---

### Post by Celauran on 2009-06-03
> **benfindlay said:**
> Thanks, that's good to know! So is it possibleto use wildcards (or some other method), so I can allow multiple remote machines to have access, for example averyone with a 192.168.1.X IP address?

Thanks again

Ben

No wildcards. You need to run multiple instances, each with their own remote IP specified, and the URL will be different for each.

---

### Post by benfindlay on 2009-06-03
In that case, I think I need another solution. Is there any way of using an apache server with perhaps some form of port forwarding to allow more access? This is happening on an isolated trusted network, so security isn't really an issue.

Thanks!

Ben

---

