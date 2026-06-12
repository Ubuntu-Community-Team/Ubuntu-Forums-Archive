---
title: "passwords"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by bobk_nyc on 2011-07-08
I know there must be a way to dis able the having to enter a password all the time. I seem to spend half the time entering a password...thanks

---

### Post by srisharan on 2011-07-08
you should login as root for that.But that is insecure.I recommend that you donot do that.U or any piece of malware can break the system that ay

---

### Post by irv on 2011-07-08
> **bobk_nyc said:**
> I know there must be a way to dis able the having to enter a password all the time. I seem to spend half the time entering a password...thanks
You can set your login to be automatic so you don't have to enter your password each time, but as far as turning it off for everything you can't. You don't really want to. If you could and someone got on to your system from the outside they could destroy your system.
And another reason for the security is so you don't change something as a user. You need admin rights to make changes to the system.

---

### Post by nerdy_kid on 2011-07-08
> **srisharan said:**
> you should login as root for that.But that is insecure.I recommend that you donot do that.U or any piece of malware can break the system that ay

The root account in Ubuntu is locked.

to the OP:  Short answer is no, every time you perform an action requiring root access (installing programs, writing to system files etc) you will have to enter your password.

Long answer is it is possible, but insecure, and afaik it is against forum policy to tell users how to unlock the root account (make it possible to login as root).  You may be able to increase the time that the system remembers the password, but it is a little complicated and generally not encouraged.

---

### Post by srisharan on 2011-07-08
> **nerdy_kid said:**
> The root account in Ubuntu is locked.
.

It is indeed locked but it is possible to open it up.That was what I meant

---

### Post by haqking on 2011-07-08
The root account is disbaled by default under the canonical model.

It is very rare that this needs to be enabled and is not encouraged.

Everthing you need to do can be accomodated with su/sudo gksu/gksudo.

You can edit the sudoers file and adjust things to accomodate the needs.

I suggest you read this and go from there.

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

it is possible to edit this file and make the sudo password blank however this is not recommended or encouraged.

If i was you i would appreciate the security and lack of viruses and malware that are associated with linux because of such security models.

The request for authorisation to carry out an admin task is for a reason and helps prevent you from messing with your system too much unless you really know what you are doing. No disrpespect meant, but if you did fully understand and know the consequeneces then you wouldnt need to ask how to do it ;-)

So my advice is NOT to do what you are asking it to and learn to love the benefits of this security mechanism.

---

### Post by uRock on 2011-07-08
> **srisharan said:**
> It is indeed locked but it is possible to open it up.That was what I meant
[**Forum policy on log-in-as-root tutorials**]("http://ubuntuforums.org/showthread.php?t=716201")

Welcome to the forums,

What are you being asked for passwords for? 

Do you have automatic login enabled?(Do you have to use a password to log in?)

If you have auto login set, then the gnome key ring will ask for a password with many of the tasks you do. 

Regards,
uRock

---

### Post by oldos2er on 2011-07-08
**sudo -i** will give you a persistent root terminal. **exit** when done.

---

