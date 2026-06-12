---
title: "Ubuntu 14.04 Desktop, Samba Local Name Resolution Issue"
date: 2016-05-14
forum: Networking &amp; Wireless
---

### Post by mike430 on 2016-05-14
Hi all. Thanks in advance for considering my inquiry. 

I am running Ubuntu 14.04 which I use as a media server and has been accessible by host name through other windows and linux pc's on my small lan by way of samba. Today I changed my ip from dynamic to static using network manager. After having done this my network access to my Ubuntu media server allows access only by way of ip or host.local. Unfortunately, this server is no longer visible on the network from other machines (both linux and windows), but is accessible by ip or host.local only. 

I have been reading many user solutions to this problem however have been unsuccessful in resolving this. 

My setup is simple I have four machine 2 windows and 2 linux and an asus router that runs my dhcp and dns. I point through network manager to my router for the dns service. In auto dhcp mode it works fine but in static mode I get this odd behavior.

Thank you in advance for any input.

vcandy

---

### Post by bab1 on 2016-05-14
> **mike430 said:**
> Hi all. Thanks in advance for considering my inquiry. 

I am running Ubuntu 14.04 which I use as a media server and has been accessible by host name through other windows and linux pc's on my small lan by way of samba. Today I changed my ip from dynamic to static using network manager. After having done this my network access to my Ubuntu media server allows access only by way of ip or host.local. Unfortunately, this server is no longer visible on the network from other machines (both linux and windows), but is accessible by ip or host.local only. 

I have been reading many user solutions to this problem however have been unsuccessful in resolving this. 

My setup is simple I have four machine 2 windows and 2 linux and an asus router that runs my dhcp and dns. I point through network manager to my router for the dns service. In auto dhcp mode it works fine but in static mode I get this odd behavior.

Thank you in advance for any input.

vcandy
Samba doesn't directly use DNS or hosts for name resolution.  What it *may* do is refer to the hostname you have defined in the /etc/hosts file to convert to a NETBIOS name.  If this is wrong then Samba won't work correctly.  Because there are so many variables it's best to look at the configuration rather than guess at what is the problem.

Post the output of these commands from the Ubuntu command line(the # lines are my comments)```

# list the samba processes
pgrep -l mbd

# display the hosts file configuration
cat /etc/hosts

# display the network shares and debug info
smbtree -d3

# display the Samba server configuration
cat /etc/samba/smb.conf

```

Please post the text output using [noparse]```
  
```[/noparse] code blocks.  This preserves the text formatting and makes the output easier to read.  The easiest way to do the is to click on the [SIZE=5]**#**[/SIZE] icon and pasting the text between the blocks.

---

