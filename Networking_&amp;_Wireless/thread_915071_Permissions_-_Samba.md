---
title: "Permissions - Samba"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by sombrancelha on 2008-09-09
Hi,

I just setted a connection up between my Hardy and a winXP. However, I had 2 problems.

1- (this problem was with the ubuntu shared folders)
I was having a problem that I couldn't edit the files created in the other computer, ie i couldn't edit, in windows, a file created in ubuntu and vice-versa. to solve this, I set (with sudo) the permissions for all users groups to read and write. But later I thought that this might not be a good idea. But now I don't know how to go back. So I've set it to read-only for everyone again, except for my user. But this, again, is not good, I guess. So, how can I set the permissions back to the default? And how can I make all files created inside this folder as read&write for both computers?

2 - (this problem was with the windows shared folders)
the other problem is that I can 'see' both computers in my network, but when I try to access it, it stays trying to connect for some time and then it shows nothing. I've accessed this computer through a vista pc and it's working fine. so i suppose the problem is with the samba/ubuntu.

hope I've been clear.

thanks in advance

---

### Post by gregphil on 2008-09-09
Item 2 on your list is probably the long standing ubuntu bugs:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)
(ignore ref to ADS, it applies to all authenticated shares)

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/224351)

These are actually due to a bug in the new gnome gvfs library 
[http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26](http://bugzilla.gnome.org/show_bug.cgi?id=524485#c26)

---

### Post by sombrancelha on 2008-09-09
i think you're right. I had a look at those links and they seem to have found a solution. However, I'm too newbie to follow the instructions there to solve my problem. I don't want to sound lazy, but could you (or someone else) please give more direct instructions?

Thanks

---

### Post by gregphil on 2008-09-09
There is no quick solution for those of us that don't want to rebuild the source and install a temporary version of the gnome library in question.  Installing a pre-built binary of the patched library is another option but involves more risk.....

You can however simply enter the FULL text share name in the applicaion you are trying to browse with, and then press enter.

For example in the nautilus network file browser, after you see the list of computers, click on one of the Windows computer icons (this leads to a blank browse screen).  Then change the input box to text (click on the pencil in the upper left) and append the share name to the network path.  Press enter.  If you entered a valid share the nautilus file browser will now prompt you for the username & password and then connect and allow browsing of that share.

You can find the name of the available shares by using the command line "smbclinet -L COMPUTERNAME"  That will prompt you for the password (assumes your logged on username) and then show the available shares on COMPUTERNAME.

Good Luck.

---

### Post by sombrancelha on 2008-09-10
weird...
I tried using the smbclient -L COMPUTERNAME command. Using it for the Ubuntu computer, it works fine. However, for the XP (named DESKTOP), I get:

```

timeout connecting to 208.70.188.17:445
timeout connecting to 208.70.188.17:139
Error connecting to 208.70.188.17 (Operação já em andamento)
Connection to DESKTOP failed (Error NT_STATUS_ACCESS_DENIED)

```

---

### Post by gregphil on 2008-09-10
That looks like a firewall issue (on the XP machines)

Turn off the firewalls to check.

---

### Post by sombrancelha on 2008-09-10
I turned it off and I keep getting the same error.

---

### Post by gregphil on 2008-09-11
Did you setup the sharing passwords on the Samba client machine? (using smbpasswd)

Samba needs to offer up the passwords to connect to the Windows box.  You may need to create accounts on the Windows box that match the username/passwords you want to allow to connect from the ubuntu box. (as an alternate you could use un-authenticated windows shares, ie anonymous guests allowed).  If you are using authenticated sharing, I think windows may default to NOT allowing "access this computer from the network" for normal users.  This can be changed, by an administrator, in the "local security policy"-"User Rights Assignment" settings (if needed)

However before you change anything else make sure you can ping the windows boxes from the ubuntu box.  You may have some other basic network setup issue.

---

