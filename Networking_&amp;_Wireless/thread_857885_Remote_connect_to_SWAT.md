---
title: "Remote connect to SWAT"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by hornetster on 2008-07-13
Hi, wondering how you can remotely connect to SWAT, on the same subnet, but from a different PC? It will only let me login as a user (root doesn't exist), and the user doesn't have any editing rights...
Thanks, John

---

### Post by Marsupilami23 on 2008-07-24
Might want to explain a bit more... have you added the root user on the Samba machine?

[HTML]smbpasswd -a root[/HTML]

---

### Post by bab1 on 2008-07-24
I'm not 100% sure on this and I'm not near a samba server to check, but I believe there is a setting to allow the use of SWAT on a local network.  Look in the config file for a reference to "localhost" for the correct changes.

---

### Post by Joonstar on 2011-02-12
I have been trying to figure this out all week now, and am super stuck

I have the new ububtu server 10.10 and did apt-get samba and swat. I'm on a private LAN and i'd like to use swat to setup samba. Ubuntu server is just and only a command line shell. Ubuntu server is on a small machine running in the corner with only power and  a network cable going to it I access the shell via ssh.

Now i boiled it down to that one option in the swat.conf file in the xinetd folder. The problem is i dont have xinetd, i have inetd which is really really different. 

I found a file called swat in /usr/sbin when i try to edit it it comes out as jargon so im thinking it in binary or something.

when i type just swat, i get an alarm clock error yet i can access swat using my linux username and pword, but i dont get and admin options. When i try to login as root it simply wont go.

I tried    sudo smbpasswd -a root nothing seemed to happen

so im thinking it all about finding that one option that only lets the admin login from the localhost.

I appoligize if the nswer is obvious a week ago i never touched linux before :)

---

