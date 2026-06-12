---
title: "Unable to browse list of SMB shares from Win10 after 20.04.5 LTS update"
date: 2023-03-10
forum: Networking &amp; Wireless
---

### Post by ianmanning on 2023-03-10
I was prompted to upgrade my Lubuntu machine this morning, and am now on 20.04.5 LTS. Previously I was able to browse a list of shares on this machine from a Windows 10 machine on the same subnet, by typing the IP address into File Explorer. Following the update, I get an error if I do this - I need to enter a share name. If I enter the IP address only it fails to connect.
Any idea how/if I can return to being able to browse the list of shares on my Lubuntu machine?

---

### Post by TheFu on 2023-03-12
Just a guess, but do you have **avahi** installed?

---

### Post by ianmanning on 2023-03-13
> **TheFu said:**
> Just a guess, but do you have **avahi** installed?

I have no idea what avahi is, so I guess not

---

### Post by him610 on 2023-03-13
> I have no idea what avahi is, so I guess not
```
apt show avahi

```

---

### Post by ianmanning on 2023-03-14
> **him610 said:**
> ```
apt show avahi

```
OK I can confirm that avahi is not installed.

---

### Post by Morbius1 on 2023-03-14
avahi is installed by default in Lubuntu 20. The apt package is not called that however:
```
apt show avahi-daemon
```

While you can access a Samba server via it's avahi host name from Win10 it's not made discoverable via avahi. You would need to specify the hostname.local and the share name just like you did with the ip address.

The problem I have with your post is this:
> Any idea how/if I can return to being able to browse the list of shares on my Lubuntu machine? 
Win10 and Lubuntu in their default states never could browse for a list of shares on a Linux samba server.

Only 2 ways to make it happen:

Ignore all the warnings about security and enable smb1 on both Win10 and Linux.

Install wsdd - which Lubuntu 20 doesn't have.

Also, based on the data you provided elsewhere none of the updates had anything to do with samba:
I> Install: 
linux-headers-5.4.0-144-generic:amd64 (5.4.0-144.161, automatic), 
linux-headers-5.4.0-144:amd64 (5.4.0-144.161, automatic), 
linux-modules-extra-5.4.0-144-generic:amd64 (5.4.0-144.161, automatic), 
linux-modules-5.4.0-144-generic:amd64 (5.4.0-144.161, automatic), 
linux-image-5.4.0-144-generic:amd64 (5.4.0-144.161, automatic)
Upgrade: 
linux-headers-generic:amd64 (5.4.0.139.137, 5.4.0.144.142), 
linux-libc-dev:amd64 (5.4.0-139.156, 5.4.0-144.161), 
linux-image-generic:amd64 (5.4.0.139.137, 5.4.0.144.142), 
tcpdump:amd64 (4.9.3-4ubuntu0.1, 4.9.3-4ubuntu0.2), 
ubuntu-advantage-tools:amd64 (27.13.5~20.04.1, 27.13.6~20.04.1), 
linux-generic:amd64 (5.4.0.139.137, 5.4.0.144.142)
End-Date: 2023-03-10  10:52:13

---

### Post by ianmanning on 2023-03-14
Ah OK yes I see it now. I was definitely able to browse the list of shares on the Lubuntu machine before the update(from File Explorer on Win10) - I used to do it alot. So I guess I had SMB1 enabled.

So I should install wsdd?
"apt install wsdd" didn't find the package
???

---

### Post by Morbius1 on 2023-03-14
There is no wsdd package in Lubuntu 20. It's there on Lubuntu 22.

---

### Post by ianmanning on 2023-03-14
> **Morbius1 said:**
> There is no wsdd package in Lubuntu 20. It's there on Lubuntu 22.

Is there any other way that I can re-enable browsing of my list of SMB shares on 20.04?

---

### Post by TheFu on 2023-03-14
> **ianmanning said:**
> Is there any other way that I can re-enable browsing of my list of SMB shares on 20.04?

"any other way" ... means is it possible without regard to cost, skills, technical challenges.  Do you really mean that?

I suspect you really mean "any other practical, free, way".  After all, if you have $50K to spend to solve this problem, I bet someone would agree to that payment to create a solution.  50% pre-paid.

---

### Post by ianmanning on 2023-03-15
> **TheFu said:**
> "any other way" ... means is it possible without regard to cost, skills, technical challenges.  Do you really mean that?

I suspect you really mean "any other practical, free, way".  After all, if you have $50K to spend to solve this problem, I bet someone would agree to that payment to create a solution.  50% pre-paid.

