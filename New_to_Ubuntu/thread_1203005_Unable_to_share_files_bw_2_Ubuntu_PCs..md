---
title: "Unable to share files b/w 2 Ubuntu PCs."
date: 2009-07-02
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-07-02
Hi everyone,

I have two computers with Ubuntu installed on them. I have a network set up between them that looks like this:

Laptop ---> Ethernet Cord ----> Desktop
Both computers are running on "link-local only" configuration, "connect automatically" and "available to all users" under the Network Configuration Window. 

This configuration used to work before I wiped the hard drive on my laptop. 

**I can see my shared music folder in Rhythmbox. DAAP seems to be working fine. 

So why aren't my shared folders visible in nautilus? Samba is installed.

Thanks for any help in advance. ;)

---

### Post by ubudog on 2009-07-03
How old is the laptop and the desktop?

---

### Post by superprash2003 on 2009-07-03
did you configure samba? post output of smbtree from the terminal of both pcs

---

### Post by asuastrophysics on 2009-07-05
Laptop is around 6 months old: Acer Aspire 4720Z 

Desktop is about 2 years old: Custom PC: ECS Elitegroup MB AMD Athlon 3800+ 64-bit. 2GB RAM 500GB hdd

---

### Post by philcamlin on 2009-07-05
yes i would go with samba

---

### Post by asuastrophysics on 2009-07-05
This is the output of smbtree:
```
girdy@girdy-laptop:~$ smbtree
Password: 
girdy@girdy-laptop:~$ 

```

I basically don't get anything. How do I go about configuring samba? I think it worked right out of the box last time. Anyone know how?

thx ;)

---

### Post by LewRockwell on 2009-07-05
I have no idea whether this will help you specifically but it might be food for thought:

[http://www.linuxplanet.com/linuxplanet/tutorials/6497/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6497/1/)

.

---

### Post by asuastrophysics on 2009-07-05
**Update**

Here is the output of smbtree:
```
girdy@girdy-laptop:~$ sudo smbtree
[sudo] password for girdy: 
Password: 
WORKGROUP
	\\GIRDY-LAPTOP   		girdy-laptop server (Samba, Ubuntu)
		\\GIRDY-LAPTOP\music          	
		\\GIRDY-LAPTOP\pictures       	
		\\GIRDY-LAPTOP\documents      	
		\\GIRDY-LAPTOP\home           	
		\\GIRDY-LAPTOP\.themes        	
		\\GIRDY-LAPTOP\videos         	
		\\GIRDY-LAPTOP\installable programs	
		\\GIRDY-LAPTOP\Officejet-7300-series	HP Officejet 7300 series
		\\GIRDY-LAPTOP\IPC$           	IPC Service (girdy-laptop server (Samba, Ubuntu))
		\\GIRDY-LAPTOP\print$         	Printer Drivers
	\\GIRDY-DESKTOP  		girdy-desktop server (Samba, Ubuntu)
timeout connecting to 208.69.32.132:445
timeout connecting to 208.69.32.132:139
cli_start_connection: failed to connect to GIRDY-DESKTOP<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
girdy@girdy-laptop:~$ 

```

Hope that helps!

---

### Post by superprash2003 on 2009-07-06
your samba shares seem to be active now , have to tried accessing now?

---

### Post by asuastrophysics on 2009-07-07
I found the problem. I realised after your suggestion to type in "smbtools" that samba may not have been installed. I went into add/remove programs and checked "samba" to install it.

heh, I guess I was just being an idiot :rolleyes:

Everything works perfectly now, thanks a lot guys for your help! 
:guitar:

(I wish you could still mark threads as being solved)

---

