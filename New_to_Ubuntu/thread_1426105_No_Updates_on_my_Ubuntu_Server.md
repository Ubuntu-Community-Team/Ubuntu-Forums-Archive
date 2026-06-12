---
title: "No Updates on my Ubuntu Server"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by dmaxel on 2010-03-09
Hi everyone,

I have a very strange problem. A couple of days ago, I was able to check for updates, where it found a new kernel, although I didn't install it. A couple of days later I try to check again, and my server is unable to even connect to the repos with sudo apt-get update. Then, if I try to skip that part and update using sudo apt-get dist-upgrade, it asks me if i want to install unauthenticated packages, and downloading fails. Any help on fixing this?

---

### Post by dmaxel on 2010-03-10
Oh, and I already know that rebooting the system doesn't help either.

---

### Post by undecim on 2010-03-10
Can you try a few things?

First, ping your download mirror, (us.archive.ubuntu.com in my case; You can check yours by looking at /etc/apt/sources.list)
```
ping us.archive.ubuntu.com
```

If you get some reponses, try downloading a file directly
```
wget http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release
```

If you didn't get any responses from the ping command, try
```
ping google.com
```
and
```
ping 8.8.8.8
```

---

### Post by dmaxel on 2010-03-10
I tried pinging both those sites, but both have the result:

unknown host us.archive.ubuntu.com
unknown host google.com

However, I know that the server has some form of internet connection because I can access the sites it hosts as well as SSH to enter the commands.

---

### Post by undecim on 2010-03-10
Looks like a DNS problem. If ping 8.8.8.8 works, that will confirm it.

What does your /etc/resolv.conf look like?

---

### Post by dmaxel on 2010-03-10
Yeah, it responded to 8.8.8.8

/etc/resolv.conf has...
```
search [domains it hosts]
nameserver [IP of router]
```
Of course, with actual values in the brakets. Should I maybe change the nameserver to Google's DNS servers 8.8.8.8;8.8.4.4?

---

### Post by undecim on 2010-03-10
> **dmaxel said:**
> Yeah, it responded to 8.8.8.8

/etc/resolv.conf has...
```
search [domains it hosts]
nameserver [IP of router]
```
Of course, with actual values in the brakets. Should I maybe change the nameserver to Google's DNS servers 8.8.8.8;8.8.4.4?

Yeah, switching to Google's DNS servers might fix it. I've switched mine to google via my router (for all my DHCP clients) and had fewer DNS related problems since.

---

### Post by rolnics on 2010-03-10
Another alternative is to use OpenDNS, which I use.

[http://www.opendns.com/]("http://www.opendns.com/")

---

### Post by dmaxel on 2010-03-10
Thank you so much for your help. I will edit the file to make it use Google as soon as I get home, as I am currently doing all of this on my BlackBerry, and editing files is the only thing I cannot do, yet.

---

### Post by undecim on 2010-03-10
You are using SSH to connect to your server from a BlackBerry?

What stops you from using "sudo nano /etc/resolv.conf"?

---

### Post by dmaxel on 2010-03-10
Yes, that works too as well as DynDNS's Internet Guide service. :D
> **undecim said:**
> You are using SSH to connect to your server from a BlackBerry?

What stops you from using "sudo nano /etc/resolv.conf"?
Yes, I use midpSSH to connect to my server's terminal with my BlackBerry.

There is something with terminal parameters that the server needs to understand, so I need to install ncurses for nano to work on my BB. But I can't do that right because of the problem I have lol.

---

### Post by dmaxel on 2010-03-10
OK, I finally got the opportunity to edit the file to include Google's DNS servers, did a reboot, and now it's finding everything like it should. Thanks for all the help. :D

---

