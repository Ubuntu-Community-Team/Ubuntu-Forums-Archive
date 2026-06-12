---
title: "Guidebooks on server security"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by p_quarles on 2007-07-12
I'd like to use my home server to host a small, low-traffic personal home page (resume, stuff like that). I have it set up to do that already, but public access is disabled. 

Anyway, I've done all the basic security things I've found in the tutorials around here (Bastille, disabling root login, automated security updates, etc.), so I'm guessing it's pretty secure as it is.

That said, I'd rather do more than guess. If anyone could recommend a good and reliable guidebook to security (either a GFDL e-book or a "real" book), I'd very much appreciate it.

My main concern, for what it's worth, is that I would like to continue to use the server as a space for backup files, and that's something I absolutely don't want compromised. I imagine a relatively secure setup could be accomplished by encrypting the backup files, and I already know how to do that. I'm just looking for a good, relatively high-level discussion of the issues so that I can understand exactly what I'm doing before I take any risks. 

Thanks.

---

### Post by 1/0 on 2007-08-05
Well, as they say, there is no thing as secure so just forget about it... There are tonnes of things to do if you want to be less vulnerable. In my case backing up the homepage is the most important since I've deleted stuff several times by mistake when updating mysql. If you are the only person to access the server, try non standard ports. 

A solid hardware firewall is much recommended. Smoothwall or M0n0wall are good. There are many others. Once the firewall is up, you can start focusing on securing the server itself. Bastille is good for that purpose. 

As for books. First, here's a short list of easy things to do:

[http://kevin.hatfieldfamilysite.com/?p=147](http://kevin.hatfieldfamilysite.com/?p=147)


O'Reilly has some good books such as:

[http://www.greendiamond.dsskcorp.com/gdi/Books/Linux.Security.Cookbook.pdf](http://www.greendiamond.dsskcorp.com/gdi/Books/Linux.Security.Cookbook.pdf)

[http://lug.git.ac.in/lib/network.pdf](http://lug.git.ac.in/lib/network.pdf)


Tldp as well:

[http://www.tldp.org/LDP/solrhe/Securing-Optimizing-Linux-The-Ultimate-Solution-v2.0.pdf](http://www.tldp.org/LDP/solrhe/Securing-Optimizing-Linux-The-Ultimate-Solution-v2.0.pdf)


This site has some interesting stuff:

[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)


I hope that's a good start for you!

---

### Post by p_quarles on 2007-08-05
Hey, thanks for the recommendations. I have downloaded/bookmarked all of them, and they do look useful, particularly the "Security Cookbook." 

And, yeah, I know that no system is ever completely safe ... the higher the wall, the higher the ladder, etc. I just want to make sure that I understand the issues well enough to know how high my wall is. :)

---

### Post by 1/0 on 2007-08-06
*"the higher the wall, the higher the ladder"* LoL

Glad it helped you. I just saw that the link to the list doesn't point to the list, if you get what I mean. Just search for: 28 Steps on how to harden your Linux server

on: [http://kevin.hatfieldfamilysite.com/?p=147](http://kevin.hatfieldfamilysite.com/?p=147)

---

### Post by Robynsveil on 2007-08-06
Hi,
I just got on one of the [above sites]("http://www.itsecurity.com/features/ubuntu-secure-install-resource/"), and have some questions about the suggestions given there for those who might have a clue about what these actually do - the author didn't explain that bit. to wit:
> 
Modifying Default Settings
The first set of basic critical changes requires you to modify three insecure default system settings:
    * Reconfiguring shared memory
      Load your favorite text editor, open the file "/etc/fstab" and add the following line of code:
      tmpfs /dev/shm tmpfs defaults,ro 0 0

    * Disabling SSH root login
      Load your favorite text editor, open the file "/etc/ssh/sshd_config" and add change the following line of code:
      PermitRootLogin yes
      to
      PermitRootLogin no

    * Limiting access to the "su" program
      Open the terminal by clicking "Applications" selecting "Accessories" and choosing "Terminal." From there enter the commands:
      sudo chown root:admin /bin/su sudo
      chmod 04750 /bin/su

My experience when trying to implement these suggestions was:
--My '/etc/ssh/sshd_config' file had nothing in it... so I just added the 'PermitRootLogin no' statement and saved it. Worries me, though. (If a little knowledge is a dangerous thing, doing this sort of stuff without understanding it as a neophyte can be downright catastrophic!) Oh, and I did open the '/etc/ssh/sshd_config' using sudo.
--When I did the 'sudo chown root:admin /bin/su sudo' (copy and pasted from the article into Terminal) I got:
```
sudo chown root:admin /bin/su sudo
chown: cannot access `sudo': No such file or directory

```
Obviously the sudo parameter at the end of the statement is the problem, or is it? No way to know. I 'man'ned chown and it didn't appear to include sudo in its list of paramaters - besides, parameters appear to be prefixed with a /.

---

### Post by p_quarles on 2007-08-06
If there's nothing in /etc/ssh/sshd_config, that probably means you don't have OpenSSH-server even installed, and thus there's really no reason to disable root login.

As for limiting access to su, this is already the default setting in Ubuntu, so I imagine that the error you're seeing is reflecting this fact.

---

