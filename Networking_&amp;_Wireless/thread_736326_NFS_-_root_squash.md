---
title: "NFS - root_squash"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by akks on 2008-03-26
Hi all,
  can anyone tell me the options root_squash and all_squash. i read the man page and  i am still confused.  root_squash means the root user on the client system will be mapped to anonymous id? Does this mean that any operation requiring super user privilages on the exported directory to the client machine will be denied?  Please help me clarify my doubt.

---

### Post by Eiríkr on 2008-03-26
If memory serves, yes, [font=courier]root_squash[/font] means you can't do any sudo-ing on the NFS share.  I dimly recall running into this when setting up my own NFS shares and wondering why I couldn't sudo to access various things my own user ID didn't have permission to do, and so I added the [font=courier]no_root_squash[/font] option to my [font=courier]/etc/exports[/font] file to fix this.  The [font=courier]all_squash[/font] option, meanwhile, maps *everyone* to the guest ID.  

HTH,

Eiríkr

---

### Post by akks on 2008-03-27
Yes exactly as i thought. Does NFS provide any authentication mechanism? i mean for example. as with FTP we can allow only valid user to download files by an authentication mechanism ( user_id and password). Is it possible in NFS? 

what i want to know is this:
suppose i have given a permission to a remote machine to mount a directory from my system. Say for example the rule i have written in /etc/exports is this:

/temp 192.168.1.33(rw). 

Now any user logged in on to 192.168.1.33 would run a mount command and mount my director on to that system. i want to know is there a way in NFS to say that user A on 192.168.1.33 can mount my directory while user B cannot. Hope i have stated my problem clearly.

---

### Post by akks on 2008-03-27
Is it possible to use PAM with NFS??

---

### Post by Eiríkr on 2008-03-27
As I understand it, yes, as you note, 

> any user logged in on to 192.168.1.33 would run a mount command and mount my directory on to that system

... however, they would have the *same* permissions on that mounted directory that they would have if they used the same UID on your machine locally.  

I have a common [font=courier]/data[/font] directory that includes various users' document directories and that I export over NFS to my two iBooks.  While iBook A can see user B's doc directory, and iBook B can see user A's, neither can *open* the other's directory because they don't have the needed permission.

That said, this is a pretty rudimentary setup.  Looking at [font=courier][man exports]("http://linux.die.net/man/5/exports")[/font] shows us:
> **RPCSEC_GSS security**
To restrict access to an export using rpcsec_gss security, use the special string "gss/krb5" as the client. It is not possible to simultaneously require rpcsec_gss and to make requirements on the IP address of the client.

Meanwhile, [font=courier][man nfs]("http://linux.die.net/man/5/nfs")[/font] says:
> *sec=mode*
    Set the security flavor for this mount to "mode". The default setting is sec=sys, which uses local unix uids and gids to authenticate NFS operations (AUTH_SYS). Other currently supported settings are: sec=krb5, which uses Kerberos V5 instead of local unix uids and gids to authenticate users; sec=krb5i, which uses Kerberos V5 for user authentication and performs integrity checking of NFS operations using secure checksums to prevent data tampering; and sec=krb5p, which uses Kerberos V5 for user authentication and integrity checking, and encrypts NFS traffic to prevent traffic sniffing (this is the most secure setting). Note that there is a performance penalty when using integrity or privacy.

Hope this helps,

Eiríkr

---

### Post by akks on 2008-03-28
This means that if sec=sys then, all users will be authenticated on their uid's and gid's right.. which is all we want. So we dont have to worry about security..

---

