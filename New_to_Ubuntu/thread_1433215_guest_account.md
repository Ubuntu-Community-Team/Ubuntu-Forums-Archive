---
title: "guest account"
date: 2010-03-18
forum: New to Ubuntu
---

### Post by Fika on 2010-03-18
Is there a guest account or other default users in ubuntu? 

If so, how do I remove or disable those accounts?

Thanks everyone

---

### Post by cariboo on 2010-03-18
The guest account is only available from the fast user switching applet, located in the same menu as the restart/shutdown command. So unless you specifically choose the guest account, it can't be used.

---

### Post by bodhi.zazen on 2010-03-18
> **Fika said:**
> Is there a guest account or other default users in ubuntu? 

If so, how do I remove or disable those accounts?

Thanks everyone

There are many many user accounts

```
cat /etc/passwd
```

I do not know of any location where all these users are documented, most are system users and you should not change them if you do not understand what they are.

In terms of the guest account, personally I lock it down with apparmor (jailbash).

If you want to see it in action , it is configured in Zenix

[http://zenix-os.net/](http://zenix-os.net/)

Otherwise jailbash is here :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-9.10/)

---

### Post by Fika on 2010-03-18
How do I add jailbash and all those extra profiles to apparmor?

sudo apt-get install apparmor-profiles does not include many of the profiles that I see there

---

### Post by pastalavista on 2010-03-18
> **cariboo907 said:**
> The guest account is only available from the fast user switching applet.....or in a terminal

```
/usr/share/gdm/guest-session/guest-session-launch
```

---

### Post by Doc on 2010-04-01
If all you want to do is disable guest sessions all you need to do is sudo **apt-get remove gdm-guest-session**.

hs

---

