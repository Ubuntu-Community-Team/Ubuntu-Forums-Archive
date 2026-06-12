---
title: "Network Problem from XP to Ubuntu 6.06"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by heather on 2006-08-25
hi
i simply chose the samba way
went to shared folders,clicked on add
i chose the folder from the network drive i wish to share with smb
i have the host name and workgroup configured correctly

Name Movies

not sure weather to select do not share wins server

Wins Server or not
or what to fill in

 

from Ubuntu 6.06 to my Xp Machine across the room
when i login to the server from the xp machine
it asks for a user name and password
none of them works
perhaps i set up the network share incorrectly?
could someone please give me any advices

thank you

---

### Post by bswilson on 2006-08-25
Heather,

The problem is, you need to create a Samba user and corresponding password.  You can't just share a folder by giving it a name.  You need to tell Samba that there is a user (not the same as a Ubuntu user) that can connect.

Give this a shot.

1. Use the smbpasswd command to add a new user and to assign the account a password.

```
$ sudo smbpasswd -a <username>
```

Note: Enter YOUR password first to envoke the sudo privliges, then you'll be prompted to give <username> a new password.  Then you'll have to confirm that new password.

2. Just to be safe, restart Samba to make sure your changes are taken.

```
$ sudo /etc/init.d/samba restart
```

All set!  You should now be able to connect with the <username> you created (and its password).

---

### Post by heather on 2006-08-25
LOl oh my
you made that look too easy and it worked
i spent like 2 days reaqding 1000 ways to do this lol
and all seemed too complex
and here you just give me one or two lines to add lol

Thank you for your assistance

---

### Post by tonywhelan on 2006-08-25
Thank you!

Heather isn't alone in being grateful for this advice. I installed Ubuntu 6 last night and like the interface a lot (nice and clean), but had no idea I needed to create a Samba user - this wasn't needed when I last played with a linux distro (Xandros) as I recall.

Now all I have to do is conquer a few other obstacles .... :)

Tony
Australia, Canberra


> **bswilson said:**
> Heather,

The problem is, you need to create a Samba user and corresponding password.  You can't just share a folder by giving it a name.  You need to tell Samba that there is a user (not the same as a Ubuntu user) that can connect.

Give this a shot.

1. Use the smbpasswd command to add a new user and to assign the account a password.

```
$ sudo smbpasswd -a <username>
```

Note: Enter YOUR password first to envoke the sudo privliges, then you'll be prompted to give <username> a new password.  Then you'll have to confirm that new password.

2. Just to be safe, restart Samba to make sure your changes are taken.

```
$ sudo /etc/init.d/samba restart
```

All set!  You should now be able to connect with the <username> you created (and its password).

---

### Post by sinister99 on 2006-08-26
I have tried to add a new smb user, but I keep getting:

Failed to initialise SAM_ACCOUNT for user <my username>. Does this user exist in the UNIX password database?

I have tried a few different usernames, and I keep getting this

---

### Post by heather on 2006-08-26
i had the same problem once till i added a new user into the 
System/administration/users and groups

i belive any name that you wanna have used must be present in the unix users base

---

