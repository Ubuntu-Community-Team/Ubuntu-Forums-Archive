---
title: "Remote managing Windows PCs"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by barcelonic on 2009-10-16
In my Ubuntu book it says that Ubuntu comes with software which allows you to do this but the only Windows editions that come with the server are Business and Enterprise type editions. 

So how would I go about remote managing a Windows Vista Home Edition PC?

---

### Post by gsuccess on 2009-10-16
this is a bit tricky.But I'll get back you soon.

---

### Post by Jason Cook on 2009-10-16
I would suggest using [LogMeIn.]("http://www.logmein.com/") That is what I am using now. There is a thread [here]("http://ubuntuforums.org/showthread.php?t=1280870") with suggestion on what others use.

---

### Post by barcelonic on 2009-10-16
Thx guys, LogMeIn sounds great!! Do both machines need Java installed?

---

### Post by CharlesA on 2009-10-16
Guessing the OP means RDP, you could use VNC to connect to a vista box no problem, but it's not secure.

---

### Post by scorp123 on 2009-10-16
> **barcelonic said:**
> In my Ubuntu book it says that Ubuntu comes with software which allows you to do this but the only Windows editions that come with the server are Business and Enterprise type editions.  Those "Windows Server" editions have a so called **"Terminal Server"**. Also known as **"Remote Desktop Server"** or **"RDP Server"**. So from Ubuntu you could use programs such as **"tsclient"** (= **T**erminal **S**erver client) or **"rdesktop"** to connect to those machines. Those Windows versions are also "multi-user" capable, e.g. each connecting user gets their own session.

With the home user versions of Windows such as XP and Vista you don't have that, as far as I know.

What you can do though:
you could install a program such as **TightVNC** on your Windows XP or Vista machine and then use a VNC client program such as **"vinagre"** to connect to it.

[http://www.tightvnc.com/](http://www.tightvnc.com/)


> **barcelonic said:**
>  So how would I go about remote managing a Windows Vista Home Edition PC? Via VNC. See above.

---

### Post by scorp123 on 2009-10-16
> **CharlesA said:**
>  but it's not secure. yes, I woulnd't use VNC over the Internet. But inside your own LAN it won't matter. If the intention is to use it over the Internet then I'd use something else, e.g. VNC-over-Hamachi or VNC-over-SSH

---

### Post by barcelonic on 2009-10-16
Ye its for internet access, not LAN.

---

### Post by scorp123 on 2009-10-16
> **barcelonic said:**
> Ye its for internet access, not LAN. You could use a VPN such as Hamachi then ...

See here:
[http://ubuntuforums.org/showthread.php?p=8113445#post8113445](http://ubuntuforums.org/showthread.php?p=8113445#post8113445)

The idea here being that you connect to the VPN and then use VNC this way. With this your VNC traffic would be encrypted.

---

### Post by CharlesA on 2009-10-16
> **scorp123 said:**
> You could use a VPN such as Hamachi then ...

See here:
[http://ubuntuforums.org/showthread.php?p=8113445#post8113445](http://ubuntuforums.org/showthread.php?p=8113445#post8113445)

The idea here being that you connect to the VPN and then use VNC this way. With this your VNC traffic would be encrypted.

This. I'd just SSH to my box then VNC over from there, but that means I'm sending over 2 virtual sessions so that's not as efficient as using Hamachi.

I don't access my windows machines from the internet anyway.

I did see [this]("http://www.softwaresecretweapons.com/jspwiki/windowsremotedesktopoverssh") talking about tunneling RDP over SSH.. but it sounds like a major pain in the butt.

---

### Post by Jason Cook on 2009-10-16
> **barcelonic said:**
> Thx guys, LogMeIn sounds great!! Do both machines need Java installed?
Both machines don't need to have Java installed. Only the machine you are connecting **from **needs Java.

---

