---
title: "Networked computer fails to mount"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by mollydoggy1971 on 2009-11-02
I upgraded to Karmic Koala today.  Now I can't access my Windows network.  It sees the Windows machine, but when I click that machine, it says "Unable to mount location.  Failed to retrieve share list from server."  Why is it doing this, and how do I make it work?  I know NOTHING about Linux, so please give me any help in the manner you would to a small child.  I don't know how to mount things, I don't know how to use command line stuff, I know virtually NOTHING.  I thank you in advance for your help.

---

### Post by TheForumTroll on 2009-11-02
In a console try this:
```
findsmb
```

This will list anything your PC can see on the network.

Like on mine I get this output:
```
                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.100   SERVER        +[WORKGROUP] [Unix] [Samba 3.3.2]

```

---

### Post by mollydoggy1971 on 2009-11-02
> **TheForumTroll said:**
> In a console try this:
```
findsmb
```

This will list anything your PC can see on the network.

Like on mine I get this output:
```
                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.100   SERVER        +[WORKGROUP] [Unix] [Samba 3.3.2]

```

When I do that, I get the following (I hope it comes out right) - 

mollydog@Ubuntu-PC:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.101   UBUNTU-PC     +[WORKGROUP] [Unix] [Samba 3.4.0]
mollydog@Ubuntu-PC:~$ 

How is the Windows machine not in that thing, but it is under the Network button, even though it's not accessible?  And how do I see it?

---

### Post by TheForumTroll on 2009-11-02
You could try this:

```
smbclient -L NAME
```

Exchange NAME with the name of the machine. It will list any shares it can see.

---

### Post by jaycee23 on 2009-11-02
I had the same problem - before you go down the various complicated solutions you will find on these pages - try turning off the firewall.

UFW is installed as default on 9.10.

It is fairly easy to change but I would recommend getting the GUI

You can get "gufw" (the GUI) from Synaptic.

You can then configure the firewall from System - Admin - Firewall Config.

Where it says Enabled take out the check so the firewall is turned off and then try connecting to the Windows Network.

If that works post back - otherwise you may have to try the complicated stuff

Good Luck

---

### Post by mollydoggy1971 on 2009-11-02
> **jaycee23 said:**
> I had the same problem - before you go down the various complicated solutions you will find on these pages - try turning off the firewall.

UFW is installed as default on 9.10.

It is fairly easy to change but I would recommend getting the GUI

You can get "gufw" (the GUI) from Synaptic.

You can then configure the firewall from System - Admin - Firewall Config.

Where it says Enabled take out the check so the firewall is turned off and then try connecting to the Windows Network.

If that works post back - otherwise you may have to try the complicated stuff

Good Luck

I did that, and the firewall was not, and is not, on.  Complicated stuff, here I come!

---

### Post by mollydoggy1971 on 2009-11-02
> **TheForumTroll said:**
> You could try this:

```
smbclient -L NAME
```

Exchange NAME with the name of the machine. It will list any shares it can see.

I did this, with the following result - 

mollydog@Ubuntu-PC:~$ smbclient -L mollydog-pc
Enter mollydog's password: 
Domain=[MOLLYDOG-PC] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

	Sharename       Type      Comment
	---------       ----      -------
Error returning browse list: NT_STATUS_NOT_SUPPORTED
Domain=[MOLLYDOG-PC] OS=[Windows 7 Ultimate 7600] Server=[Windows 7 Ultimate 6.1]

	Server               Comment
	---------            -------

	Workgroup            Master
	---------            -------
mollydog@Ubuntu-PC:~$ 


I have no idea what that means.

---

### Post by TheForumTroll on 2009-11-03
According [to this thread]("http://ubuntuforums.org/showthread.php?t=1295659") this is a Samba/Windows 7 problem. I do not know the cause though. Did you try to turn off the firewall in Windows?

It does seem that it is possible to access shares as long as you know their names. I would guess using Places -> Connect to server (think that's its name in English) and choosing Windows share you could connect even though it is not an optimal solution.

---

### Post by mollydoggy1971 on 2009-11-03
> **TheForumTroll said:**
> According [to this thread]("http://ubuntuforums.org/showthread.php?t=1295659") this is a Samba/Windows 7 problem. I do not know the cause though. Did you try to turn off the firewall in Windows?

It does seem that it is possible to access shares as long as you know their names. I would guess using Places -> Connect to server (think that's its name in English) and choosing Windows share you could connect even though it is not an optimal solution.

I'll check out that thread.  Thanks.  My firewalls are off on both computers.  I'm so very lost when it comes to new things in Linux...I've been a reluctant Windows user for many years, and I've become accustomed to the way they do things, so this Linux experience has been challenging for me...although also fun when I finally get things to work!

---

### Post by Peter09 on 2009-11-03
This mogt be worth a try. 
First edit the nsswitch.conf file
```
sudo gedit /etc/nsswitch.conf
```
and add make the hosts line look like
> hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

next install winbind

```
sudo apt-get install winbind
```

This makes sure that your windows shares are identified by name.

---

