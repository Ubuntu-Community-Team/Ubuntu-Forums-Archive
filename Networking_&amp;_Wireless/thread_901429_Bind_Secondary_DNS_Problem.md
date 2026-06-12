---
title: "Bind Secondary DNS Problem"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by gkaragoulis on 2008-08-26
I have my Ubuntu secondary DNS server setup to be a slave to my Windows Server 2003 AD-integrated DNS, but it won't transfer the DNS entries to it.  I keep getting this error in syslog:
```
Aug 26 12:17:31 Linux-DNS named[6663]: dumping master file: /slave/tmp-tfnWjQmLsb: open: permission denied
Aug 26 12:17:31 Linux-DNS named[6663]: transfer of 'mydomain.com/IN' from 192.168.1.3#53: failed while receiving responses: permission denied

```

I have checked and double-checked my permissions on everything, and even opened it all wide open with 777 permissions (I even recursively 'chmod'ed the / directory 777 just to make CERTAIN I covered everything...still permission denied...).  I tried running 'named' as 'root' but I get the same errors and it never transfers.  I'm not chrooting it yet, because I can't even get it to work normally.

Can somebody please help me with this? I've already spent a couple days troubleshooting this, and yes, I have googled this time and time again but nobody has my exact problem; all the ones I've found have to do with file permissions, and I'm almost certain mine doesn't for the reasons stated above.

---

### Post by jigsaws on 2008-08-26
Maybe bind want to write other directory than you think?
Is your Ubuntu's IP configured as a slave at Windows?
Do you use selinux?

---

### Post by gkaragoulis on 2008-08-26
Well, I think I covered all the directories by doing:
```
sudo chmod 777 / -R
```
NOT A GOOD IDEA BY THE WAY! I only did it because it's a VM and I have backups!

And still no luck, still the same permission denied.

I believe I have it configured correctly from the windows side.  If windows was rejecting me though I think I'd get a different error message.  Probably something like "CONNECTION REFUSED" or something.  But the logs say that a connection is made and it's trying to transfer, it just gets permission denied...

I don't think I'm using selinux...it's just the regular Ubuntu Desktop I installed from an ISO.

---

### Post by jigsaws on 2008-08-26
I'm sure the second message means that primary DNS don't allow transfer. It's permision denied not connection refused - you can connect to the primary, but got transfer refuse.

I don't know how to correct it in Windows server. In Bind config it can be made by "allow-transfer { IP; };"
Try to correct this at Windows side and maybe first problem also solves...

---

### Post by gkaragoulis on 2008-08-26
Thanks jigsaws, I really appreciate your help, but it is not the Windows 2003 server.  I have enabled logging and Windows is telling me multiple times that it "successfully" completes each transfer to my secondary DNS.

Does the Primary try to write to my Ubuntu Secondary as the 'bind' user?  Again, it shouldn't matter the user because everything is 777 permissions...literally EVERYTHING under '/'...How then can I get permission denied?

Does it mean anything if I say that the Windows 2003 DNS is Active Directory integrated?  I wouldn't think so because it's not Windows who is denying me, it's my Linux machine...Do acl's screw up bind permissions?  I'm just reaching in the dark now...

---

### Post by jigsaws on 2008-08-26
Wait a moment. I have a stupid idea. Set your slave directory owner to named:named (or bind user you set) and the rights to drwxrwx--- for directory and -rw-rw-r--- for files. The most important is file owner. Maybe, paradoxical, named check if files does have secure permissions and "access denied" is stupid error? Then restart named.

If not, I don't belive Windows "success logs" ;-)

And once more: show zone definitions at slave server. Maybe problem is that directory does not exists? Are there no "/" at the begining?

---

### Post by jigsaws on 2008-08-26
Two more stupid questions:
You have no quota or full filesystem?
There are no firewall?

---

### Post by dundee5 on 2009-02-20
It is probably wrong configuration of AppArmor


So solution is:

sudo service apparmor stop

---

