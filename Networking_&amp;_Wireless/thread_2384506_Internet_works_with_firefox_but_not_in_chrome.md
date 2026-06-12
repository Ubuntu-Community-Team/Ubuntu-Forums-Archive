---
title: "Internet works with firefox but not in chrome"
date: 2018-02-08
forum: Networking &amp; Wireless
---

### Post by the.fallen.one on 2018-02-08
Greetings,
i am new to Linux and know nothing about it but want to learn it. I ditched windows and use only ubuntu 17.10 as a daily driver. Up until yesterday i had issues with weak wifi signal and very very slow Internet and somehow managed to fix it after reading about it and understanding little and it was working fine. but since today Internet is not working on chrome browser, it says-"DNS_PROBE_FINISHED_BAD_CONFIG"[COLOR=#646464][FONT=sans].[/FONT][/COLOR] but works fine with firefox. my DNS primary is and secondary is showing-"8.8.8.8,8.8.4.4".
i keep reading about "resolvconf" but it says "sudo: resolvconf: command not found". 
I have installed firetools and use firejail firefox and works with or without it but in chrome it doesnt either way. i have not installed anything else.

I do not know what to do. Please be kind to  help me.

---

### Post by The Cog on 2018-02-08
This link might help:
[https://askubuntu.com/questions/622470/dns-probe-finished-bad-config-error-in-ubuntu-14-04](https://askubuntu.com/questions/622470/dns-probe-finished-bad-config-error-in-ubuntu-14-04)

Beyond that I don't know - I just did a little googling and have not had to deal with this problem myself. I confirm that the symlink  /etc/resolv.conf is still there in a working 16.04 install.

---

### Post by the.fallen.one on 2018-02-08
Thank you for your quick reply sir
Tried that too,this is what i get when i run that script.

sudo resolvconf -u

"sudo: resolvconf: command not found"

others are getting the error but i'm getting command not found. 
I don't know what am i doing wrong.

---

### Post by vasa1 on 2018-02-08
> **the.fallen.one said:**
> Thank you for your quick reply sir
Tried that too,this is what i get when i run that script.

sudo resolvconf -u

"sudo: resolvconf: command not found"

others are getting the error but i'm getting command not found. 
I don't know what am i doing wrong.
[s]Isn't it resolv_._conf?[/s]

Another link: [https://stackoverflow.com/questions/32045682/dns-probe-finished-bad-config-error](https://stackoverflow.com/questions/32045682/dns-probe-finished-bad-config-error)

---

### Post by the.fallen.one on 2018-02-08
Sorry sir, I have no idea, I just copied from that link above and it says "sudo resolvconf -u".

---

### Post by the.fallen.one on 2018-02-08
Ran the other links scrpit too.
THis is the output.
 cat /etc/resolv.conf
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.
nameserver 127.0.0.53

After this ran "systemd-resolve --status" and found the DNS Servers listed as 8.8.8.8,8.8.4.4 in a big windows with links numbering 3,2 etc

---

### Post by vasa1 on 2018-02-08
> **the.fallen.one said:**
> Sorry sir, I have no idea, I just copied from that link above and it says "sudo resolvconf -u".

Did you read a little further on in that answer?

---

### Post by the.fallen.one on 2018-02-08
> **vasa1 said:**
> Did you read a little further on in that answer?

Sorry, I didn't think it through before replying. 
I thought that was the end of your post. 
please bear with me. i'm still learning.

---

### Post by vasa1 on 2018-02-08
> **the.fallen.one said:**
> Sorry sir, I have no idea, I just copied from that link above and it says "sudo resolvconf -u".You're right! Could *man resolvconf* be of some use?

---

### Post by the.fallen.one on 2018-02-08
"sudo man resolvconf -u"
 
No manual entry for resolvconf
No manual entry for -u

Is this what i was supposed to type?
Please  could you please type the script i am supposed to execute?
I don't know the language.
Sorry to ask so much of you.

---

### Post by vasa1 on 2018-02-08
> **the.fallen.one said:**
> Thank you for your quick reply sir
Tried that too,this is what i get when i run that script.

sudo resolvconf -u

"sudo: resolvconf: command not found"

others are getting the error but i'm getting command not found. 
I don't know what am i doing wrong.
Re.

"sudo: resolvconf: command not found"

what do you see when you run```
which resolvconf
``` in your terminal?

---

### Post by the.fallen.one on 2018-02-08
> **vasa1 said:**
> Re.

"sudo: resolvconf: command not found"

what do you see when you run```
which resolvconf
``` in your terminal?

No reply.
Just another command line with my username came.

---

### Post by vasa1 on 2018-02-08
Hmmm .... Is your system fully updated?

Do you see anything odd when you run *sudo apt-get update* and *sudo apt-get upgrade*? If everything looks good, try *sudo apt-get dist-upgrade* and answer "N" if you feel uncomfortable.

---

### Post by the.fallen.one on 2018-02-08
> **vasa1 said:**
> Hmmm .... Is your system fully updated?

Do you see anything odd when you run *sudo apt-get update* and *sudo apt-get upgrade*? If everything looks good, try *sudo apt-get dist-upgrade* and answer "N" if you feel uncomfortable.

I didn't run the script for updating but definetley used the software updater to download and install a 65mb file after the clean install but i will run the update once again and report back.

---

### Post by vasa1 on 2018-02-08
Also try```
dpkg -l | grep ^..r
```and```
sudo dpkg -C
```

---

### Post by the.fallen.one on 2018-02-08
> **vasa1 said:**
> Hmmm .... Is your system fully updated?

Do you see anything odd when you run *sudo apt-get update* and *sudo apt-get upgrade*? If everything looks good, try *sudo apt-get dist-upgrade* and answer "N" if you feel uncomfortable.

This is what it says at the end "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."
and after i ran the update code it said "Installation finished. No error".

---

### Post by the.fallen.one on 2018-02-08
> **vasa1 said:**
> Also try```
dpkg -l | grep ^..r
```and```
sudo dpkg -C
```

Both these codes ran with no replies. It just ran the script. Showed nothing back. 


Also just a query i have to refresh to see new posts. Is this normal?

---

### Post by vasa1 on 2018-02-08
Please post the entire output of```
ls -alR /etc/resolvconf
``` here between code tags in case there's something amiss there.

---

### Post by the.fallen.one on 2018-02-08
> **vasa1 said:**
> Please post the entire output of```
ls -alR /etc/resolvconf
``` here between code tags in case there's something amiss there.

```
etc/resolvconf:
total 20
drwxr-xr-x   3 root root  4096 Jan  6 02:07 .
drwxr-xr-x 130 root root 12288 Feb  8 15:39 ..
drwxr-xr-x   2 root root  4096 Feb  7 01:12 update-libc.d

/etc/resolvconf/update-libc.d:
total 16
drwxr-xr-x 2 root root 4096 Feb  7 01:12 .
drwxr-xr-x 3 root root 4096 Jan  6 02:07 ..
-rwxr-xr-x 1 root root  249 Jul  4  2016 avahi-daemon
-rwxr-xr-x 1 root root  439 Sep 29 08:24 postfix
```


This is the entire output of the code.

---

### Post by vasa1 on 2018-02-08
Just for comparison, I have```
/etc/resolvconf:
total 32
drwxr-xr-x   5 root root  4096 Nov  7 06:25 .
drwxr-xr-x 148 root root 12288 Feb  8 07:07 ..
-rw-r--r--   1 root root   511 Jun  4  2015 interface-order
drwxr-xr-x   2 root root  4096 Nov  7 06:25 resolv.conf.d
drwxr-xr-x   2 root root  4096 Nov  7 06:25 update.d
drwxr-xr-x   2 root root  4096 Feb 16  2017 update-libc.d

/etc/resolvconf/resolv.conf.d:
total 12
drwxr-xr-x 2 root root 4096 Nov  7 06:25 .
drwxr-xr-x 5 root root 4096 Nov  7 06:25 ..
-rw-r--r-- 1 root root    0 Jun  4  2015 base
-rw-r--r-- 1 root root  151 Jun  4  2015 head

/etc/resolvconf/update.d:                                                                                                                            
total 16                                                                                                                                             
drwxr-xr-x 2 root root 4096 Nov  7 06:25 .                                                                                                           
drwxr-xr-x 5 root root 4096 Nov  7 06:25 ..                                                                                                          
-rwxr-xr-x 1 root root 4622 Nov 23  2015 libc                                                                                                        
                                                                                                                                                     
/etc/resolvconf/update-libc.d:                                                                                                                       
total 12                                                                                                                                             
drwxr-xr-x 2 root root 4096 Feb 16  2017 .                                                                                                           
drwxr-xr-x 5 root root 4096 Nov  7 06:25 ..                                                                                                          
-rwxr-xr-x 1 root root  249 Nov 24  2015 avahi-daemon                                                                                                
03:50 PM ~ $                                                                       
```on Kubuntu 16.04. I don't know if things are so different on 17.10 but you seem to be missing quite a bit! But you have postfix!

---

### Post by the.fallen.one on 2018-02-08
> **vasa1 said:**
> Just for comparison, I have```
/etc/resolvconf:
total 32
drwxr-xr-x   5 root root  4096 Nov  7 06:25 .
drwxr-xr-x 148 root root 12288 Feb  8 07:07 ..
-rw-r--r--   1 root root   511 Jun  4  2015 interface-order
drwxr-xr-x   2 root root  4096 Nov  7 06:25 resolv.conf.d
drwxr-xr-x   2 root root  4096 Nov  7 06:25 update.d
drwxr-xr-x   2 root root  4096 Feb 16  2017 update-libc.d

/etc/resolvconf/resolv.conf.d:
total 12
drwxr-xr-x 2 root root 4096 Nov  7 06:25 .
drwxr-xr-x 5 root root 4096 Nov  7 06:25 ..
-rw-r--r-- 1 root root    0 Jun  4  2015 base
-rw-r--r-- 1 root root  151 Jun  4  2015 head

/etc/resolvconf/update.d:                                                                                                                            
total 16                                                                                                                                             
drwxr-xr-x 2 root root 4096 Nov  7 06:25 .                                                                                                           
drwxr-xr-x 5 root root 4096 Nov  7 06:25 ..                                                                                                          
-rwxr-xr-x 1 root root 4622 Nov 23  2015 libc                                                                                                        
                                                                                                                                                     
/etc/resolvconf/update-libc.d:                                                                                                                       
total 12                                                                                                                                             
drwxr-xr-x 2 root root 4096 Feb 16  2017 .                                                                                                           
drwxr-xr-x 5 root root 4096 Nov  7 06:25 ..                                                                                                          
-rwxr-xr-x 1 root root  249 Nov 24  2015 avahi-daemon                                                                                                
03:50 PM ~ $                                                                       
```on Kubuntu 16.04. I don't know if things are so different on 17.10 but you seem to be missing quite a bit! But you have postfix!

I dont know much thats not good, right?

also its showing resolvconf but wi was it not showing when i ran "sudo resolvconf -u". Is it because i'm not in the etc directory as its showing?

---

### Post by vasa1 on 2018-02-08
Please post the output of```
lsb_release -a
```and```
cat /etc/*-release
```and```
cat /var/log/installer/media-info
```and```
cat /etc/debian_version
```

---

### Post by the.fallen.one on 2018-02-08
> **vasa1 said:**
> Please post the output of```
lsb_release -a
```and```
cat /etc/*-release
```and```
cat /var/log/installer/media-info
```and```
cat /etc/debian_version
```

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful


```
and 
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.10
DISTRIB_CODENAME=artful
DISTRIB_DESCRIPTION="Ubuntu 17.10"
NAME="Ubuntu"
VERSION="17.10 (Artful Aardvark)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 17.10"
VERSION_ID="17.10"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=artful
UBUNTU_CODENAME=artful


```
and 

```
Ubuntu 17.10 "Artful Aardvark" - Release amd64 (20180105.1)
```

and 

```
stretch/sid


```


My apologies, I went for lunch. i hope this is how you wanted.

---

### Post by vasa1 on 2018-02-08
I wonder if running```
sudo apt-get install --reinstall resolvconf
```will fix things. It's better to wait until someone who's really knowledgeable about these things comes along!

---

### Post by the.fallen.one on 2018-02-08
> **vasa1 said:**
> I wonder if running```
sudo apt-get install --reinstall resolvconf
```will fix things. It's better to wait until someone who's really knowledgeable about these things comes along!

Holy you're absolutely right. 

It worked. obviously i dont know how but it works through the firejail too. 

I hope it doesn't stop working again tomorrow.
Thank you so much again. 

Also i want to ask you if there are any pages or something where i can go and learn this? as i'm new i want to learn wi people love linux more. 

Thank you again.

---

### Post by vasa1 on 2018-02-08
You're welcome.

[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) 

As for resources, check out the "stickies" here: [https://ubuntuforums.org/forumdisplay.php?f=326](https://ubuntuforums.org/forumdisplay.php?f=326)

---

