---
title: "Network dead."
date: 2020-04-13
forum: Networking &amp; Wireless
---

### Post by warren3 on 2020-04-13
Hi.

I am running Kubuntu 19.10.

I have a separate issue where my login has broke so was using tty2 to uninstall sddm and then reinstall it.  After I uninstalled sddm I then tried to reinstall is with apt but I got a 'Temporary failure resolving' error message on the command line for all the links in sources list.  When I do apt update I get the same.

I did a quick google and found that is could possible be a DNS issue.  I looked in resolv.conf and my nameserver is 127.0.0.53.

I am really at a loss about where to start with this.  I am not sure I can run the script from the command line?

Thanks.

---

### Post by chili555 on 2020-04-13
Let's have a look at:

```
ping -c3 8.8.8.8
ls -al /etc/resolv.conf
```

---

### Post by warren3 on 2020-04-13
Thanks Chili555.

I forgot to say I use a TPLINK usb wifi adapter.

> **chili555 said:**
> Let's have a look at:

```
ping -c3 8.8.8.8
ls -al /etc/resolv.conf
```

$ ping -c3 8.8.8.8
ping: connect: Network is unreachable.

$ ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Oct 28 19:39 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

---

### Post by chili555 on 2020-04-13
You are not actually connected, it seems. Your resolv.conf looks perfect.

Let's have a look at:```
ip addr show
lspci -nnk | grep -e 0200 -e 0280 -A3
```

---

### Post by warren3 on 2020-04-13
> **chili555 said:**
> You are not actually connected, it seems. Your resolv.conf looks perfect.

Let's have a look at:```
ip addr show
lspci -nnk | grep -e 0200 -e 0280 -A3
```

Here...

---

### Post by chili555 on 2020-04-13
I assume then that it is USB wireless that is not connecting. Does it scan and see networks or are other interesting messages produced?

```
sudo iwlist scan
dmesg | grep wlx
rfkill list all
```

---

### Post by warren3 on 2020-04-14
Hi Chili555

Here is the output

---

### Post by chili555 on 2020-04-14
Although you say that you are running kubuntu, a desktop environment, all we see here are black screens. Is the problem that the usual KDE desktop no longer starts and so Network Manager is unavailable? Is the further problem that you are unable to undertake the fix to KDE without downloading packages and therefore, need the internet?

Your network device looks perfectly healthy. If it scan and sees networks, then it probably will connect. Please try:

```
nmcli device wifi rescan
nmcli device wifi list
nmcli device wifi connect my_lil_router password 1234567890
```

Of course, substitute your network name and password details here.

Confirm that you are connected:

```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by warren3 on 2020-04-14
Hi Chili555.

Yes I lost login and I was told to uninstall sddm and then reinstall.  The problem came when I tried to reinstall.  Please see [https://ubuntuforums.org/showthread.php?t=2440365](https://ubuntuforums.org/showthread.php?t=2440365) for this other issue.

I will try your commands soon and get back to you.

---

### Post by warren3 on 2020-04-14
> **chili555 said:**
> Although you say that you are running kubuntu, a desktop environment, all we see here are black screens. Is the problem that the usual KDE desktop no longer starts and so Network Manager is unavailable? Is the further problem that you are unable to undertake the fix to KDE without downloading packages and therefore, need the internet?

Your network device looks perfectly healthy. If it scan and sees networks, then it probably will connect. Please try:

```
nmcli device wifi rescan
nmcli device wifi list
nmcli device wifi connect my_lil_router password 1234567890
```

Of course, substitute your network name and password details here.

Confirm that you are connected:

```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

Yes I'm in!

I had a little hicup when I treid to connect to my router as it said 'secrets are required', so I managed to quickly google it which told me to delete my SSID and then connect again and it worked.

I reinstalled sddm and now my GUI is back!  I've logged in and everything is fine.

So thank you very much Chili555 and I'll log the thread as solved.

---

### Post by chili555 on 2020-04-14
Awesome! Glad it's working! Have fun.

---

