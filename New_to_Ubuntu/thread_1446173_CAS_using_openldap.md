---
title: "CAS using openldap?"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by koba101 on 2010-04-03
hi,

I've got 5 ubuntu workstations where I want to provide a central authentication service  to provide scalability. 

I'm considering Openldap, though I'm not sure whether or not it is the right choice.  

what i'm trying to do is the following:  setup an e-mail server on one workstation, a file server on another, and an ssh server on the third.  Though I'd like all of them to have the same credentials.  That's why i want to centralize the accounts.


Any feedback?

---

### Post by Gone fishing on 2010-04-03
Openldap sounds good to me.

Curious why you are splitting the services between the work stations so much rather than say running openldap server and nfs server on the same box?

this page might be helpful [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

Personally I used Opensuse as an openldap server and used this guide and it works just fine

[http://www.urbana.fm/~antocm/ldap-samba-howto-v4.html](http://www.urbana.fm/~antocm/ldap-samba-howto-v4.html)

---

### Post by koba101 on 2010-04-04
no reason at all...in fact logically i should place them in the same server....i'm curious how you integrated ubuntu clients to your opensuse server

---

### Post by Gone fishing on 2010-04-04
Well that&#8217;s been a little bit of a debate between me and Techie at the Prep school (I'm the Upper school). So let me tell the story ...

I had an Opensuse server but without LDAP running samba nicely etc. The prep school Techie decided to go completely Linux for the prep school (good decision) and I wanted to increase the Linux workstations - we first went for a completely Ubuntu solution - Ubuntu server running, Opendap, NFS, Squid, Postfix, with Ubuntu ldap clients and /home nfs mounted on the server. However, the Ubuntu server (Hardy) wasn't particularly stable NFS crashed a lot (it seems that this might have been to do with the default number of threads that NFS server uses which was ridicules - 4 comes to mind in needs to be about 30 in our case (I'll see if I can remember how to change or find a link on this). Anyway it crashed we and then we bust it good and properly.

After experimenting with Debian Lenny - which we couldn't get to work properly, I suggested we went full geek and tried FreeBSD or we whimped out and tried Opensuse we went for Opensuse, it took half the time to set up as Ubuntu (although postfix was a bit of a pain) and was stable although the thread thing still needed changing.

The prep school then continued with ldap client authentication on the Ubuntu workstations - which worked exactly as it had done with the Ubuntu server (we found the nolock option on the nfs clients to be a good idea). I went for Opensuse workstations as setting up ldap clients on the is literally ticking a box and clicking a button, nfs mount the same. In Ubuntu its a little more involved (I'll ask the prep school techy to give me a link)

My opinion is that the Ubuntu workstations are a little quicker - a little nicer to use tend to be less of a pain in the **** than the Opensuse workstations - but it is nice just to click a button.

Edit the thread thing was editing (in Opensuse I think it's the same in Ubuntu) /etc/sysconfig/nfs and changing USE_KERNEL_NFSD_NUMBER="4" to something more reasonable although in your case 4 should be enough

---

