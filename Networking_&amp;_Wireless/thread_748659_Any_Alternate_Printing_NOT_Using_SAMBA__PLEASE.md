---
title: "Any Alternate Printing NOT Using SAMBA ??? PLEASE??"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by samtrevino on 2008-04-07
Need help with this issue. I am running Ubunutu 7.10. I am having the following constant and irritating random problem: 

Under  Places-->Network I lose the ability to see my MSHOME (or any computer on the network). However if I open up network and link directly to the ip of a computer I connect just fine, e.g. smb://192.168.1.2 and voila I can see shares and share files. This is not my issue, sharing I really don't care if my XP computer can see my linux machine and share files. Its nice that I can send files to my XP machine from my Linux Laptop, but I am really pissed that this issue keeps recurring regularly. If I can see my network and all computers on that network and then for no good reason (I didn't update or reboot or relog any computers) the network disappears. 

I've tried to work on this issue before when I ran Feisty (and my solution worked, but no joy now): 

[http://ubuntuforums.org/showthread.php?t=513601&highlight=lost+network+places](http://ubuntuforums.org/showthread.php?t=513601&highlight=lost+network+places)

I'm really getting at my wits end on this. Home networking should not be this complex or inconsistent. 

I have attempted to remove and reinstall all components of samba. That worked, but only once and within a few minutes I was back to not seeing my network and not being able to print. 

I want samba to work so I CAN PRINT DAMMIT! If there is another means of not using samba to print then by all means let me know. 

Rather than just create a huge list of outputs that may or may not be useful please let me know if a .conf or other file output is required for analysis  with  this issue. 

Thanks,

Sam

Here are some images:

---

### Post by Eiríkr on 2008-04-07
The problem is that XP's name resolution behaviour is itself buggy.  One workaround is to install the full **samba** package and configure your Ubuntu machine to be the authoritative Windows networking server, only not set up any shares (unless so needed), simply to have consistent behaviour.  I'd suggest the following simplified smb.conf file for such a setup (with Ubuntu solely as the client for any Windows shares, either for files or printers):
```
[global]
# Name resolution options
   netbios name = ubuntu
   workgroup = mshome
   name resolve order = wins lmhosts bcast
   wins support = yes
# Master browser options
   local master = yes
   domain master = yes
   preferred master = yes
# Network security options
   hosts allow = 127. 192.168.1.
   interfaces = 127.0.0.1/8 192.168.1.0/24
# Logging options
   log file = /var/log/samba/samba.log
   max log size = 1000
# User security options
   security = user
   encrypt passwords = yes
   obey pam restrictions = yes
   passwd program = /usr/bin/passwd '%u'
   passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
```

The keys here are the name resolution and master browser options.  This simplified setup should make your Windows network browsing more stable.

HTH,

Eiríkr

---

