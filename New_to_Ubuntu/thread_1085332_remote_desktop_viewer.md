---
title: "remote desktop viewer"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by patchido on 2009-03-02
well, i wanted to know if there is a way for me to go into my laptop thats in my house that have a Vista OS from my ubuntu intrepid, i have been trying to but i cant

---

### Post by patchido on 2009-03-03
so ?? seems noane know bout it :S

---

### Post by SamNSane on 2009-03-03
> **patchido said:**
> well, i wanted to know if there is a way for me to go into my laptop thats in my house that have a Vista OS from my ubuntu intrepid, i have been trying to but i cant

You will have to be scientific about this and provide very precise information about what it is that you want to do.

I log on to the desktop environments of Windows systems all the time using tsclient. (In the menu system it's at Applications -> Internet -> Terminal Server Client, or some such.) This software is present by default on an Ubuntu installation, so you don't need to install anything.

Chances are it's not going to be as simple as just launching that application and using it, though. I'm guessing from the way you worded your query that you might be trying to log on to a Vista notebook at home from some other location? If that's so, things start getting pretty complicated very quickly. In that case you may have to deal with issues like:

1. Does the location you are trying to connect from allow Internet access for protocols like RDP? (It probably does, but the the one where I work doesn't.)
2. Is your notebook computer at home connected directly to the Internet via a DSL or cable modem, or does it connect to the Internet through a router? Whichever way it connects to the Internet, does it use a fixed IP address provided by the ISP, or does the ISP use dynamic IP address allocation? If it connects through a router, you'll have to change settings on the router to allow RDP traffic to your notebook. And if your Internet-facing IP address is dynamic, you'll have to find some way to deal with the fact that the address you're trying to find from the remote location can change from time to time.
3. Vista will require you to specify that it's okay to use RDP to connect to it. Furthermore, I think it may require you to specify that it's okay to use an earlier version of the remote desktop client than it's default. (I think Vista normally requires RDP v6, but the client in Ubuntu is RDP v5.) This is only insofar as I recall from brief exposure. I only connect to Windows NT4 / 2000 / XP / 2003 systems from my Ubuntu systems.

Before folks here can help you, you need to post your exact situation and what you envision being able to accomplish by means of this remote connection.

If it's all being done on the same home network, it's a lot simpler.

There are also other means (VNC, etc.) of getting to the Vista notebook's desktop, but I recommend RDP because it's very much more efficient for use with a Windows system.

You will also need to do some thinking about security. Many people would prefer to use some means of "tunneling" a remote desktop session rather than just using it directly. Much of how you decide this matter depends upon what type of data you have on the notebook.

---

