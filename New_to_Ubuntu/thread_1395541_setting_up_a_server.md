---
title: "setting up a server"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by Mick8882003 on 2010-02-01
I have a wireless router and access point, the computer that I am writing this on is on the WAP and is my main PC.

I have just bought a new PC and am wanting to use the old one for backups, I have a network cable, so how do I set the old box on the router so that I can access it remotely, mainly I am not sure how to do the software setup.

Mick

---

### Post by lykwydchykyn on 2010-02-01
How much do you know about networking, and what do you want your server to do?  Also, what OS's are running on your network?

For starters, you want to give the system a static IP address, and probably install ssh-server.

---

### Post by Mick8882003 on 2010-02-01
I know very little to nothing about networks, both machines have ubuntu (9.10) on them, I was thinking of ssh, but now I'm not so sure.

Edit: oh yes I just want to occasionally back up data to the "server".

Mick

---

### Post by Mick8882003 on 2010-02-01
Oh yes can I do this without a kb and screen?

Mick

---

### Post by Geoff918 on 2010-02-01
It's pretty easy, actually. And, you'll want to use SSH if you want remote access. It's one of the easier things to deal with, I've found. Pretty much install openssh-server from the repos and you're ready to go.

You should be fine w/o a kb and monitor (a headless system). The only thing to be thinking about is whether or not your system will boot w/o a keyboard. Once it's started, you shouldn't have any problem.

---

### Post by lykwydchykyn on 2010-02-01
> **Mick8882003 said:**
> I know very little to nothing about networks, both machines have ubuntu (9.10) on them, I was thinking of ssh, but now I'm not so sure.

Edit: oh yes I just want to occasionally back up data to the "server".

Mick

If it's all Ubuntu, ssh is all you need.  From there you can browse files on the server using Nautilus, or mount any directory using sshfs.

I don't use a backup software myself, but I think most of them can work with SSH.

I keep a kb hooked to my server just in case I need to shut it down or reboot it cleanly (alt-sysrq stuff).

I'll also recommend [webmin](www.webmin.org) for doing remote administration.  Makes it very easy.

---

### Post by Mick8882003 on 2010-02-01
Is there an easy way of finding the ip off the router? ie without plugging it back in?

Edit: the ip for the "server."

Mick

---

### Post by lykwydchykyn on 2010-02-01
> **Mick8882003 said:**
> Is there an easy way of finding the ip off the router? ie without plugging it back in?

Edit: the ip for the "server."

Mick

Well, if SSH is running on the server, install nmap on your desktop machine.

Then scan the network for port 22 like this:
```

nmap -p 22 192.168.1.*

```

That's assuming your network is 192.168.1.0.  You'll need to know what your network IP is.  It should come back with the IP of your server.

---

### Post by Geoff918 on 2010-02-01
> **lykwydchykyn said:**
> Well, if SSH is running on the server, install nmap on your desktop machine.

Then scan the network for port 22 like this:
```

nmap -p 22 192.168.1.*

```That's assuming your network is 192.168.1.0.  You'll need to know what your network IP is.  It should come back with the IP of your server.

What he said--or you could just go to the server itself and issue an:

ifconfig

at the terminal. Read whatever the number is off the correct interface, e.g. eth0 or wlan0 or whatever.

---

### Post by Mick8882003 on 2010-02-01
I think i have the ip, however, I get the following:

Interesting ports on 192.168.*.*:
PORT   STATE  SERVICE
22/tcp closed ssh

closed? I am assuming that I need to allow it I am guessing.

edit: either that or log in???

Mick

---

### Post by Geoff918 on 2010-02-01
> **Mick8882003 said:**
> I think i have the ip, however, I get the following:

Interesting ports on 192.168.*.*:
PORT   STATE  SERVICE
22/tcp closed ssh

closed? I am assuming that I need to allow it I am guessing.

edit: either that or log in???

Mick

Well, you would need to enable it. You may also need to change a setting on your router. The router may permit the local traffic without complaint, but it may not also. First things first, yes I would open the port.

---

### Post by Mick8882003 on 2010-02-01
Thanks guys, that got it.

Tell me is there a way to remote into the box from outside my little network?

Mick

---

### Post by lykwydchykyn on 2010-02-01
> **Mick8882003 said:**
> Thanks guys, that got it.

Tell me is there a way to remote into the box from outside my little network?

Mick

You'd have to forward some port on the router to port 22 on your server.  You probably also want to sign up for a dynamic dns service like dyndns.org so you can actually find your ip when away.

If you do this, make sure you take steps to secure ssh.  The following articles should help with all this:

[http://www.debian-administration.org/articles/573](http://www.debian-administration.org/articles/573)
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

