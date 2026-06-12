---
title: "a probleam in set up local area conncetion (pasword probleam)"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by Turge on 2008-02-27
hello!
i'm new in this forums and in ubuntu linux also.
and i have a probleam with a set up local area connection.
i was have a windows xp and me and my brother and my sister was have a local area connection.
and my sister have windows xp.
my brother ubuntu linux.
and me windows xp and ubuntu linux.
and we still have the local area connection but in my share i have a folder that only this folder in share and we cant go in to this foler cause it's want a password,
and i never have any password for share folders.
so itry to delete that and i cant, so now i cant share things with them they cant put folders and things in my folder only i can put on them a folders and things.


any body know maybe what the password could be ?
because I'm sure in a 100 percent that I didnt put any password before.
and it's not the same password in the log in i have almost try it.

Thx , ben.

---

### Post by spd106 on 2008-02-27
I'm going to assume you have installed Samba.

In order for you to access Samba shares you must have an account on the target system, this is for authentication purposes. To add a user account you must run the following command at a terminal.

```
sudo smbpasswd -a <username>
```

Then you enter their password and their account is created. This must be done for each person that you want to allow access to the machine.

You can switch on anonymous access in the smb.conf, but that's not recommended.

See this wiki page for more details [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Turge on 2008-02-28
when I put the code that you gave me in the command terminal so it's says : 

bash: syntax error near unexpected token `newline'

and I have do it in root.

any more help please?

---

### Post by Turge on 2008-03-03
Please somebody can help me?

---

### Post by Turge on 2008-03-03
any help?

---

### Post by Iowan on 2008-03-03
I'm having a hard time understanding the error message you got - what was the command you entered?

---

### Post by Turge on 2008-03-04
the code was that :
sudo smbpasswd -a <username>

what sud106 post in the first answer.

So what I should to do?

---

### Post by jonandrews on 2008-03-04
I've put a step by step guide to networking Ubuntu / XP pc's on a website:

[http://www.europe.eclipse.co.uk/Ubuntu](http://www.europe.eclipse.co.uk/Ubuntu)

Hope this is helpful.

---

### Post by Iowan on 2008-03-05
[QUOTE=Turge;4451226]the code was that :
sudo smbpasswd -a <username>QUOTE]
You are entering something like:```
sudo smbpasswd -a myusername
``` as opposed to```
sudo smbpasswd -a <username>
```  If you actually entered **<username>**, it probably won't work.

---

### Post by Turge on 2008-03-05
> **Iowan said:**
> [QUOTE=Turge;4451226]the code was that :
sudo smbpasswd -a <username>QUOTE]
You are entering something like:```
sudo smbpasswd -a myusername
``` as opposed to```
sudo smbpasswd -a <username>
```  If you actually entered **<username>**, it probably won't work.

ok i'm think it's work but it's tell me to put a new pasword so i didnt write anything and press enter
so than it's asks me the password so i press just enter and it's said wrong and than i put the password before and now it's work.
thx anyway.
and it was that code :
sudo smbpasswd -a myusername

---

