---
title: "Lost internet connection"
date: 2015-02-15
forum: Networking &amp; Wireless
---

### Post by huwsheena on 2015-02-15
Hi, 
I know there are many posts about this issue, I have tried some but with no success. I am running 14.04 alongside 12.04 as a dual boot system. 12.04 wireless works fine, as did 14.04. After a while if the laptop went into hibernation then it struggled to reconnect, sometimes needing 4 or 5 attempts before it could do so. Then it stopped working altogether. 12.04 still has no problems.
I haven't much knowledge of using terminal so I do need guiding through.
Most of the posts seem to point to the wireless card, but as its working ok on 12.04 I don't think that is the case here.
I also have an error message "the package system is broken" would that have anything to do with the problem?

---

### Post by col48 on 2015-02-15
Huwsheena
Welcome to the forum!
Let's see what more experienced users think of this....

As you say, it looks more like a software issue than a hardware one.  Is the card's driver in 14.04 different from that in 12.04? Does it need updating?  [Probably not!]
If not, I think I'd try to repair the package system to see if the problem goes away.  The command-line program for managing packages is called apt-get.  In 14.04, do
```
man  apt-get
```
which will display the manual entry for apt-get.
This is pretty powerful, so take care.
I think I'd try
```
apt-get  -sf
```
first off - the manual says this will tell you what changes would be done to your system without actually doing anything.
If you are happy with this, do 
```
apt-get  -f
```
to carry out the changes.  Don't interrupt it, it might leave things in a worse mess.
You will probably need root privileges (but try it without first), in which case the commands should be prefixed with sudo, eg ```
sudo apt-get -sf
``` and you will be prompted for the password.

But first, see what the community thinks of the above: this is a problem I have never had to deal with.

---

