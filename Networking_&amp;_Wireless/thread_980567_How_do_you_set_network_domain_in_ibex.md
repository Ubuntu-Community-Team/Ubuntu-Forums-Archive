---
title: "How do you set network domain in ibex?"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by Afkpuz on 2008-11-12
I used to know how to do this in hardy, but the network manager has changed in ibex.  How do I set my network domain in ibex?

---

### Post by maclin on 2008-11-13
do you know how to host a web site on ubuntu 8.4:):guitar::guitar:

---

### Post by maclin on 2008-11-13
...desktop distro?:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by Afkpuz on 2008-11-13
Yes, I'm running the desktop version of 8.10.  I'm not talking about internet domains.  I'm talking about when you have multiple domains on a wired network.  I need to specify which domain I am on so the correct network users can see my shared folders.

---

### Post by Afkpuz on 2008-11-15
Ok, I think I used the wrong word.  I meant workgroup.  How do you change/enter a network workgroup in ibex?

---

### Post by SteveDee on 2008-11-27
> **Afkpuz said:**
> Ok, I think I used the wrong word.  I meant workgroup.  How do you change/enter a network workgroup in ibex?

I have the same problem. On Hardy it was easy to change the workgroup from the default "workgroup" to (say) "ubuntu" using the graphical Network Connections dialog.

On Intrepid the Network Connections dialog is clearer (and wireless networking seems to work better) but there is no field for domain/workgroup.

Can someone advise how to view and edit this?

---

### Post by Afkpuz on 2008-11-29
I cannot verify this as I am away from my normal network (vacation), but I believe you can directly edit your samba conf file.  

It's located in /etc/samba/smb.conf

Look near the top for "workgroup".  Change that, save, and I guess log out and in?

---

### Post by J172 on 2008-11-29
Hey guys  Afkpuz was right on.
alright open terminal
***sudo gedit /etc/samba/smb.conf***
enter your password, press enter.
find the line "WORKGROUP"
```

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME
```
Change that to your workgroup.
Restart SAMBA
***sudo /etc/init.d/samba restart***

also you might want to backup the config before hand
***sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup***
restore by reversing the file names above.

Quick and dirty
Hope it helps.

---

