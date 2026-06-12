---
title: "Cannot access Samba server on NAS"
date: 2020-04-04
forum: Networking &amp; Wireless
---

### Post by Jeff-cao on 2020-04-04
Hi folks,

I just installed Kubuntu 20.04 yesterday. Everything is awesome. Pretty much all of my function keys are supported out of the box, volume, brightness, mic, middle button. It even promotes a BIOS update in Discovery which never happened before. I have no idea how Kubuntu can check for BIOS update. :p

Anyway, The only thing I cannot solve after two-plus hours searching is that I cannot access files stored in my NAS. I use the NAS to stream movies basically. In Windows or other distributions, I just open the file manager, go to the network and the NAS server is right there. I can see the server N5550 in Dolphin->Network, but when I double click on it, it says the connection to n5550.local is interrupted. Any idea how to fix it? I have installed samba and samba-client I even set up an smb server on this laptop following one post :p which obviously not my intention. 

A few pictures to help you understand. Thanks in advance.

[ATTACH=CONFIG]285390[/ATTACH][ATTACH=CONFIG]285391[/ATTACH][ATTACH=CONFIG]285392[/ATTACH]

---

### Post by SeijiSensei on 2020-04-04
Try this.  Open Dolphin, then go to the address bar and type "smb://username@ip.addr.of.NAS", e.g, "smb://jeff@192.168.1.100".  You should be prompted for a password if needed.

If the NAS supports NFS or SSHFS, those are easier to use on *nix systems than SMB/CIFS which is a Windows protocol.

See: [https://www.politicsbythenumbers.org/images/dolphin-smb.png](https://www.politicsbythenumbers.org/images/dolphin-smb.png)

---

### Post by Jeff-cao on 2020-04-05
> **SeijiSensei said:**
> Try this.  Open Dolphin, then go to the address bar and type "smb://username@ip.addr.of.NAS", e.g, "smb://jeff@192.168.1.100".  You should be prompted for a password if needed.

If the NAS supports NFS or SSHFS, those are easier to use on *nix systems than SMB/CIFS which is a Windows protocol.

See: [https://www.politicsbythenumbers.org/images/dolphin-smb.png](https://www.politicsbythenumbers.org/images/dolphin-smb.png)

Thanks for your reply. I tried smb://jeff@192.168.1.100 but it doesn't work. 

I enabled NFS service on the NAS, and mounted the folder to /home/jeff/N5550, but wasn't able to open the folder. I even tried to login as root in Konsole and it says no permission for access. Any idea? Thanks in advance.

```
jeff@jeff-ThinkPad-X1-Carbon-7th:~$ sudo mount -t nfs 192.168.1.12:/raid0/data/_NAS_NFS_Exports_ /home/jeff/N5550
[sudo] jeff &#30340;&#23494;&#30721;&#65306; 
jeff@jeff-ThinkPad-X1-Carbon-7th:~$ cd /home/jeff/
jeff@jeff-ThinkPad-X1-Carbon-7th:~$ ls
&#20844;&#20849;&#30340;  &#27169;&#26495;  &#35270;&#39057;  &#22270;&#29255;  &#25991;&#26723;  &#19979;&#36733;  &#38899;&#20048;  &#26700;&#38754;  N5550
jeff@jeff-ThinkPad-X1-Carbon-7th:~$ cd N5550
jeff@jeff-ThinkPad-X1-Carbon-7th:~/N5550$ ls
ls: &#26080;&#27861;&#25171;&#24320;&#30446;&#24405;'.': &#26435;&#38480;&#19981;&#22815;
jeff@jeff-ThinkPad-X1-Carbon-7th:~/N5550$ su
&#23494;&#30721;&#65306; 
root@jeff-ThinkPad-X1-Carbon-7th:/home/jeff/N5550# ls
ls: &#26080;&#27861;&#25171;&#24320;&#30446;&#24405;'.': &#26435;&#38480;&#19981;&#22815;
root@jeff-ThinkPad-X1-Carbon-7th:/home/jeff/N5550# 
```

---

### Post by Jeff-cao on 2020-04-05
> **SeijiSensei said:**
> Try this.  Open Dolphin, then go to the address bar and type "smb://username@ip.addr.of.NAS", e.g, "smb://jeff@192.168.1.100".  You should be prompted for a password if needed.

If the NAS supports NFS or SSHFS, those are easier to use on *nix systems than SMB/CIFS which is a Windows protocol.

See: [https://www.politicsbythenumbers.org/images/dolphin-smb.png](https://www.politicsbythenumbers.org/images/dolphin-smb.png)

upgraded the os on the NAS, and can access it now. Seems like it is a SMB version problem. Thanks anyway for your help!

---

