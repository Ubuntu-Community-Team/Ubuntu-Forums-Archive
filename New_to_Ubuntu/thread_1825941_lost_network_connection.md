---
title: "lost network connection"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by ihartmydoghead on 2011-08-16
I have been on Ubuntu for a week or so, and tonight, I cannot get a network connection. I have rebooted my router several times but no luck. {I am currently on my GF's computer, on the same network, so obviously the network and ISP is working, but my computer (Ubuntu 11.04) does not see the network. Help !

---

### Post by dineshs on 2011-08-16
Please open a terminal (applications-accessories-terminal) on ubuntu computer and post the result of ```
sudo lshw -C network
```

---

### Post by ihartmydoghead on 2011-08-16
> **dineshs said:**
> Please open a terminal (applications-accessories-terminal) on ubuntu computer and post the result of ```
sudo lshw -C network
```

will do - hold on a minute

---

### Post by ihartmydoghead on 2011-08-16
ok found terminal

---

### Post by HermanAB on 2011-08-16
Well, rebooting is not efficient.

Some tips:
See what is wrong with 'ifconfig' and 'route'.
Restart the network connection by simply replugging the cable.
Restart the DHCP process with 'dhclient eth0'

---

### Post by ihartmydoghead on 2011-08-16
> **ihartmydoghead said:**
> will do - hold on a minute

it asked me for my password
i entered it
it said  "network disabled"

---

### Post by ofnuts on 2011-08-16
> **ihartmydoghead said:**
> it asked me for my password
i entered it
it said  "network disabled"
In  /var/lib/NetworkManager/NetworkManager.state: check if it says 

NetworkingEnabled=false 

or

NetworkingEnabled=false

If it says "false":

sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager restart

(yes, you can erase it, it is recreated automatically)

You may have to manually kick networking back on with commands like `sudo ifconfig eth0 up` (where eth0 is your network interface) and `sudo dhclient`.

Side note: if this is indeed the problem, it also happened to me after the 1st install of Ubuntu. Despite the fix above, it came back several times during my first weeks of use (just had to rerun the commands) and then eventually the problem vanished.

---

### Post by dineshs on 2011-08-16
> **ihartmydoghead said:**
> it asked me for my password
i entered it
it said  "network disabled"
Please click on the Network Manager icon on top right of the panel.Ensure that enable networking is ticked.

---

### Post by ihartmydoghead on 2011-08-16
(totally unfamiliar with command line and terminal) 
OK, I got to var/lib/NetworkManager$ but cannot get to ".state" 
var/lib/NetworkManager$  <---major learning curve to get to here

---

### Post by ofnuts on 2011-08-16
> **ihartmydoghead said:**
> (totally unfamiliar with command line and terminal) 
OK, I got to var/lib/NetworkManager$ but cannot get to ".state" 
var/lib/NetworkManager$  <---major learning curve to get to here
issue the command:

```
cat /var/lib/NetworkManager/NetworkManager.state
```in any terminal. Should type out on terminal something like:
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```(of course, your may say "false")

---

### Post by ihartmydoghead on 2011-08-16
OK,  it says "No such file or directory"

---

### Post by ofnuts on 2011-08-16
> **ihartmydoghead said:**
> OK,  it says "No such file or directory"
Strange... 

Try 

```
sudo service network-manager start
```

and enter your password at the prompt. Any bad messages? Is the file above created?

---

### Post by ihartmydoghead on 2011-08-16
It says "Job is already running: network-manager"

---

### Post by ihartmydoghead on 2011-08-16
> **ofnuts said:**
> Strange... 

Try 

```
sudo service network-manager start
```

and enter your password at the prompt. Any bad messages? Is the file above created?

It says "Job is already running: network-manager"

---

### Post by dineshs on 2011-08-17
> (totally unfamiliar with command line and terminal) 
Did you try > Please click on the Network Manager icon on top right of the panel.Ensure that enable networking is ticked.
followed by a```
sudo service network-manager restart
```

---

### Post by ihartmydoghead on 2011-08-17
> **dineshs said:**
> Did you try followed by a```
sudo service network-manager restart
```
Will try it. Thanks...

---

### Post by ihartmydoghead on 2011-08-17
Nope.

---

### Post by pi.boy.travis on 2011-08-17
Rather than mess with the state files, maybe try rebooting the laptop?

---

### Post by dineshs on 2011-08-18
> Nope.You mean when you click NM icon and try to tick 'enable networking' you are not able to?
Is 'enable networking' greyed ?
Did you check BIOS settings? Is it enabled there?

---

### Post by ihartmydoghead on 2011-09-01
I've tried everything that was suggested. Finally, i bypassed wireless router, and it will work with a cable, and after 'learning' the wireless network, will work temporarily uncabled, but always 'forgets' wireless network again, and needs to be cabled again. ??? Another computer on network works perfectly, so WTH ? For now, running cabled.

---

