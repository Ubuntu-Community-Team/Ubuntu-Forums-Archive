---
title: "Can't get Samba to work"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by Chetamonye on 2006-10-26
Hello.  I hope someone can help me.  I am using Kubuntu on three computers.  I would like to access each computer from one of the others.  

When I go to "Remote Places", I select Samba Shares and I get the following error.  "**Unable to find any workgroups in your local network.  This might be caused by an enabled firewall**". 

I don't think I am running a firewall(I didn't set one up).  Can anyone suggest what I might try to fix this?

Is there documentation on setting this up?  

Thanks in advance

Chet

---

### Post by featherking on 2006-10-26
Not sure about kubuntu if there is a different firewall manager, but you could try install firestarter and use it as a gui for iptables(the built in ubuntu firewall run from the command line) also check the /etc/samba/smb.conf file for samba configuration parameters.

For more info on smb.conf check its man page
```
man smb.conf
```

---

### Post by dbott67 on 2006-10-26
There is a [HOWTO on setting up Samba]("http://ubuntuguide.org/wiki/Ubuntu_dapper#Samba_Server") in the Wiki.  First, you need to install Samba & smbfs:
```
sudo apt-get install samba smbfs
``` 

The Wiki is very detailed & has all the necessary steps.

BTW, if you want the 'quick & easy way' take a look at this thread:

[http://www.ubuntuforums.org/showpost.php?p=1662947&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1662947&postcount=8)

-Dave

---

