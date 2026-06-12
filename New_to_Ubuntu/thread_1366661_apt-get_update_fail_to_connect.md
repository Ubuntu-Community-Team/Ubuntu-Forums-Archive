---
title: "apt-get update fail to connect"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by tedchyn on 2009-12-28
After install ubuntu 804. I ran apt-get update and got (111 connection refused) error message. for security.ubuntu.com:80.
However, I am able to use firefox to connect to [http://www.security.ubuntu.com](http://www.security.ubuntu.com) ?
can anyone she light on this.

---

### Post by audiomick on 2009-12-28
Hallo,
first of all, I can't connect to your link.
It is possible that this is just a temporary server problem. If no-one else has a better suggestion, try it again tomorrow.
If it still doesn't work, post again here.

---

### Post by tedchyn on 2009-12-28
This happened many times over period of times and I had restart many times.

---

### Post by zero-n on 2009-12-28
Please Could you paste the exact message here.

---

### Post by tedchyn on 2009-12-28
> **zero-n said:**
> Please Could you paste the exact message here.
 
 
[EMAIL="root@tedchyn-desktop"]root@tedchyn-desktop[/EMAIL]:~# apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
  Could not connect to us.archive.ubuntu.com:80 (91.189.88.40). - connect (111 Connection refused) [IP: 91.189.88.40 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
0% [Connecting to us.archive.ubuntu.com (91.189.88.46)] [Connecting to security
[EMAIL="root@tedchyn-desktop"]root@tedchyn-desktop[/EMAIL]:~#

---

### Post by EssexEagle on 2009-12-28
> **audiomick said:**
> Hallo,
first of all, I can't connect to your link.

That's because the link should have been [http://security.ubuntu.com/](http://security.ubuntu.com/) (no www. at the start).

---

### Post by zero-n on 2009-12-28
tedchyn could paste the content of this file :

```
sudo gedit /etc/apt/apt.conf
```

---

### Post by tedchyn on 2009-12-29
> **EssexEagle said:**
> That's because the link should have been [http://security.ubuntu.com/](http://security.ubuntu.com/) (no www. at the start).
 
I execute apt-get update see my post [http://security.ubuntu.com](http://security.ubuntu.com) with error meeage.

---

### Post by tedchyn on 2009-12-29
under /etc/apt I don't have file apt.conf.  however there is a directory apt.conf.d under /etc/apt with many files in them. name of these files like 00turstcdrom 01autoremove 99update-notifier etc

---

### Post by slakkie on 2009-12-29
Post your sources.list.

Are you trying to connect via a proxy?

---

### Post by sandyd on 2009-12-29
> **zero-n said:**
> tedchyn could paste the content of this file :

```
sudo gedit /etc/apt/apt.conf
```
aww comeon.....

should be 
```

cat /etc/apt/sources.list >> ~/Desktop/sources.list

```
attach the sources.list file that just appeared magically to your post.

---

### Post by tedchyn on 2009-12-29
what is a source.list ?
I am connect via a proxy. apt-get update gave errors(see prior posting) but firefox with same url worked.

---

### Post by tedchyn on 2009-12-29
here is sources_list:
 
#deb cdrom:[Ubuntu 8.04.3 _Hardy Heron_ - Release i386 (20090713.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

---

### Post by tedchyn on 2009-12-29
issue resolved. I changed system-> proxy from connect direct to use proxy and reboot ubunto and update is working now. thanks ted

---

