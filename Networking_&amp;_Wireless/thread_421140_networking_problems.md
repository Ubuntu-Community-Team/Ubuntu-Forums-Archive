---
title: "networking problems"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by jacom on 2007-04-24
Hi Everyvody

I'm very new to linux. I installed Ubuntu 7.0.4 on my pc and everthing works fine. I can browse all the windows pc's. I tried to share a folder, and it said that it needed to install some services. After the instalation of these services it allowed me to share to folder.

My problem is that none of the windows pc (vista and XP) can browse my linux pc. All the windows machines can ping the machine but windows says pc not available. 

Can you please help me?

Thanks

Jaco

---

### Post by rjfioravanti on 2007-04-24
Can the windows machines see the shared folder?

If so, what is the error message you get when you try to navigate into the shared folder

---

### Post by jacom on 2007-04-24
When I type \\LINUXPC in windows explorer it says "LINUXPC is not available. But like I said I can ping the linux pc

---

### Post by selim76 on 2007-04-24
did you try to use the ip address instead of hostname? \\192.168...

---

### Post by rjfioravanti on 2007-04-24
Usually you can browse to a linux network share much like you would to a windows shared folder

I think it automatically installed samba for you, and usually that defaults to workgroup name of MSHOME I believe

Try browsing through All Windows Networks and see if you can find your computer in any of the workgroups available

---

### Post by JustinAlf on 2007-04-24
I just installed VirtualBox on Fiesty.  I used to be able to see my Linux machine with Vmware, but Vmware dosn't work with fiesty.  When i click on workgroup conputers, it says "MSHOME is not accesiable".  What does this mean?

---

### Post by rjfioravanti on 2007-04-25
I don't know anything about virtual boxes. It sounds like you are trying to access your linux machine from a windows virtual machine that is on the same computer as your linux? 

If so, maybe try accessing the linux machine from another separate windows machine on the network... if that also breaks then it rules out the possibility of the problem being related to the virtualization

---

