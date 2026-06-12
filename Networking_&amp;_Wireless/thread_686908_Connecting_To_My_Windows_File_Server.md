---
title: "Connecting To My Windows File Server"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by Stephan Smith on 2008-02-03
Hi, All, I have been using Kubuntu 6.06 for a bit, and decided to give its Gnome brother a try, so I just installed Ubuntu 7.10. I am now trying to access my file server, which runs Windows 2000. Going through Places - Network, it gives me an icon that says Windows Network. So far, so good. When I click on this, I get workgroup. Good again. When I click this, instead of showing me the computers connected to workgroup, I get an error stating that the contents could not be displayed. I have gone into Shared Folders and made sure the work group name is correct. I also installed the full samba package, and smbfs. What have I missed here? I know that my server is set right, because Kubuntu accessed it just fine with smb4k (a kde program). Thanks for your help,

Steve

Question: Is it possible to use smb4k in Gnome?

---

### Post by wahr on 2008-02-03
Have the same problem.. Can't see my mac's smb shares.

I get a little bit closer.. I see my mac's hostname, click on that, and get the same error.

---

### Post by tad1073 on 2008-02-03
I have samba set up according to [THIS](http://support.microsoft.com/kb/813936/) post but it is not working for me. My problem is that i can't even get a shared file in "My Network Places" on XP. We have network magic that came with the router and I can share a file there but I can't see that file from ubuntu and i can only see ubuntu from network magic but i can't access my files and after 7days the you have to purchase a subscription to continue using network magic. i have my firewall on ubuntu set up correctly. I am about ready to give up.

---

### Post by hyperair on 2008-02-04
You can use smb4k in GNOME alright. Just like how I use Amarok in GNOME, Pidgin in KDE and so on.

---

### Post by Stephan Smith on 2008-02-04
Hi, hyperair,
Thanks much for the info! I installed smb4k through synaptic, and was connected to my server about a minute later. Excellent! \\:D/ 

Thanks again,

Steve

---

### Post by hyperair on 2008-02-04
@Stephan Smith: No problem.

@tad1073: Windows XP often has problem detecting other computers in the network. It's a very common problem, with very few simple solutions. There's one way to access your ubuntu shares from Windows, and that is to directly connect from the location bar. Use something like:
```

\\<ip address of ubuntu machine>\sharename

```

That's what I do at home, because Windows XP just annoys the hell out of me.

---

