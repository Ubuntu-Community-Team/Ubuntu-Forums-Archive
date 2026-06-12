---
title: "Ubuntu thin client - &quot;How to&quot; and &quot;Suggested Spec&quot;"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by spangeman on 2008-12-11
Hi

I would like to get a thin client setup going on my home network and I have a couple of questions. I currently have two old PC's and a laptop which would be the clients and I'd like to buy a new beefy PC to be the server.

I have done a little [reading]("http://wiki.ltsp.org/twiki/bin/view/Ltsp/LTSPTerminal") into this and Ubuntu seems capable of doing this using LTSP, having used Ubuntu as my desktop OS for the past year I have a fair level of experience with it but none with LTSP.

So anyway here are my questions........


1. Is the above setup possible using Ubuntu LPSP i.e. 1 new PC as the server, two more old PC's as the thin clients and a laptop as a thin client as well. The laptop is currently running Ubuntu 8.1.

2. I am guessing I would need to install a server edition of Ubuntu OS on the server and then a thin client install of the Ubuntu OS on each of the thin client machines (two old PC's and a laptop), is that correct?

3. How "beefy" (recommended spec) does the server need to be to have two clients browsing the internet, listening to music on amarok and downloading stuff like MP3's at the same time?

4. Can you point me towards some web pages on the subject for a noob? I have tried some googling but I am always worried that the advice may be out of date.

5. Is it possible for the thin clients to have a kind of dual boot where by they can boot up as thin clients if they wish or boot up as thick clients (full Ubuntu) off their own hard disk?

Thanks
Spangeman

---

### Post by albinootje on 2008-12-11
This link is useful for the server-install :
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

---

### Post by UbuWu on 2008-12-11
You don't need to install anything on the thin clients, they only need to be setup to boot from the network instead of the harddrive. You can sort of dualboot by switching between these two.

---

### Post by thefiestysoldier on 2008-12-16
> **UbuWu said:**
> You don't need to install anything on the thin clients, they only need to be setup to boot from the network instead of the harddrive. You can sort of dualboot by switching between these two.

So how would you do that??

---

### Post by thefiestysoldier on 2008-12-16
Also if youre interested, you can always use telnet or SSH to run programs from the server on the client.

---

### Post by spangeman on 2009-06-10
In case anyone is interested. In the end I installed a server edition of MS Windows on the server and then installed a full copy of ubuntu on the clients. From ubuntu I then remote desktop (using tsclient) to the server.

This setup works quite well because someone can be logged onto the server taking advantage of the full graphics power (actually at the desk logged on) while someone else is remote desktop'd to it.

Cheers
Spangeman

---