$50k to restore a feature which was lost simply by doing a routine O/S upgrade? Rolling back the upgrade would make more sense, but I *thought *that this was a forum where more experienced people than me could offer simple advice to resolve the problem. I guess that doesn't apply to everyone.

---

### Post by TheFu on 2023-03-15
> **ianmanning said:**
> $50k to restore a feature which was lost simply by doing a routine O/S upgrade? Rolling back the upgrade would make more sense, but I *thought *that this was a forum where more experienced people than me could offer simple advice to resolve the problem. I guess that doesn't apply to everyone.

When that's possible, it is the goal.  Sounds like you mistook my little pedantic joke. Of course, no home user would pay $50K to get something like this working. OTOH, I've known businesses where their process was so integrated with a specific feature that they spent $100K to resolve the problem ASAP.

If Morbius doesn't have a quick answer, I doubt anyone else here does.  Have you tried to get MSFT to help?  After all, they are 50% of this issue.

I'm not a samba expert and don't use Lubuntu or Windows10/11, but have been setting up samba since the mid-1990s both at home and at a few jobs when necessary.  [https://www.linuxbabe.com/ubuntu/install-samba-server-file-share](https://www.linuxbabe.com/ubuntu/install-samba-server-file-share) seems to have the most complete installation instructions that address most of the common issues along the way. I've not needed anything so complex for my smb 2.1 clients.
```
sudo nmap --script smb-protocols 172.22.22.6
...
Host script results:
| smb-protocols: 
|   dialects: 
|     2.10
|     3.00
|     3.02
|_    3.11

```
shows that my samba server on 172.22.22.6 supports those specific smb versions.  Win10 supports smb version 3.00, BTW. 

A similar question was asked and answered here: [https://askubuntu.com/questions/1236510/i-cant-access-my-samba-shares-ubuntu-server-20-04](https://askubuntu.com/questions/1236510/i-cant-access-my-samba-shares-ubuntu-server-20-04)  Seems using NT1 as the protocol was the highest voted answer, but a few others posted other things to try.  Hard to know if those other proposed answers actually matter or not. Can't hurt to try, assuming to keep careful backups of all attempts.  Seems something around samba requires a full reboot between some changes, so restarting the smbd and nmbd dæmons isn't always sufficient. Hard to known when it is and isn't required.

Complaint rant:
Routine upgrades aren't always routine.  Things change which are outside our control.  For example, MS-Win10 changed many things about the CIFS protocol used over the last few years.  That's outside our control.  They didn't ask you or me for our approval.  The entire CIFS protocol implementation on all Unix-like OSes is reverse engineered. To be clear, the recent CIFS changes for better security and improved performance are generally an overall "good" thing, but the migration could have been more clearly planned with teams outside MSFT.
For a few decades, MSFT provided ZERO help to make CIFS/Samba work.  I vaguely recall they helped the Samba project about a decade ago with some things.
[https://www.zdnet.com/article/microsoft-steps-on-sambas-toes-5000122696/](https://www.zdnet.com/article/microsoft-steps-on-sambas-toes-5000122696/) from 2002.
[https://www.computerworld.com/article/2734095/microsoft-s-samba-contribution--a-genuine-open-source-overture-.html](https://www.computerworld.com/article/2734095/microsoft-s-samba-contribution--a-genuine-open-source-overture-.html)

For about the last 5 yrs, MSFT hasn't been nearly as nasty, but they still are a little secretive on many topics which make integrations harder than necessary.  Maybe they will be more team players in the future?  Hard to say. Most users are stuck dealing with the fallout.

BTW, nobody here works for Canonical and Canonical isn't the team running or coding the Apache Samba project.  Perhaps the installed defaults could have been better, IDK.  Whenever I've had CIFS connectivity issues, the fix was always on the MSFT platforms, not Linux.

---

### Post by Morbius1 on 2023-03-16
Before you start to reinvent the wheel:
> **ianmanning said:**
> ..... Previously I was able to browse a list of shares on this machine from a Windows 10 machine on the same subnet, by typing the IP address into File Explorer. Following the update, I get an error if I do this - **[COLOR="#FF0000"]I need to enter a share name[/COLOR]**. If I enter the IP address only it fails to connect.

Samba isn't broken. You can still connect to the shares on your Linux samba server from Win10.

Do you have that many shares that you cannot "map the network drives" or even "pin to Quick Access" the shares to explorer in Win10?

---

