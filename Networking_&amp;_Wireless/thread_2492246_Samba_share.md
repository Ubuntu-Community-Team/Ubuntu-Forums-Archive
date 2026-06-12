---
title: "Samba share"
date: 2023-11-05
forum: Networking &amp; Wireless
---

### Post by rev03 on 2023-11-05
Hello,

I would like to share one linux folder and have access from W11 PC. I have Ubuntu server, running on Proxmox VM. I am new linux user and probably doing something wrog. Please can you advice me?

I do as follow:




[LIST=1]
[*]Install Samba
[/LIST]
```
[INDENT=2]
[LIST=1]
[*]**sudo apt-get update**
[*]**sudo apt-get install samba**
[/LIST]
[/INDENT]

```Seems, samba is running
[https://ibb.co/Jk2j5Gw](https://ibb.co/Jk2j5Gw)



2.) Set a password for me (my user name is rev)```
[INDENT]
[LIST=1]
[*]**sudo smbpasswd -a rev**
[/LIST]
[/INDENT]

```
3.) I set myself as owner and also allow for now all permissions: Folder I want to share is filmy
[https://ibb.co/8MGhxwc](https://ibb.co/8MGhxwc)




 
4.) Edit the file "/etc/samba/smb.conf"
```
**sudo nano /etc/samba/smb.conf**
```

I added to the end:
[https://ibb.co/ws4PGpL](https://ibb.co/ws4PGpL)



5.) I restarted samba:```
[INDENT]
[LIST=1]
[*]**sudo service smbd restart**
[/LIST]
[/INDENT]

```
[LIST=1]
[*]

**6.) Ping from my W11 PC to Ubuntru server is OK**

[https://ibb.co/xX1hwHR](https://ibb.co/xX1hwHR)





**7.) Trying to acces shared folder from W11 PC by Total Commander:**


[https://ibb.co/9txTnDy]("https://ibb.co/6PF7RCp")
[/LIST]


8.) Always got error message, windows not able to get access, network name unknown.
   - Seems I do not have right to access folder according to Windows.


[https://ibb.co/94MrLfW](https://ibb.co/94MrLfW)


Pleasse do you have idea, what I am doing wrong?

---

### Post by TheFu on 2023-11-05
Please don't use external links for relatively tiny files.  I have no idea where those lead and **will not click on them.**
When posting text here, please wrap that text in "code" tags, so the whitespace is retained. Often, for terminal/CLI commands, this will make it much more readable.  

Please don't make it hard to help you.

---

### Post by rev03 on 2023-11-05
Hello,

Originally, I posted all monitor screens here, but was over limit. So, I compressed all pictures but still over limit and in addition, was not readable in some cases.

All commands are in code tags from beginning. 

Sorry if I I angry you in some way, but I did my best to describe and post thread as best as I could.

---

### Post by SeijiSensei on 2023-11-05
On the Windows machine try to connect to \\ip.addr.of.server, e.g., \\10.10.10.10. It may be a name resolution problem.

---

### Post by rev03 on 2023-11-05
> **SeijiSensei said:**
> On the Windows machine try to connect to \\ip.addr.of.server, e.g., \\10.10.10.10. It may be a name resolution problem.


Hi,

thank you very much. That was it!

In all guides, I visited, there was written to always use whole path to shared folder.

Thank you one more time,
R.

---

