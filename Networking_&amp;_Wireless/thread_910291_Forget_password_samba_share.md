---
title: "Forget password samba share"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by eggy524 on 2008-09-04
Hi, I have a samba share in ubuntu which when i first connected, I checked the box, "remember forever" so ubuntu stores the password somewhere.

Is there any way I can make ubuntu remove the saved password?

Thanks

---

### Post by mykrob on 2008-09-04
yes, in the command line (terminal), type the following:

```

sudo smbpasswd -x username

```

for more information, check the manual page for smbpasswd in the terminal by typing:

man smbpasswd



hope this helps,
-myk

---

### Post by eggy524 on 2008-09-04
It gives the error:
Failed to modify password entry for user eggy

Is there a way to view a list of users with stored passwords?

---

### Post by dermawan123 on 2009-06-29
I am having this exact problem too... Anyone have any solution?

---

### Post by papenpj on 2009-06-29
Little clarification please on what your situation is.

1) Your Ubuntu system has the samba share and you want the other computer to stop connecting to it with the old password
   In this case you should be able to use "sudo smbpasswd <username that was stored on other computer>" that will change the password and make it so the computer isn't able to connect anymore.

2) Your Ubuntu system is connecting to ANOTHER computer and you have the password saved for that Second computer. And want to remove the password from the keyring.
   I'm not exactly sure what to do in this case.

3) Some situation i didn't list.

---

### Post by dermawan123 on 2009-06-29
> **papenpj said:**
> Little clarification please on what your situation is.

1) Your Ubuntu system has the samba share and you want the other computer to stop connecting to it with the old password
   In this case you should be able to use "sudo smbpasswd <username that was stored on other computer>" that will change the password and make it so the computer isn't able to connect anymore.

2) Your Ubuntu system is connecting to ANOTHER computer and you have the password saved for that Second computer. And want to remove the password from the keyring.
   I'm not exactly sure what to do in this case.

3) Some situation i didn't list.

Thank you for the quick reply...

The case is as your point (2).

I have an ubuntu system with 2 users. The first is "administrator" and the second is "public" which doesn't have administration rights. The "public" user can connect to any samba share on the samba server (Fedora Core 5), but he can not choose "remember forever". Suppose he accidentally selects the option "remember forever", other computer users who use the user "public" will then be able to access the samba share on the Fedora server he's not supposed to.

Doing the:
```
sudo smbpasswd <username>
```with the user "public" is not possible. So I tried with the user "administrator", but when i do ```
sudo smbpasswd <username>
```it gives the error:
```
failed to modify password entry for user <username>
```

---

### Post by papenpj on 2009-06-29
Well it sounds like then you should run the command on the Fedora system. Do you know what username was used for samba?
ex} your ubuntu system is remembering the password for "papenpj", so you login to the Fedora machine that is hosting that samba share. And you change the password for the username papenpj. Now, the administator will need a new password. Note: This way is different that you asked because your not changing ubuntu merely making its saved password useless. 

Or you could look under the keyring under the system tab or one of the administration things, Im running windows right now and headed to bed. But I can check back in the morning to see if I can find out exactly for you.  I'm still motivating myself to switch my desktop to Ubuntu since I rarely need office 2007. Most of my ubuntu experience is command line

---

### Post by dermawan123 on 2009-06-29
> **papenpj said:**
> Well it sounds like then you should run the command on the Fedora system. Do you know what username was used for samba?
ex} your ubuntu system is remembering the password for "papenpj", so you login to the Fedora machine that is hosting that samba share. And you change the password for the username papenpj. Now, the administator will need a new password. Note: This way is different that you asked because your not changing ubuntu merely making its saved password useless. 

Or you could look under the keyring under the system tab or one of the administration things, Im running windows right now and headed to bed. But I can check back in the morning to see if I can find out exactly for you.  I'm still motivating myself to switch my desktop to Ubuntu since I rarely need office 2007. Most of my ubuntu experience is command line

I can not change anything on the Fedora server, because there are other computers connected to the server, who may use the user I'm supposed to delete from the "public" user on this Ubuntu system.

Your second alternative is more feasible for me in this case. I have read that I need to check the keyring. But I dont know how to do that exactly. I have always been a Windows administrator, but have been a Linux user for quite a while. I'm not afraid to use the command lines. So if u want to show me how, I would very much appreciate it.

Anyway, just rest for tonight. I appreciate you trying to help me. Thanx :)

---

### Post by papenpj on 2009-06-29
ok I just tested it on mine so it should work for you.
On the top bar you want to go to
Applications->Accessories->Passwords and Encryption Keys

Then go to the "Passwords" tab
Then you can right click on the password you want to delete.

You may need to restart if you havn't since you saved the password because I did to get it to show up so I could delete it.

---

### Post by dermawan123 on 2009-06-29
> **papenpj said:**
> ok I just tested it on mine so it should work for you.
On the top bar you want to go to
Applications->Accessories->Passwords and Encryption Keys

Then go to the "Passwords" tab
Then you can right click on the password you want to delete.

You may need to restart if you havn't since you saved the password because I did to get it to show up so I could delete it.

Perfect... Tried it, and **it works**. Problem **solved**. Maybe because I haven't mounted the samba share, when I deleted the password entry, so I didn't have to restart.

Thanks a lot to you, papenpj.... highly appreciated :)

---

### Post by candidguy on 2009-07-31
hey i bought new laptop and having ubuntu 8.10 in it and i dont know the administrator password...... can any body help......

---

### Post by Adrianzr1 on 2012-05-25
I know this thread is old, just want to say thanks for the help, I had the same problem and fixed it the same way =) Thank you

---

### Post by oldos2er on 2012-05-25
Closed, please don't bump old threads.

---

