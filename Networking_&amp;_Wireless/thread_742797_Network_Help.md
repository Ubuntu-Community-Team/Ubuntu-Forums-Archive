---
title: "Network Help"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by cchester on 2008-04-02
Hey Guys,

I need help with networking I guess.

I have 3 computers with XP on them 2 are for my kids one for me and the other computers are Ubuntu 7.10 and a Vista Laptop.

I can't see any of the Xp computers the Ubuntu or the Vista computer no matter which computer I am using. I have sharing setup on all of them.

My 2 kids computers are using wireless cards and so is the laptop. My Xp computer and Ubuntu computer are plugged directly into my 2wire router.

On the first screen under network file browser in Ubuntu it shows an icon for Windows Network.

I click and open that and the page is blank. I am not sure what is going on in the past when I installed Ubuntu it would see the Xp computers no problem never the Vista Laptop.

So any thoughts? I don't think it makes a difference but the computer I use for Ubuntu and XP are connected by a KVM switch but I don't think it should make a difference right considering they are two seperate computers.

Thanks for any help.

---

### Post by dmizer on 2008-04-02
start by making sure all computers are members of the same workgroup.  doesn't matter what you use as your workgroup name, just as long as ALL computers are set the same.
xp: [http://www.leeindy.com/text_wkgrpnamechange.shtml](http://www.leeindy.com/text_wkgrpnamechange.shtml)
vista: [http://www.techduke.com/2007/06/25/changing-network-settings-in-windows-vista/](http://www.techduke.com/2007/06/25/changing-network-settings-in-windows-vista/)
ubuntu: right-click on your shared folder --> General Windows sharing settings --> (change the domain/workgroup name)

if that doesn't fix things, check firewall settings on all machines.

---

### Post by cchester on 2008-04-02
Thanks for the help.

Ok still having issues. I can see a couple of machines in Ubuntu which are shown in the attachment. My Ubuntu Machine and my daughters Xp machine. Strange thing is once I changed the workgroup name like you said I was able to see all machines just couldn't access my vista machine or my xp machine.

Under Vista I see no other machines on the network and under Xp when I try to browse the network I get that I might not have to right to use the resource.

So any other thoughts. Do I need to check my router? I have a Embarq 2Wire router. Could that be a problem?

Thanks for any more help.

---

### Post by Iowan on 2008-04-02
Firewalls on "missing" machines?

---

### Post by dmizer on 2008-04-02
you have a firewall problem.  firestarter on ubuntu?  vista has an internal firewall which can be a nightmare to navigate through.  xp also has a native firewall which has a tendency to turn itself back on after updates.  this is to say nothing of any other 3rd party software (norton internet security, mcafee internet security) firewall/antivirus you may have installed on xp or vista which (even when disabled or expired) can cause ceaseless headaches with file sharing.

---

### Post by cchester on 2008-04-02
> **dmizer said:**
> you have a firewall problem.  firestarter on ubuntu?  vista has an internal firewall which can be a nightmare to navigate through.  xp also has a native firewall which has a tendency to turn itself back on after updates.  this is to say nothing of any other 3rd party software (norton internet security, mcafee internet security) firewall/antivirus you may have installed on xp or vista which (even when disabled or expired) can cause ceaseless headaches with file sharing.

Thanks for the reply turning off Norton 360 Firewall made it so I can see my Ubuntu machine but when I try to browse it. It also made it so that I could see all my XP machines from Ubuntu and my see my Ubuntu machine from all my XP machines.

Still having a problem with Vista and all the machines. I turned off the Vista firewall. I can see the folders but it wants a password even though I have it set to not ask for one.

Thanks for anymore help.

---

### Post by dmizer on 2008-04-03
have you added your ubuntu user account to the samba group?

if not, try these commands:
```
sudo smbpasswd -L -a [COLOR="Red"]ubuntu_username[/COLOR]
sudo smbpasswd -L -e [COLOR="Red"]ubuntu_username[/COLOR]
```
(replace "[COLOR="Red"]ubuntu_username[/COLOR]" with your actual ubuntu user name)

i don't have vista, but depending on what version you have (home) you may not be able to map network drives, in which case it may never work properly.  i did a bit if light digging on google and didn't come up with any great answers.  so, if the above doesn't work for allowing your vista to view ubuntu shares, then i'm afraid you may have to work through this thread: [http://ubuntuforums.org/showthread.php?t=394412](http://ubuntuforums.org/showthread.php?t=394412) starting from _post 14_.

---

### Post by cchester on 2008-04-03
> **dmizer said:**
> have you added your ubuntu user account to the samba group?

if not, try these commands:
```
sudo smbpasswd -L -a [COLOR="Red"]ubuntu_username[/COLOR]
sudo smbpasswd -L -e [COLOR="Red"]ubuntu_username[/COLOR]
```
(replace "[COLOR="Red"]ubuntu_username[/COLOR]" with your actual ubuntu user name)

i don't have vista, but depending on what version you have (home) you may not be able to map network drives, in which case it may never work properly.  i did a bit if light digging on google and didn't come up with any great answers.  so, if the above doesn't work for allowing your vista to view ubuntu shares, then i'm afraid you may have to work through this thread: [http://ubuntuforums.org/showthread.php?t=394412](http://ubuntuforums.org/showthread.php?t=394412) starting from _post 14_.

Thanks your last post helped and everything is working. You've been a great help.

Thanks again.

---

### Post by dmizer on 2008-04-03
my pleasure.  glad you got it all working.

---

