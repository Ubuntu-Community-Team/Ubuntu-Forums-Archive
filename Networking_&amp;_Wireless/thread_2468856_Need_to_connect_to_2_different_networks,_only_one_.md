---
title: "Need to connect to 2 different networks, only one has internet"
date: 2021-11-12
forum: Networking &amp; Wireless
---

### Post by aeong on 2021-11-12
Hello! I'm a bit inexperienced with linux, so please treat me as a newbie here:

I need my Thinkpad T430 to connect to 2 different networks.

1. Connect wirelessly to a router I have with internet connection
2. Connect via LAN to a local area network so I can use this computer as an FTP server to send files to to very old computers that shouldn't be online.

I want to be on both of connections at the same time, but when I try to, I cannot use the internet anymore. Every online guide I've tried has not worked, so I'm hoping by getting help I can get something to work here.

---

### Post by TheFu on 2021-11-12
This is just subnetting.  Ensure that both subnets are different and use private LAN addresses.

Also, please don't use plain FTP - ever. There are many better answers.  So many better answers. Which would be best depends on the different clients involved. In general, **sftp** is the default answer. The **sftp-server** is part of the "ssh" package, which is necessary for all Unix-like OSes and Windows more and more.
```
**sudo apt install ssh fail2ban**
```
Then any client system can connect using any sftp client software you like to pull and push files.  Linux file managers use the sftp:// or ssh:// URL. From Windows, you can use the CLI or **WinSCP**.  There are plenty of methods for Android and OSX stuff too.  If you install **rsync** as well, you can use rsync+ssh to move entire directory structures between machines.  If you want a GUI, there is **grsync**.  rsync uses ssh tunnels and credentials automatically.  ssh is how computers are securely connected for all sorts of needs.  Setup ssh-keys (just 2 commands), and you have more convenience AND drastically more secure connections.  With any of the ssh-based tools using key-based authentication, this access doesn't need to be limited.  Back when travel was easy, I'd ssh into my home network from 5 continents to access, modify, delete files and to run a proxy connect or even a remote desktop if I was in a really not-so-secure part of the world and didn't want to bring anything sensitive on my minimal laptop.  I've traveled with just ssh access using debian (N800) and android tablets as well.

Friends don't let friends use plan FTP since ... er ... 2002.

---

